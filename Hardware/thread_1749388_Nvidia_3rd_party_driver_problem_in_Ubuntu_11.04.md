---
title: "Nvidia 3rd party driver problem in Ubuntu 11.04"
date: 2011-05-04
forum: Hardware
---

### Post by Rezwan Mahbub on 2011-05-04
Hello,
I have installed Ubuntu 11.04 and activated the Nvidia 3rd party driver  provided by Jockey as available in the  System->Administration->Additional Drivers by default. Then, I  tried to reboot, after that my computer freezes every time between grub  and logon screen. For this reason I am forced to re-install the whole  operating system (Ubuntu) several times.
My graphics card is NVIDIA GT240.
Can someone help me out showing the right way of installing the driver?

---

### Post by mörgæs on 2011-05-04
I would recommend staying with 10.10, if you have these problems.

More here:
[http://ubuntuforums.org/showthread.php?t=1743386](http://ubuntuforums.org/showthread.php?t=1743386)

---

### Post by ted_rmt on 2011-05-04
I have an Nvidia driver issue as well. Nvidia ion machine. The driver downloads and installs and the Nvidia Xserver works. In additional drivers it says the driver is activated but a line tells me it is not being used.

As a result of this I cannot enable visual effects. Tried disabling Unity in CCSM (big mistake. lost access to everything. Will post a fix)

For now, after many hours of trying, I am assuming that it is a problem between 11.04 and the nVidia driver.

Cannot enable effects in classic view either. I think downgrading as the last poster suggested might be the best advice.

---

### Post by bwallum on 2011-05-04
First try to Install Ubuntu without the nVidia driver. Ubuntu has it's own graphics driver called nouveau which is the default driver.

If you have the nVidia driver activated then de-activate it. To do this, at log on, when you see your user name click on it but do not enter your password...yet. Instead look at the bottom panel and you will see the session type. Make sure it says 'Ubuntu Classic'. Use the arrows to the right of the text field to change if necessary. Then put in your password and hit the 'Enter' key.

When you get to Desktop go to System>Administration>Additional Hardware.
Disable any graphics hardware drivers.
Reboot

After the cmos boot and before Ubuntu is loaded hold down the shift key.
The Grub menu will appear. Select recovery mode.
Choose the failsafe X option. You will be asked if you want to reconfigure the Xserver configuration file. Agree and then choose to restart the Xserver. Continue in Failsafe mode.

When you get to Desktop go to System>Administration>Update Manager
Choose 'Check' and agree to any updates offered
Reboot (this is playing safe, you may not need to)

When back to Desktop go to System>Administration>Additional Hardware
Select the 3D experimental driver (this is for 11.04) and activate.
Reboot

When you next come to the log in screen select your user name but don't put in your password...yet.
Select 'Ubuntu' from the bottom panel. Key in your password and go to Desktop.
You should now see Unity in most cases (I've fixed two out of three non starters). Stick with it, it grows on you.

It would be good to get comments on the above, good or bad, I'm still a novice with Unity.

Good luck

---

### Post by Rezwan Mahbub on 2011-05-07
I have activated all the restricted Multiverse and Universe as well as Medibuntu repository.
Tried the command :sudo apt-get install linux-headers-$(uname -r)
and
sudo apt-get install dkms build-essential
and
sudo dpkg-reconfigure -phigh xserver-xorg
 and then I found no Jockey written in the Additional drivers and then activated the NVIDIA driver. My problem solved!!

---

### Post by ted_rmt on 2011-05-08
Looks like I can enable all of the compiz fusion effects when using Unity, without changing anything I have done with the drivers. 

I will have to look into nouveau and what its capabilities are. It would be nice if there was something like that that could give me 3D graphics on another machine with Intel GMA 950 graphics.

Currently using Ubuntu classic sessions when I want stability and gaming. Tried to get my compiz 3d sphere desktop back in gnome but nothing will enable in the classic session. Frustrated me for a week or so, but now I am appreciating the stability of gnome wiothout the glitz.

Unity is glitzy. Not sure if deactivating the nVidia driver will keep it from not drawing vital menu bars whenever I make minor changes in Compiz CCSM. Relog corrects any problems and if I don't change configuration settings it seems to behave so far.

So now I just use whichever session gives me the most of what I want and everything seems to be working without doing anything fancy, at least with my nVidia machine.

---

### Post by Michelle Ellert on 2011-05-09
I'm having the same problem here. I have a Gateway LT25 notebook (new December 2010) with Intel GMA 950 chipset. I installed Ubuntu 11.04 (on a separate partition, always a good idea) and it simply can't see the graphics accelerator hardware. I'm not much on linux hacking so I'm hoping a Debian (eg .deb) package will be available soon to fix this. Ubuntu 10.04 works fine for now and that's my default boot so I'll stick with that for now. I do have the Intel driver so if someone could direct me to a utility for directly installing Windows drivers it would be greatly appreciated.
BTW, I completely expunged Windows 7 from my system and will never go back. Ubuntu rocks!

---

### Post by mörgæs on 2011-05-09
Maybe this thread will help:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by Blasphemist on 2011-05-09
Please see this page.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

There is also a link in that page to this blog.
[http://joeslifewithubuntu.blogspot.com/2010/12/update-on-nvidia-96-driver-with-ubuntu.html](http://joeslifewithubuntu.blogspot.com/2010/12/update-on-nvidia-96-driver-with-ubuntu.html)

I followed that to this on launchpad. [https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/96.43.19-0ubuntu8](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/96.43.19-0ubuntu8)

> The binary driver provide optimized hardware acceleration of OpenGL
 applications via a direct-rendering X Server. AGP, PCIe, SLI, TV-out
 and flat panel displays are also supported.
 .
 This package also includes the source for building the kernel module
 required by the Xorg driver.
 .
 GPUs ranging from GeForce series 2 (except for GeForce2 GTS/GeForce2 Pro,
 GeForce2 Ti and GeForce2 Ultra) to GeForce series 7 are supported.
 .
 See /usr/share/doc/nvidia-96/README.txt.gz for a complete list
 of supported GPUs and PCIIDs

---

### Post by ted_rmt on 2011-05-10
> **Michelle Ellert said:**
> I'm having the same problem here. I have a Gateway LT25 notebook (new December 2010) with Intel GMA 950 chipset. I installed Ubuntu 11.04 (on a separate partition, always a good idea) and it simply can't see the graphics accelerator hardware. I'm not much on linux hacking so I'm hoping a Debian (eg .deb) package will be available soon to fix this. Ubuntu 10.04 works fine for now and that's my default boot so I'll stick with that for now. I do have the Intel driver so if someone could direct me to a utility for directly installing Windows drivers it would be greatly appreciated.
BTW, I completely expunged Windows 7 from my system and will never go back. Ubuntu rocks!


I stopped trying with the GMA 950 machine after 9.10. Interesting to hear you have 3D acceleration working well in 10.04. Did Additional Drivers auto fetch that intel driver or did you have to go outside to Intel? I will have to try upgrading that machine to 10.04 to see what it can do.

Is there something in particular that Natty cannot do for you? Took me a week to realise that Natty unity sessions allowed Compiz effects to work but Natty ubuntu classic sessions do not. I had been thrown by the fact that the Additional Drivers description of my nVidia driver said the driver was activated but not in use. 

3D rendering in games works fine in both, however, whereas the same programs on the GMA 950 did not.

Just wondering if Nouveau replaces your intel drivers as well.

---

### Post by RBLevin on 2011-05-11
> **Rezwan Mahbub said:**
> Hello,
I have installed Ubuntu 11.04 and activated the Nvidia 3rd party driver  provided by Jockey as available in the  System->Administration->Additional Drivers by default. Then, I  tried to reboot, after that my computer freezes every time between grub  and logon screen. For this reason I am forced to re-install the whole  operating system (Ubuntu) several times.
My graphics card is NVIDIA GT240.
Can someone help me out showing the right way of installing the driver?

FYI, in the future, you can get past this type of problem by booting Ubuntu in recovery mode and selecting the default driver at boot time (you'll be prompted). That will get you into the OS, at which point you can disable the proprietary driver. Reboot, and you're back in business.

---

### Post by RBLevin on 2011-05-11
> **ted_rmt said:**
> I have an Nvidia driver issue as well. Nvidia ion machine. The driver downloads and installs and the Nvidia Xserver works. In additional drivers it says the driver is activated but a line tells me it is not being used.

As a result of this I cannot enable visual effects. Tried disabling Unity in CCSM (big mistake. lost access to everything. Will post a fix)

For now, after many hours of trying, I am assuming that it is a problem between 11.04 and the nVidia driver.

Cannot enable effects in classic view either. I think downgrading as the last poster suggested might be the best advice.

Same problem here. Nvidia Ion on Lenovo S12, and Nvidia GeForce on Alienware laptop. Driver is installed, activated, non-functional. Both machines exhibit flickering video and occasional broken graphics (artifacts that remain on the screen after a window closes) on the default 2-D Ubuntu driver now, as well.

Very disappointing.

PS: I also tried installing directly via the Nvidia PPA. No luck.

---

### Post by ted_rmt on 2011-05-17
I was actually having problems with flickering and artifacts BEFORE the  upgrade to 11.04. Those issues were actually resolved by the upgrade to  11.04 Natty Narwhal. 

Originally 10.10 Maverick Meerkat worked very well. The artifacts I had  were always remnants from the Adobe flash player plugin in Firefox. Inclusion of Firefox 4 in the 11.04 distro is likely what has resolved those flash issues.

To update, the new driver seems to be working fine, (at least for the  Zotac nVidia ION ITX B series). My guess is that the copy text box for  the Additional Drivers was not changed, so now it is misleading. 

I am still just guessing, but this seems the simplest explanation for  why the text in the GUI tells me that Compiz will not work without the  proprietary driver, and the same window tells me the driver is not in  use, but Compiz is working fine.

Last thing I need to do is to get Unity to stop drawing the top panel  menu when I have a program that needs to use the whole screen. Program  draws full screen but a non-functional panel bar remains. It blocks view  of top of the fullscreen blocking important indicators in games and  such.

Pretty sure this is a configuration problem, but I can't find it in CCSM  for the life of me. So far the only fix is to rerlog in a gnome session  or to turn Unity off in CCSM. Neither is ideal.

---

