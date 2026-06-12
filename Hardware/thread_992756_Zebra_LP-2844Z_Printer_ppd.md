---
title: "Zebra LP-2844Z Printer ppd"
date: 2008-11-25
forum: Hardware
---

### Post by davemc on 2008-11-25
I have a Zebra LP-2844Z label printer.

The Z suffix indicates it runs ZPL language.  The non-Z models run EPL II language from Eltron, which Zebra aquired.

I find I get mangled print with CUPS 1.1, 1.2, 1.3, 1.4.  The zebra.ppd doesn't seem to have changed through these versions.

I use a 4"x4" label, 101.6mm x 101.6mm.

The page layout seems to be wrong, it's trying to put the output in the wrong place, gets the pagination wrong, then trips out stopping at a non-label boundary, and flashing the red light on the printer.

So I took zebra.ppd and hacked out all the other paper sizes, so the only paper size was the one I have installed, and likewise the imagable area and defaults.  I then used system settings/printers to install, and changed the margins to custom margins of 0 in all angles.

Presto, it works.  I get full sized labels from OpenOffice writer (using a custom paper size of 4x4).

zebra4.ppd file attached, should anyone find it useful.
:)
David
McPond

---

### Post by vpaul on 2009-12-09
I See references to resolution in the file and am wondering if I can get a 300dpi Zebra model TLP3844-Z to print correctly using this?  When I print the label comes out small unless I print to a model 2844-Z.  Can the resolution be added for 300dpi?  I need a 4 x 6 inch 300dpi label. THANKS.

---

### Post by amidala3 on 2009-12-28
Sorry, your driver didn't work for me... i used the variant in the attachement;
Maybe it helps someone...
Amidala

---

### Post by llargotuejar on 2010-05-27
> **amidala3 said:**
> Sorry, your driver didn't work for me... i used the variant in the attachement;
Maybe it helps someone...
Amidala

I love you. 

2 days with a Zebra TLP 2844 and Ubuntu 10.04 triying generic-printer-driver and 1000 of combinations. ¡Finally with this ppd file it is printing!
Very, very thanks.

Best regards from Spain.

---

### Post by appostroff on 2010-11-29
Me too ! I have TLP 2844-Z and with this ppd file works fine.

---

### Post by clone2046 on 2011-02-03
just to further the information on this post... the zebraep2.ppd cups file worked for my LP2844
:p



[^^]@88:~$ cat /etc/issue
Ubuntu 10.10 \n \l
GNOME 2.32.0

---

### Post by pagomez1983 on 2011-05-19
Gracias funciono perfecto! :D

---

