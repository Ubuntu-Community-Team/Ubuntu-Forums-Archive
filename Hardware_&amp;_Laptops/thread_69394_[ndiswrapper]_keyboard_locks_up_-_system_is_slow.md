---
title: "[ndiswrapper] keyboard locks up - system is slow"
date: 2005-09-26
forum: Hardware &amp; Laptops
---

### Post by coffemonkey on 2005-09-26
Hello fellow users,

I've got troubles running my Netgear WG111v2 USB 2.0 WLAN stick using ndiswrapper under Ubuntu 5.04.
I've really tried everything - the ndiswrapper version bundled with the installation CD of Ubuntu, and I also lately compiled and installed the latest version of ndiswrapper.

The problem is, that the system partially locks up, after calling ```
modprobe ndiswrapper
```. The keyboard does not work anymore and while running GNOME, the mouse movements are jerky due to a periodically repeating delay.
While being in "text mode" the system still responds to ctrl+alt+del, which yields to a very slow system shutdown. All the other keys do not work.

I tried all Netgear drivers from the device's CD, also the latest from netgear.com.
I do not see any changes in this behaviour. I also tried turning off acpi via boot parameter. No better.

Somewhere I read, that hoary might have problems with USB support. Could that be the (or one) cause? I've also got two USB hubs attached to my system.

I hope somebody can point me to a solution to this problem, since I'm trying to figure it out for three days, now.


Thanks in advance,

Thomas

---

### Post by mlomker on 2005-09-26
> I hope somebody can point me to a solution to this problem, since I'm trying to figure it out for three days, now.


This might not sound like a helpful answer, but can you use a non-usb adapter instead?  Most of the problems with ndiswrapper seem to be with the usb adapters, not pci or pcmcia.

---

### Post by coffemonkey on 2005-09-26
[quote=mlomker]This might not sound like a helpful answer, but can you use a non-usb adapter instead? Most of the problems with ndiswrapper seem to be with the usb adapters, not pci or pcmcia.[/quote]

Well, I already thought about that, but I don't have any free PCI slot in my computer.
Maybe I should ask for a WPA-capable USB WLAN device which is natively supported by Linux. Does something like that exist?

---

### Post by az on 2005-09-26
Maybe you can download the latestversion of ndiswrapper and compile it by hand.  I had a similar problem in Warty and that helped.

sudo apt-get install build-essential linux-headers-(whatever kernel version you are running)

Get the latest ndiswrapper tarball and compile it  ( If I remember properly, you can use the debian scripts in it to make two debian packages

sudo debian/rules binary (or something like that)

sudo dpkg -i ndisw*.deb

---

### Post by mlomker on 2005-09-26
>  Does something like that exist?

No, that's the problem--there are no natively supported usb adapters.  A lot of people manage to get them to work but you'll see post after post on here about them.  If you have to then you have to.  I'd agree with installing the latest version.

If you search the wiki in my sig below for *ndiswrapper* you'll find some how-to's.

---

### Post by coffemonkey on 2005-09-27
Thanks for your replies so far, but I already did install the latest version of ndiswrapper. I think I'm going to test that commercial DriverLoader. Maybe that's better...

---

### Post by coffemonkey on 2005-09-27
Hey there, I could manage some progress with my problem:

I downloaded the previous stable version of ndiswrapper (1.2), compiled and installed it. The system does not freeze anymore and my WLAN stick's LED flashes like running under Windows.

My only problem is getting WPA to run (sigh....) :rolleyes:


P.S.: I just checked ndiswrapper's sourceforge page. A new stable version is out (1.4). Got to check it. Unfortunately 1.2 seems to be gone. Maybe it's just temporarily removed.

---

### Post by mlomker on 2005-09-27
> P.S.: I just checked ndiswrapper's sourceforge page. A new stable version is out (1.4). Got to check it. Unfortunately 1.2 seems to be gone. Maybe it's just temporarily removed.

Ndiswrapper requires the use of wpa_supplicant, I believe.

---

### Post by sn33kyP3t3 on 2005-09-27
I tried messing with ndiswrapper every which way, ultimately I think you might be in for problems unless you are using one of the listed cards that are known to work. 

I finally broke down and got (paid for) Linuxant Driverloader. Do the trial, its free, and you might be amazed! :)

---

