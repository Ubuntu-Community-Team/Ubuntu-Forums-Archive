---
title: "Install Success, but boot problem"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by Vaelrith on 2007-04-29
I had problems booting the livecd on this computer, but when booting from the livecd if I changed the settings from VGA to 1024 x 768 x 32 (or any other setting besides VGA) the livecd booted fine.  Then I installed ubuntu and everything went fine until I tried to boot it up.

When I try to boot the same thing happens as what happened when the live cd booted with VGA.  The boot screen comes on with the orange bar going side to side then all of a sudden everything turns black and then nothing else happens and I have to turn the computer off.  

Is there anyway I can change the boot options so it doesn't boot using VGA or do I need some kind of driver for my graphics card or what?

And, can this be done without booting ubuntu (on account of I can't)?

You can see this computers specs [HERE](http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c00847947&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN)

---

### Post by Ziox on 2007-04-29
boot up your computer and go into the recovery mode
you can access the recovery mode by hitting ESC during the Grub loading screen, and selecting your kernel (recovery). This automatically boots you into root without any GUI.

Now you can remove the boot screen to see if that helps.

sudo nano /boot/grub/menu.lst

then scroll down to the part similar to this:

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=fdc74973-76b5-433e-9f89-2eaacba08b64 ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault


Remove the "splash" in the line "kernel". 

Then "sudo update-grub" and "sudo reboot"

---

### Post by Vaelrith on 2007-04-29
I managed to jot down what looks like a problem when it starts booting.

> * Loading hardware drives...
firmware_helper[3624]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:03:00.0' with driver '(unknown)'
firmware_helper[3641]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:03:00.0' with driver '(unknown)'
firmware_helper[3649]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:03:00.0' with driver '(unknown)'

---

### Post by Ziox on 2007-04-29
I suspect your Wireless card.  If there is a on/off switch, then play around with that abit. 

I have a HP Pavillion dv6000t and I had trouble booting when I had my switch on the off position.

---

### Post by Vaelrith on 2007-04-30
I've been trying to boot with it turned on, but I'll try it with it turned off.  I don't think ubuntu has a driver for my card because when I'm on the livecd I can't connect to the internet...

Could that be the problem preventing startup?

Also each time I boot I have to use noapic and I get into ubuntu, but not after it performs a disk check on one of the drives and it usually freezes part way through.

---

