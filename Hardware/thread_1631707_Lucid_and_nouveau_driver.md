---
title: "Lucid and nouveau driver"
date: 2010-11-27
forum: Hardware
---

### Post by John Jason Jordan on 2010-11-27
OK, before you kill me, I used Ubuntu for years as a dumbass desktop user, but a year ago I decided to expand my knowledge of Linux. So I went distro shopping and ended up with Fedora, currently Fedora 14 x86_64. (Still a dumbass, though.) But now I have a problem and only an Ubuntian can help. 

My laptop (Thinkpad T61) has an nVidia Quadro NVS 140M chip. It works well with either the nouveau driver or the nVidia proprietary driver. But suddenly I need to give a presentation in a classroom that has a Hitachi CP-SX1350 projector. The projector can accept up to 1600x1200 from a computer, and regardless of what you feed it, displays 1400x1050 on the wall. My laptop screen defaults to 1680x1050, but that is 16:10 ratio, where the projector is 4:3. One of the two must be distorted, and I want it to be the latop so the audience sees a normal display. In other words, I need to set the laptop to 1400x1050 or 1600x1200. 

In Fedora, no matter which driver I use I get the option to set the laptop screen to 1680x1050, 1280x0124, and on to lower resolutions. I do not have the option to set the laptop display to 1400x1050. Using xrandr from the command line just gives me an error message if I try to set it to 1400x1050.

My presentation is about open source desktop publishing, so I need all the screen real estate I can get. I want the laptop at either 1600x1200 or 1400x1050.

Now for where Ubuntu comes in. If I boot to a Lucid live CD (which uses the nouveau driver) I do get the option to set the resolution to 1400x1050. And I have done so, and the laptop screen looks fine, although distorted because the aspect ratio is off. In other words, the laptop screen is capable of 1400x1050, and somehow or another, Ubuntu made the nouveau driver give me that option. Yet, if boot to the nouveau driver in Fedora 14 all I get are 1680x1050 and 1280x1024.

I have created an xorg.conf file where I have set modes and modelines to offer 1400x1050, but both the nouveau and nVidia drivers ignore it. The Xorg.0.log file says "mode <resolution> not supported, deleting mode."

How does Ubuntu get the nouveau driver to offer 1400x1050 with my nVidia chip?

---

### Post by John Jason Jordan on 2010-11-27
Just in case any users google on this problem and end up here, I resolved the problem, although it took an entire day of fiddling and googling.

I upgraded Fedora 13 to Fedora 14 (x86_64). Then I reinstalled the nouveau driver. Then I checked to make sure the nouveau driver was not blacklisted (I had previously run the nVidia driver, whose install utility blacklists nouveau.) I found that something had added "nouveau.modeset=0 rdblacklist.nouveau" at the end of the kernel line in Grub. I added a # before these parameters. Also something during the upgrade to Fedora 14 had created an xorg.conf file, in which it was calling the VESA driver. I changed the line to "nouveau." 

When I rebooted X came up at 1680x1050 and was using the nouveau driver. No problems. More important, when I went into System > Preferences > Monitors I found that I had the 1400x1050 resolution option. I selected it and it works perfectly, exactly as it did when I booted the Lucid live CD.

My best guess is that there was an update to the nouveau driver that was not available until after the upgrade to Fedora 14. Lucid already had the newer driver.

---

