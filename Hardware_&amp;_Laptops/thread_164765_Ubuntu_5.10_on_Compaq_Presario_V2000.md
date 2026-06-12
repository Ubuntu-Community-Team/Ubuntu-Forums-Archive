---
title: "Ubuntu 5.10 on Compaq Presario V2000"
date: 2006-04-23
forum: Hardware &amp; Laptops
---

### Post by stalkier on 2006-04-23
I just downloaded the new Install CD for Ubuntu 5.10. It installed with no trouble and it rebooted. It says it cannot load the Server X program???? I know it has to do with the GUI, and that is all I know of it. I ran into the same problem with version 4.10 the other day. I could not get the Ubuntu GUI to load. I am not sure what specs I have to tell you about for you to help. Also is there wireless support in Ubuntu 5.10/4.10?? This laptop has a wireless card built in and that is the only way I connect to the broadband router/network. I run version 4.10 on my desktop along with XP home SP2. I really love Ubuntu and would love to use it as a dual-boot on my laptop. Thanks for the help.

John Brady

---

### Post by tiuk on 2006-04-23
I own a Presario V2305CA, and had the same problems as you with X starting when I tried 5.10. I decided to give Dapper a shot (flight 6), and it worked like a dream. Everything was automatically config'd (sound, video, ethernet, you name it), with the exception of wireless. My particular laptop has as Broadcom bcm4318 (as yours probably also does, it seems to be very popular amongst compaq presario and HP laptops), which I was able to get working with ndiswrapper. I'm happy to report I'm now posting from my laptop via wifi. Once you get Dapper installed you'll need to download a few things, like ndiswrapper and the windows drivers for your wifi card, so you'll either need to do it from another computer and use a flash drive, or connect your laptop temporarily via ethernet. There are some great threads on these forums if you get stuck, you can be almost guaranteed that someone has already had your problem (if you run into one) so searching is usually the quickest way to get up and running. Good luck.

---

### Post by stalkier on 2006-04-23
Thanks for your help. I am downloading the Dapper Drake version right now. I will also look for the additional files needed. I really appreciate it.

John

---

### Post by tiuk on 2006-04-24
Glad to help, I know I was happy when I was able to get everything working.

---

### Post by stalkier on 2006-04-24
I have it installed and everything but I cannot get the ndiswrapper to install. How do I get it to install? I am reading and re-reading the install instructions but I guess I am not understanding them. Thanks for the help.

John Brady

---

### Post by stalkier on 2006-04-24
Sorry I have the ndiswrapper installed now (found it in another thread). However, I cannot get the driver files to copy using the sudo command. It says I do not have permission to write to the directory. Thnaks for all the help you can give me. I know I will get this up and running.

John Brady

---

### Post by stalkier on 2006-04-24
Sorry I have the ndiswrapper installed now (found it in another thread). However, I cannot get the driver files to copy using the sudo command. It says I do not have permission to write to the directory. Thnaks for all the help you can give me. I know I will get this up and running.

John Brady

---

### Post by tiuk on 2006-04-25
What directory are you trying to move the drivers to? Their location doesn't really matter. Mine were in a directory called wlan on my Desktop.

---

### Post by stalkier on 2006-04-25
Actually mine are on my desktop as well. I am not sure why it will not install the driver. Everything else works perfect except for the wireless card. I DID however find some interesting info on the Broadcom Linux driver. Yes I said it, Linux driver for the Broadcom wireless devices. It is in the current 43xx stage and can be found at [http://bcm43xx.berlios.de/](http://bcm43xx.berlios.de/)

I have not been able to download the driver as of yet though. Could be an older site???? All I know is what the website talks about. Thanks.

John

---

### Post by stalkier on 2006-04-25
Do you happen to know if something from this website would help? 

[http://www.broadcom.com/products/raid_2.1.0_linuxdriver_download.php](http://www.broadcom.com/products/raid_2.1.0_linuxdriver_download.php)

They don't Ubuntu on the list of versions of Linux supported. Do you think on of the ones that ARE supported would work?

John

---

### Post by tiuk on 2006-04-26
I'm sorry, I have no idea. I have very little experience with Linux, just what I've learned while recently installing Ubuntu.

What was the exact command you used that said you didn't have permission?

---

### Post by stalkier on 2006-04-26
I used this thread:
[http://www.ubuntuforums.org/showthread.php?t=131797](http://www.ubuntuforums.org/showthread.php?t=131797)

Thanks
John

---

