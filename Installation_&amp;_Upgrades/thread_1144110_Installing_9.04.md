---
title: "Installing 9.04"
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by GreenBowlPacker_3 on 2009-04-30
I've downloaded Ubuntu 9.04 and made the start up cd.  When I boot my computer from the cd I can get as far as the menu that asks if I want to try, install, etc...  But no matter what I pick I get a long list of I/O errors that doesn't end.  I'm using a Dell Inspiron 1501 laptop with dual boot Windows XP and Ubuntu 8.04.  I even tried uninstalling the 8.04 version and formated the HD I wanted to put 9.04 on and it still didn't work.  Any ideas?

---

### Post by kestrel1 on 2009-04-30
I would suggest that you re-burn your CD. It sounds like it could be corrupt. Try burning at a lower speed.

---

### Post by GreenBowlPacker_3 on 2009-04-30
That worked, thanks!

---

### Post by kestrel1 on 2009-04-30
Great stuff. Glad to be of help.

---

### Post by giosimar on 2009-07-04
O__o
I have your same problem, but starting from a 7.10 the cd works.

Hoe did you solve? just recording another disk?

did you give the option pci=nomsi at beginning?

---

### Post by kestrel1 on 2009-07-04
> **giosimar said:**
> O__o
I have your same problem, but starting from a 7.10 the cd works.

Hoe did you solve? just recording another disk?

did you give the option pci=nomsi at beginning?
Have you tried burning the iso to a CD at a lower speed. Use the lowest speed possible.

---

### Post by giosimar on 2009-07-04
actually I tried before with a 9.04, after with 8.04 and at the end with a 7.10 on the same rewritable cd...

the last worked.

the problem is that a beginning every version works, and open the menu dialog.
but when i choose to start live cd, the 9.04/8.04 is unable to start (and there aren't I/O errors), whereas 7.10 starts.

this happens if i give at beginning the option pci=nomsi
without this initial option also 7.10 fails, giving the same error.

---

### Post by earthpigg on 2009-07-04
i can personally attest that burning at the slowest speed possible increases the chances of a good burn by quite a bit.

alternatively, you can make a usb startup disk and bypass the possibility of your cd burner being damaged:

system -> administration -> USB startup disk creator

("My cd burner works fine! i burn music on it all the time!" ... if a single 1 or 0 is on the wrong place in a music cd, you wont notice... an operating system, different story :) )

---

### Post by Ra-Hoor-Khuit on 2009-07-04
> **giosimar said:**
> ... 9.04, after with 8.04 and at the end with a 7.10 on the same rewritable cd...
Ditch the CD-RW for a standard CD-R.  Rewritables are no good for this sort of operation. 

Use a name-brand CD-R and burn it slow, no faster than 8x.

---

### Post by giosimar on 2009-07-04
yeah, I know :)
but, I check the written files every time, and I didn't notice any I/O error during installation (and, moreover, if you have problems with rw cd, usually you have them at the end, not at beginning!).
and the error I noticed with 9.04 and 8.04 is the same I noticed with 7.10 when I don't put the option pci=nomsi.

---

### Post by kestrel1 on 2009-07-05
> **giosimar said:**
> yeah, I know :)
but, I check the written files every time, and I didn't notice any I/O error during installation (and, moreover, if you have problems with rw cd, usually you have them at the end, not at beginning!).
and the error I noticed with 9.04 and 8.04 is the same I noticed with 7.10 when I don't put the option pci=nomsi.
It is possibly to do with your hardware & not the CD.

---

