---
title: "New Monitor with Ubuntu 14.04"
date: 2016-04-06
forum: Hardware
---

### Post by AlyssaVS on 2016-04-06
I just bought a new monitor for my desktop and all of the icons are huge and I can't navigate to the settings to change it (screen is stuck). 

Any help would be appreciated. It's an HP 25vx with an HDMI connection.

---

### Post by grahammechanical on 2016-04-06
> I can't navigate to the settings to change it (screen is stuck). 

That is unusual. Try loading in recovery mode. Grub menu>Advanced options for Ubuntu>Select a kernel with a recovery mode option>Recovery Menu>Resume. That should load to a working desktop with an open source video driver.

Then either go to system settings>Display and click Detect displays. Or, go the Software & Updates>Additional Drivers tab and change video drivers. I would do both. I would run with an open source video driver for a few restarts to set a good loading profile and then try again with a proprietary video driver.

Modern digital monitors contain information about screen resolution & all that stuff in an integrated circuit chip. The information is called Extended Display Identification Data (EDID). At every boot Linux accesses the EDID chip and sets the optimum screen resolution from that. 

Regards.

---

### Post by AlyssaVS on 2016-04-06
Thank you very much for the detailed advice! I will try these steps and update the thread.

Ok, first thing is after rebooting in recovery mode the display loaded correctly and I was able to navigate freely to "Display" to click detect displays. However, when I went to software and updates to change video drivers there are no proprietary drivers installed which is what I should have known it would say. :redface:

I forgot to mention the original problem which was the error message from trying to download the .exe drivers from the CD. It's honestly been so long since I've had a desktop, this hasn't been an issue for years. I don't remember what I need to do in terminal command mode to get the drivers installed in the first place.  

A little more advice would be much appreciated. :)

---

### Post by Bucky Ball on 2016-04-07
You don't get .exe files installed in Ubuntu so you can forget about that and them. They are for Windows. 

What you can do is open a terminal and:

> sudo lshw -C video

... and post the output here between code tags, please.

---

### Post by AlyssaVS on 2016-04-07
I realize that. I guess I wasn't clear when I said "I should have known"... I didn't have the proprietary drivers installed because the CD only had .exe files when I went to download them which of course won't work. ;)

I am re-typing this because the TP link wireless adapter that came with the desktop is terrible so I am on my laptop....

<*-display unclaimed
description: VGA compatible controller
product: xeon E3-1200 v3/4th Gen Core Processor Integrated Controller
vendor: Intel Corporation
physical ID: 2
bus info: pci@0000:00:02.0
version: 06
width: 64 bits
clock: 33MHz
capabilities: msi pm vga_controller bus_master cap_list
configuration: latency=0
resources: memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)>

Hopefully I got that right. Also, by any chance do you know the proper usb wireless adapter I should buy? I researched mine and I guess it's better to just get another one. I am using:
Intel Core i7-4790K CPU @ 4.00GHz x 8
Ubuntu 14.04.2
15.5 GiB
Disk 1.0 TB

Thank you sooooo much for your help!

---

### Post by Bucky Ball on 2016-04-07
Please start a new thread for the wireless issue. We might be able to get that one going, but let's not get into it here. ;)

And that is all of the output? There is nothing missing from the bottom? Did you scroll all the way down the terminal window?

---

### Post by AlyssaVS on 2016-04-07
Yeah, that's it. Ran it again too.

My PC keeps trying to download a bunch of updates but fails thanks to the adapter problem. The updates may be all it needs to get past the driver issue. I'm only guessing. I will attempt to get an ethernet line connected back here and see if that makes a difference.

Well that didn't work. Still fails to download and I have to boot into recovery mode to be able to access anything.

The internet works fine on the Windows side so it isn't the hardware.

---

### Post by Bucky Ball on 2016-04-08
*Thread moved to **Hardware**.*

What is the exact message you get when you try to update/upgrade in a terminal with these two commands:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Please post here between code tags.

---

### Post by AlyssaVS on 2016-04-10
> **Bucky Ball said:**
> *Thread moved to **Hardware**.*

What is the exact message you get when you try to update/upgrade in a terminal with these two commands:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Please post here between code tags.

Ok, one piece of good news is for some reason now I can get on the internet through the wired connection. But still got the same error message trying to update through system settings. 

So after running the first command you listed I got this:

```
 Get:1 http://plex.r.worldssl.net lucid InRelease99% [1 InRelease gpgv 980 B] [Connecting to archive.ubuntu.com (2001:67c:1560:8Splitting up /var/lib/apt/lists/partial/plex.r.worldssl.net_PlexMediaServer_ubuntIgn http://plex.r.worldssl.net lucid InRelease                                 
E: GPG error: http://plex.r.worldssl.net lucid InRelease: Clearsigned file isn't valid, got 'NODATA' (does the network require authentication?)
```

I ran the second one you listed and it completed several updates/upgrades but there were way too many pages for me to try and re-type. I rebooted, still have monitor issues and re-ran the second command. Now it just says this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  linux-image-3.13.0-32-generic linux-image-extra-3.13.0-32-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

It looks like updating was successful through terminal, but that did not correct the original problem as I had hoped. :(

---

### Post by AlyssaVS on 2016-04-10
Sorry, I did the code tags wrong again...

---

### Post by Irihapeti on 2016-04-10
The final code tag needs to have a / in front of it. i.e. [/code]

---

### Post by AlyssaVS on 2016-04-11
> **Irihapeti said:**
> The final code tag needs to have a / in front of it. i.e. [/code]

Ok, I'll be sure to do that next time. And thank you very much for fixing that for me!

---

### Post by AlyssaVS on 2016-04-16
Well, I guess I'll try again somewhere else.

---

### Post by oldfred on 2016-06-10
Did you try Intel boot parameter to see if it works?

Check size defaults:
 xwininfo -root 
      xrandr -q 
    
 # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size

To test add like nomodeset on grub. If one works then make permanent in /etc/default/grub 
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

