---
title: "T41 Dynamicclocks"
date: 2009-03-08
forum: Hardware
---

### Post by mojo2405 on 2009-03-08
Hi,
I am a bit of a Linux noob, but am having a lot of fun getting my laptop working.:D
I have a Thinkpad T41 with the Radeon 9000 Mobility (M9).
I am using Intrepid.

I was having trouble with high power drain in suspend.  I followed: [http://ubuntuforums.org/showthread.php?t=1070403&highlight=thinkpad+sleep+power+drain](http://ubuntuforums.org/showthread.php?t=1070403&highlight=thinkpad+sleep+power+drain) to fix it.
As such, I have radeonfb enabled in my kernel (confirmed in my kernel log).  Also, according to the kernel log, DynamicClocks is enabled:
Mar  7 12:11:59 pavan-T40laptop kernel: [    3.880018] radeonfb: Dynamic Clock Power Management enabled

I have Dynamicclocks enabled in my xorg.conf:
Section "Device"
       Identifier  "Videocard0"
       Driver      "radeon"
       VendorName  "IBM ThinkPad"
       BoardName   "ATI Radeon Mobility M9"
       Option	   "DynamicClocks" "on"
EndSection

However, if I look at my Xorg.0.log, I see:
(II) RADEON(0): Dynamic Clock Scaling Disabled

Based on:
[http://www.thinkwiki.org/wiki/How_to_make_use_of_Graphics_Chips_Power_Management_features](http://www.thinkwiki.org/wiki/How_to_make_use_of_Graphics_Chips_Power_Management_features)

I should be doing everything correctly...still no luck.


I am very happy with my installation on this laptop so far...I have full suspend functionality, full effects working, and everything else.

The ONLY thing missing are the benefits of Dynamicclocks (I have used rovclock...).

I am not sure what I am doing wrong...can anyone help?

Thanks

---

