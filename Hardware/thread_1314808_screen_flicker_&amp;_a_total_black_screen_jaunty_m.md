---
title: "screen flicker &amp; a total black screen jaunty msi wind U100"
date: 2009-11-04
forum: Hardware
---

### Post by dj-toonz on 2009-11-04
Hi all, every now & then the screen starts flickering & slowing down if that's the word for it & the screen goes totally black or a Orange colour (everything else still works like If I'm playing music that carrys on playing) and all the FN keys but no way to get the display back without holding down the power button for 4 seconds till it shuts down then leave it for a couple of minutes then power up, then it's alright then for a bit (it doesn't do it all the time, now & then but I can't tell when it's going to do it. Is there anything I can do to fix the display problems? I'm already using the latest X drivers for Intel, could that be the problem or does it look like I'm using the unstable X drivers. cheers

---

### Post by kaptainkatsu on 2009-11-10
I am having similar issues. When I login, the screen brightness will also go up and down and the screen brightness bar will show the brightness going up and down.

It will also just shut off the screen every once in a while requiring a shut down.

---

### Post by mckelly46 on 2009-11-10
Same here on my MSI Wind U100!

I've fiddled with the brightness setting, screen saver and display attributed but to no avail.

---

### Post by mckelly46 on 2009-11-10
Correction, the screen flicker happens with version 9.10 - Karmic Koala.

---

### Post by kio_http on 2009-11-10
Try booting in recovery mode and selecting xfix

also what graphic card does that laptop have?

---

### Post by ricojonah on 2009-11-11
I've had this problem for several weeks (during testing, before the official release).

The site below appears to have several potential solutions that have worked for several MSI Wind owners.

Source: [https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/415023]("https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/415023")

I'll post back in a little while with a quick report on whether any of the proposed, temporary workarounds resolve this issue.

---

### Post by ricojonah on 2009-11-11
Okay, I've just updated from Jaunty to Karmic. I haven't tried the above solutions just yet--mainly because I just noticed that this problem is actually now documented in Ubuntu 9.10's [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/910#Brightness%20flickering%20on%20MSI%20Wind%20netbooks%20with%20KMS").

Before I try the other suggestions, I'm going to give the proposed solution from the release notes a shot (disabling KMS).

See y'all soon! (If I'm not back, I probably killed my netbook! :P)

---

### Post by ricojonah on 2009-11-11
Okay, it's official. I just tried the workaround suggested from the release notes (see above), and the flickering is (finally) gone on my U100!

As a side effect, the bootsplash doesn't to seem to be quite as graceful transitioning to the login, but that's a puny cosmetic issue that I can live with until the bugfix is officially released (which looks like it will be soon).

Here's the quick steps to apply the workaround:

```
gksudo gedit /boot/grub/menu.lst
``` to edit your grub configuration.

once open, find the line that starts with *kopt=root*=. For example: kopt=root=UUID=0b0asdf03-dk29-dk23-a99a-asdfasdfasdf ro

and append *nomodeset* to that line, (in other words, place a space after *ro*, then enter *nomodeset* right after it)

((EDIT: If this file is blank or doesn't exist, you may need to refer to [the release notes here]("http://www.ubuntu.com/getubuntu/releasenotes/910#Brightness%20flickering%20on%20MSI%20Wind%20netbooks%20with%20KMS") your GRUB2 settings. The fix I'm explaining here is for GRUB v1, which is what any users will have in they *upgraded* to Karmic versus a fresh install. The release notes explanation for GRUB2 is just as quick and easy!))
Save and close the file.

From the terminal:

```
sudo update-grub
```

Reboot, and see if the fix worked! I hope this helps a few other frustrated MSI Wind / Karmic users for the meantime.

---

### Post by pearldrums on 2009-11-19
Did this NOT work for any one else? I have tried the workaround for grub1 to no success. Once my grub was upgraded to grub2 I tried again and still no success.

---

### Post by wirelessman on 2009-11-20
After I did the "fix", the flickering stopped, but moving from screen to screen (on my desktop, icon to icon)is VERY SLOW!

---

### Post by mckelly46 on 2009-11-30
I wouldn't recommend 9.10 on a MSI at all. 

The flicker might be the least of your problems. For example, if you dual boot with XP, you will find XP gets trashed. I can no longer get to the Windows side.

Fortunately I can read my Windows files from the linux side.

Anyway, I wonder if a reinstall of Jaunty would fix the problem?

Michael

---

### Post by mckelly46 on 2009-12-01
BTW I did the "fix" and lost my mouse (both wireless and touchpad). Flicker went away but a small consolation considering the importance of a mouse.

Oh, and while the flicker is gone, the recurring image of the screen brightness icon is still there (at the top right corner of screen).

Still no access to Windows side of my dual-booted machine.

Plenty of sighs ...

Michael

---

### Post by dfme on 2010-01-10
updating to latest msi u100 BIOS solved a lot of issues i had with this machine! webcam and flickering.
I suggest updating your bios!

---

### Post by ricojonah on 2010-01-10
> **dfme said:**
> updating to latest msi u100 BIOS solved a lot of issues i had with this machine! webcam and flickering.
I suggest updating your bios!

dfme, thanks for the info. I've had a little trouble finding the newest BIOS version from MSI's site. Could you provide a quick link? 

Thanks again!

---

### Post by kaptainkatsu on 2010-01-14
[http://www.msi.com/index.php?func=downloaddetail&type=bios&maincat_no=135&prod_no=1474](http://www.msi.com/index.php?func=downloaddetail&type=bios&maincat_no=135&prod_no=1474)

I too updated my Bios and running the latest Kernel. 2.6.31-18

No flickering. I took out the nomodeset flag out of the grub config file and again, no flickering.

Hope this really fixes the problem

---

