---
title: "Help! I accidentally installed ubuntu over vista"
date: 2008-10-27
forum: General Help
---

### Post by Nerv68 on 2008-10-27
I put the live cd in, clicked install(which I shouldnt have) and now vista is gone along with all my data, and ubuntu is all that starts up.
I have a windows backup on 2 DVDs and a NTI backup on a external hard disk, I was thinking maybe I could install NTI backup now and use that. is there anything I can do?

---

### Post by Elfy on 2008-10-27
Are you sure - you need to do more than click install - you have to set up partitions before it starts to install, it has to be deliberately started.

If all you did was click the install only option on the livecd menu - it is just starting/running from the cd.

If rather than accidentally you did start the install the first thing to do is not use the drive butuse the livecd as you can at least get on line and make fuirther enquiries - [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by TeXtonyx on 2008-10-27
Assuming Vista is really gone. This method is for non-geeks.

Reinstall Vista and wipe the whole partition and install Vista
on the whole partition. 

After Vista is installed resize/shrink the Vista partition using
the Vista resize program. Suppose you drive is 120GB. If you resize
it to 90GB then you will leave 30GB for the Ubuntu installation.
Leave or make that remainder partition (30GB is just an example)
unformatted. That means it is unallocated.

Now install Ubuntu. Choose 'install to largest free space' which
means it will install to the unallocated space, in this case 30GB,
and it won't overwrite or mess with XP, and it will be "guided".

During Step 7, Advanced, of the Ubuntu live cd install, choose
install grub to the /boot partition from the drop-down menu.
That means that you will uncheck the box which says hd0. hd0
means you would write to the MBR which makes Vista depend on the
health or existence of the Ubuntu partition. My method makes each
OS standalone, so that you can boot either OS if one of them fails.
Download and burn the Super Grub cd. It's good for fixing problems.

Now, you won't be able to boot Ubuntu yet. Download Easybcd which
is a visual way of adding a boot entry for a different OS. After
downloading Easybcd to Vista run it, and add Ubuntu which should
be under "Linux" towards the bottom of the configuration screen.

It is a good idea to also add Vista to the grub menu.lst boot
option list. This duplication carries the backup concept. I've
had a problem booting Vista from the Vista bootloader (bcd).
So I booted with the Super Grub disk and selected Ubuntu. From
the menu.lst options I picked Vista which did boot Vista, even
though it had just directly failed to boot. This redundancy of
function makes your entire system more flexible and easier to
troubleshoot in case a problem arises. If and when you get around
to adding Vista to the grub menu.lst ask for instructions for
editing: gksudo gedit /etc/boot/menu.lst ,to add Vista, other OS.
This method is best for the dual boot of *Windows and Ubuntu*.

---

### Post by jason.b.c on 2008-10-27
> **Nerv68 said:**
> I put the live cd in, clicked install(which I shouldnt have) and now vista is gone along with all my data, and ubuntu is all that starts up.
I have a windows backup on 2 DVDs and a NTI backup on a external hard disk, I was thinking maybe I could install NTI backup now and use that. is there anything I can do?

oh big loss there...

---

### Post by DGortze380 on 2008-10-27
> **Nerv68 said:**
> I put the live cd in, clicked install(which I shouldnt have) and now vista is gone along with all my data, and ubuntu is all that starts up.
I have a windows backup on 2 DVDs and a NTI backup on a external hard disk, I was thinking maybe I could install NTI backup now and use that. is there anything I can do?

First things first. Breathe.

Vista may or may not be gone, but if you have backups you're fine.

First please start Ubuntu and open a terminal. Post the output of the command: df -l

---

