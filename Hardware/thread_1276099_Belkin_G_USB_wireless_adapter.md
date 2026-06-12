---
title: "Belkin G USB wireless adapter"
date: 2009-09-26
forum: Hardware
---

### Post by winecurmudgeon on 2009-09-26
This worked out of the box on my ASUS 1005HA running Netbook remix. But when I plugged it in to my 64-bit Acer Aspire, nothing happened. Lsusb recognized it as Belkin, but that's it. 

A couple of questions: I was running 9.04 off the live CD, so it wasn't a real install. Is that the problem? (Though the live CD install recognized my printer and even searched for a driver.) Or is it a 64-bit problem with the live CD install?

My plan is to replace Vista with 9.04, but I want to make sure I have Internet access when I do it. Any words of wisdom?

---

### Post by TiredBird on 2009-09-26
I am using a Belkin G wireless usb adaptor with a full install of 9.04. I had to go the ndiswrapper route to make it work. If that sounds like what you need, I'll be glad to dig up the links.

---

### Post by winecurmudgeon on 2009-09-27
That's more than I want to do, but I appreciate the offer. I just want to be able to pop the thing in, and start downloading the stuff that needs to be fixed.

The curiosity for me is why it works on the Asus and doesn't work on the Acer.

---

### Post by TiredBird on 2009-09-27
Not sure about why one and not the other. Could be how you were running it though. That particular adapter needs a driver that is proprietary and only runs under windows. If you had installed it on your windows machine and were running ubuntu on top of windows, ubuntu might have been using the windows driver.

Thats what NDISWRAPPER is all about. It provides an interface from the native Windows code to Linux so that such beasts will work.

Installation is not really all that hard. Unlike it suggests in some of the tutorials, you don't really need to compile anything. 

Synaptic provides ndiswrapper all ready to go. The only other you need is a file from the CD that came with your adapter. A few short commands and a few short minutes and you'll have it working.

---

### Post by rehman on 2009-09-27
Dear All, I have installed ubuntu 9.04 on my system. I want to connect to the internet through my wireless phone (huwaie) . this phone comes with a usb serial cable. system detects this as connected to ttyUSB0. Up till here, all is fine.
but the problem is when i use "sudo wvdial", It says that there is no such a command. Please help me how I can connect to the internet.

---

