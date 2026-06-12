---
title: "Windows Partitions Not Mountable"
date: 2013-04-26
forum: Hardware
---

### Post by amtur_poet on 2013-04-26
I have noticed that in the past few versions of Ubuntu, I have been unable to access my Windows partitions due to a mounting error. Usually, I was able to access one and not the other, but now I cannot access either. Here is the error message:
```
Error mounting system-managed device /dev/sda2: Command-line `mount "/media/TI106169W0D"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

```
It says that the error was caused by an abrupt shutdown, but I always shut my computer down normally, and this has been a recurring issue. Any suggestions?

---

### Post by ahallubuntu on 2013-04-26
~

---

### Post by amtur_poet on 2013-04-26
> **ahallubuntu said:**
> As the message says, Windows is hibernated, so the partition can't safely be mounted.  Why is that a potential catastrophe?  Because Windows has a journal of the NTFS filesystem, and that's hibernated, too.  Say you were able to mount the partition and change files on it.  Then you shut down Ubuntu and resume Windows from hibernation.  Now Windows has a different map of the filesystem than is correct.  The potential for massive corruption exists - although you might get lucky and fix the issues later with a chkdsk.

Solutions are simple: shut down Ubuntu, resume WIndows, then shut down without hibernating - or, you can delete the hibernation file so that anything you were doing in Windows at the point you hibernated will be lost.  (Unsaved documents lost, etc.)I'm using Windows 8; there's no way i know of to shut it down WITHOUT hibernating.

---

### Post by ahallubuntu on 2013-04-26
~

---

### Post by ArindamSaha1507 on 2013-04-28
Yup faced the same problem as I started using windows 8. The workaround that I use is to RESTART windows 8 and boot into ubuntu.

I get the same message is I shut down windows 8; turn the computer on and into into ubuntu.

---

### Post by ArindamSaha1507 on 2013-04-28
> **amtur_poet said:**
> I'm using Windows 8; there's no way i know of to shut it down WITHOUT hibernating.

Yup faced the same problem as I started using windows 8. The workaround that I use is to RESTART windows 8 and boot into ubuntu.

I get the same message is I shut down windows 8; turn the computer on and into into ubuntu.

---

### Post by prodigy_ on 2013-04-28
Well, if you're sure you used shutdown and not hibernate:
```
sudo mount -t ntfs -o remove_hiberfile /dev/sda2 /mnt # you can replace /mnt with any mount point you need
```

But I think you should run **chkdsk /f** on your Windows partition first. It's a Windows tool that checks file system for errors. You'll probably be prompted to schedule the check on the next reboot (if it's the system partition). Confirm, restart Windows and wait for the check to complete.

---

### Post by ahallubuntu on 2013-04-28
~

---

### Post by msz on 2013-06-02
I have just installed dual-boot Windows 8 and Ubuntu 12.04.2 LTS on a Dell Inspiron One 2330 and goit into this problem but even worse. No matter if I shutdown the Win8 or "restart" them straight into Ubuntu, Nautilus refuses to mount "hibernated" partition. I have also followed the above link to disable "fast start-up" and that did not help either. So I am stuck.

---

