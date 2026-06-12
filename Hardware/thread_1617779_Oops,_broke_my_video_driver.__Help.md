---
title: "Oops, broke my video driver.  Help?"
date: 2010-11-09
forum: Hardware
---

### Post by joshuajon on 2010-11-09
So while trying to setup a second video card I installed the nvidia-96 drivers per the instructions here:  [https://wiki.ubuntu.com/X/Drivers](https://wiki.ubuntu.com/X/Drivers) then rebooted.

The new drivers don't work, and now the other display (on an intel integrated card) doesn't work either. 

I was able to boot from a liveCD and restore the xorg.conf but this doesn't seem to have fixed the problem.

The page says > **How to switch back to the open source driver**

 1) Remove your xorg.conf 
sudo rm /etc/X11/xorg.conf 
2) Select the open source alternative (i.e. /usr/lib/mesa/ld.so.conf ) with the following command 
sudo update-alternatives --config gl_conf 
3) Update the ld cache and the initramfs: 

sudo ldconfig
sudo update-initramfs -u4) Restart your computer Any guesses how I could do that to my harddisk from the livecd?  or is there some other way to fix this?  Any help would be appreciated.

---

### Post by joshuajon on 2010-11-09
I'm just about at the end of my rope here.  I can't even boot single user mode!  I append the word "single" to the kernel line in the grub1.5 menu and all I get is 

"Starting up..." then a black screen.

This is maddening.

---

### Post by joshuajon on 2010-11-09
Well I fixed it.  I got single user with an older version of the kernel and reset my drivers to the generic.  I still don't have two monitors but I guess I'll cut my losses and live with one that works.

Sheesh.

---

