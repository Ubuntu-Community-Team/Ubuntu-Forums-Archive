---
title: "Problems with various graphics cards."
date: 2014-01-23
forum: Hardware
---

### Post by Twan_Slegers on 2014-01-23
So I had installed Ubuntu 13.10 on a 10-year-old PC previously running Windows XP. 

Specs:
ASUS P4P800-VM motherboard
Intel Pentium 4 HT 3.0GHz
1.5GB DDR RAM
20GB Maxtor hard drive
GeForce FX 5200 128MB
300W PSU

I made sure everything was working. So I installed the new drivers, and at times, the screen would fill up with strange black "symbols", except for applications like videos. 
I assumed it was the problem of the graphics card, so I replaced it with a 6600 GT 128MB (after having erased the old drivers), and noticed that it gave a BIOS message, but the text was unreadable, and the PC unusable. So again, I swapped it out for a Sapphire Radeon X1650 Pro. Sometimes it didn't boot at all, and other times the screen would be full of moving colored bars (artifacts) and after that the screen would go black or it would just be light blue, with no reaction at all.

What could be the problem?

---

### Post by E_Sound on 2014-01-23
It can be hardware related problem as well (e.g. faulty capacitors of motherboard). Have you experienced any problems, when using windows OS?
There is no need no install VGA drivers in ubuntu, unless you want to have 3D acceleration. If open source nvidia/amd drivers worked well, which come with ubuntu, then you shouldn't install something else.

---

### Post by Incarnadine on 2014-01-23
Have you tried installing the proprietary drivers from the "Software Update" application?

My experience installing the Linux drivers provided by the graphic card's manufacture website has never been good. Your best option is to use the open-source driver or to try out the proprietary driver found in the Software Update application.

---

### Post by Twan_Slegers on 2014-01-24
For the FX 5200, I have used the proprietary drivers from the software update application. Also, Nvidia doesn't appear to have Ubuntu compatible drivers on their site. 

The motherboard works perfectly, every feature works, I had not gotten to install a Windows OS because I used an occupied hard drive and needed a clean install. I don't think it's got enough space to dual-boot Ubuntu and Windows.

---

### Post by grahammechanical on 2014-01-24
I am pointing to the amount of video memory in the video card. 2 x 128MB would still be low in my opinion.

> [COLOR=#333333][FONT=Ubuntu]* 3D Acceleration Capable Videocard with at least 256 MB[/FONT][/COLOR]

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

Regards.

---

### Post by Mark Phelps on 2014-01-24
> I swapped it out for a Sapphire Radeon X1650 Pro.If THIS is what you are using now, then the advice > Have you tried installing the proprietary drivers from the "Software Update" application? will NOT work because AMD dropped proprietary Linux driver support for the X-series cards YEARS ago.  The only drivers available now are the default Radeon drivers and those should install automatically.

---

### Post by Twan_Slegers on 2014-01-25
> **Mark Phelps said:**
> If THIS is what you are using now, then the advice  will NOT work because AMD dropped proprietary Linux driver support for the X-series cards YEARS ago.  The only drivers available now are the default Radeon drivers and those should install automatically.

I would like to note that the PC does not boot up properly with the X1650 Pro. So, I can't install my drivers.

I think it would be a good idea to roll back to Windows XP. However, that would be a security risk, and I don't think it'll handle Windows 7 properly.

Also, the Radeon X1650 Pro appears to be 512MB DDR2 so it should run fine within Ubuntu.

The FX 5200 however is 128MB which could be the problem in 3D applications.

Any other suggestions perhaps?

---

### Post by Mark Phelps on 2014-01-25
What does > not boot up properly with the X1650 Pro mean?  IS it getting part way through the boot and hanging?  Is there no display after the initial start?

If it is a display problem, then try setting the kernel "xforcevesa" parm using the info linked: [http://askubuntu.com/questions/53279/how-to-set-xforcevesa]("http://askubuntu.com/questions/53279/how-to-set-xforcevesa")

---

### Post by Twan_Slegers on 2014-01-25
> **Mark Phelps said:**
> What does  mean?  IS it getting part way through the boot and hanging?  Is there no display after the initial start?

If it is a display problem, then try setting the kernel "xforcevesa" parm using the info linked: [http://askubuntu.com/questions/53279/how-to-set-xforcevesa](http://askubuntu.com/questions/53279/how-to-set-xforcevesa)


What it means is kind of complex. More like a 50/50 percent chance of two things happening.

One: There is no display at all when booting, and the video card fan makes a lot of noise.
Two: There is display, but it is an artifact and the PC is unusable.

---

### Post by Twan_Slegers on 2014-01-30
Anyone? I can't seem to solve it.

---

### Post by Mark Phelps on 2014-01-30
Not really much you can do without a working display.

What I would try is using another PC to grab a copy of Lubuntu.  

Create something bootable using the ISO file -- CD/DVD or USB, and boot from that using the Sapphire x1650.  I had an old x1600 ATI card and it worked fine with older versions of Ubuntu (prior to 12.x).

---

### Post by Twan_Slegers on 2014-01-31
Ok, I will try that instead.

---

