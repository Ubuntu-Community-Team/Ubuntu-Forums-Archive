---
title: "Using both intel and amd graphics for dual screen"
date: 2013-03-28
forum: Hardware
---

### Post by arcsin on 2013-03-28
In windows I normally use the vga port on the motherboard I/O panel and the vga port on my amd graphics card.

However when I try to enable the screen connected to the motherboard from the display and monitors settings it logs me out of my session and takes me back to the login screen.

---

### Post by arcsin on 2013-03-28
I've done a bit of googling and it seems I need to set up a dual head in xorg and tell it to use the ati drivers for 1 screen and the intel drivers for the other. However I've never played around with the xorg config files so if someone could tell me where to get them and what bits to play about with would be awesome.

---

### Post by Bashing-om on 2013-03-28
arcsin; Hi !

I do not use hybrid graphics thus reluctant to respond - 'till I seen your last.
 "xorg config files" are now largely depreciated. Take a look at these links:
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

[http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics](http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics)
[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)

I expect they will give direction on how you may want to proceed.[INDENT=3]
just try'n to help

[/INDENT]

---

### Post by arcsin on 2013-03-28
> **Bashing-om said:**
> arcsin; Hi !

I do not use hybrid graphics thus reluctant to respond - 'till I seen your last.
 "xorg config files" are now largely depreciated. Take a look at these links:
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

[http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics](http://ubuntuforums.org/showthread.php?t=1930450&highlight=hybrid+graphics)
[https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux)

I expect they will give direction on how you may want to proceed.[INDENT=3]
just try'n to help

[/INDENT]


Thanks, those links are for laptops that have switchable graphics.

I should have said that this is a desktop with an AMD 7850 and Intel HD 4000 graphics. (Currently it seems to be defaulting to run the amd card)

---

### Post by Bashing-om on 2013-03-28
arcsin;
Again I must default to a lack of knowledge and refer you to the best guide I have seen:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
A very long thread as a treatise on many graphics problems and how to troubleshoot them. Best I recall about 2/3 's of the way through it is MAFoElffen's procedure using the Xorg file to switch cards.[INDENT=2]not much, but I hope it helps

[/INDENT]

---

