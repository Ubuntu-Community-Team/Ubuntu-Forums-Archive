---
title: "Booting from CD hangs at Bluetooth"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by KuroKuroKuro on 2009-02-17
Okay, this is my first attempt at using Ubuntu/Linux ever. Yesterday my Vista decided to give me some troubles to do with the User Profile Service... Luckily after using Safe Mode and using Regedit I managed to fix that, but my boyfriend suggested that I should create an Ubuntu boot from CD disk just in case I should ever need one.

So I've downloaded ubuntu-8.10-desktop-i386.iso and burnt it to a CD-R. I used the winMD5sum to check the hash of the iso, and also I've checked for defects on the CD from the menu that boots up with the CD and everything seems fine there.

The issue is that when I try to boot from the CD it ultimately seems to hang when it gets to "Starting Bluetooth". After restarting again and looking around online (using Vista) I found some advice that told to hit F6 to change the options by removing "quiet splash" from the line to not show the orange bar and instead more information about what was loading.


So it progresses again hanging at the same place: "Starting Bluetooth".
The line that I see last is:
```
[  240.400353]  pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_cSum
```

I have no idea what that means, or whether it's any use to any one reading, but it's what I know.

My computer is a HP Pavilion S3541 (a slimline desktop) with Intel Core2 Duo CPU 2.60GHz with 3Gb RAM. I don't think I even have Bluetooth (Device Manager seems to back me up on that) which I'm guessing is possibly part of the problem?


Hope that's enough information (or not too much), and that somebody knows something that can help me! (I'm a complete noob when it comes to Linux)

Thanks in advance. :)

---

### Post by dstew on 2009-02-17
The problem is that the Live CD kernel has modules (drivers) in it that aren't working well with your hardware. It may have nothing to do with Bluetooth, but it may be that some module is accessed first when Bluetooth services are started, causing the hang-up.

To get a clue, look back farther in the output of kernel messages. See if there are any errors higher up on the display. One module that frequently causes problems is the APCI module. You can disable it by adding **acpi=off** to the kernel line the same way you removed **quiet** and **splash**. Another source of trouble is the advanced interrupt control processor (APIC -- not to be confused with APCI!). To turn off the interrupt module, you add the parameters **noapic** **nolapic** to the kernel line. If you error messages suggest some other module, post back.

You can also try a different version of Ubuntu. Each version uses different modules, and sometimes one works better than another.  If you are using 8.10, then try 8.04 instead.

---

