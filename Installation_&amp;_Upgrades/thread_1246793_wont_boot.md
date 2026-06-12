---
title: "wont boot"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by AmerNewbieInDE on 2009-08-22
i cant get my notebook to boot, after selecting ubuntu in grub, it starts to load, but then stops. something about missing or bad file ls /dev ??? any idea? is there a way do do a repair?

---

### Post by whych on 2009-08-22
Can you boot from the live cd and then open a terminal and type: sudo /sbin/fdisk -l and post the output.
Also, what is the whole error message for /dev??

---

### Post by AmerNewbieInDE on 2009-08-22
ok, here is what is on the screen at boot...

[  16.663115] sd 6:0:0:0: [sdb] attached SCSI removable disk

Done.

Gave up waiting for root devise. Common problems

-Boot args (cat /proc/cmdline)
      -check rootdelay= (did the system wait long enough?)
      -check root= (did the system wait for the right devise?)
- mising modules (cat /proc/modules; ls /dev

ALERT!  Does not exist, dropping to shell

BusyBox v1.10.2

(initramfs)

i am on the pc, started by usb, just cant boot off main drive. i have looked in /proc/ there is nothing there

---

### Post by AmerNewbieInDE on 2009-08-22
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdab5c232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10240000   27  Unknown
/dev/sda2   *        1275       19897   149579776    7  HPFS/NTFS
/dev/sda3           19898       38403   148649445   83  Linux
/dev/sda4           38404       38913     4096575    5  Extended
/dev/sda5           38404       38913     4096543+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ffc810

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       37785   303507981   83  Linux
/dev/sdb2           37786       38913     9060660    5  Extended
/dev/sdb5           37786       38913     9060628+  82  Linux swap / Solaris

---

### Post by AmerNewbieInDE on 2009-08-22
can anyone help??

---

### Post by presence1960 on 2009-08-22
Let's get a better look at your setup. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by AmerNewbieInDE on 2009-08-22
thanks for the help, i found the error.. it was in menu.lst ... lrft out root=/dev/sda3.. but now i got another problem. I got loged on, but it has me with no privileges. cant even sudo or gksudo users-admin, tells me i am not allowed..

---

### Post by presence1960 on 2009-08-22
> **AmerNewbieInDE said:**
> thanks for the help, i found the error.. it was in menu.lst ... lrft out root=/dev/sda3.. but now i got another problem. I got loged on, but it has me with no privileges. cant even sudo or gksudo users-admin, tells me i am not allowed..

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

follow the instructions on that link

---

