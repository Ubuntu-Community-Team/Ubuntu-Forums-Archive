---
title: "Onboard modem / softmodem / not working"
date: 2009-05-09
forum: Hardware
---

### Post by baiki on 2009-05-09
Dear Community

And still modem problems. I convinced one lady to use Ubuntu instead of alternative OS's. But it looks like I am not able to install the on-board modem. I search now since days in this forum and major search engines. I am obviously totally unable to install a modem (and this in the year 2009) but I am not yet willing to give up.

I try this on a Toshiba Protege M100, using Ubuntu 9.04. I used **scanModem** and I guess inside the laptop is a **SmartLink (snd_intel8x0m using ALSA)**.

So I downloaded...
1. sl-modem-deamon
2. sl-modem-modules-2.6.28-11-generic
3. sl-modem-source

and installed them. So far so good. After...

$ sudo dpkg-reconfigure sl-modem-daemon -plow
$ sudo /etc/init.d/sl-modem-daemon restart 

sometimes the software tells me the /dev/ttySL0 should be available (and a link from /dev/modem should be created as well). However I just can find /dev/modem which is now a broken link to /dev/ttySL0.

So, and now I don't know what to do anymore. Buying quickly a new modem is absolutely no option (1. I am in Africa and 2. no cash in my pocket).

Please help.

Cheers,
Baiki

Content of ModemData.txt as attachment.

---

