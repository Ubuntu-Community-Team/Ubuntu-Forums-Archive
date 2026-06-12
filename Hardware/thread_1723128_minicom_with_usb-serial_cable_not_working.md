---
title: "minicom with usb-serial cable not working"
date: 2011-04-06
forum: Hardware
---

### Post by bugpeople on 2011-04-06
Hi.  I hope I can figure this out.  I've seen messages similar to my problem, and I've followed the steps from [https://help.ubuntu.com/community/CiscoConsole](https://help.ubuntu.com/community/CiscoConsole), but it's not working.  so, here goes: 

I have a dell inspiron mini with only usb ports, no serial ports, running ubuntu 10.04 lucid lynx on a dual booted system.  the other OS is Windows XP.

I have a radio shack gigaware usb-serial cable

I want to connect to an adtran 600 series with an rj45 craft port using minicom or gtkterm (I really don't care, but minicom seems sexier.)  Before you say adtran ??? Let me just say that in Windows, I use the same USB port and cable to connect to the adtran and have no problems, and it also works without any changes in windows for connecting to a cisco router as well.

This works for me in Windows, but I would like to throw XP out, and only use Ubuntu.  I had it working at one point, but I couldn't get files to transfer, so I added lszrz to minicom, and now I can't connect through minicom at all.  I've changed every setting I can think of and I'm afraid I messed up my minicom, so I removed minicom and tried again, but no luck.

If I haven't given enough info, let me know.  I did dmesg | grep tty, here are the results: 
[ 2915.564066] usb 3-2: generic converter now attached to ttyUSB0.

Thanks

---

### Post by wt8008 on 2011-04-06
Your system did detect the USB-serial converter and you can access it at /dev/ttyUSB0.

How did you start minicom? Did you use any commandline options? What settings do you need to access the device connected to the serial port?

---

