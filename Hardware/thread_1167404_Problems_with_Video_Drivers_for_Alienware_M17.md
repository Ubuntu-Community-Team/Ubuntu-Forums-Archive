---
title: "Problems with Video Drivers for Alienware M17"
date: 2009-05-22
forum: Hardware
---

### Post by sxe4ever on 2009-05-22
I purchased an Alienware M17 laptop and almost have it all set up exactly how I want it, and am just having problems with video drivers.  I have 2 video cards and they are  512MB ATI Mobility Radeon HD 3870 with CrossFireX.  I attempted to install the latest drivers using the restricted default ones through Ubuntu and it caused my GUI to stop loading.  I got that problem fixed, and then downloaded the drivers from AMD's site directly.  I downloaded the ones for the ATI Radeon HD 3xxx series as I couldn't find my series under the mobility listings.

I'm currently running version 9.04, Jaunty with the latest updates that I'm aware of.

Could someone please assist me in getting the appropriate drivers for my computer??? If anymore information is needed I'll gladly do my best to provide.  Also, could you provide the directions on how to uninstall if it goes bad as I've had my GUI crash at least 5 times now when trying to get the video drivers to work????

Please & thanks, any feedback is greatly appreciated!!!!

---

### Post by sxe4ever on 2009-05-22
Bumping, sorry just really want to try and get this resolved as soon as possible

---

### Post by sxe4ever on 2009-05-23
Can someone please take a swing at this? THank you!

---

### Post by sxe4ever on 2009-05-29
Please??? Anyone??? I can't seem to get this to work

---

### Post by swolgoose on 2009-05-30
Bump...I am currently using Ubuntu Server Edition and Ubuntu Hardy Heron. I just purchased a M17 Alienware Laptop with Dual ATI HD 3870 using Crossfire. I would like to install the 9.X Ubuntu on this laptop as well.

Any help would be appreciated.

Thanks,
Swollgoose

---

### Post by sxe4ever on 2009-06-06
Please??? Someone help???

---

### Post by rianaj on 2009-06-08
have you tried this thread... [http://ubuntuforums.org/archive/index.php/t-1053142.html](http://ubuntuforums.org/archive/index.php/t-1053142.html)

---

### Post by sxe4ever on 2009-06-09
Thanks for the reply!!! Although it was mostly about getting Internet connection through the terminal and how to install drivers, there were a couple of things that I was able to use.  I tried to install the specific driver that they had listed on the first page, and it said that it wasn't supported with my version, here's the exact message it gave > Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.28-11-generic
I also tried installing the drivers using envyng, which was really nice as it gave me an easy uninstall method, but it said that it was downloaded successfully, but when I rebooted it just gave me the terminal.  Any ideas????

---

### Post by Pooncakes on 2009-07-20
Guys,

I have the same computer and the same problems.  Q9100, 3870x2. If you've browsed the forums @ AW I'm having the stuttering problem they described.  Tech support had me disable the RAID 0 array, so now I have 2 128 gb SSDs.  Naturally I have Vista on one for games and Linux on the other.  A few things:

Ubuntu 9.04 goes from the boot loader to login window in 13 seconds!!!!

This is faster than Debian 5 and Red Hat.  I'm not sure how this is possible, but it happened.  Not only that but EVERYTHING WORKS out of the box. Wireless, media buttons, all pci devices, etc, and VESA graphics (yuck)

I went to time the vista loadup but it did an update - taking it over 4 minutes.  

The core problem here is getting the ATI driver flgrx to output to the monitor.  Flgrx supports Xfire, but if you read the release notes, only on 48** series cards.  Thanks ATI.  That means you'll have to install the driver, run aticonfig, and then flag the kernel to ignore one of the cards.  The key here is to bind the 3870 at PCI address 6, and unbind the one at PCI address 3.  This is counterintuitive because 3 is the primary; 6 being the slave with audio out.

I did this, and it has almost worked. :confused:

Instead of booting to a prompt, the freaking thing gives the GUI progress bar, then makes off-color hash in which the letters and logo of Ubuntu are barely readable.  I login and it makes the GNOME pleasure sound, then the screen goes to 1920x1200 pixels of pure black.

Bh by the way there's a wiki entry for some 1337 dude to did a Gentoo build.  Behold his xorg.conf:  [http://en.gentoo-wiki.com/wiki/Alienware_M17](http://en.gentoo-wiki.com/wiki/Alienware_M17)

His xorg.conf is wildly different than mine; I'd love to talk with him about it.  I can go back to VESA graphics at will but I have to have my native res with video acceleration.

When I do an aticonfig it shows 3870 PCI 3 as the primary, and 3870 PCI6 as the secondary.  I flagged PCI6 as my primary and made xorg.conf reflect that.  Aticonfig shows Xfire bridge one as PCI 6 master, PCI3 second. It shows no Xfire bridge 0,

I can get to a half-working Gnome Login, that then takes me to pure black, so I'm on the right track.

Once trail and error and a few tips help me succeed I'll post updates.

---

### Post by sxe4ever on 2009-07-20
Thanks for replying Pooncakes, if you get any further be sure to let us know.  I had to disable the RAID as well when I installed Ubuntu onto here.  I pretty much have just given up though.  If I could get the video cards to work though, I might be able to get my games to work through Wine.... but in the meantime, I guess I'm stuck using Windows for my games :(

---

### Post by sxe4ever on 2009-08-14
Bump.  Can anyone assist with this????

---

### Post by dkhajavi on 2009-10-25
Just to add another name to the group...

M17 w/NVIDIA 9400M G SLI
No discrete graphics, after install must go into recovery of GUI and default to embedded GUI

No 3D, no dual view etc....

I am a devoted Ubuntu user but am feeling a little silly with my Ferrari laptop relegated to being a YUGO. 

Just to add insult to injury....no sound, 50% hot keys (no brightness control is very annoying)...etc...  Not my previous Ubuntu bliss by any stretch...

Can anybody help?

---

### Post by dkhajavi on 2009-12-04
Just thought I would update this still unresolved issue.  I tried the latest NVIDIA driver 190 and still no go.  Same issue, after boot logo, black screen.

This seems like a pretty big issue that is not being addressed over such a long time.

Can anybody help?

---

### Post by sxe4ever on 2009-12-05
> **dkhajavi said:**
> Just thought I would update this still unresolved issue.  I tried the latest NVIDIA driver 190 and still no go.  Same issue, after boot logo, black screen.

This seems like a pretty big issue that is not being addressed over such a long time.

Can anybody help?

This issue seems to be being handled in this other thread that I'm trying to get the same answer as well:

[http://ubuntuforums.org/showthread.php?t=1305459&page=27](http://ubuntuforums.org/showthread.php?t=1305459&page=27)

---

### Post by dkhajavi on 2009-12-15
OK a little more info:

I tried loading a fully configured xorg.conf from my home desktop running dual NVIDIA 7800 GTs in SLI and it did not work.  However it caused Grub to stop the boot and give me an error box where I was able to try to repair, fix manually etc...  what was interesting is that I got a detailed error report and what popped out for me was the failure to load GLX.  Can this be the root of the problem?

Sorry I am still a green Ubuntu guy but trying to help.  

I also read that 8.04LTS will work on an M17 with NVIDIA drivers so it looks like I will be trying that next as 8.10, 9.04, and now 9.10...three distros still will not let me use my laptop to it's full potential.  Unfortunate to say the least.

---

### Post by sxe4ever on 2009-12-16
> **dkhajavi said:**
> OK a little more info:

what was interesting is that I got a detailed error report and what popped out for me was the failure to load GLX.  Can this be the root of the problem?

Sorry I am still a green Ubuntu guy but trying to help. 

I understand your frustrations completely.  Right now I'm on the newest build and I don't even have sound currently.  I don't think that GLX is the issue however as I'm running ATI video cards and still having the issue.  I think I remember uninstalling any support of GLX just in case this was causing an issue however, but it didn't help out at all

---

