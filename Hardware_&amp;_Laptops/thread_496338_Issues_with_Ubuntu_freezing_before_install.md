---
title: "Issues with Ubuntu freezing before install"
date: 2007-07-09
forum: Hardware &amp; Laptops
---

### Post by kyleh_ on 2007-07-09
I  just got my HP dv6500 in today, it has:
 t7100 1.83ghz cpu, 160gb 5500rpm hd, 8400 nvidia card, 2 gig of ram and the stock dvd player.  I get into the normal boot screen fine.  When I attempt to do the install, I get the loading Ubuntu screen, then video is lost.  I can still hear the drives spinning, yet nothing is displaying on the screen.  Any clue as to what the cause of this is?

---

### Post by loserboy on 2007-07-09
did you try safe graphics mode,im sure it's having a problem with that nvidia card

---

### Post by kyleh_ on 2007-07-09
Attempted that too, using both the 64bit and x386 disks

---

### Post by loserboy on 2007-07-09
you may have to boot with the NOAPIC or NOLAPIC option, but I don't remember how off the top of my head

do you hear the login sound when it boots?

could you try hitting ctrl+alt+F1 when it gets to that point and see if you get to a command line

---

### Post by merlinus on 2007-07-09
If you can get to a command prompt via Ctrl-Alt-F1:
```

sudo dpkg-reconfigure xserver-xorg

```
You can probably go with the default for most screens, but select "vesa" for your video driver.

Then:
```

startx

```

If this does not work, then try the text-based Alternate Desktop install cd.

Good luck!

-merlin

---

