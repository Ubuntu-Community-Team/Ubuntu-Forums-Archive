---
title: "Broadcom and Gusty on a Dell Latitude D600"
date: 2007-10-21
forum: Hardware &amp; Laptops
---

### Post by wareagle on 2007-10-21
I was able to get my Broadcom wireless working with a clean install of Kubuntu Feisty using the bcm43xx-fwcutter program.

I did a clean install of Kubuntu Gusty.  It asked me about restricted drivers, one of which was for my Broadcom card, so I installed it.

When I reboot, the wireless doesn't work immediately.  I have to open a console and type ```
sudo iwconfig eth1 essid {my ssid}
``` and then ```
sudo dhclient eth1
```  More annoyingly, if I try to set it to use my AP in Kwifimanager, it won't work at all (even setting the ESSID through iwconfig and running dhclient doesn't work) until I reboot.  The same thing happens if I run kismet or airodump.

I tried running ```
bcm43xx-fwcutter -w /lib/firmware/'uname -r' bcmwl5.sys
``` using the firmware I had on Feisty but it still behaves the same way.

(The code extracted it to the same folder as the stock firmware from Gusty so the above code isn't wrong.)

What gives? :confused:

---

### Post by Dr.Suave on 2007-10-21
I'm completely new to this so I didnt understand half your post.

but I was having trouble setting up WiFi in Gutsy. In the end what worked for me was reinstalling the OS, and then straight away following the instructions here: [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)
using the online version, as gutsy's kernel is not supported for the offline.

since then my WiFi has been completely fine, not a single problem.

hope this helps

Wilf

---

### Post by wareagle on 2007-10-23
I would like to get the native drivers working so I can use Kismet/Aircrack.  (They don't work with NDISwrapper.)

I wonder if this is a bug or a "feature."

---

