---
title: "Ubuntu doesn´t control fan speed"
date: 2024-01-14
forum: Hardware
---

### Post by joaomarceloq on 2024-01-14
English isn´t my native language, sorry in advance.

I have a Gigabyte Aero 16 XE4 laptop that is reaching temperatures like 90° Celsius (194 Fahrenheit) without any increase in fan speed. So I tryed to install lm-sensors and fancontrol to mitigate this, but after run sensors-detect I can´t find any information about fan speed at all.

```

$ sudo sensors-detect
# sensors-detect version 3.6.0
# System: GIGABYTE AERO 16 XE4 [P86VE] (laptop)
# Kernel: 6.5.0-14-generic x86_64
# Processor: 12th Gen Intel(R) Core(TM) i7-12700H (6/154/3)

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
AMD Family 16h thermal sensors...                           No
AMD Family 17h thermal sensors...                           No
AMD Family 15h power sensors...                             No
AMD Family 16h power sensors...                             No
Hygon Family 18h thermal sensors...                         No
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
Intel 5500/5520/X58 thermal sensor...                       No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
/dev/port: Operation not permitted

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): 
/dev/port: Operation not permitted

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): 
Found unknown SMBus adapter 8086:51a3 at 0000:00:1f.4.
Sorry, no supported PCI bus adapters found.

Next adapter: SMBus I801 adapter at efa0 (i2c-0)
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x50
Handled by driver `ee1004' (already loaded), chip type `ee1004'
    (note: this is probably NOT a sensor chip!)
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: Synopsys DesignWare I2C adapter (i2c-1)
Do you want to scan it? (YES/no/selectively): 
Adapter doesn't support all probing functions.
Some addresses won't be probed.

Next adapter: i915 gmbus dpa (i2c-2)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: i915 gmbus dpb (i2c-3)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: i915 gmbus dpc (i2c-4)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: i915 gmbus tc1 (i2c-5)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: i915 gmbus tc2 (i2c-6)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: i915 gmbus tc3 (i2c-7)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: i915 gmbus tc4 (i2c-8)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: i915 gmbus tc5 (i2c-9)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: i915 gmbus tc6 (i2c-10)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: NVIDIA i2c adapter 1 at 1:00.0 (i2c-11)
Do you want to scan it? (yes/NO/selectively): YES

Next adapter: NVIDIA i2c adapter 7 at 1:00.0 (i2c-12)
Do you want to scan it? (yes/NO/selectively): YES

Next adapter: AUX A/DDI A/PHY A (i2c-13)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: AUX USBC1/DDI TC1/PHY TC1 (i2c-14)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: AUX USBC2/DDI TC2/PHY TC2 (i2c-15)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: AUX USBC3/DDI TC3/PHY TC3 (i2c-16)
Do you want to scan it? (yes/NO/selectively): 

Next adapter: AUX USBC4/DDI TC4/PHY TC4 (i2c-17)
Do you want to scan it? (yes/NO/selectively): 


Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)yes
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run '/etc/init.d/kmod start'
to load them.

Unloading cpuid... OK

```

I suspected that "/dev/port: Operation not permitted" has something to do with that. But I do not have secure boot enable at my BIOS.

Since I cannot find fan's rotation speed, I think I can't install fancontrol.

After searching for two days with no success, I decided to ask for help.
Does anyone have a clue?

Thanks!

---

### Post by TheFu on 2024-01-15
Check the BIOS of the motherboard.  That's where fan control without drive support (blame the motherboard people for not making Linux drivers) is for hardware-only solutions.

BTW, Gigabyte has a long history of being hostile towards Linux.  These days, I think they just say "we don't support Linux", but in the past, they were much less nice.
Assume that any Linux drivers that happen to work on Gigabyte were created by the community or the upstream people.

I've had a few Gigabyte motherboards over the decades and generally didn't need support at all related to Linux from them. That's the best case.

---

