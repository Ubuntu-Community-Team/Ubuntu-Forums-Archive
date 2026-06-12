---
title: "Is there any way I can decrease my CPU temp in Ubuntu?"
date: 2013-06-03
forum: Hardware
---

### Post by racie on 2013-06-03
Hello everyone.  I haven't used Ubuntu in a while, but now that it appears to be working better with the graphics card in my new laptop, I decided to come back.

I just installed 13.04 and I noticed that my fan is always on (it is only selectively on in Windows).  I installed several programs, including lm-sensors (and ran sensors-detect) fancontrol, but I'm not entirely sure what to do with these.  I then monitored the core temps using...
```
watch -n 1 -d sensors
```
...and found that the idle temp for my CPU is roughly 68C.  Now, I have an HP Envy 14 with a quad-core i7 processor and a switchable HD Radeon card (I don't remember which one), so it is going to run a bit hot.  AFAIK, Ubuntu only utilizes my lower-end Intel HD GPU.  I am fine with this and don't really need the other one for Ubuntu, but I would think that it should run cooler than it does in Windows.  Plus the fan sound is a tad irritating.

I know this is a dumb question, but is there any way I can make my laptop run cooler in Ubuntu?


It should also be noted that I have to have apci=off in order for the OS to start properly.  Would that have anything to do with it?

---

### Post by Mark Phelps on 2013-06-03
> I would think that it should run cooler than it does in Windows. 

Actually, it's the other way around with recent Linux kernel versions.  The PCs that come preinstalled with Windows do a better job of CPU load management because they have special drivers installed to do that.  Those drivers aren't available for Linux

> Plus the fan sound is a tad irritating. -- Understand -- but that's because your CPU is not dropping back to idle state as it is in MS windows.  Since it's running faster (in general), it's also running hotter -- requiring the fan to run  faster, too.

Also, Switchable Graphics is a serious problem with running Linux distos.  Some details are in the linked thread:  [http://ubuntuforums.org/showthread.php?t=1917897]("http://ubuntuforums.org/showthread.php?t=1917897")

---

### Post by ahallubuntu on 2013-06-03
~

---

### Post by Yellow Pasque on 2013-06-03
Fan control won't work without ACPI. Try "acpi_osi=Linux" instead of "acpi=off"

---

### Post by jaweinre on 2013-06-04
Check out and understand the following:
[https://01.org/powertop/](https://01.org/powertop/)
[https://launchpad.net/~linrunner/+archive/tlp](https://launchpad.net/~linrunner/+archive/tlp)

AFAIK Intel power management is pretty solid, specially on latest kernels. I wonder if the heat is actually coming from the radeon, have you tried disabling it completely through the BIOS? Makes sense anyways since you stated you're not gona be using it.

---

### Post by racie on 2013-06-04
> **Mark Phelps said:**
> Actually, it's the other way around with recent Linux kernel versions.  The PCs that come preinstalled with Windows do a better job of CPU load management because they have special drivers installed to do that.  Those drivers aren't available for Linux

 -- Understand -- but that's because your CPU is not dropping back to idle state as it is in MS windows.  Since it's running faster (in general), it's also running hotter -- requiring the fan to run  faster, too.

Also, Switchable Graphics is a serious problem with running Linux distos.  Some details are in the linked thread:  [http://ubuntuforums.org/showthread.php?t=1917897]("http://ubuntuforums.org/showthread.php?t=1917897")

I understand switchable graphics don't work well in Linux and I haven't tried the steps in the link yet.  *However*, because Ubuntu only seems to detect my Intel graphics card, I don't see why the other one would be causing any trouble.  When booting, I notice a quick "fatal error" message for my Radeon card, so I'd assume it is non-functional within Ubuntu.

And anyway, this just sounds like I might have to keep playing the waiting game.  A few distros ago, I couldn't get either of my graphics cards to work properly in Ubuntu.  Now one of them functions just fine.  When I first got my previous laptop, it was a huge PITA to try to get the WiFi card working.  A few releases later, it worked out of the box.  It always seems that the older the PC, the more compatible it is with Ubuntu.  :)

Do you think underclocking the CPU would help?  I know nothing about underclocking/overclocking...

> **ahallubuntu said:**
> To clarify, the Linux kernel certainly has drivers to drop the idle state of the CPU to low power states when the CPU is not in use.  But depending on the CPU and chipset, the Linux driver may not be optimal compared to Windows drivers.  I use Ubuntu 12.04 on several laptops and netbooks, and I do not have problems with the fan or excessive CPU heat.  On my primary Dell notebook (Core 2 Duo 2.5GHHZ), when I do something CPU-intensive (say, saving and compressing a picture I've been editing), the CPU load goes up according to my on-screen monitor, and the fan goes on and can get very loud.  As soon as the operation is over, the CPU cools down and soon the fan slows down or shuts off.  Newer CPUs like Ivybridge or Haswell may not yet be well supported by Linux kernels.

I'd definitely try to get rid of the "acpi=off" parameter if you can, as that can break lots of things e.g. suspend and power saving modes.  I suppose it could contribute to your excessive heat problem - not sure.  If you still have Windows, I'd also update the BIOS to the latest version available from HP, if there's a newer BIOS (or UEFI).
I updated the BIOS and noticed a funny new feature.  In an entry called "fan always on," it was set to "enabled."  I disabled it, but I didn't notice any change.  I would love to get rid of "acpi=off," but I wouldn't know what to do or where to begin.  On my old laptop, simply setting "nomodeset" would cause it to boot up just fine, but I just get a black screen on my current laptop if I do that.

> **Temüjin said:**
> Fan control won't work without ACPI. Try "acpi_osi=Linux" instead of "acpi=off"
As I suspected, but unfortunately "acpi_osi=Linux" does not work for me.  I have also tried "acpi_osi="Linux,"" "acpi_osi="Windows 2006,"" and simply "acpi_osi=."  Quite frankly, I'm not really sure what all of these options do, but I've seen them on the 'net at one point or another.

> **jaweinre said:**
> Check out and understand the following:
[https://01.org/powertop/](https://01.org/powertop/)
[https://launchpad.net/~linrunner/+archive/tlp](https://launchpad.net/~linrunner/+archive/tlp)

AFAIK Intel power management is pretty solid, specially on latest kernels. I wonder if the heat is actually coming from the radeon, have you tried disabling it completely through the BIOS? Makes sense anyways since you stated you're not gona be using it.
There is not an option to disable it through the BIOS, and I have no intention of doing so.  Perhaps I should have specified that I *do* currently use it in Windows.  I just don't mind it not working in Linux.

And I'm not entirely sure how to use PowerTop.  All I know is that I can toggle a list of items between "bad" and "good."  Mind pointing in the right direction?
TLP looks interesting, but I'm afraid to alter some of the settings because they need me to remove Ubuntu's default power saving settings or something.

I will say that for PowerTop,  I tried the command
```
sudo powertop -html
```
and it outputted an interesting file for me.  I found this inside:
> S[B]oftware Settings in need of Tuning
[/B]
Wireless Power Saving for interface wlan0	iw dev wlan0 set power_save off
Enable SATA link power management for /dev/sda	echo 'min_power' > '/sys/class/scsi_host/host0/link_power_management_policy';
Runtime PM for PCI Device Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1	echo 'auto' > '/sys/bus/pci/devices/0000:00:1d.0/power/control';
Runtime PM for PCI Device NEC Corporation uPD720200 USB 3.0 Host Controller	echo 'auto' > '/sys/bus/pci/devices/0000:0b:00.0/power/control';
Runtime PM for PCI Device Advanced Micro Devices [AMD] nee ATI Whistler [Radeon HD 6600M/6700M/7600M Series]	echo 'auto' > '/sys/bus/pci/devices/0000:01:00.0/power/control';
Runtime PM for PCI Device Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller	echo 'auto' > '/sys/bus/pci/devices/0000:00:1f.3/power/control';
Runtime PM for PCI Device Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller	echo 'auto' > '/sys/bus/pci/devices/0000:00:1f.2/power/control';
Runtime PM for PCI Device Intel Corporation HM65 Express Chipset Family LPC Controller	echo 'auto' > '/sys/bus/pci/devices/0000:00:1f.0/power/control';
Runtime PM for PCI Device Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 8	echo 'auto' > '/sys/bus/pci/devices/0000:00:1c.7/power/control';
Runtime PM for PCI Device Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5	echo 'auto' > '/sys/bus/pci/devices/0000:00:1c.4/power/control';
Runtime PM for PCI Device Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1	echo 'auto' > '/sys/bus/pci/devices/0000:00:1c.0/power/control';
Runtime PM for PCI Device Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port	echo 'auto' > '/sys/bus/pci/devices/0000:00:01.0/power/control';
Runtime PM for PCI Device Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port	echo 'auto' > '/sys/bus/pci/devices/0000:00:01.1/power/control';
Runtime PM for PCI Device Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port	echo 'auto' > '/sys/bus/pci/devices/0000:00:01.2/power/control';
Runtime PM for PCI Device Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller	echo 'auto' > '/sys/bus/pci/devices/0000:00:02.0/power/control';
Runtime PM for PCI Device Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1	echo 'auto' > '/sys/bus/pci/devices/0000:00:16.0/power/control';
Runtime PM for PCI Device Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2	echo 'auto' > '/sys/bus/pci/devices/0000:00:1a.0/power/control';

Clearly it recommends some changes for me, but I don't know what to do.

---

### Post by Yellow Pasque on 2013-06-04
What exact model of Envy 14 do you have? Check for BIOS/EFI update. [http://h10025.www1.hp.com/ewfrf/wc/siteHome?cc=us&lc=en](http://h10025.www1.hp.com/ewfrf/wc/siteHome?cc=us&lc=en)

---

### Post by racie on 2013-06-04
> **Temüjin said:**
> What exact model of Envy 14 do you have? Check for BIOS/EFI update. [http://h10025.www1.hp.com/ewfrf/wc/siteHome?cc=us&lc=en](http://h10025.www1.hp.com/ewfrf/wc/siteHome?cc=us&lc=en)

Hi.  I already tried a BIOS update.  (See the post above yours.)

---

### Post by Yellow Pasque on 2013-06-04
It's worth a try to write HP and tell them their BIOS is borked, but I wouldn't expect anything beyond the standard "we only support Windows" response, especially if dealing with a low-level tech support drone.

If you're using the open-source radeon driver, setting it to "low" might help: [http://www.x.org/wiki/RadeonFeature#KMS_Power_Management_Options](http://www.x.org/wiki/RadeonFeature#KMS_Power_Management_Options)

---

### Post by racie on 2013-06-05
> **Temüjin said:**
> It's worth a try to write HP and tell them their BIOS is borked, but I wouldn't expect anything beyond the standard "we only support Windows" response, especially if dealing with a low-level tech support drone.

If you're using the open-source radeon driver, setting it to "low" might help: [http://www.x.org/wiki/RadeonFeature#KMS_Power_Management_Options](http://www.x.org/wiki/RadeonFeature#KMS_Power_Management_Options)

Why would you assume it's a problem with the BIOS?  I have the boot parameter "acpi=off," which I suspect may be part of the problem.

I was of the opinion that my Radeon card simply does not function, but I have just noticed [this](http://ubuntuforums.org/showthread.php?t=1930450) thread, which luckily states otherwise.  I will have to try these steps later and see if anything happens.

---

### Post by Yellow Pasque on 2013-06-05
> Why would you assume it's a problem with the BIOS? 
The system-specific ACPI tables are a part of the BIOS. 

> I have the boot parameter "acpi=off," which I suspect may be part of the problem.
Disabling ACPI is probably a large portion of your problem...

---

