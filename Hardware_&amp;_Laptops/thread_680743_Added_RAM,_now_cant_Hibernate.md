---
title: "Added RAM, now cant Hibernate"
date: 2008-01-28
forum: Hardware &amp; Laptops
---

### Post by fig_wright on 2008-01-28
I liked the look of Ubuntu, so installed it to an old laptop which was dual-boot Win XP and Fedora 1.9. I hadnt seriously used Fedora since 1.9 because it was rubbish on laptops. Ubuntu is great though, so I thought: *this laptop has life in it with Ubuntu - I'll add more RAM and extend its life!*

I added extra RAM to up the memory from 256MB to 512MB. Performance much better :)  But... hibernate broke :mad: . I have a 256MB swap partition, which is no longer big enough to save all the hibernate image. Looking on the forums here there are a few other sufferers, and the response is always "*use gparted to extend your swap partition*". Oh, how my Windows using friends laughed and laughed. "*Our hibfile.sys file got bigger automatically*" they said, and "*You wreck your whole system by hacking with the partition tables, we're off to the pub!*" Not so smug about my free operating system now, am I?

I am **NOT** fiddling with dynamic partition resizing on this system, especially since they are nearly all full anyway. There has to be another way. There is no way I should be expected to know in 2004 how much RAM I will have in 2008.

This [http://cns.bu.edu/~sat/satblog/archives/54](http://cns.bu.edu/~sat/satblog/archives/54) helped, and after reading [http://www.tuxonice.net/HOWTO-7.html](http://www.tuxonice.net/HOWTO-7.html) I figured I would add more swap as a file. I added a swapfile of just bigger than the extra RAM I added. Unfortunately, this results in the hibernate button disappearing from the menu. I then learnt that tuxonice is not quite the same as swsusp, and swsusp can only handle a single swap device.

Here this issue is discussed on the Kernel mailing list, indicating why people shouldnt have to jump through these hoops to hibernate: [http://lkml.org/lkml/2007/7/13/22](http://lkml.org/lkml/2007/7/13/22) (This also leads me to believe that swap partitions are no longer the best solution in linux).

I considered turning off the swap partition and running just a bigger swap file, which required me to point /etc/initramfs-tools/conf.d/resume to the first block of the file (use *filefrag -v /swapfile | grep "First block"* and add the result to *resume=/dev/sda3 resume_offset=<first block>*, then run *update-initramfs -u* but something didnt work and it all got a bit complicated and I could hear my Windows buddies starting to laugh again...)

Is it possible to get tuxonice running in Ubuntu 7.10, and will this allow me to hibernate again, and thereby join my giggling Windows friends down the pub?

---

### Post by jeffus_il on 2008-01-28
Use a swap file instead of a swap partition.

---

### Post by fig_wright on 2008-01-28
I see. That's great.

So, I've discovered that Tuxonice is actually the same thing as suspend2, which explains some things. These links are useful:
[https://help.ubuntu.com/community/Suspend2Kernel]("https://help.ubuntu.com/community/Suspend2Kernel")
[http://wiki.tuxonice.net/DistroAndHardwareSetup/Ubuntu_Gutsy_Gibbon]("http://wiki.tuxonice.net/DistroAndHardwareSetup/Ubuntu_Gutsy_Gibbon")
but they all require kernel compilation, which I'm not doing. Did enough of that in my 20's.

Has someone simply compiled the modules against the stock Gutsy kernel and put up the binaries somewhere? That would be nice...

---

### Post by articpenguin on 2008-01-28
dont you need swap twice as big as ram for hibernation?

---

### Post by fig_wright on 2008-01-30
> **articpenguin said:**
> dont you need swap twice as big as ram for hibernation?

Um, this is the point - I've added RAM and now the swap I had is too small, so I'm trying to solve this issue.

---

### Post by cdtech on 2008-01-30
> **fig_wright said:**
> Oh, how my Windows using friends laughed and laughed. "*Our hibfile.sys file got bigger automatically*" they said, and "*You wreck your whole system by hacking with the partition tables, we're off to the pub!*" Not so smug about my free operating system now, am I?

Is it possible to get tuxonice running in Ubuntu 7.10, and will this allow me to hibernate again, and thereby join my giggling Windows friends down the pub?

I'm sorry, I can't help but laugh at your story.

---

### Post by fig_wright on 2008-02-01
> **cdtech said:**
> I'm sorry, I can't help but laugh at your story.

#-o

I spent some time looking for any sign of a standard Ubuntu kernel with the Tuxonice patches compiled in, but couldnt find any. The closest thing I could find was the **Zen Kernel**, which includes Tuxonice, but also loads of other optimisations which I figured from experience were likely to break lots of stuff on my old laptop. [http://ubuntuforums.org/showthread.php?t=623874]("http://ubuntuforums.org/showthread.php?t=623874")

In the end I had to give up and resort to partition resizing. Yep, I had to take the ribbing from my Windows using chums. It's disappointing because many people simply wont risk such a procedure, and for many laptop users, without the safety feature of having "hibernate on critical low power" it's just too dangerous to use a laptop when not on AC power...

---

### Post by cdtech on 2008-02-01
> **fig_wright said:**
> 
In the end I had to give up and resort to partition resizing. Yep, I had to take the ribbing from my Windows using chums. It's disappointing because many people simply wont risk such a procedure, and for many laptop users, without the safety feature of having "hibernate on critical low power" it's just too dangerous to use a laptop when not on AC power...

I agree..

I had to repartition mine as well, seven hours to do my 250g.

---

