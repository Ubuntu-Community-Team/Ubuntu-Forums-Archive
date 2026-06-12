---
title: "I got problems installing my video card [URGENT]"
date: 2009-06-24
forum: Hardware
---

### Post by Ahmedio on 2009-06-24
Ive tried everything, from blacklisting several repositories to checking what name my video card is
first of all i run this in terminal:  
lspci | grep VGA
Result:
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 
[Mobility FireGL 9000] (rev 01)
After that I ran: 
$ sudo apt-get remove --purge xorg-driver-fglrx

Result: i removed the fglrx driver

So i continues to follow the steps and entered: 
$ glxinfo |grep vendor  expecting to see ATI, instead i get this:
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

Now wth happened to the ATI driver plz help me. Source¬[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)
                                                                                             [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

