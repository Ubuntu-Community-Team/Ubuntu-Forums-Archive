---
title: "Advice about Broadcom - Unknown Device"
date: 2006-08-27
forum: Hardware &amp; Laptops
---

### Post by czaleski on 2006-08-27
Greetings. I'm hoping someone can offer some advice. I have a new Dell Inspiron e1405 with a "Dell Wireless 1390" adapter. I've found that this is a Broadcom adapter (4311 I believe).
As most folks, I've spent a lot of time reading these forums and scouring Google results.

"lspci | grep Broadcom" reports the following:
0000:02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:0c:00.0 Network controller: Broadcom Corporation: Unknown device 4311 (rev 01)

I've tried 2 different ndiswrapper installation tutorials here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
and here:
[http://www.ubuntuforums.org/showthread.php?t=193350&highlight=bcm1390m](http://www.ubuntuforums.org/showthread.php?t=193350&highlight=bcm1390m)
The second time was after a fresh install.
I've also tried the "bcm43xx-fwcutter" here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper)

Sadly none have worked. After working through each of these processes, there is simply still no wireless adapter to be found. (eg: "Hardware present: No")
lspci still always says "unknown device" for this little sucker

I am hoping someone can tell me...
Does something else need to be done before any of these driver install methods will *see* the adapter?
If so how do I resolve this problem?
If not, what should I do?

Any help or advice is greatly appreciated.
Thanks very much

---

### Post by Zelut on 2006-08-27
I have the BCM4306 card & I use the bcm43xx-fwcutter package.. 

Have you tried installing that (bcm43xx-fwcutter) and then funning the included script at:
/usr/share/bcm43xx-fwcutter/install_bcm43xx_firmware.sh

All I've had to do is install the package, run the script & I'm ready to go.

---

### Post by czaleski on 2006-08-27
Yes that was the 2nd thing I tried - no dice. I attempted ndiswrapper before that (unsuccessfully), and did my best to undo/uninstall ndiswrapper before the fwcutter stuff. So maybe that had an effect somehow.
Maybe I'll try yet another clean install and try the fwcutter from scratch.

Would still love any other suggestions :-?

---

### Post by jedleman on 2006-08-29
HELP!!!!!!!!

I am having the same problem with my new Dell 1705.  It has the same card (Dell Wireless 1390) and gives me the same message stating that it is unknown.  PLease let me know if you ever hear anything from anyone or if you get it working.  I would love to not have to revert to Windows simply to avoid this problem.  I love Umbuntu!

(I too tried ndiswrapper and cutter with no success.)

Thanks in advance - 

Jason

---

### Post by Sh8kR on 2006-09-09
> **czaleski said:**
> Yes that was the 2nd thing I tried - no dice. I attempted ndiswrapper before that (unsuccessfully), and did my best to undo/uninstall ndiswrapper before the fwcutter stuff. So maybe that had an effect somehow.
Maybe I'll try yet another clean install and try the fwcutter from scratch.

Would still love any other suggestions :-?


Someone posted that Ndiswrapper was the only way to get the Broadcom 4311 card working.

---

