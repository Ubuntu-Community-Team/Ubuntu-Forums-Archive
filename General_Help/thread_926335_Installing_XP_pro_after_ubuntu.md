---
title: "Installing XP pro after ubuntu?"
date: 2008-09-21
forum: General Help
---

### Post by VGF on 2008-09-21
I have a Dell Inspiron 1420, which came pre-loaded with Ubuntu.  I recently got a copy of Windows XP Pro, but when i get it in the drive and start up, the system runs a bit and i'm told that no hard disk drive was detected.  Do I need to format my hard drive first? Or is there an easier way around this?  If I need to format, how would I go about doing that?

---

### Post by niteshifter on 2008-09-21
Hi,

The 1420 comes with a SATA hard drive, which XP can't deal with without finding and loading drivers for - a major PITA. Then the next problem will be after installing XP, Ubuntu will seem to have disappeared (and may actually do so if you're not careful with the Win installer). It's correctable, but again, a PITA.

What you can do is install XP as Virtual Machine, via VirtualBox / VMWare.

Myself (also a 1420n owner) I used VirtualBox. XP installed easy and works well. Should VirtualBox look good for you, the OSE version in the repositories does not support USB. The PEUL (Personal Use and Evaluation License) version does support USB, available via VirtualBox's web site.

---

