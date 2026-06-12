---
title: "acpi and fnfxd not working on toshiba A70 PIV"
date: 2006-03-22
forum: Hardware &amp; Laptops
---

### Post by cantormath on 2006-03-22
Hello everyone, I need a direction and a little instruction....

1st
lshw and dmesg files are below:
[lshw]("http://vwsporttech.com/lshw.html")
[dmesg]("http://vwsporttech.com/dmesg.html")

I have a Toshiba A70 with a Pentium IV 3.06 mhz chip, ATI Radeon AGP(9100 IGP) etc... video card.  These two things have been a combination of problems.

issue:
I have the not so uncommon problem of my ACPI not working properly.  Breezy has been the closest, ie battery meter works, and warns me when power is low and screen will shut off after none use.  The problem is I am not able to hibernate and my fan runs twice as much as it does under windows, an on going problem with this laptop.  I have tried install the fnfxd and fnfx-client, but it fail to intiate because there is no "proc/acpi/toshiba" file......  From what I can tell, my acpi seems to be picking up alright, so I can't tell what's going wrong.
Note: I have toshset install (installed on installation) no toshutils (wasn't installed on installation) and fnfxd was not installed on installation.

The people at [Fnfx]("http://fnfx.sourceforge.net/index.php?section=doc") say:
[I][INDENT]
"To check if ACPI and ACPI Toshiba support are enabled check the following proc entries exists:
/proc/acpi
/proc/acpi/toshiba
-If they do exist, FnFX will work on that system. If they do not exist try `modprobe toshiba_acpi' as root. If this throws errors like 'FATAL: Module toshiba_acpi not found' the kernel is most likely not compiled with CONFIG_ACPI and CONFIG_ACPI_TOSHIBA.
-Please recompile your kernel with the ACPI drivers or have a look for a precompiled kernel for your distribution which has ACPI and ACPI Toshiba support."[/INDENT][/I]
I urname -r:
[I][INDENT]cantormath# uname -r
2.6.12-10-386[/INDENT][/I]
so I modprobe as root:
[I][INDENT]cantormath# modprobe toshiba_acpi
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.12-10-386/kernel/drivers/acpi/toshiba_acpi.ko): No such device[/INDENT][/I]
so either toshiba_acpi is not there, or it is there and cannot be inserted..?
I have no idea, so, I came to the forum ::grin::
Please help or tell me what you need to know to help.. ](*,) 

My video card problems are for another post...

cantormath...

---

### Post by cantormath on 2006-03-25
wow,

not the hottest topic.....
is this post in the wrong place?

---

### Post by ranf on 2006-03-25
Maybe you find some helpful info:
[http://tuxmobil.org/toshiba.html](http://tuxmobil.org/toshiba.html)
[http://linux-on-laptops.com/toshiba.html](http://linux-on-laptops.com/toshiba.html)

---

### Post by cantormath on 2006-04-06
Both of those site mentioned do not have acpi working nor do they install on ubuntu

---

### Post by mjg59 on 2006-04-06
If toshiba_acpi does not load, then it implies that you have a Toshiba with slightly different ACPI functionality. The only thing that this really loses you is hotkey support - the toshiba_acpi driver isn't used in suspend/resume.

---

### Post by mdmarmer on 2006-04-06
This laptop probably has a Phoenix BIOS.  The Toshiba utilities are intended for Toshiba with Toshiba BIOS.  Get any available BIOS update from the Toshiba site -- it may help.

Also notes on this laptop for other distros will be largely applicable to Ubuntu.

There is an Ubuntu laptop wiki here but it has only limited info for Toshiba A70

 [https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsToshiba](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsToshiba)
Here's the testing page but it doesn't have much either:
[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteA70](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteA70)

Mike

---

### Post by cantormath on 2006-04-06
I dont have the phoenix bios.

I am talking about suspend and hibernate, acpi seems to show me battery etc......
cpufreq also seems to be working.....
hibernate does nothing.......
suspend does suspends, but when it comes back, the screen does not come back on.....
any info is welcome.....

also, my other problem is everything in this laptop is ATI
lspci
Host bridge: ATI Technologies Inc RS300 Host Bridge (rev 02)
PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
SMBus: ATI Technologies Inc ATI SMBus (rev 18)
IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
ISA bridge: ATI Technologies Inc: Unknown device 434c
 PCI bridge: ATI Technologies Inc: Unknown device 4342
 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]

ati/acpi hell.............actually, just the vid card is a pain...

---

### Post by cantormath on 2006-07-30
> **mdmarmer said:**
> This laptop probably has a Phoenix BIOS.  The Toshiba utilities are intended for Toshiba with Toshiba BIOS.  Get any available BIOS update from the Toshiba site -- it may help.

Also notes on this laptop for other distros will be largely applicable to Ubuntu.

There is an Ubuntu laptop wiki here but it has only limited info for Toshiba A70

 [https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsToshiba](https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsToshiba)
Here's the testing page but it doesn't have much either:
[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteA70](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteA70)

Mike

I have a toshiba bios with software v1.50

---

