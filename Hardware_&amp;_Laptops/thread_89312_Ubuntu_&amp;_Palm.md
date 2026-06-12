---
title: "Ubuntu &amp; Palm"
date: 2005-11-12
forum: Hardware &amp; Laptops
---

### Post by joplass on 2005-11-12
I am trying to synchronize my Palm with my Notebook.  I was just wondering if I need anything else because I tried using the palm wizard under preference but the Palm does not send data.  I get something like communication failed.
I will appreciate some help.

---

### Post by matthew on 2005-11-12
This might help you.

[http://ubuntuforums.org/showthread.php?p=485764](http://ubuntuforums.org/showthread.php?p=485764)

---

### Post by scubajeff on 2005-11-12
The link /dev/pilot in Breezy is broken. Try using /dev/ttyUSB0 or /dev/ttyUSB1. You would see these two files in /dev directory only after you press your Palm's Hotsync button, because they are created dynamically by "udev". Just for your information, my Treo 650 use /dev/ttyUSB1.

---

### Post by joplass on 2005-11-12
Thanks guys; too bad it seems Thunderbird does not support Palm sync.  My contacts are seating on Evolution while my main email client is Thunderbird:rolleyes: .

---

