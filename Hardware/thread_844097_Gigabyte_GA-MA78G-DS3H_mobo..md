---
title: "Gigabyte GA-MA78G-DS3H mobo."
date: 2008-06-29
forum: Hardware
---

### Post by superarmy on 2008-06-29
I have just placed an order for my new, fully ubuntu, (no space wasting windows partitions this time) computer. I decided to go with the GA-MA78G-DS3H, just wondering if anyone here has used it and if so are there any known issues? any driver installations required? Thanks in advance.

---

### Post by superarmy on 2008-06-30
bump

---

### Post by superarmy on 2008-06-30
bump

---

### Post by konzeew on 2008-07-17
> **superarmy said:**
> I have just placed an order for my new, fully ubuntu, (no space wasting windows partitions this time) computer. I decided to go with the GA-MA78G-DS3H, just wondering if anyone here has used it and if so are there any known issues? any driver installations required? Thanks in advance.

Hi superarmy, I have read in another your thread that motherboard Gigabyte GA-MA78G-DS3H works with no issues on ubuntu 8.04.
But can you confirm me that ethernet card realtek onboard works good out of the box? I have not wifi connection and if it doesn't work I can't go online...
Another thing... Do you use the integrated video card or not?
Thank you very much.

---

### Post by petri on 2008-07-19
Yes Realtek works out of the box. :)

I use the integrated video and it works like charm. You will be offered to download propietary code for ATI and after you install it you have a correct resolution and compiz works as it should.

---

### Post by konzeew on 2008-07-19
> **petri said:**
> Yes Realtek works out of the box. :)

I use the integrated video and it works like charm. You will be offered to download propietary code for ATI and after you install it you have a correct resolution and compiz works as it should.

OK petri thanks!
So for the video card it's a simple procedure, right? I go in the sistem/advanced tab and I enable the restricted driver.

I am interested in monitor HP w2207h
Is the resolution 1680x1050 hdmi-hdmi supported?
Bye.

---

### Post by Milanche on 2008-08-07
I have this mobo, and i have problems with video card hd3200...Other things works great ;)

---

### Post by bicyclebarron on 2008-08-07
> **Milanche said:**
> I have this mobo, and i have problems with video card hd3200...Other things works great ;)
Built a box with this system board and radeon hd3470 video no issues with Ubuntu at all

---

### Post by petri on 2008-08-08
Hi konzeew, 

sorry about the "2 weeks ago" ... vacation and stuff... 8)
I believe you have installed the drivers already. I'm looking after the secret of hdmi by myself right now. DVI > hdmi and hdmi > hdmi did not show picture on my Panasonic TH-37PX70. Only VGA did work with any VGA monitor I have.

I'll be back about hdmi.

------------

Milanche, can you describe the problems you have but if you already have solved it I hope you see this and please paste a link to the solution.

---

### Post by konzeew on 2008-08-10
MILANCHE, what is the problem with the integrated video card?
Have you issues with the correct resolution/visualisation? Or with the installation of restricted drivers? 
Or is only a problem about compiz and 3D, and other things work well?
Because I am not interested in 3D or compiz or video games, I use it for internet, openoffice and watching dvd. Thanks.


PETRI, I have not bought my new PC yet, because my hardware store now is on vacation. You give me very bad news about hdmi-hdmi or dvi-hdmi connection :(
I hope you can resolve it and post here! Thanks.

Bye.

---

### Post by petri on 2008-08-11
Both hdmi > hdmi and DVI > hdmi works now. Maybe it just needed a restart :) I get 720p at boot (bios picture) and with X it shows 1080p resolution automaticly. Ubuntu desktop is not readable at 1080p but changing the resolution to 720p shows the desktop in workable format.

There is although black border around the screen about 1,5-2,5 cm thick and no dvd movie appears on full screen just in letterbox mode :confused:

Audio over hdmi does not work but that seems to be an Linux issue. 
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/148097](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/148097)

Also the audio over 3,5mm plug is very low but at least it works.

---

### Post by superarmy on 2008-08-16
Indeed audio HDMI does not work at all, I did tinker with it a bit last night and nothing seemed to work, so I connected it up to my speaker system, 1080p with the right audio is amazing :D

---

### Post by Milanche on 2008-08-28
> **petri said:**
> 

Milanche, can you describe the problems you have but if you already have solved it I hope you see this and please paste a link to the solution.


[http://ubuntuforums.org/showthread.php?t=882676](http://ubuntuforums.org/showthread.php?t=882676)

Yes, i solved problem :) First i tried harder solution... that was so stupid.


**konzeew**,i had problem with the correct resolution :) But i tried some ATI drivers from synaptic, then tried envyng... And still nothing.

But i didn't tried to enable HW drivers(ATI driver) after i enabled ubuntu DL driver, then i restart computer and now everything works great.
And yes :) and compiz works great. Before this config. i had only 256MB of RAM, and old MX440 and i use Ubuntu from 6.06...

Only problem is sound, it's little quiet in Ubuntu... But in Kubuntu with KDE 4.1 is great, i don't know maybe problem is in some drivers.

---

### Post by konzeew on 2008-08-29
Thank you Milanche!! A lot of things was solved, so I think I will buy it.
Do you use vga, dvi or hdmi connection? Have you perfect borders in image monitor?
Thanks again. Bye.

---

### Post by TheTank on 2008-09-03
I have also the same mobo and was wondering if anyone knows if it is possible to use two monitors attached to vga & dvi?

I read somewhere that it is possible, just have no idea where to configure it.

---

### Post by TheTank on 2008-09-03
Fixed:
I downloaded the latest ATI drivers from the ati site and after installing them I got a nice tool to configure the screens.
Now I have my dual monitors.

---

### Post by petri on 2008-09-04
DVI and VGA works simultaneously same with HDMI and VGA.

DVI and HDMI does not work at the same time.

Atis controlpanel can be found in Synaptic search **fglrx-control**

---

### Post by wolfchri on 2008-09-12
Hello,

did one of you test resume / suspend with this board? 

Is this working, at least with the ati driver (I know that ACPI is usually not working with the fglrx drivers for some reason, no matter what mainboard).

---

### Post by TheTank on 2008-09-13
I was able to change my config for big desktop & dual head mode.
Only problem now is that flvs while being shown will crash X11.

---

### Post by akamaleldin on 2008-10-12
I just bought this MoBo and installed Ubuntu HardyHeron 8.04.1. Everything worked out of the box with no problems.

After installation I was offered to install the ATI Ristricted drivers that also worked like a charm.

I did not test the resume/suspend.

I am still trying to figure out the RAM problem as I have 2x2GB and the system is only reading 3GB.

Regards all

---

### Post by petri on 2008-10-12
> **akamaleldin said:**
> ....
I am still trying to figure out the RAM problem as I have 2x2GB and the system is only reading 3GB.

Regards all

Sounds like you have installed 32-bits Ubuntu. Those can not use more than 3GB ram due the "adressing problems" in ram.

I have 64-bits Ubuntu but I can't see if it makes system faster.

---

