---
title: "Toshiba a215"
date: 2007-07-23
forum: Hardware &amp; Laptops
---

### Post by plex0r on 2007-07-23
bought this laptop and straight away ripped vista off, everything in the install went ok, but when the system booted xorg failed to start

i ran
sudo dpkg-reconfigure xserver-xorg and played with some things to see what was wrong, i used the ati drivers because the computer has an ati radeon x1200 in it, well that didnt work and it still failed, then i just was messing with some setting and changed it to vga and it worked but everything is huge...any suggestions or any drivers i can use that will work?

---

### Post by Cappy on 2007-07-23
Did you try setting the resolution for vesa?
When you ```
sudo dpkg-reconfigure xserver-xorg
```
and select vesa and then later on when you get to pick your resolution(s), use the arrow keys and hit space on your native laptop's resolution. Once you get into Ubuntu you should be able to use the restricted fglrx drivers by going to System-->Preferences-->Restricted Drivers Manager
Sometimes the fglrx drivers cause the computer not to be able to suspend, however.

---

