---
title: "USB ports not working"
date: 2010-12-08
forum: Hardware
---

### Post by Trigger_21 on 2010-12-08
Please Help 

I have a HP Pavilion ze4800 after installing Ubuntu 10.10 none of the USB ports are working.

Any Suggestions?

---

### Post by Fafler on 2010-12-08
Did it work in older versions of Ubuntu?

Open a terminal and do a:

```
lspci > sysinfo.txt
lsmod >> sysinfo.txt
dmesg >> sysinfo.txt
```

Attach the resulting file here.

---

### Post by Trigger_21 on 2010-12-09
Thank you for your help, i upgraded to 10.10 from 10.04 in attempt to fix the problem, which didn't work.

Here is the outputted file you requested, had to compress as it exceeded file size upload limit for text file
[ATTACH]177887[/ATTACH]


:D

---

### Post by Trigger_21 on 2010-12-11
also it might be worth mentioning that the usb drives do work on other machines, the common error seems to be "device not accpeting address 13, error -62" & "unable to enumerate USB device on port 1", the usb drives show no signs or power with no lights turning on, still working on solution :D

---

### Post by WinRiddance on 2010-12-11
According to the HP website (googled it) this laptop was originally made for Win98, WinME, and WinXP. It won't even conform to Winvista standards which came out about close to 4 years ago. So I'm assuming that your laptop is anywhere from 5 to 7 years old and that means that all of your USB ports are more than likely just USB 1.0 as opposed to USB 2.0 ports. Can't say for sure though ...

[Here's a tech support post all the way back from 2004 (click on this line) ...]("http://209.68.14.80/vb/showthread.php?p=199651")
256 MB of RAM is really pushing it with a lot of the newer Ubuntus.

Considering the age of your machine you'd probably be best served by installing Xubuntu or PCLinuxOS, or Ubuntu 8.04, all of which are much friendlier on systems with old or severely limited hardware resources such as CPU speed, amount of RAM, and so on. Keep in mind that Windows and Linux are completely different operating systems too. Hardware manufacturers stood to profit by providing proper/adequate hardware drivers for their devices within the Windows environment. With Linux that's not the case though, since almost everything is free. That's why I think that the age of your machine along with Ubuntu may have a lot to do with the problems that you're experiencing. Best of luck to you!

---

