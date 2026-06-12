---
title: "Ubuntu 8.10 kernel v2.6.27.13 upgrade ?"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by ddastoor on 2009-03-05
Hi All, 
(System: Dell Inspiron 6400 Laptop)

I installed Ubuntu 8.10 (kernel v2.6.27.12) a while ago and all was fine. Just yesterday, I got an upgrade-bubble telling me that (kernel v2.6.27.13 generic) was available.

Though I'm not a linux newbie, I'm new to Ubuntu's update mechanism, and so in good faith, I installed the updates. After the update was finished, I got a popup stating that I needed to restart.

Along with a host of other dependencies, expectedly, the new kernel image and initrd files were copied to /boot (in my case, a mount to a dedicated grub partition).

I, then modified the consolidated menu.lst file (in the grub partition) with the new kernel entries.I restarted and chose the new kernel v2.6.27.13 generic and my screen wehnt blank and my PC froze.

I managed to boot back into kernel v2.6.27.12 using my grub boot disk.

----------------------------------------------

My question is: What went wrong? Did I miss something? Can I indeed install v2.6.27.13 again, doing something differently?
Kindly advice.

Thanks, 
Dinshaw

---

### Post by Vevmesteren on 2009-03-05
Same problem for me. Regular old user, know my way around Terminal, so any hints and tips would be greatly /appreciated. Am currently running out of -12 as -13 gave be the black screen. 

Possible that some packages for -12 where not properly configured to run under -13? 

I am running 8.10 on a Dell XPS M1210, 4Gig Ram. 

until then startupmanager is a nice tool to have :)

V

---

### Post by ddastoor on 2009-03-05
u used grub to get back to -12, right ?
startupmanager is for apps, then ?

---

### Post by avtolle on 2009-03-05
I upgraded to 2.6.27.13 yesterday, with no problems. I noticed that as I have a nvidia card (model escapes me at the moment) on the laptop where said kernel was installed, there was loading of the module for the 177 driver via DKMS (I think that's what the terminal output said), and upon reboot, all was well. Running 8.10 64 bit, Compaq Presario f750US, 1 GB RAM. Wondering if you have either nvidia or ATI graphics card with drivers installed manually?

---

### Post by ddastoor on 2009-03-06
Yes, I did install the "nvidia graphics acceleration 177 (recommended)" manually though "restricted drivers". Would this be a proglem ? Should I uninstall this ?
Im on an x86.

Thanks, Dinshaw

---

### Post by blde99 on 2009-03-06
Take a look in this [thread]("http://ubuntuforums.org/showthread.php?t=1084959")

---

### Post by ddastoor on 2009-03-06
thanks blde99 ... will follow that thread... : )

---

