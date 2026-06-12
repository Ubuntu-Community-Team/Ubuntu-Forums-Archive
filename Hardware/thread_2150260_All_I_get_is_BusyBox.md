---
title: "All I get is BusyBox"
date: 2013-05-31
forum: Hardware
---

### Post by sqrooup on 2013-05-31
My laptop (Dual boot Ubuntu/Windows 7) has developed a bit of a fault;
in Grub:
Ubuntu goes to BusyBox
Ubuntu Recovery Mode also goes to BusyBox
Previous Versions of Ubuntu also goes to BusyBox
MemTest says no problem with memory
Windows hangs after log in
But, Windows Safe Mode works

I have tried to see if it is a disk error, both in Windows Safe Mode (could not run chkdsk for some reason) and a spare LinuxMint 12 disc (this tells me it is unable to mount the partition, missing codepage?)

Have tried installing the LinuxMint, it comes up with an ubi-partman failed with exit code 141 error,

I wish to get this this laptop back to normal, scrapping the Windows partition, but my other PC is a Xubuntu, I have an Ubuntu.ISO downloaded,  but no way of burning it to CD/DVD/USB stick.

Please help on ether.

---

### Post by gordintoronto on 2013-05-31
What version of Ubuntu?

If both Windows and Ubuntu have problems, it sounds like a hardware failure.

I'm astonished that you can't burn a USB stick. Have you installed unetbootin?

---

### Post by varunendra on 2013-06-01
> **sqrooup said:**
> 
Ubuntu goes to BusyBox
Ubuntu Recovery Mode also goes to BusyBox
Previous Versions of Ubuntu also goes to BusyBox
MemTest says **no problem with memory**
Windows hangs after log in
But, Windows Safe Mode works
....
....
Have tried installing the LinuxMint, it comes up with an **ubi-partman** failed with exit code 141 error..
Indeed sounds like a dying hard disk.
The first thing you should do before booting your computer again is to prepare a boot cd/usb on another computer that allows you to do that (or try unetbootin in the windows safe mode). Then boot with it, save all your important data to an external drive to be safe. Then try whatever you wish to.

> **gordintoronto said:**
> I'm astonished that you can't burn a USB stick.
Maybe because safe mode isn't allowing many things..? In any case, I think it would be safer to use that drive as little as possible until he has a bootable cd/usb and an external drive ready for backups.

---

