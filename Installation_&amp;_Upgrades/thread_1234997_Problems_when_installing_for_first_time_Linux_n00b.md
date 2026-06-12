---
title: "Problems when installing for first time Linux n00b"
date: 2009-08-08
forum: Installation &amp; Upgrades
---

### Post by chrisxuk on 2009-08-08
Hi there,
2nd post on the forums, so go easy on me ;)

Anyway, i've decided to try Linux :)
I downloaded the latest .iso of Ubuntu and burnt it too a CD and DVD following the guide on Ubuntu's main website. This seemed to go successfully so decided to try and install.

Restarted PC and set it to boot from CD-Drive. Did this alright, and just waited for a few seconds and then a Ubuntu loading screen came up. I thought 'Excellent, it's working first time'. 

It seems i thought wrong :(

Once the loading screen had gone, my monitor (I use my TV) just went blank, and i had the No Signal blue screen. Any ideas of what has gone wrong?

This is a photo of my build (Although i don't have the monitor, i decided to save some money and use my TV instead   HDMI -> HDMI)

[IMG]http://i32.tinypic.com/2s8gwi8.jpg[/IMG]


Anyway, i hope this all makes sense. If not, don't hesitate to ask me anything :)

Thanks in advance

Chris

---

### Post by T-Train on 2009-08-08
If you just let the Ubuntu install CD run it will default to the "live CD" option.  The live option will load in memory and run without installing anything.  Can you post a screen shot of the error screen?

---

### Post by cariboo on 2009-08-08
Try starting in safe graphics mode. Press F4 at the menu screen, the select safe graphics mode and then start the Live CD. This will have no effect on your installation, it is just that your TV is not being detected properly.

---

### Post by chrisxuk on 2009-08-08
Thanks for the fast reply!

I will get a screenshot for you, just not on my PC at the moment. I will have one for you later :)

Chris

---

### Post by chrisxuk on 2009-08-08
> **cariboo907 said:**
> Try starting in safe graphics mode. Press F4 at the menu screen, the select safe graphics mode and then start the Live CD. This will have no effect on your installation, it is just that your TV is not being detected properly.

Thanks also for the fast reply!

Once again, i will also try this later. Hopefully it will work

Chris

---

### Post by aesis05401 on 2009-08-08
Launchpad bug related to hdmi signal to monitor dropping, hdmi troubleshooting page linked to from comments (in case they help):

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/289177]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/289177")

[https://wiki.ubuntu.com/X/Config/HDMI]("https://wiki.ubuntu.com/X/Config/HDMI")

---

### Post by chrisxuk on 2009-08-09
Hi there,
Right, Ubuntu is installed. Pressing F4 at startup and entering Safe Graphics Mode worked :)

However, all's not so good. I seem to have another problem now :(  Basically the resolution on my screen is wrong. I've been into the Display settings and there is only 640 x 480 (4:3) available. Is this all you get with Linux? Or are there other resolutions available.

Unfortunately, i don't think i could continue to use Ubuntu if i can't change the ratio as it's cutting off half the screen :(

Once again, thanks in advance for any help that you can give :)
Chris

---

### Post by eVAPor8 on 2009-08-09
My guess it the problem is with your graphics card drivers.

I'm guess it's a fairly new nVidia or ATi. nVidia has a "native" driver for linux, you should be able to surf to nvidia.com, choose the Drivers section and download the latest driver package after automatic detection. ATi seems somewhat thornier (and I no experience with ATi cards).

Once you've got the nvidiaxxxyyyzzz.123.run file you need to two things:

* Set it to "executable"
* Run it (and install)

 You can do this in gnome by right-clicking and going to Properties, set the "executable" checkbox.
Then double-click to run it.

Or you can do it in the CLI by running terminal, CD'ing to the folder you downloaded and then

chmod +x nvidiafilename.run
./nvidiafilename.run

Once the native drivers are installed you're problems may well disappear (and your card will run MUCH faster). It sounds to me like the card is running the standard drivers and can't correctly interrogate the TV when it boots so it's defauting to the "lowest common denominator" to be on the safe side and *not* destroying £1000's of your telly! ;)

---

### Post by chrisxuk on 2009-08-09
Thanks for the reply, doesn't look to hard to do :)

On my EEE at the moment, so when i'm back on my desktop i'll follow what you said and hopefully i'll get some good results

Thanks again
Chris

---

### Post by ugm6hr on 2009-08-09
It should be possible to use the restricted driver.

Just confirm the chipset here by giving the output from:
```
lspci
lshw -class network
```

But it looks like GForce 6100 [http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2755](http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2755)

Look in Hardware drivers (in System Menu) to see what options you have.  Be warned that it is possible you may end up with a blank screen again, but this can be rectified from Recovery Mode if required.

---

### Post by chrisxuk on 2009-08-09
Hi there,

> **ugm6hr said:**
> It should be possible to use the restricted driver.

Just confirm the chipset here by giving the output from:
```
lspci
lshw -class network
```But it looks like GForce 6100 [http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2755](http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=2755)

Look in Hardware drivers (in System Menu) to see what options you have.  Be warned that it is possible you may end up with a blank screen again, but this can be rectified from Recovery Mode if required.

Heres what i get for lspci :)
```

chris@chris-desktop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
02:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]
02:00.1 Audio device: ATI Technologies Inc HD48x0 audio
chris@chris-desktop:~$ 

```

And for lshw -class network
```

chris@chris-desktop:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: fe:ce:7c:d6:1f:d7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
chris@chris-desktop:~$ 


```

I also downloaded the latest drivers from the ATI website. Says i need to be superuser to install :confused:

Thanks again, and any help would be great :)

Chris

---

### Post by ugm6hr on 2009-08-09
Sorry.

That lshw commoand should be:

```
lshw -class display
```

But your card is an ATI Radeon HD 4850.

Lots of older generation radeon cards are no longer supported by ATI, so you may have problems installing the latest driver.

There are at least 2 alternative opensource drivers available: ati and radeonhd

I think a bit of googling is required to sort out which is best for you.  I have previously had problems with TV-out on an ATI card, and ended up having to use the vesa (Safe) driver - but that was fine for a CRT TV.

---

### Post by chrisxuk on 2009-08-09
I have managed to open the window to install the latest drivers. But as the resolutions wrong, i can't see the continue button to click through to the next step. I have also tried tabbing to it and pressing enter to select the button, but that didn't work either :(

---

### Post by ugm6hr on 2009-08-09
You can move windows around by holding the left-alt key and clicking anywhere in the window to drag.

This says no TV-out for your card on radeonhd: [http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

I would actually suggest you try the default "Hardware Drivers" options first, then try the ati/radeon open source driver, then use envy-ng (which automates ATI driver installation), rather than doing it manually.

---

### Post by chrisxuk on 2009-08-09
Hi there,

Thanks, i'll try moving the window.

And then if that doesn't work, i'll try envy-ng

Cheers
Chris

---

### Post by chrisxuk on 2009-08-09
Hi there,

Now when i restart my PC it says GRUB loading, please wait...
Error 17

and wont get any further :(

Any idea whats wrong?

Chris

---

### Post by ugm6hr on 2009-08-09
> **chrisxuk said:**
> Now when i restart my PC it says GRUB loading, please wait...
Error 17

Have you edited partitions since installing?  
[http://members.iinet.net.au/~herman546/p15.html#17](http://members.iinet.net.au/~herman546/p15.html#17)

---

