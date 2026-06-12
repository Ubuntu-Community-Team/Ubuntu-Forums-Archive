---
title: "Ubuntu 6.06, Installed perfectly, now desktop will not load."
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by cokashmola on 2007-07-28
I'm brand new to Linux and really like it. I just installed Ubuntu on my laptop yesterday and everything was working great. The internet was connected, I learned lots of stuff about how to work it, all was well. Then, suddenly, my Terminal would no longer load. I looked in some threads and found a solution...so i typed the commands i saw as follows to fix it:

(logged in as root user)

apt-get update
apt-get dist-upgrade

Everything ran through as normal and completed, so i rebooted. When i entered my username and password, my cursor showed up as normal...but the window stating certain things (GNOME, windows manager, etc.) that were loading did not appear. Nothing appeared. All i had was a brown screen and a cursor.

I rebooted to see if maybe something just freaked for a second and got the same problem.

Any suggestions would be greatly appreciated!

Thanks.



By the way, I use an IBM Thinkpad 770X (yes, its old).
256mb of RAM 
about 7gb of disk space.

---

### Post by ugm6hr on 2007-07-28
> **cokashmola said:**
> By the way, I use an IBM Thinkpad 770X (yes, its old).
256mb of RAM 
about 7gb of disk space.

I wonder whether the 7GB HD space is your problem.  If you have been installing programs / updates, then I suspect you have filled your HD to the point where Ubuntu can't load now.

I had a 5GB Xubuntu installation, that went wrong when I updated OpenOffice.  So I reinstalled without OpenOffice, and have had no problems since.

---

### Post by gentine on 2007-07-28
Perhaps you should purchuse a bigger hd (or increase partrtion space)

---

### Post by davidsrsb on 2007-07-28
Look in /var/cache/apt/archive
You will probabbly see several versions of the same package. Delete some of the earlier versions (requires sudo) to recover some of your space.

---

### Post by az on 2007-07-28
> **cokashmola said:**
> I'm brand new to Linux and really like it. I just installed Ubuntu on my laptop yesterday and everything was working great. The internet was connected, I learned lots of stuff about how to work it, all was well. Then, suddenly, my Terminal would no longer load. 

Did you install or remove anything before this?

You don't need a bigger hard drive.

Try booting into recovery mode and running

apt-get install ubuntu-desktop

and then run

init 2

What happens then?

---

