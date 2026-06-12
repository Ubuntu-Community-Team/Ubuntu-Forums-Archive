---
title: "New Video Card Woes (Nvidia GTS250)"
date: 2009-05-08
forum: Hardware
---

### Post by djuke04 on 2009-05-08
First off,
  I'll thank you for your time and assistance.  

  I just purchased and installed a new video card: Nvidia, GeForce GTS250.  Linux and my build did some rather screwy things when first starting up.  To begin with, the first "boot" lasted about two seconds - the fans fired, and everything shut down.  I've had that happen before, so I let it go and "booted" again.  The second time it went past the BIOS screen and just stopped everything with a cursor flashing on a black backdrop, nothing else.  Okay, lets try this again, "reboot" and it comes up like I expected it to, running in low-graphcs mode and upset about it's new hardware.

  Soon enough however, it went looking for a driver for the new hardware and found the Nvidia drivers wherever it gets them from (that magical interweb).  Ubuntu found two - the (180) and the (177).  It recommends the 180, but that doesn't seem to work at all.  It doesn't do anything more than it did without "drivers."  So I thought I'd try the 177, which DOES work.  And like everything with Linux, it works "but..."

  I can't get any sound out of my motherboard.  Not only that, but every application that uses sound freezes and needs a force-quit.  Yuck Nvidia! Also my entire system seems to be running about 3-4 seconds slower than before.  That's no good, I'd rather stick with the 20 fps my on board graphics gave my HDTV than have no sound and a slow computer! So I went looking on the Nvidia website for drivers, and found this:

[http://www.nvidia.com/object/linux_display_amd64_180.51.html](http://www.nvidia.com/object/linux_display_amd64_180.51.html)

  It seems like recently they developed drivers for 64-bit Linux systems.  I however am relatively new to Linux.  Based upon the information in the page linked above, I do not undestand how to install this driver.  I read the attached "how to" and it involved more than I understand.  

WHAT I'M LOOKING FOR FROM THIS THREAD:

  Can I get this card to work with my computer? 

      Specs:
      G43 Intel board - Q9400 Quad - 8 gigs 1066 - I think that's all that might matters

  Is this card too new (Nvidia released the drivers "21 April 2009") to expect support quite yet? 

  Do the steps they list make sense for installing the drivers?



I REALLY appreciate any help you might be able to give me here, thanks so much!

---

### Post by DJYoshaBYD on 2009-05-08
its not nvidia's fault at all.. its a config problem on your system.. you should be using the 180 driver, as that is the best one out right now..

you should use EnvyNG to install your drivers, and if that doesnt work, then there is something else with your system causing these issues.. perhaps the 64 bit is the issue.. download EnvyNG from here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

which version of ubuntu are you using?

---

### Post by djuke04 on 2009-05-08
I'm running 8.10, should I upgrade to 9.04? I've been debating it but I thought that patience wouldn't hurt.

I didn't mean to blame Nvidia, in fact I'd first blame myself and my unfamiliarity with this system.  

I'm installing EnvyNG right now. Thank you for your VERY prompt response!!!  I wouldn't be surprised if I have questions about this very soon still.

---

### Post by djuke04 on 2009-05-08
Alright I got EnvyNG, and used it to install the new 180 driver, and it reverted to low-graphics mode again.  I don't see how 64-bit could be the problem, but am not dismissing it.  Should my next step be to upgrade to Jaunty?

---

### Post by DJYoshaBYD on 2009-05-08
jaunty will make your issues worse.. look at other posts in this forums.. almost all the recent ones are about jaunty and graphics.. I think your issue is the 64 bit stuff.. try the 32 bit..

---

### Post by djuke04 on 2009-05-08
Alright, well Nvidia makes a driver for 64-bit Linux.  It's at the link that I posted the first time, but is here again:

[http://www.nvidia.com/object/linux_display_amd64_180.51.html](http://www.nvidia.com/object/linux_display_amd64_180.51.html)

On that page, they list "step 2," which is to download a file.  What am I supposed to do with that file?  Their step 3 is to 'Type "sh NVIDIA-Linux-x86_64-180.51-pkg2.run" to install the driver.'

So I assumed that is at a command prompt, but when I do that is says "cannot open" or something to that effect.  

[SIZE=2]What do I need to do in order to install the drivers off of the Nvidia website?[/SIZE]

As far as I can tell, EnvyNG doesn't do anything differently than the "Hardware Drivers" tab under "System Administration" does, which doesn't give me any sound, crappy looking HDMI output, and the latest (180) driver doesn't do squat.

---

### Post by djuke04 on 2009-05-09
I have gotten the 177 driver to work and produce satisfactory results using the D-Sub output only, not the HDMI as I would prefer.  However, all programs that use sound now freeze up, and the system cannot produce any sound at all.

This is frustrating because it seems like so many NVIDIA users have success with their cards.

What else might I try?

---

### Post by djuke04 on 2009-05-09
Alright,
  I've found another resource I'm curious about:
> 
**Debian GNU/Linux or [K]Ubuntu with Xorg 7.x**

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:
[INDENT][FONT=Courier New]* development tools like *make* and *gcc* are installed
* the *linux-headers* package matching the installed Linux kernel is installed
* the *pkg-config* and *xserver-xorg-dev* packages are installed
* the *nvidia-glx* package has been uninstalled with the *--purge* option and the files [FONT=Courier New]/etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel[/FONT] do not exist[/FONT][/INDENT]If you use Ubuntu, please also ensure that the *linux-restricted-modules* or *linux-restricted-modules-common* packages have been uninstalled. Alternatively, you can edit the [FONT=Courier New]/etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common[/FONT] configuration file and disable the NVIDIA *linux-restricted* kernel modules (*nvidia*, *nvidia_legacy*) via:
[INDENT][FONT=Courier New]DISABLED_MODULES="nv nvidia_new"[/FONT][/INDENT]Additionally, delete the following file if it exists:[INDENT][FONT=Courier New]/lib/linux-restricted-modules/.nvidia_new_installed[/FONT][/INDENT]**Please note:** unfortunately, it has become difficult to keep track of the pre-/post-installation steps required for [K]Ubuntu, and the above instructions may be incomplete. If in doubt, it is recommended that you use your distributor's NVIDIA Linux graphics driver packages, exclusively.


If you require further assistance after following the instructions above, please see:
[http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678).


I've made the ammendments to my system as described above.  Now should I just run the driver install all over again?

Is this necessary and would it perhaps solve my problems?
Do I have Xorg 7.x?
If I have linux header for "2.6.27-11" AND "2.6.27-7", is that an issue?

---

### Post by djuke04 on 2009-05-09
After the ammendments, the next boot up stopped at tty1, and the desktops wouldn't start.  I then did:

sudo sh NVIDIA-Linux-x86_64-180.51-pkg2.run

And it went back through the set up, throwing up various problems like "Cannot create file," etc etc for about ten different things.  I realize this information would be helpful to have, but it didn't exactly give me time to write it all down.  So I finished the setup, and restarted, expecting to return to tty1, but instead it booted up all the way to a desktop, outputting in full 1080p like I want, with awesome graphics processing capabilities etc.

When I look under the Hardware drivers tab, it shows that neither 180 or 177 are activated and being used.  I expect that has something to do with the tomfoolery of all those changes I did before this current driver install, based on the instructions I quoted.  

Basically the graphics work! Fine I feel.  I didn't try HDMI yet, but if it comes down to it, I'm not going to mind if it needs to stay on D-Sub, the TV loves it just the same.

NOW FOR THE PROBLEMS

The system is still running slower than before.  Why? 
Also, the sound still doesn't work, and every program that tries to make a sound, such as the sound configuration utility under the preferences menu under System, or rhythmbox, or movies, basically all the good stuff that I want this computer to do, they freeze up and require a force quit.  

I'm still trying to use onboard sound, do I need to go get a separate audio card?

Or what can I try to get this to work?

Where do I even start troubleshooting?

____________________________________

I know I threw A LOT of stuff down here in this thread, so THANKS SO MUCH!!! For following, reading, and helping me out.  I'm learning gobs and gobs as I mess around with this stuff, and I love it more and more all the while.  I can't wait until I'll actually be able to give back to this community instead of just take from it.

---

### Post by djuke04 on 2009-05-12
Alright I hate bumping, but I really need some help here.

I think the graphics are working alright, but I have a problem with my sound.

After I installed the graphics card, I stopped getting any sound, and most programs that output sound freeze up.

Where can I even go to troubleshoot this?

What's the first thing I should look at?

Thanks really so so much for helping me out!

---

### Post by gjn on 2009-05-31
I bought this card in March when it was released and it was not supported by Nvidia on Linux yet. Now it is at driver level 180.51. It is not supported by Unbuntu prior to 9.04. I opened a bug report to get it include in jaunty and it was done. However it does work on 8.10 and even on 8.04.2 with occasional freeze. Use the recommended 177 driver on 8.10 and 180 on 9.04. Driver 180 does not work on 8.10.

You do not need (unless different on Intel) to use the nvidia drivers that you get directly from nvidia.com. Nothing wrong about them, you need to re-install them for every kernel upgrade. This is done for you when you use the Ubuntu packaged recommended driver. Use a Live CD to test the card and the driver. 

If you decide/need to install nvidia drivers from nvidia.com, you need to do it the right way:
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

Note: I was not familiar with PCI express card, make sure you connect the 6 pin power cable from the power supply to your card.
I have an AMD 64 bit machine. 

Here are my notes I have taken while testing my card with 8.10. For 9.04, it works right out of the box, at least for me. There might be problems with specific features, I don't know. Keep in mind you are trying to use a card that is unsupported by Ubuntu at 8.10 and unsupported by Nvidia at 177. Out of the box (or out of the Live CD) the "vesa" driver is loaded. With the workaround, the "nv" open-source driver is loaded which allows you to select the restricted driver. 


===========================================================================================================
Behaviour of NVIDIA GeForce GTS 250 under 8.10 Hardy

This card was released March 3rd 2009 and it's pci device id 0x0615 is not recognized by the open-source "nv" driver. I wanted to document how the system behaves on a known good computer/card to help people debug their installation. I used the Live CD to make comparaison reliable.
Troubleshooting information can be found at [https://wiki.ubuntu.com/X/Troubleshooting/OnlyLoadsVesa](https://wiki.ubuntu.com/X/Troubleshooting/OnlyLoadsVesa). 


After First Boot
================
First make sure you have the card you think you have. 
Partial output of lspci -v
01:00.0 VGA compatible controller: nVidia Corporation Device 0615 (rev a2)
	Subsystem: eVga.com. Corp. Device 1155
The subsystem line represents the manufacturer of the card, e.g. EVGA, XFX, Giga-Byte, etc...

The /etc/X11/xorg.conf is automatically generated at startup. Do not specify the driver name in there. Because the card is not recognized, the vesa (xserver-xorg-video-vesa) driver is loaded. Otherwise the "nv" driver would have been loaded.

In /var/log/Xorg.0.log, verify the presence of those lines:
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) No matches found for this device in /usr/share/xserver-xorg/pci
(==) Registering 'vesa' as fallback
(==) Matched vesa for the autoconfigured driver

In System->Administration->Hardware driver, the Nvidia binary driver version 177 is available, but not yet activated. The default resolution used may not be what you expect, but in my case the LCD native resoltion of 1280x1024 was selected. So I have a perfectly working desktop.


Workaround to use xserver-xorg-video-nv driver
==============================================
I have added device id 10DE0615 in the /usr/share/xserver-xorg/pci/nv.ids file. I restarted the desktop (Ctrl-Alt-Backspace).
The content of /etc/X11/xorg.conf has not been change. You may customize it as per the X server and nv driver spec. Do not specify the driver name. Now that the card is recognized, the nv driver gets loaded as evidenced in the xorg log:

In /var/log/Xorg.0.log, verify the presence of those lines:
nVidia Corporation unknown chipset (0x0615) rev 162
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched nv from file name nv.ids
(==) Matched nv for the autoconfigured driver
(II) LoadModule: "nv"

System->Administration->Hardware driver: Nvidia version 177 is recommended
System->Preferences->Screen Resolution: LCD panel is detected and correct native resolution is used.

Using the unsupported Ubuntu packaged NVIDIA Corp binary driver v.177
==========================================================================
System->Administration-> Hardware driver: click on the Activate button
Restart desktop (you are asked to reboot, but you can't in Live CD)

The content of /etc/X11/xorg.conf was changed to specified the driver name "nvidia". You may customize it as per the X server and nvidia driver spec. The NVIDIA Corp driver gets loaded as evidenced in the xorg log:

In /var/log/Xorg.0.log, verify the presence of those lines:
(II) Module nvidia: vendor="NVIDIA Corporation"
(II) NVIDIA dlloader X Driver  177.82  Tue Nov  4 16:56:15 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs

System->Administration->Hardware driver: Nvidia version 177 is shown as installed
LCD panel is not detected, but correct native resolution is used. 

Note that NVIDIA Corp GST 250 driver support starts at version 180.51. I tried v180 but X was unable to load it.
Complete guide: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by tommah04 on 2009-05-31
> **djuke04 said:**
> Alright I hate bumping, but I really need some help here.

I think the graphics are working alright, but I have a problem with my sound.

After I installed the graphics card, I stopped getting any sound, and most programs that output sound freeze up.

Where can I even go to troubleshoot this?

What's the first thing I should look at?

Thanks really so so much for helping me out!



if you didn't do anything else except the graphics card, then that's wierd....

but you could try opening Volume control and make sure your soundcard is selected....then Preferences and make sure everything is checked..... in Volume Control window, some people (including me) have had results unchecking Line Jack Sense, Headphone Jack Sense, and External Amplifier under the Switches tab.

if that doesn't work, you could always try this...
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by djuke04 on 2009-06-04
First and foremost, thanks for all the helpful suggestions.  This has not only been an incredibly educational experience, but a wonderful interaction with the community here.  

I could not get onboard sound working.  That being said, I threw in a crappy old sound card and it just worked.  No configuring, no messing around, it just works great.  

Maybe there's some sorta fluke with my BIOS or specific motherboard that it doesn't like onboard when you have a graphics card.  Oh well, 1080p movies are working great, and everything is good to go for now.  

Thanks again for all your help everyone!

---

### Post by carbonbased on 2010-02-06
I'm going to tack this reply onto the end of this thread, for the record. Anyone searching for install help with the Nvidia GTS 250 is likely to find it.  All you need to do is download the driver from this page: [http://www.nvidia.com/Download/index5.aspx?lang=en-us](http://www.nvidia.com/Download/index5.aspx?lang=en-us)

Be sure to use the drop down menus to select your card and which Linux, 32 or 64 bit versions. The driver number currently is 190.53.  It is not available in any Ubuntu driver packs.

Download it to an easy to find folder. Reboot and at Grub menu select Repair option, then scroll down to Root shell option.

At the command line type, sudo telinit 3. You'll be asked for password.

Next, find your directory and type, sudo sh <filename>.  If you're a newbie, you can type the first few letters of the filename, hit the Tab key, and the shell will auto-complete the name--watch out for case in names.

Follow the menus and reboot. 

Watch out for updates wrecking your drivers. That's the reason I just happen to be passing by this thread, an update retro'd my driver and I had to reinstall.

Ciao

---

