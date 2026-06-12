---
title: "Grub Boot Loader question"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by Erdo on 2009-08-10
Hi guys,

Setup is as follows:
(320gb) Windows XP
(320gb) Ubuntu 8

I'm using the Grub boot loader. Want to wipe XP and install Windows 7. Can I just unplug the ubuntu drive, run the Windows 7 installer and format/install over the Windows drive, plug in the Linux drive and be on my merry way or will that not work?

Just basically need confirmation that formatting/installing on the Windows drive won't effect the grub boot loader on the linux drive?

Or if it does, what should I do to rectify the issue?

Hope this makes sense,

Thanks :)

---

### Post by merlinus on 2009-08-10
If grub is installed in the mbr of your linux hdd, then no change will be necessary.  If installed on the mbr of the win hdd, then you will have to restore grub, but this is very easy.

All things being equal, installing 7 over xp in the way you describe should not present any problems with your current setup.

---

### Post by raymondh on 2009-08-10
As merlin said ... it depends on where GRUB is installed.  Should you lose GRUB after installing win7, you can easily [recover/re-install]("http://ubuntuforums.org/showthread.php?t=224351") grub.

---

### Post by Erdo on 2009-08-10
Yeah GRUB is on the MBR of the Linux drive and yes it's two separate drives :)

Perfect, just confirmed what I suspected.

Thanks for the help guys, seriously appreciated.

---

### Post by raymondh on 2009-08-10
> **Erdo said:**
> Yeah GRUB is on the MBR of the Linux drive and yes it's two separate drives :)

Perfect, just confirmed what I suspected.

Thanks for the help guys, seriously appreciated.

Excellent.  Happy Ubuntu-ing :)

---

