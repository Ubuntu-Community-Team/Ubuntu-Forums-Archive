---
title: "[SOLVED] Buffer I/O error on device fd0, logical"
date: 2008-07-27
forum: General Help
---

### Post by jeffmills on 2008-07-27
Hi all,

I'm currently running Ubuntu 8.04.1 from a USB-drive (Sandisk U3 Cruzer Contour 4GB, removed the Launchpad-software)

I used the method for a persistant install on the following website: [http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-tutorial/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-tutorial/)

However, during startup... I see multiple of the following messages.

"Buffer I/O error on device fd0, logical block 0"

These seem to make the booting-process _alot_ slower and I would like to know if I can solve this problem somehow.

---

### Post by ryanhaigh on 2008-07-27
You could [try this]("http://fedoraproject.org/wiki/KernelCommonProblems#Boot_pauses_probing_floppy_device") and if it works edit your menu.list to permanently add that parameter for all kernel lines.

---

### Post by jeffmills on 2008-07-28
> **ryanhaigh said:**
> You could [try this]("http://fedoraproject.org/wiki/KernelCommonProblems#Boot_pauses_probing_floppy_device") and if it works edit your menu.list to permanently add that parameter for all kernel lines.

Thank you.

I tried the same USB boot on a PC with floppy drive and indeed the error did not appear. After realising what the explanation was, it seemed all so logical to me: the 'fd' stands for **f**loppy **d**evice! I should have been able to find this with some use of Google. Thanks for making my like a bit easier though.

---

### Post by mcbowler on 2013-02-28
Or you can turn off the floppy option in BIOS

---

