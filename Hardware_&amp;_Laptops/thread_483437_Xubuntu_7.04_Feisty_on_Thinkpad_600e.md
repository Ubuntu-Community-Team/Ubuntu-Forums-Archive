---
title: "Xubuntu 7.04 Feisty on Thinkpad 600e"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by TubaTodd on 2007-06-24
I've read and read and read and I still can't figure out what I am doing wrong. I have an IBM Thinkpad 600e with 256MB of RAM and a 30GB HD. I've installed Xubuntu and Ubuntu on this machine with much success. In the past I've tried installing Xubuntu Edgy and Feisty on this machine and it gives me problems EVERY time.

So, this weekend I decided to punish myself and try and get Xubuntu Feisty installed on this machine. I read many websites that outline how to install it and they make it sound like it is very straight forward. In any event, here's what I have done. Perhaps someone can help give me some success.

1. I Flashed the BIOS. I downloaded 1.16 and made a boot CD (which IBM's website did NOT provide. They only have a diskette driver. Funny...the 600e doesn't HAVE a floppy drive.) and manually flashed the BIOS (my battery won't hold a charge so the IBM utility refuses to flash it). After the flash, the BIOS is reporting the correct version. 

2. Put in the Xubuntu Feisty Live CD and use the following boot commands (as per several websites)

```
acpi=off pci=noacpi pnpbios=off vga=0x317
```

3. Everything appears to be running smoothly and I reach a desktop. One noticeable problem, the top and bottom panels crash EVERYTIME I try this. Sooooo, I have a desktop with icons and tell the machine to do an install.

4. I answer questions and the install is underway. 

5. Somewhere around 55% or so the CD says that it has failed on a particular file and sends me back to the desktop. I tried downloading a new ISO image and using a different CD. Same result.

6. I tried the Xubuntu Feisty Alternate CD instead. I answered a bunch of questions...took a nap and eventually it finished loading. I rebooted the machine and it crashes on bootup with a Kernel Panic. Coincidentally, I get a Kernel Panic EVERYTIME I try booting the Ubuntu Feisty Live CD. 

Well, I went back to installing Dapper....since it works everytime. I still want to load Feisty if I can. (I want the latest and the greatest). So, what am I doing wrong??

Thanks.

---

### Post by TubaTodd on 2007-06-25
Anybody?? Here's a different oddity. I have Xubuntu Dapper installed now, and when I was running off the live CD I had my Linksys PCMCIA card and working great, but after the install the card isn't even detected. DOH!

Help

---

### Post by TubaTodd on 2007-06-28
Well, I never could find a solution to allow me to install Feisty and have it work. So, I installed Zenwalk and it is working without a hitch. I don't think of this as a "solution" to my problem. To me this is more like avoiding the problem entirely. Does anyone have any ideas on how I can get my machine running Xubuntu Feisty??

Thanks.

---

### Post by CnlPepper on 2007-06-29
Hi TubaTodd, have you considered installing the normal version of ubuntu and then apt-get/synaptic installing the xubuntu desktop. I have done this on a 600e recently (though it had 296Mb of RAM) and it worked fine. You'll need to remove the normal ubuntu desktop applications but this is fairly easy to do.

Btw if it helps, I'm in the middle of writing a page on installing (K/X)ubuntu on the thinkpad 600e, it includes pretty much all the info required to get it working fully bar the modem:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_Feisty_Fawn_on_a_ThinkPad_600E](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_Feisty_Fawn_on_a_ThinkPad_600E)

I guess I better finish writing it sometime!

---

### Post by TubaTodd on 2007-07-05
I took the advice of CnlPepper.......sorta. I installed Ubuntu 6.06 again and it worked great. Next I did an upgrade to Edgy by running..

```
update-manager -c
``` 

...which gave me the option to upgrade the version. After the 1+ hours it took to download and install I had Edgy working on the laptop. (that was a **first**) Next I ran the very same command again...

```
update-manager -c
```

This time I had the option to upgrade to Feisty. After 2+ hours and a couple nagging questions, I had Fesity on my Thinkpad 600E. Everything completed this morning before I left for work. I haven't checked every application to make sure they are working. The key points I checked for were 

1. Does it boot
2. Do I have a wifi connection
3. Can I connect to the internet 

YES to all 3.

I tried installing XFCE, but the install package was not listed in Synaptic. I will need to make sure that I consult the ubuntu guide and update my ***sources.list file***.


The $1,000,000 question is....

"What is so different between the Feisty CD install and my upgrade path that allows my fickle machine to work?"

---

### Post by TubaTodd on 2007-07-06
UPDATE:

I went to the Ubuntuguide.org site and used the sources.list file that they suggest. I installed "xubuntu-desktop" and I was good-to-go. No sooner did I get this "*project pc*" working again, my mom (visiting from NY and **_NOT**_ computer savvy at all) said to me "can I look on the internet with that?" I put the laptop by the couch and she surfed the internet....an activity she RARELY does. 

Who says old machines don't have purposes?

---

