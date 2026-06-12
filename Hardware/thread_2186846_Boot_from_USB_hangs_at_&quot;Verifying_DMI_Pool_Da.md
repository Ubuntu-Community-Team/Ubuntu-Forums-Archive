---
title: "Boot from USB hangs at &quot;Verifying DMI Pool Data&quot;"
date: 2013-11-09
forum: Hardware
---

### Post by ogp on 2013-11-09
Hello, 

I'd be grateful for any help with a problem I am having booting from a USB memory stick. 

I have a desktop computer which has dual-boot XP and Mint (Mate). I have run many different *buntu installations on the machine over the last 3 years, the early ones booted from a CD and later ones booted from USB (when the installer files became a bit too big to fit on a CD.) Each time it has worked fine, the machine has booted from the USB stick and I have gone straight into the installer. 

I'm trying to install a new Linux install - Kubuntu 13.10 - to replace the Mint installation. I have downloaded the Kubuntu 13.10 desktop 32-bit iso file, use unetbootin to put it on the USB stick and tried to boot from it, but the computer hangs at "Verifying DMI Pool Data". The hardware hasn't been changed since I last loaded a Linux install onto it (about 3 weeks ago) and I am using the same USB stick, formatted to FAT16 (as before). 

I have tried other iso's - ubuntu, Mint-KDE and the minimal install mini.iso. All of them produce the same results - it hangs at "Verifying DMI Pool Data". I can choose any of the USB options at boot (by pressing F12 I get a list of boot devices); USB-FDD, USB-ZIP, USB-CDROM or USB-HDD, and they all do the same thing. The USB stick seems to work fine in all other ways (you can save stuff onto it and read stuff off it), and unetbootin runs fine without producing any errors. I can also use the USB stick in other machines (I've tried it in a laptop) and it produces the installer as you would expect. 

I have checked the USB stick in gparted and it as the bootable flag raised. Is there anything else I should be looking at? 

For what it's worth, the motherboard of the machine is a Gigabyte GA-MA790GP-DS4H. As I said, I have installed a number of Linux distro's on this machine with this USB stick in the last 3 years and never had this problem before. If I don't have the USB stick plugged in then the machine goes through to GRUB fine and allows me to boot into XP or my Mint install. Google suggests that the problem is possibly hardware related, hence the post in the "Hardware" part of this forum. 

If anyone can help me, I'd be really grateful - thanks. 


Oli.

---

### Post by ogp on 2013-11-09
Two more bits of information which may be useful; 

- I have tried plugging the USB memory stick into other USB ports on the computer, but it makes no difference

- I have just tried booting from a CD of an old version of Ubuntu and it boots from CD fine. 


Oli.

---

### Post by ogp on 2013-11-18
Very slight update; I didn't make the machine boot from a USB stick but I did manage to rebuilt it using the method here: 

[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

... installing from within an existing linux installation. 

If anyone can shed any light on the problems with USB-installation I had then I'd be interested to hear them but it's not important. 


Oli.

---

### Post by brokenhorseshoe on 2014-01-10
hi I have the exact same motherboard same problem.

I try same as one all the usb port and two differant usb sticks
then I reminbered how all the motherboards have changed to this efi for bois

I figured I would try to install an older usb with older ubuntu 12.10 and it worked

not sure what but theres something with the new efi and new ubuntu conflict older bois in that board


I installed older usb multiinstaller using [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) yumi a year ago and it was on the usb already you could try that and install older ubuntu maybe thats it/

---

