---
title: "AC power plug/unplug events"
date: 2014-03-26
forum: Hardware
---

### Post by Jackson_Wiegman on 2014-03-26
[COLOR=#333333][FONT=UbuntuRegular]Running Ubuntu Server 13.04 (kernel 3.8.0-19-generic). I want to react when AC power is applied or removed. I can query the state correctly either through `acpi -b`or `cat /sys/class/power_supply/online`.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]
I would like to react automatically but it appears that ac power events through acpid are not working (I don't see anything coming through on acpi-listen or connecting to acpid.socket, even if I reset acpid and enable logging or debug.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][It looks like ACPI support is partially broken/in transition]("https://wiki.ubuntu.com/AcpiSupportDeprecation") in Ubuntu, but I haven't been able to find what component is intercepting these events. 

Also, c[COLOR=#444444]harging/discharging shows correctly the first time I run [/COLOR]upower[COLOR=#444444], I have to kill the [/COLOR]upowerd[COLOR=#444444] to get it to update. If I query `[/COLOR]/sys/class/power_supply/online` [COLOR=#444444]that is right everytime. looks like it is related to uevents not updating properly[/COLOR][/FONT][/COLOR]

---

### Post by tgalati4 on 2014-03-27
The server installation may be missing some packages used by laptop mode to detect power and change the panel icon to a lightning bolt and compute time-to-fully-charged.

tgalati4@Mint14-Extensa ~ $ laptop-detect -v
We're a laptop (ACPI batteries found)

What exactly are you trying to do?  If you want to monitor power loss on the AC line, then a SMARTUPS and apcupsd will do that.  DBUS may also have a method to detect power changes.

---

