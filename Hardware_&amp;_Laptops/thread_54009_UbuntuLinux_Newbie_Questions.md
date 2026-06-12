---
title: "Ubuntu/Linux Newbie Questions"
date: 2005-08-03
forum: Hardware &amp; Laptops
---

### Post by shthap3ns on 2005-08-03
Hello all, 

I'm a fresh user to Linux, and I chose Ubuntu for my first attempt at tackling this thing. I successfully installed a dual-boot setup (Windows XP and Ubuntu) on my HP Pavilion 4805us (refurbished) laptop. Unfortunately I don't know how to configure anything (which I am working on by reading) and don't know my way around the linux environment at all. I'm having some problems getting my wireless card to work. It's a Broadcom (BCM4306 802.11b/g Wireless LAN) adapter, and I've followed that tutorial by jonny. It didn't work though. Perhaps I'm doing something wrong. My wireless card doesn't appear in my Networking options, there's only eth0, which is what I'm using to connect right now. 

Besides that problem, I also have a few questions. Please forgive me if this sounds completely stupid to some of you guys, but I gotta start somewhere. :D

1. What is the "default" directory that I should install most of my programs to?

2. How do I change the "host name" that I typed in during installation? 

3. After I tried the Broadcom configuration thing from jonny's post, I can't seem to access any Help files. EX: When I click on the GNOME help icon, it gives me an error: "Cannot launch icon -- Details: Failed to execute child process "yelp" (No such files or directory)

4. Some of the hardware in Device Manager is shown as "Unknown" (everything under BIOS, Processor, Memory). Is there something I can do to fix this? I'm just not sure if the system is recognizing all my hardware correctly. Everything else seems to work fine though, video, audio, network (wired ethernet), and mouse + touchpad. 

Thanks for any help, I appreciate it!

-shthap3ns

---

### Post by sebdah on 2005-08-03
Hi and welcome!

1. /usr/local/ is the most common directory. I suggest you to use Synaptic (System -> Administration -> Synaptic Package Manager) for installation. It's very easy. You just search och browse for an application and click to install. More about Synaptic and installing software is found here (well worth a try): [http://www.ubuntuguide.org](http://www.ubuntuguide.org).

2. System -> Administrartion -> Network. Click on 'General' (I think that is the name - otherwise the second tab), then you'll see it.

3. Don't konw, acctually.. Sorry

4. The same for me - but as long as it work I'm happy =)

/Damian

---

### Post by az on 2005-08-03
What hardware is not properly detected?

And if I ever need to compile something myself and install it to a directory, I use a subdirectory in my home directory.  I do not need to change permissions or anything.  I feel better doing that.

---

### Post by shthap3ns on 2005-08-03
[QUOTE=azz]What hardware is not properly detected?[/QUOTE]

Everything under the subdirectories of BIOS, Processor, and Memory in Device Manager shows "Unknown" for vendor, etc. I'm not sure if this means if the hardware is not being detected properly, or if the drivers aren't installed properly. Even if it doesn't affect system performance, I'd like to know if there's a way to have Ubuntu properly register the hardware in Device Manager.

Also, there's the problem with the wireless connection that I still can't figure out...

---

