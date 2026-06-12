---
title: "HELP!-Ubuntu 8.10 will not install on Dell Dimension 2400 on live CD"
date: 2009-06-20
forum: Installation &amp; Upgrades
---

### Post by poller4 on 2009-06-20
Several months ago, i received a live DVD distribution of Ubuntu 8.10. I have been working on figuring out how to install it on my _stock_ Dell Dimension 2400. With it not having a DVD drive intalled, i purchased an HP USB external DVD drive. A problem I seem to be running into is getting the BIOS to recognize the drive and the disc. What should be my next step?

---

### Post by presence1960 on 2009-06-20
why not just download the iso and burn it to a CD, or have someone you know do it for you if you can't. 
Or if your BIOS will support booting from USB (your drive is USB right?) set your boot order with USB or Removable as first boot.

---

### Post by presence1960 on 2009-06-20
```
Booting to a USB Device
NOTE: To boot to a USB device, the device must be bootable. To ensure that your device is bootable,
check the device documentation.
To restart your computer to a USB device such as a floppy drive, memory key, or CD-RW drive:
1 Connect the USB device to a USB connector (see page 46).
2 Shut down the computer through the Start menu (see page 18).
3 Turn on the computer. When the DELL&#8482; logo appears, press <F12> immediately.
If you wait too long and the Microsoft® Windows® logo appears, continue to wait until you
see the Windows desktop. Then shut down your computer through the Start menu and try
again.
NOTE: These steps change the boot sequence for one time only. On the next start-up, the computer
boots according to the devices specified in the system setup program.
4 When the boot device list appears, highlight USB Flash Device and press <Enter>.
The computer reboots to the connected USB device.
```

That is from your computer manual which I got from dell's web site.

---

### Post by poller4 on 2009-06-22
Thanks guys

     My new question is what to do or where to go if the boot sequence in the BIOS don't include a USB device. I have not tried a google search for an update of the bios if there is one for my model.

---

### Post by mattwilkes512 on 2009-06-23
> **poller4 said:**
> Thanks guys

     My new question is what to do or where to go if the boot sequence in the BIOS don't include a USB device. I have not tried a google search for an update of the bios if there is one for my model.

I have a dell dimension 2400 and mine came with a DVD drive.  At restart/power on press f2 and go into boot sequence deselect harddrive by pressing spacebar and select cddrive by same method.  Switch cddrive to 1st position by pressing the minus key - exit and save.  Make sure live dvd is in top drive and it should boot!  Problem though the dimension 2400 has onboard graphics that arent supported in Ubuntu 8.10 and 9.04 so you'll have to downgrade or boot in safe mode and purge compiz.  Your other option is to buy a PCI graphics card and you can install lastest edition 9.04 .  Good Luck.

---

### Post by mattwilkes512 on 2009-06-23
> **poller4 said:**
> Thanks guys

     My new question is what to do or where to go if the boot sequence in the BIOS don't include a USB device. I have not tried a google search for an update of the bios if there is one for my model.

Latest BIOS is A05 .  Get a graphics card or install Ubuntu 8.04 .

---

