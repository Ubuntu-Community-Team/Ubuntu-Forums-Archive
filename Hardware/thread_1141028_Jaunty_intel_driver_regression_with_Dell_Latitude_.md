---
title: "Jaunty intel driver regression with Dell Latitude D630"
date: 2009-04-28
forum: Hardware
---

### Post by oimon on 2009-04-28
hi
anyone performed a clean install of jaunty on a Dell Latitude D630 laptop with intel graphics card?
I wiped 8.04 (worked great) and put 9.04 on last night. 
First problem i noticed was the "vesa" driver was being used. Switched to intel and got the correct resolution, but desktop effects/compiz cannot be enabled.

Maybe if someone has this working they could post their xorg.conf

thanks

Edit: Found some info on this. Intel GM965 cards are widely used - this is not good!
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363821](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363821)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392)

---

### Post by benbelly on 2009-04-28
I just upgraded my D630 to Jaunty, and I seem to be having graphics problems.  My available resolutions 600x800 and 1024x768.  I'm on a 1600x1050 monitor that worked before the upgrade.  Can you tell me how you knew that the VESA drivers were being used and how you corrected that?

Thanks,
-Ben

---

### Post by oimon on 2009-04-28
hi benbelly
i noticed /etc/X11/xorg.conf contained a line 
Driver "vesa"

I had problems booting from the livecd so i used safe graphics mode initially, which created a xforcevesa command in the kernel boot options in /boot/grub/menu.lst.
I removed this in order to stop the vesa override (which is not required)

---

### Post by pixolex on 2009-04-29
> **oimon said:**
> hi
anyone performed a clean install of jaunty on a Dell Latitude D630 laptop with intel graphics card?
I wiped 8.04 (worked great) and put 9.04 on last night. 
First problem i noticed was the "vesa" driver was being used. Switched to intel and got the correct resolution, but desktop effects/compiz cannot be enabled.

Maybe if someone has this working they could post their xorg.conf

thanks

Edit: Found some info on this. Intel GM965 cards are widely used - this is not good!
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363821](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363821)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392)

I have the exactly same problem with my Dell D630.

Thanks for the links of the bugs, I have already subscribed them.

---

### Post by Nemo34 on 2009-06-17
Same here. Upgrade to 9.04 was great because it brought me OpenOffice 3.0 and better multiple screen support but I lost all the special effects such as 3D, cube, blobing windows and so on.

Considering reverting to 8.04 that was a really good release

---

### Post by oimon on 2009-06-17
i agree with you there - however the 8.04 release had issues with intel wireless. e.g. cannot enable wireless if you boot with the wireless turned off.
however currently i cannot run docky, which is a big shame.

if it was my main work machine i would definitely downgrade but since the wife isn't complaining (and she likes the new notification system) then i'll limp along until karmic (while hoping the issue is fixed). october seems a long way away!

---

### Post by john_navarro on 2009-06-18
My video issues were fixed by downgrading the video driver using these instructions:

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4")

---

### Post by s_baramov on 2009-06-19
I have a D620 (the one before D630) and my video is : 

```
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
```

Adding this line an option  "AccelMethod" "XAA" to the xorg.conf helps. The "Device" section of xorg.conf looks like this :

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver          "Intel"
	Option		"AccelMethod"	"XAA"
EndSection

```

---

### Post by kronidas on 2009-06-20
Bingo !!! On my Dell d630 I did 

1) Add the following lines to your /etc/apt/sources.list: 

 deb [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main
 deb-src [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main

2) Import the appropriate GPG key: 

 $ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.

3) Install the driver: 

 $ sudo apt-get update
 $ sudo apt-get install xserver-xorg-video-intel-2.44) Restart X by running "sudo /etc/init.d/gdm restart"

It works. Video is fixed ! 

Many thanks!

---

### Post by Kazonri on 2009-08-16
Sorry noob here.  I was able to add the item to my sources.list.
But how do I "Import the appropriate GPG key?"

when I type "$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu" nothing happens.

I guess I need to know the key ID to type at the end of the last statement, but being a noob I have no idea how to figure that out.

So when I type "$ sudo apt-get update" I get "public key is not available" for ppa.launchpad.net.

Please help because I have no idea how to get the drivers working right for my D630.

---

### Post by oimon on 2009-08-17
kazonri
compiz should be working on this graphics card now, i am getting on OK with the regular drivers provided by jaunty.
however if you want to revert to the old drivers follow this instruction
[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)
it seems you missed a part of the import keys line.

---

