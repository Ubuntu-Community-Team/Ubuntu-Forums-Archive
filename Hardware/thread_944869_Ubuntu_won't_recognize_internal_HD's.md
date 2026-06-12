---
title: "Ubuntu won't recognize internal HD's"
date: 2008-10-11
forum: Hardware
---

### Post by DOS Chuck on 2008-10-11
I have recently just started using Ubuntu 8.04 and, so far, love it. I do have a problem...I can't mount my 2 internal HD's. 
I have a 3GHz P4, 1G RAM, 2 internal HD's(C:,D:) and a 3rd RAID HD(E:). I also have a USB external drive.
Ubuntu is installed on the RAID E: drive. It finds and mounts the USB drive (takes about 30 minutes to do so) but never finds the 2 internal drives. The C: drive has WinXP installed and the D: drive is formatted NTFS,active and blank.
How can I access the the drives? Should it take so long to find the USB drive? And the CD/DVD drives, as well? Is it because it's installed on the RAID drive? I tried installing it on the blank D; drive but it took forever,way too many errors, and eventually just stopped.
I tried Mandriva out, installed on the D: drive and it worked ok but I like Ubuntu better.

Thanks in advance.

---

### Post by bhaverkamp on 2008-10-11
> **DOS Chuck said:**
> I have recently just started using Ubuntu 8.04 and, so far, love it. I do have a problem...I can't mount my 2 internal HD's. 
I have a 3GHz P4, 1G RAM, 2 internal HD's(C:,D:) and a 3rd RAID HD(E:). I also have a USB external drive.
Ubuntu is installed on the RAID E: drive. It finds and mounts the USB drive (takes about 30 minutes to do so) but never finds the 2 internal drives. The C: drive has WinXP installed and the D: drive is formatted NTFS,active and blank.
How can I access the the drives? Should it take so long to find the USB drive? And the CD/DVD drives, as well? Is it because it's installed on the RAID drive? I tried installing it on the blank D; drive but it took forever,way too many errors, and eventually just stopped.
I tried Mandriva out, installed on the D: drive and it worked ok but I like Ubuntu better.

Thanks in advance.
Definitely should not take 30 minutes to detect usb drives. I hotplug them all the time and they are noticed in a few seconds. Could be you don't have automounter service enabled. ntfs-3g driver should be able to mount your nfts drives. I have a similar setup and it all works just fine. Check services automounter for usb drive issue and ntfs-3g driver for ntfs issues.

---

### Post by DOS Chuck on 2008-10-12
I checked the services...there is no "automounter" listed. And I can't find the ntfs-3g driver. Also, if this means anything,under "computer" there is a SCSI drive listed. I don't have any SCSI drives. Should it be there?

Also, just how did you install Ubuntu? Did you boot off the CD? Install directly from that or allow the Live version to load and then install through that? Or,"Install along side Windows"? Does it make a difference?

---

### Post by bhaverkamp on 2008-10-13
The automounter is called volumes mounter in the gui. The service name is autofs.

---

### Post by DOS Chuck on 2008-10-13
Yup...it's there and activated. I found ntfs-3g but don't see anything I can do with it. Also,I noticed, the CD and DVD drives don't show up until the USB drive mounts. THEN I can also plug in a flashdrive and it mounts instantly,along with any CD or DVD I insert.
I reinstalled Mandriva on the D: drive and it mounts all drives as it boots. It's bootloader is in the MBR. Could that be why Ubuntu is so slow? It's only listed in my WinXP boot.ini file.

---

### Post by DOS Chuck on 2008-11-07
Sorry about not getting back to this......
For various reasons,I had to reinstall everything. It still takes,and I timed it,an hour before Ubuntu recognizes my external USB drive,CD-RW drive and my DVD drive.

Now,I just have WinXP on c: & d: drives and Ubuntu 8.04 on the RAID h: drive.
Autofs IS running.Ntfs-3g is present.

While booting I will get this message maybe 6 times or more:

170.405435 etc., through 350.xxxxxx status: {DRDY}
(and so on)                         ata1:00: buffer i/o error device sda logical block 0
Loading hardware drivers                          [fail]

and eventually it boots into Ubuntu.

Any connection? All the present drives do show up during boot sequence. But still no internal drives,c: and d:, mounted.

---

### Post by DOS Chuck on 2008-12-11
Ok....I have done evrything I can find to do dealing with this problem. autofs is running,ntfs-3g is configured,I edited fstab and added an appropriate line to mount sdc1. No change. It takes an hour to find and mount the USB drive.

The 2 internal drives never do show up, much less get mounted. Also, I can't use the CD/DVD drives until the USB drive is mounted.

Any ideas? I'm stumped.

---

