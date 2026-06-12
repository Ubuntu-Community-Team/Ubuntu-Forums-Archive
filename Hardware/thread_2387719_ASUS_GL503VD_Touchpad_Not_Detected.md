---
title: "ASUS GL503VD Touchpad Not Detected"
date: 2018-03-22
forum: Hardware
---

### Post by myss2 on 2018-03-22
Hi guys, two days ago I've bought a new ASUS ROG GL503VD laptop. Naturally it came with preinstalled Windows 10 and I decided to just remove that stuff right away, had some problems tweaking it to load Linux properly but managed to do it in the end.
Had to set acpi_osi=! in order to let me run graphic drivers, but all in all, I've managed to make it working. Now the only problem I'm having, and quite a big one though is that touchpad is not being detected. I can plug in external mouse but this is not best solution always. Might be useful to note that keyboard works fine.

```

$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; ITE Tech. Inc. ITE Device(8910)             id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; USB2.0 HD UVC WebCam: USB2.0 HD             id=13    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=15    [slave  keyboard (3)]
    &#8627; ITE Tech. Inc. ITE Device(8910)             id=17    [slave  keyboard (3)]


$ synclient
Couldn't find synaptics properties. No synaptics driver loaded?

```

Things I've tried:
- [COLOR=#000000]i8042 flags on startup
- different operating systems, Debian 9, Ubuntu 16.04, 16.04 GNOME, Ubuntu 17.10, Kali 2018.1
- different kernel versions, starting from 4.9 to stable mainline 4.15 but will try to update it to latest RC tomorrow
- mtrack input drivers

Being without ideas, I've reinstalled Windows on secondary drive and installed touchpad drivers there, and it says my touchpad is the following; ASUS Precision Touchpad (obviusly just generic name for drivers)
When I check driver events, it mentions the driver is ELAN. Also the touchpad works out of box on Windows 10, through hidi2c.inf driver.

Was reading on several sites that if xinput doesn't lists my device, means generally I have to wait for Linux kernel to support it. This is a pretty new laptop and I've read that on some ASUS devices it took two years for support to come to Linux. I gave more than 1000€ for this laptop and would rather not depend on someone may or may not adding this to kernel one day. Anybody has some ideas or advices what to do here? [/COLOR]:roll: :roll: :roll:

---

### Post by feelnopain on 2018-04-07
Hi, I have the same problem with Linux, the touchpad is not working, not even detected in xinput

---

### Post by meleeikon on 2018-04-07
If it is an Elantech one, support is junk. I can't even find the company that makes the touchpad to ask them to build linux drivers.

---

### Post by myss2 on 2018-04-10
ELAN1200 according to Windows

---

### Post by mario-milanesio on 2018-04-16
same for me, same problems, with ubuntu and with manjaro.
mine is a GL703VD, so identical but 17.3''

hope someone will solve...

---

### Post by mörgæs on 2018-04-17
Have you tried 18.04 (beta)?

---

### Post by myss2 on 2018-04-25
Just tried live 18.04 with boot flags I have on my current installation, still the same problem.

---

### Post by maxime+t on 2018-06-20
Hi everyone,

I'm late in this discussion but I think I have a solution for those who are in the same case than myss2 and me before.
I had exactly the same issue on my Asus FX503VD with the same config. I tried everything I found on several forums without success... until today!

If you get one of the **latest kernel** (4.17.2 for me) **and** **remove the kernel parameter 'acpi_osi=!'** you should find the elantech touchpad with xinput and use it (for years I hope...) without bugs with the screen backlight... et voilaaaa!

Sorry for my frenglish.

Maxime

---

### Post by feelnopain on 2018-06-29
I can confirm that using latest kernel 4.17.3 in my case and removing acpi_osi=! and acpi_osi="Windows 2009" from grub makes the touchpad work

---

### Post by marclandolt on 2018-07-10
On ASUS ROG Strix SCAR GL703GE-EE010T the touchpad does not work, not even with Bios Update and Kernel 4.17 :(

---

### Post by feelnopain on 2018-07-30
It worked until first reboot, then I got black screen everytime I booted without the acpi_osi settings. Back to acpi_osi=! and acpi_osi="Windows 2009" and no touchpad

---

