---
title: "lm-sensors on 12.04.2"
date: 2013-05-04
forum: Hardware
---

### Post by thatguymark on 2013-05-04
I've followed the usual instructions and got the following. Sorry for the lengthy quotes but I just want to make sure to include all the relevant info.

Hardware made sense in my mind but apologies if this is the wrong forum, I will move it if I can or if any mod wants to...

```
user@user-MS-6728:~$ sudo sensors-detect
# sensors-detect revision 5984 (2011-07-10 21:22:53 +0200)
# System: MICRO-STAR INC. MS-6728

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): 
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
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes
Found `Winbond W83627THF/THG Super IO Sensors'              Success!
    (address 0x290, driver `w83627hf')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               Yes
Found unknown chip with ID 0xf7f7

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): 
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): 

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): 
Using driver `i2c-i801' for device 0000:00:1f.3: Intel 82801EB ICH5
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.

Next adapter: NVIDIA i2c adapter  (i2c-0)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x4a
Probing for `National Semiconductor LM75'...                No
Probing for `National Semiconductor LM75A'...               No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Analog Devices ADT7410'...                     No
Probing for `Analog Devices ADT7411'...                     No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Maxim MAX6642'...                              No
Probing for `National Semiconductor LM73'...                No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `NXP/Philips SA56004'...                        No
Client found at address 0x4b
Probing for `National Semiconductor LM75'...                No
Probing for `National Semiconductor LM75A'...               No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Analog Devices ADT7410'...                     No
Probing for `Analog Devices ADT7411'...                     No
Probing for `Dallas Semiconductor DS1621/DS1631'...         No
Probing for `Maxim MAX6642'...                              No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `NXP/Philips SA56004'...                        No
Probing for `Analog Devices ADT7481'...                     No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): 

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `w83627hf':
  * ISA bus, address 0x290
    Chip `Winbond W83627THF/THG Super IO Sensors' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
w83627hf
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)yes
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run 'service module-init-tools start'
to load them.

Unloading i2c-dev... OK
Unloading i2c-i801... OK
Unloading cpuid... OK


```

And then: 
```
user@user-MS-6728:~$ sudo service module-init-tools restart 
stop: Unknown instance: 
module-init-tools stop/waiting

```

```
user@user-MS-6728:~$ sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
```

This is probably already pretty clear cut to someone who knows, but here is some other possibly relevant info in case it's needed. Thanks in advance for any help!

```

user@user-MS-6728:~$ lsmod
Module                  Size  Used by
vesafb                 13516  1 
bnep                   17830  2 
rfcomm                 38139  4 
bluetooth             158479  10 bnep,rfcomm
arc4                   12473  2 
rt2500pci              22948  0 
rt2x00pci              14237  1 rt2500pci
rt2x00lib              48875  2 rt2500pci,rt2x00pci
mac80211              436493  2 rt2x00pci,rt2x00lib
nvidia               7098356  24 
cfg80211              178877  2 rt2x00lib,mac80211
snd_intel8x0           33455  3 
snd_ac97_codec        110213  1 snd_intel8x0
psmouse                96718  0 
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
eeprom_93cx6           12687  1 rt2500pci
snd_rawmidi            25424  1 snd_seq_midi
serio_raw              13027  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62218  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13077  0 
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
shpchp                 32265  0 
ppdev                  12849  0 
parport_pc             32114  1 
hwmon_vid              12723  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
8139too                23283  0 
8139cp                 22633  0 
floppy                 60184  0 
```

```
user@user-MS-6728:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface [8086:2570] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82865G/PE/P AGP Bridge [8086:2571] (rev 02)
00:06.0 System peripheral [0880]: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface [8086:2576] (rev 02)
00:1d.0 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
00:1d.1 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
00:1d.2 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02)
00:1d.3 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
00:1d.7 USB controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation NV36 [GeForce FX 5700LE] [10de:0343] (rev a1)
02:02.0 Network controller [0280]: Ralink corp. RT2500 Wireless 802.11bg [1814:0201] (rev 01)
02:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
```

---

### Post by thatguymark on 2013-05-04
Found my answer here:

[http://ubuntuforums.org/showthread.php?t=1351956&p=8485676#post8485676](http://ubuntuforums.org/showthread.php?t=1351956&p=8485676#post8485676)

---

