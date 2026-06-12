---
title: "Can't install on HP Pavilion Ze4200 laptop"
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by teched58 on 2007-05-27
Ubuntu 7.04 won't install on my HP Pavilion ze4200 laptop.

1) I DID change the boot order, so the install DID proceed.

2) Problem seems to be graphics related. Install proceeds, but midway through I get the following error message: 
"There was an error starting the GNOME setting daemon...blah, blah, GNOME will try to restart the setting daemon next time you log in.

3) After some poking around, I re-ran the install using the command:  Boot:live vga=771.  (That's what the help file on the CD recommends for "laptop screens with VGA problems."   No luck. (The install seems to get past where it was before, but some very messed up type appears on the screen (what's probably supposed to be a logo, like it "thinks" its got the right graphics setting for the machine, but doesn't. Then the install just totally fritzes out, doesn't complete.)

Any suggestions? Thanks.

btw, the HP Pavilion ze4200 is Pentium 4-class (mobile Celeron 1.7 GHz), 192 MB RAM, i don't remember what the hard drive is.

---

### Post by kosminen on 2007-08-06
I had the same problem with my ze4220 using the "regular" installation CD.
However, the alternate desktop CD (with the text-based installer) worked just fine.

Now, if I only could get that ACPI-thing to work...

---

### Post by Achetar on 2007-12-05
It worked fine for me, maybe you need more RAM (I got ~650MB) or more HD space (is Windows still installed?) the minimum HD space is 3GB

---

### Post by stiopaa on 2008-05-30
I had the same problem with my ze4200 but i updated my bios from  hp website.  and now acpi work great ;;) hope you find this useful,  update bios

---

