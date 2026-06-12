---
title: "Repartitioning..15 hours???"
date: 2009-09-15
forum: Installation &amp; Upgrades
---

### Post by john_t67 on 2009-09-15
I'm installing ubuntu to my Compaq laptop. 
Going through the repartitioning process, after 15 hours, I had to abort the process in order to use the computer for other things.
Is this normal to take so long?
This is a winXP laptop, 20 gig HD, 512Meg ram (about 6 yrs old)
Trying to use Ubuntu's repartitioning tool so I can dual boot.
Should I start over or Could something be wrong?
Thanks

---

### Post by Copernicus1234 on 2009-09-15
Umm no. :)

No idea what is wrong but of course its not supposed to take hours to re-partion it. Ive never been a fan of Compaq myself since their stuff never works correctly, but in this case I doubt its the hardware.

---

### Post by wojox on 2009-09-15
Run the Windows defragmentation tool a couple of times.

Then look here:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Mark Phelps on 2009-09-15
Having done partition resizing on a more "modern" (3-years old) tablet PC running a Centrino processor and 2GB of RAM, I can say that partitioning CAN take a long time.  It took me several hours to expand a single 30GB drive.  GParted appeared to do everything twice -- once in simulation mode, and then a second time for real.

But, that said, 15 hours is a really long time!  

At least with the GParted LiveCD, you have the option to drill down through the menus and actions to see the details.  It doesn't give you progress within the individual steps, but at least you can see it moving from one step to the next.

You might try that and see if it's hanging in the beginning or actually progressing through the steps.

---

