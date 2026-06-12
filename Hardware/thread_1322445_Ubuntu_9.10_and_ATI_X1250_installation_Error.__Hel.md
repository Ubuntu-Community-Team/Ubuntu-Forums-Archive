---
title: "Ubuntu 9.10 and ATI X1250 installation Error.  Help!"
date: 2009-11-10
forum: Hardware
---

### Post by frenchfriedfaery on 2009-11-10
I am brand-spanking-new at this whole linux thing and I'm having a difficult time of installing my graphics driver.  I installed Ubuntu 9.10 on an Acer Extensa 4420.  It has an ATI Radeon Xpress 1250.  I have gone to the ATI/Radeon site and downloaded the proprietary driver that is supposed to correspond with my card. When I run the file as executable (in the terminal), it gives me an error saying, 

"Error: ./default_policy.sh does not support version      
default:v2: x86_64:lib32::none:2.6.31.14-generic; make sure that the version is being correctly set by --iscurrentdistro"

Can anyone help me?  Maybe tell me what this blurb means?  I really want to get my graphics working!  Please Help!

---

### Post by darkshadow on 2009-11-10
System > Administration > Hardware Drivers
Activate the drivers in their.

---

### Post by frenchfriedfaery on 2009-11-11
When I open "Hardware Drivers", the only driver to show up is my Wireless Driver.  There doesn't seem to be another option to even look for other drivers in that program.  Am I looking at it wrong?

---

### Post by lidex on 2009-11-11
You could try this howto:
[http://www.webupd8.org/2009/05/graphic-video-drivers-ubuntu-repository.html]("http://www.webupd8.org/2009/05/graphic-video-drivers-ubuntu-repository.html")
Should be foolproof.

---

### Post by frenchfriedfaery on 2009-11-11
How do I save the Public Key Server?  In what format?  I'm confused about this part.

---

### Post by frenchfriedfaery on 2009-11-11
Ok...  So disregard my last question.  I figured it out.  now, when I try to open the Catalyst Converter, it gives me an error:

"No ATI graphics driver is installed, or the ATI driver is not functioning properly.  Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig."

And the terminal says that the command, "aticonfig" doesn't exist.

---

### Post by lidex on 2009-11-11
You should probably install drivers thru jockey(hardware drivers). I have no idea what "catalyst converter" is. 
run these commands:
```
sudo apt-get update
sudo apt-get upgrade
```
Apply any updates and reboot.
Then go into jockey.

---

### Post by frenchfriedfaery on 2009-11-11
Just tried that.  Did the updates like you instructed, restarted, and opened Jockey.  The only available driver that jocky lists is the driver I'm using for my Proprietary Broadcom Wireless driver.  It doesn't look like it gives me the option to search for more.  Am I looking at the wrong place?

---

### Post by lidex on 2009-11-11
No. Try going to "system>preferences>appearance" and on the "visual effects" tab click to select the radio button for "extra". On another thread one user said his drivers (ATI/AMD) worked even though not showing up in jockey.

---

### Post by gdbutcher on 2009-11-17
You have the same problem as me, basically AMD/ATI are no longer supporting linux drivers for this GPU chipset, (even though they are still supporting them for windows, I dual boot the laptop with Windows 7 64 bit, and they have developed a driver for this)

Unless someone has found a way to force the old ATI Catalyst drivers to work in Ubuntu 9.10, your stuck with the basic open source linux drivers (created and supported by linux developers). 

Whilst they work for most apps, I have found that they do struggle with 3D programs such as games or google earth, and full screen flash videos. 

I believe the last version of Ubuntu that AMD/ATI created fully functioning drivers for this chipset was Ubuntu 8.04 or 8.10. 

If you do find a solution please post it here

---

### Post by ssri on 2009-11-17
I'm running the legacy proprietary drivers in jaunty.  I think it will be more tricky in karmic since the drivers only support kernels up to 2.6.28.  Yeah, one could downgrade xserver to version 1.5.2 (intrepid), but I would be hesitant to the prospect of downgrading the kernel to 2.6.28 from 2.6.31, quite a big drop.

---

### Post by gdbutcher on 2009-11-17
ssri how did you do this? is the 3d support any good? I have no problem with Ubuntu 9.04 it might be worth downgrading

---

### Post by ssri on 2009-11-18
> **gdbutcher said:**
> ssri how did you do this? is the 3d support any good? I have no problem with Ubuntu 9.04 it might be worth downgrading

[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

This guide worked wonderfully for me.  However, it can hose your xserver.  What I mean is that you will be greeted by a terminal login if the install process is not smooth.  To be honest, I installed the legacy drivers in Jaunty on the first shot.  As for 3D, well it is the best you can get for ATI legacy cards.  However, admittedly, 2D is faster and smoother with the opensource drivers.

---

### Post by ssri on 2009-11-18
Also, you will need to patch the legacy drivers only if you downloaded and are using 2.6.29 from ubuntu's mainline kernel ppa.  Jaunty shipped with 2.6.28.

---

### Post by gdbutcher on 2009-11-20
Thanks for this suggestion Ssri, it worked for me. I was more than happy the results, google earth and quantz both run very smoothly now. I'd only wish ATI/AMD would do an update so that it would work in Ubuntu 9.10! but i know they are no longer supporting this "old" card for linux....

---

### Post by mogliii on 2009-11-21
A bit unsatisfying.

I have a MSI K9AG Neo 2 Digital with AMD 690g chipset. This comes with the Radeon x1250.

Until 8.10 I could use the ATI driver, and I was stunned by the performance. I could play Nexuiz and Urban Terror and Stuff on low details and 1024x768.

Since 9.04 and now in 9.10 Ubuntu has the new x-server and kernel, and AMD doesnt seem to have any intention to maintain these. Even though that motherboard is not that old. And the radeonhd/opensource driver are not up to the task yet (OpenGL games hanging after ~1 min).

I am using my 16x PCIe for something else, so I would have to buy a 1x PCIe graphics card. But they are unreasonably expensive and I don't want the extra idle power consumption.

A bit a pity. Guess I will wait until the post 790 chipsets come out and upgrade all together late next year. Maybe I can use my time for something more useful than gaming ;)

But please post if anyone gets good 3D performance with the x1250 and Karmic (9.10).

---

### Post by mayur_rathi90 on 2010-02-21
i am having the same problem that frenchfriedfaery have . i have even tried the ati amd site drivers .run file and run all the deb files created but it not hapning and am not able to use the 3d effects or any desktop effects
can anyone tell me where i can find the besic graphics drivers 
and how to install them

---

### Post by mayur_rathi90 on 2010-02-21
go to this page and do as directed
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
i know it will work as expected
couse it worked for me
do and have fun 
india is great

---

