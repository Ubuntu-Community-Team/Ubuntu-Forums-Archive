---
title: "Mobility Radeon 7500"
date: 2010-10-12
forum: Hardware
---

### Post by kardhal on 2010-10-12
I have this really old ibm thinkpad t42 laptop with mobility radeon 7500 (rv200). Direct rendering works with ubuntu 10.04 out of the box, which according to this page [http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500)
means i have the open source radeon dri driver installed. My problem is, that it is really freaking slow, even for a legacy card like this. According to the archive of this forum it shoud produce around 2000fps in glxgears yet it does around 400 for me. Every solution i've found to this problem involves tweaking xorg.conf which apparently exists no more in newer ubuntu versions.
Can anyone help me?

---

### Post by kardhal on 2010-10-13
Shameless self bump

Can it be that this card is no longer supported even with the open source driver? I might switch back to win xp than.

---

### Post by scottiw2000 on 2011-01-20
I'm having the same problem with the Mobility Radeon 7500 card. Black login screen (though I can log in blind), VERY slow rendering, a lot of tearing. From what I've read the binary drivers were started by ATI a year or so after the 7500 came out, so we're stuck without proprietary drivers. But is there no way to get the open source radeon driver to work better with this old card? One of the main reasons I like Ubuntu is that it can breathe new life into old hardware, but here WinXP does a better job.

---

### Post by tatsujin79 on 2011-01-21
I have a T41 with a mobility radeon 7500 32MB and after a while of looking I have it working just fine, although there is some screen tearing (but not much to worry about) and some opengl apps just don't like full screen.  

First I added the xorg edgers ppa [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa") and ran a sudo apt-get update && sudo apt-get upgrade

next i install dkms (don't know if this is part of it but it seems to be) 

next I ran sudo echo options radeon modeset=1 | sudo tee /etc/modprobe.d/radeon.conf

next sudo update-initramfs -u and after it was done rebuilding the kernel

sudo nano /etc/default/grub and add radeon.modeset=1 to the GRUB_CMDLINE_LINUX="" line within the quotes and sudo update-grub and restart 

I've attached my xorg.conf file as well if you choose to use it just extract and run sudo cp xorg.conf /etc/X11/ and restart or ctrl+alt+backspace to kill the xserver

You can also use driconf and set the first option to "use software tcl" or something similar and it helps with a few things like osmos for example

Keep in mind that im still pretty new to linux but this has worked for me and my t41 thus far using ubuntu 10.10 on one hard drive and 11.04 alpha on the other.

---

