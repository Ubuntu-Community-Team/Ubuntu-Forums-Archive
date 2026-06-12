---
title: "Ubuntu is a non go on my new PC!"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by Galban on 2009-02-06
**[COLOR="Red"]*_SOLVED_*[/COLOR]**

[COLOR="Blue"]Update[/COLOR]: *It was about the ATI's hybrid crossfire.I have to disabled it from the BIOS in order to get Ubuntu installed and adjust the driver thereafter in order to get crossfire working. The bad news is that the MOBO's configuration required to get crossfire running on Ubuntu, it does not work for windows and vice versa. Sadly it is all about to the probably impossibility to have the same order/sequence for the master adapter and the secondary adapter in both ATI's drivers for each OS  *

Hello. I need help and ideas. I've been unable to install Ubuntu (and any other distro) on a rig that I have assembled few days ago. The install process always ends  freezing right at the beginning.  Using different kinds of methods all of them shows signs that the kernel doesn't understand nor like a piece of hardware. A blank screen with a blinking white dot takes for ever right after hitting "enter" for installing or as a live CD. All depends on how I try to get it, the "blinking dot" will change for "loading, please wait", or for an "aperture beyond 4Gb. Ignoring".

When erasing the "quiet splash" at the boot options it shows a lot more than that but it ends by freezing any ways. The curious thing is when doing it like that you can see/read it is like the kernel is activating one by one the cores of the CPU (4), but the process on the 4th one seems to don't be finalized when it ends by freezing. 

Here a description of the hardware been used (none of them being over-clocked):

* Foxconn A7DA-S (bios P06)
* AMD Phenom II X4 940 3Ghz
* 4Gb Kingston HyperX DDR2 HKX8500D2K2/4GR
* Western Digital Caviar SE WD3200AAJS 320GB 7200 RPM 8MB Cache  SATA 3.0Gb/s
* hec ZEPHYR HEC-750DR-AT 750W PSU
* Asus EAH3450 GPU hybrid crossfires with the HD3300 IGP.

NOTE: Memtest86+ pass at 800Mhz and 1066Mhz. Windows7 Beta up and running without any problems

So then.. any hints or ideas, because that beta is not for ever and I don't want to buy windows when Ubuntu had been so good for years on my old Athlon PC. Please Help! :(

[COLOR="Blue"]**Here a picture of the last screen when erasing "quiet-spalsh" and adding "iommu=noaperture" as options for boot, and prior to the install to freeze.**[/COLOR]

---

### Post by Niniel on 2009-02-06
Try searching for the aperture error.
You'll find all kinds of things, such as [http://ubuntuforums.org/showthread.php?t=963892]("http://ubuntuforums.org/showthread.php?t=963892")

---

### Post by Coreigh on 2009-02-06
Does the BIOS information look right? Does the BIOS report everything correctly and as expected? Does the Windows hardware manger or event log offer any clues such as hardware not showing up or reporting as wrong size or as "unidentified"?

You might try removing as much extra hardware as possible. Install the minimum RAM, and try changing sticks and slots. Is the machine multi-processor or only multi-core? Can you remove etra processors or disable them in BIOS? Try running the machine on MINIMUM resources. That may show faulty hardware or at least identify where the install process fails, specifically.

Finally I know you indicated that you tried other distros but have you tried older versions or mini-distros like puppy or DSL?

Oh one more, have you reviewed the hardware compatibility list? 
[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)

---

### Post by estyles on 2009-02-06
Do you know what revision your BIOS firmware is?  Foxconn had a problem where they were completely hosing Linux OS's, which was discovered by a board-member and finally fixed after a lot of back-and-forth with the company.  If the motherboard was made more than about 6 months ago, that *might* be the issue - you should be able to download a BIOS flash from Foxconn.

I'm not sure that's the problem, but maybe...

---

### Post by ByteJuggler on 2009-02-06
> **Niniel said:**
> Try searching for the aperture error.
You'll find all kinds of things, such as [http://ubuntuforums.org/showthread.php?t=963892]("http://ubuntuforums.org/showthread.php?t=963892")

It's not clear that the hanging/crashing is neccesarily related to the aperture error message, although it may be.  Suffice it to say, I also have that message on my older AMD 64-bit setup but the system still boots fine regardless.

---

### Post by estyles on 2009-02-06
> **ByteJuggler said:**
> It's not clear that the hanging/crashing is neccesarily related to the aperture error message, although it may be.  Suffice it to say, I also have that message on my older AMD 64-bit setup but the system still boots fine regardless.

Yeah, what he said.  My wife's PC had that error and wouldn't boot, but it turned out to be a red herring.  I'm trying to remember how I fixed it...  I think there's an option for booting the kernel with ACPI turned off.  I don't remember how to do that, but if you can boot with ACPI=off as a kernel option, and it works, then that means that it *is* likely a problem with your BIOS firmware.

---

### Post by Niniel on 2009-02-06
True, but it's a good starting point. :)
But maybe estyle's excellent advice will solve the problem.

---

### Post by ByteJuggler on 2009-02-06
> **estyles said:**
> Yeah, what he said.  My wife's PC had that error and wouldn't boot, but it turned out to be a red herring.  I'm trying to remember how I fixed it...  I think there's an option for booting the kernel with ACPI turned off.  I don't remember how to do that, but if you can boot with ACPI=off as a kernel option, and it works, then that means that it *is* likely a problem with your BIOS firmware.

Yep, :)  In my experience hangs and crashes usually have more to do with various slightly problematic BIOS's and so on, and particularly with ACPI and APIC support.  You might want to bookmark [this]("http://www.kernel.org/doc/Documentation/kernel-parameters.txt").

Then you might want to add one or more of the following (in turn) onto your kernel boot line (Off the top of my head: While in Grub, press "e" to edit the menu entry, then select the line to edit, press "e" again, etc.):

acpi=off
noapic
nolapic
nox2apic

There's probably others that may be worth a try, but those would be my first/best guesses.

---

### Post by Galban on 2009-02-06
> **estyles said:**
> Yeah, what he said.  My wife's PC had that error and wouldn't boot, but it turned out to be a red herring.  I'm trying to remember how I fixed it...  I think there's an option for booting the kernel with ACPI turned off.  I don't remember how to do that, but if you can boot with ACPI=off as a kernel option, and it works, then that means that it *is* likely a problem with your BIOS firmware.

[COLOR="Black"]estyles[/COLOR] It sounds like a logical possibility. The option for ACPI turned off on the boot it is "noapic", that's it. I will try out that and give you news.Another question; when you say BIOS firmaware are we talking about the software version to flash the CMOS being used or the version of the BIOS itself? For the record until today, February 6th, P06 BIOS version is the lastest. And thanks to all other that have also answered and those to come!

---

### Post by ByteJuggler on 2009-02-06
> **Galban said:**
> The option for ACPI turned off on the boot it is "noapic", that's it. 

Umm, **no**, be careful, *ACPI *is not the same as **APIC**.  

ACPI stands for Advanced Configuration and Power Interface.

APIC stands for Advanced Programmable Interrupt Controller

They're different things (hence the different options I listed) but both can sometimes cause trouble.

---

### Post by ByteJuggler on 2009-02-06
Aside: It would probably be very good if you can post a bug report about this.  Good luck.

---

### Post by Galban on 2009-02-06
Thanks ByteJuggler for that remark. Appreciated!

---

### Post by stchman on 2009-02-06
Try the safe graphics mode.  I had to use it to install on my new PC.

---

### Post by Tomatz on 2009-02-06
Try the alternate cd?

---

