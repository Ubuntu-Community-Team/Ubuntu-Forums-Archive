---
title: "Trouble with Lucid on a Toshiba Satellite L635-S3015"
date: 2010-08-05
forum: Hardware
---

### Post by rugito on 2010-08-05
Hello everyone,
 
I finished installing Ubuntu 10.04 (amd64 architecture) on my new laptop, a Toshiba Satellite L635-S3015. I'm having lots of problems. Here's the list.
 
1. To install the system, I had to add "acpi=off" in the boot parameters, because otherwise the system hangs. And of course I need to add it in the grub.cfg file, for the same reason. I think this is the reason why the hotkeys aren't working (volume control, wifi switch etc.).
 
2. The wireless card isn't detected. The card is an Intel Corporation WiMAX/WiFi Link 6050 Series (rev 57). ifconfig doesn't detect it, and if I run ```
sudo ifconfig wlan0 up
``` then I obtain ```
SIOCSIFFLAGS: No such file or directory
``` My first attempt of fixing this problem was to install the WinXP driver via ndiswrapper. ndiswrapper -l shows that the driver is installed, but still, the card isn't working.
 
3. The wired ethernet card isn't working. I posted the problem I have in the relevant thread ([http://ubuntuforums.org/showthread.php?p=9682123#post9682123](http://ubuntuforums.org/showthread.php?p=9682123#post9682123))
 
4. Strangest of all, when I plug in my USB stick, it sometimes doesn't mount it. lsusb shows it plugged in, but there is no /dev/sdb file.
 
Should I change distro? Should I fight against each one of these problems and attempt to solve them?
 
For the moment, I feel to strongly disencourage anyone wishing to use Ubuntu 10.04 to buy this laptop.
 
Any help is greatly appreciated.

---

### Post by lidex on 2010-08-07
See this thread:
[http://swiss.ubuntuforums.org/showthread.php?p=9403187](http://swiss.ubuntuforums.org/showthread.php?p=9403187)

---

### Post by rugito on 2010-08-07
Hi lidex, thanks for the reply. I already tried installing the Intel drivers, without success. And I also came upon that thread, and I installed the [FONT="Courier New"]linux-backports-modules-wireless-lucid-generic[/FONT] package, but the card is still not working.

One way I thought about is to downgrade my kernel from 2.6.32 to 2.6.23, which is the one supported by the Intel drivers, and see if it works this way. Waiting for Intel to support more up-to-date kernels.

Any other suggestions?

---

### Post by rugito on 2010-08-11
So, I'm working my way through these problems. So far, I have solved the problems concerning the wired and wireless cards.
 
Since the computer doesn't have any way to connect to the internet, I had to use another computer to download the necessary package to start up.
 
SET UP THE WIRED CARD: follow the instructions given by Pytheas22 on [http://ubuntuforums.org/showthread.php?p=9449490](http://ubuntuforums.org/showthread.php?p=9449490)
 
This should get you the possibility to get the computer online.
 
SET UP THE WIFI CARD: as I explained here [http://ubuntuforums.org/showthread.php?t=1424177](http://ubuntuforums.org/showthread.php?t=1424177)
 
Now I am struggling with the acpi problem. Setting acpi=off allows to boot up, but I don't have a battery monitor status, I don't have the FN+something keys, and I suspect that the USB problem that I have sometimes is something related to that.
 
Also, sometimes the computer hangs when I shut down.

Any ideas anybody?

---

### Post by lidex on 2010-08-11
Bios update?
[http://ubuntuforums.org/showthread.php?t=1534195](http://ubuntuforums.org/showthread.php?t=1534195)

More:
[http://www.google.com/search?hl=en&newwindow=1&safe=off&sitesearch=ubuntuforums.org&q=Toshiba+Satellite+acpi&btnG=Search&aq=f&aqi=&aql=&oq=&gs_rfai=](http://www.google.com/search?hl=en&newwindow=1&safe=off&sitesearch=ubuntuforums.org&q=Toshiba+Satellite+acpi&btnG=Search&aq=f&aqi=&aql=&oq=&gs_rfai=)

---

### Post by rugito on 2010-08-11
Great, so now it works! I downloaded the new BIOS from the UK Toshiba site ([http://uk.computers.toshiba-europe.com/innovation/download_bios.jsp?service=UK](http://uk.computers.toshiba-europe.com/innovation/download_bios.jsp?service=UK)), I cancelled the acpi=off options, and now many things work:

- I have a battery monitor.
- The fan works properly
- Volume control from keyboard works
- USB stick mounts correctly
- I have 4 CPUs instead of one :p

Still not working:

- LCD brightness control
- Toggle Wifi On/Off

And I just realized that the speakers are playing when I plug the earphones in! Working on this one...

---

### Post by rugito on 2010-08-11
To automatically turn off speakers when plugging in the earphones:
[http://ubuntu-utah.ubuntuforums.org/showpost.php?p=9178795&postcount=131](http://ubuntu-utah.ubuntuforums.org/showpost.php?p=9178795&postcount=131)

---

### Post by Cabalbl4 on 2010-08-12
Btw what bios do You have? If it is not toshiba bios but phoenix bios, LCD brightness, bluetooth and many other things can be managed with omnibook module (needed to be compiled). It helped me with bluetooth at toshiba satellite a210p.

---

### Post by rugito on 2010-08-12
> **Cabalbl4 said:**
> Btw what bios do You have? If it is not toshiba bios but phoenix bios, LCD brightness, bluetooth and many other things can be managed with omnibook module (needed to be compiled). It helped me with bluetooth at toshiba satellite a210p.
 
I have a H20 bios. The installed version on my system was 1.40, but Toshiba released 1.50 on 21/07/2010...

---

### Post by Cabalbl4 on 2010-08-12
Not a phoenix bios. Then it should be toshset utility and toshiba_acpi module, I am not much familiar with them. :(

As far as I remember, on my A210p LCD brightness is configured by "video" module. Maybe You can do some tricks with it?

---

