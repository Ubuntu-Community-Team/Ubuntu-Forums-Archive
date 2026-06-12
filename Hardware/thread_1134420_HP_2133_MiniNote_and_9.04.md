---
title: "HP 2133 MiniNote and 9.04"
date: 2009-04-23
forum: Hardware
---

### Post by jarome on 2009-04-23
Does anyone know if 9.04 works on the HP 2133 MiniNote? The wiki [https://wiki.ubuntu.com/LaptopTestingTeam/HP2133](https://wiki.ubuntu.com/LaptopTestingTeam/HP2133) is mum on this. If so, what must one go through to get it all up and going? Does an upgrade work?

And will the notebook remix work on the Via processor in the MiniNote? The download page says Intel Atom.

---

### Post by Barry Carroll on 2009-04-24
The remix will run fine with your processor because it's x86 based.  I have 9.04 running on VIA hardware: Samsung NC20 with Nano CPU and VX800 graphics.  

I found the following page useful: [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome) as I had to compile my own display driver (very easy).  You might not need to do that though - I was getting a blank screen so I did ;)

Why not write the image or iso to a usb stick and give the live environment a go?  You'll be able to see if your stuff works then.

---

### Post by jarome on 2009-04-24
Well, the video works just fine, but my Broadcom BCM4312 is very dead. Does the full installation fix this somehow?
I tried to install the hardware driver. But now I can't boot off the jump drive.

And the new Gnome desktop has me totally confused. I can't find any way to add things to the top menu or to get multiple desktops. Is this supposed to be a step forward? Is there a tutorial on how to use this new desktop?

I also do not see the cpu frequency controller (which conserves power). So where are all the wonderful things for netbooks located?

Well removing and reinserting the USB drive lets me boot off it. But the installed wireless drivers are gone, and after installing them, a reboot is required to use them. Catch 22. How does one install the wireless on the USB? I tried both the B43 and BSTA drivers.

---

### Post by Barry Carroll on 2009-04-25
Sorry, I don't know about your broadcomm card as I use an intel 5100 for wireless.  Are you using the normal install or the netbook remix?

If you want to add something to the top panel you can right-click, select add to panel and add the cpu frequency scaler applet there.  Initially mine said that my cpu did not support frequency scaling so I had to add e_powersaver to /etc/modules.  I don't know if that's a general via fix or something specific to the nano though.

On my desktop I have the multiple desktops at the lower right of the screen and by right-clicking I can configure them or add more.

---

### Post by jarome on 2009-04-25
The regular 9.04 (boot off CD) gives a real desktop. The Notebook Remix looks like the awful HP Linux desktop. Everything is full screen, the whole desktop is cluttered. It is truly awful.

But I am scared to upgrade until the mininote wiki is updated for 9.04.

But there seems no way to install a driver that is persistent in a live boot scenario.

---

### Post by peakshysteria on 2009-04-25
Installed 9.04 on our HP 2133 last night. Everything except the Wifi worked out of the box. Booted from an usb dvd drive. It's really strange that the wifi don't work since it detects our network and let us log on to it (WEP). Damn strange. Very pleased to see that the install process itself went without any problems. Especially pleased tosee that the display finally has the right resolution (1280x768).

---

### Post by Barry Carroll on 2009-04-25
If you don't have a usb dvd drive you could also try unetbootin to write the standard iso to a usb flash drive.

---

### Post by jarome on 2009-04-25
Peakshysteria,

So were you able to get wifi to work after you installed the Broadcom driver.

And does frequency scaling work?

---

### Post by peakshysteria on 2009-04-25
> **jarome said:**
> Peakshysteria,

So were you able to get wifi to work after you installed the Broadcom driver.

And does frequency scaling work?

I were ale to get it working tonight actually. Not sure it is the driver that is the problem any longer.I'll report back as soon as I figure it out.I got it working for about 45 min. Then working very very smooth. But then suddenly shutting down.

---

### Post by jarome on 2009-04-25
Hardy did that for me also. Wireless died after a while. And then I usually could no longer see the adapter. I filed a bug. But it is still there.

Add your voice to [https://bugs.launchpad.net/ubuntu/+bug/293631](https://bugs.launchpad.net/ubuntu/+bug/293631)

---

### Post by mrxoliver on 2009-04-29
With me, the wireless wouldn't work after the screen went blank/ after hibernating. After lots of burrowing around, this seems to make it work:

Make knetworkmanager load on login and use this for the network management.

If the wireless goes down, go into

System settings --> service manager

and stop running the network status daemon.


There seems to be some clash of code between the KDE network status daemon and the wireless driver. Any ideas how to disable the daemon for good?

---

### Post by peakshysteria on 2009-04-30
> **jarome said:**
> Peakshysteria,

So were you able to get wifi to work after you installed the Broadcom driver.

And does frequency scaling work?

All is working smooth now. The problem seemed to be the Wi-fi router :) Meaning all worked out of the box.

jarome; I haven't tried the CPU Frequency Scaling Monitor if that's what you mean. CPU seems fine. Not able to cook bacon on it any more. The whole box seems cooler than with Intrepid actually (8.10 seemed to get very hot from time to time).

---

### Post by kutjara on 2009-06-01
I installed 9.04 Desktop on my 2133 yesterday and everything worked out of the box. The only issues I encountered were:

- After Ubuntu installed the restricted Broadcom wireless driver and I subsequently rebooted, my screen resolution was messed up. This is a known issue, the fix for which is to insert the correct resolution into xorg config, which takes about 30 seconds.

- I thought wireless wasn't working, until I noticed the wireless button on the front of the 2133 had defaulted to "off". Sliding it to "on" solved that problem.

9.04 on the 2133 has been the most painless Linux install I've yet encountered on a laptop. Compared to glacially-slow Vista that came preinstalled, Ubuntu is a speed demon.

---

### Post by jarome on 2009-06-01
What about the cpu frequency scaling, the audio in/out and the video output? Do they work?

---

### Post by kutjara on 2009-06-01
> **jarome said:**
> What about the cpu frequency scaling, the audio in/out and the video output? Do they work?

I haven't tested all of those features yet.

For CPU scaling, I haven't installed the CPU toolbar app yet to see if the feature works, but, if not, I'll try the old trick of replacing "xforcevesa" with acpi_osi="!Windows 2006" in grub.

The onboard audio works well and the microphone was recognized, but I have heard of problems with Skype, so I'll check that out this evening.

Video works well, with YouTube and WMV movies playing smoothly. The webcam works well with Cheese. I haven't tried outputting to a monitor yet, but I'll give it a test and report back.

---

### Post by jarome on 2009-06-01
Well, I tried the auto upgrade. It has trouble using the hi-res display. Claimed that freetype was not installed, but it was. I rebooted, and it still does not work. It puts me into low res graphics mode on display 1. I an not sure how to fix this. It gives me a choice of using the default configuration, but somehow I think that will not work. What did you do?

And also, the cpu scaling did get wiped out. The boot/grub/menu.lst is quite different, I hope replacing the xforcevesa will work. It does not seem to. I edited the commented out line (which it says not to uncomment) but to no avail. Well, I did not look down far enough in the file. I'll try another reboot. That fixed it

But I still am stuck in low mode graphics (although it looks good).

The wireless seems to work if I turn it on.

---

### Post by kutjara on 2009-06-01
> **jarome said:**
> Well, I tried the auto upgrade. It has trouble using the hi-res display. Claimed that freetype was not installed, but it was. I rebooted, and it still does not work. It puts me into low res graphics mode on display 1. I an not sure how to fix this. It gives me a choice of using the default configuration, but somehow I think that will not work. What did you do?

And also, the cpu scaling did get wiped out. The boot/grub/menu.lst is quite different, I hope replacing the xforcevesa will work. It does not seem to. I edited the commented out line (which it says not to uncomment) but to no avail. Well, I did not look down far enough in the file. I'll try another reboot. That fixed it

But I still am stuck in low mode graphics (although it looks good).

The wireless seems to work if I turn it on.

First off, I did a clean install. Most of the problems I've seen on the forums are from people who upgraded to 9.04. It seems the upgrade is keeping some old settings from 8.10 that it probably shouldn't.

When I did the initial install, everything was perfect except the wifi. After a couple of minutes, Ubuntu recognized the Broadcom card and warned me that it needed to install the evil proprietary driver for this card. I OKed it and the driver was duly installed. I suddenly had wifi and was able to connect to my home network. Fabulous!

When I rebooted later in the day, however, I saw that the screen had reverted to 640x480. A bit of googling showed me that this was a fairly common problem, related to the Broadcom wifi driver (don't ask me why a wifi driver has the ability to hose graphics settings...nobody seems to have the answer to that one). Fortunately, the problem is easily fixed:

Open xorg.conf in the editor of your choice and look for the following entry:

Section "Device" 
    Identifier    "Configured Video Device"
EndSection

Edit the section, so that it looks like this:

Section "Device" 
    Identifier    "Configured Video Device"
    Option "PanelSize" "1024x600"
EndSection

Save the newly-edited xorg.conf, restart x-server and you should be back to hi-res happiness.

Of course, if you've got one of the bigger screen models that is capable of 1024x768, put that into the Option line instead.

---

### Post by jarome on 2009-06-01
Strange. The xorg.conf file on my updated OS seems to know all about the HP 2133. Many many specific settings for it, including the correct resolutions (1280x768).
There is no Identifier "Configured Video Device" anywhere.

freetype is in the Module section (after the Input Devices sections). Commenting it out stopped the error message, but I am still in lo-res graphics on Display 1. It looks quite good though, so I am not sure what the current resolution is.

Well, the freetype issue is a know bug. [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/373917](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-savage/+bug/373917)
I commented it out as per the bug resolution. But X is still not happy.

---

### Post by kutjara on 2009-06-01
> **jarome said:**
> Strange. The xorg.conf file on my updated OS seems to know all about the HP 2133. Many many specific settings for it, including the correct resolutions (1280x768).
There is no Identifier "Configured Video Device" anywhere.

freetype is in the Module section (after the Input Devices sections). Commenting it out stopped the error message, but I am still in lo-res graphics on Display 1. It looks quite good though, so I am not sure what the current resolution is.

Strange indeed. All I can think is that the difference is either the result of the fact that you upgraded, while I clean-installed, or that your 1280x768 model uses a different chipset than my 1024x600 one.

If you post your xorg.conf file, I'll compare it to mine and try to see what the differences are.

---

### Post by jarome on 2009-06-01
I think I attached xorg.conf and the Xorg.0.log as zip files.
I presume that it is the 0 display that is the issue, since I am put on the lo-res 1 display.

The exact message i see is:
"Ubuntu is running in low Graphics mode. Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself"
In the startup log, it says:
/usr/X11R6/bin/X: symbol lookup error: /usr/lib/xorg/modules/drivers/via_drv.so: Undefined symbol: x86GetVersion

Thanks,
Jim

---

### Post by jarome on 2009-06-17
I am still stuck here. Please help.

---

