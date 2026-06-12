---
title: "power manager not recognizing battery"
date: 2011-06-04
forum: Hardware
---

### Post by silverhaze06 on 2011-06-04
Just got a new Toshiba Satellite L-655-S5150. (running 64Bit ubuntu 11.04)

the only thing wrong with it now is the power manager has no tab for battery options. the computer works if its unpluged, and when plugged back in the indicator lights on the laptop will say its charging, but the whole time power manager thinks the laptop is plugged in.

the other day i had this problem with my headphone jack not working that was fixed, [http://ubuntuforums.org/showthread.php?t=1774627]("http://http://ubuntuforums.org/showthread.php?t=1774627")

i dont know if that had anything to do with it, ( i wouldn't think so anyway.) 

i mostly keep my laptop plugged in, but there are lots of times where im using only battery power, and it would be nice to know when my battery is getting low, so i don't lose my work.


(screenshot of my problem)
[http://i56.tinypic.com/allngw.png]("http://i56.tinypic.com/allngw.png")

---

### Post by matt_symes on 2011-06-04
Hi

Not sure if i can help with this one but maybe it can be narrowed down for others.

Open a terminal and type

```
acpi_listen
```Pull out the laptop power supply and put it back in. Do you get output like below ?

```
matthew@matthew-laptop:~/a$ acpi_listen
ac_adapter ADP1 00000080 00000000
battery BAT0 00000080 00000001
ac_adapter ADP1 00000080 00000001
battery BAT0 00000080 00000001
^C
matthew@matthew-laptop:~/a$ 
```

Press ctrl + c to stop acpi_listen

Kind regards

---

### Post by silverhaze06 on 2011-06-04
i get absolutely nothing. ubuntu just behaves as if it is still plugged in. the indicator lights on my laptop are working just fine though. ubuntu seems to be ignoring this whole process.

---

### Post by silverhaze06 on 2011-06-04
```
nate@ubuntu:~$ acpi_listen


^C
nate@ubuntu:~$
```

---

### Post by matt_symes on 2011-06-04
Hi

I am no expert on this at all. However, my understanding on this was acpi_listen connects to the acpid and that gets the acpi events using netlink from the kernel.

Therefore, this may be a kernel issue if you are getting no acpi events for unplugging the power supply. However, i am not 100% sure about this and someone will correct me if i am wrong.

What is the make and model of the laptop ? 

Can you post the output of

```
ls /sys/class
```

and 

```
ls /sys/class/power_supply
```

Kind regards

---

### Post by silverhaze06 on 2011-06-04
it's a toshiba satellite L-655-S5150


```
nate@ubuntu:~$ ls /sys/class
ata_device  dmi          ieee80211  pci_bus       rtc           tty
ata_link    drm          input      pktcdvd       scsi_device   usb
ata_port    firmware     leds       power_supply  scsi_disk     usbmon
backlight   gpio         mdio_bus   ppdev         scsi_generic  vc
bdi         graphics     mem        ppp           scsi_host     video4linux
block       hidraw       misc       printer       sound         vtconsole
bsg         hwmon        mmc_host   regulator     spi_master    wmi
dma         i2c-adapter  net        rfkill        thermal
nate@ubuntu:~$ ls /sys/class/power_supply
ACAD
nate@ubuntu:~$ 

```

---

### Post by matt_symes on 2011-06-04
Hi

What's the output of
[FONT=monospace]
[/FONT]```
cat /sys/class/power_supply/ACAD/online

```

What is your output from

```
uname -a
```

Kind regards

---

### Post by silverhaze06 on 2011-06-04
```
nate@ubuntu:~$ cat /sys/class/power_supply/ACAD/online
1
nate@ubuntu:~$ uname -a
Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
nate@ubuntu:~$ 
```

i ran the first command with the power cord both plugged-in, and then with it un-plugged, with the same result.

---

### Post by matt_symes on 2011-06-04
Hi

That looks all right so far.

A quick look at the kernel message buffer might be in order. Can you post the output of

```
dmesg | grep -i acpi
```

Kind regards

---

### Post by silverhaze06 on 2011-06-04
```
nate@ubuntu:~$ dmesg | grep -i acpi
[    0.000000]  BIOS-e820: 00000000bb6bf000 - 00000000bb7bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bb7bf000 - 00000000bb7ff000 (ACPI data)
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 TOSQCI)
[    0.000000] ACPI: XSDT 00000000bb7fe120 00074 (v01 TOSQCI TOSQCI00 00000001      01000013)
[    0.000000] ACPI: FACP 00000000bb7fc000 000F4 (v04 TOSQCI TOSQCI00 00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT 00000000bb7ec000 0CE26 (v02 TOSQCI TOSQCI00 00000001 MSFT 01000013)
[    0.000000] ACPI: FACS 00000000bb76e000 00040
[    0.000000] ACPI: ASF! 00000000bb7fd000 000A5 (v32 TOSQCI TOSQCI00 00000001 MSFT 01000013)
[    0.000000] ACPI: HPET 00000000bb7fb000 00038 (v01 TOSQCI TOSQCI00 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 00000000bb7fa000 0008C (v02 TOSQCI TOSQCI00 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 00000000bb7f9000 0003C (v01 TOSQCI TOSQCI00 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 00000000bb7eb000 00176 (v01 TOSQCI TOSQCI00 00000001 MSFT 01000013)
[    0.000000] ACPI: BOOT 00000000bb7e7000 00028 (v01 TOSQCI TOSQCI00 00000001 MSFT 01000013)
[    0.000000] ACPI: ASPT 00000000bb7e4000 00034 (v04 INTEL  Calpella 00000001 MSFT 01000013)
[    0.000000] ACPI: WDAT 00000000bb7e3000 00224 (v01 INTEL  Calpella 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 00000000bb7e2000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x00] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.004492] ACPI: Core revision 20110112
[    0.004617] ACPI: Forced DSDT copy: length 0x0CE26 copied locally, original unmapped
[    0.445257] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.445259] ACPI: bus type pci registered
[    0.496003] ACPI: EC: Look up EC in DSDT
[    0.498390] ACPI: Executed 1 blocks of module-level executable AML code
[    0.583359] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.584041] ACPI: SSDT 00000000bb691c18 003C7 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.584620] ACPI: Dynamic OEM Table Load:
[    0.584623] ACPI: SSDT           (null) 003C7 (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.584832] ACPI: SSDT 00000000bb68f018 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.585386] ACPI: Dynamic OEM Table Load:
[    0.585388] ACPI: SSDT           (null) 00891 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.693610] ACPI: SSDT 00000000bb690a98 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.694249] ACPI: Dynamic OEM Table Load:
[    0.694252] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.713433] ACPI: SSDT 00000000bb68ed98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.714064] ACPI: Dynamic OEM Table Load:
[    0.714067] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.743543] ACPI: Interpreter enabled
[    0.743547] ACPI: (supports S0 S3 S4 S5)
[    0.743592] ACPI: Using IOAPIC for interrupt routing
[    0.783755] ACPI: EC: GPE = 0x1e, I/O: command/status = 0x66, data = 0x62
[    0.813608] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.813614] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.814044] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.822191] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.822366] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.822454] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.822500] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.827952] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
[    0.828406] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.828461] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.828510] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.828559] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.828607] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.828656] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.828704] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.828752] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.829390] PCI: Using ACPI for IRQ routing
[    0.837832] pnp: PnP ACPI init
[    0.837849] ACPI: bus type pnp registered
[    0.838386] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.838492] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.838525] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    0.838663] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.838711] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.838837] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.838879] pnp 00:06: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.838957] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.839026] pnp 00:08: Plug and Play ACPI device, IDs SYN103f PNP0f13 (active)
[    0.839426] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.839641] pnp 00:0a: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.839729] pnp: PnP ACPI: found 11 devices
[    0.839731] ACPI: ACPI bus type pnp unregistered
[    0.899228] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.899281] ACPI: AC Adapter [ACAD] (on-line)
[    0.899419] ACPI: Power Button [PWRB]
[    0.921664] ACPI: Lid Switch [LID]
[    0.921762] ACPI: Power Button [PWRF]
[    0.921977] ACPI: acpi_idle yielding to intel_idle
[    0.923477] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.923505] ACPI: Battery Slot [BAT1] (battery absent)
[   13.740383] acpi device:02: registered as cooling_device2
[   13.740924] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
nate@ubuntu:~$ 

```

---

### Post by jonathon6017 on 2011-06-04
Many toshiba computers have this issue. I finally fixed mine today using this tutorial [http://techinterplay.com/fix-toshiba-battery-issue-linux.html](http://techinterplay.com/fix-toshiba-battery-issue-linux.html) It is a long and advanced tutorial but boy was I happy when it worked.

---

### Post by matt_symes on 2011-06-04
Hi

Looking at the output of dmesg...

> [    0.899281] ACPI: AC Adapter [ACAD] (on-line)
<snip>
[    0.923505] ACPI: Battery Slot [BAT1] (battery absent)...it would seem that the problem is not with your AC adaptor but with the battery not being discovered correctly. 

You do not get any notifications when you unplug the AC supply and run off battery power because it does not think you have a battery.

That gives us a starting point to try to identify a solution (if we can find one). I must eat first before i can help look though.

Kind regards

---

### Post by silverhaze06 on 2011-06-04
> **jonathon6017 said:**
> Many toshiba computers have this issue. I finally fixed mine today using this tutorial [http://techinterplay.com/fix-toshiba-battery-issue-linux.html](http://techinterplay.com/fix-toshiba-battery-issue-linux.html) It is a long and advanced tutorial but boy was I happy when it worked.


that just might be what the problem is for me too i'm guessing. but that tutorial is a little beyond me. 

can anyone help???

---

### Post by matt_symes on 2011-06-04
Hi

> That gives us a starting point to try to identify a solution

> **jonathon6017 said:**
> Many toshiba computers have this issue. I finally fixed mine today using this tutorial [http://techinterplay.com/fix-toshiba-battery-issue-linux.html](http://techinterplay.com/fix-toshiba-battery-issue-linux.html) It is a long and advanced tutorial but boy was I happy when it worked.

Nice one Jonathon6017 :D 

That looks very much like the issue you are having Silverhaze06 and if i was a betting man i would bet that would fix it. 

If it is the problem, it is a kernel issue after all and the fix requires recompiling the kernel with a new DSDT table.

This is relatively advanced and would take a while to do. I don't have a Toshiba laptop so i would only be able to attempt to talk you through it from the instructions posted.

If you really want to fix it we can work through the tutorial. What do you want to do ?

Kind regards

---

### Post by silverhaze06 on 2011-06-04
if you don't mind walking me through it, it would be much appreciated!

---

### Post by matt_symes on 2011-06-04
Hi

> **silverhaze06 said:**
> if you don't mind walking me through it, it would be much appreciated!

Alright then, lets give it a go. We'll take it in stages and see how what the instructions are like.

The first thing you want to do is enter a root shell so open a terminal and type

```
sudo su
```Enter password as normal.

Then install iasl

```
apt-get install iasl
```After that get a dump of the dsdt table.

```
cat /sys/firmware/acpi/tables/DSDT > DSDT.dat
```Then disassemble it

```
iasl -d DSDT.dat
```After that the table need to be modified so type

```
nano DSDT.dsl
```This will open it in nano (the text editor). Press ctrl + w and enter

```
OperationRegion (EMEM, SystemMemory, 0xFF808001, 0xFF)
```then hit enter. This should find the line in the table for you. You then need to edit it so it looks like this.

```
OperationRegion (EMEM, EmbeddedControl, 0×00, 0xFF)
```Ensure you keep the case correct and spaces (etc).

Then recompile it using

```
iasl -tc DSDT.dsl
```Post back at that point to tell me how you are doing. If there any any errors from the compilation process then also post back.

Kind regards

---

### Post by silverhaze06 on 2011-06-04
```
nate@ubuntu:~$ sudo su
[sudo] password for nate: 
root@ubuntu:/home/nate# apt-get install iasl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  python-sip
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  iasl
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 366 kB of archives.
After this operation, 811 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ natty/main iasl amd64 20100528-3 [366 kB]
Fetched 366 kB in 1s (232 kB/s)
Selecting previously deselected package iasl.
(Reading database ... 180813 files and directories currently installed.)
Unpacking iasl (from .../iasl_20100528-3_amd64.deb) ...
Processing triggers for man-db ...
Setting up iasl (20100528-3) ...
root@ubuntu:/home/nate# cat /sys/firmware/acpi/tables/DSDT > DSDT.d
root@ubuntu:/home/nate# cat /sys/firmware/acpi/tables/DSDT > DSDT.d
root@ubuntu:/home/nate# iasl -d DSDT.dat

Intel ACPI Component Architecture
AML Disassembler version 20100528 [Oct 15 2010]
Copyright (c) 2000 - 2010 Intel Corporation
Supports ACPI Specification Revision 4.0a

Could not open input file DSDT.dat
root@ubuntu:/home/nate# nano DSDT.dat
root@ubuntu:/home/nate# nano DSDT.dat
root@ubuntu:/home/nate# 

```


it couldn't find some of the things, also when in the text edit mode gave me this error,[IMG]http://i51.tinypic.com/ehyush.png[/IMG]

---

### Post by matt_symes on 2011-06-04
Hi

Type this next

```
cat /sys/firmware/acpi/tables/DSDT > DSDT.dat
```The at off .dat got cut off from my post above. Continue with the commands. I will amend my post above.


Kind regards

---

### Post by silverhaze06 on 2011-06-04
```
root@ubuntu:/home/nate# ls
alsa-info.sh  Documents  examples.desktop  Podcasts   Ubuntu One
Audiobooks    Downloads  Music             Public     Videos
Desktop       DSDT.d     Pictures          Templates  wallpapers
root@ubuntu:/home/nate# 

```

---

### Post by silverhaze06 on 2011-06-04
```
root@ubuntu:/home/nate# cat /sys/firmware/acpi/tables/DSDT > DSDT.dat
root@ubuntu:/home/nate# 

```

doesn't seem to do anything.

---

### Post by matt_symes on 2011-06-04
Hi

Sorry there was a typo in my previous post :(

> doesn't seem to do anything.It creates a file in your local directory but gives you no feedback if sucessfull; only if it fails do you get feedback.

Do this step next
[FONT=monospace]
[/FONT]```
iasl -d DSDT.dat 
```Then this one.

```
nano DSDT.dat
```And continue using my earlier post

Kind regards

---

### Post by silverhaze06 on 2011-06-04
it made the file but still cant find that line it seems.

[IMG]http://i55.tinypic.com/akess0.png[/IMG]

---

### Post by matt_symes on 2011-06-04
Hi

Sorry for the delay. Follow these instructions carefully. 

I made a couple of typos earlier. Sorry about that. I had kids in the house earlier. A bit distracting.

```
**iasl -d DSDT.dat**
```After that the table need to be modified so type

```
nano DSDT.**dsl**
```This will open it in nano (the text editor). Press ctrl + w and enter

```
OperationRegion (EMEM, SystemMemory, 0xFF808001, 0xFF)
```then hit enter. This should find the line in the table for you. You then need to edit it so it looks like this.

     ```
OperationRegion (EMEM, EmbeddedControl, 0×00, 0xFF)
```      
Ensure you keep the case correct and spaces (etc).

Then recompile it using

     ```
iasl -tc DSDT.**dsl**
```      
Post back at that point to tell me how you are doing. If there any any errors from the compilation process then also post back.

Kind regards

---

### Post by silverhaze06 on 2011-06-04
ok, that worked so far, now i'm at

```
root@ubuntu:/home/nate# nano DSDT.dsl
root@ubuntu:/home/nate# iasl -tc DSDT.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20100528 [Oct 15 2010]
Copyright (c) 2000 - 2010 Intel Corporation
Supports ACPI Specification Revision 4.0a

Non-ascii input file - DSDT.dsl
root@ubuntu:/home/nate# 

```

---

### Post by matt_symes on 2011-06-04
Hi

Excellent. We are making progress. Next we need to recoompile the kernel.

First install the packages necessary to compile and install the kernel.

```
apt-get install fakeroot kernel-wedge build-essential makedumpfile kernel-package libncurses5 libncurses5-dev
```

```
apt-get build-dep --no-install-recommends linux-image-$(uname -r)
```
  
```
mkdir /root/source && cd $_
```
  
```
apt-get source linux-image-$(uname -r)
```

then type

```
uname -r
```

Post the result of that last command back here. It is required for a later step.

Kind regards

---

### Post by silverhaze06 on 2011-06-04
sorry it took so long, computer froze, and it took a bit to figure out where i was. all that worked so far, here are results of last command...


```
root@ubuntu:~/source# uname -r
2.6.38-8-generic
root@ubuntu:~/source# 

```

---

### Post by silverhaze06 on 2011-06-05
ok, i tried doing the rest my self, but didn't get far and got totally lost and had to close the terminal a few times. that wouldn't screw this whole process up would it?

---

### Post by jonathon6017 on 2011-06-05
> **silverhaze06 said:**
> ok, that worked so far, now i'm at

```
root@ubuntu:/home/nate# nano DSDT.dsl
root@ubuntu:/home/nate# iasl -tc DSDT.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20100528 [Oct 15 2010]
Copyright (c) 2000 - 2010 Intel Corporation
Supports ACPI Specification Revision 4.0a

**Non-ascii input file - DSDT.dsl**
root@ubuntu:/home/nate# 

```
 
It won't compile right if you get this message. I struggled with this issue until I figured it out, you will get this issue If you paste the corrections into the file. To get past this error you will have to manually type in the corrections instead of just pasting them in

---

### Post by matt_symes on 2011-06-05
Hi

Nicely done jonathon6017. I'm glad you're keeping an eye on this thread :D. You have done this and we have not. Your input is very much appreciated.

@OP. Whereabouts are you at the moment. What steps have you completed ?

Kind regards

---

### Post by silverhaze06 on 2011-06-05
im right were we left off.

---

### Post by jonathon6017 on 2011-06-05
> **silverhaze06 said:**
> im right were we left off.

As I said you will have to re-edit the file erase what you previously pasted and manually type it out then recompile, after that you should get two errors like the tutorial said (and possibly many other warnings but you can ignore those) go back to the file and in the lines that it is complaining about correct them with the values the tutorial asks you to but as I said before the compiler does not like pasted characters so everything will have to be typed out. After that if you done everything correctly you should only have to re-compile one last time and then you can go on to installing the necessary packages. I'll keep monitoring this post and provide any help I can.

---

### Post by silverhaze06 on 2011-06-05
ok, i did that, now i am here...

```
nate@ubuntu:~$ sudo su
[sudo] password for nate: 
root@ubuntu:/home/nate# iasl -d DSDT.dat

Intel ACPI Component Architecture
AML Disassembler version 20100528 [Oct 15 2010]
Copyright (c) 2000 - 2010 Intel Corporation
Supports ACPI Specification Revision 4.0a

Loading Acpi table from file DSDT.dat
Acpi table [DSDT] successfully installed and loaded
Pass 1 parse of [DSDT]
Pass 2 parse of [DSDT]
Parsing Deferred Opcodes (Methods/Buffers/Packages/Regions)
............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
Parsing completed

Found 5 external control methods, reparsing with new information
Pass 1 parse of [DSDT]
Pass 2 parse of [DSDT]
Parsing Deferred Opcodes (Methods/Buffers/Packages/Regions)
............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
Parsing completed
Disassembly completed, written to "DSDT.dsl"
root@ubuntu:/home/nate# nano DSDT.dsl
root@ubuntu:/home/nate# iasl -tc DSDT.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20100528 [Oct 15 2010]
Copyright (c) 2000 - 2010 Intel Corporation
Supports ACPI Specification Revision 4.0a

DSDT.dsl  2662:                     0x00000000,         // Length
Error    4122 -                              ^ Invalid combination of Length and Min/Max fixed flags

DSDT.dsl  2669:                     0x00000000,         // Length
Error    4122 -                              ^ Invalid combination of Length and Min/Max fixed flags

DSDT.dsl  2924:             Method (CBRL, 0, NotSerialized)
Warning  1088 -                        ^ Not all control paths return a value (CBRL)

DSDT.dsl  2986:                 Name (_T_0, Zero)
Remark   5111 -                          ^ Use of compiler reserved name (_T_0)

DSDT.dsl  3366:                             Name (_T_0, Zero)
Remark   5111 -        Use of compiler reserved name ^  (_T_0)

DSDT.dsl  4574:                         Name (_T_0, Zero)
Remark   5111 -    Use of compiler reserved name ^  (_T_0)

DSDT.dsl  4616:                     Method (_DSM, 4, NotSerialized)
Warning  1088 -                                ^ Not all control paths return a value (_DSM)

DSDT.dsl  4616:                     Method (_DSM, 4, NotSerialized)
Warning  1081 -                                ^ Reserved method must return a value (Integer/String/Buffer/Package/Reference required for _DSM)

DSDT.dsl  4926:                             Name (_T_0, Zero)
Remark   5111 -        Use of compiler reserved name ^  (_T_0)

DSDT.dsl  5230:                             Name (_T_0, Zero)
Remark   5111 -        Use of compiler reserved name ^  (_T_0)

DSDT.dsl  5259:                             Name (_T_1, Zero)
Remark   5111 -        Use of compiler reserved name ^  (_T_1)

DSDT.dsl 10429:             Method (EVNT, 1, NotSerialized)
Warning  1088 -                        ^ Not all control paths return a value (EVNT)

DSDT.dsl 10999:                 Name (_T_0, Zero)
Remark   5111 -                          ^ Use of compiler reserved name (_T_0)

DSDT.dsl 11047:                             Name (_T_1, Zero)
Remark   5111 -        Use of compiler reserved name ^  (_T_1)

DSDT.dsl 11115:                         Name (_T_2, Zero)
Remark   5111 -    Use of compiler reserved name ^  (_T_2)

DSDT.dsl 11152:                                 Name (_T_3, Zero)
Remark   5111 -            Use of compiler reserved name ^  (_T_3)

DSDT.dsl 11185:                                 Name (_T_4, Zero)
Remark   5111 -            Use of compiler reserved name ^  (_T_4)

DSDT.dsl 11245:                                             Name (_T_5, Zero)
Remark   5111 -                        Use of compiler reserved name ^  (_T_5)

DSDT.dsl 11249:                                                 Name (_T_6, Zero)
Remark   5111 -                            Use of compiler reserved name ^  (_T_6)

DSDT.dsl 11302:                                                 Name (_T_7, Zero)
Remark   5111 -                            Use of compiler reserved name ^  (_T_7)

DSDT.dsl 11331:                                                         Name (_T_8, Zero)
Remark   5111 -                                    Use of compiler reserved name ^  (_T_8)

DSDT.dsl 11532:                                                                     Name (_T_9, Zero)
Remark   5111 -                                                Use of compiler reserved name ^  (_T_9)

DSDT.dsl 11590:                                                                     Name (_T_A, Zero)
Remark   5111 -                                                Use of compiler reserved name ^  (_T_A)

DSDT.dsl 11653:                                                                     Name (_T_B, Zero)
Remark   5111 -                                                Use of compiler reserved name ^  (_T_B)

DSDT.dsl 11679:                                                                             Name (_T_C, Zero)
Remark   5111 -                                                        Use of compiler reserved name ^  (_T_C)

DSDT.dsl 11706:                                                                                 Name (_T_D, Zero)
Remark   5111 -                                                            Use of compiler reserved name ^  (_T_D)

DSDT.dsl 11726:                                                                             Name (_T_E, Zero)
Remark   5111 -                                                        Use of compiler reserved name ^  (_T_E)

DSDT.dsl 11773:                                                                                 Name (_T_F, Zero)
Remark   5111 -                                                            Use of compiler reserved name ^  (_T_F)

DSDT.dsl 11842:                                                                                         Name (_T_G, Zero)
Remark   5111 -                                                                    Use of compiler reserved name ^  (_T_G)

DSDT.dsl 11846:                                                                                             Name (_T_H, Zero)
Remark   5111 -                                                                        Use of compiler reserved name ^  (_T_H)

DSDT.dsl 11888:                                                                                                     Name (_T_I, Zero)
Remark   5111 -                                                                                Use of compiler reserved name ^  (_T_I)

DSDT.dsl 11960:                                                                                         Name (_T_J, Zero)
Remark   5111 -                                                                    Use of compiler reserved name ^  (_T_J)

DSDT.dsl 12017:                                                                                             Name (_T_K, Zero)
Remark   5111 -                                                                        Use of compiler reserved name ^  (_T_K)

DSDT.dsl 12021:                                                                                                 Name (_T_L, Zero)
Remark   5111 -                                                                            Use of compiler reserved name ^  (_T_L)

DSDT.dsl 12083:                                                                                                     Name (_T_M, Zero)
Remark   5111 -                                                                                Use of compiler reserved name ^  (_T_M)

DSDT.dsl 12126:                                                                                                         Name (_T_N, Zero)
Remark   5111 -                                                                                    Use of compiler reserved name ^  (_T_N)

DSDT.dsl 12221:                                                                                                                 Name (_T_O, Zero)
Remark   5111 -                                                                                            Use of compiler reserved name ^  (_T_O)

DSDT.dsl 12262:                                                                                                                 Name (_T_P, Zero)
Remark   5111 -                                                                                            Use of compiler reserved name ^  (_T_P)

DSDT.dsl 12276:                                                                                                                             Name (_T_Q, Zero)
Remark   5111 -                                                                                                        Use of compiler reserved name ^  (_T_Q)

DSDT.dsl 12348:                                                                                                                     Name (_T_R, Zero)
Remark   5111 -                                                                                                Use of compiler reserved name ^  (_T_R)

DSDT.dsl 12379:                                                                                                     Name (_T_S, Zero)
Remark   5111 -                                                                                Use of compiler reserved name ^  (_T_S)

DSDT.dsl 12383:                                                                                                         Name (_T_T, Zero)
Remark   5111 -                                                                                    Use of compiler reserved name ^  (_T_T)

DSDT.dsl 12464:                                                                                                                     Name (_T_U, Zero)
Remark   5111 -                                                                                                Use of compiler reserved name ^  (_T_U)

DSDT.dsl 13647:             Method (BTST, 0, NotSerialized)
Warning  1088 -                        ^ Not all control paths return a value (BTST)

ASL Input:  DSDT.dsl - 13750 lines, 547404 bytes, 6061 keywords
Compilation complete. 2 Errors, 5 Warnings, 37 Remarks, 7 Optimizations
root@ubuntu:/home/nate# 

```

---

### Post by jonathon6017 on 2011-06-05
Now replace the values in those two lines like the tutorial says

---

### Post by silverhaze06 on 2011-06-05
yeah that tutorial confuses me. especially that part. can anyone else out there help?

---

### Post by jonathon6017 on 2011-06-05
> **silverhaze06 said:**
> yeah that tutorial confuses me. especially that part. can anyone else out there help?

Ha ha I warned you was confusing. Just about every step I went through I had an error and had to solve it myself talk about a frustrating puzzle ;) Anyways I used gedit so I can help you best if you use that.

Use this command (as root if you're not already) 
```
gedit DSDT.dsl
```

Click Search (up at the top) then click "go to line"

Enter 2662 and press enter

Change 0x00000000 (which is under //length) to 0xFEB00000 (but please don't forget that you can't paste this)

then again Click Search, "go to line" enter 2669 and press enter 

Change 0x00000000 (also the length) to 0×00005000

and now recompile

---

### Post by silverhaze06 on 2011-06-05
ok, i did that and saved it, now how do i recompile? (sorry, but i have no idea what all this stuff means exactly so im pretty lost.)

---

### Post by jonathon6017 on 2011-06-05
> **silverhaze06 said:**
> ok, i did that and saved it, now how do i recompile? (sorry, but i have no idea what all this stuff means exactly so im pretty lost.)

```
iasl -tc DSDT.dsl
```

---

### Post by silverhaze06 on 2011-06-05
ok, didnt give me any errors this time. so now do i reinstall those packages?

---

### Post by jonathon6017 on 2011-06-05
> **silverhaze06 said:**
> ok, didnt give me any errors this time. so now do i reinstall those packages?

Well what part did you leave off of before we had to go back and recompile?

Have you already done this "apt-get source linux-image-$(uname -r)"

---

### Post by silverhaze06 on 2011-06-05
yes, just did that, worked fine then did 

```
root@ubuntu:/home/nate# uname -r
2.6.38-8-generic

```

so whats next after this?

---

### Post by jonathon6017 on 2011-06-05
> **silverhaze06 said:**
> yes, just did that, worked fine then did 

```
root@ubuntu:/home/nate# uname -r
2.6.38-8-generic

```

so whats next after this?
Enter these commands in order and let me know if you encounter any errors

```
cd linux-2.6.38-8
```
```
cp -vi /boot/config-`uname -r` .config

```
```
cp DSDT.hex /root/source/linux-2.6.38.8/include
```

If you get through these three commands without error we'll move on

---

### Post by silverhaze06 on 2011-06-05
im getting this error on the first command,

```
root@ubuntu:/home/nate# cd linux-2.6.38-8
bash: cd: linux-2.6.38-8: No such file or directory
root@ubuntu:/home/nate# cd linux-2.6.38-8-generic
bash: cd: linux-2.6.38-8-generic: No such file or directory
root@ubuntu:/home/nate# 

```

---

### Post by jonathon6017 on 2011-06-05
> **silverhaze06 said:**
> im getting this error on the first command,

```
root@ubuntu:/home/nate# cd linux-2.6.38-8
bash: cd: linux-2.6.38-8: No such file or directory
root@ubuntu:/home/nate# cd linux-2.6.38-8-generic
bash: cd: linux-2.6.38-8-generic: No such file or directory
root@ubuntu:/home/nate# 

```

Ok type ```
ls
``` to make sure the folder is in there

---

### Post by silverhaze06 on 2011-06-05
```
root@ubuntu:/home/nate# ls
alsa-info.sh  DSDT.aml  examples.desktop           Music      Ubuntu One
Audiobooks    DSDT.d    linux-2.6.38               Pictures   Videos
Desktop       DSDT.dat  linux_2.6.38-8.42.diff.gz  Podcasts   wallpapers
Documents     DSDT.dsl  linux_2.6.38-8.42.dsc      Public
Downloads     DSDT.hex  linux_2.6.38.orig.tar.gz   Templates
root@ubuntu:/home/nate# 

```

it gave me this.

---

### Post by jonathon6017 on 2011-06-05
ok the proper command is 

cd linux-2.6.38

---

### Post by silverhaze06 on 2011-06-05
ok, just got an error on the last command.


```
root@ubuntu:/home/nate# cd linux-2.6.38
root@ubuntu:/home/nate/linux-2.6.38# cp -vi /boot/config-`uname -r` .config
`/boot/config-2.6.38-8-generic' -> `.config'
root@ubuntu:/home/nate/linux-2.6.38# cp DSDT.hex /root/source/linux-2.6.38.8/include
cp: cannot stat `DSDT.hex': No such file or directory
root@ubuntu:/home/nate/linux-2.6.38#
```

---

### Post by jonathon6017 on 2011-06-05
Ok lets change that command to ```
cp /home/nate/DSDT.hex /root/source/linux-2.6.38.8/include
```

assuming nate is your username

---

### Post by silverhaze06 on 2011-06-05
it is, but that didnt seem to work either.

```
root@ubuntu:/home/nate/linux-2.6.38# cp /home/nate/DSDT.hex /root/source/linux-2.6.38.8/include
cp: cannot create regular file `/root/source/linux-2.6.38.8/include': No such file or directory
root@ubuntu:/home/nate/linux-2.6.38#
```

---

### Post by jonathon6017 on 2011-06-05
do the ls command again

---

### Post by silverhaze06 on 2011-06-05
```
root@ubuntu:/home/nate/linux-2.6.38# ls
arch     debian         firmware  Kbuild       Makefile        samples   ubuntu
block    debian.master  fs        Kconfig      mm              scripts   usr
COPYING  Documentation  include   kernel       net             security  virt
CREDITS  drivers        init      lib          README          sound
crypto   dropped.txt    ipc       MAINTAINERS  REPORTING-BUGS  tools
root@ubuntu:/home/nate/linux-2.6.38#
```

---

### Post by jonathon6017 on 2011-06-05
OK I see the problem now a minor annoyance.... change it this time to 

cp /home/nate/DSDT.hex /home/nate/source/linux-2.6.38.8/include

Hopefully this works

---

### Post by silverhaze06 on 2011-06-05
```
root@ubuntu:/home/nate/linux-2.6.38# cp /home/nate/DSDT.hex /home/nate/source/linux-2.6.38.8/include
cp: cannot create regular file `/home/nate/source/linux-2.6.38.8/include': No such file or directory
root@ubuntu:/home/nate/linux-2.6.38#
```

yeah, sorry, this is so irritating! :x

---

### Post by jonathon6017 on 2011-06-05
Ok this is irritating but let's see we know /include is inside /linux-2.6.38.8 is your source file is your home folder (/home/nate) or root'shome folder (/root) you can check by running 

ls /home/nate

and then

ls /root 

and post the results of both of those...This issue we are having is a very easy one to fix it's just taking me a little longer to solve it cause I don't have immediate access to your file system and I'm having to do a trial and error type of guess and wait for you to post the results.

I sometimes will make little mistakes like this with my own system but of course then it's easier to figure out where the folder is that I'm looking for.

---

### Post by silverhaze06 on 2011-06-05
```
root@ubuntu:/home/nate/linux-2.6.38# ls /home/nate
alsa-info.sh  DSDT.aml  examples.desktop           Music      Ubuntu One
Audiobooks    DSDT.d    linux-2.6.38               Pictures   Videos
Desktop       DSDT.dat  linux_2.6.38-8.42.diff.gz  Podcasts   wallpapers
Documents     DSDT.dsl  linux_2.6.38-8.42.dsc      Public
Downloads     DSDT.hex  linux_2.6.38.orig.tar.gz   Templates
root@ubuntu:/home/nate/linux-2.6.38# ls /root 
source
root@ubuntu:/home/nate/linux-2.6.38# 

```

---

### Post by jonathon6017 on 2011-06-05
```
ls /root/source
```

---

### Post by silverhaze06 on 2011-06-05
```
root@ubuntu:/home/nate/linux-2.6.38# ls /root/source
linux-2.6.38               linux_2.6.38-8.42.dsc
linux_2.6.38-8.42.diff.gz  linux_2.6.38.orig.tar.gz
root@ubuntu:/home/nate/linux-2.6.38# 

```

---

### Post by jonathon6017 on 2011-06-05
cp /home/nate/DSDT.hex /root/source/linux-2.6.38.8/include

---

### Post by silverhaze06 on 2011-06-05
still nothing...

```
root@ubuntu:/home/nate/linux-2.6.38# cp /home/nate/DSDT.hex /root/source/linux-2.6.38.8/include
cp: cannot create regular file `/root/source/linux-2.6.38.8/include': No such file or directory
root@ubuntu:/home/nate/linux-2.6.38# 
```

---

### Post by silverhaze06 on 2011-06-05
wait...

```
root@ubuntu:/home/nate/linux-2.6.38# ls /root/source/linux-2.6.38
arch     debian         firmware  Kbuild       Makefile        samples   ubuntu
block    debian.master  fs        Kconfig      mm              scripts   usr
COPYING  Documentation  include   kernel       net             security  virt
CREDITS  drivers        init      lib          README          sound
crypto   dropped.txt    ipc       MAINTAINERS  REPORTING-BUGS  tools
root@ubuntu:/home/nate/linux-2.6.38# 
```

does that help?

---

### Post by jonathon6017 on 2011-06-05
Well I tell you I'm stumped right now I know that basically you're copying the  DSDT.hex file to the /include folder inside the /linux-2.6.38 folder except that it seems like you have two of those folders or something. I'll think about it and see if I can come up with a solution, in the mean time maybe somebody else can see something I missed.

---

### Post by jonathon6017 on 2011-06-05
WAIT!!!!!!!!!! I see now 

cp /home/nate/DSDT.hex /root/source/linux-2.6.38/include

we had to erase the .8 from the linux-2.6.38.8 now it should work

---

### Post by silverhaze06 on 2011-06-05
ALLRIGHT! FINALLY WORKED!  now, what is the next step after this?

---

### Post by jonathon6017 on 2011-06-05
```
gedit /root/source/linux-2.6.38/.config
```

Use Ctrl+F to find these

Search for CONFIG_STANDALONE which I believe is commented out with a # and says something like it isn't configured. Erase the # and change the last part and change it to where it looks like this: CONFIG_STANDALONE=n

Search for CONFIG_ACPI_CUSTOM_DSDT and make it into CONFIG_ACPI_CUSTOM_DSDT=y

and last right above it change CONFIG_ACPI_CUSTOM_DSDT_FILE="" to CONFIG_ACPI_CUSTOM_DSDT_FILE="DSDT.hex"

save and quit then let me know when you are done

---

### Post by silverhaze06 on 2011-06-05
```
root@ubuntu:/home/nate/linux-2.6.38# gedit /root/source/linux-2.6.38/.config

(gedit:18414): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.WDJQWV': No such file or directory

(gedit:18414): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:18414): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.BX7EWV': No such file or directory

(gedit:18414): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
root@ubuntu:/home/nate/linux-2.6.38# 

```

it opened an empty file, but thats it.

---

### Post by jonathon6017 on 2011-06-05
cp -vi /boot/config-`uname -r` /root/source/linux-2.6.38/.config

then try what I just said

---

### Post by silverhaze06 on 2011-06-05
ok, that all worked and i am done with that step. so whats after this?

---

### Post by jonathon6017 on 2011-06-05
make menuconfig

Enter this command and post a screenshot because I forgot which one you press but I know its one of them on the bottom

---

### Post by silverhaze06 on 2011-06-05
[IMG]http://i55.tinypic.com/qoexrk.png[/IMG]

---

### Post by jonathon6017 on 2011-06-05
Scroll down and see if there are more options

---

### Post by jonathon6017 on 2011-06-05
You are looking for something about a config file

---

### Post by silverhaze06 on 2011-06-05
[IMG]http://i52.tinypic.com/xg9us7.png[/IMG]

thats all of them

---

### Post by jonathon6017 on 2011-06-05
Load an Alternative config then tell me what it says

---

### Post by silverhaze06 on 2011-06-05
[IMG]http://i56.tinypic.com/ajkyvc.png[/IMG]

---

### Post by jonathon6017 on 2011-06-05
Ok.... click Ok and then at the main menu press exit 

Before we continue what kind of a processor do you have (a dual-core, quad-core, etc)

---

### Post by silverhaze06 on 2011-06-05
pentium p6200 64bit dual core

---

### Post by jonathon6017 on 2011-06-05
Ok so you will want this command

```
export CONCURRENCY_LEVEL=3

```

then.. 
```
 make-kpkg clean

```
and then...
```
 fakeroot make-kpkg --initrd --append-to-version=-tuxsage kernel-image kernel-headers

```
 
After this starts the part that took my computer about an hour to complete so let me know when you are done with these three...we are almost done :)

---

### Post by silverhaze06 on 2011-06-05
ok, seems to have worked and is now installing all that stuff, i'll post again when it is done.

---

### Post by jonathon6017 on 2011-06-05
ok :) In case you're wondering what we are doing we are recompiling a new kernel that will work for the toshiba laptop. and it should automatically boot into the new kernel when we reboot later. Btw I looked at your laptop online earlier, yours is very similar to mine, the biggest difference is mine don't have a numeric keypad.

---

### Post by silverhaze06 on 2011-06-05
crap, screensaver kicked in and put display asleep while i was making a pizza, and it wouldn't come out of sleep  so i had to reboot in the middle of it. now im getting this when i try to start where i left off.

```
root@ubuntu:/home/nate# export CONCURRENCY_LEVEL=3
root@ubuntu:/home/nate# make-kpkg clean
We do not seem to be in a top level linux kernel source directory
tree. Since we are trying to make a kernel package, that does not make
sense.  Please change directory to a top level linux kernel source
directory, and try again. (If I am wrong, and this is indeed a top
level linux kernel source directory, then I have gotten sadly out of
date with current kernels, and you should upgrade kernel-package)
root@ubuntu:/home/nate# 
```

---

### Post by jonathon6017 on 2011-06-05
You are not in the directory you were in you are in your home folder go back to /root/source/linux-2.6.38

---

### Post by silverhaze06 on 2011-06-05
ok, still not working, what am i doing wrong?

```
root@ubuntu:/home/nate# ls /root/source/linux-2.6.38
arch     debian         firmware  Kbuild       Makefile        samples   ubuntu
block    debian.master  fs        Kconfig      mm              scripts   usr
COPYING  Documentation  include   kernel       net             security  virt
CREDITS  drivers        init      lib          README          sound
crypto   dropped.txt    ipc       MAINTAINERS  REPORTING-BUGS  tools
root@ubuntu:/home/nate# export CONCURRENCY_LEVEL=3
root@ubuntu:/home/nate# make-kpkg clean
We do not seem to be in a top level linux kernel source directory
tree. Since we are trying to make a kernel package, that does not make
sense.  Please change directory to a top level linux kernel source
directory, and try again. (If I am wrong, and this is indeed a top
level linux kernel source directory, then I have gotten sadly out of
date with current kernels, and you should upgrade kernel-package)
root@ubuntu:/home/nate# 

```

---

### Post by jonathon6017 on 2011-06-05
you have to use the command cd to enter a directory so use 
cd /root/source/linux-2.6.38

---

### Post by jonathon6017 on 2011-06-05
you have to use the command cd to enter a directory so use 
cd /root/source/linux-2.6.38

---

### Post by silverhaze06 on 2011-06-05
its in the directory now, but getting these errors now.

```
root@ubuntu:/home/nate# cd /root/source/linux-2.6.38
root@ubuntu:~/source/linux-2.6.38# export CONCURRENCY_LEVEL=3
root@ubuntu:~/source/linux-2.6.38# make-kpkg clean
exec make kpkg_version=12.036+nmu1 -f /usr/share/kernel-package/ruleset/minimal.mk clean 
====== making target minimal_clean [new prereqs: ]======
This is kernel package version 12.036+nmu1.
test ! -f .config || cp -pf .config config.precious
cp: cannot create regular file `config.precious': Read-only file system
make: *** [minimal_clean] Error 1
root@ubuntu:~/source/linux-2.6.38# fakeroot make-kpkg --initrd --append-to-version=-tuxsage kernel-image kernel-headers
exec make kpkg_version=12.036+nmu1 -f /usr/share/kernel-package/ruleset/minimal.mk debian APPEND_TO_VERSION=-tuxsage  INITRD=YES 
====== making target debian/stamp/conf/minimal_debian [new prereqs: ]======
This is kernel package version 12.036+nmu1.
test -d debian             || mkdir debian
mkdir: cannot create directory `debian': Read-only file system
make: *** [debian/stamp/conf/minimal_debian] Error 1
Failed to create a ./debian directory: No such file or directory at /usr/bin/make-kpkg line 984.
root@ubuntu:~/source/linux-2.6.38# 

```

---

### Post by jonathon6017 on 2011-06-05
Honestly I have no idea how to solve this error. I never had this error myself. The first half of it is telling you that you are in a read only file system which I don't understand since you are in a linux filesystem and you are root but the second one (Failed to create a ./debian directory: No such file or directory at /usr/bin/make-kpkg line 984.) is telling you that something don't exist which also don't make sense cause that directory and file DOES exist. I'm gonna look into this some more and see what I can find.

---

### Post by silverhaze06 on 2011-06-05
ok, well if anyone else reading this knows the solution, please let us know!

---

### Post by silverhaze06 on 2011-06-05
i think the computer freezing during the recompile might have screwed everything up, because most of my programs are not working that well right now. lots of stuff in the windows not showing up...

---

### Post by silverhaze06 on 2011-06-05
ok, never mind, i rebooted my computer again and now its back to normal, and recompiling. i turned off the screen saver this time so hopefully ill be done next time i post.

---

### Post by jonathon6017 on 2011-06-05
I'll keep watching the thread just post an update

---

### Post by silverhaze06 on 2011-06-05
well it froze again, even tho screen saver is not activated.
 trying again, if you could just post the steps i need to take after this, that would be great. otherwise this will just take forever for both of us.

---

### Post by jonathon6017 on 2011-06-05
Well idk if it will work (actually I'm 99% sure it won't) but....

cd /root/source

dpkg -i linux-image-2.6.38.(press tab then press enter)

dpkg -i linux-headers-2.6.38.(press tab then press enter)

update-initramfs -c -k 2.6.38+tuxsage(press tab then enter)

update-grub

---

### Post by silverhaze06 on 2011-06-05
well it seems to be getting further along each time so far, so hopefully after 1,000 times this will work! ](*,)

---

### Post by jonathon6017 on 2011-06-05
lol ok

---

### Post by silverhaze06 on 2011-06-06
ok, it just keeps on freezing and the background goes from the shades of grey that its supposed to be, to red, blue, green and yellow, like it got set back to 256 colors or even less. anyone know why? or if this will ever work?

---

### Post by techinterplay on 2011-07-31
Did you manage to fix the output of  'iasl -tc DSDT.dsl' before proceeding to further steps? It should give you results something like below

iasl -tc DSDT.dsl

******************************************

DSDT.dsl 12903:             Method (BTST, 0, NotSerialized)
Warning  1088 -                        ^ Not all control paths return a value (BTST)

ASL Input:  DSDT.dsl - 13006 lines, 476649 bytes, 5461 keywords
AML Output: DSDT.aml - 49221 bytes, 1128 named objects, 4333 executable opcodes

Compilation complete. 0 Errors, 3 Warnings, 32 Remarks, 6 Optimizations
***********************************************

I dint read the whole thread one by one as its just a long one :D Is glad to see [matt_symes]("http://ubuntuforums.org/member.php?u=1067998") and [jonathon6017]("http://ubuntuforums.org/member.php?u=1310063") efforts to help the fellow Ubuntu users :-)

---

### Post by volcom7205 on 2011-08-09
> **jonathon6017 said:**
> Well idk if it will work (actually I'm 99% sure it won't) but....

cd /root/source

_**dpkg -i linux-image-2.6.38.(press tab then press enter)**_

dpkg -i linux-headers-2.6.38.(press tab then press enter)

update-initramfs -c -k 2.6.38+tuxsage(press tab then enter)

update-grub


sorry to hijack this post but i have followed and made it this far. this commands do not work for me i get when i type the bold in above
root@ubuntu:~/source# dpkg -i linux-image-2.6.38.
dpkg: error processing linux-image-2.6.38. (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-image-2.6.38.

---

