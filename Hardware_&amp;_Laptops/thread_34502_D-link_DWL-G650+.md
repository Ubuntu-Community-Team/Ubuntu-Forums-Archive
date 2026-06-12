---
title: "D-link DWL-G650+"
date: 2005-05-15
forum: Hardware &amp; Laptops
---

### Post by maci on 2005-05-15
Hi,

I have already KUbuntu 5.04 on my laptop (toshiba anyway).
Now I try to install DWL-G650+, but my kubuntu does't want to find the card.

Please help me.
Write in few step, hot to make it fine ?

Thank you, 
mAcI
___________________
(k)UBUNTU RULEZ

---

### Post by Cal Paterson on 2005-05-15
You could try checking the Linux Hardware Compatibility HOWTO:
[HTML]http://www.tldp.org/HOWTO/Hardware-HOWTO/nic.html[/HTML]

3rd result on google search for "DWL-G650+ linux":
[HTML]http://www.ndeepak.info/tech/wlansarge.php[/HTML]

---

### Post by dbott67 on 2005-05-15
[QUOTE=maci]Hi,

I have already KUbuntu 5.04 on my laptop (toshiba anyway).
Now I try to install DWL-G650+, but my kubuntu does't want to find the card.

Please help me.
Write in few step, hot to make it fine ?

Thank you, 
mAcI
___________________
(k)UBUNTU RULEZ[/QUOTE]

Hi Maci,

I didn't follow Cal Paterson's links, so it may have the answer you're looking for, however, I've got a D-Link DWL-650+ in my Toshiba Laptop and it's working fine.

The driver required is the acx_pci.  From the terminal, search for the appropriate driver to see if it's loaded:

lsmod | grep acx

If it's there, try removing & reloading it:

rmmod acx_pci

The reload it:

modprobe acx_pci

And finally restart the network services:

/etc/init.d/networking restart

If it's not there, you may need to download & install it from [here.](http://stef.tvk.rwth-aachen.de/~nazgul/debian/DWL-650+_Howto.html) 

*****************************************

Here's something I posted earlier when I was having wireless problems with ubuntu 4.10.  Wireless access seemed to drop out with some regularity. Some research in ubuntuforums led me to *borrow* the following script from snop (who wrote the original):

#############################################

#!/bin/bash

rmmod acx_pci
modprobe acx_pci
/etc/init.d/networking restart

##############################################

The issue appears to be resolved in Ubuntu 5.04 (for me anyhow).

You may need to install/download the drivers (I didn't have to --- the DWL-650+ was detected correctly during installation), but it definitely works!  :)

-Dave

---

### Post by maci on 2005-05-22
When I firtst time install (k)ubuntu 
it recognized my DWL-G650+ card, but when I install without it
I can't use ubuntu driver .... ](*,) 

I don't want to make it with ...ndiswrapper.


Is it possible to do it like ubuntu ?? when install OS ?? :-?

---

### Post by jiyuu0 on 2005-05-22
i'm running on ubuntu 5.04 and my D-Link AirPlus (DWL-650+) worked out of the box without any additional installation of drivers

my curiousity, i thought kubuntu is based on ubuntu. so, shouldn't it work too?

or is it because i'm running on a Dell Inspiron 5150?

---

