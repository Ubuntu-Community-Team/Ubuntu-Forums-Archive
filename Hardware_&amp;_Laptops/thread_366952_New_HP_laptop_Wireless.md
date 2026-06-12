---
title: "New HP laptop Wireless"
date: 2007-02-21
forum: Hardware &amp; Laptops
---

### Post by kd5ob on 2007-02-21
I followed the ndiswrapper instructions and got a driver to load from this help forum.

Problem is, I've never run wireless from Linux.  I have it working on XP but not yet
on Ubuntu.

I'm a truck driver and have several places at one truck stop you could use but I only
use SIRICOMM and have to get a lease from them.

Wonder, is there a way you can list who's available to get a lease from then pick the
right one?  Tried getting that ethereal thing to work and it doesn't.

Somebody want to teach me how to use my wireless driver now that I have it installed
BCMWL5.inf Broadcomm.

Broadcomm 802.11b/g WLAN

File version 4.40.19.0

I also got told by the Knoppix folks that 4X versions of drivers are not supported yet
so I used the zip driver found here on Ubuntu for the ndiswrapper idea.
Knoppix idea was to use bfwcutter modules which is slightly different.

Anyway, I'm good and lost.  

Thanks for any help.

Charlie

---

### Post by nachotronics on 2007-02-28
I recommend you to use gnome network manager, wich can be instaled and configured following _**[this howto]("https://help.ubuntu.com/community/WifiDocs/NetworkManager")**_, its very usefull specially when you need to connect to wep and/or wpa pretected networks

Hope this helps.

---

### Post by Ehnvis on 2007-02-28
Are you sure that your new HP laptop has a broadcom wlan? Mine doesn't, it's using an Atheros based wlan and works out of the box.

print the hardware with ```
lspci
``` and drop the output here and I bet you will get help on howto get it up and running.

---

