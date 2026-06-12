---
title: "Live ubuntu on usb pen where other OS are already present"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by upsfeup on 2009-11-06
I have an usb pen where I have several recovery OSes (PE, recovery cd..)

I would like to add ubuntu (live) to this pen.

I unzipped the ISO contents to a folder in the pen /ubuntu and created an extra grub entry for it in menu.lst

```

title Ubuntu 9.10
kernel /ubuntu/casper/vmlinuz file=/ubuntu/preseed/ubuntu.seed initrd=/ubuntu/casper/initrd.lz ro single ignore_uuid
initrd /ubuntu/casper/initrd.lz
boot
```

It starts to boot fine, until it gives the following error.
Waiting for root file system...
```
(some lines regarding the pen usb drive)
[ 8.590545]  sdb sdb1
[ 8.601533] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 8.601533] sd 2:0:0:0: [sdb] Attached SCSI removable disk
Done.
Gave up waiting for root device. Common problems
- Boot args (cat /proc/cmdline)
 - Check rootdelay= (did the system wait long enough?)
 - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/mudles; ls /dev)
ALERT! does not exist. Dropping to a shell!

```

Please not that I can't use any of the installers as I need to preserve the present grub and menu.lst.

I just need the correct grub commands.

Can anyone help?

---

### Post by upsfeup on 2009-11-12
Can't anyone help with this issue?

---

### Post by evenglow on 2009-11-20
Add rootdelay=90 to your kernel line. I had the same problem with this:
kernel /casper/vmlinuz noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper

after this though it worked fine.
kernel /casper/vmlinuz rootdelay=90 noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper

Got the tip from here:
[http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

---

### Post by darkod on 2009-11-20
I recently created usb stick with both 32bit and 64bit version of desktop and clonezilla live cd.
I put them in separate partitions and after many different tries the entry in grub that worked for me was:

title Try Ubuntu 9.10 32bit
uuid ####
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
initrd /casper/initrd.lz
boot

This is for the live CD Try Ubuntu entry. I used uuid because I had to use different partitions otherwise files use same structure. For the Install Ubuntu option the entry is:

title Install Ubuntu 9.10 32bit
uuid ####
kernel /casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
initrd /casper/initrd.lz
boot

Adjust to your situation. Hope that could help.

---

### Post by evenglow on 2009-11-21
After messing around with another flash drive I ended up with this:

title Ubuntu Live Persistent
find --set-root /casper-rw
kernel /casper/vmlinuz rootdelay=90 cdrom-detect/try-usb=true persistent rw file=/cdrom/reseed/ubuntu.seed boot=casper
initrd=/casper/initrd.lz

That seemed to fix the errors about root device not responding.

---

### Post by upsfeup on 2009-11-23
Thanks for the tips guys!

Currently, I'm using
```

title Ubuntu 9.10
kernel /ubuntu/casper/vmlinuz rootdelay=90 file=/ubuntu/preseed/ubuntu.seed single ignore_uuid cdrom-detect/try-usb=true ro boot=casper
initrd /ubuntu/casper/initrd.lz
boot
```

Unfortunately now I'm pegged with another error:

/init: line 1: can't open /dev/sr0: No medium found

The other reports that mention this error on the web report to missing .disk folder (that is present). What is he looking for?

---

### Post by evenglow on 2009-11-30
How far along during loading are you getting that error? I have seen similar messages while loading and I thought it was looking for files on CD. Of course there is no CD but some parts during loading specifically look for info at the CD drive, not where the install was launched from.

---

### Post by darkod on 2009-11-30
Why don't you try my suggestion from post #4. I am booting Ubuntu with those commands from usb stick, and I am able to boot either Try Ubuntu option or Install Ubuntu with slightly different entries.

---

