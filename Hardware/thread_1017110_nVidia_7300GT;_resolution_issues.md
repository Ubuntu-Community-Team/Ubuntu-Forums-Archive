---
title: "nVidia 7300GT; resolution issues"
date: 2008-12-20
forum: Hardware
---

### Post by Hatch3r on 2008-12-20
It seems to be that every time I install ubuntu I have no end of trouble getting the resolution I'm used to (1280x1024).
Each time I eventually achieve it, I either can't remember or can't do what I did previously to get it working the next time (usually at the next upgrade!)
I'm currently running on a PCI-E nVidia 7300GT. On 8.10 i386 with all the latest updates installed.
This (eventually) worked fine in 8.04 and is in the supported GPU list.
I've tried using the nVidia 96 and 177 driver from the restricted list to no avail. I've also tried disabling these restricted drivers and then using the EnvyNG program to install them. Again same problem. I've downloaded the nVidia drivers and still same problem.

With the 177 drivers I can get a max resolution of 1024*768. My aim is to achieve 1280*1024.
In 8.04 I achieved this with the displayconfig-gtk, unfortunately it would appear that this is no longer available in Intrepid.

Any help would be greatly appreciated. I've looked at everyother thread I can find so far and searched the internet far and wide.

Thanks
Hatch3r

(I created a seperate thread so [this one ](http://ubuntuforums.org/showthread.php?t=1016819) didn't get too crowded)

---

### Post by Hatch3r on 2008-12-21
There has been some progress. I've now got some additional resolutions but they do not appear to work correctly.
By using "sudo nvidia-settings" from a terminal I was able to change the resolution to either:
Auto
1360*768
1152*864
1024*768
right down to 320*240

Using the 1360*768 option doesn't work since it appears to be a widescreen resolution. And 1152*864 looks to be identical to 1024*768.

---

### Post by Hatch3r on 2008-12-21
Another step forwards?
On the suggestion of another resolution problem thread here, I found a liveCD that worked with my graphics card to give a decent resolution. Well 8.10 and 8.04 didn't but fortunately 7.10 did! So booted and copied the xorg.conf over to my new machine.
Opened up each and copied the screen, device and something else* into the new xorg.conf.
Reboot X and was greeted with "OUT OF RANGE" on my monitor, I've seen this before though and it's because my monitor only works at some stupid frequencies, specifically 30 - 80kHz Horizontally and 55 - 75Hz Vertically.
So rebooted, selecting recovery mode, root shell and edited the xorg.conf with nano. Replaced the frequencies with what they ought to be and rebooted. Same problem, still says out of range.
Back to the recovery console. This time selecting the xfix option, this worked and at least now my monitor comes up with something! I've apparently gone back to the default 8.10 drivers.
Reboot a few times and get EnvyNG to load the nVidia 177 drivers and we're back where we started with a 1024*768 resolution.
This time I've more carefully edited the xorg.conf with the correct driver settings and frequencies. Upon reboot, it says my max resolution is 1024*768 but this time I have the space for options above that! The plot thickens.
**FINALLY** before diving back into the xorg.conf to try and force it to a certain resolution. I opened the nvidia-settings! I have every resolution under the sun there. Started it again with "sudo nvidia-settings" and got an error messages when saving it to xorg.conf. Hmm, reboot and see I think.
My login screen comes up with the correct resolution everytime. But when I login, my screen is offcentre which usually indicates (well to me anyway) that the restricted drivers aren't in use.
Reboot a few times and the issue still remains, so I used the auto adjust tool on the mointor and lo and behold it fixes it. But is this at the cost of making my login screen offcentre? First reboot, login screen seems to be right and desktop...is right as well. I think I'll call it a day here. Do my first backup with Clonezilla and start installing software. I'll simplify this post, and what I did to get it working later on when I have some spare time!

---

