---
title: "saned altered scanning margins?"
date: 2007-06-01
forum: Hardware &amp; Laptops
---

### Post by tuco penguin on 2007-06-01
I am using Xsane under Feisty to scan docs as needed.  I recently migrated the all-in-one printer/copier/scanner (HP PSC-750) over to a newly resurrected PC acting as a home server (also running Feisty), which now includes cups for print sharing and saned for scanner sharing.

I am now noticing, however, that the scanned images are not all there.  The scanner appears to not be capturing the left most edge of the page--I am actually missing 0.5-0.75 inches on the left hand side of the page.  On first scan it looked like my paper had been misplaced on the bed, but in fact it was placed exactly in the right spot.  The problem is reproducible, but I have not tried moving the scanner back over to the USB port for a direct connection to the desktop computer.  Does this sound like something that could be part of a saned configuration file?  If so, where is that file and what settings should I look for?

Clearly not a Ubuntu-specific problem, but the community here is so great I could not think of a better place to ask.  If I can get the help I need, I'll be tempted to ask for help fixing my Toyota parking light problem!;)

---

### Post by tuco penguin on 2007-06-04
OK, fixed this one myself--posting results in case it helps anyone else in the future.

There were some strange settings in the configuration file for my scanner, located in:
/home/[username]/.sane/xsane/[scannername.drc]  (note hidden ".sane" directory)  Namely, these
```

"tl-x"
0
"tl-y"
0
"br-x"
14136115
"br-y"
19459340

```
for some reason, however, "tl-x" and "tl-y" were not set to zero, but to some rather large number.  Surmising that these designated the "top left" and "bottom right" corner of the scanner bed in pixels (or some other metric) I tried setting the "tl" numbers to zero and I got the right effect on the scan image area.  Note, this is just speculation, not from any documentation, but it worked for me.  Now, I never opened these file before, so they certainly weren't altered by me, but an older .drc file from my pre-saned days (when my scanner was just local) was also present in this directory and had "tl-x" and "tl-y" set to zero, so something about my networked scanner installation had the effect of creating or altering this file.

Anyway, happy scanning now.:p

---

### Post by thrice_loved on 2007-12-13
Have a look in the settings of xsane. 
One setting is the Top-left Bottom-right setting. When the top is lower than the bottom setting, or the right is further left than the 'left' setting it cannot scan.

They are found in "window" > "Advanced Options"

Set the first two to zero (left hand side) and the other two to whatever your maximum is (right hand side). This fixed the problem for me. Also if it doesn't stay that way you can save the scanner settings so that this change is permanent.

---

