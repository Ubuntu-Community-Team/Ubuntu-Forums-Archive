---
title: "OMG my computer's not even starting"
date: 2007-04-15
forum: Hardware &amp; Laptops
---

### Post by LostArt on 2007-04-15
Ok I just tried installing beryl on my computer, and I followed the tutorial carefully and did everything it said, but when I restarted my computer this popped up

a horrible looking blue screen with weird text saying "Failed to start the X server (your graphical interface) it is likely that it is not setup properly. Would you like to view the X server output to diagnose the problem?"
I went on "No" and it said "The X server is now disabled. Restart GDM when it is configured properly".

Then it goes to a black screen with white text, and from there I have no idea what the hell to do, so I started to hyperventilate, and now I'm going to curl up in a little ball and prey for some help.

thanks for the help.

---

### Post by teaker1s on 2007-04-15
at boot hit recovery kernel in boot and
```
sudo dpkg-reconfigure xserver-xorg
``` follow the prompts and you should get a working gui
```
startx
``` do you get a gui? if yes then log out and 
```
sudo reboot
```

---

### Post by LostArt on 2007-04-15
Okay, i got Ubuntu working again, and I'm gonna try another tutorial for beryl later today, thanks.

---

