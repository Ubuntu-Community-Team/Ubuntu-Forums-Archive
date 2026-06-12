---
title: "Ubunu 14.04 and Nvidia ION graphics - HDMI out not working"
date: 2014-12-28
forum: Hardware
---

### Post by aaron68 on 2014-12-28
I have an old Asus 1201n netbook that has a broken screen so I decided to just load ubuntu on it and use it as a media server machine for my TV.  My problem is that the HDMI port on it is no longer working.  I use the VGA port to plug into my computer screen to tinker on the netbook but when I hook the HDMI to the TV the computer screen immediately goes blank and does not come back and I get no output on the TV either.  The only way to get video again is to do a hard shutdown and reboot.  I have tried rebooting only connecting the HDMI but still get no signal.  

The system is clearly acknowledging that a cord is being plugged in but I get no output.  Is there a GUI for nvidia settings or a config file I can take a look at?  Again the netbook is an Asus 1201N with Nvidia ION graphics card.  Thanks for any help, I am relatively new to Linux, thanks.

edit:  I have searched the system for the nvidia x server settings GUI that I keep on seeing on youtube but it doesnt seem to be installed on my system.  I have tried to manually install their proprietary drivers from the command line but it keeps telling me that it cant install them because the X server is running.  It appears it is the Xorg process and every time I try to kill this process using the kill command as root it just starts right back up.

---

### Post by aaron68 on 2014-12-28
update:
used apt-get purge to remove any nvidia drivers and was able to install nvidia 340 drivers.  I have the x server settings gui and all that but still same problem.

---

