---
title: "VAIO PRO 13 UEFI problems Ubuntu 14.04 and Windows 8.1"
date: 2014-04-27
forum: Hardware
---

### Post by kwoby on 2014-04-27
On my VAIO pro 13 I installed Ubuntu 14.04 with fastboot disabled in the Bios.

As long as I boot Ubuntu grub come back.     If I choose Windows I never get grub again and Windows comes up     automatically. What can I do?

---

### Post by kwoby on 2014-04-27
After searching around I finally found a solution
To be able to boot in Ubuntu again using the grub I     had to boot from an USB Ubuntu:
    then I did  in a terminal:
    
    [INDENT]s[FONT=courier new]udo mount /dev/sda6         /mnt/                                                                                      #monte le / du systeme a réparer dans /mnt du live usb [/FONT][FONT=courier new]
      sudo mount /dev/sda3         /mnt/boot/efi/                                                                         #monte la partition de boot dans /boot/efi du système a réparer 
      for i in /dev /dev/pts /proc /sys; do sudo mount -B ${i}         /mnt${i}; done               # ainsi que d'autres répertoires         necessaires 
      sudo modprobe         efivars                                                                                             # charge les variables efi 
      sudo chroot /mnt
      exit 
      for i in /sys/ /proc/ /dev/pts /dev; do sudo umount         /mnt${i}; done 
      sudo umount /mnt/boot/efi 
        sudo reboot[/FONT]

[/INDENT]
After rebooting you get your original grub back again.


Now in a terminal:[FONT=courier new]
[/FONT]
[INDENT=2][FONT=courier new]sudo mount /dev/sda3         /mnt/boot/efi/[/FONT]
[/INDENT]
you have to copy mnt/boot/efi/EFI/Microsoft to i.e. mnt/boot/efi/EFI/MSBoot
and rename the original mnt/boot/efi/EFI/Microsoft to  i.e as     /mnt/boot/efi/EFI/BAKMicrosoft

Now comes a further step, you have to make a new entry in grub telling grub to choose the efi in the new MSBoot folder:
edit the file /etc/grub.d/40_custom like this:
[INDENT]       [INDENT]#!/bin/sh
        exec tail -n +3 $0
        # This file provides an easy way to add custom menu           entries.  Simply type the
        # menu entries you want to add after this comment.  Be           careful not to change
        # the 'exec tail' line above.
        menuentry 'Windows 8.1 (on /dev/sda3)' --class           windows --class os $menuentry_id_option           'osprober-efi-5E8F-28C8' {
                insmod part_gpt
                insmod fat
                set root='hd0,gpt3'
                if [ x$feature_platform_search_hint = xy ];           then
                  search --no-floppy --fs-uuid --set=root           --hint-bios=hd0,gpt3 --hint-efi=hd0,gpt3           --hint-baremetal=ahci0,gpt3  5E8F-28C8
                else
                  search --no-floppy --fs-uuid --set=root           5E8F-28C8
                fi
                chainloader /EFI/MSBoot/bootmgfw.efi
        }
        set timeout_style=menu
        if [ "${timeout}" = 0 ]; then
          set timeout=10
        fi
        [/INDENT]     [/INDENT]
When you want to reboot in Windows select the new entry. Now you     have your grub again.
    
    
    Hope it helps!

---

