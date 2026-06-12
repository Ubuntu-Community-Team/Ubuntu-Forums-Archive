---
title: "Strange behavior with my hard drive"
date: 2012-05-02
forum: Hardware
---

### Post by samuel.faith on 2012-05-02
I have been using Ubuntu since 8.04 on several laptops, mostly from Dell and Asus. It has been my primary choice of OS.

My current laptop is Dell Studio XPS 1645 and running on 4GB RAM. Been using it for over a year without any problem. But recently, since my upgrade to 11.04 then subsequently to 11.10 (within 2 days) I noticed sluggish performance which I put down to Unity. Two months ago, even after changing to Gnome-Shell didn't help, I was so frustrated and reinstalled Windows for awhile for my work (I needed Photoshop).

After 12.04 came out, I installed it recently and found it to be pretty stable. However, laggy performance still exists although it is not too much like in 11.10. I finally settled myself in Cinnamon Desktop as it fits my need well, and run pretty smooth without giving up GNOME (I tried LXDE, XFCE and KDE. All of them have laggy performance, and I guess I am too used to GNOME too).

Then today, I have noticed something strange about my hard drive. After the excruciatingly slow experience in my Windows installation, I put that down to the hard drive, the poor little fella that has been running for 7752 hours (according to smartmontools). I recently installed Ubuntu 12.04, and now settled into Cinnamon Desktop, and will be waiting for Elementary OS to release its Luna shell since I liked Jupiter shell a lot on 10.10 and 11.04. 12.04 seems to be pretty stable.

So today I was using smartmontools to do extended self-test on my hard drive, which takes about 2:11 hours. And also ran badblocks to check bad sectors on my hard drive. Yup, probably a bad idea, I first thought, but WTH I ran both tests simultaneously.

Surprisingly, my system performance increased during that time. No laggy browser windows tabbing, no laggy menus, everything was smooth and running as it should. Heck, badblocks finished checking and found 4 bad sectors, so I even dumped them into a flat file, which took another 1:20 hours. All during this time, my system performance was smooth. Much smoother than before, and it might be a bit slower but everything was smooth.

So what's the deal, folks? What do you reckon? Oh and I have set jbd2 to only write to the disk at every 30 minutes interval. So it's not jbd2 issue. And I already set look_ahead value to on using hdparm, since it was off by default. On or off, I don't see a noticeable improvement though.

I am intending to buy a new hard drive and dd all current partitions onto new one then replace it within my laptop. But then, current drive seems to be healthy, and I don't want to spend extra unnecessarily. If I can solve this issue, I would like to.

I am running an ATI card and proprietary drivers are installed. BIOS is updated to latest version provided by Dell.

---

