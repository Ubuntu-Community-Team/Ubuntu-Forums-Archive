---
title: "gnome-power-manager(gpm) / hal suspends only once on gutsy"
date: 2007-11-05
forum: Hardware &amp; Laptops
---

### Post by Egalus on 2007-11-05
Hi,

I have an annoying problem with gutsy on my laptop.
After a hard boot (not after a resume) I can suspend2disk / suspend2ram (with uswsusp or tuxonice) nicely (via hibernate/sleep buttons and via gpm menu)
But if I resume after a s2disk or s2ram it seems like gnome-power-manager, hal or acpi ignores the buttons, or is left in a state where hal/gpm still thinks it's in a suspended system.

On a resumed system:
- pressing hardwarebuttons for suspend/sleep just lead to gpm locking the screen
- klicking on gpm and shoosing sleep/hibernate just leads to gpm locking the screen
- calling the hibernate/sleep script from a terminal-window works without problems
- killing hal and gpm and restarting both and I am back with working gpm hibernate/sleep, this would be a nice workaround if I would find a way to start gpm from a suspend skript, but it seems I am not able to get it up and running, so i have to restart it myself
- if i kill hal and gpm and restart it after I tried to hibernate/sleep unsuccesfully (cause the system was resumed before) and I now call hibernate/sleep scripts in an xterm the pc goes to sleep and on the next resume gets back to the deskop and directly resumes again. The next resume works as normal and the system is back in a "no more hibernat/suspend with gpm"-state again.

Does anyone know how to solve this hal/gpm problem?

---

### Post by Egalus on 2007-11-05
I did a little research trip through my system and at the end of 
/usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux 
I found some lines about Rescanning Hal-Features of some acpi things like button,battery,ac_adapter.

Running these 
```

#Refresh devices as a resume can do funny things
for type in button
do
        devices=`hal-find-by-capability --capability $type`
        for device in $devices
        do
                dbus-send --system --print-reply --dest=org.freedesktop.Hal \
                          $device org.freedesktop.Hal.Device.Rescan
        done
done

```
lines on a freshly booted gutsy (only using type button as ac_adapter and battery are of no interest) 
results in this output
```

method return sender=:1.62 -> dest=:1.84 reply_serial=2
   boolean false
method return sender=:1.62 -> dest=:1.85 reply_serial=2
   boolean false
method return sender=:1.62 -> dest=:1.86 reply_serial=2
   boolean true
method return sender=:1.62 -> dest=:1.87 reply_serial=2
   boolean false

```

On a freshly resumed system its
```

method return sender=:1.62 -> dest=:1.101 reply_serial=2
   boolean true
method return sender=:1.62 -> dest=:1.102 reply_serial=2
   boolean false
method return sender=:1.62 -> dest=:1.103 reply_serial=2
   boolean false
method return sender=:1.62 -> dest=:1.104 reply_serial=2
   boolean false

```
and resuming no longer works.

BTW, Devices are:
```

/org/freedesktop/Hal/devices/computer_logicaldev_input_1 /org/freedesktop/Hal/devices/computer_logicaldev_input_0 /org/freedesktop/Hal/devices/computer_logicaldev_input /org/freedesktop/Hal/devices/platform_i8042_i8042_KBD_port_logicaldev_input

```

If have absolutely no idea if this should tell me something or not and as documentation on hal and gpm is either almost non existant or hidden from me it's hard to debug this sucker ;)

---

