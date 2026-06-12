---
title: "Keyboard unsupported, possible workaround?"
date: 2011-06-04
forum: Hardware
---

### Post by Peckles on 2011-06-04
Hey guys,

Ive just recently installed linux and found that my Gigabyte Aivia K8100 gaming keyboard is not supported.  Link here -> [K8100]("http://www.gigabyte.com/products/product-page.aspx?pid=3588#kf").

It seems to be a linux kernel issue as I have found a few bug reports online that have been submitted. Here -> [Bug Report]("https://bugzilla.kernel.org/show_bug.cgi?id=31342").

All of the lights work and the one key that does work is the backspace key (this seems strange to me).  

Do I have any options here?  Is there anyway I could somehow see what keys its sending when I press one and possibly remap it myself?  What are the odds that the linux kernel will be updated to support this and in what time period?

Other thoughts and opinions welcome!

Thanks,

Peckles

(BTW, 5 days into linux and Ive absolutely fallen in love.  Why does anyone still use windows?)

---

### Post by papibe on 2011-06-04
Try to see if xev registers an event while pressing the backspace key:
```
$ xev
```
Regards.

---

### Post by Peckles on 2011-06-04
Thanks for the command, very useful.  Thats going in the memory bank...

The backspace key registers a backspace.  Also all of the multimedia keys and special 5 mappable keys work as well. (very strange...)

All other keys do not register an event at all.

Could it be possible I have the wrong driver loaded?

Peckles

---

### Post by papibe on 2011-06-04
First I would try to play a little with other keyboard layouts, and check if you can get a better mapping. Check this [tutorial]("http://www.wikihow.com/Change-Keyboard-Layout-in-Ubuntu").

Another solution maybe to map those events into extra keys. This would be a [start ]("https://wiki.archlinux.org/index.php/Extra_Keyboard_Keys") for that (I haven't tried it myself).

Regards.

---

