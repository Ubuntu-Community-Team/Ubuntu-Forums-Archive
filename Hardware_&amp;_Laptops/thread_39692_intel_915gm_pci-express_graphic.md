---
title: "intel 915gm pci-express graphic"
date: 2005-06-06
forum: Hardware &amp; Laptops
---

### Post by ruben_b on 2005-06-06
hi

i own a toshiba satellite m40x 112 with an intel 915gm graphicscard with 128mb shared memory.

the card works and displays a 1280x800 resolution as it should, but i only get 800fps when testing with glxgears.
my old geforce 420 go allready made 1500fps.

is the intel 915gm really that slow or is there someting i can do to speed up the 3d acceleration?

---

### Post by ruben_b on 2005-06-29
any hints!?

---

### Post by Burkey on 2005-06-29
[QUOTE=ruben_b]hi

i own a toshiba satellite m40x 112 with an intel 915gm graphicscard with 128mb shared memory.

the card works and displays a 1280x800 resolution as it should, but i only get 800fps when testing with glxgears.
my old geforce 420 go allready made 1500fps.

is the intel 915gm really that slow or is there someting i can do to speed up the 3d acceleration?[/QUOTE]
 I have a DELL D410 with the 915 in it, with the default drivers and at 1024x768 Gnome session I am pulling around 950-1000fps.

Would love to get some more out of it too.

---

### Post by luca_linux on 2005-06-29
Could you post your xorg.conf?

---

### Post by jamaas on 2005-07-12
Hi Burkey,

I just installed 5.04 on a d410 and all I get is a blank black screen, get the drums noise when I use correct username and password so it is doing something, just can't see it.  Any suggestions?

Thanks

Jim

[QUOTE=Burkey]I have a DELL D410 with the 915 in it, with the default drivers and at 1024x768 Gnome session I am pulling around 950-1000fps.

Would love to get some more out of it too.[/QUOTE]

---

### Post by varunus on 2005-07-12
jaamaas,

Can you post your /etc/X11/xorg.conf?

Anyone who's getting low framerates in glxgears, can you post the output of "glxinfo"?

The i915 isn't that great of a card, its integrated and uses system RAM (I think) so you're not going to get that much out of it...

---

### Post by jamaas on 2005-07-12
I wish I could, so far am not connect to network, and can not even copy it to a disk or because can not boot.  I tried copying to cd but no luck.  Can you send me yours such that I might be able to compare?  Do you have a d410?

Thanks

Jim

[QUOTE=varunus]jaamaas,

Can you post your /etc/X11/xorg.conf?

Anyone who's getting low framerates in glxgears, can you post the output of "glxinfo"?

The i915 isn't that great of a card, its integrated and uses system RAM (I think) so you're not going to get that much out of it...[/QUOTE]

---

### Post by varunus on 2005-07-12
Jim,

I don't have a d410, but I do have a laptop which uses the i855GM architecture (which uses the same driver called "i810" by X.org and "i915" by the kernel).  One thing to try, boot into recovery mode in Ubuntu, and type:
```
sudo nano /etc/X11/xorg.conf
``` 

Scroll down to the Device section and change the driver line so it looks like this:

```
Driver "vesa"
``` 

Save the file by typing CTRL-O, then type CTRL-X t exit.  Then reboot by typing "reboot".  Does this let you get into a graphical environment?  It should, but you will not have any hardware acceleration with the VESA driver.  Once you're in a GUI though, we can figure out your problems better.

EDIT:  Also, what network card do you have?  Maybe we can set that up from the console itself.

Attached is my /etc/X11/xorg.conf.

---

