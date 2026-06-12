---
title: "Cannot load live cd nor install 8.04"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by RageAgainstThis on 2009-01-14
The title says it all.  I have recently aquired an older laptop hp zx5180us with no OS.  

I have tried running 8.04 and 8.10 live cds with no success.  My intention is to install.  I have also tried the alternative install without success as well.  I get through the main screens just fine, but then after a this warning mentioned [here]("http://ubuntuforums.org/showthread.php?t=836358") the screen goes blank.  

Both puppy and tinyme (pclinuxos) boot up just fine without any hiccups.  I would really like to install ubuntu as that is what I use daily on my desktop.  

I suspect the problem I have on windows may be why ubuntu is behaving the way it is. After a fresh win2k install everything works fine until I install the GART drivers, which apparently has something to do with the graphics card.  After rebooting my win2k the screen would lock up on the loading windows and it would restart.  

Any help would be appreciated.

---

### Post by logos34 on 2009-01-14
What about trying Xubuntu?  Might have the same problem, but worth a shot

---

### Post by meindian523 on 2009-01-14
Are you sure you have the correct ISOs,checked the CDS,and burnt them slow?

---

### Post by RageAgainstThis on 2009-01-14
Yes, I have tried Xubuntu, and I have done a media check.  These disks work fine on other computers.  Right after that error I mentioned with the broadcom wireless firmware the disc stops loading, so I just sit at a black screen.  I have left the computer on for 30 minutes to see if it would go anywhere, no such luck.  

Also, I have update my dvd drives firmware to the latest to see if that may be the problem.  I guess my next shot in the dark may be to load ubuntu from usb.  We will see.

If anyone has any suggestions please post and thankyou to those who did.

---

### Post by abn91c on 2009-01-14
pull the wireless card then use a **wired** connection during the install, that way when its done you can mess with the wireless at that time

---

### Post by RageAgainstThis on 2009-01-14
The wireless is integrated into the motherboard, I can not disable it from the bios either.

---

### Post by Bucky Ball on 2009-01-14
Perhaps a dodgy graphics card. Older machines can be problematic; just spent hours on a friends crappy old p4 trying to do the same. You are getting one single short beep when you switch the machine on? I would test the hardware before commencing a software investigation. You have nothing plugged into the box, no usb or external drives of any kind?

---

### Post by RageAgainstThis on 2009-01-15
Actually, I have some reason to suspect the graphic card may be going south, because of the issue with the GART drivers as stated above.  However, both pclinuxos and puppylinux boot without any error what so ever.  

I will be trying an install from usb, if that doesnt work I will just put pclinuxos on the laptop.  I just prefer ubuntu as that has been my distro of choice for quite some time now. 

Thank you all for you help,

I think ubuntu from the CD is just not going to work out for me, crossing my fingers for usb :).

---

### Post by ryanjanssen on 2009-01-15
I am also having the same problem with old a HP desktop, every time I try booting off the live cd I get the I/O error. The disc works fine with my MacBook also the HP's drive seems to be working fine under xp.

---

### Post by Bucky Ball on 2009-01-15
Is your error message exactly the same as the one on this page from your first post [here]("http://ubuntuforums.org/showthread.php?t=836358")?

If so, sorry. This would definitely have something to do with you card's software. It might pay to try fixing this before you give up. Does it connect eventually and *then* hit the blank screen?

Other thing, do you have an ethernet cable plugged in when you are installing rather than wireless? If not, plug in a cable and go again. This will prevent b43 from giving you problems for now (I think, standing corrected if this is wrong) then you can fix the wireless from within Ubuntu once you are rolling.

---

