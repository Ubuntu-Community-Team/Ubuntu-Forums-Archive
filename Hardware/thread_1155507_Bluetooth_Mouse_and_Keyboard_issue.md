---
title: "Bluetooth Mouse and Keyboard issue"
date: 2009-05-10
forum: Hardware
---

### Post by BGG001 on 2009-05-10
I've been trying to set up my Microsoft Wireless Entertainment Keyboard 7000 and Microsoft Wireless Laser Mouse 8000 for the past hour and have only succeeded in getting the keyboard working (howeer, now it no longer works). When I got the keyboard working at first, it was automatically accepted by the bluetooth manager, but the mouse is rejected. I've tried I don't know how many things I've found here and elsewhere, none of which have worked. Any help?

(MOST of the things I tried ended with:

user@user-desktop:~$ sudo hidd --search
sudo: hidd: command not found

)

Ubuntu 9.04

---

### Post by BGG001 on 2009-05-10
Fixed it.

Oddest fix ever, had to go back into Windows 7, reconnect both mouse and keyboard using their bluetooth handler, came back into Ubuntu, mouse instantly worked, had to delete keyboard from list of known devices and reconnect it.

Hopefully that helps someone with similar problems and a dual-boot set up.

---

