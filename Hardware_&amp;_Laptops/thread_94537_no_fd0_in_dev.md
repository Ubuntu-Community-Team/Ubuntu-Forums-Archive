---
title: "no fd0 in /dev"
date: 2005-11-24
forum: Hardware &amp; Laptops
---

### Post by bonjun on 2005-11-24
i can't mount my floppy drive, it gives a mount error:

> mount: special device /dev/fd0 does not exist

when i check /dev there is no fd0 device in the directory

i also tried mounting at root (mount & pmount), i got the same error 

it seems that it has not been loaded during installation, it's been working nicely in hoary, i upgraded to breezy, fresh install,,,,

how can i add fd0 device,,

TIA

---

### Post by magomago on 2005-11-24
[QUOTE=bonjun]i can't mount my floppy drive, it gives a mount error:



when i check /dev there is no fd0 device in the directory

i also tried mounting at root (mount & pmount), i got the same error 

it seems that it has not been loaded during installation, it's been working nicely in hoary, i upgraded to breezy, fresh install,,,,

how can i add fd0 device,,

TIA[/QUOTE]


same here.  if anyone knows why i'd appreciate it.  currently on breezy here

---

### Post by bonjun on 2005-11-28
bump...

---

### Post by bonjun on 2005-11-30
*sigh* no help yet,,,

---

### Post by bonjun on 2005-12-08
when i try modprobe, the floppy is detected and mountable, but when i restart the pc & mount floppy, i get the same error... help, anyone

---

### Post by bonjun on 2005-12-08
[QUOTE=magomago]same here.  if anyone knows why i'd appreciate it.  currently on breezy here[/QUOTE]
sir, is your problem solve?

---

### Post by fredlangva on 2005-12-14
the floppy module is not being loaded. If you open a terminal session and type lsmod | grep floppy   you will probably not get a result. This can be fixed by editing the "modules" file in the /etc directory and adding the line at the end   floppy

reboot and you are golden.

Now for the $10,000 question. Why did the floppy module get removed from the modules file when upgrading from Hoary to Breezy?

---

### Post by bonjun on 2006-01-21
[QUOTE=fredlangva]the floppy module is not being loaded. If you open a terminal session and type lsmod | grep floppy   you will probably not get a result. This can be fixed by editing the "modules" file in the /etc directory and adding the line at the end   floppy

reboot and you are golden.

Now for the $10,000 question. Why did the floppy module get removed from the modules file when upgrading from Hoary to Breezy?[/QUOTE]

thanks a lot sir, it works now...
sorry for the late reply

---

