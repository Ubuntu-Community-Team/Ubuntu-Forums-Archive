---
title: "nVidia PCI Installation Problem"
date: 2010-05-18
forum: Hardware
---

### Post by funnyname on 2010-05-18
I am having an issue installing a PCI video card GeForce 8400.  After a fresh install of 10.04, I changed the video settings in the bios, install the card, but the system will not boot.  Also using a LiveCD, the system will not boot.

Upon searching, I discovered a solution here [http://ubuntuforums.org/archive/index.php/t-615381.html](http://ubuntuforums.org/archive/index.php/t-615381.html)  but it does not work.  Entering sudo dpkg-reconfigure xserver-xorg  in the terminal brings up nothing.

Is there any solution for this?  This card is better than using the onboard, and this mainboard only has PCI slots.

---

### Post by dabl on 2010-05-18
> **funnyname said:**
> 

After a fresh install of 10.04, I changed the video settings in the bios, install the card



That strikes me as an odd sequence.  I would try it like this:

1. Install the card and do whatever BIOS setting seems appropriate (I am not accustomed to seeing any need for a BIOS setting to accommodate a PCI video card ....).

2. Boot a Live CD.

3. Does it display?  If not, try some of the common boot codes, like:

vga=785
vga=788
vga=791
xforcevesa

If yes, then you're good to proceed with installation. Initial installation is with vesa display.  Afterward, you can use "Hardware Drivers" to install an Nvidia driver.  If no, it starts sounding like a hardware/BIOS problem of some kind.

---

### Post by funnyname on 2010-05-18
The BIOS setting change is to go from onboard to PCI.  Also I tried the LiveCD route with 10.04, PCLinuxOS and Knoppix 5.1.1 in safe graphics mode - nothing.

This seems to be a hardware conflict error during the hardware update search.

Thanks for the reply, I will try some of those suggestions.

---

### Post by funnyname on 2010-05-19
Nothing worked.  I even did a reload this morning of 10.04 with the card in but using the onboard video (bios was not switched to PCI video) and this time the Restricted Drivers option popped up, so I thought greta it detected the card.  So I loaded the drivers, rebooted, switched the BIOS to PCI video and nothing. Same issue.

It truely seems to be stopping at hardware detection.  According to the the link above it has something to do with ghosting.  "the xserver-xconfig tool will detect the pci bus for the on board video card not your Nvidia/ATI card"  There are instructions ther to fix it but the "sudo dpkg-reconfigure xserver-xorg" does not work.

Any suggestions to fix?

---

### Post by funnyname on 2010-05-19
Okay - this is kind of a bump and an update.  Reloaded the OS again.  Thankfully this is a test machine and not my main machine.

The card is recognized.  I see it in the Gnome Hardware Manager as well as the onboard video (which I am still using).  Is there any way as the instructions lay out (although outdated) to get X to use the nVidia card and not onboard first.

---

