---
title: "Monitor troubles after install"
date: 2006-02-15
forum: Installation &amp; Upgrades
---

### Post by Coelocanth on 2006-02-15
So, the install seemed to go perfectly. Partitioned the drive, got everything installed for the dual-boot. Grub worked perfectly. However, once the install finished and it took me to the sign-on screen, I got nothing on the monitor but a mass of color. No way at all to tell what the screen was showing. I signed in (since I knew what the sign-on screen was *suppposed* to look like) by typing my username, then Enter, then my password, then Enter again.

When it went to desktop, same problem. I cannot see anything coherent at all. The upper 2/3 of the screen is a mass of color (mostly yellow, with some pink and blue) and the lower 1/3 is mostly blue with some pink and yellow.

Monitor is a Samsung 940B LCD, and the graphics card is eVGA GeForce 6800 GS PCIe.

Any thoughts? There's no way I can fix this by using any type of commands - either through the terminal or through a GUI, since I cannot see anything even remotely coherent at all (I guess the best way to describe the screen is it looks like I'm looking into a kaleidoscope). Do I need to try a new install?

Oh, and I rebooted into Windows (which is how I'm able to ask for help) and I got a request to check the drive from Windows before it went to desktop. As well, I got a "Windows has detected new hardware" message, with a request to reboot to complete the install of the hardware.  Of course, I didn't install any hardware at all - is this just because I repartitioned the drive? Or is this something far more ominous?

Help/info would be greatly appreciated, as I'm even reluctant to shut Windows down now...

---

### Post by Herman on 2006-02-15
> As well, I got a "Windows has detected new hardware" message, with a request to reboot to complete the install of the hardware. Of course, I didn't install any hardware at all - is this just because I repartitioned the drive? Or is this something far more ominous? I'm pretty sure your 'new hardware' will be your new fat32 partition that you just made. Does an icon show up for it in 'My Computer' yet? I think that's what your 'new hardware' will be, regardless of whether the icon shows yet or not.

That's disappionting about your log-in screen. Every so often my 'book pc' (test computer, pictured in my avatar) doesn't boot up quite 100% right and gets a log-in screen that is light-grey with dark-grey lines. When that happens I just re-boot it and it normally boots up okay the next time. But that's just what 'book pcs are like, they have a personality of their own, I need some patience with it sometimes. You could try simply re-booting and see what happens.

Here's a link to a hardware listing thread where someone else ([see post #10 in this thread]("http://ubuntuforums.org/showpost.php?p=526278&postcount=10")) djeffrey has the same graphics card and similar monitor to yours and says they used a nvidia card driver from synaptic to get it working better. I presume then that djeffrey's worked at least average, to begin with. That's the only post I could find on djeffreys or that exact video card.

We can re-boot into recovery mode and access a terminal there if we have to, from your GRUB menu on reboot. Others before you have had other kinds of display problems after the first install and solved them recovery mode. 
```
dpkg-reconfigure xserver-xorg
```Will get you a whole series of panels offering you manually settings you can use to confure just about any of it by hand if you know what you are doing.
Even if you can obtian as much info on your hardware specs beforehand, (from Windows maybe since you already have that, or a Knoppix CD is excellent for finding out all about all your hardware), you may see what's wrong in there and be able to set it right if you are reasonably tech minded. Maybe try something simple the first time like setting a lower resolution, djeffry said 1280x1024 was okay for his until he updated the driver for it. That might help and shouldn't do any harm. Make a note of any of the settings you change, of course, in case you will want to reverse the changes again later. I hope this helps you. (Herman)

---

### Post by Coelocanth on 2006-02-15
Herman: thanks for the reply.

Re the hardware: you were correct, it was detecting the FAT32 partition.

Re the monitor problem: I'll give it a go, but I don' think I'll nee to go for higher resolution, as my monitor's native res is 1280x1048. From what I gather in the link you posted, the other poster's system was working under this res, and he was trying to get support for a higher resolution for his (bigger) monitor.

I'll see what happens when I try your xserver-xorg solution and let you know. Thanks again.

---

### Post by Herman on 2006-02-15
Okay, good luck with it.
 If you have too much trouble getting it to work after checking the settings are okay, it could be that an error has occured at some stage during the downloading of the .iso from the internet, or when the .iso was burned to your install CD if that's how you got the CD.
I am curious as to whether your CD will pass am md5sum test. 
It could be you have a broken package for your Xserver somewhere.
Regardless of the reason, it might solve you problem, (if they persist), to re-download and install the X-server from the internet. I have seen similar problems solved this way. I would look up the command to do that in recovery mode, but I have to go right now, for work in rather a hurry, (sorry), someone around here will be able to help you if not I'll check as soon as I get home and see how you are doing. Good Luck, regards,:-D (Herman).

---

### Post by Coelocanth on 2006-02-15
[QUOTE=Herman]Okay, good luck with it.
 If you have too much trouble getting it to work after checking the settings are okay, it could be that an error has occured at some stage during the downloading of the .iso from the internet, or when the .iso was burned to your install CD if that's how you got the CD.
I am curious as to whether your CD will pass am md5sum test. 
It could be you have a broken package for your Xserver somewhere.
Regardless of the reason, it might solve you problem, (if they persist), to re-download and install the X-server from the internet. I have seen similar problems solved this way. I would look up the command to do that in recovery mode, but I have to go right now, for work in rather a hurry, (sorry), someone around here will be able to help you if not I'll check as soon as I get home and see how you are doing. Good Luck, regards,:-D (Herman).[/QUOTE]

Herman, thanks for the input. I got the display to work finally. Had to use the vesa option to get it up. Now I'm locked into a max resolution of 1024x768 and am trying to figure out how to get the proper nVidia drivers so I can use the native res of 1280x1024.

I've poked and prodded at a number of things and may have fubared some things up, as when I rebooted just a while ago, GRUB's showing 2 kernels for Linux to boot (not sure why or even what that means) as well as 2 options for recovery (one for each kernel), and there's of course Windows XP as an option as well.

As to the ISO, yes I DLed the i386.iso file and checked the file with md5sumtest. It passed, so I burnt it at 4x speed to CD.

I have to admit I'm really at sea here, as I don't know any of the commands, what they do, or what they mean and am becoming more than a little frustrated. Oh well, perhaps things will work out later.

BTW, I'll post a snippet of some odd stuff I get when I open Synaptic and see what you can make of it.

Once again, thanks for your help. It's much appreciated.

---

### Post by kevinlw on 2006-02-15
Greetings all,

I'm newbie in Linux and so far, my eyes blur up when I read the command line suggestions. :confused:

Back to the issue at hand, I have monitor issues after auto-install of Ubuntu, Kubuntu and Edubuntu.  based on my Windows experience, it seems to be monitor resolution setting related.  How do I go about manually setting this during the install process?(since the auto-install failed to do it correctly, I assume I'll have to manually intervene)  Do I have to specify specific monitor and video card makes and models and specs?

I had to do this when I tried out a Mandriva install some time last year.

thanks & best regards,
Kevinlw
to all of chinese ancestery Happy New Year!

---

### Post by Coelocanth on 2006-02-16
Herman: I got everything pretty much sorted out. Thanks to you and Estarian (apologies if I spelled it wrong, Est!) and aysiu. Now I'm having a bit of fun trying to learn all I can. Seems a pretty enjoyable OS. Cheers!

Kevin: try posting a bit more detailed info on your problem. I'm sure the great folks here can get you up and running.

---

