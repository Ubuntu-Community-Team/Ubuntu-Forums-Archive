---
title: "Installing fglrx AMD drivers on R9 280x Ubuntu 14.04"
date: 2014-09-18
forum: Hardware
---

### Post by john293 on 2014-09-18
Hi, I've been trying for several days straight to install fglrx drivers on ubuntu 14.04 for an R9 280x card.

Here's what I'm installing on:
CPU: AMD A10 7850 APU
GPU: XFX Radeon R9 280x
Motherboard: MSI A88X-G45

Everytime I reboot, I get a black screen that says USB 10-1 device not accepting address 2 error -108 after installing fglrx

That error is then followed by a black screen where I can only get a login shell by pressing ALt-F1

fglrxinfo gives me something about not being able to detect display or something

To fix this I uninstall all fglrx packages and go back to using the open source driver which causes horrible flickering on 2d rendering and anything using hardware acceleration

I've tried installing through these methods
-from the official amd site
-from the additional drivers software on ubuntu
-from synaptic package manager

Each method gives me the same crap.

The most disheartening thing about all of this is that the only reason I switched to linux is because getting windows 7 to stop flickering/tearing with 2d rendering requires a hacky fix I found on some youtube video.

I don't know what to do at this point. :mad:

---

### Post by john293 on 2014-09-18
Ok, so I followed this thread:
[http://ubuntuforums.org/showthread.php?t=2244651](http://ubuntuforums.org/showthread.php?t=2244651)

And I am still at the black screen when rebooting

When I run the command: startx

I see these errors:
(ww) fgrlrx: No matching device section for instance (BusID PCI:0@1:0:0) found
(ww) fgrlrx: No matching device section for instance (BusID PCI:0@0:1:1) found
(ww) fgrlrx: No matching device section for instance (BusID PCI:0@1:0:1) found

Also, when i get to the part of that guide where it says rename file xorg.conf.mmddyy to xorg.conf, everytime I reboot the xorg.conf file is unchanged as if i never overwrote it at all.

---

### Post by maxinstuff2 on 2014-09-18
Have you set the "nomodeset" parameter correctly in grub?
And don't forget to update grub afterwards.
(step 3 of the guide)

Also if you find it too hard trying to do the whole process in command line, remove the GPU from the computer and use onboard graphics while you sort it out.

EDIT: This could be to do with IOMMU, if you turn it off in bios it may fix it (AMD-IOMMU is said to cause problems)
From here:
[https://answers.launchpad.net/ubuntu/+question/216494](https://answers.launchpad.net/ubuntu/+question/216494)
Which links to here:
[http://www.nvnews.net/vbulletin/showthread.php?p=2532365](http://www.nvnews.net/vbulletin/showthread.php?p=2532365)

They mention it happens for AMD too. 
Hope that will solve for you.

---

### Post by waffleguy4 on 2014-09-25
I'm having these same issues, except I still can access my desktop. Please post if you find a fix, thanks!

---

### Post by tutenstain2 on 2014-09-25
[SIZE=1]Same problem[/SIZE] as [john293]("http://ubuntuforums.org/member.php?u=1946093"). Any news?[SIZE=1][/SIZE]

---

### Post by wy-2-k on 2014-11-03
The best way to solve this issues is the Install Proprietary AMD drivers from the Settings-Additional drivers.

Reboot and the 3D is activated

---

### Post by ron-neversleep on 2015-02-25
> **wy-2-k said:**
> The best way to solve this issues is the Install Proprietary AMD drivers from the Settings-Additional drivers. 

Using Proprietary AMD / fglrx drivers from Settings-Additional drivers actually CAUSES the black screen/lock problem on a fresh 14.10 Utopic.

It seems the open source drivers are loading and conflicting with the proprietary drivers. The fix was somewhat easy.

Create a file /etc/modprobe.d/blacklist-radeon.conf  with CONTENT:
```
blacklist ati_drv
blacklist radeon_drv
```
And reboot.  

Just remember to remove this file, if you ever decide to uninstall the proprietary fglrx driver.

-Ron

---

### Post by QIII on 2015-02-25
Unless your experience is quite different from [mine]("http://theleftcoastgeek.net/"), I suspect other factors are in play.

---

