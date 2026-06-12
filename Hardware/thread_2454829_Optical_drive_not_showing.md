---
title: "Optical drive not showing"
date: 2020-12-07
forum: Hardware
---

### Post by Nina_W on 2020-12-07
I have an internal optical drive on my laptop that used to work and now doesn't. I can open and close it, when I put a disk in, it goes round  - then nothing. It isn't showing on the file manager, I've opened up a terminal window and nothing showing in the /dev drive either. 
I don't use it all that often so I'm not sure if it stopped working after an update or not.

Any suggestions as to how to fix or what diagnostics I can do? I've searched online but all the help things I can find assume the drive is actually showing.

---

### Post by CelticWarrior on 2020-12-07
Check BIOS/UEFI first. 
If still recognized in the firmware then try booting with a know good bootable disk. If it boots then it's a problem with the OS (Ubuntu, I'm assuming) because booting from optical media happens before and independently of the installed OS. If it doesn't boot then it's probably defective.

Please also note that optical drives have different lasers for different types of media and they can fail independently.

---

### Post by Nina_W on 2020-12-07
I've only got Ubuntu on USB rather than disk. 
I didn't know about the different lasers but I've tried CD-Rom, Audio CD and DVD and it reacts to the fact that there is something in there in that it spins round, but doesn't seem to be able to see it.
Ubunut OS only shows the drive is present if a disk is in which doesn't help me know if it isn't detecting the drive at all or it isn't reading the disk. Is there a Linux command that would tell me if it was detecting the drive at all, or command the drive to do something.
Does the UEFI tell me if it is seeing the drive, if so any idea what heading it is under? I'm suspecting it might be easy to find if it is there but not easy to see where it should be if it is missing.

---

### Post by ajgreeny on 2020-12-07
I had this problem with my 6 year old desktop machine recently.

I stuck a lens-cleaner disk in the drive, ran the cleaning process which was shown in VLC on screen and all was well.

I don't know what happens if you do not have a disk player application of some sort open, hence using VLC, which normally plays anything I throw at it.  It worked for this cleaner disk as well!

---

### Post by tea for one on 2020-12-07
> **Nina_W said:**
> I've only got Ubuntu on USB rather than disk.

It looks like you are using Ubuntu [COLOR="#0000FF"]live[/COLOR] to troubleshoot hardware.

What OS is installed on your hard drive?

---

### Post by Yellow Pasque on 2020-12-08
> **Nina_W said:**
> Does the UEFI tell me if it is seeing the drive, if so any idea what heading it is under? I'm suspecting it might be easy to find if it is there but not easy to see where it should be if it is missing.

It's hard to say without knowing what specific laptop model you have. "Boot Order" is generally a good place to look.

As for diagnostics within Ubuntu, cd-drive is a good tool.
```
sudo apt-get install libcdio-utils
cd-drive
```

Output with my CD drive disconnected:
```

cd-drive version 2.1.0 x86_64-pc-linux-gnu
Copyright ...
No loaded CD-ROM device accessible.

```

And connected:
```

cd-drive version 2.1.0 x86_64-pc-linux-gnu
Copyright ...
The driver selected is GNU/Linux
The default device for this driver is /dev/cdrom

Drivers available...
  GNU/Linux ioctl and MMC driver     
  cdrdao (TOC) disk image driver     
  bin/cuesheet disk image driver     
  Nero NRG disk image driver         

CD-ROM drive supports MMC 3

                       Drive: /dev/cdrom
Vendor                      : TSSTcorp
Model                       : CDDVDW SH-S243N 
Revision                    : SB00
...

```

---

