---
title: "epson-printer-utility can no longer find printer under Ubuntu 16.04 LTS."
date: 2021-07-29
forum: Hardware
---

### Post by John Nagle on 2021-07-29
The program "epson-printer-utility", which allows checking ink and head cleaning, worked on my Ubuntu 16.04 LTS until two months ago. Now, after only routine Ubuntu-ordered Software Updater updaes, it can't find the printer.

The printer (Epson ET-2650, USB-connected) is found by the Ubuntu printing system, shows up in the Printers list, and can print. But "epson-printer-utility" can't find it.

Here's what it looks like. This is with the latest version of epson-printer-utility, as of July 2021.

So I can't do a head cleaning and my printer is producing very bad output.

[IMG]https://i.ibb.co/dmZZPRk/printerutilitynofind.png[/IMG]

---

### Post by brian_p on 2021-07-29
Ubuntu 16.04 LTS reached the end of its five-year LTS window
on April 30th 2021 and is no longer supported by its vendor.

Do you really expect users to support it and some non-Ubuntu package instead?

---

### Post by John Nagle on 2021-07-30
> **brian_p said:**
> Ubuntu 16.04 LTS reached the end of its five-year LTS window
on April 30th 2021 and is no longer supported by its vendor.

Do you really expect users to support it and some non-Ubuntu package instead?

Oh, was *that* bad advice. Cost me 4 hours just to get to this next fail.

I upgraded the whole system to Ubuntu 20.04. Which means dealing with a host of other problems.

For this problem, it made things worse.

epson-printer-utility: error while loading shared libraries: libQtCore.so.4: cannot open shared object file: No such file or directory

This causes much grief, because Ubuntu 20.04 does not, by intention, support Qt4. Installing Qt4 and Qt5 both will mess up the package system.

Fortunately, someone has already worked through the mess you have to go through to fix this for this program only.
Unfortunately, the suggested workaround links to dead URLs.

[https://askubuntu.com/questions/1233178/epson-printer-utility-error-loading-shared-libraries](https://askubuntu.com/questions/1233178/epson-printer-utility-error-loading-shared-libraries)

This is going to take a while.

---

### Post by Autodave on 2021-07-30
Did you do a clean install or upgrade what you already had?  With what you had being so old, a new, clean install is what is really called for AFTER you backup everything that you might need!

---

### Post by brian_p on 2021-07-31
The manual recommends **visually** checking ink levels. Head cleaning may be done from the control panel. Is this utility really needed?

---

