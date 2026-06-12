---
title: "PC don't turn on after dual boot"
date: 2020-10-04
forum: Hardware
---

### Post by dualdualr on 2020-10-04
hello guys, i hope i can get an answer from this forum.
i bought an used laptop and i dual boot ubuntu and window10 as i use on my former laptops.
This laptop has strange problem. Everytime i dual boot, it went fine.After using laptop and i sleep at night.In the next morning that laptop doesn't turn on.
Then i remove battery and use DC , then plug in and power up.,it went fine.(but grub went missing and direct boot to window).
So, i reinstall linux and grub re-appear.(i use as before and i sleep).In the next morning that happen again.It went like that in 3 days straight.
After 3 days,i don't install linux anymore.That power doesn't up problem didn't happen anymore.
What wrong with this.This pc can't accept dual boot? or any problem relates to hardware?

forgive my bad writing and hope u understand what i mean.

My laptop is MSIGL62M.

---

### Post by oldfred on 2020-10-05
Have you updated UEFI to latest version? And if SSD, updated SSD firmware?

What version of Ubuntu.

Issues often common by brand, some issues different if Intel or AMD.
MSI MPG x570 Gaming Edge & 2080S GPU
[https://askubuntu.com/questions/1197414/dual-booting-windows-10-and-ubuntu-on-separate-ssds?noredirect=1#comment2008840_1197414](https://askubuntu.com/questions/1197414/dual-booting-windows-10-and-ubuntu-on-separate-ssds?noredirect=1#comment2008840_1197414)
MSI GS65  Boot parameter: modprobe.blacklist=nouveau 
[https://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions](https://askubuntu.com/questions/1061109/dual-boot-windows-10-cannot-boot-latest-ubuntu-but-only-older-versions)
MSI GE63 Update UEFI then acpi=off not required
[https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues](https://askubuntu.com/questions/1059029/18-04lts-msi-ge63-boot-issues) & 
[https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off](https://askubuntu.com/questions/1038637/how-to-install-ubuntu-on-msi-ge63-without-acpi-off)
MSi GT72VR-6RE Dominator Pro - some settings required
[https://ubuntuforums.org/showthread.php?t=2365997](https://ubuntuforums.org/showthread.php?t=2365997)

---

### Post by dualdualr on 2020-10-05
i believe my bios is latest version for this laptop sir.And i am using HDD not SSD.i use 20.0.4 ubuntu.

---

