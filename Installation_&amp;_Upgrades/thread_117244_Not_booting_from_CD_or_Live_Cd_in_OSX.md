---
title: "Not booting from CD or Live Cd in OSX"
date: 2006-01-14
forum: Installation &amp; Upgrades
---

### Post by enzedchris on 2006-01-14
I am running an iMac G5 Rev. B with Tiger and I have never been able to boot from Ubuntu CD's, only mac ones and I can't get to yaboot. none of my key commands work at start-up, and no I am not using a bluetooth keyboard at start-up, i am using a logitech that works fine otherwise. ubuntu will also not show up in my start-up disk pane. i have been able to run this on old g3 slot-loading but have since parted that out, and this keyobard worked for booting it. I don't know why this computer just is not working, is ther anything i need to install to "open it up" so that it will recognize and boot from ubuntu cd at start up
btw these are the official ubuntu cds for ppc, not ones i burned, and the version is 5.10

---

### Post by linear on 2006-01-14
Two things you can try:

1. Is the keyboard plugged into a hub? If so, try it direct into the iMac.

2. If the CD still won't boot, try this incantation from an Apple support article:

([http://docs.info.apple.com/article.html?artnum=25793](http://docs.info.apple.com/article.html?artnum=25793))

> Restart the computer and hold these keys: Command-Option-O-F . This asks the computer to start in Open Firmware.
Tip: If you don't start in Open Firmware, try again. Make sure you're using a USB keyboard, and that the keyboard is connected directly to one of the computer's USB ports.
type: boot cd:,\\:tbxi
Press Return.


---

### Post by enzedchris on 2006-01-14
no it was direct and i know not to use a bluetooth keyboard, i tried each of the three usb ports. i have been trying that key combo the whole time, that was what i wanted to do the whole time to get into yaboot prompt but it just keeps bootign into osx. i have no idea why this is happening, i am doing these key combos in the right order during the start chime, i have no idea why this does not work.

---

### Post by yottabite on 2006-01-26
That open firmware command for booting CD's really helped me boot the Breezy CD while using a Logitech keyboard on a Mac Mini. Most keyboard commands don't seem to work with this USB keyboard, and I am currently considering an Apple keyboard in the event I may need one, but at this point as long as I can get into open firmware it looks like I can do most of what would be needed to recover the mini.

(To get into firmware I held the power button in untill the chime, watched the blinking power LED, and presto - open firmware)

Thanks!

---

