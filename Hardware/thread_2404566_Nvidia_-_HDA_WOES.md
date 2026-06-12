---
title: "Nvidia - HDA WOES"
date: 2018-10-25
forum: Hardware
---

### Post by markackerman8@gmail.com on 2018-10-25
OK,

This is a new thread, and I will make it HUGE!
**Edit Solution/ Work Around for the "2/" Problem**
see Post # 4, Thanks PeterSaints :guitar:

Ubuntu, Please Listen!

Nvidia, HDA WOES in the Title ... HDA stands for High Definition Audio, or HDMI Audio,  or Surround Sound 5.1-7.1  etc. ...
NVHDA stands for Nvidia HDA.  Just for anyone who does not know the Jargon! :p

What does Work ... (and I will post ALL my Notes and Links for others below!)
1/  Everything AFTER STUPIDLY!, I need to install a Kernel PATCH! and 
2/ A STUPIDLY Necessary Restart after ANY Hibernation or Suspend!

First my System, and most importantly is it is a NEW Cutting Edge Hp Omen X Laptop with a Nvidia GTX 1080m GPU, and the latest Linux 3.18 Kernel!
> -Computer-
Processor		: Intel(R) Core(TM) i7-7820HK CPU @ 2.90GHz
Memory		: 16245MB (3330MB used)
Machine Type		: Notebook
Operating System		: Ubuntu 18.10
-Display-
Resolution		: 1920x1080 pixels
OpenGL Renderer		: GeForce GTX 1080/PCIe/SSE2
X11 Vendor		: The X.Org Foundation

-Audio Devices-
Audio Adapter		: HDA-Intel - HDA Intel PCH
Audio Adapter		: HDA-Intel - HDA NVidia
-Input Devices-

 Video Bus
 ST LIS3LV02DL Accelerometer
 HDA Intel PCH Mic
 HDA Intel PCH Mic
 HDA Intel PCH Headphone
 HP WMI hotkeys
 HDA NVidia HDMI/DP,pcm:3
 HDA NVidia HDMI/DP,pcm:7
 HDA NVidia HDMI/DP,pcm:8


So the LATEST 2 Problems I am looking for a SOLUTION that would indeed help THOUSANDS and/or MILLIONS of people Now and/or in the near future! :P
1/  Why SHOULD I need to apply a PATCH to a YEAR old KNOWN problem!
and MORE IMPORTANTLY!

2/  Why is the fixed Patch System NOT working after a Suspend or Hibernation
(Yes I am reiterating my issue once again!)
After EITHER a Suspend or Hibernation, the HDA Sound is EITHER, 
1/ Not VISIBLE AGAIN! ANYWHERE! Trust me, or :confused:
2/ Visible but in a Dysfunctional State, ... Showing 3 version of the NVHDA 0,1&2 ...
and NONE of the 3 (three) WORK! to be clear NO SOUND AT ALL! when testing them. :confused:

So I will leave it here, and to show my continued Good Faith and Obvious Continued Support For Ubuntu, below are ALL my Solutions to Date!

**1st Solution** -  
Install the patch to get the INVISIBLE and/or Unloaded HDA Visible and/or Loaded
&#8728; I can confirm that kernel module, posted by 
&#8227; Maik Freudenberg ([https://bugs.freedesktop.org/show_bug.cgi?id=75985#c27](https://bugs.freedesktop.org/show_bug.cgi?id=75985#c27)),
• Kernel module to toggle audio function
&#8728;  is working fine on my system. Thank you for the fix. The HDMI audio device now works as it should (now detected).
&#8728; The steps I did to enable HDMI audio device:
• 1. Download and extract the file nvhda.tar.xz.  (from above link)
• 2. Run these commands in Terminal,  in the location of the extracted folder 
```
• $ make
• $ sudo make install
• $ echo nvhda | sudo tee -a /etc/initramfs-tools/modules
• $ echo "options nvhda load_state=1" | sudo tee /etc/modprobe.d/nvhda.conf
• $ sudo update-initramfs -u
``` 
&#8227; 3. Reboot.
## SOLVED #################################################################

**2nd Solution**
Hibernation/Suspend Working (Not HDA Sound of Course)

 Troubleshooting
&#8227; Prerequisites - does your kernel support suspend-to-disk?
• Kernel supports whatever is listed in /sys/power/state, so:
```
cat /sys/power/state
```
&#8728; Allowed (to my knowledge) entries there include: mem, standby, freeze, disk. Explanation:
&#8227; mem -        has several meanings, which one exactly on your system you'll find out via cat /sys/power/mem_sleep. I have: s2idle [deep]
&#8227; standby -   Power-On Suspend (if supported)
&#8227; freeze -     Suspend To Idle (STI)
&#8227; disk -          Hibernate -  Suspend To Disk (STD),  This - you want.
&#8728; mine says :  freeze mem disk - PERFECT!

• Then we need to check
```
$ cat /sys/power/disk
```
&#8227; If (good) shows ... 
&#8227; [platform] shutdown reboot suspend test_resume  

• if : (Bad)
• [disabled]   
• (not very good)
&#8227; Enable Hibernate and put it in menu - Easy-Peasy

• Software Prerequisites
 ```
sudo apt install pm-utils  cpufrequtils
```

1. Edit a specific file with this command.
```
 sudo gedit /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla
```

&#8728; 2. Scroll down the Text Document and find the below sections:
 > [Disable hibernate by default in upower]
 >  [Disable hibernate by default in logind]

&#8227; Change both the values from no to yes in:
 > ResultActive=no (change this to yes)

• Save, Exit & Reboot - Done!

• To test if hibernate works in your computer by running command:
```
 sudo pm-hibernate
```
• After you computer turns off, switch it back on.
&#8227;  Did your open applications re-open? If so it works, if not then hibernate does not work.  You can check if your Swappiness partition is at least as large as your available RAM, as it may solve the problem. 

**3rd Solution**
ACPI Woes Bandaid FIX,
ACPI stands for Advance Configuration and Power Interface **(Thunderbolt)**
If you are getting a ZILLION ACPI Errors of any kind
ex. Error:   
> ACPI:3400 Unsupported Event

&#8227; Here is a surprisingly simple solution that solved both problems (fast startup and normal background)
&#8227; Try disabling acpi in /etc/default/grub change this variable so it looks like this:
```
 sudo gedit /etc/default/grub 
```
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=strict",

• Just add acpi=off  (caused problems), "acpi=strict" Did NOT cause these problems
• (used for acpi INT34000 Errors but resulted in 800x600 resolution PROBLEM)

• Make sure to
```
sudo update-grub2
```, after modifying the file and before rebooting
• and reboot
 **Problems Controlled if not Solved :D**

Other notes on this issue (not tried on my system but may help yours) :P
&#8728;  Sometimes you see "ACPI: EC: input buffer is not empty, aborting transaction". This is a problem with ACPI, more specifically an incompatibility of the BIOS. There may be four ways to solve this issue:
&#8227; 1/ If available, update the BIOS.
&#8227; 2/ Use acpi=off (acpi=strict WORKS BEST) as kernel parameter, however this will kill all ACPI functionality like battery charging and power saving.
&#8227; 3/ In some cases disabling DPMS has been reported to solve the issue [1]. However, screen brightness may no longer be fully controllable:
• $ xset dpms force off
&#8227; 4/ Build a custom kernel with patches

---

### Post by oldos2er on 2018-10-25
I'm not sure who you're addressing with "Ubuntu, Please Listen," but developers rarely to never post here. Forum staff are all volunteers, not Canonical employees.

To report bugs, please see [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by markackerman8@gmail.com on 2018-10-25
OK  I WILL PUT IT THERE,

Yet Once Again,

Just trying to help get it some attention, this effects SO MANY PEOPLE!!!

and Just trying to Help, Mark

---

### Post by markackerman8@gmail.com on 2018-10-25
**A Solution to the Hibernating/Suspend Issue**
Thanks to PeterSaints  :guitar:
[HTML]https://mail.google.com/mail/u/0/?tab=wm#inbox/FMfcgxvzLNWRlqwRKSFSvkfCBHLngvrP[/HTML]

However, if I manually disable the NVHDA Module **BEFORE** I put it to Sleep/Suspend or Hibernate
```
sudo tee /proc/acpi/nvhda <<< OFF
```"

I then have to turn it on again **AFTER** I resume with 
```
sudo tee /proc/acpi/nvhda <<< ON
```

 I'm then able to get it to Suspend/Hibernate and Resume with Total Functionality :p

To be clear NVHDA COMES BACK PROPERLY!  :p

Always Trying to help, Mark

---

### Post by markackerman8@gmail.com on 2018-10-26
So I guess We All know ** NOW** that this HDA Sound Issue(s) has to do with a **DEEPER** Ubuntu's Dysfunctionality ... AGAIN ... AGAIN with ...

ACPI Problems (and Ubuntu), :(

Who Would have known that ...

Nvidia's NVHDA  through the HDMI Port is ALSO tied with the ACPI (Advanced Configuration and Power Input) Port? and therefor **Ubuntu ISSUES** [to reiterate]

Thanks again to PeterSaints and his solution from
[HTML]https://mail.google.com/mail/u/0/?tab=wm#inbox/FMfcgxvzLNWRlqwRKSFSvkfCBHLngvrP[/HTML]

----------------------------------------

Live and Learn

---

### Post by markackerman8@gmail.com on 2018-10-26
OK So for the Heck of it I ONCE AGAIN Google Searched

"Ubuntu ACPI Problems Solved"

and these issues have been around for at least 7 years, 
[https://ubuntuforums.org/showthread.php?t=1882050](https://ubuntuforums.org/showthread.php?t=1882050)
November 16th, 2011
from Don't get me wrong but perhaps it is just particular to just this laptop (HP) and Quite a few others but NOT ALL,

So here is a suggestion from 2011
```
$ dmesg | grep -i acpi
[    0.000000] BIOS-e820: [mem 0x000000004183d000-0x000000004183dfff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x000000004f5f5000-0x000000004f659fff] ACPI data
[    0.000000] BIOS-e820: [mem 0x000000004f65a000-0x000000004fb13fff] ACPI NVS
[    0.000000] efi:  ACPI 2.0=0x4f611000  ACPI=0x4f611000  SMBIOS=0x4feb4000  SMBIOS 3.0=0x4feb3000  ESRT=0x4d07bd18  MEMATTR=0x4d06e018 
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x000000004F611000 000024 (v02 HPQOEM)
[    0.000000] ACPI: XSDT 0x000000004F6110C8 00010C (v01 HPQOEM SLIC-MPC 01072009 HP   00010013)
[    0.000000] ACPI: FACP 0x000000004F647D18 000114 (v06 HPQOEM SLIC-MPC 01072009 HP   00010013)
[    0.000000] ACPI: DSDT 0x000000004F611260 036AB3 (v02 HPQOEM 83A5     01072009 ACPI 20160422)
[    0.000000] ACPI: FACS 0x000000004FADFF00 000040
[    0.000000] ACPI: APIC 0x000000004F647E30 0000BC (v03 HPQOEM 83A5     01072009 HP   00010013)
[    0.000000] ACPI: FPDT 0x000000004F647EF0 000044 (v01 HPQOEM 83A5     01072009 HP   00010013)
[    0.000000] ACPI: FIDT 0x000000004F647F38 00009C (v01 HPQOEM 83A5     01072009 HP   00010013)
[    0.000000] ACPI: MCFG 0x000000004F647FD8 00003C (v01 HPQOEM 83A5     01072009 HP   00000097)
[    0.000000] ACPI: SSDT 0x000000004F648018 000359 (v01 HPQOEM 83A5     00001000 ACPI 20160422)
[    0.000000] ACPI: SSDT 0x000000004F648378 0047A8 (v02 HPQOEM 83A5     00001000 ACPI 20160422)
[    0.000000] ACPI: MSDM 0x000000004F64CB20 000055 (v03 HPQOEM SLIC-MPC 00000001 HP   00010013)
[    0.000000] ACPI: SSDT 0x000000004F64CB78 003156 (v02 HPQOEM 83A5     00003000 ACPI 20160422)
[    0.000000] ACPI: SSDT 0x000000004F64FCD0 0026B8 (v02 HPQOEM 83A5     00001000 ACPI 20160422)
[    0.000000] ACPI: HPET 0x000000004F652388 000038 (v01 HPQOEM 83A5     00000001 HP   0000005F)
[    0.000000] ACPI: SSDT 0x000000004F6523C0 0008FE (v02 HPQOEM 83A5     00000000 ACPI 20160422)
[    0.000000] ACPI: UEFI 0x000000004F652CC0 000042 (v01 HPQOEM 83A5     00000002 HP   01000013)
[    0.000000] ACPI: SSDT 0x000000004F652D08 000792 (v02 HPQOEM 83A5     00001000 ACPI 20160422)
[    0.000000] ACPI: SSDT 0x000000004F6534A0 0017AE (v02 HPQOEM 83A5     00003000 ACPI 20160422)
[    0.000000] ACPI: LPIT 0x000000004F654C50 000094 (v01 HPQOEM 83A5     00000000 HP   0000005F)
[    0.000000] ACPI: SSDT 0x000000004F654CE8 000141 (v02 HPQOEM 83A5     00000000 ACPI 20160422)
[    0.000000] ACPI: SSDT 0x000000004F654E30 00029F (v02 HPQOEM 83A5     00000000 ACPI 20160422)
[    0.000000] ACPI: SSDT 0x000000004F6550D0 0011E7 (v02 HPQOEM 83A5     00001000 ACPI 20160422)
[    0.000000] ACPI: SSDT 0x000000004F6562B8 0002AD (v02 HPQOEM 83A5     00000000 ACPI 20160422)
[    0.000000] ACPI: DBGP 0x000000004F656568 000034 (v01 HPQOEM 83A5     00000002 HP   0000005F)
[    0.000000] ACPI: DBG2 0x000000004F6565A0 000054 (v00 HPQOEM 83A5     00000002 HP   0000005F)
[    0.000000] ACPI: DMAR 0x000000004F6565F8 000070 (v01 HPQOEM 83A5     00000001 HP   00000001)
[    0.000000] ACPI: NHLT 0x000000004F656668 00002D (v00 HPQOEM 83A5     00000002 HP   01000013)
[    0.000000] ACPI: TPM2 0x000000004F656698 000034 (v03 HPQOEM 83A5     00000001 HP   00000000)
[    0.000000] ACPI: SSDT 0x000000004F6566D0 002CB1 (v01 HPQOEM 83A5     00001000 ACPI 20160422)
[    0.000000] ACPI: ASF! 0x000000004F659388 0000A0 (v32 HPQOEM 83A5     00000001 HP   000F4240)
[    0.000000] ACPI: WSMT 0x000000004F659428 000028 (v01 HPQOEM 83A5     01072009 HP   00010013)
[    0.000000] ACPI: BGRT 0x000000004F659450 000038 (v01 HPQOEM 83A5     01072009 HP   00010013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x1808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x08] high edge lint[0x1])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] ACPI: Core revision 20180531
[    0.040745] PM: Registering ACPI NVS region [mem 0x4183d000-0x4183dfff] (4096 bytes)
[    0.040745] PM: Registering ACPI NVS region [mem 0x4f65a000-0x4fb13fff] (4956160 bytes)
[    0.040745] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.040745] ACPI: bus type PCI registered
[    0.040745] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.040863] ACPI: Added _OSI(Module Device)
[    0.040863] ACPI: Added _OSI(Processor Device)
[    0.040863] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.040863] ACPI: Added _OSI(Processor Aggregator Device)
[    0.040863] ACPI: Added _OSI(Linux-Dell-Video)
[    0.040863] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.084389] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.GPLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084394] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084396] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084398] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.GUPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084401] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084402] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084405] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS01._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084408] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084409] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084411] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS01._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084414] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084415] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084418] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS02._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084420] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084422] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084424] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS02._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084426] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084428] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084430] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS03._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084433] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084434] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084436] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS03._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084438] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084440] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084443] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS04._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084445] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084447] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084448] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS04._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084451] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084452] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084455] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS05._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084457] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084459] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084461] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS05._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084463] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084465] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084468] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS06._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084470] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084471] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084473] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS06._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084475] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084477] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084480] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS07._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084482] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084484] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084485] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS07._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084488] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084489] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084492] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS08._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084494] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084496] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084498] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS08._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084500] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084502] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084505] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS09._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084507] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084508] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084510] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS09._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084512] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084514] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084517] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS10._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084519] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084521] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084522] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS10._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084525] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084526] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084577] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS11._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084580] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084582] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084583] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS11._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084586] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084587] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084590] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS12._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084593] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084594] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084596] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS12._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084598] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084600] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084603] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS13._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084605] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084606] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084608] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS13._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084610] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084612] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084615] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS14._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084617] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084619] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084621] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.HS14._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084623] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084624] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084627] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.USR1._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084630] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084631] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084633] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.USR1._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084635] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084637] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084640] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.USR2._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084642] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084643] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084645] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.USR2._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084647] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084649] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084652] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.SS01._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084654] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084656] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084657] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.SS01._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084660] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084661] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084664] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.SS02._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084667] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084668] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084670] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.SS02._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084672] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084674] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084676] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.SS03._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084679] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084680] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084682] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.SS03._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084684] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084686] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084689] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.SS04._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084691] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084693] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084694] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.SS04._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084697] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084698] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084701] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.SS05._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084703] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084705] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084707] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.SS05._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084709] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084710] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084714] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.SS06._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084716] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084717] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084719] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.SS06._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084721] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084723] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084772] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.SS07._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084774] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084776] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084778] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.SS07._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084780] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084781] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084784] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.SS08._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084787] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084788] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084790] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.SS08._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084792] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084794] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084797] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.SS09._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084799] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084801] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084802] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.SS09._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084805] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084806] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084809] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.SS10._UPC], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084812] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084813] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.084815] ACPI BIOS Error (bug): Failure creating [\_SB.PCI0.XHC.RHUB.SS10._PLD], AE_ALREADY_EXISTS (20180531/dswload2-316)
[    0.084817] ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20180531/psobject-221)
[    0.084819] ACPI Error: Skip parsing opcode Method (20180531/psloop-542)
[    0.086017] ACPI: 13 ACPI AML tables successfully acquired and loaded
[    0.096207] ACPI: Dynamic OEM Table Load:
[    0.096212] ACPI: SSDT 0xFFFF9E6B93E63800 000672 (v02 PmRef  Cpu0Ist  00003000 INTL 20160422)
[    0.096668] ACPI: \_PR_.PR00: _OSC native thermal LVT Acked
[    0.096952] ACPI: Dynamic OEM Table Load:
[    0.096956] ACPI: SSDT 0xFFFF9E6B93AB3C00 0003FF (v02 PmRef  Cpu0Cst  00003001 INTL 20160422)
[    0.097348] ACPI: Dynamic OEM Table Load:
[    0.097351] ACPI: SSDT 0xFFFF9E6B93ECFB40 0000BA (v02 PmRef  Cpu0Hwp  00003000 INTL 20160422)
[    0.097675] ACPI: Dynamic OEM Table Load:
[    0.097678] ACPI: SSDT 0xFFFF9E6B93ED6800 000628 (v02 PmRef  HwpLvt   00003000 INTL 20160422)
[    0.100403] ACPI: Dynamic OEM Table Load:
[    0.100409] ACPI: SSDT 0xFFFF9E6B93A1C000 000D14 (v02 PmRef  ApIst    00003000 INTL 20160422)
[    0.101237] ACPI: Dynamic OEM Table Load:
[    0.101237] ACPI: SSDT 0xFFFF9E6B93AB2000 000317 (v02 PmRef  ApHwp    00003000 INTL 20160422)
[    0.101238] ACPI: Dynamic OEM Table Load:
[    0.101238] ACPI: SSDT 0xFFFF9E6B93A25C00 00030A (v02 PmRef  ApCst    00003000 INTL 20160422)
[    0.106756] ACPI: EC: EC started
[    0.106756] ACPI: EC: interrupt blocked
[    0.261031] ACPI: \_SB_.PCI0.LPCB.EC0_: Used as first EC
[    0.261032] ACPI: \_SB_.PCI0.LPCB.EC0_: GPE=0x17, EC_CMD/EC_SC=0x66, EC_DATA=0x62
[    0.261033] ACPI: \_SB_.PCI0.LPCB.EC0_: Used as boot DSDT EC to handle transactions
[    0.261034] ACPI: Interpreter enabled
[    0.261066] ACPI: (supports S0 S3 S4 S5)
[    0.261067] ACPI: Using IOAPIC for interrupt routing
[    0.261096] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.262015] ACPI: Enabled 8 GPEs in block 00 to 7F
[    0.264636] ACPI: Power Resource [PG00] (on)
[    0.286175] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.286180] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.286347] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug SHPCHotplug PME AER]
[    0.286504] acpi PNP0A08:00: _OSC: OS now controls [PCIeCapability LTR]
[    0.286504] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
[    0.295894] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.295946] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.295998] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.296052] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.296103] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.296154] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.296205] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.296254] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.297635] ACPI: EC: interrupt unblocked
[    0.297681] ACPI: EC: event unblocked
[    0.297699] ACPI: \_SB_.PCI0.LPCB.EC0_: GPE=0x17, EC_CMD/EC_SC=0x66, EC_DATA=0x62
[    0.297700] ACPI: \_SB_.PCI0.LPCB.EC0_: Used as boot DSDT EC to handle transactions and events
[    0.297840] ACPI: bus type USB registered
[    0.328010] PCI: Using ACPI for IRQ routing
[    0.354859] pnp: PnP ACPI init
[    0.354859] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.354859] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.354859] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.354859] system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.354859] pnp 00:04: Plug and Play ACPI device, IDs HPQ8001 PNP0303 (active)
[    0.354859] pnp 00:05: Plug and Play ACPI device, IDs SYN3265 SYN1e00 SYN0002 PNP0f13 (active)
[    0.354859] system 00:06: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.354859] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.354859] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.356807] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.358077] pnp: PnP ACPI: found 10 devices
[    0.363274] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.757231] ACPI: AC Adapter [ADP1] (on-line)
[    0.757295] ACPI: Lid Switch [LID0]
[    0.757322] ACPI: Power Button [PWRB]
[    0.757352] ACPI: Power Button [PWRF]
[    0.765223] ACPI: Thermal Zone [TZ01] (56 C)
[    0.898431] ACPI: Battery Slot [BAT0] (battery present)
[    6.734810] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[    6.734870] ACPI: Video Device [PEGP] (multi-head: yes  rom: yes  post: no)
[    7.389565] ACPI Error: Field [D128] at bit offset/length 128/1024 exceeds size of target Buffer (160 bits) (20180531/dsopcode-201)
[    7.389591] ACPI Error: Method parse/execution failed \HWMC, AE_AML_BUFFER_LIMIT (20180531/psparse-516)
[    7.389600] ACPI Error: Method parse/execution failed \_SB.WMID.WMAA, AE_AML_BUFFER_LIMIT (20180531/psparse-516)
[    7.389667] ACPI Error: Field [D128] at bit offset/length 128/1024 exceeds size of target Buffer (160 bits) (20180531/dsopcode-201)
[    7.389687] ACPI Error: Method parse/execution failed \HWMC, AE_AML_BUFFER_LIMIT (20180531/psparse-516)
[    7.389695] ACPI Error: Method parse/execution failed \_SB.WMID.WMAA, AE_AML_BUFFER_LIMIT (20180531/psparse-516)
[    7.389765] ACPI Error: Field [D128] at bit offset/length 128/1024 exceeds size of target Buffer (160 bits) (20180531/dsopcode-201)
[    7.389786] ACPI Error: Method parse/execution failed \HWMC, AE_AML_BUFFER_LIMIT (20180531/psparse-516)
[    7.389794] ACPI Error: Method parse/execution failed \_SB.WMID.WMAA, AE_AML_BUFFER_LIMIT (20180531/psparse-516)
[    7.389951] ACPI Error: Field [D128] at bit offset/length 128/1024 exceeds size of target Buffer (160 bits) (20180531/dsopcode-201)
[    7.389969] ACPI Error: Method parse/execution failed \HWMC, AE_AML_BUFFER_LIMIT (20180531/psparse-516)
[    7.389975] ACPI Error: Method parse/execution failed \_SB.WMID.WMAA, AE_AML_BUFFER_LIMIT (20180531/psparse-516)
[    7.390016] ACPI Error: Field [D128] at bit offset/length 128/1024 exceeds size of target Buffer (160 bits) (20180531/dsopcode-201)
[    7.390030] ACPI Error: Method parse/execution failed \HWMC, AE_AML_BUFFER_LIMIT (20180531/psparse-516)
[    7.390035] ACPI Error: Method parse/execution failed \_SB.WMID.WMAA, AE_AML_BUFFER_LIMIT (20180531/psparse-516)
[    7.636340] ACPI Warning: \_SB.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20180531/nsarguments-66)

```

And I am too exhausted to look through all these errors.

If anyone has any suggestions regarding the bigger ACPI Issues 

Please help, Thanks in advance, Mark

---

