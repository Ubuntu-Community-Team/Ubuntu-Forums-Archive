---
title: "MSI laptop modem"
date: 2007-06-01
forum: Hardware &amp; Laptops
---

### Post by kilou on 2007-06-01
Hi,

I'd like to make the internal modem of my MSI S260 laptop work with Gnome-PPP. When I launch Gnome-PPP and try to detect my modem I get "No modem was found on your system".

However lspci gives the following:

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)

This is a pretty common modem and it is supposed to work in Linux. Do I need any driver/module or whatever to make it work? I tried to load snd_intel8x0m module but it doesn't help...

Thanks

---

### Post by kilou on 2007-06-03
up

---

### Post by Matchless on 2007-06-03
Hi,
     Your first job is to exactly determine what modem chipset is used so that you can determine which drivers to install, if you are dual booting with Windows have a look at the windows drivers or do a modem query i.e. Smartlink, Lucent, Conexant etc.
I suggest you go to [https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto) and use scanmodem to try and identify your actual modem. Once you are sure what you have then search the forum for you modem type and the chances are good you will get it running.
Basically you need to install drivers and maybe a daemon ( for Smartlink) to get yourself up and running.
Good luck

---

### Post by kilou on 2007-06-03
Thanks! Will look at that.

---

### Post by Matchless on 2007-06-04
Hi,
     Your MSI S260 laptop seems(according to google) to have an Agere System AC97 Modem and that is then the same as the Lucent or ltmodem. I know there are Martian drivers that should work. The best would be to download the latest Martian drivers and compile for your kernel version. Have a look here:
[http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/martian/)

Enjoy!

---

