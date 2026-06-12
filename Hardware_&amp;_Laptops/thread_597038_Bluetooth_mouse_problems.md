---
title: "Bluetooth mouse problems"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by stardustdk on 2007-10-30
Hey.

I am running Ubuntu Gutsy I386 on a LG Laptop with a USB Bluetooth dongle.
My Logitech Mobile Pro headset is working perfectly with that dongle, therefore i decided to get a Bluetooth mouse. That is a Logitech V470.

Maybe af bad idea? I didn't get it working, even when the laptop saw the mouse.

Directly translated from Danish, i got this error message:
----

**[SIZE="4"]"OBEX://[00:07:61:96:71:5d]" is not a valid place.[/SIZE]**

Check spelling and try again
---

Which i did, and rebooted just in case, and that didn't help either :confused:

What can i do?

Best regards

Stardustdk

---

### Post by goomior on 2007-10-30
Please install gnome-vfs-obexftp package
```
sudo apitutde install gnome-vfs-obexftp
```
or
```
sudo apt-get install gnome-vfs-obexftp
```
or whatever.

---

### Post by stardustdk on 2007-10-30
Thanx that solved part of the problem, now the error message is:
----
**Could not show "obex://[xxxxxxxxx] **
Check if the service is available.

---

Downloaded several obex-related stuff, it didn't help :(

Again: I am confused, because the headset works fine.

Best regards

Stardustdk

---

### Post by KevNice on 2007-10-30
> **stardustdk said:**
> Thanx that solved part of the problem, now the error message is:
----
**Could not show "obex://[xxxxxxxxx] **
Check if the service is available.

---

Downloaded several obex-related stuff, it didn't help :(

Again: I am confused, because the headset works fine.

Best regards

Stardustdk

bump, because Ive got the same problem

---

