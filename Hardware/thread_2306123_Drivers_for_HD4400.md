---
title: "Drivers for HD4400"
date: 2015-12-12
forum: Hardware
---

### Post by jim_10 on 2015-12-12
Hi,
I have: ASUS H97M-PLUS and Intel Core i3-4150 and I have installed Lubuntu 15.10 but I have problem with VGA. When I use command lspci I see:
VGA compatible controller: Intel Corporation 4th Generation Core Processor Family Integrated Graphics Controller (rev 06).
I have install drivers from:  [https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads) I used drivers: 
Graphics Installer 1.2.1 for Ubuntu* 15.10, 64-bit. I add signatures: 
wget --no-check-certificate [https://download.01.org/gfx/RPM-GPG-KEY-ilg](https://download.01.org/gfx/RPM-GPG-KEY-ilg) -O - | \
sudo apt-key add -


wget --no-check-certificate [https://download.01.org/gfx/RPM-GPG-KEY-ilg-2](https://download.01.org/gfx/RPM-GPG-KEY-ilg-2) -O - | \
sudo apt-key add -


And also use: intel-linux-graphics-installer. Installer was completely, but when reboot vga is still: VGA compatible controller: Intel Corporation 4th Generation Core Processor Family Integrated Graphics Controller (rev 06). I do not know if the drivers are installed properly, why not knowledge HD 4400?
Please help me. Thx.

---

### Post by mikewhatever on 2015-12-12
What is wrong with that output? What exactly do you expect to see? Why do you think there is a need for drivers?

---

### Post by jim_10 on 2015-12-12
I'm not sure that drivers are good. When I use Windows always name of graphic card was correctly. So you think that these drivers are correct not need anything else installed?

---

### Post by mikewhatever on 2015-12-12
Not quite sure I understand what you want, let's resort to a word of wisdom: 'if it works, don't fix it.

PS: ...also, Ubuntu is not Windows.

---

### Post by jim_10 on 2015-12-12
Mainly I mean that these drivers are correct, whether the description should be a HD 4400 or simply the description Intel Corporation 4th Generation Core Processor Family Integrated Graphics Controller (rev 06) ?
Ok, so ticket maybe close.

---

### Post by Bashing-om on 2015-12-12
jim_10; Hello;

Like this, Intel supports us very well . They do provide the best driver and it is incorporated in the kernel as open source .
You do in terminal:
```

sudo lshw -C display

```
and in all this info is the "configuration" line with a "driver=1915" or similar.
You can rest assured that a driver is loaded and is the best that the kernel can  provide because Intel gave us the best .

If it is Intel
[INDENT][INDENT]it just works
[/INDENT][/INDENT]

---

### Post by jim_10 on 2015-12-12
Thank you Bashing-om for your comprehensive explanation.

---

### Post by jeremy31 on 2015-12-13
The info you see is not set by the drivers, the name comes from a PCI ID database that some users can modify.  There is a database for USB devices also, you might see just a manufacturers name behind some devices if nobody has given the device a description in the database in ```
lsusb
```

You can download the newer database with ```
sudo update-pciids && sudo update-usbids
```

---

### Post by mikewhatever on 2016-01-02
> **Bashing-om said:**
> ...

You can rest assured that a driver is loaded and is the best that the kernel can  provide because Intel gave us the best .

If it is Intel
[INDENT][INDENT]it just works
[/INDENT][/INDENT]
I do respect your opinion, and don't want to argue needlessly, ...just thought I'd present the other side of the coin.
Not sure where that info comes from. Intel graphics for Linux is pretty horrible, it does not just work, and the i915 driver is many years behind the competition in features and performance. It's also worth noting that some Intel GPU - GMA500 - enjoy next to no support from Intel for no apparent reason.

---

