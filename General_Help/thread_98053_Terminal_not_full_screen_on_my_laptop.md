---
title: "Terminal not full screen on my laptop?"
date: 2005-12-02
forum: General Help
---

### Post by yamagami on 2005-12-02
Heya all, 

I've got Breezy installed on my Toshiba Satellite, and I can't get the terminal to use the entire screen. I'm not talking about the gnome terminal, but the actual linux terminal (ALT+F2,F3 etc, or boot into a shell instead of gnome).

Also during bootup, the boot messages appear only as a box in the middle of my screen, instead of using the entire size... 

Any ideas on how to set it so that the terminal uses the full screen? 

Updated - added a lovely illustration to better describe my problem:

```

this is my monitor and the actual shell is dead in the centre.... 
what a waste of real estate
+-----------------------------+
|                             |
|                             |
|         +---------+         |
|         |bash>    |         |
|         |         |         |
|         |         |         |
|         +---------+         |
|                             |
|                             |
+-----------------------------+

```


Cheers,
Harel

---

### Post by mcduck on 2005-12-02
That is because TFT displays have a native resolution, and anything smaller/bigger than that has to be scaled or it will show as a small box (or doesn't fully fit in your screen).

But don't worry, you can set virtual terminal to use higher resolution. First thing you need to do is find out what is your displays resolution. Then you can add a line to Grubs config file to set Ubuntu to use that resolution, for 1024*768 you'd have to add 'vga=792' to kernel line in /boot/grub/menu.lst. The downside would be that you'll loose the nice Ubuntu logo at boot and get normal linux text boot instead.

---

### Post by 23meg on 2005-12-02
If that doesn't work, see if you have and option in your BIOS setup to adjust scaling in your display, and turn scaling on if you do.

---

### Post by jrib on 2005-12-02
Sometimes there is a Fn key that will stretch the screen instead of displaying  it like you described.  On my inspiron 8200 it is Fn + F7 (F7 is labeled "font").

---

### Post by yamagami on 2005-12-10
Brilliant! That works now. Thanks a lot.
Harel
:p

---

