---
title: "Resolution will not go higher than 1024x768"
date: 2007-01-09
forum: Hardware &amp; Laptops
---

### Post by qphone on 2007-01-09
I finally got a chance to install ubuntu 6.10 onto my laptop. Installed perfectly without a hitch on a clean, formatted, single hard drive. Can't remember the onboard video but when running XP, my resolution (15 inch 4:3) was defaulted to 1280 x 1024. Now that ubuntu is installed...I only have 3 options:

640x480
800x600
1024x768

The highest that ubuntu is giving me is at 1024x768 and by comparing to windows...the 1024 ubuntu version is running at 16 bit colors NOT 24 or 32 bit colors. The refresh rate is at 61mhz. Windows default is 60 so...it's close enough.

Does anyone know how I can increase the resolution rates? The onboard video card can definitely handle it, but ubuntu so far...only gives me 3 options.

---

### Post by Quillz on 2007-01-09
What graphics card do you have? If it's Intel, run 915resolution. If it's ATI or nVidia, just get the drivers.

---

### Post by qphone on 2007-01-09
> **Quillz said:**
> What graphics card do you have? If it's Intel, run 915resolution. If it's ATI or nVidia, just get the drivers.


I went under system/administration/device manager and from looking there, it's a S3 Inc. Pro SavageDDR K4M266 Device:86C380

---

### Post by Simanek on 2007-01-09
I don't know about the support for that video card, but I had a similar problem with my PowerMac G5. After installation on the G5 my display resolution topped out at 1024. After some looking around, someone suggested reconfiguring X11. I make no guarantees, but after walking through the questions that follow this command, I was able to set my resolution to 1280 as was possible under OSX. Here's the X11 reconfigure command:

sudo dpkg-reconfigure xserver-xorg

Be careful. Don't worry if things are over your head. There is always a way of saying 'use default' to any question. This will actually reconfigure your keyboard and mouse if you alter the values on those questions. What you need to be out on the look for is a screen that lets you 'check' which display resolutions you would like available to X.

Proceed at your own risk and good luck.

---

### Post by Ron on 2007-01-09
My Toshiba laptop has a 1280 x 800 widescreen mode. I installed the nVidia driver as per instructions I found somewhere here on the ubuntu site (turned out to be dead easy and instantaneous). Then I put some dot-clock lines into the /etc/X11/xorg.conf file (after backing up the original!) and then I restarted X. It started in my old resolution and asked me to confirm that the new settings were visible when I tried to change resolution, so ubuntu seems to have a good safe setup mechanism here, and there seems to be no reason to worry about fried monitors or such. As it happened, it worked first time. I got the dot-clock lines from an article I found on google. Sorry I can't post them here right now, but my laptop is at home and I am at work. Ten minutes fun googling should turn up some xorg.conf settings suitable for your best screen resolution.

---

### Post by venik212 on 2007-01-10
After some search, I found the nice ENVY script that installed the Nvidia drivers on my computer, and I was able to get the 1280X1024 resolution that the card and monitor are capable of.  However, once I reboot, the resolution goes back to 1024X768, even though I have SAVED the X configuration file.  Something is not being read or initialized correctly.  Can anyone help?
Thanks,

---

