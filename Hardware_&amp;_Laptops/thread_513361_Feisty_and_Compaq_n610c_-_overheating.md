---
title: "Feisty and Compaq n610c - overheating"
date: 2007-07-30
forum: Hardware &amp; Laptops
---

### Post by spottraining on 2007-07-30
Hi

Something is really wrong with Ubuntu Feisty acpi support. In Ubuntu 6.06 I don't have any problems with my laptop overheating and fan control. Now with Feisty - this is main problem. Cooling fan does not starts, when its needed. Right now I have fallowing temperatures:
suvi@lapakas:~$ acpi -t
     Battery 1: discharging, 86%, 03:16:22 remaining
     Thermal 1: ok, 70.0 degrees C
     Thermal 2: ok, 45.0 degrees C
And it is hot again. And fan don't starts. Sometimes its starts - sometimes not. Its really strange. There was before long time Ubuntu 6.06 and with that I dont have any problems.

So - what I can to with acpi, so that its starts again normal to work with fans.

---

### Post by spottraining on 2007-07-31
Is the only possible thing to replace Ubuntu with other distribution?

---

### Post by Aparatey on 2007-07-31
Hello spottraining!

Please could you run the folowing commands and post the output, please?

dmesg | grep "ACPI"


find /proc/acpi -type f -perm -04 | xargs head 


                               Good Luck


                                        Aparatey

---

### Post by spottraining on 2007-07-31
First output:
suvi@lapakas:~$ dmesg | grep "ACPI"
[    0.000000]  BIOS-e820: 000000002fff0c00 - 000000002fffc000 (ACPI NVS)
[   18.609113] ACPI: Interpreter disabled.
[   18.609138] pnp: PnP ACPI: disabled
[   18.609624] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO

Second:
suvi@lapakas:~$ find /proc/acpi -type f -perm -04 | xargs head
find: /proc/acpi: No such file or directory


I have check from Ubuntu Feisty bugs and I have find also other peopols with same problems.

In my laptop - In first start fan works fine. After suspend will starts problem - some times fan starts - some times not. 
Before was Dapper - and all works fine, before that Brezy and also no problem with overheating. Fancontrol works out of the box.

---

### Post by spottraining on 2007-08-01
Previous outputs are wrong. I install other kernel and so the acpi was set off (LiveCD don't start with acpi). Now its again on and outputs are:
suvi@lapakas:~$ dmesg | grep "ACPI"
[    0.000000]  BIOS-e820: 000000002fff0c00 - 000000002fffc000 (ACPI NVS)
[    0.000000] ACPI: RSDP (v000 COMPAQ                                ) @ 0x000f6990
[    0.000000] ACPI: RSDT (v001 COMPAQ CPQ00B7  0x31050220 CPQ  0x00000001) @ 0x2fff0c84
[    0.000000] ACPI: FADT (v002 COMPAQ CPQ00B7  0x00000002 CPQ  0x00000001) @ 0x2fff0c00
[    0.000000] ACPI: DSDT (v001 COMPAQ EVON610C 0x00010000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[   17.309372] ACPI: Core revision 20060707
[   17.310756] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   17.316086] ACPI: setting ELCR to 0200 (from 0c00)
[   17.351139] ACPI: bus type pci registered
[   17.377928] ACPI: Interpreter enabled
[   17.377936] ACPI: Using PIC for interrupt routing
[   17.378601] ACPI: PCI Root Bridge [C03A] (0000:00)
[   17.378653] ACPI: Assume root bridge [\_SB_.C03A] bus is 0
[   17.386141] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[   17.387460] ACPI: PCI Interrupt Routing Table [\_SB_.C03A._PRT]
[   17.399853] ACPI: PCI Interrupt Routing Table [\_SB_.C03A.C03B._PRT]
[   17.400069] ACPI: PCI Interrupt Routing Table [\_SB_.C03A.C04D._PRT]
[   17.405198] ACPI: Power Resource [C148] (on)
[   17.408940] ACPI: Power Resource [C15C] (on)
[   17.411949] ACPI: Power Resource [C160] (on)
[   17.414956] ACPI: Power Resource [C163] (on)
[   17.415709] ACPI: Power Resource [C16C] (on)
[   17.418664] ACPI: PCI Interrupt Link [C0B5] (IRQs 5 10 *11)
[   17.419594] ACPI: PCI Interrupt Link [C0B6] (IRQs 5 10 *11)
[   17.420507] ACPI: PCI Interrupt Link [C0B7] (IRQs 5 10 11) *0, disabled.
[   17.421441] ACPI: PCI Interrupt Link [C0B8] (IRQs 5 10 *11)
[   17.422379] ACPI: PCI Interrupt Link [C0B9] (IRQs 5 *10 11)
[   17.423043] ACPI: Blank IRQ resource
[   17.423048] ACPI: Resource is not an IRQ entry
[   17.423340] ACPI: PCI Interrupt Link [C0BA] (IRQs) *0, disabled.
[   17.424003] ACPI: Blank IRQ resource
[   17.424007] ACPI: Resource is not an IRQ entry
[   17.424295] ACPI: PCI Interrupt Link [C0BB] (IRQs) *0, disabled.
[   17.424955] ACPI: Blank IRQ resource
[   17.424960] ACPI: Resource is not an IRQ entry
[   17.425245] ACPI: PCI Interrupt Link [C0BC] (IRQs) *0, disabled.
[   17.427998] ACPI: Power Resource [C1D7] (off)
[   17.428276] ACPI: Power Resource [C1D8] (off)
[   17.428550] ACPI: Power Resource [C1D9] (off)
[   17.429031] pnp: PnP ACPI init
[   17.461417] pnp: PnP ACPI: found 15 devices
[   17.461427] PnPBIOS: Disabled by ACPI PNP
[   17.461530] PCI: Using ACPI for IRQ routing
[   17.526995] ACPI: PCI Interrupt Link [C0B8] enabled at IRQ 11
[   17.527008] ACPI: PCI Interrupt 0000:02:06.0[A] -> Link [C0B8] -> GSI 11 (level, low) -> IRQ 11
[   17.527039] ACPI: PCI Interrupt 0000:02:06.1[A] -> Link [C0B8] -> GSI 11 (level, low) -> IRQ 11
[   19.361767] ACPI: (supports S0 S3 S4 S5)
[   21.517572] ACPI: Transitioning device [C1DA] to D3
[   21.517579] ACPI: Transitioning device [C1DA] to D3
[   21.517588] ACPI: Fan [C1DA] (off)
[   21.517986] ACPI: Transitioning device [C1DB] to D3
[   21.517991] ACPI: Transitioning device [C1DB] to D3
[   21.517998] ACPI: Fan [C1DB] (off)
[   21.518394] ACPI: Transitioning device [C1DC] to D3
[   21.518399] ACPI: Transitioning device [C1DC] to D3
[   21.518406] ACPI: Fan [C1DC] (off)
[   21.526305] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   21.526319] ACPI: Processor [C000] (supports 8 throttling states)
[   21.544761] ACPI: Thermal Zone [TZ1] (51 C)
[   21.546510] ACPI: Thermal Zone [C1D6] (45 C)
[   22.781325] ACPI: PCI Interrupt Link [C0B7] enabled at IRQ 10
[   22.781338] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [C0B7] -> GSI 10 (level, low) -> IRQ 10
[    7.156000] ACPI: PCI Interrupt Link [C0B9] enabled at IRQ 10
[    7.156000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [C0B9] -> GSI 10 (level, low) -> IRQ 10
[    7.256000] ACPI: PCI Interrupt 0000:02:0e.2[C] -> Link [C0B9] -> GSI 10 (level, low) -> IRQ 10
[    7.384000] ACPI: PCI Interrupt 0000:02:0e.0[A] -> Link [C0B9] -> GSI 10 (level, low) -> IRQ 10
[    8.464000] ACPI: PCI Interrupt 0000:02:0e.1[B] -> Link [C0B9] -> GSI 10 (level, low) -> IRQ 10
[   29.828000] ACPI: PCI Interrupt Link [C0B6] enabled at IRQ 11
[   29.828000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [C0B6] -> GSI 11 (level, low) -> IRQ 11
[  142.528000] ACPI: Battery Slot [C184] (battery present)
[  142.528000] ACPI: Battery Slot [C185] (battery absent)
[  142.672000] ACPI: Power Button (FF) [PWRF]
[  142.672000] ACPI: Sleep Button (CM) [C187]
[  142.672000] ACPI: Lid Switch [C188]
[  143.112000] ACPI: AC Adapter [C186] (on-line)
[  149.152000] ACPI: PCI Interrupt Link [C0B5] enabled at IRQ 11
[  149.152000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [C0B5] -> GSI 11 (level, low) -> IRQ 11
[  149.912000] apm: overridden by ACPI.
[  299.540000] ACPI: PCI interrupt for device 0000:02:08.0 disabled
[  307.032000] ACPI: PCI interrupt for device 0000:02:0e.2 disabled
[  307.048000] ACPI: PCI interrupt for device 0000:02:0e.1 disabled
[  307.064000] ACPI: PCI interrupt for device 0000:02:0e.0 disabled
[  307.080000] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
[  307.080000] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[14125.136000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [C0B7] -> GSI 10 (level, low) -> IRQ 10
[14125.140000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [C0B6] -> GSI 11 (level, low) -> IRQ 11
[14125.496000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [C0B5] -> GSI 11 (level, low) -> IRQ 11
[14125.512000] ACPI: PCI Interrupt 0000:02:0e.0[A] -> Link [C0B9] -> GSI 10 (level, low) -> IRQ 10
[14125.528000] ACPI: PCI Interrupt 0000:02:0e.1[B] -> Link [C0B9] -> GSI 10 (level, low) -> IRQ 10
[14125.544000] ACPI: PCI Interrupt 0000:02:0e.2[C] -> Link [C0B9] -> GSI 10 (level, low) -> IRQ 10
[14139.796000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [C0B9] -> GSI 10 (level, low) -> IRQ 10
[14146.308000] ACPI: Power Button (FF) [PWRF]
[14146.308000] ACPI: Sleep Button (CM) [C187]
[14146.308000] ACPI: Lid Switch [C188]
[14147.400000] ACPI: Transitioning device [C1DA] to D3
[14147.400000] ACPI: Transitioning device [C1DA] to D3
[14147.400000] ACPI: Fan [C1DA] (off)
[14147.400000] ACPI: Transitioning device [C1DB] to D3
[14147.400000] ACPI: Transitioning device [C1DB] to D3
[14147.400000] ACPI: Fan [C1DB] (off)
[14147.408000] ACPI: Fan [C1DC] (on)
[14147.432000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[14147.432000] ACPI: Processor [C000] (supports 8 throttling states)
[14147.448000] ACPI: Thermal Zone [TZ1] (31 C)
[14147.452000] ACPI: Thermal Zone [C1D6] (45 C)
[14147.548000] ACPI: AC Adapter [C186] (on-line)
[14147.600000] ACPI: Battery Slot [C184] (battery present)
[14147.604000] ACPI: Battery Slot [C185] (battery absent)
[21325.820000] ACPI: PCI interrupt for device 0000:02:08.0 disabled
[21334.348000] ACPI: PCI interrupt for device 0000:02:0e.2 disabled
[21334.364000] ACPI: PCI interrupt for device 0000:02:0e.1 disabled
[21334.380000] ACPI: PCI interrupt for device 0000:02:0e.0 disabled
[21334.396000] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
[21334.396000] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[25523.452000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [C0B7] -> GSI 10 (level, low) -> IRQ 10
[25523.456000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [C0B6] -> GSI 11 (level, low) -> IRQ 11
[25523.812000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [C0B5] -> GSI 11 (level, low) -> IRQ 11
[25523.828000] ACPI: PCI Interrupt 0000:02:0e.0[A] -> Link [C0B9] -> GSI 10 (level, low) -> IRQ 10
[25523.844000] ACPI: PCI Interrupt 0000:02:0e.1[B] -> Link [C0B9] -> GSI 10 (level, low) -> IRQ 10
[25523.860000] ACPI: PCI Interrupt 0000:02:0e.2[C] -> Link [C0B9] -> GSI 10 (level, low) -> IRQ 10
[25536.144000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [C0B9] -> GSI 10 (level, low) -> IRQ 10
[25542.812000] ACPI: Power Button (FF) [PWRF]
[25542.812000] ACPI: Sleep Button (CM) [C187]
[25542.812000] ACPI: Lid Switch [C188]
[25543.948000] ACPI: Transitioning device [C1DA] to D3
[25543.948000] ACPI: Transitioning device [C1DA] to D3
[25543.952000] ACPI: Fan [C1DA] (off)
[25543.956000] ACPI: Fan [C1DB] (on)
[25543.968000] ACPI: Fan [C1DC] (on)
[25544.000000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[25544.000000] ACPI: Processor [C000] (supports 8 throttling states)
[25544.016000] ACPI: Thermal Zone [TZ1] (69 C)
[25544.016000] ACPI: Thermal Zone [C1D6] (45 C)
[25544.164000] ACPI: AC Adapter [C186] (on-line)
[25544.216000] ACPI: Battery Slot [C184] (battery present)
[25544.216000] ACPI: Battery Slot [C185] (battery absent)
suvi@lapakas:~$ 

and second:

suvi@lapakas:~$ find /proc/acpi -type f -perm -04 | xargs head 
==> /proc/acpi/thermal_zone/C1D6/polling_frequency <==
<polling disabled>

==> /proc/acpi/thermal_zone/C1D6/cooling_mode <==
<setting not supported>
cooling mode:   passive

==> /proc/acpi/thermal_zone/C1D6/trip_points <==
critical (S5):           94 C
passive:                 50 C: tc1=1 tc2=2 tsp=300 devices=0xeed8b338 

==> /proc/acpi/thermal_zone/C1D6/temperature <==
temperature:             45 C

==> /proc/acpi/thermal_zone/C1D6/state <==
state:                   ok

==> /proc/acpi/thermal_zone/TZ1/polling_frequency <==
<polling disabled>

==> /proc/acpi/thermal_zone/TZ1/cooling_mode <==
<setting not supported>
cooling mode:   active

==> /proc/acpi/thermal_zone/TZ1/trip_points <==
critical (S5):           94 C
passive:                 92 C: tc1=1 tc2=2 tsp=100 devices=0xeed8b338 
active[0]:               80 C: devices=0xeed983ec 
active[1]:               65 C: devices=0xeed98388 
active[2]:               16 C: devices=0xeed98338 

==> /proc/acpi/thermal_zone/TZ1/temperature <==
temperature:             47 C

==> /proc/acpi/thermal_zone/TZ1/state <==
state:                   active[2]

==> /proc/acpi/processor/C000/power <==
active state:            C2
max_cstate:              C8
bus master activity:     feffcfaf
maximum allowed latency: 8000 usec
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[001] usage[00001470] duration[00000000000000000000]
   *C2:                  type[C2] promotion[C3] demotion[C1] latency[002] usage[00096764] duration[00000000000968150054]
    C3:                  type[C3] promotion[--] demotion[C2] latency[185] usage[00000000] duration[00000000000000000000]

==> /proc/acpi/processor/C000/limit <==
active limit:            P0:T0
user limit:              P0:T0
thermal limit:           P0:T0

==> /proc/acpi/processor/C000/throttling <==
state count:             8
active state:            T0
states:
   *T0:                  00%
    T1:                  12%
    T2:                  25%
    T3:                  37%
    T4:                  50%
    T5:                  62%
    T6:                  75%

==> /proc/acpi/processor/C000/info <==
processor id:            0
acpi id:                 1
bus mastering control:   yes
power management:        yes
throttling control:      yes
limit interface:         yes

==> /proc/acpi/fan/C1DC/state <==
status:                  off

==> /proc/acpi/fan/C1DB/state <==
status:                  off

==> /proc/acpi/fan/C1DA/state <==
status:                  off

==> /proc/acpi/button/lid/C188/state <==
state:      open

==> /proc/acpi/button/lid/C188/info <==
type:                    Lid Switch

==> /proc/acpi/button/sleep/C187/info <==
type:                    Sleep Button (CM)

==> /proc/acpi/button/power/PWRF/info <==
type:                    Power Button (FF)

==> /proc/acpi/ac_adapter/C186/state <==
state:                   off-line

==> /proc/acpi/battery/C185/alarm <==
present:                 no

==> /proc/acpi/battery/C185/state <==
present:                 no

==> /proc/acpi/battery/C185/info <==
present:                 no

==> /proc/acpi/battery/C184/alarm <==
alarm:                   unsupported

==> /proc/acpi/battery/C184/state <==
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            14000 mW
remaining capacity:      51869 mWh
present voltage:         16387 mV

==> /proc/acpi/battery/C184/info <==
present:                 yes
design capacity:         54720 mWh
last full capacity:      53140 mWh
battery technology:      rechargeable
design voltage:          15999 mV
design capacity warning: 0 mWh
design capacity low:     0 mWh
capacity granularity 1:  10 mWh
capacity granularity 2:  10 mWh
model number:            Primary

==> /proc/acpi/wakeup <==
Device  Sleep state     Status
C04D       5            disabled
C09F       3            disabled
C0A5       3            disabled
C0A8       3            disabled
C184       3            disabled
C185       3            disabled
C187       4            * enabled
C188       4            * enabled

==> /proc/acpi/alarm <==
2007-08-00 16:03:00

==> /proc/acpi/sleep <==
S0 S3 S4 S5 

==> /proc/acpi/info <==
version:                 20060707

==> /proc/acpi/power_resource/C1D9/state <==
state:                   off
system level:            S0
order:                   0
reference count:         0

==> /proc/acpi/power_resource/C1D8/state <==
state:                   off
system level:            S0
order:                   0
reference count:         0

==> /proc/acpi/power_resource/C1D7/state <==
state:                   off
system level:            S0
order:                   0
reference count:         0

==> /proc/acpi/power_resource/C16C/state <==
state:                   off
system level:            S0
order:                   0
reference count:         0

==> /proc/acpi/power_resource/C163/state <==
state:                   off
system level:            S0
order:                   0
reference count:         0

==> /proc/acpi/power_resource/C160/state <==
state:                   off
system level:            S0
order:                   0
reference count:         0

==> /proc/acpi/power_resource/C15C/state <==
state:                   off
system level:            S0
order:                   0
reference count:         0

==> /proc/acpi/power_resource/C148/state <==
state:                   off
system level:            S0
order:                   0
reference count:         0
suvi@lapakas:~$ 



And right now - fan is not working.

---

### Post by Aparatey on 2007-08-01
Hello spottraining!

Mmnnn... the polling is disabled, so the ACPI don't refresh the current temperature. And the C1D6 zone don't have an active temperature.

Please run the followings commands :

echo 30 > /proc/acpi/thermal_zone/TZ1/polling_frequency
echo 30 > /proc/acpi/thermal_zone/C1D6/polling_frequency
echo 94:0:80:65:40 > /proc/acpi/thermal_zone/C1D6/trip_points

With these commands every 30 seconds the sensors should read the temperature again.

And use the laptop for a while. When the sensors reached the 65 Celcius the fan should be activated. 

Also you can try to start the fans manually with the following commands :

echo 0 > /proc/acpi/fan/C1DC/state
echo 0 > /proc/acpi/fan/C1DB/state
echo 0 > /proc/acpi/fan/C1DA/state

To turn off the fans :

echo 3 > /proc/acpi/fan/C1DC/state
echo 3 > /proc/acpi/fan/C1DB/state
echo 3 > /proc/acpi/fan/C1DA/state

Please try the commands and get my posted.

Good Luck!


                                              Aparatey

---

### Post by spottraining on 2007-08-05
Two days - everything works fine. Today I make restart and now is again problems (acpi works). When I giving previously given commands, then I am getting permission denied errors:

suvi@lapakas:~$ echo 0 > /proc/acpi/fan/C1DC/state
bash: /proc/acpi/fan/C1DC/state: Permission denied
suvi@lapakas:~$ sudo echo 0 > /proc/acpi/fan/C1DC/state
bash: /proc/acpi/fan/C1DC/state: Permission denied
suvi@lapakas:~$ echo 30 > /proc/acpi/thermal_zone/TZ1/polling_frequency
bash: /proc/acpi/thermal_zone/TZ1/polling_frequency: Permission denied
suvi@lapakas:~$ sudo echo 30 > /proc/acpi/thermal_zone/TZ1/polling_frequency
bash: /proc/acpi/thermal_zone/TZ1/polling_frequency: Permission denied
suvi@lapakas:~$

---

### Post by Aparatey on 2007-08-16
Hello spottraining!

Did you try to run the command as root?
If not use :
sudo echo 30 > /proc/acpi/thermal_zone/TZ1/polling_frequency
sudo echo 30 > /proc/acpi/thermal_zone/C1D6/polling_frequency
sudo echo 94:0:80:65:40 > /proc/acpi/thermal_zone/C1D6/trip_points

Good Luck!

Aparatey

---

### Post by spottraining on 2007-08-17
Hi

How you can see - yes - I am using also sudo - still premission denyed. 

But this thread is not so important any more for me - I have now IBM T40 and this works fine. 

But this is strange, that laptop, what before works like charm has problems with feisty.

---

