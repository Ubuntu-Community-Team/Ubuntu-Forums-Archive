---
title: "Toshiba L300 Slow Boot Time"
date: 2009-04-22
forum: Hardware
---

### Post by freakofwar on 2009-04-22
Hi there all. I have been a user of Ubuntu for a couple of years now.

Recently I purchased a new laptop, the Toshiba L300-20D. I have Jaunty installed. I have everything working apart from one thing which has been annoying me.

When I start up my laptop it goes through the grub loader screen, and then the next screen which says booting hard drive and starting up, which should then in turn lead on to the usplash loading screen. In between the last 2 screens I mentioned there seems to be a pause of about 10 seconds, in which it is just a black screen. I'm not sure if this is normal or if there is indeed anyway to reduce the time. I did not previously have this problem with my old laptop.

Any help would be most appreciated.

Many Thanks

---

### Post by folgado on 2009-04-27
I have the same problem with my Toshiba A300. He takes 60 seconds to boot. Too much time. Can anyone help me.

BR

---

### Post by folgado on 2009-04-27
Here is my Bootchart. Only after 20 secs the computer iniciates.

BR

---

### Post by freakofwar on 2009-04-28
I am still stuck on what the problem might be. As i am sure windows does not have this problem on this model. Any one out there have any ideas??

---

### Post by freakofwar on 2009-04-30
Could it possibly be a problem with the bios? Maybe it needs an update? How would you go by doing this through ubuntu as i have never had any experience other than through windows.

---

### Post by tuxpenguin on 2009-05-31
*Bump* 

I have the same problem. My A305-S6916 has 4GB of RAM and a Core 2 Duo. There's no way this is normal. My family's 3 year old machine [which I installed Ubuntu on after it's Vista install died] boots much faster than my brand-new laptop, even using EXT4.

What happens on this machine is strange. I will select Ubuntu in the boot menu, then I will get the normal "booting from [hard drive partition], ext3" screen, which on my family's PC only displays for a fraction of a second, but on my laptop will take nearly a minute. Anyone get further solving this than I?

---

### Post by danlea on 2009-08-24
Bump for this.  Toshiba A300-2C5 here - there's a fair wait (not thirty seconds, but still more than it should) between "Starting up" and "Loading, please wait".  Could it be due to the hard drive partitioning (the laptops come with three - one small one for the restore procedure, the vista one, and the rest as data, including the restore data).  I shrank and moved these over so that the ext3 partitions could be put together in the latter half of the hard drive.

---

