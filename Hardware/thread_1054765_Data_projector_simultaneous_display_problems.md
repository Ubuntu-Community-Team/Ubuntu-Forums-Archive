---
title: "Data projector simultaneous display problems"
date: 2009-01-30
forum: Hardware
---

### Post by geoffrussell on 2009-01-30
I have a Dell 1600 Inspiron with 8.04 installed, pretty well
uptodate. I can connect a Data Projector and Fn/F8 throws the
display on the Data Project and blanks the LCD screen. Fn/F8
again renders both screens black. 

At some point (a few kernels/updates ago), everything worked 
fine. The second Fn/F8 would give a simultaneous display on both projector and LCD.

During some upgrade, this function broke, but I don't know 
when.

---

### Post by keithpeter on 2009-02-05
Hello All

"me too"

I've just bought an Asus 1000 webbook with Ubuntu 8.10, stock kernel,  installed. External LCD monitor recognised ok and controllable from the system/preferences/screen resolution dialogue

Data projector not recognised at all, nothing, nada under Ubuntu. Does echo PC screen during boot up, stops once the Ubuntu desktop appears.

Any ideas?

---

### Post by geoffrussell on 2009-02-08
First, a correction. My Inspiron is a 6400, must have been some
brain fade on the first post.

Second. With kernel 2.6.20-16-generic, the simultaneous display
works. Fn-F8 toggles between the following screen displays: LDC, 
DataProjector, Both, Neither. i.e, its not perfect, but usable.

Similarly with kernel 2.6.22-14-generic. Usable but not perfect.

All kernels after this are broken in the sense that there is
no simultaneous DataProjector/LCD display

---

