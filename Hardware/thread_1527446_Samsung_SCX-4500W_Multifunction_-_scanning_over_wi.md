---
title: "Samsung SCX-4500W Multifunction - scanning over wifi"
date: 2010-07-09
forum: Hardware
---

### Post by WFdeVlam on 2010-07-09
I'm trying to get an SCX-4500w scanner function to work on ubuntu 10.04  64bit via wifi network.

The printer works great, but the scanner is not recognized.

i have installed
samsungmfp-driver
samsungmfp-data

using[ tweedledee's procedure described here]("http://ubuntuforums.org/showthread.php?t=341621&page=48")

tested with and without
samsungmfp-scanner
splix
xsane

i'm a member of both the lp and the saned groups.

I feel i have to tell the scanner software where the printer/scanner is  on the network, but i can't figure out how i do that.

I am also a linux-newbie, so i probably missed something silly.

Can anyone point me in a direction? thanks!

---

### Post by WFdeVlam on 2010-07-12
update:

i tried sudo scanimage -L which gave me the following mystical stuff:
```

netdiscovery: relocation error: /lib32/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference
netdiscovery: relocation error: /lib32/libnss_files.so.2: symbol strcmp, version GLIBC_2.0 not defined in file libc.so.6 with link time reference

```

Does this mean anything to anyone?

---

### Post by tweedledee on 2010-07-13
> **WFdeVlam said:**
> Does this mean anything to anyone?

This looks like the same error arising for many people on 64-bit Ubuntu 10.04.  It turns up in many situations, you'll see a few examples if you scan back through the thread where you originally posted.  Not that doing so will help; I've yet to find a large block of time to try to track down the issue and see if there even is a fix, or if the drivers are just finally starting to break from lack of development by Samsung.  Check over in my thread in a month or so and hopefully there will be an update.

---

### Post by WFdeVlam on 2010-07-13
Thanks for replying and for all your work in this area. 

I'be sure to keep your thread bookmarked for any updates and would be happy to help test any possible fixes. Also I'll bug Samsung's costumer service some more, since the manual says it should work with sane, and the box claims linux support. 

Maybe they'll relent and set an intern on updating the drivers or something :)

---

### Post by irjozagata on 2010-08-06
[WFdeVlam]("http://ubuntuforums.org/member.php?u=1108995"): Few minutes ago I have solved the problem with SCX-4500W scanning over network with UBUNTU 10.04 - just via ethernet cable, but I believe in similar solution for Wifi.

Scanner was still not recognized by SANE, although I followed Samsung driver installation procedure and printer worked fine. I was also missing the place where scanner IP should be located.
I found SCX-4500W in /etc/sane.d/xerox_mfp.conf, where I replaced USB assignement with IP address of the scanner and it was recognized by SANE imediately!

/etc/sane.d/xerox_mfp.conf
....
# Samsung SCX-4500W
#usb 0x04e8 0x342b     #original USB definition put commented
IP 192.168.123.202       # added line with IP destination
....
Let me know, please, if it works with WiFi too.

---

### Post by tweedledee on 2010-08-12
> **irjozagata said:**
> [WFdeVlam]("http://ubuntuforums.org/member.php?u=1108995"): Few minutes ago I have solved the problem with SCX-4500W scanning over network with UBUNTU 10.04 - just via ethernet cable, but I believe in similar solution for Wifi.

Was this with an AMD64 or 32-bit installation of Ubuntu?

---

### Post by ACCA on 2010-08-15
> **irjozagata said:**
> 
I found SCX-4500W in /etc/sane.d/xerox_mfp.conf, where I replaced USB assignement with IP address of the scanner and it was recognized by SANE imediately!

/etc/sane.d/xerox_mfp.conf
....
# Samsung SCX-4500W
#usb 0x04e8 0x342b     #original USB definition put commented
IP 192.168.123.202       # added line with IP destination
....
Let me know, please, if it works with WiFi too.

Tried to add "IP" line in /etc/sane.d/xerox_mfp.conf - still does not work.

What version of backend do you have? In 1.0.20 xerox_mfp.c does not have any functionality to deal with IP - it is USB-only.

---

### Post by l_masoumi on 2012-01-17
Hi all,

I'm having a similar problem with two Samsung multi-function printers Models are CLX-3185FW and SCX-4833FD.

They are both connected to the same network as my PC is in along with the other colleagues' PCs. 

I have Ubuntu 10.04.3 on my PC and Windows 7 on VirtualBox OSE. Installin the drivers available in Samsung website I can PRINT and SCAN from my Virtual Machine (WIN. 7), but after installing the UnifiedLinuxDriver_0.91, Smartpanel_0.91, and PSU_0.91 on my ubuntu, I can PRINT but I can NOT SCAN in Ubuntu.

Ubuntu does not discover any scanner on my network, except one "HP Color Laserjet" which I added through System>Administration>New Printer, and I can use Application>Graphics>Simple Scan or XSane Image Scanner  to scan documents with it.

Anybody has any idea on how I can make the Samsung scanners discoverable through network connection?

Thanks heaps,

---

### Post by tweedledee on 2012-01-17
> **l_masoumi said:**
> Anybody has any idea on how I can make the Samsung scanners discoverable through network connection?

Thanks heaps,

Have you looked at [http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621), the associated web page, and recent posts?  There are lots of ideas there, some of which may help.  If you still can't get it to work, posting in that thread is more likely to be seen by someone who can help you, especially if you indicate what you have already tried and that hasn't worked.

---

