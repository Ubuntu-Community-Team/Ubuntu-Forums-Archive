---
title: "nvidia installation help needed"
date: 2012-11-03
forum: Hardware
---

### Post by aj7360 on 2012-11-03
Am attempting to go to three monitors, thus installing two NVidia cards (9800GT and 8600) with Lucid Lynx.  The motherboard does support two PCI-e cards.

However, I can't seem to install latest Nvidia drivers. 

Downloaded latest driver from Nvidia website but can't get into console mode... or rather, when I enter Ctrl Alt F1 I have a blank screen. No command prompt. Nothing. 

Been searching here for a couple of hours and have gotten no where.

Any assistance would be greatly appreciated.

---

### Post by aj7360 on 2012-11-03
Apparently I didn't search long enough as I found and tried this command:

sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings

and that did the trick.

Course when I try Ctrl Alt F1 I still see nothing on any of the screens. And now Ctrl Alt F7 doesn't bring X back. 

Needed a hard reboot to bring it back.

---

