---
title: "[SOLVED] Hardware list"
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by nikRbokR on 2008-03-23
Is there a command for the terminal that will tell me what hardware I have?  Is there anyway for me to do this (even if it does not require terminal)?  I especially want to know what graphics card my laptop has (I cannot enable desktop effects, and I am trying to figure out if its a problem w/ the graphics card).

Thanks

---

### Post by Sam Lars on 2008-03-23
Two commands...
```
lspci
```
That will list all of your PCI devices, including your graphics card.
```
lshw
```
That will list all hardware, PCI as well as some other stuff.

---

### Post by nick_h on 2008-03-23
There are two terminal commands I can think of:  *lshw* and *hwinfo.*

For *hwinfo* you will need to install the package *hwinfo.*

To check a graphics card then using *lspci* is probably the easiest way.

From the GUI you can use System->Preferences->Hardware Information.

---

### Post by Cannaregio on 2008-04-06
Two commands I often use and recommend:

```
sudo lshw -html >MyGNULinuxBox.html
```

and then browse your own harddisk for [COLOR="Blue"]MyGNULinuxBox.html[/COLOR]

and

```
sudo hwinfo | less
```

plenty of info without funny characters.

---

