---
title: "Placing iso files in partition"
date: 2011-06-03
forum: Hardware
---

### Post by MRoeDesigns on 2011-06-03
So I made a 17 gig partition in my harddrive for a second linux system, but Im stuck as to how I continue. I've got the ISO file for linux, and like I said the partition is made and formatted, I just don't understand how / what tools I can use to put the files on the harddrive and get it to dual boot?

---

### Post by oldfred on 2011-06-04
The normal ways are to use burn it to a CD (not copy) or install to a USB flash drive.

But you can use grub2 to loopmount boot many ISOs and install to a different partition. But ISO has to be set up a certain way for that to work.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by MRoeDesigns on 2011-06-04
I followed the "ISO Booting with Grub 2" thread, but I'm not sure what to do after updating grub. I got up to that point fine. I added this to the custom_40 file like it said;

```

menuentry "Linux 2" {
set isofile="/boot/iso/lnx.iso"
loopback loop (hd0,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
} 

```

But now what? I read elsewhere that you also need to edit the menu.lst file, is this true?

Also, I'm not sure if the hd0,1 needs to be changed.. I know when I open GParted it says its in /dev/sdb (sdb1 being the ext4 partition), so I'm not exactly sure what to put there. Is hd0,1 right or would it be like sdb,1?

Thanks for all the help, and sorry for all the questions. I'm relatively new to linux.

---

### Post by oldfred on 2011-06-04
After editing anything with grub2, you just run this to create a new grub.cfg. The menu.lst is from grub legacy which now has not been used since 9.04 unless you upgraded and did not upgrade grub.

sudo update-grub

If your Ubuntu install is in sdb1 (where /boot/iso is) and you boot from sda then I think it would be hd1,1, but if you boot from sdb ( BIOS setting) then it is hd0,1. If it does not work use e on grub's menu and edit to the other number.

When you boot from any device then that device is in grub hd0. I boot from sdb or sdc and sometimes have to manually adjust the entries that I copied depending on which drive I boot at time of booting. It is even worse with flash drives as I may have more than one and when I boot one of them, it gets real confusing.

---

