---
title: "series 7 compatible with ubuntu now?"
date: 2013-04-08
forum: Hardware
---

### Post by oh my on 2013-04-08
hi, 
i'm falling in love with samsung's series7 at the moment and am considering buying one (model version 730u3e). 
Has anybody installed ubuntu on one of the latest models yet? 

I read some disturbing articles about samsung's bios/uefi being buggy and ubuntu effectively bricking the machines. Is that still the case or has there been an update?

regards ohmy

---

### Post by oldfred on 2013-04-08
Do not know if they have the bug or not, but some have installed.

 Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)
Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

Supposedly a bug fix was released to help, but then it turned out that Windows also triggers the bug so it is a Samsung issue in UEFI implementation. Just make sure you have the newest UEFI/BIOS version.


 UEFI boot live-usb bricks SAMSUNG 530U3C,np700z5c laptop - fix released
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)
[http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html](http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html)
The problem also appears to affect Ubuntu 12.10 and other Samsung models. The Ubuntu bug report includes posts from users reporting that the problem also affects 300E5C, NP700Z5C, NP700Z7C and NP900X4C series laptops.
[http://mjg59.dreamwidth.org/23554.html](http://mjg59.dreamwidth.org/23554.html)

---

### Post by oh my on 2013-04-08
Hi,

thanks for all the links! :) I will take a close look and hopefully Samsung will release an update soon!

regards ohmy

---

### Post by gkbgkb on 2013-04-10
Hi

i have one of this samsung series 7 730u3e
with i7, 13.3 full hd and so on ... 
very good laptop 
but i have problems with ubuntu :(
especially - kubuntu
for last 5 days im trying to use it but there are some problems that drives me crazy 
1. touch pad - this elantouchpad did not works like touchpad but like regular mouse 
i read so many things but i dont have solution :( - i dont have 2 finger scroll and 2 finger right click  /the bad thing is that i cannot click right and left button of touchpad on the same time and i cannot paste :(
2. wifi - i thing that wireless is to weak ... for example on my old HP i have full signal, but on samsung - no connection
3. suspend dont work like must work /i cannot suspend it when close it for example/

but laptop is very good 
every other things work good
i try kubuntu 12.04, 12.10 and now 13.04  - the problems are same 

i want to use it but touchpad is real problem :(

if somebody find a solution ... please keep me informed 
regards

---

### Post by peppedaman on 2013-04-10
For the touchpad issue I've created a bug on Launchpad. You should mark it as affecting you as we probably have the exact same touchpad model. Here's the link: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1166442) Also, relating to that bug, if you're on CSM/BIOS boot instead of UEFI you could test the latest mainline kernel for any improvements, which I sadly cannot :(

---

### Post by gkbgkb on 2013-04-11
Hi
i installed 3.9 kernel but no improvements :(

i'm on UEFI 
if i switched to CSM/BIOS boot my laptop does not boot 
if i can help with anything ... 
cos i want to use my laptop :)

---

### Post by peppedaman on 2013-04-12
Could you report for me on the launchpad page that 3.9 does not solve the issue? And also adhere to the other bug-reporting guidelines. It's the best way to get this bug resolved, is to do all the testing we can.

---

### Post by ott-maaten on 2013-11-30
I just bought 730U3E-K01EE, installed Xubuntu 13.10 (i386) and...
...everything works:
touchpad multitouch
Intel graphics
Intel Wifi + BT
sound
Webcam
etc etc
even keyboard light sensor works, simply I cannot change the light manually (keys F9-F10)
and cannot switch manually Wifi on-off (key F12) but this doesnt matter for me.
No problem at all with this hardware

Initially I had to mess up with BIOS:
to boot from USB I had to disable all things: UEFI (changed to CSM), SecureBoot, FastBoot and also I had to disable this strange "Windows Login Prompt..." or something similar.
After that all went flawlessly - install, update, battery tuning etc
I deleted completely Windows 8 (because I never use it)  and took all drive for Xubuntu. I cannot say if dualboot would be possible with this BIOS.

But generally it works much much better than I supposed before the purchase. I was expecting lot more problems.

---

