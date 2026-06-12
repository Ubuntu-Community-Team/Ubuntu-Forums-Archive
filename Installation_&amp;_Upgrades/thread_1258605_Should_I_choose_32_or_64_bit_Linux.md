---
title: "Should I choose 32 or 64 bit Linux?"
date: 2009-09-05
forum: Installation &amp; Upgrades
---

### Post by torbengb on 2009-09-05
Hi all!
--> Should I choose 32 or 64 bit Linux? 

There are 32-bit and 64-bit versions available. I want to use Linux for a Desktop PC and for a Media Center PC, and I am an utter newbie to Linux. Is there any benefit in 64-bit for me, or will I run into problems because  things work better on 32-bit?

---

### Post by dagoth_pie on 2009-09-05
I've never used 64bit, I've read that people run into problems with programs that don't have very good 64bit support yet (not many, Adobe Flash Player is the most notable, but that's just a useless program to begin with). Unless you want to have more than 3gb of RAM or whatever other benefits 64bit has I'd say just to go with 32bit. Someone please correct me if I'm wrong!

---

### Post by torbengb on 2009-09-05
Thank you Dagoth, I was expecting an answer like this, but not this fast :-)
Since I don't have >3GB RAM and I'm just looking for something that'll work, I will stick to 32-bit.

---

### Post by Liolikas on 2009-09-05
Native Ubuntu programs work well and even better on 64bit, but not Adobe things, ID games, Skype etc. like that. if you do not plan to use then go 64bit.

---

### Post by 3rdalbum on 2009-09-05
On Windows, things work better on 32-bit, because for years every programmer assumed that their programs were only going to be running on 32-bit x86 processors. So lots of things on Windows will only run on genuine 32-bit, or need to be run in 32-bit mode on the 64-bit operating system, because they've been written with that 32-bit assumption, and only the developer can rewrite it for 64-bit support.

On Linux, all drivers and programs are written to be portable to any of the CPU architectures that Linux supports, and there are a LOT of them. By comparison, 64-bit x86 is pretty much the same as 32-bit, and so software and drivers are merely al recompile away from being 64-bit native.

Where's 64-bit Flash Player for Windows? Doesn't exist yet. It's here on Linux and has been for some months. What about Google Chrome in 64-bit? Doesn't exist yet on Windows, but we've already got 64-bit Chromium.

Summary:

If your CPU supports 64-bit mode, and you have more than a gigabyte of RAM, run 64-bit Linux. You might not see any benefits, but there are no problems either, and you might as well use it in case you want to use more than 3 gigabytes of RAM in the future.

EDIT: I actually use 64-bit Linux, unlike the first person who replied.

---

### Post by dagoth_pie on 2009-09-05
Happy to help, I'm using 32bit and look at my system monitor shows I'm using 418MB of RAM (I like multitasking...) and 1.5MB of Swap space, Ubuntu isn't very memory intensive.

Feel free to ask more questions if you run into problems, although do give the forums a quick search over first, some people get a lil frustrated with people asking the same questions over and over again (although those are the first things to get fixed in the next version... :D)

Good luck, hopefully you have a smooth install

---

### Post by Moop on 2009-09-05
> **dagoth_pie said:**
> I've never used 64bit, I've read that people run into problems with programs that don't have very good 64bit support yet (not many, Adobe Flash Player is the most notable, but that's just a useless program to begin with). Unless you want to have more than 3gb of RAM or whatever other benefits 64bit has I'd say just to go with 32bit. Someone please correct me if I'm wrong!

Adobe flash has 64bit support and it works great. If you have the right hardware there's no reason not to use 64bit.

---

### Post by dagoth_pie on 2009-09-05
Now the pros come rolling in...:P

---

### Post by torbengb on 2009-09-05
Sounds like it is worth a try to use 64-bit after all! Thank you all for the inputs, I'll try it out and see how it goes. Thanks again!

---

### Post by dagoth_pie on 2009-09-05
And sorry for almost misleading you

---

### Post by oldos2er on 2009-09-05
> **torbengb said:**
> Sounds like it is worth a try to use 64-bit after all! Thank you all for the inputs, I'll try it out and see how it goes. Thanks again!

 Visit the x86_64 subforum. If you read the stickies there, you'll find scripts to install 64-bit Flash, and Java.

---

### Post by zipperback on 2009-09-06
> **dagoth_pie said:**
> I've never used 64bit, I've read that people run into problems with programs that don't have very good 64bit support yet (not many, Adobe Flash Player is the most notable, but that's just a useless program to begin with).

Flash 10 is available in 64bit now. Previously you had to download and install the 32bit version using the ndiswrapper to get it to work under 64bit. Now however they have released it for 64bit systems. It's far more stable for me under 64 bit than the 32 bit version was.


If you have a 64bit processor why not use a 64bit operating system? 

I am currently running Ubuntu Karmic Koala 9.10 64bit and it's been very stable for me. 

- zipperback
:popcorn:

---

### Post by eyeyoubin on 2009-09-06
I doubt you would see any significant differences in performance when you have less than 4 GB RAM. But then again, if you have 64-bit compatible CPUs like Intel Core Duo, and have 2 GB RAM like me. You might as well install 64-bit OS just in case you upgrade your RAM like I'm planning to do :D.

---

### Post by lemming465 on 2009-09-06
I run both 32-bit and 64-bit variants on different computers.  You will have more compatibility problems with 64-bit, but not enough to stop anyone determined.  64-bit has at least 15% better performance, possibly more, depending on your workload (due to more registers and reduced virtual memory management overhead).

If you aren't performance constrained, and value compatibility, stability, and low annoyance value stick with 32-bit.  Anyone running scientific code, DB code, or feeling like living on the bleeding edge should go 64-bit.

(typed from a 64-bit jaunty)

---

### Post by jtuchscherer on 2009-09-16
I recently switched to a 64Bit system. I don't regret doing so, but the overall experience reminded me of my first Ubuntu install (2005). I needed to hunt down drivers for the webcam and I needed to recompile the kernel to get my sound to work properly. Nothing serious and I kind of enjoyed it, but by far not as smooth as all the other Ubuntu installs I had recently. Ubuntu came such a long way when it comes to ease of install. The 64Bit version is lacking a bit behind, but not much.

And yes, I indeed noticed the performance gain.

---

