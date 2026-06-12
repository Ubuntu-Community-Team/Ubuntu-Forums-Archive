---
title: "MSI GT683R-242US on 64-bit ubuntu 11.04?"
date: 2011-06-21
forum: Hardware
---

### Post by Martin__ on 2011-06-21
Hi, has anybody tried installing 64 bit ubuntu 11.04 on a MSI GT683R-242US laptop?
The new NVIDIA driver [http://www.nvidia.com/object/linux-display-amd64-275.09.07-driver.html](http://www.nvidia.com/object/linux-display-amd64-275.09.07-driver.html) supports the GeForce GTX 560M, and was the full 3D acceleration and the rest of the laptop working OK?

---

### Post by OpenMouth_os on 2011-09-15
yes. i would also like to know this. I heard that this laptop will not include nvidia optimus (thank god!!). But even without optimus, I want to know if ubuntu recognizes the graphics card (Geforce GTX560m).

I hope somebody might share his experience on this laptop or graphics card.

---

### Post by Mr_Blacksmith on 2011-10-19
My work just purchased a GT683R for me, just got it today.   I for the life of me can not get Ubuntu 11.10 to install or live boot.   It looks like there is a kernel issue with loading it stops at usbhid and there are problems with nouveau driver right before.   I'm still investigating whats wrong, this problem exists in other distro's too (fedora,Suse)  I've tried several, and no linux love.   

So right now I say hold off on purchase.   This saddens :( me to say this, since this machine is sweet.

---

### Post by Mr_Blacksmith on 2011-10-19
ok,  update.     when booting press any key to get to the grub screen, then hit f6,  then esc.   edit the boot parameters remove the --   and add the following

rdblacklist=nouveau nouveau.modeset=0 xdriver=vesa     


this will allow you to boot the live disk and install.   So far everything works as far as i can tell hardware wise.

---

### Post by Mr_Blacksmith on 2011-10-20
Ok,  post install update.     All important hardware works wireless,ethernet,bluetooh,sound,Nvidia 560m (with propriatary driver), webcam, microphone, etc...   What is not working is some of the nifty touch buttons, the side led's wont come on, turbo,P1, windows button prevent or eco.  These are not critical to the functioning of the laptop.    The other touch buttions bluetooh, wireless and extra fan all work.


So I'm retracting my don't buy this yet, so if you were thinking of getting it go for it.   This is a very good laptop with a lot of power and pretty good battery life. :p

---

