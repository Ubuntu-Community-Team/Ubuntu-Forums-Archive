---
title: "Screen Resolution jacked up."
date: 2008-08-12
forum: General Help
---

### Post by Raphial on 2008-08-12
Okie...got my Ubuntu working fine and dandy with everything (Except one upgrade that didnt install for some weird reason; it was the "linux-image" upgrade) but when I rrebooted my computer after installing the updates, my screen resolution went huge! It's like, zoomed in a lot...and I personally hate it.

My graphics card has worked perfectly with Ubuntu the last few times I used it on this computer...but this time I'm not so sure.

---

### Post by sam1948 on 2008-08-12
if by update u mean update from 7.10 to 8.04
then it had huppend to me to
_**anyway u can try this**_
start u'r system from the live cd that worked good for u
copy 
/etc/X11/xorg.conf
on some usb disk or some other disk in u'r computer
restart back to u'r regular (on hard drive) ubuntu
do the folowing
#> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkup
#> sudo cp <the place where u saved the xorg file> /etc/X11/xorg.conf
press simultaneously Ctrl+Alt+Backspace 
if it crashs u'r xserver start ubuntu in safe/text mode
and do this:
#> sudo cp /etc/X11/xorg.conf.bkup /etc/X11/xorg.conf
in order to restore th old bad-but-working resolution

if after installing ubuntu u needed to install some video card key-board or mouse drivers u may need to do that again 
it might be easier to do by looking in the backed up file
/etc/X11/xorg.conf.bkup 

good luck

---

### Post by overdrank on 2008-08-12
> **Raphial said:**
> Okie...got my Ubuntu working fine and dandy with everything (Except one upgrade that didnt install for some weird reason; it was the "linux-image" upgrade) but when I rrebooted my computer after installing the updates, my screen resolution went huge! It's like, zoomed in a lot...and I personally hate it.

My graphics card has worked perfectly with Ubuntu the last few times I used it on this computer...but this time I'm not so sure.

Hi and welcome, what is the model of the graphics card? If you are using hardy then you can try and boot into recovery mode and use the xfix option. If not then you can try and reconfigure you xorg.

---

### Post by Raphial on 2008-08-13
> **overdrank said:**
> Hi and welcome, what is the model of the graphics card? If you are using hardy then you can try and boot into recovery mode and use the xfix option. If not then you can try and reconfigure you xorg.

Recovery mode? Not sure how to do this...and I use NVidia.

---

### Post by overdrank on 2008-08-13
> **Raphial said:**
> Recovery mode? Not sure how to do this...and I use NVidia.

Hi and recovery mode is usually the second choice when boot from the grub. Then it will have the xfix option.

---

### Post by Raphial on 2008-08-13
But how do I do this? I've never seen any of this before. I used Wubi if that helps.

EDIT: I found it, and I used recovery mode, but it's still zoomed in a lot...gah.

---

