---
title: "Grub password reset - change default OS"
date: 2008-09-16
forum: General Help
---

### Post by scotthammy on 2008-09-16
So for all my love of ubuntu I'm heading back to windows, I'm still very keen to keep ubuntu and upgrade to new versions as they come out, every since I found ubuntu 4 odd versions ago, it has jumped leaps and bounds. getting so much better every time, more support easy of use. 


[COLOR="DarkGreen"]However[/COLOR]


I have multitude of Ubuntu faults and I'm hoping someone can help me back up and running..

Currently on running **DELL XPS 1530 **(updated firmware in windows to A6 i think, now I cannot use the mouse as it moves around the screen with its own mind. Touchpad fault no doubt.

**So my Questions are:**


[COLOR="DarkRed"]1, How can I reset the Grub password so I can set Vista as the Default, and keep the ubuntu,  I was going to format my HDD and put Vista back on but id really like an easy way to reset this.[/COLOR]  


[COLOR="DarkOliveGreen"]2. Since I have done the firmware upgrade the Mouse in Ubuntu is no longer usable, It moves around the screen in high speed and clicking all over the place.
I hope some wise GURI can help me on this one. [/COLOR]


[COLOR="DarkRed"]If someone can give me step by step using the command prompt [/COLOR]

[B]Thanks
Scott NZ.[/B]

---

### Post by Iowan on 2008-09-16
I'm not sure about the GRUB password, but you can change default OS by editing **/boot/grub/menu.lst** and changing the number in the line that (probably) reads **default  0**. (I like **sudo nano /boot/grub/menu.lst**)
BTW, I have this Gutsy Ubuntu machine and a Hardy Xubuntu machine connected via KVM switch.  If I boot a machine with KVM switched to another machine, sometimes the mouse gets crazy when I switch to booted machine.

---

