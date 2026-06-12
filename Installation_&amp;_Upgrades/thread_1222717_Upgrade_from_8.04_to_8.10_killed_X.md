---
title: "Upgrade from 8.04 to 8.10 killed X"
date: 2009-07-25
forum: Installation &amp; Upgrades
---

### Post by AndrewLeiper on 2009-07-25
Hi there,
 
I tried to upgrade from 8.04 to 8.10 but a screen came up saying only a partial update was possible. I updated much as I could but subsequent reboots only come up in command line mode.
 
I think the problem is to do with the nvidia driver. I've tried tips from various posts but nothing works. Booting with a V9 live cd works so I think if I could just get things back to using a standard driver it would work.
 
I have done the command to reset xorg.conf which now looks very basic.
 
Here is an excerpt from Xorg.0.log:
 
[SIZE=2](II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.0.0
ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) No matches found for this device in /usr/share/xserver-xorg/pci
(==) Registering 'vesa' as fallback
(==) Matched vesa for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "vesa"
(WW) Warning, couldn't open module vesa
(II) UnloadModule: "vesa"
(EE) Failed to load module "vesa" (module does not exist, 0)
(EE) No drivers available.
Fatal server error:
no screens found
 
 
 
Here is an excerpt from syslog:
 
[SIZE=2]Jul 25 11:43:54 GreatElms kernel: [ 48.963924] PCI: Setting latency timer of device 0000:00:11.5 to 64
Jul 25 11:43:54 GreatElms kernel: [ 49.479420] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 17
Jul 25 11:43:54 GreatElms kernel: [ 49.479716] NVRM: loading NVIDIA Linux x86 Kernel Module 96.43.05 Tue Jan 22 19:36:58 PST 2008
Jul 25 11:43:54 GreatElms kernel: [ 53.288835] sr 6:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 25 11:43:54 GreatElms kernel: [ 53.288841] sr 6:0:1:0: [sr0] Sense Key : Medium Error [current] 
Jul 25 11:43:54 GreatElms kernel: [ 53.288846] Info fld=0x575e9
Jul 25 11:43:54 GreatElms kernel: [ 53.288848] sr 6:0:1:0: [sr0] Add. Sense: L-EC uncorrectable error
Jul 25 11:43:54 GreatElms kernel: [ 53.288852] end_request: I/O error, dev sr0, sector 1431456
Jul 25 11:43:54 GreatElms kernel: [ 53.288856] Buffer I/O error on device sr0, logical block 178932
Jul 25 11:43:54 GreatElms kernel: [ 58.282747] sr 6:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Jul 25 11:43:54 GreatElms kernel: [ 58.282751] sr 6:0:1:0: [sr0] Sense Key : Medium Error [current] 
 
 
 
I hope someone out there can help.
 
Thanks,
 
Andy.
[/SIZE][/SIZE]

---

### Post by quixote on 2009-07-26
I don't know much about this, and I don't know if I'm telling you something you've already tried, but the last time I had problems getting my nvidia drivers sorted back out, I dug around on [Alberto Milone's]("http://albertomilone.com/wordpress/?p=212") site until I got the right drivers and the right lines in xorg.conf.

It seems you're far from alone in this problem :(.  I also saw [this site about nvidia problems after intrepid upgrades]("http://www.ubuntugeek.com/common-problems-and-solutions-for-nvidia-restricted-drivers-after-ubuntu-810-intrepid-ibex-upgrade.html"), which may or may not be any use to you.

What is the model of nvidia card that you have?

---

