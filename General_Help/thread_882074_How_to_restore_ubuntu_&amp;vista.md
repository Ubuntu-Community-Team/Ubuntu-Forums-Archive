---
title: "How to restore ubuntu &amp;vista"
date: 2008-08-06
forum: General Help
---

### Post by kingkong22 on 2008-08-06
After I created a thread [http://ubuntuforums.org/showthread.php?t=874114](http://ubuntuforums.org/showthread.php?t=874114)

It seems vista came back & worked fine. But Ubuntu still cannot work due to the following error message:

Error 17: can not selected partition
press any key to continue ...

Does anyone can guide me to fix it ! Thank you very. very much !!!

Regards,

---

### Post by northern lights on 2008-08-06
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by kingkong22 on 2008-08-06
Could you give me more specific instructions on how to do step by step ? thank you so much !!!

Regards,

---

### Post by northern lights on 2008-08-06
From within Windows download [Auto Super Grub Disk]("http://forjamari.linex.org/frs/download.php/910/auto_super_grub_disk_1.0.exe"). Double-click auto_super_grub_disk_1.0 icon, install it, and reboot.

On the next boot, select the UNetbootin-supergrubdisk menu entry. Do nothing till you see your Grub menu again.

Next time you boot Windows, click yes when asked to remove UNetbootin-supergrubdisk to remove the Super Grub Disk menu entry.

---

### Post by kingkong22 on 2008-08-06
COOL ! I will try it & report it ! Thanks alot !!!

Regards,

---

### Post by kingkong22 on 2008-08-07
I downloaded auto_super_grub_disk_1.0 & installed it, then re-booted Laptop, it run & displayed the following information:

Booting 'GRUB => MBR & !LINUX! (1)  AUTO  ;-)'
findf  /grub/stage1  /boot/grub/stage1
root (hd0,3)
filesystem type is ext2fs, partition type 0x83
setup (hd0)
checking if "/boot/grub/stage1" exists ... yes
checking if "/boot/grub/stage2" exists ... yes
checking if "/boot/grub/e2fs_stage1_5" exists ... yes
Running "embed /boot/grub/e2fs_stage1_5(hd0)" ...

over here, it looks hang. does it take a long time to go through ? could you tell me why ?  Thanks a lot !

Regards,

---

