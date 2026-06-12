---
title: "sVideoOut Radeon X1400 and ubuntu"
date: 2010-10-04
forum: Hardware
---

### Post by Amplus1 on 2010-10-04
Greetings,

I want to convert my old Toshiba Satellite A100-163 laptop to a Linux media center. I installed Ubuntu Lucid and it works pretty well except for the sVideo Out. At first my external screen/TV was detected but when I try to clone/extend onto the TV I get a no input signal on the TV. At the moment the TV is no longer detected. 

I have read a lot about ATI Radeon mobility x1400 problems and I know now that it is no longer supported by the ATI driver and my only option is to use open source drivers in Lucid. I'm ok with it if I'm not able to get the 3D acceleration working, I just want the sVideo out to work so I can watch movies on the TV.

So what are my options? At the moment I'm leaning towards installing an older Ubuntu version where I can run the ATI native driver. If I do that, what Ubuntu version should I go for?

On the other hand maybe I should try to tweak the radeon open source driver so it will work with my TV. I'm thinking that maybe the default output is NTC not PAL. How do I check it? Are there known problems with Radeon X1400 and sVideo and the open source radeon driver?

Any advice would be greatly appreciated.

---

### Post by Amplus1 on 2010-10-05
Latest update:

I fiddled a little bit more with the SvideoOut in Display Manager. Now I do see a garbled image on my TV, the color is off and it's quite distorted/pixelated. I can hardly make out what is being displayed. Can that be a incorrect refresh rate or resolution problem? Maybe the radion driver isn't reading the supported settings of my TV right?

I was able to get a clear picture on my tv by fiddling around in the display settings, I do not know what it was that made it work but I have gone through all the different resolution settings available for my TV several times with no avail. It just seems to happen randomly. Next time the image comes through correctly I'm going to run xrandr to see what setting is being use. Is there a GUI tool available for Xrandr in Ubuntu?

the screen has twice gone completely black during this process where I had to force shut down my computer to get it sorted. Furthermore I did a software update and left the computer on for some time, when I came back to it the screen was completely black and did not come back on, but I was able to go into command line and restart from there. Any help would be greatly appreciated

---

### Post by Mark Phelps on 2010-10-05
> **Amplus1 said:**
> At the moment I'm leaning towards installing an older Ubuntu version where I can run the ATI native driver. If I do that, what Ubuntu version should I go for?

I believe that 8.10 is the last one for which "legacy" card proprietary driver are available and work with the X-server version in Ubuntu.

I know they were no longer available in 9.04 because when I upgraded, I lost fglrx support.

---

### Post by Amplus1 on 2010-10-06
Thanks for the reply Mark. Is there a way for me to test Ubuntu 8.10 from a cd with the ATI driver loaded? Can I set boot options so that it will load? I did download and burn 8.10 and I was able to:

* Boot from CD
* Connect to Wireless
* Run hardware drivers program that detected the Radeon
* After I downloaded, istalled and enabled the ATI driver it asked me to restart but then nothing is retained and I can't test the system running with the ATI driver :(

Can I restart the x server without having to restart the system? In other words, can I make Ubuntu use the ATI driver without restarting or have it load during the CD boot?

---

### Post by Amplus1 on 2010-10-08
Latest update:

I couldn't find a way to test the ATI driver by booting from the CD. I created a USB pen drive startup disk, booted from it and enabled the ATI driver but the setup wasn't retained after reboot from the usb drive (I thought it might work since it is write-able media, which would be cool by the way). 

I went ahead and installed 8.10 and enabled the ATI driver. It worked for a short while (display was cloned by default) but when I fiddled a bit with the display settings both screens went black. Both screens turned black on restart if I had the TV plugged in while starting up. 

Finally I followed the installation guide on:

**[Installing the restricted drivers manually]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually")**

I installed version 9.3 of the driver.

After that I am able to clone the desktop with 1024x768 resolution on both screens. However I haven't been able to use the extended/big desktop setting but the clone mode should be fine for my purposes. Next step is to install a media center...

Is it possible to Install the legacy proprietary drivers manually on Lucid (10.04)?

---

