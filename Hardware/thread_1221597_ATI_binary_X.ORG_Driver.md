---
title: "ATI binary X.ORG Driver"
date: 2009-07-24
forum: Hardware
---

### Post by abandonedthe_mulletator on 2009-07-24
My friend sent me this.  What can he do to fix it?

Hi,

not sure why i did this but (i thought it would make the xorg run faster)
i added  "ATI binary X.ORG Driver" last night. when i was done i shut off the computer.
today when i turned it on it showed the UBUNTU screen loading then the screen goes black and nothing ever happens after that.
is ther anything i can do after i press esc at the begining? can i remove "ATI binary X.ORG Driver" from the esc screen?
i tried to reboot in recovery but it just does the same thing. from the black screen nothing works.
i tried ctrl alt delete, f1 - f12, cntrl alt backspace
it must be something from the esc screen before it boots.

Thanks

---

### Post by abandonedthe_mulletator on 2009-07-28
Come on people.  Where is the love.
The whole appeal of linux is the community support aspect.

---

### Post by Sepanderi on 2009-07-29
> **the_mulletator said:**
> 
i tried to reboot in recovery but it just does the same thing. from the black screen nothing works.

Thinking that he has done something with X / graphics drivers, I think he should still be able to boot to the non-graphical terminal through GRUB's recovery menu. This may help: [http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/](http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/)

Another way is to boot from the LiveCD and mount the file system (it should be mounted automatically). From there, I would check the /etc/X11/xorg.conf and possibly revert to one of it's backups.

---

### Post by abandonedthe_mulletator on 2009-07-30
I was able to boot using a live usb.  The xorg.conf is fine, I tried booting from a previous version and nothing happened.  Also I deleted xorg.conf and hoped Ubuntu would try to configure it on its own but no luck.  What should I do?

---

### Post by Docaltmed on 2009-07-30
> **the_mulletator said:**
> I was able to boot using a live usb.  The xorg.conf is fine, I tried booting from a previous version and nothing happened.  Also I deleted xorg.conf and hoped Ubuntu would try to configure it on its own but no luck.  What should I do?

Do you have a backup of the xorg.conf file from before all of this happened? If so, try restoring it and rebooting. I don't know for sure, but there may be "generic" xorg.conf files that you can download then use to get up and running.

---

### Post by apocalypse80 on 2009-07-30
Enter recovery mode from grub menu (you might need to press a key to enter the menu if you're not dual-booting), then get to root terminal.
There run ; 
aticonfig --initial
aticonfig --acpi-services=off

Then reboot and all should be well.

At least that's what fixed it for me back when 9.04 was first released.
After that I've installed all fglrx versions from the ati site without issues.

---

### Post by abandonedthe_mulletator on 2009-07-31
Thanks for the help.
I tried 
```
aticonfig --initial
aticonfig --acpi-services=off
```

and I got
```
aticonfig: No supported adapters detected
```

and there was no change.

Also I tried this
```
sudo dpkg-recounfigure xserver-xorg
```
to do an auto configuration for X but it did nothing.  The xorg.conf file is generic but I still get a blank screen


lspci tells me he has a Nvidia GeForce MX 440 AGP 8x

I don't know why he tried to install an ATI driver.
Any other ideas?

---

### Post by abandonedthe_mulletator on 2009-07-31
Ok I fixed it.
I removed the ATI driver and installed the correct Nvidia driver using apt.

Thanks guys!

---

