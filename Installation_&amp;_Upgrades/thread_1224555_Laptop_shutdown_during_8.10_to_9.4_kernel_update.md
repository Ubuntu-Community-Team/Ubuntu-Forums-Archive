---
title: "Laptop shutdown during 8.10 to 9.4 kernel update"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by Tigiot on 2009-07-27
First of all, excuse me for not searching extensively.

I have this old Dell Inspiron 1150 laptop that was given to me and had been running Ubuntu on it but during a kernel upgrade overnight my roommate turned it off not paying attention to what was going on.

Now I've decided to put XP back on that laptop, partially because I don't have any blank disks or any install disks for Ubuntu around and partially because my 5 and 6 year old little brothers know how to use XP better than Ubuntu as of current. The problem I'm having is that when I attempt to install XP and do a full format it never leaves 0%. When a quick format is done it installs but after removing the disk so that the install can finish the computer crashes.

My question is, is it possible this damaged the hdd? As I said, I haven't been able to attempt a Ubuntu install yet but that's my next route of action.

Thanks in advance.

---

### Post by eekie on 2009-07-27
I never get answers to my questions on this forum so I decided to take on an exemplary function.
The answer to your question about disk damage is simple. The disk cannot be damaged by a kernel upgrade.
And to be honest the capabilities of the windows xp installation disks are poor. So you better get yourself an ubuntu live cd to do the partitioning work using gparted (which is standard on the live cd).
For this you need another computer with network facilities and an empty writable or rewritable disk. 
See that you get the latest ubuntu version 9.04 just by googling ubuntu, download. Burn the image on cd and start up from the cd.
Actually Ubuntu 9.04 is much better than xp, so maybe you should install and give it a try.
Hopefully you had a separate data partition, if not any data on your old ubuntu are lost. If you decide to install ubuntu then create two partitions, one with mount point / (10 gig will do))and one with mountpoint /home (should be large enough to contain all your future data). That way you don't lose data after a crash. The system will also create a swap partition.

---

### Post by Tigiot on 2009-07-27
Thanks for your reply and I never did keep anything of value on that laptop, it was mainly used for internet browsing since it had such low capabilities.

---

### Post by wojox on 2009-07-27
Google killdisk and scrub your hard drive the do a fresh install of what ever OS you want. Works like a charm everytime for me.

---

### Post by Tigiot on 2009-07-29
Thanks, I'll keep that in mind next time something happens.

I got some more blank cds so I burned me a 9.04 disk and am installing it right now.

---

### Post by ZaHACKieL on 2009-07-30
Another solution may be downloading the Ultimate Boot CD from here:

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

It has great utilities and like 4 or 5 different programs to wipe out the HD.

If you just want a wiping software, WipeDrive is an excellent program. I don't remember if it's free but if not, msg me and I can send it to you, it's around 16MB  but one thing with this program, I've only used it making a floppy boot disk. I'm sure you can also do a CD bootable disk with it but I haven't tried that. Anyway, let me know

ZL

---

