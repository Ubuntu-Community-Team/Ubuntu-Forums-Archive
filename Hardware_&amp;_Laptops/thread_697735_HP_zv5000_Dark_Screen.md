---
title: "HP zv5000 Dark Screen"
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by user_linux08 on 2008-02-15
I just replaced the LCD Inverter. Still the same no display problem. When I push the lid-switch, full display appears for millisecond, then darks again. Is there another component which needs to be replaced.

I might add, the second monitor works fine. So it would not be a display problem.

Can anyone shed some light here please.


thanks

---

### Post by yyyyyy on 2008-02-18
You have tested everything there is to test (video adapter, invertor, and LCD does display just dark).

The only left is the CCFL (LCD Backlit Lamp). The symptoms you show definitely points to it. You can find this on Ebay for roughly $10 but installation means complete disassembly of the display, down to taking the LCD panel itself apart.

I would recommend search the net for some sample instructions and see if you want to deal with the labor (it would be a great learning experience, if you have the time). Otherwise, buying a replacement assembly would be the easiest.

---

### Post by NewJack on 2008-02-22
I don't mean to hijack your thread, but what version of Ubuntu do you have installed on your zv5000?  I have one laying around the house that I would like to put back into service.  Did you use a particular HOWTO to get it going?  Thanks!

Joe

---

### Post by user_linux08 on 2008-02-27
I already replaced both. the backlight and the power inverter. Still the problem persists.

---

### Post by dradicci on 2008-02-28
hi, I got the same issue.... I take apart the motherboard and I will replace the display lid switch. I guess we got a chance to disable this switch becouse to replace it you must unsolder this very small switch. Some other laptops you can disable very easy unplugging an a small conector.

I did everthing. but first I took the complete screen to test in another laptop zv5000 and I tell you there is not problem with the screen.

I will try and I`ll let you know soon

Best Regards and sorry about my english...

---

### Post by user_linux08 on 2008-03-04
I am not sure disabling the lid switch will solve the problem. 
I was wondering if there is a diagnostics porgram in Linux (ubuntu) which will test all the h/w to identify (as much as possible) the real problem.

With ubuntu, when the primary monitor is disabled, the 2nd monitor automatically will take over.  Unfortunately,  with windows XP this is not the case, which prevents testing the Laptop online with HP remote diagnostics test..

---

### Post by sharingan_kzero on 2008-03-10
I also have the same issue at you do when the screen turn completely dark. After I replaced the inverter, nothing happen. So I change out the cable and the CCFL then it's working fine. You can do a hardware test on Window XP by using DXDIAG at the command prompt to test it. Not sure on Linux.

---

