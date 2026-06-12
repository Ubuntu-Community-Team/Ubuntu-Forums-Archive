---
title: "ndiswrapper &amp; belkin f5d6020 help"
date: 2005-12-05
forum: Hardware &amp; Laptops
---

### Post by sean12345 on 2005-12-05
Hi all,

***Background**
  I am a complete newbie and have just installed breezy on a t22 thinkpad.  I use acpi=off so that my ethernet card will work.  I have a belkin f5d5060 ver 3 card that I would like to get working.

I have found the thread concerning this card and I tried following the instructions.
-use mix of realtek and belkin .inf and .sys, replace bel6020 with rlt8081 etc.

thread here - [http://www.ubuntuforums.org/showthread.php?t=61717&highlight=F5D6020](http://www.ubuntuforums.org/showthread.php?t=61717&highlight=F5D6020)

I also installed ndiswrapper -utils via the package manager

*problem*

ndiswrapper is giving me an error when I try to use modprobe.
here is the terminal ouput

becca@Beccascomp:~$ sudo ndiswrapper -i /home/belkin drivers/bel6020.inf
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-hotplug          (Re)Generate hotplug information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
becca@Beccascomp:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

I also tried useing both files from the belkin cd, and then both files from the realtek website.

Any help would be greatly appreciated
Thanks

---

