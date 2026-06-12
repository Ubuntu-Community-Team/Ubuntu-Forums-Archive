---
title: "What do I install???"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by jimbo md on 2009-08-12
So here is the deal:

Somebody installed Ubuntu onto my computer, but did not know that I had a 64-bit CPU in it so the 32-bit version is on it.  I also believe that this is the reason why the CPU frequency scaling does not work.
Now I would like to reinstall the whole thing and get it right.  

I downloaded the file from the Ubuntu website and popped it in my computer but it doesn't start automatically and when I want to start it manually, I do not really know what to click on.  When I double click the .exe file, it loads and then I get an error message.

Please help me figure out how to install my lovely Ubuntu OS on my AMD.
Thanks so much in advance.

---

### Post by bossa on 2009-08-12
Hi Jimbo 
I think you will be able to run 32 bit version no problem most people do . Look up enabling cpu scaling and you will be fine.
Try this  [http://wlmtips.com/2008/06/13/enable-cpu-scaling-in-ubuntu-linux-friday/](http://wlmtips.com/2008/06/13/enable-cpu-scaling-in-ubuntu-linux-friday/)

---

### Post by jimbo md on 2009-08-12
Hey Bossa,
I appreciate your answer, but I would really like to reinstall it.  What would the best way to do this be?

---

### Post by oldfred on 2009-08-12
Currently the only real advantage of 64 bit is the capability to use greater the 4GB of memory. I am running 32bit on my machine with 4GB and it only sees about 3.2 in both Windows and Ubuntu. 

The 64bit desktop version up until recently was missing some applications and had some issues. Almost all these are resolved, but some applications are still the 32bit running in the 64bit environment. 

Only windows uses .exe files, Ubuntu cannot do anything with those. All applications are installed thru Synaptic or from the command line via apt-get. The file was probably for ubuntu in windows called Wubi or to allow windows to create a version. Normally you download an .iso which is an image file that is written/extracted to a CD by iso writer (most cd writing programs copy files).

---

### Post by jimbo md on 2009-08-12
The .exe file is probably there because I downloaded the file from Windows.  

In any event, I would still like to reinstall the OS and put on the 64-bit version.  For some reason the CD will not autostart.

---

### Post by raymondh on 2009-08-12
Hi Jimbo MD,

1.  Your original ubuntu install, is it thru WUBI?
2.  This 64-bit, do you want a wubi-install or... Ubuntu in it's own partition?

When you say "autostart", kindly clarify.  Did you download and burn the iso file into a liveCD?  Are you trying to install with windows open?

Back-up your files.

---

### Post by jimbo md on 2009-08-13
Hi Raymond Henson,

1.  I wanted a new computer so what I did was I bought all the necessary parts for it.  When I put everything together, I did not have an operating system and since I had used Ubuntu for my laptop, I thought it would be a good idea to put Ubuntu on my new machine.  So when the person installed it for me, he just popped the CD into the drive (I'm assuming) and installed it through there.  I am sure he got the CD through downloading it on Windows.
2.  I cannot get a wubi install because I do not have Windows on it.  I have Ubuntu on there and I want the new partition to overwrite the old one.

When I say "autostart" I mean that the CD will not start on its own.  I have to go into the folder and try to open it from there but I do not know what to click on.  
What I did, was I downloaded it and burned it onto a CD just like I did it for my laptop some months ago, but I guess I installed it through Windows on my laptop.

Thanks for your help, Ray.

---

### Post by Nburnes on 2009-08-13
> **jimbo md said:**
> Hi Raymond Henson,

1.  I wanted a new computer so what I did was I bought all the necessary parts for it.  When I put everything together, I did not have an operating system and since I had used Ubuntu for my laptop, I thought it would be a good idea to put Ubuntu on my new machine.  So when the person installed it for me, he just popped the CD into the drive (I'm assuming) and installed it through there.  I am sure he got the CD through downloading it on Windows.
2.  I cannot get a wubi install because I do not have Windows on it.  I have Ubuntu on there and I want the new partition to overwrite the old one.

When I say "autostart" I mean that the CD will not start on its own.  I have to go into the folder and try to open it from there but I do not know what to click on.  
What I did, was I downloaded it and burned it onto a CD just like I did it for my laptop some months ago, but I guess I installed it through Windows on my laptop.

Thanks for your help, Ray.
You need to enable booting off your CD inside your BIOS.

---

