---
title: "Toshiba Satellite A215-S7437 laptop wireless(realtek) not working"
date: 2008-07-17
forum: Hardware
---

### Post by jmetter18 on 2008-07-17
I am new to the linux community and this is my first successful install of linux. It doesn't detect that I have a wireless card. It is an integrated card. 
As stated before I am a complete newbie to linux with no programing experience. All the threads I saw on the issue with realtek cards on satellite laptop the OS at least found a wireless card. Any help would be appericated.

---

### Post by mbarvian on 2008-07-18
Here's a guide that will work with your hardware, especially your Realtek (if I you have a 8187b card, which I think you do):

[https://help.ubuntu.com/community/ToshibaSatelliteA215S7422Guide](https://help.ubuntu.com/community/ToshibaSatelliteA215S7422Guide)

Hope it helps :)

---

### Post by jmetter18 on 2008-07-20
thanks mbarvian that did help me get wireless drivers that will mostly likely work, but linux still isn't recognizing a wireless card at all.

---

### Post by digitaldude99 on 2008-09-20
> **mbarvian said:**
> Here's a guide that will work with your hardware, especially your Realtek (if I you have a 8187b card, which I think you do):

[https://help.ubuntu.com/community/ToshibaSatelliteA215S7422Guide](https://help.ubuntu.com/community/ToshibaSatelliteA215S7422Guide)

Hope it helps :)

Thanks!  My primary goal was to establish an internet connection first and foremost.  Since I was initially unable to connect via wireless, *that did not prevent me from establishing an internet connection using the RJ-45 cable!*  After several attempts I was able to get the wireless to work using those instructions.  If you cannot get the wireless to work, you need to go back and check what you're entering in terminal.  My mistake was leaving out a "." in the command line that I wasn't able to clearly see in the instructions.  The link you provided also fixed an additional problem I was having with the mouse on the Toshiba Satellite A215-S7437.  My mouse would intermittently freeze up using either the touchpad or USB mouse.  I followed the steps to configure the ATI Radeon x1200 Graphics Card after learning that an incorrect video driver could cause mouse problems.  Since the video driver was the last issue I hadn't addressed, I followed those steps and the mouse problem is resolved!

---

