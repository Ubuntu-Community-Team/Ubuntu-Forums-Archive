---
title: "can ipw2200 LED cause instability?"
date: 2006-08-28
forum: Hardware &amp; Laptops
---

### Post by zba78 on 2006-08-28
Is anyone aware if an issue that enabling the LED on laptops with the ipw2200 module can make the ipw2200 module less stable?

I've been trying to troubleshoot a problem with my laptop for about a couple of months where sometimes it connects to my router fine for a few days (even up to a week) but then gradually it needs 2/3/4 trys until it reaches the point where it just doesn't connect altogether. Then I try all maner of thing to ge it working.

Today however I have tried disabling the LED (by commenting out the line in /etc/modprobe.d/ipw2200) and my laptop has connected fine since.

I'll update in a few days as to how it's gone but I'm wondering if anyone knows of a problem with the LED making ipw220 less stable?

BTW, I'm connecting via WPA-PSK

---

### Post by x64Jimbo on 2006-08-28
Do you really need the LED? I haven't used mine in 2+ years. I just use the status indicator in the tray.

---

### Post by zba78 on 2006-08-28
You are correct I don't need it. Thats why I disabled it. Seems that it hasn't helped anyway. I'm still getting the same problems.

My **Rx invalid crypt** count keeps increasing when I try to connect. I'm considering switching over to WEP to see if it helps.

---

### Post by zba78 on 2006-08-28
OK, a quick thought. Do is it worth downloading the latest driver from the ipw2200.sourceforge.net/ page?

according to dmesg | grep ipw ```
[17179592.564000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[17179592.564000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179592.564000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!

``` Ive got version 1.1.1 and the latest on the site is 1.1.4.

Would I need to remove the old driver first? if so how?

---

### Post by Kashirigi on 2006-08-28
I've had the LED enabled for months, and have never experienced any problems. At least, none related to the IPW2200 driver. I also connect using WPA-PSK.

Maybe I'm just lucky.

---

### Post by zba78 on 2006-08-29
I’ve now switched over to WEP. It’s not what I wanted to do but it has made my connection perfectly stable

---

### Post by k_smolka on 2006-11-15
I am having the same stability problems on ipw220 and WPA.

My connection worked fine in dapper but in edgy its very unstable and eventually stops working. However everything works fine with WEP.

Have you had any luck solving this problem. 

Regards 

Karl

---

