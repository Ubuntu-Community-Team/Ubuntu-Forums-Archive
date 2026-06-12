---
title: "Brother HL-1670N Printer not printing"
date: 2012-05-21
forum: Hardware
---

### Post by Goldpin on 2012-05-21
I've just upgraded to Precise Pangolin 64bit and have one major glitch.  My Brother lazer printer will not print a newly created document. :confused: It works ok with ones I created before the upgrade, but when I try to print a new document, the printer spits out a blank page and then a page with the following:

ERROR:
invalidfont
OFFENDING COMMAND:
Type 1BuildGlyph
STACK:
63
-mark-
-mark-
-mark-

Also, I tried installing a Brother driver using GEDBI, but I think I screwed it up!:oops:  Now I need to know how to remove it (the program tells me it didn't install, but it shows up in Synaptic marked in red).

The file is:  hl1670nlpr:i386

Now synaptic says it didn't install and can't find the archive.  I can't get into synaptic or the software centre.  They both close down on me.

Does anyone have any ideas??? Thanks in advance

---

### Post by plucky on 2012-05-22
The driver for your printer is packaged in **Synaptic Package Manager**

Open Synaptic and search for **HL-1670N** and install both of the programs that it finds.

If the broken package stops the installation,open a terminal and run ```
sudo apt-get remove <name of package>
``` to un-install the broken package.Use the name that shows up in synaptic.

Good Luck

---

### Post by Goldpin on 2012-05-23
Unfortunately, I didn't see Plucky's reply until after I'd mad the change.  I simply reinstalled Oneric.  I'm afraid there just seemed to be one problem after another.  When I originally tried installing something, The software centre kept telling me to check my internet connectionn (which was working).  At least with Oneric everything works.

Thanks for the input Plucky, sorry I didn't see it in time.

---

