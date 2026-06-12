---
title: "ACPI: battery-technology reported as non-rechargeable"
date: 2007-06-16
forum: Hardware &amp; Laptops
---

### Post by IntuitiveNipple on 2007-06-16
Feisty 7.04 32-bit kernel: 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

Sony Vaio VGN-FE41Z with standard Li-Ion battery.

Since the automatic kernel upgrade "linux-generic (2.6.20.15.14) to 2.6.20.16.28.1" I've been noticing some weird ACPI battery issues.

The Gnome Power Manager (v2.18.2) battery icon and power history charts often get very confused and/or behind-the-times reporting battery and AC adapter status. For example sometimes the battery will be 90% charged but the graphs will report only 2 minutes of charge remaining, or the battery will be charging but it will report the laptop is running on battery power, not charging. Actual lifetime of the hardware on battery remains the same as before. These false reports cause problems because the software wants to hibernate or shutdown the OS and keeps on displaying warnings.

In all cases there are no unusual ACPI messages in dmesg.

I decided to do some investigating today and discovered that according to acpi the battery type is "**non-rechargeable**" and also doesn't report 'Present rate'.

As a side-note, from these reports it is also apparent there is confusion between the hal and acpi modules over what constitutes 'battery technology' and 'battery type' and they appear to have swapped meanings of 'technology' in particular, which can lead to confusion.
 
On Battery:
```
$ acpitool -Bv
  Battery #1     : present
    Remaining capacity : 15510 mWh, 26.87%
    Design capacity    : 57720 mWh
    Last full capacity : 57720 mWh
    Present rate       : unknown
    Charging state     : discharging
    Battery type       : non-recharge, LiOn
```
With AC charger:
```
$ acpitool -Bv
  Battery #1     : present
    Remaining capacity : 10320 mWh, 17.88%
    Design capacity    : 57720 mWh
    Last full capacity : 57720 mWh
    Present rate       : unknown
    Charging state     : charging
    Battery type       : non-recharge, LiOn
```
Notice how it is managing to charge a '**non-recharge**' battery?

The "*non-recharge*" string should really be "non-rechargeable" but there is a truncation-bug in acpitools that limits the string to 13 characters (see my [bug report #120708](https://bugs.launchpad.net/ubuntu/+source/acpitool/+bug/120708) )

The actual output comes from:
```
$ grep -rn 'non-rechargeable' *
drivers/acpi/battery.c:376:             seq_printf(seq, "battery technology:      non-rechargeable\n");
```
And is reported by:
```
$ cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         57720 mWh
last full capacity:      57720 mWh
battery technology:      non-rechargeable
design voltage:          118530 mV
design capacity warning: 1000 mWh
design capacity low:     400 mWh
capacity granularity 1:  100 mWh
capacity granularity 2:  100 mWh
model number:            
serial number:           
battery type:            LiOn
OEM info:                Sony Corp.
```
However, lshal reports "**battery.is_rechargeable = true**" although from looking at the source of **hal-0.5.8.1/hald/linux/acpi.c** line 580:
```
  /* we are assuming a laptop battery is rechargeable */
  hal_device_property_set_bool (d, "battery.is_rechargeable", TRUE);
```
So it seems hal is guessing rather than checking the real device! I've reports this as [bug report #120721 ](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/120721)
```
$ lshal -lu /org/freedesktop/Hal/devices/acpi_BAT0
udi = '/org/freedesktop/Hal/devices/acpi_BAT0'
  battery.remaining_time = 3256  (0xcb8)  (int)
  info.udi = '/org/freedesktop/Hal/devices/acpi_BAT0'  (string)
  linux.hotplug_type = 4  (0x4)  (int)
  battery.charge_level.percentage = 29  (0x1d)  (int)
  battery.charge_level.rate = 0  (0x0)  (int)
  battery.charge_level.last_full = 57720  (0xe178)  (int)
  battery.charge_level.current = 17240  (0x4358)  (int)
  battery.reporting.rate = 0  (0x0)  (int)
  battery.reporting.current = 17240  (0x4358)  (int)
  battery.charge_level.capacity_state = 'ok'  (string)
  battery.rechargeable.is_discharging = true  (bool)
  battery.rechargeable.is_charging = false  (bool)
  battery.is_rechargeable = true  (bool)
  battery.charge_level.unit = 'mWh'  (string)
  battery.charge_level.granularity_2 = 100  (0x64)  (int)
  battery.charge_level.granularity_1 = 100  (0x64)  (int)
  battery.charge_level.low = 400  (0x190)  (int)
  battery.charge_level.warning = 1000  (0x3e8)  (int)
  battery.charge_level.design = 57720  (0xe178)  (int)
  battery.voltage.design = 116170  (0x1c5ca)  (int)
  battery.voltage.unit = 'mV'  (string)
  battery.reporting.granularity_2 = 100  (0x64)  (int)
  battery.reporting.granularity_1 = 100  (0x64)  (int)
  battery.reporting.low = 400  (0x190)  (int)
  battery.reporting.warning = 1000  (0x3e8)  (int)
  battery.reporting.design = 57720  (0xe178)  (int)
  battery.reporting.last_full = 57720  (0xe178)  (int)
  battery.reporting.unit = 'mWh'  (string)
  battery.technology = 'lithium-ion'  (string)
  battery.reporting.technology = 'LiOn'  (string)
  battery.vendor = 'Sony'  (string)
  battery.present = true  (bool)
  info.capabilities = {'battery'} (string list)
  info.category = 'battery'  (string)
  battery.type = 'primary'  (string)
  info.product = 'Battery Bay'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  linux.acpi_type = 0  (0x0)  (int)
  linux.acpi_path = '/proc/acpi/battery/BAT0'  (string)
```
The issue seems to stem from drivers/acpi/battery.c where it finds in acpi_battery_read_info() **bif->battery_technology** == 0 rather than 1.
```
  switch ((u32) bif->battery_technology) {
   case 0:
    seq_printf(seq, "battery technology:      non-rechargeable\n");
    break;
   case 1:
    seq_printf(seq, "battery technology:      rechargeable\n");
    break;
  default:
    seq_printf(seq, "battery technology:      unknown\n");
    break;
 }
```
bif is an acpi_battery_info structure
```
struct acpi_battery_info {
	acpi_integer power_unit;
	acpi_integer design_capacity;
	acpi_integer last_full_capacity;
	acpi_integer battery_technology;
	acpi_integer design_voltage;
	acpi_integer design_capacity_warning;
	acpi_integer design_capacity_low;
	acpi_integer battery_capacity_granularity_1;
	acpi_integer battery_capacity_granularity_2;
	acpi_string model_number;
	acpi_string serial_number;
	acpi_string battery_type;
	acpi_string oem_info;
};
```
populated via 
```
acpi_battery_get_info(battery, &bif)
```
with a call to drivers/acpi/namespace/nsxfeval.c
```
acpi_evaluate_object(battery->device->handle, "_BIF", NULL, &buffer)
```
acpi_battery_get_info() then calls drivers/acpi/utils.c 
```
  package = buffer.pointer;
  acpi_extract_package(package, &format, &data);
```
which uses 
```
  #define ACPI_BATTERY_FORMAT_BIF	"NNNNNNNNNSSSS"
  struct acpi_buffer format = { sizeof(ACPI_BATTERY_FORMAT_BIF), ACPI_BATTERY_FORMAT_BIF };
```
from drivers/acpi/battery.c to control what values it expects to interpret.

It extracts the value using
```
  case ACPI_TYPE_INTEGER:
   switch (format_string[i]) {
    case 'N':
     *((acpi_integer *) head) = element->integer.value;
     head += sizeof(acpi_integer);
     break;
```
So, at this point bif->battery_technology should be 1 not 0.

The ACPI specification v3.0 says:
> Battery Technology DWORD
 0x00000000 – Primary (for example, non-rechargeable)
 0x00000001 – Secondary (for example, rechargeable)

I have the BIOS DSDT decompiled as part of my sony-laptop driver development work, so I looked at the Battery _BIF method and discovered that Sony seem to have incorrectly (**read *BUG***) set the battery technology to **Zero** (non-rechargeable) rather than ***One*** (rechargeable)!

```
$ sudo apt-get install acpidump
$ sudo acpidump -b -t DSDT -o DSDT.aml
$ sudo apt-get install iasl
$ iasl -d DSDT.aml
```
In DSDT.dsl you can find something similar to this (I've added comments here) - search for "_BIF":
```
  Method (_BIF, 0, NotSerialized)	// get Battery InFormation
  {
   Name (MULV, Zero)
   Name (BATI, Package (0x0D)
   {
        Zero, 			// power_unit
        0x2710, 		// design_capacity
        0x2710, 		// last_full_capacity
        Zero, 			// battery_technology
        Ones, 			// design_voltage
        0x03E8, 		// design_capacity_warning
        0x0190, 		// design_capacity_low
        0x64, 			// battery_capacity_granularity_1
        0x64, 			// battery_capacity_granularity_2
        "", 			// model_number
        "", 			// serial_number
        "LiOn", 			// battery_type
        "Sony Corp."		// oem_info
   })
```
I changed the battery_technlogy 'Zero' to 'One', saved then recompiled the file with iasl and copied the output file 'DSDT.aml' to the '/etc/initramfs-tools/' directory and then rebuilt the boot images. This updates the boot-images so the custom DSDT is used in preference to the BIOS version. 

Edit the DSDT.dsl file, changing _BIF battery_technology to 'One', then recompile:
```
$ iasl DSDT.dsl
```
there is now an updated DSDT.aml created by iasl.
```
$ sudo cp DSDT.aml /etc/initramfs-tools/
$ sudo dpkg-reconfigure linux-image-$(uname -r)
```
After a reboot the dmesg log shows:

```
  [   19.207785] ACPI: Looking for DSDT in initramfs... successfully read 23334 bytes from /DSDT.aml.
  [   19.207941] ACPI (tbget-0297): Table [DSDT] replaced by host OS [20060707]
```
and acpi correctly reports a "rechargeable" battery:
```

$ cat /proc/acpi/battery/*/info
present:                 yes
design capacity:         57720 mWh
last full capacity:      57720 mWh
battery technology:      rechargeable
design voltage:          125340 mV
design capacity warning: 1000 mWh
design capacity low:     400 mWh
capacity granularity 1:  100 mWh
capacity granularity 2:  100 mWh
model number:            
serial number:           
battery type:            LiOn
OEM info:                Sony Corp.
```

---

### Post by IntuitiveNipple on 2007-06-18
I've reported this issue to Sony today and it is being escalated to the BIOS engineering team. I'll let you know if/when they do something about it.

---

### Post by IntuitiveNipple on 2007-06-19
Some interesting information. I was reading the Smart Battery Data specfication v1.1 and found this interesting quote:
> When the Smart Battery enters the &#8220;On State&#8221; the following values must be reinitialized...

...The Smart Battery defaults to disabling the internal charge controller (if it exists) in order to prevent possible overloading of the power supply in systems when more than one battery is present. Without this default, it is possible for multiple batteries to concurrently demand more charging power than is available potentially starving the system of power. The Smart Battery&#8217;s **defaults to act as a secondary battery** in order to prevent large amounts of energy that could potentially flow between two primary batteries not at the same charge level.

---

### Post by Migs on 2007-07-03
> **IntuitiveNipple said:**
> Some interesting information. I was reading the Smart Battery Data specfication v1.1 and found this interesting quote:

Yesterday I was playing with the latest stable kernel and noticed that there was an option for smart batery's(carefull it's experimental), any change you have noticed that too? I did not have time enough to try it out but later this week I will have some spare time to test it.

---

### Post by IntuitiveNipple on 2007-07-03
These batteries are managed via ACPI Control Method so its not something I have investigated.

---

### Post by Toufik on 2007-07-07
Damned, I wished I'd find this post before reading the ACPI doc :)

I discover the bug yesterday and decided to have a look at the dsdt and I also found the Zero instead of One in the _BIF method... 2 weeks too late ;)

---

### Post by Toufik on 2007-07-07
Well, it works but...

I wanted to fix this because of two problems I've got:
* when at 100% "charging state" keeps telling "charging" and never tells "charged"
* When charging and discharging, "present rate" keeps telling "unknown"

Theses two bugs are really annoying: you never know how much time you're left. I hoped they were related with the "non-rechargeable" bug, but it does'nt seem.

---

### Post by Max Luebbe on 2007-08-23
I have the same issue on my Sony FS760/W

Would love to know where I could get rate info or how I could get my battery to report itself as being charged, or how I could help in getting this solved.

---

### Post by c98928 on 2008-06-18
i have a similar problem
i have an old vaio laptop and lately i bought a OEM battery for it which is 7200mah,but in fact i can only charge 6900mah or so but the it keeps saying "in charge" after reaching 6900mah as well as the charing LED keeps flashing.

another weird thing is that when i check the battery detail,the design capacity is showing 10000mah which should be 7200mah instead

anybody has any idea on this?

---

### Post by henok on 2008-07-17
So has there been a better solution to this issue, or do we still need to do the hack that IntuitiveNipple described above? 

I am using: 

Sony Vaio VGN-S460 
Ubuntu 8.04.1 (hardy) 

```

$ cat /proc/acpi/battery/BAT1/info
present:                 yes
design capacity:         53280 mWh
last full capacity:      33430 mWh
battery technology:      non-rechargeable
design voltage:          11100 mV
design capacity warning: 0 mWh
design capacity low:     120 mWh
capacity granularity 1:  0 mWh
capacity granularity 2:  10 mWh
model number:            
serial number:           
battery type:            LION
OEM info:                Sony Corp.

$ cat /proc/acpi/battery/BAT1/state
present:                 yes
capacity state:          ok
charging state:          charging
present rate:            86 mW
remaining capacity:      33430 mWh
present voltage:         12316 mV

```

---

