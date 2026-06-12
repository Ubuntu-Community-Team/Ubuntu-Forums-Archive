---
title: "Ubuntu Studio &amp; Hardy: share /home &amp; /swap?"
date: 2008-10-25
forum: General Help
---

### Post by Steve H on 2008-10-25
I'm sure this is a daft question but here goes.

Is it possible for Ubuntu Hardy Heron and Ubuntu Studio to share my /home and /swap partitions if they are dual booting?

The reason I want this is so when I boot into Ubuntu Studio it uses the real-time kernel for production but when I boot into Ubuntu Hardy it uses the normal distro kernel.

I'm struggling with disc space and this would mean I don't have to create any new partitions.

---

### Post by lswb on 2008-10-25
Yes it is definitely possible. The swap is easy to share, just needs the appropriate entry in each /etc/fstab. /home would also need to be in both the studio and hardy /etc/fstab, and appropriate symlinks set up on each distro pointing to your /home partition. Sharing /home can sometimes lead to complications, though, if you use the same apps in both distros but with different configurations. Personally I like to let each distro have its own /home directory, and use a separate partiton for any large shared files (music, pictures, etc) that is accessible from any of the distros.

Another option you may want to consider is adding the programs you use in ubuntu studio to your regular ubuntu system, and adding the rt kernel which would be available at boot time as a grub menu option. I'm not familiar with studio so I'm not sure if this is practical.

---

### Post by fjf on 2008-10-25
Why not just using ubuntusutdio+installing the additional software you may need that is present in the regular ubuntu?.

---

### Post by Steve H on 2008-10-25
> **lswb said:**
> Yes it is definitely possible. The swap is easy to share, just needs the appropriate entry in each /etc/fstab. /home would also need to be in both the studio and hardy /etc/fstab, and appropriate symlinks set up on each distro pointing to your /home partition. Sharing /home can sometimes lead to complications, though, if you use the same apps in both distros but with different configurations. Personally I like to let each distro have its own /home directory, and use a separate partiton for any large shared files (music, pictures, etc) that is accessible from any of the distros.

Another option you may want to consider is adding the programs you use in ubuntu studio to your regular ubuntu system, and adding the rt kernel which would be available at boot time as a grub menu option. I'm not familiar with studio so I'm not sure if this is practical.

Thanks for that, I may look into that as an option a bit further (fstab thing). It was the sharing of the /home that was concerning me more tbh.

> **fjf said:**
> Why not just using ubuntusutdio+installing the additional software you may need that is present in the regular ubuntu?.

I have tried using the rt-kernel in the past for day-to-day usage and it wasn't the most stable I have used. Is the new rt-kernel safe enough for everyday use? If so, Is there any benefit? for example, playing games in WINE etc??

---

### Post by fjf on 2008-10-25
The rt hardy kernel is stable in my computer, and plays back audio perfectly.  I havent tried to game. If you want ibex, an alternative would be to install ubuntu, then add the extras in ubuntustudio and choose kernel at boot time:

[http://ubuntuforums.org/showthread.php?t=900676](http://ubuntuforums.org/showthread.php?t=900676)

---

### Post by dcstar on 2008-10-25
> **Steve H said:**
> I'm sure this is a daft question but here goes.

Is it possible for Ubuntu Hardy Heron and Ubuntu Studio to share my /home and /swap partitions if they are dual booting?
......

The only issue I have experienced with sharing /home is if there is a difference in the Gnome version between the systems you are booting.

Newer versions of Gnome can change configuration settings, which can break things when you load the older O/S with the older Gnome.

Apart from that, no problems at all and you should have a separate /home partition so it is preserved between system upgrades.

---

### Post by Steve H on 2008-10-29
Thanks for the help, guys. I'll have a go at the weekend, when I've more time. I think the boot-time choice sounds the most practical so I'll probably set that up.

I'll let ya know if I hit any probs.

:D

---

