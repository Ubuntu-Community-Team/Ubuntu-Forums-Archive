---
title: "Disable Keyboard Detection on Boot"
date: 2010-11-13
forum: Hardware
---

### Post by CoreyJKelly on 2010-11-13
I realize that this isn't an Ubuntu issue, but I thought I'd ask the community anyway. I'm trying to get a server up and running on an old Compaq EVO D510, and there is no option in the BIOS to disable keyboard detection on boot. I've checked every section of the BIOS thoroughly. I've also searched for any mention of this in Compaq's documentation, but can't find anything.
Anybody familiar with this Mobo?

---

### Post by CoreyJKelly on 2010-11-14
Solved this. For any others who might come across this post, give this a read:

[http://www.edlug.ed.ac.uk/archive/May2004/msg00486.html](http://www.edlug.ed.ac.uk/archive/May2004/msg00486.html)

It seems that certain version of the Compaq BIOS don't have a setting to disable this, so they've provided a workaround (NO_F1) which still displays the "No Keyboard" warning, but doesn't halt the boot process. Installing the workaround involves either a bootable floppy or USB key, but is quite simple. The only downside is that any sort of reconfiguration in the BIOS can undo the fix, so it might have to be re-applied occasionally.

---

### Post by Bob1nz on 2011-03-07
Hi i know you marked this as solved but i think i might have found another solution. 
There is a mode called Network Server Mode which allows keyboard-less operation (no keyboard check on boot)


1) Press F10 when prompted at startup to enter BIOS setup.
2) Go to the Security menu and select Power-On Password.
3) Assign a password and press F10.
4) In the Security menu, a new option should appear called Password Options.
5) Open this item and set Network Server Mode to Enabled.
6) Save the changes and exit.

the steps are taken from [http://www.marlwifi.org.nz/projects/deskpro-keyboard](http://www.marlwifi.org.nz/projects/deskpro-keyboard)

it may or may not work for you as the guy has noted some older deskpros bios's dont support the Network Server Mode but i have just done this on my compaq evo d510 CMT and it has worked so just thought i would share :)

---

