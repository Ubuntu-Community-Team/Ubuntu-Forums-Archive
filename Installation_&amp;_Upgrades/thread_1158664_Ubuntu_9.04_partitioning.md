---
title: "Ubuntu 9.04 partitioning?"
date: 2009-05-13
forum: Installation &amp; Upgrades
---

### Post by coldcut on 2009-05-13
Hi you guys

I'm going to be installing Ubuntu 9.04 on my computer on Saturday and I was wondering how I should partition my harddrive for optimal performance and so it will be easy to upgrade every 6 months. I will be compiling the kernel and will be programming alot in Python. 
I have two HDD's.
**[HDD1=500gb - 2 partitions]**
55,18gb where I am going to install Ubuntu
410,57gb where I keep all my videos
**[HDD2=320gb]**
Where I keep my music, pics etc.

As you can see I don't really need a big /home because I have about 730gb for my stuff.

So my question is: How should I partition my 55.18gb partition?

Kind regards,
Coldcut ):P

P.S. Is ext4 the way to go or what?

---

### Post by Electron on 2009-05-13
Once you do your partitions (protect your videos and pics partitions)go and install in the 55 GB. Swap should be 1.5 times your Ram and home whatever Ubuntu choose by default.
Ext4 is not quite ready yet if you want something stable.

---

### Post by coldcut on 2009-05-13
Yeah I'm gonna install Ubuntu on my 55,8 gb partition. I was merely wondering if I should create extended partitions like: /boot, /usr, /data or something like that?

---

### Post by coldcut on 2009-05-14
can nobody lend a helping hand?

it would be much appreciated :D

---

### Post by fainsleep on 2009-05-23
**Short answer:**  
    If I was in your shoes, I would set a root ('/') partition at about 12 gigs, a home ('/home') to about 5 gigs, and set a swap at 1.5 time your amount of RAM (**however I rarely use that much swap since I have 4 gigs of RAM, and therefore set mine at 1.5 gigs because even though the system will not depend on the swap much because of the large amount of available memory, I think some programs depend on/require the swap space, google around to be sure)
[B]
Detailed explanation (for reference):[/B]
    What I did on my system was set a separate partition for the root ('/') and the home ('/home').  The root is recommended to be around 8-10 gigs from what I've read around (its current size for me is around 3.5 gigs) but I would set it at 12gigs to be on the safe side, especially if you are going to be using the ext4 file system where partition resizing is potentially dangerous for the time being.  For the home partition I used everything left from the available space after swap, ect.  The home partition is so big because it will be where an average user stores their music, pictures, videos, ect.  It is on a separate partition because it keeps all of your settings, which is very important if you have to reinstall for some reason ( I hate re-themeing for example) It is also where the users Desktop is located (where I store recent downloads) Since you in particular store all of your music and other data on different partitions/hard drives, you are right in thinking that you will not need as much space, but I would leave 5-10 gigs for new downloads anyway and of course your settings.  
    On my other computer I also set up another 10 gig partition labled as "linux backup" where I use the tool Simple Backup ('sbackup' in the repositories) naturally to store backups.  Since the tool compresses using tar the entire system backup (excluding /procs, /dev, ect) came to be only 1.7 gigs you could settle for more depending on how often you want to backup your system or how many successive older copies you want to store.  But once again since you specifically are using several harddrives, it might be better to store them on another hard drive all together (in case of drive failure).

**Other thoughts:**
    I think ext3 is still used as the default file system in 9.04, so if you want to use the ext4 make sure it is selected or manually select it yourself at partition configuration time.  Also make sure that if all of your hard drives are connected when you install, that you install the bootloader ont he correct hard drive that you want.  Find it before the end of the install under the advanced button.

---

