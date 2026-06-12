---
title: "Just shoot me if I have to return to VISTA"
date: 2007-11-07
forum: Hardware &amp; Laptops
---

### Post by bobbythehun on 2007-11-07
I (a newbie) am having problems on install of 7.10:confused:. Am running ASUSM2A-VM HDMI motherboard. SATA hard drive. AMD64 processor.  I cannot get the install to run completely. It freezes at random places in the install process. PLEASE HELP I DO NOT WANT TO GO BACK TO MICROSOFT. thanx.

---

### Post by mon_m on 2007-11-08
Hey there bud.  Welcome :D

For us to be able to help you though, is there any way you could be a little bit more specific about the problem?  i.e. at which points is it freezing and so on.

---

### Post by ARhere on 2007-11-08
Not much info to go on, but I will try to help.

In my many years of debugging PC's if the installer freezes during install it is usually a hardware issue 99% of the time.  Please take a moment and list *everything* in your box, including devices on the motherboard (i.e.: integrated sound card, etc.)

So, start removing cards one at a time, attempting to install after each device.  One of the biggest issues usually is with cheap modems, sound cards, and IDE/fakeRAID controllers.  You should be able to disable the extra controllers in the BIOS.

UUUuugh!!!  I just looked up your mother board and it is ***integrated hell***.  Ok, first step... visit [ASUS web site]("http://support.asus.com/download/download.aspx?modelname=M2A-VM%20HDMI&SLanguage=en-us").  They are really good about driver support.  I am sure there is a way to install drivers during the install process but an Ubuntu guru will have to speak up on how to do this.

If that does not solve your woes, then defiantly disable that on-board RAID in the BIOS and retry to install Ubuntu.

I will be surprised if you cannot solve your problem from here.

-ARhere

---

### Post by trippinnik on 2007-11-08
I think it could be the install medium.  Try checking it for errors from the boot prompt or burn at a really slow speed.  Are you using CDRW? thos are often bad also.

---

