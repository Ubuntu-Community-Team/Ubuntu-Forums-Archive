---
title: "where should I put this?"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by corpsehacker on 2009-04-06
I was installing Americas Army onto my computer with wine and ran into a problem.As it is installing it tries to put things into C:/Program Files/Americas Army. What should I do? I figure I have a few options.

1. I could try to create that file and put it there.

2. I could redirect it (although I tried redirecting it and it had more problems) so I will need some help with that.

3. I could do whatever else you guys suggest

So throw some options at me and Ill try them. Thanks a lot.;)

---

### Post by damis648 on 2009-04-06
C:\ is somewhat of a virtual drive in WINE. It is located at ~/.wine/drive_c :popcorn: It's not /, nor an actual windows partition on your computer. :popcorn:

---

### Post by upchucky on 2009-04-06
wine creates a C:\ drive in your home directory, but you do not have to install to it. if your home directory does not have lots of room then you can install to a drive of your choice, however you then need to make sure the startup icon for the program knows where you installed to, right click the icon, select properties and see where it launches from and where the start target is set to. 

for example, my guild wars is on drive F, and wine is in /home, so my start icon properties --> command: are

env WINEPREFIX="/home/electric/.wine" wine "F:\Guild Wars\Gw.exe"

---

### Post by oldos2er on 2009-04-06
Why not get the Linux version?

---

### Post by upchucky on 2009-04-06
> **oldos2er said:**
> Why not get the Linux version?

linux version of army or guild wars?

---

### Post by oldos2er on 2009-04-06
> **upchucky said:**
> linux version of army or guild wars?

 America's Army.

---

### Post by corpsehacker on 2009-04-08
OK, I downloaded the Linux version and pretty much got it installed when a message pops up saying " there is no tech support for this e-mail". This is extremely strange because I never gave it my email and this message just pops up out of nowhere in the terminal. I am so confused!!!

---

