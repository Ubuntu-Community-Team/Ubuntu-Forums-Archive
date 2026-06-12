---
title: "I broke X server from boot"
date: 2009-08-10
forum: Installation &amp; Upgrades
---

### Post by OhBooHooTu on 2009-08-10
Quick history - 
Old, working system had 8.1 running from random partitions on two disks. (unused Windows and Mepis on other partitions) One started making bearing noise, so time to consolidate.

New disk, using gparted put Ubuntu root on sdb1, created extended partition for swap and /home. It booted into this config, but other drives were still in the system and wanted to clean up, so started messing with fstab. Apparent mistake.

New fstab mounts sdb1 as /, sdb5 as swap and sdb6 as /home. 

I cycle power, the boot starts, Ubuntu splash screen shows, text continues to scroll, then dumps to a text/blue screen with

"Could not start the X Server (your graphical environment) due to some internal error. Please contact your system administrator or check your syslog to diagnose. In the meantime, this display will be disable. Please restart GDM when the problem is corrected."
Then it drops to command line login which generally works (I can get in).

As far as I can tell, /var/log/syslog was last written a week ago, so has nothing useful (did I somehow turn it off?)

I am running 8.10 2.6.27.14 on a generic Intel DuoCore thing.

How do I start to troubleshoot this?

My experience - persistent Ubuntu user, no code knowledge. I can follow linux directions, but have little knowledge of what I am doing. 

OBTW, I am able to still run from a cd I built with remastersys from the working system.

Help!!!
thanks

---

### Post by arky on 2009-08-10
Press Control + Alt + F1 

and login with your username/password.

Then run this command to reconfigure your X server

sudo dpkg-reconfigure xserver-xorg

---

### Post by OhBooHooTu on 2009-08-10
Thanks for the response. I am not dragging my feet, I just keep getting stuck after entering the dpkg command. I get the next response, asking if I want to "Use kernal framebuffer  device interface" but then the keyboard locks up, responds only to ctrl-alt-delete. I'm working on it (but any suggestions...)

Thanks,
jeff

---

### Post by OhBooHooTu on 2009-08-10
A bit more info. Instead of executing the instruction, I tried to create a new directory for a mount point (not sure what I was going to do with it, just looking for things I could do).

me> sudo mkdir /newboot
mkdir: Cannot create directory /newboot. Read-only file system.

So somehow it thinks the files system is read-only?

Trying to ignore that, I tried some options for dpkg-reconfigure that I thought might reduce the wedging. --terse didn't help, neither did --force.

---

### Post by OhBooHooTu on 2009-08-11
OK, I'm an idiot.

And thanks arky for the suggestion anyway - it started me rolling the right way. Since I was locking up on the dpkg command, and then got the 'read-only' message I mentioned, it slowly registered that having a read-only file system was probably a bad thing, and certainly not what I intended. So by using ctrl-s to catch some of the messages scrolling past during the early boot sequence, I saw that when mounting my drive, it did not understand the option "default" in the fstab entry.

Of course not. The option is 'defaultSSSSS'. OK, perhaps just one "s" and it is lower case, but I figured if I emphasized it, I might remember next time.

Fixed that, fixed everything. So far.

Thanks!

---

