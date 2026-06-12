---
title: "Missing Fan"
date: 2009-11-03
forum: Hardware
---

### Post by Brown Betty on 2009-11-03
I cannot get my laptop's fan to start.

I have an HP Pavilion N5310 running Xubuntu 9.4 2.6.28-16-generic.

The BIOS is updated to the latest version.

acpi=force provides an entry at /proc/acpi/fan/FAN/state which is always off.

[COLOR="Red"]Edit:[/COLOR] Writing "echo 0 > /cat/proc/acpi/fan/FAN/state" changes the fan state to "ON" but the fan is manifestly not on.  (In addition to producing no noise, it can be viewed through the grill and is not spinning.)

Originally /proc/thermal_zones/*/trip_points produced

critical (S5):           100 C
passive:                 98 C: tc1=2 tc2=5 tsp=300 devices=CPU0 
active[0]:               100 C: devices= FAN

Which was obviously nonsense, so I edited my dsdt with more sane values, (If you do this, anyone else, the temperatures are in *tenths of degrees kelvin*, just in case, I don't know, you want your fan to come on when the cpu reaches -200 Celsius.) which are now showing up in /proc/etc. but do not result in the fan coming on, even when trip_points are reached.  (Passive cooling is not working either, so far as I can tell, but really, it's the fan that worries me.)

Booting with the Knoppix install CD does not provide a working fan.

I've reached the end of my googling.  Is it possible that the kernel has misidentified which device is actually the fan?  Is there anyone with any suggestion at all, really?

Supposedly the fan worked when it was running Windows.

---

### Post by raygj on 2009-11-08
instead of "acpi=force" try
acpi_enforce_resources=lax

---

