---
title: "L aptop boot freezes when on battery..[SOLVED]"
date: 2009-08-28
forum: Hardware
---

### Post by DJKnut on 2009-08-28
This is a problem I encountered the first time I tried linux on my laptop (Mint7..) and now I re-encountered it in Ubuntu 9.04.... Everything is fine when it's plugged in, but on battery, I must keep typing the enter key until the boot up gets to the pointer (arrow..) then it finishes OK....        The problem stems from the High Precision Timer (HPET, formerly known as the Multimedia Timer..) is a hardware timer used in PCs. It was jointly developed by Intel and Microsoft...

In the terminal, type:
**gksu gedit /boot/grub/menu.lst**

You'll have to enter the system password, then the editor will open.. slide down to...
                                 

                                   **[COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]## ## End Default Options ##[/SIZE][/FONT][/COLOR]**
 
[COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]title        Ubuntu 9.04, kernel 2.6.28-15-generic[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]uuid        7e2d82bc-b82f-4af3-9e84-9167a8426d31[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=7e2d82bc-b82f-4af3-9e84-9167a8426d31 ro quiet splash [/SIZE][/FONT][/COLOR] 
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]initrd        /boot/initrd.img-2.6.28-15-generic[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]quiet[/SIZE][/FONT][/COLOR]
 

 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]uuid        7e2d82bc-b82f-4af3-9e84-9167a8426d31[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=7e2d82bc-b82f-4af3-9e84-9167a8426d31 ro  single[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]initrd        /boot/initrd.img-2.6.28-15-generic[/SIZE][/FONT][/COLOR]
 

 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]title        Ubuntu 9.04, kernel 2.6.28-11-generic[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]uuid        7e2d82bc-b82f-4af3-9e84-9167a8426d31[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7e2d82bc-b82f-4af3-9e84-9167a8426d31 ro quiet splash [/SIZE][/FONT][/COLOR] 
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]initrd        /boot/initrd.img-2.6.28-11-generic[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]quiet[/SIZE][/FONT][/COLOR]
 

 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]uuid        7e2d82bc-b82f-4af3-9e84-9167a8426d31[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7e2d82bc-b82f-4af3-9e84-9167a8426d31 ro  single[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]initrd        /boot/initrd.img-2.6.28-11-generic[/SIZE][/FONT][/COLOR]
 

 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]title        Ubuntu 9.04, memtest86+[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]uuid        7e2d82bc-b82f-4af3-9e84-9167a8426d31[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]kernel        /boot/memtest86+.bin[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]quiet[/SIZE][/FONT][/COLOR]


[COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]You'll need to edit two places... and add **hpet=disabled**[/SIZE][/FONT][/COLOR]


                                                                    [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]## ## End Default Options ##[/SIZE][/FONT][/COLOR]
  
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]title        Ubuntu 9.04, kernel 2.6.28-15-generic[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]uuid        7e2d82bc-b82f-4af3-9e84-9167a8426d31[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=7e2d82bc-b82f-4af3-9e84-9167a8426d31 [/SIZE][/FONT][/COLOR][COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]**hpet=disabled **[/SIZE][/FONT][/COLOR][COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]ro quiet splash [/SIZE][/FONT][/COLOR] 
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]initrd        /boot/initrd.img-2.6.28-15-generic[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]quiet[/SIZE][/FONT][/COLOR]
 

 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]uuid        7e2d82bc-b82f-4af3-9e84-9167a8426d31[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=7e2d82bc-b82f-4af3-9e84-9167a8426d31 ro  single[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]initrd        /boot/initrd.img-2.6.28-15-generic[/SIZE][/FONT][/COLOR]
 

 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]title        Ubuntu 9.04, kernel 2.6.28-11-generic[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]uuid        7e2d82bc-b82f-4af3-9e84-9167a8426d31[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7e2d82bc-b82f-4af3-9e84-9167a8426d31 [/SIZE][/FONT][/COLOR][COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]**hpet=disabled **[/SIZE][/FONT][/COLOR][COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]ro quiet splash [/SIZE][/FONT][/COLOR] 
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]initrd        /boot/initrd.img-2.6.28-11-generic[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]quiet[/SIZE][/FONT][/COLOR]
 

 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]uuid        7e2d82bc-b82f-4af3-9e84-9167a8426d31[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=7e2d82bc-b82f-4af3-9e84-9167a8426d31 ro  single[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]initrd        /boot/initrd.img-2.6.28-11-generic[/SIZE][/FONT][/COLOR]
 

 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]title        Ubuntu 9.04, memtest86+[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]uuid        7e2d82bc-b82f-4af3-9e84-9167a8426d31[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]kernel        /boot/memtest86+.bin[/SIZE][/FONT][/COLOR]
 [COLOR=#333333][FONT=FreeSerif, serif][SIZE=2]quiet[/SIZE][/FONT][/COLOR]
 
 
Save and exit the editor, then exit the terminal and all will go smoothly on the next boot!!   Cheers, Dave

---

