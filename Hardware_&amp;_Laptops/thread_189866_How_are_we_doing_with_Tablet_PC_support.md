---
title: "How are we doing with Tablet PC support?"
date: 2006-06-05
forum: Hardware &amp; Laptops
---

### Post by starkruzr on 2006-06-05
Last year I posted regarding how tablet support was doing in Breezy, and the answer was "meh."

The answer appears to still be "meh."

For some reason, when it detects that you have a tablet, it uses the wrong device name.  In xorg.conf, it thinks the device name is /dev/wacom.  It isn't.  It's /dev/input/wacom.  You have to change this manually yourself, just like you did in Breezy.  That seems a little silly to me, but whatever; moving on...

Does anyone know of ANY applications that have:

Pen-button support
Eraser support

Other than the GIMP?  Gournal is more or less worthless in this regard and it can't do anything with PDFs either.

I have a Toshiba Portege M205 Tablet PC and am pretty much stuck with Windows until there is something available that vaguely resembles Windows Journal.  ](*,)  :(

---

