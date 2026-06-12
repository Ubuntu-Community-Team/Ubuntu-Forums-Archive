---
title: "USB storage devices won't automount"
date: 2011-08-06
forum: Hardware
---

### Post by andrewkirk on 2011-08-06
When I plug in a USB stick or USB external HDD, the following happens:

1- the device doesn't automount and appear as a desktop icon as it is supposed to
2- the device doesn't appear in the main menu 'places' list
3- the device appears in the 'Places' list of a Nautilus browser window, but doesn't mount. If I try to mount it from there by double-clicking or right-clicking , nothing happens.
4- If I open a Nautilus window with root privileges, to try to mount it from there, the device doesn't appear in the Places side panel
5- If I open a terminal, find out the /dev/ location of the device and then mount from the command line as root, it works

Needless to say, option 5 is very time-wasting and annoying. I have tried the gconf-editor approach in

[https://help.ubuntu.com/community/Mount/USB#User%20Privileges](https://help.ubuntu.com/community/Mount/USB#User%20Privileges)

but that didn't help.

I have also gone into System/Administration/Users and Groups/. In User Privileges for my logon id, it has the 'Access external storage devices automatically' box ticked.

Can anybody please advise me how to get automounting working properly?

Thanks very much

Lucid Lynx 10.04

10.04 Lucid Lynx

---

