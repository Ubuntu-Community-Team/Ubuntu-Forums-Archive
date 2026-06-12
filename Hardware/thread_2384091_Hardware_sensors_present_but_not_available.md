---
title: "Hardware sensors present but not available"
date: 2018-02-02
forum: Hardware
---

### Post by SageOfSmeg on 2018-02-02
I have a very old desktop machine (c.1999) dual booting:

 - lubuntu 14.04.5 LTS, Trusty (3.13.0-141-generic) – the latest that will run on this PC
 - Windows98 (original/gold version)
 
 
 I wish to access the hardware temperature measurements for the motherboard and CPU.  
 
 
 Under Windows98 I have some software “MBProbe” that detects and monitors sensors.  
 The utility shows the following information…
  .     MBProbe 1.31 Beta 9
  .     Pentium II .25µ
  .     Family 6 Model 5 Stepping 2, 2.00V
  .     SMBUS: ALiM1543C port 440h
  .     Sensors: GL520SM rev 0h SMBus address 2Dh
  .     Temperature Sensors...
  .          - Motherboard: GL520SM:1
  .          - CPU: GL520SM:2
 This utility successfully monitors the temperatures in which I am interested, so obviously the mobo can access the sensor data.
 
 
 However, under linux the sensors cannot be detected/found using “lmsensors”, “sensors-detect” and so on. 
Psensor was only able to monitor CPU usage, it was not detecting CPU or MB temperatures, nor any fan speeds.

 Sadly, MBProbe will not run with linux wine due to missing components/libraries.
 
 
 Can anyone provide me with step-by-step instructions on how to access the desired sensor values in linux?
 Thanks.
 
 
 ------------------------------
 
 
 HARDWARE INFO:
  .     Motherboard details...
  .     - PC100 "PC-Chips Motherboard M726", M726 V3.3
  .       ([http://www.maitmbn.com/unisia/product/motherboard/slot1/m726.html](http://www.maitmbn.com/unisia/product/motherboard/slot1/m726.html))
  .     CPU details...
  .     - Pentium II 350 MHz - 350/512/100/2.0V S1 '97 SL356
  .     RAM details...
  .     - Memory: 768MB SDRAM (maximum possible using all slots)
  .     Other...
  .     - BIOS Identification: AMIBIOS(C)1996 American Megatrends Inc. Release: 10/20/1998 S

---

### Post by Yellow Pasque on 2018-02-02
Try and load the module manually and see what happens:
```
sudo modprobe -v gl520sm
sensors
dmesg | tail -n 20
```

---

### Post by SageOfSmeg on 2018-02-03
Results...

```
sudo modprobe -v gl520sm
[sudo] password for gjd: 
insmod /lib/modules/3.13.0-141-generic/kernel/drivers/hwmon/hwmon-vid.ko 
insmod /lib/modules/3.13.0-141-generic/kernel/drivers/hwmon/gl520sm.ko 

```

```
gjd@gjdpc1:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.

```

```
gjd@gjdpc1:~$ dmesg | tail -n 20
[   50.008261] type=1400 audit(1517617599.989:15): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-previewer" pid=941 comm="apparmor_parser"
[   50.008316] type=1400 audit(1517617599.989:16): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=941 comm="apparmor_parser"
[   50.008372] type=1400 audit(1517617599.989:17): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/evince-thumbnailer" pid=941 comm="apparmor_parser"
[   53.583594] tulip 0000:00:12.0 eth0: tulip_stop_rxtx() failed (CSR5 0xfc664010 CSR6 0xff972113)
[   53.583647] net eth0: Setting full-duplex based on MII#1 link partner capability of 45e1
[   63.336824] nf_conntrack: automatic helper assignment is deprecated and it will be removed soon. Use the iptables CT target to attach helpers instead.
[   70.567891] init: plymouth-upstart-bridge main process ended, respawning
[   70.792554] init: plymouth-upstart-bridge main process (1276) terminated with status 1
[   70.792719] init: plymouth-upstart-bridge main process ended, respawning
[   74.587177] init: plymouth-stop pre-start process (1365) terminated with status 1
[  129.955892] Netfilter messages via NETLINK v0.30.
[  137.657854] cfg80211: Calling CRDA to update world regulatory domain
[  137.815672] cfg80211: World regulatory domain updated:
[  137.815723] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  137.815744] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  137.815763] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  137.815779] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  137.815796] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  137.815813] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  142.903980] device eth0 entered promiscuous mode

```


Additionally...
```
gjd@gjdpc1:~$ sudo sensors-detect
# sensors-detect revision 6170 (2013-05-20 21:25:22 +0200)
# Board: Acer Lab Inc. Aladdin Pro

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): yes
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           No
AMD Family 15h power sensors...                             No
AMD Family 16h power sensors...                             No
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): yes
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): yes
Sorry, no supported PCI bus adapters found.
Module i2c-dev loaded successfully.

Sorry, no sensors were detected.
Either your system has no sensors, or they are not supported, or
they are connected to an I2C or SMBus adapter that is not
supported. If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.
gjd@gjdpc1:~$ 

```

It appears as if I am out of luck!

---

### Post by Yellow Pasque on 2018-02-03
Maybe you also need to load smbus module manually:
```
sudo modprobe -v i2c-ali15x3 gl520sm
```

See documentation here:
[https://www.mjmwired.net/kernel/Documentation/i2c/busses/i2c-ali15x3](https://www.mjmwired.net/kernel/Documentation/i2c/busses/i2c-ali15x3)

---

### Post by SageOfSmeg on 2018-02-08
I have tried this and still no luck according to sensors-detect. 
The machine is running headless at the moment but I shall take a closer look over the next few days.

Will it be necessary to repeat all of the aforementioned module/bus/probe loads every time the machine reboots?

---

### Post by Yellow Pasque on 2018-02-08
You can put modules you want to load automatically in /etc/modules

Did you look to see if the appropriate devices show up in lspci output?

---

### Post by SageOfSmeg on 2018-02-09
```
gjd@gjdpc1:~$ lspci
00:00.0 Host bridge: ULi Electronics Inc. M1621 (rev 05)
00:01.0 PCI bridge: ULi Electronics Inc. PCI to AGP Controller (rev 01)
00:02.0 USB controller: ULi Electronics Inc. USB 1.1 Controller (rev 03)
00:07.0 ISA bridge: ULi Electronics Inc. M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+] (rev b4)
00:0f.0 IDE interface: ULi Electronics Inc. M5229 IDE (rev 20)
00:10.0 Communication controller: Conexant Systems, Inc. HCF 56k Data/Fax/Voice Modem (rev 08)
00:12.0 Ethernet controller: 3Com Corporation 3CSOHO100B-TX 910-A01 [tulip] (rev 31)
01:00.0 VGA compatible controller: NVidia / SGS Thomson (Joint Venture) Riva128 (rev 22)
gjd@gjdpc1:~$ 
```


I guess still no luck.

---

### Post by Yellow Pasque on 2018-02-09
Make sure appropriate options are enabled in BIOS.
[https://www.mjmwired.net/kernel/Documentation/i2c/busses/i2c-ali15x3#69](https://www.mjmwired.net/kernel/Documentation/i2c/busses/i2c-ali15x3#69)

```
** If you see the 1533 and 5229 devices but NOT the 7101 device,
** then you must enable ACPI, the PMU, SMB, or something similar
** in the BIOS.
** The driver won't work if it can't find the M7101 device.
```

---

### Post by SageOfSmeg on 2018-02-10
Wouldn't they already be enabled in the BIOS if the sensors can be detected in Windows98 but not Linux?

---

### Post by Yellow Pasque on 2018-02-10
> **SageOfSmeg said:**
> Wouldn't they already be enabled in the BIOS if the sensors can be detected in Windows98 but not Linux?

I would think so. I'm out of good suggestions. The only ideas I have are to look through dmesg and see if your BIOS has a setting for OS. IIRC, some of these old mobos had an OS setting like "Win98/ME, Win2000, Other"

---

### Post by SageOfSmeg on 2018-02-12
Having looked in the BIOS there are no entries for ACPI, PMU, SMB or WIndows98 (or similar).

Psensor can detect the CPU usage but not the fan speeds or temperature sensors, which is what I wanted because I plan to place the machine up in the loft where it can get pretty hot in the summer and being able to monitor the temperatures might have given me some advance warning of overheating.

Well I give up!
Being that it is such an old machine I think I have spent enough time on this issue.

Thanks for all the help.

---

