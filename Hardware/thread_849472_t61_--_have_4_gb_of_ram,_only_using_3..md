---
title: "t61 -- have 4 gb of ram, only using 3."
date: 2008-07-04
forum: Hardware
---

### Post by wenuswilson on 2008-07-04
I've been natively using Ubuntu for about 5 months now.
I was wondering what my processor speed was and noticed that I'm only utilizing 3gb of RAM.
I am 100% sure that I have an extra gig not doing anything (jacked my over all price up 40 bucks when I bought the laptop).
So, is there anyway to get that last gig functional?
Or, possibly, is there an error in the System Monitor.

(I'm using Gnome, if that helps anything out)

nate

---

### Post by phidia on 2008-07-04
A 32 bit OS will only see 3GB ram max. You would need to go 64 bit to use the 4GB and up.

---

### Post by wenuswilson on 2008-07-05
> **phidia said:**
> A 32 bit OS will only see 3GB ram max. You would need to go 64 bit to use the 4GB and up.


Thanks for the info. I was curious as to that as the problem.
Are there any other Linux distros that would utilize all 4Gb or am I just screwed with the 32 bit keeping me slow?
I'm partial to Ubuntu but I am fine with a switch... I'm not a fan of Mandriva though.

Nate.

---

### Post by sdennie on 2008-07-05
All 32bit kernels will be limited to around 3G of RAM unless they have PAE enabled.  You have a few options:

1) Switch to a 64 bit version of Ubuntu.  This is probably the easiest solution.

2) Use the Ubuntu server 32 bit kernel (which has PAE enabled).  This isn't optimal for desktop usage though (and, if you use nvidia, it probably won't work well for you).

3) Compile your own 32 bit kernel with PAE enabled.  I would only recommend this method for really experienced users.

4) Switch to a distro that has a PAE desktop tuned 32-bit kernel.  I'm not very familiar with other distros so, you'd have to search around to see which distros have this.

---

### Post by wenuswilson on 2008-07-06
> **vor said:**
> 1) Switch to a 64 bit version of Ubuntu.  This is probably the easiest solution.


Wait -- I know almost nothing about the difference between 32bit vs a 64bit. I thought I was only able to get a 32bit.

Appreciate the info and continuing the quest for knowledge by wondering what other distros would allow my computer to run all 4gb... Linux obviuosly.

---

### Post by sdennie on 2008-07-06
> **wenuswilson said:**
> Wait -- I know almost nothing about the difference between 32bit vs a 64bit. I thought I was only able to get a 32bit.


If you have a laptop that supports 4G of RAM, chances are very good that your CPU/chipset will support 64bit.  You can find a lot of good information about 64bit here: [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by wenuswilson on 2008-07-06
> **vor said:**
> If you have a laptop that supports 4G of RAM, chances are very good that your CPU/chipset will support 64bit.  You can find a lot of good information about 64bit here: [http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

Thanks for that link, very useful. I think I'm going to create a partition and see if I can't install a 64bit Ubuntu and test it out.








Gave the 64 a try -- not really any different, at least as speed is concerned, I might migrate to it at some point. But I have a feeling it would be too much work to reget everything I already have.

---

