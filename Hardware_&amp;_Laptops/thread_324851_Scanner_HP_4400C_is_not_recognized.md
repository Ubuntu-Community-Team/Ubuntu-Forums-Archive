---
title: "Scanner HP 4400C is not recognized"
date: 2006-12-24
forum: Hardware &amp; Laptops
---

### Post by YigalB on 2006-12-24
My Ubuntu doesn't recognize HP scanner 4400C.
How can I install it? 
I also wonder why I don't see any report from the OS when I plug the USB plug in, such as "new hardware detected" similiar to what I see from the "other OS".

Thanks

---

### Post by YigalB on 2006-12-27
No one can help with installation of one of the most commom scanners in the world? Does it mean Ubuntu has poor support of hardware?

---

### Post by vergelking on 2008-02-04
anyone help me in configuring my hp scanjet 4400c.  please!

---

### Post by mathnuked on 2008-05-28
Hello,

I'll tell you what I know. I still do not have the hp scanjet 4400c working yet, but I do have xsane recognizing it. Just load libsane-extras and hpoj packages.

I still get errors, but it is a start.

---

### Post by Zimmer on 2008-05-28
SANE page shows it as 'untested'  in the latest development version. It is not even listed in the stable version ...
[http://www.sane-project.org/sane-supported-devices.html](http://www.sane-project.org/sane-supported-devices.html)

there is an external backend for it though, 
> Backend: hp_rts88xx

Link(s): [http://hp44x0backend.sourceforge.net](http://hp44x0backend.sourceforge.net)
Comment: This backend is not included in the sane-backends distribution at the request of its author. There is a lot of different hardware worldwide on the market and the backend can't cover all this different versions.
Manufacturer 	Model 	Interface 	USB id 	Status 	Comment
Hewlett-Packard 	HP4400C 	USB 	0x03f0/0x0705 	Basic 	grayscale 300DPI only
HP4470C 	USB 	0x03f0/0x0805 	Basic 	grayscale 300DPI only, XPA/bed mode
Oh, and the hplip package has superceded hpoj....
> HPOJ is not maintained anymore. It's recommended to use the hpaio (hplip) backend instead of hpoj.

---

### Post by mathnuked on 2008-05-28
Thank you for the correction. Alway learning.

---

