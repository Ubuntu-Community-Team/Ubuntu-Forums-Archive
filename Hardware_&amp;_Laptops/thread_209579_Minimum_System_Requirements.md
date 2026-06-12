---
title: "Minimum System Requirements"
date: 2006-07-05
forum: Hardware &amp; Laptops
---

### Post by roxics on 2006-07-05
My mom has an older computer running an AMD Duron 800Mhz on 64MB's of PC100 RAM and an old 8gig hard drive that dates back to the era of Pentium 200Mhz machines (slow and loud).

I had installed WindowsXP home on there and it worked fine, but slow. But this was also when she had 128MB's of RAM. The other day her system crashed on her and after some troubleshooting I discovered one of her two 64MB sticks of RAM had gone bad. So now she is just running on one. 

I tried running the ubuntu 6.06 liveCD on her machine and it said it was loading the kernal but then just never went anywhere. I blindly assume it's because the OS needs more RAM to run. However we did boot back into Windows XP home and that did run. But she called me later to tell me she stopped using it because it kept freezing up on her. So I assume that's also because of the RAM.

I was curious if I was right about the minim ram requirements and that's why the ubuntu liveCD didn't run? And if so would Xubuntu work any better?

---

### Post by IYY on 2006-07-05
64 MB of RAM is not enough for even the Xubuntu liveCD to run smoothly. The Ubuntu/Kubuntu liveCD doesn't have a chance (and even if you install them, Gnome and KDE will be too slow to use). You can try the Xubuntu liveCD, but I don't think it will work well enough.

Your options are the following:

1. install Xubuntu from an alternate (non-live) CD.
2. use Puppy Linux or Damn Small Linux, both of which will run nicely on that hardware.

---

### Post by roxics on 2006-07-05
I guess option 3, the best option of all would be to buy more RAM and just run ubuntu. Just need to figure out where I can get PC100 ram locally and how much it will cost.

So what is the minimum amount of RAM needed to run the liveCD?

---

### Post by jvdowney on 2006-07-05
If I remember right, the minumum for Xubuntu was listed at 128MB. I installed on  similar hardware but with 192MB ram and Xubuntu live cd ran fine, and installed without a problem.

If you have a Circuit City locally, they may have a PC100 compatible card. I bought one locally a few weeks ago. 128MB cost about $50US.

---

### Post by roxics on 2006-07-05
That's way too much money. I found some on ebay for about $6. 

Thanks for the info though.

---

### Post by jvdowney on 2006-07-05
You're right, it was way to much to pay :( . I was in a hurry -

---

### Post by Matthamilton23 on 2007-02-13
does anybody out there know if ubuntu would run well on an emachine e tower 500i
500 mhz Intel Celeron
160 mb ram
10 gig hd

---

### Post by zgornel on 2007-02-13
> **Matthamilton23 said:**
> does anybody out there know if ubuntu would run well on an emachine e tower 500i
500 mhz Intel Celeron
160 mb ram
10 gig hd
Depends very much on what you intend to o with it. Simple tasks like web surfing, music and movies can be handled. Intensive programs will most likely run slow. Lightweight window managers are highly recommended :D .

---

### Post by linuxify on 2007-03-23
I've had xubuntu working beautifully although quite slow on a HP Pavillion N5190. Its PIII 700 MHz 256 MB with a 2.2 GB HDD (the original 40 GB failed, I have a prehistoric Compaq 410c from where I pulled out the working 2.2 GB)
1.7 GB is available for install as I have a 250 MB /home ext3 partition on it from many years.
Its a slightly lengthy process, but i have a fully functional laptop. I'm a system admin. with about 12 yrs exp. :) 

Download the alt. CD - xubuntu-X.XX-alternate-i386.iso (X.XX depending on which version you want) from any of the Xubuntu mirrors. Install command line system only, then install minimal desktop. customize from there with synaptic or apt-get. Its not rocket science, although in my opinion you should have some experience with the command line.

---

