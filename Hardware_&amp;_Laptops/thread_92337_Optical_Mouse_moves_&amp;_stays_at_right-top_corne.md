---
title: "Optical Mouse moves &amp; stays at right-top corner!"
date: 2005-11-19
forum: Hardware &amp; Laptops
---

### Post by asithab on 2005-11-19
Hi,

I installed ubuntu as a dual-boot system yesterday: I have Windows XP as well. The problem is that when Ubuntu starts the mouse is at the default position (middle) and would not move at all. When I right-click it would move to the top-right corner of the screen and stay there! It would give me response to the clicks (right or left) I make! .. But, I cannot move it!

I tried doing different things that were suggested on this forum & elsewhere! I ran "mdetect" and it gave me that I have "intellimouse at /dev/psaux". What I have is a cheap optical mouse! With just two buttons & a scroll wheel! So, I interpreted all the advices given in the forum to suit this! Changed Xorg.conf many a times, with different settings. NOTHING worked! 

Now, the strangest thing is this. When I reboot to Windows XP after trying Ubuntu (even before configuring the mouse settings!), the mouse is just stuck in the middle! Nothing would rectify the problem, except for shutting down, disconnecting the power, wait 10 sec or so & reboot again, where it works like a charm!

Any advice should be grately appreciated.

asitha.

---

### Post by jliedeka on 2005-11-19
Are you using a KVM switch?  I have had occasional issues when changing between boxes.

Even if you don't, try resetting your mouse with this:

/bin/echo -n reconnect > /sys/bus/serio/devices/serioX/drvctl

Where "serioX" is your mouse device (often serio1, try grepping dmesg or /var/log/messages to be sure)

---

### Post by asithab on 2005-11-19
No I don't use a KVM switch! The mouse is just connected to the PS/2 port. As I  have mentioned, when I run "mdetect" it is identified as "Intellimouse at /dev/psaux". 

And also, I used FreeBSD previously, and even with that I didn't have a problem with the mouse!

---

### Post by vinnyjones on 2005-11-19
I got the same damn problem... I think its to do with the new 2.6 kernel, its not ubuntu specific.. The mouse (cheap optical 2 button scroll mouse) works fine with kernel 2.4 but refuses to work with 2.6...

I've been looking around and haven't found any solutions, anyone have any ideas...

---

### Post by winkerbean on 2006-02-16
[QUOTE=vinnyjones]I got the same damn problem... I think its to do with the new 2.6 kernel, its not ubuntu specific.. The mouse (cheap optical 2 button scroll mouse) works fine with kernel 2.4 but refuses to work with 2.6...

I've been looking around and haven't found any solutions, anyone have any ideas...[/QUOTE]

Any success here?  Is installing the 2.4 kernel an option?  (I'm relatively new to Linux and still feeling my way around.)

---

### Post by drifter0000 on 2006-02-22
I have the exact same problem. 
using breezy on  pavilion 6330 with K6 300 150mb mem  
new optical mouse.

My only problem is I dont know anything about linux.
Here is what I have found in my problem.
When my machine is booting the light in my mouse is active..so it seems to be working...during the module loading process the light comes on until it loads module that says setting up system clock then the light quits working.

In my bios I tried disabling ps2 mouse then reinstalling breezy.  When I do this and get to the desktop my mouse light is still working....but it dosnt do anything.  When I pick enable or os select in bios.... my light goes off during module loading and only buttons work at desktop.

Also I have noticed that when I reboot back into windows 98se it tells me there is no mouse connected and I have to boot windows a second time to get the mouse to work.

Like I said I dont know anything about linux but it seems to me that breezy is shutting down the mouse in the bios....maybe irQ 12 problems..and it persists during a reboot and going to windows os.

If you guys find a fix please send me a message because I dont have a cd burner....only a cd for breezy and I hate windows!!!!!

---

### Post by ahd100 on 2006-02-22
I have the same problem with my PS2 optical mouse. I've had to revert to a cheapo-nasty-freebie ball mouse until I find a solution.

I'm on a Duron 1.3Ghz machine w/ 256MB RAM. My optical mouse is a cheap Ebuyer extra value job.

It sounds the same as Drifter0000, the light goes out when I get into Gnome/KDE or, even if it doesn't, it will as soon as I try and move the mouse. I have the same issue with Win98SE too, after attempting to use linux I get a 'no mouse detected' type message from Windows upon reboot requiring another reboot and a quick disconnect and reconnect on the PS2 plug to fix it.

I hope someone out there knows what's going on because I don't want to live with this horrible mouse forever.

Andrew

---

### Post by winkerbean on 2006-02-22
The solution I found is this (paraphrased from Linus Torvald, himself): PS/2 support in Linux Kernel 2.6 is facacta.  I, yesterday, bought a ps/2-to-usb adapter, plugged my mouse in there and now everything is juuuuuuuuuuuuuuuuuuuuuuuuuuust peachy.\\:D/

---

### Post by Efwis on 2006-02-28
[QUOTE=winkerbean]The solution I found is this (paraphrased from Linus Torvald, himself): PS/2 support in Linux Kernel 2.6 is facacta.  I, yesterday, bought a ps/2-to-usb adapter, plugged my mouse in there and now everything is juuuuuuuuuuuuuuuuuuuuuuuuuuust peachy.\\:D/[/QUOTE]
Thats all fine and dandy for those that have the extra usb port to spare, but what about those of us who don't???

I too have the same issue. only my light turns off at "loading Modules" in the boot process. I know it worked with no issues in Hoary. I hope they figure it out soon, this is rediculous. I have searched this board all over the place, and find topic after topic about the p/s2 optical mice not working with Breezy from the get go. I have a friend who is using Kubuntu, and his optical is working like a charm, it's ps2 also. so why can't they get this fixed in the Gnome version???

Sounds like something that is maybe Gnome related.

---

### Post by winkerbean on 2006-03-01
[QUOTE=Efwis]Sounds like something that is maybe Gnome related.[/QUOTE]

Can't honestly say I know anything about that.  As far as having an extra usb port, are you able to use a 'usb-splitter'?  I have an adapter that turns a single usb port into 4, each visible as a separate usb port.  I bought an El Cheapo one for less than US$10.

---

### Post by Efwis on 2006-03-01
Those splitters are nice. but I can't validate spending 10 - 20 bucks on one just to get my mouse working on a system that should already support it. I didn't have this issue with hoary, so it shouldn't be one with Breezy.

---

### Post by morbidi on 2006-04-02
got the same problem, got an ps2 optical mouse, and noticed that the protocol detected on the boot was for ImExPS/2 Generic Explorer Mouse, I think you can pass some kernel information from grub and have it to load psmouse module with the apropriate parameters.

---

### Post by Efwis on 2006-04-02
I ended up compiling a Vanilla kernel 2.6.16, after I compiled it the Mouse worked without any issues. It has something to do with /dev/psaux module that 2.6.15 loads, I tried Debian Sarge with the same results under 2.6.15.

Sounds like compiling your own kernel is going to be the best way to resolve this issue. I'm not complaining, I got rid of the Bluetooth modules when I built it. Wasn't using them anyway, so why have the modules on the system.

---

