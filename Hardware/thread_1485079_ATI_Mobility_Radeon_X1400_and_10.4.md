---
title: "ATI Mobility Radeon X1400 and 10.4"
date: 2010-05-16
forum: Hardware
---

### Post by sunstriker on 2010-05-16
Hi!

I've installed Lucid Lynx on my old laptop which serves as a media center. I used to run XBMC on 9.10 before without problems. I did a clean install of 10.4 and installed XBMC. When I ran XBMC it was very, very laggy. So I tried installing fglrx drivers and the official ATI drivers.
Since then I can't even start XBMC anymore because it can't use OpenGL. When trying to run the catalyst control center or aticonfig it says "ati driver not in use or no ati device present" or similar.
In the first place I'd like to know where I can configure my video card driver like I used to do in Xorg.conf, a file which seems disappeared.
If anyone has a solution on how to install the X1400 Mobility Radeon properly, that would be great! Otherwise I'll have to work with Windows 7, which is not cool...

---

### Post by libertao on 2010-05-31
Yeah, have exact same problem here with 10.04, x1400 and xbmc.

---

### Post by rgm3 on 2010-06-03
I too have this problem.  See also:
[http://ubuntuforums.org/showthread.php?p=9325644](http://ubuntuforums.org/showthread.php?p=9325644)

---

### Post by Yellow Pasque on 2010-06-03
The X1400 isn't supported in newer fglrx/Catalyst. So trying to install a driver that doesn't support your card = bad. Fortunately, it's reversible: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

---

### Post by rgm3 on 2010-06-11
> **Temüjin said:**
> The X1400 isn't supported in newer fglrx/Catalyst. So trying to install a driver that doesn't support your card = bad. Fortunately, it's reversible: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

In my case the above document doesn't apply, since I've never had fglrx installed (fresh install of 10.4 Lucid Lynx).  The issue seems to be simply that the open source driver sucks, and there is no way to use the proprietary Catalyst driver with the new X server included in Ubuntu 10.4 LTS.

---

