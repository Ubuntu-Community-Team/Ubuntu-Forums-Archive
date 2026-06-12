---
title: "PCI : Cannot allocate resource region 7 of bridge"
date: 2006-12-09
forum: Hardware &amp; Laptops
---

### Post by Woifi1988 on 2006-12-09
I hope someone of you can help me. I asked in many forums but nobody has a solution for this problem

I found out that im not the only one who has this problem, but i think the only one who has it with ubuntu- os's

I tried
ubuntu
kubunt
xubuntu

When I start my laptop, i recieve a cuple of such errors:
PCI : Cannot allocate resource region 7 of bridge

Normally my laptop starts anyway but when I havent connected my laptop to the power supply the boot progress stops and nothing happens.

I asked some teachers from me who are linux experts but they also had no solution for that problem.
I have had it with 6.06 and now with 6.10.

when I boot with ACPI=off there are no errors displayed, but when i log in intu the GUI my laptop hangs up after the login prompt.

I dispair. When I can't find a solution for that problem I have to accept that my laptop is against a linux distribution.

My laptop's specifications:

Intel Pentium M Prozessor 2 Ghz
ATI Mobility Grafics with PCI Express

I hope someone can help me!

Please note, that I am common with the basic function of the OS but I don't know any detail config!

And please excuse my bad english.. I work on it 

Greets

---

### Post by plaz42 on 2006-12-09
Post some more detailed specs about your exact hardware.  

The PCI errors you mention are known about, expected, and relatively harmless on my laptop (Acer Aspire 5672WLMi), for instance.  

My guess as to your gui hang problem is that your display driver has been set to the open-source ati driver, which doesn't support the newer cards.  To get started, try logging into a command line and modifying your X server configuration (sudo vim /etc/X11/xorg.conf).  Look for a section which reads Device:   "ati".  Replace "ati" with "vesa".  This should get you a usable but low-quality graphics driver when you reboot. 

 For more information, check through some of this thread: [http://www.ubuntuforums.org/showthread.php?t=121125](http://www.ubuntuforums.org/showthread.php?t=121125)

---

### Post by Woifi1988 on 2006-12-10
This errors aren't harmless becaus my laptop sometimes stops to boot when this errors appear!

greets

---

### Post by kracheck on 2006-12-13
Hi there Woifi,
I have the same errors as those you are referring at.  I've done the same research as you did and you are correct I haven't seen anybody come up with an answer that makes them go away.  Some people suggest to turn of ACPI, others upgrade their BIOS.  However I haven't seen anyone (YET) posting those errors beeing the reason for their computer to freeze up or stop booting.  You could indeed be the first one but it would be nice if you could give the solution Plaz42 suggested a try just to make sure it's not the graphics card playing tricks on you.  If after having done that your laptop still keeps freezing we can be pretty sure to look in another place to find a solution.
Thanks.

---

### Post by MrSoussey on 2007-01-14
try a bios update... worked for me

---

### Post by Quintus Maximus on 2007-02-19
Okay I have the same problem. 
The messages
PCI : Cannot allocate resource region 7 of bridge
are harmless
my guess is that it crashes on booting with the message
soft lock detected on CPU#0
(check it when you come to the craphical boot sequence enter ctrl+alt+F1 you should get the output from the boot sequence)
If this is the case, you should boot in recovery mode (this might not work at first also but after a try or 2 you'll get in)
Once you were able to boot into your system, follow the instructions here:
[http://kmr.nada.kth.se/~mini/ubuntu/](http://kmr.nada.kth.se/~mini/ubuntu/)

That should take care of your problem.

(more info :
[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63418](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63418))

---

### Post by bs.it on 2008-01-02
I had this same exact problem with kubuntu, ubuntu 6.06, 7.10...etc..
But what finally fixed it for me is I installed ubuntu feisty which I believe is 7.04.
Hope that helps :).

---

### Post by notsoworried on 2008-04-30
> **Quintus Maximus said:**
> Okay I have the same problem. 
The messages
PCI : Cannot allocate resource region 7 of bridge
are harmless
my guess is that it crashes on booting with the message
soft lock detected on CPU#0
(check it when you come to the craphical boot sequence enter ctrl+alt+F1 you should get the output from the boot sequence)
If this is the case, you should boot in recovery mode (this might not work at first also but after a try or 2 you'll get in)
Once you were able to boot into your system, follow the instructions here:
[http://kmr.nada.kth.se/~mini/ubuntu/](http://kmr.nada.kth.se/~mini/ubuntu/)

That should take care of your problem.

(more info :
[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63418](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63418))
Quintus Maximus or anyone else who knows. I am having the same problem with resource region 7. You had the following in your message... 

Once you were able to boot into your system, follow the instructions here:
[http://kmr.nada.kth.se/~mini/ubuntu/](http://kmr.nada.kth.se/~mini/ubuntu/)

I went to that url but is there anything for kernel 2.6.22-14 generic?

Thank for the help in advance. 

Aloha

---

