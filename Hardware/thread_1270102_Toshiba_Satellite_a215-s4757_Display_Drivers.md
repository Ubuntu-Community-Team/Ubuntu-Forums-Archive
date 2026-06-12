---
title: "Toshiba Satellite a215-s4757 Display Drivers"
date: 2009-09-19
forum: Hardware
---

### Post by srChrisKnight on 2009-09-19
Well, I recently got into ubuntu, and I got into it pretty hard. I have been a pc man all my life. I still can appreciate it, however the attraction to open source computing has always been in the back of my mind. Now that i have tried it out, i am in absolute love with it. Thank you all for such a wonderful OS.

While that is all fine and dandy, it is not why i am posting. I need help.

I am running Ubuntu 9.04 on my Toshiba Satellite A215-S4757 Laptop. Everything works surprisingly well, however my display is a little off. It has a tendency to flicker in and out (when i open a new tab, or play withe the cube <3.

When connected to a monitor, The entire screen is... shaky. Almost static-y, not so bad i cant use it, but bad enough to notice. I don't know how to go about fixing this. I did a search and did not find anything relating to my problem specific enough to solve it.

I have tried updating my system, and i did scan for new/proprietary drivers... Nothing

Any ideas?

---

### Post by IcarusR on 2009-09-19
It would help if you told us what graphics it has.

---

### Post by srChrisKnight on 2009-09-19
Sorry, It is an ATI Radeon X1200

---

### Post by andon21 on 2009-09-20
I have the same laptop and can say with experience that ATI + linux for me at least has always been a royal pain. The x1200 has always had sub-par support from ATI ... the open sourced driver is basically the only bet and the ATI packaged ones are incompatible with the new Xorg server so no luck there. I attempted downgrading Xorg back to the older one in Gutsy but that failed miserably. I'll be interested if anyone manages to do that. But until then I can't afford to mess with my laptop and linux. Once i get my new one i'll be happy to use this as a test machine. Good Luck and next time go Nvidia.till then i'll be looking through windows to see the world :(

---

### Post by srChrisKnight on 2009-09-20
Bummer :(

Well like i said it DOES boot and it IS usable... just a little annoying when using desktop effects. And very annoying when connected to certain monitors.

If anyone has any ideas please let me know. For now i will be running both windows 7 and ubuntu.

---

### Post by Yellow Pasque on 2009-09-21
Right now, there are two open-source drivers, radeon and radeonhd. These drivers share the same acceleration code, but they do mode-setting a bit differently (in the future, the mode-setting code will move into the kernel and obsolete the current drivers). I suggest trying the other one: [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

Installing the radeonhd driver won't conflict with the current radeon driver. You can always switch back and forth by editing the 'Driver' line in your xorg.conf

---

### Post by Zombywuf on 2009-11-10
I've found the Radeon drivers seem to play badly with CPU frequency scaling. Try forcing your CPU to it's highest frequency setting. The easiest way is to use the CPU Frequency Switcher applet in gnome-panel.

---

