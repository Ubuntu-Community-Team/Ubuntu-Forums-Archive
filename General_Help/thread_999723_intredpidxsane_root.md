---
title: "intredpid/xsane root?"
date: 2008-12-02
forum: General Help
---

### Post by Flynn555 on 2008-12-02
hmm ok i upgraded to intrepid and now xsane will only run in root.  any ideas?

---

### Post by feanor512 on 2008-12-04
I have had the same [problem]("http://ubuntuforums.org/showthread.php?t=733374") starting with 8.04.

What worked for me:

Plug in your scanner. Type

```
dmesg | grep usb
```You'll see something like

```
usb m-2: new full speed USB device using uhci_hcd and address n
```where m and n are integers. Type

```
sudo chgrp scanner /dev/bus/usb/00m/00n
```If it gives you an error when you close it, you'll need to take ownership of /home/yourusername/.sane/

Hope that helps.

---

### Post by dwpbike on 2010-07-16
"if it gives you an error when you close it, you'll need to take ownership of /home/yourusername/.sane/"


tanks, that was the tip i needed to get the rest of the way.  i'm doing 10.4 and having to do xsane as root.  changing the permissions was all i needed to do to get my epson nx400 back to scanning.



[email]david@amd:~/.sane[/email]/xsane$ sudo chmod a+rw bat*
[email]david@amd:~/.sane[/email]/xsane$ sudo chmod a+rw Eps*
[email]david@amd:~/.sane[/email]/xsane$ sudo chmod a+rw xsane.mdf
[email]david@amd:~/.sane[/email]/xsane$

---

