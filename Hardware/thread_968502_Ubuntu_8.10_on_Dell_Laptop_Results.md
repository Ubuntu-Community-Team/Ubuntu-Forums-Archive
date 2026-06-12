---
title: "Ubuntu 8.10 on Dell Laptop Results"
date: 2008-11-02
forum: Hardware
---

### Post by syga on 2008-11-02
Installed 8.10 a few days ago on my Dell Inspiron 1501 laptop. The biggest complaint I have with any Linux distro is that my hard drive is always active, noisey and annoying. So, I gave the new Ubuntu a shot...

I used the ext2 filesystem.

I've made a few minor changes from the out of the box configuration.

I had to use fwcutter to get my broadcom wireless card working. The default wl driver did not work.

Installed Sharp-Fonts

I enabled laptop-mode. Adjusted the cpu to powersave and to the minimum frequency.

Adjusted the lcd backlight to 75 instead of the default 100, so its dimmer.

Removed unnecessary default applications. 

Disabled most of the logging.

The end result is that the hard drive is quiet, it has very low activity, at least 40% less, as compared to all of the other Ubuntu versions and distros that I tried. 

It runs cooler. The fan does not turn on as much as compared to the other versions.

So far the results have been favourable...

---

### Post by ssneff on 2008-11-02
This is comforting to hear!  I am in process of partitioning for 8.10 on a Inspiron 1520 that is presently running Vista.  I was having questions about what file system to use for partitioning.  You answered that one.  Can I ask how you did your partition as far as the space is concerned?  I am trying to get this working yet tonight.  How long did the partitioning take?  I am using Gparted.  I do not want anything more to do with Vista.  Can I completely get rid of it or what?  Please bear with me...I am an EXTREME NEWBIE !

Thanks
Steve

---

### Post by scotland42 on 2008-11-02
If you want to get rid of Vista all together, just boot to the live cd and click on "Install".  As a self proclaimed "Extreme Newbie", don't worry about partitioning it yourself.  Just let Ubuntu install how it wants to (which uses EXT3, not EXT2).

The problem that I am having with my Latitude D800 laptop, is that the status lights (Numlock, Capslock, Wireless, Power light) and the volume buttons don't work as of version 8.10.  It seems to be a kernel problem, because as soon as grub boots Ubuntu, the lights go off.  Does anybody have any ideas?

---

### Post by ad_267 on 2008-11-02
ssneff: Keep Vista for now and dual boot, make sure you get used to Ubuntu before making the complete switch.

Do a defragment in Vista before resizing the Vista partition.
If you're comfortable with partitioning then set up a separate partition for /home. 
How big is your hard drive? A default Ubuntu installation takes up about 4GB, usually 10 or 20GB is plenty, and then use however much space you want for all your stuff in /home.
Also make sure you remember to create a swap partition, which should be about twice the size of your RAM.

If you're new you could stick to the guided resize option in the installer which takes care of everything.

---

### Post by ssneff on 2008-11-02
ad...my hard drive is 120G. Sounds like the safest thing for me to do as a newbie is to let ubuntu do all the sizing for me for now.  I am pretty sure I will end up getting rid of Vista all together..I am that tired of it...but I will wait til I understand things better.  I dont want to be dead in the water for any length of time.

Thanks for everyones help...another reason to leave the Windows world and come over to the Ubuntu side !  :)

Steve

---

### Post by ad_267 on 2008-11-02
> **ssneff said:**
> ad...my hard drive is 120G. Sounds like the safest thing for me to do as a newbie is to let ubuntu do all the sizing for me for now.  I am pretty sure I will end up getting rid of Vista all together..I am that tired of it...but I will wait til I understand things better.  I dont want to be dead in the water for any length of time.

Thanks for everyones help...another reason to leave the Windows world and come over to the Ubuntu side !  :)

Steve

Exactly, you don't want to find that you have some incompatibility with Ubuntu after wiping Vista, or that you need to get something done quickly and you have no idea how to do it in Ubuntu.

Good luck and have fun with Ubuntu! It's well worth the switch if you just have a bit of patience to get used to the differences. I did a dual boot with XP for a while but got rid of XP pretty quickly.

---

### Post by syga on 2008-11-02
> **scotland42 said:**
>  don't worry about partitioning it yourself.  Just let Ubuntu install how it wants to (which uses EXT3, not EXT2).


There's several file systems that are available on installation, ext2,ext3,fat,reiser and a few others.

I picked ext2 because it non journaling and writes to the hard drive less.
I know there are pros and cons to ext2, ext3 and the others. 
If I had a desktop where the tower sits on the floor and I can't hear the hard drive, I would have picked ext3. On my laptop, where I'm close to my hard drive, I want it as quiet as possible.

---

### Post by ssneff on 2008-11-02
Well, I tried to execute my plan but when the partitioner started or tried to start partitioning after I chose the "guided" method, it came up and said the partitioning could not be done.  I de-fragged before I booted to the Ubuntu cd too.  Any ideas?

---

### Post by ad_267 on 2008-11-02
That's weird. Did it say why it couldn't partition?

You could set up the partitions manually using gparted which is on the live CD under System - Administration - Partition Editor. It should be pretty self explanatory how to use gparted, and it only applies changes when you click apply, so you can play around and just reset everything to start again.

You can make an ext3 partition for your root directory and then an extended partition with a linux swap partition in it. If you want you can have a separate partition for /home. Then in the installation select manual partitioning and select your new partition to be mounted at / and your home partition mounted at /home if you have one.

Have a look here for partitioning schemes: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
The dual boot guide on that site is also useful: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Also, another option if gparted has problems resizing your vista partition is to use Vistas built in partition resizer, which is explained at [http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by ssneff on 2008-11-02
> **ad_267 said:**
> That's weird. Did it say why it couldn't partition?

You could set up the partitions manually using gparted which is on the live CD under System - Administration - Partition Editor. It should be pretty self explanatory how to use gparted, and it only applies changes when you click apply, so you can play around and just reset everything to start again.

You can make an ext3 partition for your root directory and then an extended partition with a linux swap partition in it. If you want you can have a separate partition for /home. Then in the installation select manual partitioning and select your new partition to be mounted at / and your home partition mounted at /home if you have one.

Have a look here for partitioning schemes: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
The dual boot guide on that site is also useful: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Also, another option if gparted has problems resizing your vista partition is to use Vistas built in partition resizer, which is explained at [http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

I tried running the partitioner from System - Administration - Partition Editor....it told me I could not have more than 3 primary partitions and would not let me do what I wanted. I didnt know how to proceed so I just stopped messing around before I screwed something up.  Getting late now...brain is tired.  I will be checking here tomorrow from work.

Thanks again for your help ad_267...I really appreciate it.    Hope I am not being too much of a moron.  Have a good night.  Talk to you tomorrow I hope.

---

### Post by ad_267 on 2008-11-02
That's why you make an extended partition and put the swap partition inside that. Then if you have a vista partition, ubuntu partition, and a home partition you only have 3 primary partitions.

Feel free to ask any questions and don't be afraid of sounding like a moron, people here are pretty helpful and everyone was new to this once. Installation is usually the hardest part.

---

