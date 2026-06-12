---
title: "[SOLVED] Can't boot to Hard Drive OR Floppy"
date: 2006-12-12
forum: Hardware &amp; Laptops
---

### Post by altonbr on 2006-12-12
Hey guys,

I have an interesting problem here. I'm trying to install Ubuntu over my Grandmothers Win2k system but the computer can't seem to boot to the CD. I've ran into this problem MANY times over my career, so I always have Smart Boot Disk handy, but the computer can't even read that!

I guess it's an old IBM workstation (sporting a Pentium 3 and other older hardware) and has a network BIOS loader.

I'm not new at basic repairs to PCs but I've never worked with a Workstation that has this kind of security feature built into the BIOS (can't boot to CD or Floppy)

This is what, (I believe the BIOS is), has as a menu. (What I have underlined, is what is currently selected):

> [SIZE="3"][B][CENTER]Intel Boot Agent Version 3.0.04
Setup Menu[/CENTER][/B][/SIZE]
**Network Boot Protocol** (_PXE_|RPL)
**Boot Order **(_Try local drives only_ | Try network first, then local drivres | Try local drives first, then network | Try network only)
**Show Setup Prompt** (_Enabled_ | Disabled)
**Setup Menu Wait Time** (_8 seconds_ | 2 seconds | 3 seconds | 5 seconds)
**Lagacy OS Wakeup Support **(_Enabled_ | Disabled)

As you can tell, there's not a lot going on there. I saw a post on LinuxQuestions.org about the same problem, but it was unanswered.

Does anyone know how to bypass this or update the firmware to a newer version? Thanks.:-k

---

### Post by altonbr on 2006-12-12
Sorry guys!

I just found out that to get into the _real_ BIOS, you must press F1 repeatedly and then you can change the Boot Sequence.

Sorry! I hope this helps someone in the future.

---

### Post by frup on 2007-05-09
Thank You!!!!!

---

