---
title: "ASUS P8Z68-V PRO - SSD - i5 2500k Build Help"
date: 2012-03-14
forum: Hardware
---

### Post by outspoken on 2012-03-14
Hello,

I'm about to build a server and use Ubuntu 12.04 beta1 as I want to ensure drivers are available for the following:

Asus P8Z68-V Pro/Gen3
Intel i5 2500k
Crucial M4 64GB
G.Skill 8GB 1600
Corsair 520HX

Should this work right from install or will there be some tweaking to get all the SATA and others ports working?

I'm going to be using 1 SATA port for the OS (Crucial M4) and 5 ports will be in a software RAID (mdadm).

I will need to use the on-board video with DVI output.

---

### Post by Bucky Ball on 2012-03-14
Welcome. 12.04 LTS is pre-release, still testing and NOT the best choice for a server. Expect breakages.

You would be much better to use the current, stable, long term support release for a production machine, 10.04 LTS. Server version supported until April 2015 and a one click upgrade to 12.04 LTS when that is stable (I'd wait a couple of months after release or until 10.04 LTS EOL - end of life - when 12.04 should be rock solid). All the things you mention will work fine with 10.04; all standard and no exotic drivers required. There is nothing special there, generic. I would be more concerned with your graphics and wireless cards, if used.

You are doing the right thing sticking with the LTS releases for your server, though. That is what they are intended for; production machines and stability with five year support (although as of 12.04 LTS the desktop version will also be five year support).

Before launching into this, though, I would familiarise yourself with Linux and particularly Ubuntu if you haven't already (particularly setting up a RAID array). There is a learning curve and putting a server together will call for all brain cells on deck if you haven't used Ubuntu before (*especially* if you are going headless). ;)

Best thing to do is build the thing, boot from a Ubuntu CD and see how it flies using the 'Try Ubuntu' option (don't know if that's available on server version though). 

One MAJOR point: ***Use a good quality PSU!*** _DON'T_ skimp on this; it is the heart of the machine and a dodgy generic silver box PSU won't do. When that dies unexpectedly (and being a server which may be on 24/7 this could be in the middle of the night) it can take out the rest of your machine; motherboard, RAM, hard drives, CPU ... the lot. Not to mention burning down the house if the thing is unattended when the generic PSU pops (and many of us here have seen them die in a blaze of glory). Go for 85+ efficiency rated and known brand (600, 000 hours life cycle is a good start).

---

### Post by outspoken on 2012-03-14
this will not be a production machine in the sense of running produced content in a customer facing environment. though my customer (my family) will be using it to stream movies. I'm not too concerned over temporary breakage.

Can I upgrade from this current 12.04 beta1 to the official LTS when it is released without any pain? I've never used a beta/pre-release image of ubuntu before, only LTS and desktop releases.

Thank you for the input, I'm glad to know there is nothing out of the norm with the hardware.

---

### Post by outspoken on 2012-03-14
> **Bucky Ball said:**
> 
Best thing to do is build the thing, boot from a Ubuntu CD and see how it flies using the 'Try Ubuntu' option (don't know if that's available on server version though).

That's a good idea, and I'm using the Desktop 64bit version as I need the GUI for a few apps that run in java.

> **Bucky Ball said:**
> 
One point: use a good quality PSU! DON'T skimp on this; it is the heart of the machine and a dodgy generic silver box PSU won't do. When that dies unexpectedly (and being a server that could be on 24/7 this could be in the middle of the night) it can take out the rest of your machine; motherboard, RAM, hard drives, CPU ... the lot. Not to mention burning down the house if the thing is unattended when the generic PSU pops (and many of us here have seen them die in a blaze of glory). Go for 85+ efficiency rated and known brand (600, 000 hours life cycle is a good start).

Ya, PSU is important, that's why I'm using a quality Corsair 520HX that I listed in the top post. I'm far from new to linux and hardware, I just haven't built an up to date machine in a few years. ;)

---

### Post by Bucky Ball on 2012-03-14
Please read my post again as have edited. You need to familiarise yourself with Linux as not Windows before commencing this project. There will be a learning curve (possibly steep).

And yes; just keep accepting your updates and you will end up with the released 12.04 LTS. 

Production machine doesn't need to be for a paying 'customer'. It needs to be relied on. As long as your family doesn't mind not streaming movies for an hour, day, week, while you nut out breakages after the last update then all good. ;)

---

### Post by joephi on 2012-05-10
If you're using an SSD, you will want to look into using a filesystem for your build which supports TRIM, such as ext4 with the "discard" mount option (maybe others too with similar mount options).  Otherwise your whole reason for using an SSD will be moot or actually perform worse after some time.  Also I would caution you to do regular backups, as, despite having no moving parts like a conventional HDD, SSDs do fail (but perhaps with less frequency than a mechanical HDD).

---

