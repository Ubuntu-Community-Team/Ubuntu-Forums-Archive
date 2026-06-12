---
title: "HP Pavilion dv2710us Problems"
date: 2008-03-27
forum: Hardware &amp; Laptops
---

### Post by demonzrulaz on 2008-03-27
Hi I bought a HP Pavilion dv2710us laptop recently and I really wanted to install ubuntu on it. I already dual-boot XP and Ubuntu on my desktop and I wanted to the same on my laptop but I ran into a lot of difficulties setting up Ubuntu on my laptop. First off, the live CD doesn't work well on my laptop. It gives me a screen resolution of 800x600 which is not good because I can't see most of the screen, esp the installer prompts....This is a problem for me because I won't be able to use the Ubuntu Live CD in case of, lets say, a Hard Drive failure or MBR being erased.

My BIGGEST problem with this laptop is the wireless. I cannot tell you the exact model of Wireless it uses but i'm sure its Broadcom (43-something?). I looked EVERYWHERE yet i couldn't find anything. I assumed that this laptop won't work with ubuntu but I'm looking for someone to prove me wrong. Is there anyone who can knows anything about this matter?

---

### Post by Nathan.Flow on 2008-04-17
using the live cd you want to use safe graphics mode, the Video problem is due to not having the proper video drivers get [Envy]("http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu10_all.deb") 
it requires some dependency's >apt-get --build-dep package name< so be sure to install them. as well as the latest drivers for your card use the utility. i recommend you edit your xorg.conf by hand as the utility can cause some undesired side effects.post what device you have and i'll help you the best i can. As for the [wireless]("http://ftp.us.dell.com/network/Dell_multi-device_A17_R174291.exe") this  driver should work for you, it did for me... you will have to unzip it, extract the files. i used wine. navagate to the driver directory in the new folder and use ndiswrapper -i bcmwl5.inf. if you get a message saying something like bcmwl5 : driver installed device (14E4:4315) present that's good and your on your way just add ndiswrapper to your /etc/modules and your driver will work when you next boot. if your in a hurry use the modprobe ndiswrapper command. 
:KS
:popcorn:
Enjoy

---

### Post by demonzrulaz on 2008-04-18
Hey thanks for your response. lol I uninstalled Ubuntu due to the wireless problem I had so once I reinstall it, i'll let you know whats up with my laptop. Thanks again for replying...thought no one else had this laptop :D

---

### Post by demonzrulaz on 2008-04-25
Hi I just installed Ubuntu 8.04 so I have attached the output of lspci. Hope you can help. This is my wireless: 04:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
Oh and I tried using the restricted driver (built in restricted driver manager thingie) for the graphics but the highest resolution I can get is 800x600...help?

---

### Post by Nathan.Flow on 2008-04-28
Looks like you have the same setup I have..
use apt and search for envy-qt install it then use envy-qy -t and install the nvdia drivers manualy using the latest drivers THEN set your modes under depth = default depth to "1280X800" after that see my post on the wireless problem.. [url]http://ubuntuforums.org/showthread.php?t=769405&highlight=DV2710us[url/]
down at the bottom of the first page..

I have a dvd problem maby you can help me with...
It states that I don't have enough permitions, or their no disk. but it will play the intro :confussion:

---

