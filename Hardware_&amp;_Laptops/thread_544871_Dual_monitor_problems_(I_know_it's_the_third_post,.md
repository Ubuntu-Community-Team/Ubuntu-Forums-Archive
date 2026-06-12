---
title: "Dual monitor problems (I know it's the third post, I was told to post in this forum)"
date: 2007-09-06
forum: Hardware &amp; Laptops
---

### Post by Chuckles8732 on 2007-09-06
I am running Ubuntu with the KDE desktop environment installed on top. I just tried to run two monitors as seperate monitors (my laptop monitor and an external monitor) through the KDE system settings page. Now the laptop screen is in 640x480 and garbled. If I try to open the display config page in the KDE system settings, it opens half in each screen (sticking out of the laptop screen if no other monitor is connected) and the computer freezes if I try to move the window. I need help to fix it, I'm thinking editing xorg.conf will fix it, but I do not know how to edit it. I also noticed that the computer now thinks there are three monitors regardless of what is connected. Can anyone help? I've been waiting for help for a week or so, no answer in general help and I was told to post here in the beginner talk.

---

### Post by Chuckles8732 on 2007-09-06
Can anyone at least tell me how to edit my xorg.conf? Or should I ](*,) reformat and reinstall ubuntu?

---

### Post by Chuckles8732 on 2007-09-06
You know, I was told they have good experts here!!!! :confused:

---

### Post by Chuckles8732 on 2007-09-07
I am starting to get slightly ticked off. Is there really nobody out there who can even tell me how to edit my xorg.conf? :evil:

---

### Post by tenmillionmilesaway on 2007-09-07
If you run then it will open up your xorg.conf file,
```
 sudo kate /etc/X11/xorg.conf
```

but i would try 
```
sudo dpkg-reconfigure xserver-xorg
```
 first as this is a kind of gui for editing the xorg

---

### Post by Chuckles8732 on 2007-09-07
Ok, thanks, I'll try that. Should I stop the X server first? I'm going to try anyway. Thanks again. :)

---

### Post by Chuckles8732 on 2007-09-07
Ok, I reconfigured, the garbled screen went away, and xorg.conf thinks 800x600 is the only mode, but the screen is still 640x480 and i cannot change it. Any suggestions for this problem? Please?

---

### Post by Chuckles8732 on 2007-09-07
I managed to fix it :):)

I reconfigured again and selected 640x480 too rather than just 800x600 in the "which resolutions would you like xorg to use" or whatever it is box.

---

