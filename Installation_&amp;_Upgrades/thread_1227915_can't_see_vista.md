---
title: "can't see vista"
date: 2009-07-31
forum: Installation &amp; Upgrades
---

### Post by juliankossmann on 2009-07-31
i am trying to install a vista/kubuntu dualboot on my friends laptop (HP pavilion dv 2000) and according to the installation guide on this website: [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=3&viewall=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=3&viewall=1) , in step 4 of 6 of the installer it should metion the fact that vista/longhorn is installed, and then install ubuntu in the free space, however it neglects to mention anything about vista, except when choosing what partition to install it on, the default reads install THEM side by side, implying there is another system..

in the live disk in dolphinn there is a volume (ntfs) disk in places, but when i click it i get The enclosing drive for the volume is locked.

i am afraid to continue as it might remove vista and all the data on that partition... HELP??!!..

thanks

Julian

---

### Post by Mark Phelps on 2009-07-31
Laptops have an especially bad time with Linux distros, primarily because the OEMs do so much customizing of the hardware and drivers.  Your best first step is to download, burn, and boot from a Kubuntu LiveCD -- to see how well the Ubuntu version detects your hardware and installs the drivers.  Anything that does not work from the Live CD is going to be a challenge, ranging from easy to impossible, to solve after installation.

Also, do not allow the installer to shrink the Vista installation.  If you do that, you run the risk of corrupting the Vista OS partition and rendering it unbootable.  If you have a Vista DVD, you can repair that -- but since you have a machine where Vista came preinstalled, I'm guessing that you do NOT have such a DVD.

If you're really worried about damage to your Vista stuff, you should do a backup of the partition before you start.  There are some freeware products you can use to do that.  Macrium Reflect is an MS Windows product you can download; P.I.N.G. (Partimage Is Not Ghost) is a Linux product you can download.  Both will allow you to backup your partitions to external media and restore them.

---

### Post by juliankossmann on 2009-08-01
All the hardware works perectly, screen resolution is correct, everything.

I didn't let the installer shrink the vista partition I shrunk it myself in computer manager,
so far vista still seems to working. 

I could of course back everything up, but unfortunately my external harddisk stopped working yesterday ("...malfuctioned, and Windows does not recognize it") and I have no other big enough hdd... 

thanks for the help, anyway

---

