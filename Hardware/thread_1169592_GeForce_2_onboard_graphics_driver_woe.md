---
title: "GeForce 2 onboard graphics driver woe"
date: 2009-05-25
forum: Hardware
---

### Post by frisbeelinux on 2009-05-25
My first post - you might guess I'm a newbie, so forgive if I'm asking obvious questions. I've had a look elsewhere on the forum, but can't see an answer to the problem I'm having.
 
Having run the live cd version of Ubuntu before and enjoyed it, I thought I'd give it a go and install it on my hard drive. My motherboard uses GeForce2 onboard graphics. After I'd installed Ubuntu, I went to adjust the screen resolution in Display, looking for the 1280x1024 that I normally run under Xp (so I know both my graphics chip and monitor support it - the version of the Nvidia driver that I use in Xp is 6.13.10.2980), but that resolution wasn't listed. The best resolution I could find in the list of those available was 800x600 - this is that same as the live cd offers me. So, thinking that I needed to install an Nvidia driver to access higher resolutions, I went to Hardware Drivers and duly downloaded the version of the Nvidia driver that was suggested - 96 was the only one listed - which it said had been tested by the Ubuntu developers. However, when I restarted Ubuntu, the display was corrupted. To access any menu items meant dragging the mouse pointer over them, and even then, the display was mainly illegible. I tried selecting 1280x1024 and various other resolutions, but all gave some kind of corruption on screen.
 
My question is, as I don't want to go out and buy a new graphics card as a first choice remedy (I wouldn't know which to buy anyway: wouldn't want the same thing to happen again!), is there a solution to this resolution problem specifically for users with onboard Geforce2 graphics? Is it as simple as using the same driver that I use in Xp - or will that not work in Ubuntu - and if so, how do I tell Ubuntu to use it when it doesn't list such an old driver as a possible choice? I'm a beginner, so if there is a remedy, please keep your instructions simple! :)

---

### Post by overdrank on 2009-05-25
Hi and welcome, which version of Ubuntu are you using? it sounds like you are using Jaunty 9.04. You may try and boot into recovery mode and use the xfix option to correct the graphical issues.
Recovery mode is usually the second choice from the grub when booting. Then you should be give 4 option and the last is xfix, when xfix is complete then you should be given the option to boot normally.
Also how much memory is shared with the onboard graphics? This may cause some issues also.

---

### Post by frisbeelinux on 2009-05-25
Hello Overdrank, and thanks for the welcome and the swift reply. I wasn't expecting anyone to answer that quickly!
 
I an indeed using 9.04. I have tried booting into recovery mode and using xfix yesterday - that's about as adventurous as I dared be - but the graphics corruption persists. The GeForce2's onboard memory is 32mb. I have 992mb of ram available.

---

### Post by overdrank on 2009-05-25
> **frisbeelinux said:**
> Hello Overdrank, and thanks for the welcome and the swift reply. I wasn't expecting anyone to answer that quickly!
 
I an indeed using 9.04. I have tried booting into recovery mode and using xfix yesterday - that's about as adventurous as I dared be - but the graphics corruption persists. The GeForce2's onboard memory is 32mb. I have 992mb of ram available.

Ok I do not believe you will be able to increase the amount shared with the nvidia graphics. So If you can reach the command line by using the ctrl, alt, F1 keys you may try these commands
```
sudo /etc/init.d/gdm stop
``` 
Then use ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
This will reconfigure the xorg to hopefully correct the graphics then use
```
sudo /etc/init.d/gdm start
```
And hopefully this will bring you back to the desktop. You may be better off using the nv driver instead.
You may also want to try Hardy 8.04 if you would like the desktop effects. :)

---

### Post by frisbeelinux on 2009-05-25
Thanks for this. I will give these suggestions a try. Someone else has mentioned that the 8.04 version may be less troublesome in this respect, so if the other ideas draw a blank, I think I will give 8.04 a go.

---

