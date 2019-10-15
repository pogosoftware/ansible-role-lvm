LVM
=========

This role allows to create a volume group with logical volume and mount it to fstab.


Role Variables
--------------

| Attribute | Description                  |
|-----------|------------------------------|
| vgs.vg    | volume group name            |
| vgs.pvs   | physical device              |
| lvs.lv    | logical volume name          |
| lvs.size  | logical volume size          |
| lvs.path  | logical volume path to mount |


Example Playbook
----------------

  - hosts: localhost
    become: yes
    roles:
      - pogosoftware.lvm
    vars:
      vgs:
        - vg: data
          pvs: /dev/sdc
          lvs:
            - lv: docker
              size: +80%VG
              path: /var/lib/docker
            - lv: logs
              size: +20%VG
              path: /var/log
