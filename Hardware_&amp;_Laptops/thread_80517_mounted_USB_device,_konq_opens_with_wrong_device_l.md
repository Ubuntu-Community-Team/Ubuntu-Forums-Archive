---
title: "mounted USB device, konq opens with wrong device link (Solved)"
date: 2005-10-22
forum: Hardware &amp; Laptops
---

### Post by jabster on 2005-10-22
Hi.

I just installed kubuntu, and am having a bit of an issue with USB. The same problem happens with both my Fuji camera and my iriver iHP120.

I plug it in, it gets detected, and konqueror pops up. It is pointed at this location: media:/sda1: ```
error occurred while loading media:/sda1/: The file or folder media:/sda1/ does not exist.
``` And it doesn't show up in the "media:/" list either. Edit: It DOES show up in "/media" tho. (end edit)

Here's the output from tail -f /var/log/messages: ```
Oct 22 11:15:25 localhost kernel: [30358.236445] usb 5-2.4: new high speed USB device using ehci_hcd and address 6 Oct 22 11:15:25 localhost kernel: [30358.291231] scsi4 : SCSI emulation for USB Mass Storage devices Oct 22 11:15:26 localhost usb.agent[19258]: usb-storage: already loaded Oct 22 11:15:30 localhost kernel: [30361.068951] Vendor: TOSHIBA Model: MK2004GAL Rev: JC10 Oct 22 11:15:30 localhost kernel: [30361.068960] Type: Direct-Access ANSI SCSI revision: 00 Oct 22 11:15:30 localhost kernel: [30361.071198] SCSI device sda: 39063024 512-byte hdwr sectors (20000 MB) Oct 22 11:15:30 localhost kernel: [30361.072865] SCSI device sda: 39063024 512-byte hdwr sectors (20000 MB) Oct 22 11:15:30 localhost kernel: [30361.072874] /dev/scsi/host4/bus0/target0/lun0: p1 Oct 22 11:15:30 localhost kernel: [30361.113183] Attached scsi disk sda at scsi4, channel 0, id 0, lun 0 Oct 22 11:15:31 localhost scsi.agent[19307]: sd_mod: loaded sucessfully (for disk)
```

And here is /etc/mtab: ```
/dev/sda1 /media/IHP-100 vfat rw,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
```

As you can see, it is mounted at /media/IHP-100. Pointing konq there brings up the directory listing for the iriver.

Why does it do this?

Do I need to go and create some udev rules with some consistent symlinks and mount points? I would think not, since autodetection is working and it's getting mounted; it's just that konq is opening up the wrong location. I'm not getting an icon on my desktop either, and I have KDE set to show mounted hard disk volumes.

I am running the AMD64 version of kubuntu btw.

Also, along these same lines, how do I unmount this thing? (Besides "umount /mnt/IHP-100" that is.) I want my wife to be able to plug in, transfer files, then disconnect. Safely. Having her type things into a console is not acceptable. She'll hurt me. :-)

Thanks in advance, 
john

---

### Post by aysiu on 2005-10-22
[http://www.ubuntuforums.org/showthread.php?t=74541](http://www.ubuntuforums.org/showthread.php?t=74541)

---

### Post by jabster on 2005-10-22
Thank you. Didn't think it'd be a universal k-ubuntu problem and not just kde.

Reboot fixed things.

thx,
john

---

