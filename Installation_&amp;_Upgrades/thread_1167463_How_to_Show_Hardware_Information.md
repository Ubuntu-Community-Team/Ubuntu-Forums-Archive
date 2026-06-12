---
title: "How to: Show Hardware Information?"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by NukeouT on 2009-05-22
hey all

I'm new to Ubuntu. Right now im trying to figure out how to get the GUI or the Terminal to show me hardware data for my machine without having to take it apart.

I need to see Processor info. (beyond "PIII Coppermine", to find out how many Hz it is.)

Also ATM the Motherboard name and RAM sticks. (... so I can see if I can upgrade to 1g sticks).

(so far I've been only able to find out information for what is in my PCI slots and System Monitor)

---

### Post by pytheas22 on 2009-05-22
You can install the utility 'hwinfo' by typing:
```

sudo apt-get install hwinfo
```

Then run it by typing:
```

hwinfo
```

If the output gets cut off by your terminal, you could pipe it into a text file with a command like:
```

hwinfo > output.txt
```

Then open the text file in a text editor for viewing:
```

gedit output.txt
```

I think hwinfo will tell you everything you need to know, although I'm not positive that there's any way to tell how much memory your motherboard supports without looking it up in BIOS or in documentation.

---

### Post by NukeouT on 2009-05-22
[FONT=monospace]:D thanks a bunch

found out my motherboard is: AUSUSTeK CUSI-FX motherboard
I have two 256 RAM sticks which I can upgrade to 2x512 100/133MHz !

processor is Pentium III Coppermine 996 MHz
I can upgrade it to a PIII Coppermine [/FONT]1133 MHz 100/133 MHz FSB !

im gonna go stop by a used comuter hardware store next time i can and pick those up.

---

### Post by NukeouT on 2009-05-29
found one pre-DDR 512 RAM stick. Upgraded to Jaunty 9.04. Broke Blender with Jaunty. :(

atleast OS upgreades look fun.

---

### Post by pytheas22 on 2009-05-29
> found one pre-DDR 512 RAM stick. Upgraded to Jaunty 9.04. Broke Blender with Jaunty

Upgrading over the Internet from earlier versions of Ubuntu to more recent doesn't always go smoothly.  You'd probably have better luck if you just did a clean reinstallation of Ubuntu 9.04.

Ubuntu 9.04 is also known to have graphics-performance issues, specifically with Intel and ATI video cards.  This could also be why Blender broke (I haven't used it in a while, but it requires 3D video acceleration, right?).

---

