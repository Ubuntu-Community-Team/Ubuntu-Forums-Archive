---
title: "Sony Vaio Fn-Keys...again"
date: 2006-01-17
forum: Hardware &amp; Laptops
---

### Post by firehead on 2006-01-17
Hi all
I'm running Kubuntu Breezy on a Vaio S4xp and encounter some strange things with my Fn-keys...
If I'm running KDE (what i usually don't because i prefer fluxbox) and i hit a Fn+Key Combo let's say Fn+F2 (mute) i get an OSD telling my what i just hit (like "mute on" or "mute off") and it actually does what is says (i.e. the key works and actually mutes the system). the same thing happens with volume up/down (these also work) and brightness up/down (don't change anything, but that's for later). 
btw i got the OSD only after checking the box "Report unhandled events using On Screen Display" in Kcontrol->System Administration->Sony vaio Laptop... 

So far so good...

now if i switch to fluxbox(because i boot to console and start the wm from there i wrote this .xinitrc: [[ATTACH]5406[/ATTACH]], maybe i'm mising something in here) and hit the same Fn+key combos nothing happens... no OSD (could live with this) but also no action...

now after having read some threads in this forum about vaio fn-buttons or brightness changing etc. i was told that the s4-series doesn't implement acpi-events, but uses sonypi...now i have basically 2 questions:

1.)if i run "acpi_listen" and hit a Fn+key combo (let's say Fn+F2 - mute) i get the following:```
sony/hotkey SPIC 00000001 0000000d
sony/hotkey SPIC 00000001 0000003b
``` 
where the first line represents the "mute-button" and the second the Fn-key
looking at /etc/acpi/events/sony-mute shows
```
# /etc/acpi/events/sony-mute

event=sony/hotkey SPIC 00000001 0000000d
action=/etc/acpi/mutebtn.sh

```
and a quick glance at /etc/acpi/mutebtn.sh shows:
```
#!/bin/bash

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs

getXconsole
if [ x"$XAUTHORITY" != x"" ]; then
    acpi_fakekey 160
fi

```
couldn't i just change the mutebtn.sh script, so that it actually mutes the system (if yes, how??),because even ./mutebtn.sh doesn't do something...(i guess that's what's meant by "acpi-events are not implemented")

2.)If the first method doesn't work, what is there to do? is anybody familiar with sonypi(d)? there is a howtoo for gentoo [here]("http://gentoo-wiki.com/HARDWARE_Sony_VGN-S4"), but to be honest it's a little too complicated for me, and i don't like messing around with my kernel...so if anybody could translate it into kubuntu i would be very grateful

if you need any further information about my system i'll be pleased to provide you with it...

thx for any helpfull reply

---

### Post by ninja_indiano on 2006-01-17
I also want to add in your request if anybody could give me some hints on how to install sonypid in de Kunbuntu

thxs 4 any help

---

