---
title: "Problems with DVD and CD drives..."
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by alexhughes on 2007-01-21
OK, recently installed Ubuntu 6.06 over the weekend, and everything's going swimmingly, until I realise my CD/RW and DVD drives are acting up. Two separate problems, may (or may not) be connected.

1. The CD/RW drive works OK for a few ticks, then ejects the CD. It's a Mitsumi CR-4804TE, and I've noticed this problem being mentioned elsewhere in the forums for this drive, but have found no absolute solution. Haven't even tried burning anything with it. It worked alright before, indeed this is the drive I installed everything on. It's the same problem with audio or data CDs.

2. The DVD drive is apparently recognised by Ubuntu (it appears in the 'Places' menu when there's a disc in it, but refuses to do anything. Upon inserting a disc it opens up the CD/DVD creator menu, but properties claim there's essentially nothing there. It's a Matshita DVD-ROM SR-8585F, and as before, this problem occurs whether it's an audio CD, CD-ROM or DVD.

Any help? I'm relatively new to all this, so please spell out anything I need to do or check.

Thanks,

---

### Post by teaker1s on 2007-01-21
I don't know the specific answer to your issue, but I have had many DVD and CD rom drives complaining of no media and odd behavior and found the drive manufacturer had updated firmware for them

---

### Post by alexhughes on 2007-01-22
I'm not sure that that's the problem - they both worked without any problems on WinXP before this...

---

### Post by alexhughes on 2007-01-23
OK - a small development... I discovered (through using VLC) that I can mount my DVD drive, using

> sudo mount /dev/dvd /media/dvd

instead of the /dev/hdd which is where Ubuntu thinks my DVD player is. As a result I can play DVDs and read CD-ROMs, but can't play Audio CDs with it.

This doesn't completely solve my problem though - is there

1. any way of setting this as the default when I put a disk in, rather than run around typing in mount/unmount every time.

2. is there any way of fixing this overall...?

---

### Post by alexhughes on 2007-02-04
Help! Still stuck with a not-properly-functioning DVD drive and a not-properly-functioning CD drive. Any thoughts? ...anything?

---

### Post by Aifel on 2007-02-04
Try going to System--->Preferences--->Removable Drives and Media
Make sure your DVD drive is set to automount for conviniece, and you may also want to mess around with some other settings in there too.

---

### Post by alexhughes on 2007-02-07
Nope - that ain't doing it. Any other thoughts?

---

### Post by jdackle on 2007-02-08
On the automatic dvd mounting/unounting, have you tried to edit your /etc/fstab file?

-if not, go there, look for the line that starts with "/dev/hdd" and replace it with the apropriate path to your DVD player.

---

### Post by alexhughes on 2007-02-08
Had a look at the /etc/fstab - no record for the dvd at all (although I've recently reinstalled Ubuntu). 

I've added:

```
/dev/hdc     /media/dvd     iso9660     noauto,user,ro     0     0
```

to /etc/fstab, but still no joy. As far as I can tell, Ubuntu knows there's a disc there, can recognise what it is (DVD, CD-R etc), puts an icon on the desktop and in the Places menu and that's about it. I can mount it with 

```
sudo mount /dev/hdc 
```

and view the data, and I can get DVD software such as VLC to play DVDs, but it's just not automatically kicking in, and it doesn't pick up audio CDs at all... Clicking on the icon on the desktop just brings up CD/DVD Creator, as though it was a blank disc.

---

### Post by jdackle on 2007-02-08
**1.**
 Well, "/dev/hdc" usually refers to the "first" CD/DVD drive on the system (Primary Master) which on your system I assume is the CD-RW drive...?
The DVD (Primary Slave or Secondary Master) will then be "**/dev/hdd**". You've said before that was the system default assumption and it wasn't working. However that may be because the device's file (/dev/something) was wrong as you seemed to me to have assumed, but it might also be because the options were wrong. That's why I advised you to only change the device-file as VLC was giving you and keeping the original options at the same time.

**2.**
A DVD filesystem is actually an UDF one by default, NOT ISO 9660!! You can also use the lines below safely with a CD drive as CDs can also use a UDF filesystem:
```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
```
UDF is the first type of fs the system will look for in the CD/DVD, then ISO 9660. This setup works fine in recognizing all kinds of media in my system, including audio CDs.
But I'm still using Ubuntu **6.06** here...

**3.**
I forgot to mention... :oops: 
You'll have to **remount your drive(s) in order for the changes in your /etc/fstab to take effect**!!! That file is used to mount filesystems on bootup, so it will be automatically done for you, surpasing that annoying mounting/unmounting routine...
You can remount all media filesystems (to test that it's working) with the commands:
```
sudo umount -a
sudo mount -a
```

Good luck!

---

### Post by alexhughes on 2007-02-09
Thanks... but that seems to have made things a tad worse.

now neither drive appears at all when I put a disc in the drive... although I can access the data via the terminal. Audo CDs don't work at all on either drive.

Also, don't know if it's a quirk of the system, but I'm pretty sure my DVD is the primary drive and my CD-R/W is the secondary.

---

### Post by jdackle on 2007-02-09
Sorry... :oops:

I can't help (or harm!) anymore then. That was about all I could think of. :(

---

### Post by jdackle on 2007-02-09
Wait, I remembered something!

Try accessing your DVD drive with VLC and while you're at it, type:
```
cat /etc/mtab
```

/etc/fstab lists the filesystems to load at bootup.
/etc/mtab lists the FSs currently mounted.

So, if you look at /etc/mtab when VLC is using the drive (and hopefully correctly mounted), you may catch the proper way to mount that drive and copy-paste it into /etc/fstab so that it becomes the default way for your system to mount it. ;)

Then again, VLC might be doing something more to correctly access your drive, so this may end up in nothing. :(
Still, you could try...

---

### Post by alexhughes on 2007-02-10
Since my earlier reply I rebooted, and it all seems back to (not-properly-functioning) normal.

Tried jdackle's suggestion above - still no joy, I'm afraid. Nothing dvd-related in the /etc/mtab, as far as I can tell... here's the response:

```
/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-28-386/volatile tmpfs rw 0 0
/dev/hda3 /home ext3 rw 0 0
/dev/sda /media/NUMBERTWO vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0

```

---

### Post by jdackle on 2007-02-10
You're right, nothing there seems to concern any cd/dvd drive.. (I'm suposing your /dev/sda dirve is either an usb flash disk OR a Windows harddisk with a SCSI interface; might be one of your cd or dvd drives, but the vfat fs says it's not..)

So if you got that while VLC was successfully reading your drive, then it's because VLC is NOT even mounting the drive to gain access over it. So no luck there. :(


But as you are reporting the drives are being recognised again, I'm assuming your system is mounting the drives in a different way than mine.
I'm still using Ubuntu 6.06 LTS (Long Term Support) and will update only at the next LTS release.
If you're using 6.10 your media drives may be mounted differently, WITHOUT any refference to them in /etc/fstab. But you may try and check if that's normal or not in 6.10...

Keep the faith! ;)

---

### Post by mikeyc45 on 2007-02-12
I've had the same problem since an update from 2.6.15-26 to 2.6.15-27 in 6.06 LTS.

Linux has had problems with removable media since the beginning.  I started with the first release of Caldera and have used Slackware, Red Hat, SuSE, Debian, Knoppix, Fedora, and now Ubuntu.  All with varying success using removable media.  Ubuntu had been the best so far.  This is one area where M$ Windows far outshines Linux.  And this is what an operating system is all about - interfacing to the hardware.

As I stated above, I lost my dvd drives when I updated from -26 to -27.  Everything was working fine in -26.  I updated to -28 hoping the problem in -27 might be fixed, but instead lost sound and all my scheduling in Mythtv.  I tried booting with -26, but the nVidia module puked, stating there was a mismatch between it and the kernel.

I'm currently booting -27 and using W2k when I need to write a dvd.  Unfortunately this precludes creating any video dvd's using DVDAuthor.

My computer's specs:

GA-7VT600 1394 Gigabyte MB
AMD Athlon 2500+ CPU
1 Gb PC3200 RAM
nVidia GeForce MX440 AGP graphics card w/128 Mb
1.44 Diskette Drive
Seagate 160 Gb IDE HD 
  Partitioned with primaries for W2k FAT32, Boot EXT2, Root EXT3, and extended w/Swap and LVM JFS
Seagate 300 Gb IDE HD 
  One primary partition LVM JFS
Plextor PX-708A DVD rewriter
Liteon 1693S DVD rewriter

If anyone knows a good way to get back to -26, I would really appreciate it.  Possibly a way to get back to the proper nVidia module would solve the problem.

If there's anything I can do to help with this issue I'd like to get involved.

---

### Post by d_yat on 2007-08-04
Hey there. So my parents PC has the same 2 drives as you (Mitsumi CR-4804TE and Matshita DVD-ROM SR-8585F). Basically I've been having the same problems, so I was wondering if you (or anyone) knew if this problem had been resolved yet?

---

### Post by alexhughes on 2007-08-05
> **d_yat said:**
> Hey there. So my parents PC has the same 2 drives as you (Mitsumi CR-4804TE and Matshita DVD-ROM SR-8585F). Basically I've been having the same problems, so I was wondering if you (or anyone) knew if this problem had been resolved yet?

Nope - still the same problems with both!

---

### Post by jdackle on 2007-09-15
> **mikeyc45 said:**
> If anyone knows a good way to get back to -26, I would really appreciate it.  Possibly a way to get back to the proper nVidia module would solve the problem.

If there's anything I can do to help with this issue I'd like to get involved.
I think I remember there has been a problem with upgrading from  kernel -26 to -27 in Dapper. There was a thread about it and all... It was not just about the nvidia drivers, but it affected them as well.
Try doing a search in the forum, possibly in the "Installing & Upgrade" board, for it... ;)
I'm using -29 now but never had any problems with my drives...

> **alexhughes said:**
> Nope - still the same problems with both!
Well... You've been patient with me... trying all them crazy ideas of mine before... So I thought I'd give you another one! lol
Have you tried contacting the developpers of VLS...? This is probably and advice NOT to be given but... I don't know how busy and/or "accessible" they are... But if you talk to them informally, maybe on some irc chat that might be available out there... clearly stating you do *not* need to know how to *program the access* to your drive, but rahter **what mounting options will work correctly**... AND they're not too busy answering questions about THEIR software... ;)

---

