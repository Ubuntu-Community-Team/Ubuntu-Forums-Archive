---
title: "HELP!!!---Installing wireless for Ubuntu 9.1"
date: 2010-01-12
forum: Hardware
---

### Post by jae06 on 2010-01-12
Ok I just installed Ubuntu 9.10 today and am having trouble installing my Broadcom wireless 4318.
I checked out several outlets and in each one I am ending in a dead end.
I tried installing ndiswrapper 1.55 (latest version). I get the file extracted to:
 /usr/src/ndiswrapper-1.55
then I change directories to the containing folder: /usr/src/ndiswrapper-1.55/ndiswrapper-1.55.
at this point I am changed to just my regular user account
and I type in "make" and hit enter. I receive just errors all around.

I have attached my results below.

   [COLOR=Magenta]jae@jae-laptop:/usr/src/ndiswrapper-1.55/ndiswrapper-1.55$ make[/COLOR]
  [COLOR=Magenta]make -C driver[/COLOR]
  [COLOR=Magenta]make[1]: Entering directory `/usr/src/ndiswrapper-1.55/ndiswrapper-1.55/driver'[/COLOR]
  [COLOR=Magenta]make -C /usr/src/linux-headers-2.6.31-14-generic M=/usr/src/ndiswrapper-1.55/ndiswrapper-1.55/driver[/COLOR]
  [COLOR=Magenta]make[2]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'[/COLOR]
  [COLOR=Magenta]mkdir: cannot create directory `/usr/src/ndiswrapper-1.55/ndiswrapper-1.55/driver/.tmp_versions': Permission denied[/COLOR]
  [COLOR=Magenta]  LD      /usr/src/ndiswrapper-1.55/ndiswrapper-1.55/driver/built-in.o[/COLOR]
  [COLOR=Magenta]ar: /usr/src/ndiswrapper-1.55/ndiswrapper-1.55/driver/built-in.o: Permission denied[/COLOR]
  [COLOR=Magenta]make[3]: *** [/usr/src/ndiswrapper-1.55/ndiswrapper-1.55/driver/built-in.o] Error 1[/COLOR]
  [COLOR=Magenta]make[2]: *** [_module_/usr/src/ndiswrapper-1.55/ndiswrapper-1.55/driver] Error 2[/COLOR]
  [COLOR=Magenta]make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'[/COLOR]
  [COLOR=Magenta]make[1]: *** [modules] Error 2[/COLOR]
  [COLOR=Magenta]make[1]: Leaving directory `/usr/src/ndiswrapper-1.55/ndiswrapper-1.55/driver'[/COLOR]
  [COLOR=Magenta]make: *** [all] Error 2[/COLOR]
  

I have also tried other things like the "synaptic package manager" there is nothing that resembles bcm wireless except "bcmwl-modaliases" and I don't have the option to "mark of installation" - its greyed out.

can anyone help me out? By the way I should mention that I am a complete linux newbie.
I also tried doing this as a root user ...still no luck.

I do have the windows driver downloaded to the same directory.

Again thanks in advanced with any pointers you can give me :)
Maybe I'm doing this completely wrong even...is there another way to get this downloaded?

Wireless information:

    [COLOR=Magenta]05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)[/COLOR]
  [COLOR=Magenta]        Subsystem: Hewlett-Packard Company Device 1355[/COLOR]
  [COLOR=Magenta]        Flags: bus master, fast devsel, latency 64, IRQ 20[/COLOR]
  [COLOR=Magenta]        Memory at c0204000 (32-bit, non-prefetchable) [size=8K][/COLOR]
  [COLOR=Magenta]        Kernel driver in use: b43-pci-bridge[/COLOR]
  [COLOR=Magenta]        Kernel modules: ssb[/COLOR]
  
  
  [COLOR=Magenta]05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)[/COLOR]
  
  [COLOR=Magenta]05:02.0 0280: 14e4:4318 (rev 02)[/COLOR]
   
  
Jae06

---

### Post by Ayuthia on 2010-01-12
You might first try installing b43-fwcutter.  You will need a working internet connection though.

For ndiswrapper, you might try installing ndis-gtk or ndiswrapper-common from the repositories unless you need a newer version.

As for the problem you are showing, you need to use:
```
sudo make
```because you are in /usr/src

If you are having problems with compiling as root, please post the error message that shows up when compiling.

Hope that helps.

---

### Post by kuby on 2010-01-12
I recommend to try first enabling Broadcom 4318 proprietary drivers using Ubuntu --> System --> Administration --> Hardware drivers.

I also have a 4318 wireless chipset and that was detected by ubuntu, enabling the driver was easy.

---

### Post by Ayuthia on 2010-01-12
> **kuby said:**
> I recommend to try first enabling Broadcom 4318 proprietary drivers using Ubuntu --> System --> Administration --> Hardware drivers.

I also have a 4318 wireless chipset and that was detected by ubuntu, enabling the driver was easy.

Thank you for pointing that out.  I am used to people not being able to see it through Hardware Drivers in the past so I just point them to its equivalent--b43-fwcutter.  

jae06, I agree with kuby.  You should try that option first.  If it is not there, then you can check and see if you can install b43-fwcutter.

---

