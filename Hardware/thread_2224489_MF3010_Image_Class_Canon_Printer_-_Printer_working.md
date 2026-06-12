---
title: "MF3010 Image Class Canon Printer - Printer working but not the scanner"
date: 2014-05-16
forum: Hardware
---

### Post by rvgmec2 on 2014-05-16
I could install the driver for printer. It is working fine. But the scanner is not working. Where can I get the driver for scanner? The MF3010 is a printer and scanner combo.

---

### Post by pdc on 2014-05-16
SANE (scanning access now easy) is the open-source place for scanning information;

if one looks in the Canon section [http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)          .........and looks under imageclass, they seem to say the MF series are all supported by the backend pixma [http://home.arcor.de/wittawat/pixma/](http://home.arcor.de/wittawat/pixma/) and the manual page is sane-pixma [http://www.sane-project.org/man/sane-pixma.5.html](http://www.sane-project.org/man/sane-pixma.5.html)

..not much comfort for you when they say that

Can you tell us what 

> [COLOR="#FF0000"]sane-find-scanner[/COLOR] and > [COLOR="#FF0000"]scanimage -L[/COLOR] give if pasted into a terminal please? If you type terminal into the Dash search function on your desktop, it should find a terminal for you: 

If you get a not seen reply, if you add sudo in front of each command, and run them again......you will be asked for your sudo password.....

________________________________________________

also could you type > [COLOR="#FF0000"]lsusb[/COLOR] into the terminal; (hit the enter key after each insert); and copy and paste back the ID of the device: eg [COLOR="#0000FF"]04a9:2660[/COLOR]

__________________________________________-

I am thinking we might have to add an entry to the file 40-libsane.rules to tell it about your device:

eg for the very similar MF3110 it says

> # Canon imageCLASS MF3110
ATTRS{idVendor}=="04a9", ATTRS{idProduct}=="2660", ENV{libsane_matched}="yes"

so we would do 

> gksudo gedit /lib/udev/rulles.d/40-libsane.rules and that hopefully would open the file, and one would paste in an entry telling it the idProduct number for your device

---

