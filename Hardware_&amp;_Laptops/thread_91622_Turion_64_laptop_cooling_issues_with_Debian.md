---
title: "Turion 64 laptop cooling issues with Debian"
date: 2005-11-17
forum: Hardware &amp; Laptops
---

### Post by WebDrake on 2005-11-17
I came across this message on one of the Debian usenet groups, regarding problems one user was having with Debian and a Turion 64 laptop... Seems kind of relevant, since Ubuntu is Debian-based. Anyone have this experience with Ubuntu?

If someone knows how to fix it, perhaps someone could go across and help out the poor guy; the original post was on linux.debian.ports.x86-64.  Or I'll cut-and-paste replies from here, if that's OK.


> I've been working steadily over the past few weeks to get my new HP nx6125
working under Debian (amd64 port) and have made significant progress.
However, there is one considerable problem: thermal events don't seem to be
recognised or processed by the kernel (until I do a
cat /proc/acpi/thermal_zone/TZ?/temperature). As soon as I do anything CPU
intensive I really run the risk of frying my laptop

To be more specific, I am running kernel 2.6.13.4
([www.kernel.org](www.kernel.org) vanilla) with the double timer patch applied (see
[http://bugzilla.kernel.org/attachmen...1&action=view)](http://bugzilla.kernel.org/attachmen...1&action=view)). When I boot
up, my thermal trip points get set nicely. The first is at 58 *C, then 65*C,
then 75 *C, and 80*C (S5 = 95 *C). When I was testing things I was doing
frequent executions of

cat /proc/acpi/thermal_zone/TZ?/temperature

and I would observe the temp rise to 58 C, then the fan would kick in, the
first trip point would then (automatically) re-set to 50 C and the CPU would
cool through 8 C before the fan turned off (nice, I thought, and very clever
this re-setting of trip points--sorry I'm very new to ACPI). When the fan
turned off, the trip point would again re-set to 58 C. So, I thought all was
working well. However, subsequent tests done by running glxgears and not
executing the above cat command allowed the CPU temp to rise above several
trip points without the fans kicking in! Only when I ran the above cat
command did the fans start!?

So, I stopped acpid and did a

cat /proc/acpi/event

while running glxgears. I waited a while and then did a
cat /proc/acpi/thermal_zone/TZ?/temperature to see that indeed the temp of
TZ1 had exceeded 58C---and immediately /proc/acpi/event received a thermal
event (note: the temp had already exceeded 58 C, my first thermal trip point;
the thermal event only occurred when I did the 'cat'). So, in order for
thermal events to "get through/processed" I need to keep doing
cat /proc/acpi/thermal_zone/TZ?/temperature!!!!

Can anybody shed some light on this behaviour. I don't know much about ACPI,
but it seems (?) like the linux kernel is not processing the thermal events
properly. Incidentally, I am also seeing spurious syslog errors that read
APIC error on CPU0: 40(40) meaning that some interrupts presumably are not
being correctly identified by the interrupt controller (thermal ones? could
there be some correlation here?).

Other info: the HP nx6125 is a Turion 64 based laptop with ATI chipset (yes,
I know). I am running acpid and have just installed powernowd (doesn't fix
it). I have also observed the above behaviour running the standard Debian
2.6.12-1-amd64 kernel (booting with no_timer_check to avoid double timer
interrupts). Any help, suggestions would be greatly appreciated. If anyone
has any ideas why catting /proc/acpi/thermal_zone/TZ?/temperature gets
things to work, I'd be very happy to hear an explanation, too.

---

### Post by Patsoe on 2005-11-23
Hi there,

I've just started running Ubuntu on such a laptop. I'm running 2.6.12-10-amd64-generic (at least, that's the output of /proc/version), with versions 0.09-1 of acpi, 1.0.4-1ubuntu8 of acpid and 0.46ubuntu1 of acpi-support (packages). All settings are standard (just up since yesterday).

My machine is a HP Compaq nx6125, model PY416EA: Turion 64, ATi chipset and graphics, 1400x1050 tft panel. *Edit: the chipset is the ATi Radeon Express 200M.*

I had no installation issues other than having to run vesa drivers before X could start. *Edit: this is not exactly correct - installation froze while copying files the first time - I then redid the installation using "noapic nolapic" options on boot in addition to the "vga=771" option - just for completeness...* 
I have not yet bothered to install Wifi, Bluetooth, card readers and anything else, so other than now having fglrx drivers, everything is in "out-of-the-box" state.

Getting to the point: my cpu fan does come on when the cpu is running warm (cpu freq scaling is enabled and works fine according to the gnome panel utility, so that is not happening very often). Sometimes it takes a long time however for the fan to switch off again - if I then read out the temperature through /proc/.../temperature, it gets below 30 degrees Celsius... and I think that the fan indeed switches off as I probe the temp.

So something is going funny there it seems. I'm not sure however, and will post new observations as I find them. 

By the way, I've read some other posts where people have changed the polling_frequency variables. According to [this site]("http://http://acpi.sourceforge.net/documentation/thermal.html"), you should leave it at <polling disabled> however, if that's what it is set to.

I have to go now, bye!

---

### Post by Patsoe on 2005-12-09
I can now confirm that when I run glxgears, the same thing happens here: fan only comes on after doing a 'acpi -V' command, which probes the thermal zones.

In normal use, however, then fan does come on at some point by itself without my intervention. Perhaps the priority of the process that is supposed to control the fan is set too low?

---

### Post by grillip on 2005-12-13
hi,

i have quite same problem on my hp nx6125 turion ml-32

at first sorry for my "poor" english, but i hope that youu will get the point...

I have the nx6125 for few weeks and i cant solve the foloving problem.

i found that the default trip points in bios ar ser to:
critical (S5): 95 C
passive: 88 C:
active[0]: 80 C:
active[1]: 75 C:
active[2]: 65 C:
active[3]: 58 C:

at first everything seems to be ok. when the temperature reached 58C the fan turns on and the trip points was changed to


critical (S5): 95 C
passive: 88 C:
tp4 active[0]: 80 C:
tp3 active[1]: 75 C:
tp2 active[2]: 65 C:
tp1 active[3]: 50 C:

then the temperature goes slowly down and when it reached 50 the fan turns off and the trip points was changed back to defaults

but when i use 100% cpu for long time the temperature reached the firs trip point again (58) fan turn on, then temperature reached second trip point (65) > fan speeds up (still everithing ok smile.gif ) > tempearture reached third trip point (75) > fan speeds up again (still everithing ok smile.gif ).....then i stop using cpu and the temperature slowli goes down to 60C, in this moment the second trip point was reached and fan should slow down, but it does not, it tunns off completly sad.gif. then (in idle state) temperature slowly goes down to 50C (fan still off). the problem is that when i started to use 100% cpu again and when temperature reached 1 and 2 trip points the fa does not turn on sad.gif it turns on only when the third trip point was reached. then i experimented a bit and i found out that the torns on only at higest trip point, ever been reached (third in this case)

so if the second trip point was not reached everything is ok, ehrn second tp is reached fans does not turn on first tp, when third tp is reached fans does not turn on first and second tp ect...

i tried to solve this by overiding the trip points by pover scheme conf, but i was not able to overide the 1 and 2 tp.

then i try to disable fan acpi module to let the bios controll the fan - does not work...also does not work to start fan manually by
echo "on" > /proc/acpi/fan/C26*/state

cat /proc/acpi/fan/*
cat: /proc/acpi/fan/C260:
cat: /proc/acpi/fan/C261:
cat: /proc/acpi/fan/C262:
cat: /proc/acpi/fan/C263:

cat /proc/acpi/fan/*/state
status: off
status: off
status: off
status: off

peter grilli

---

### Post by jml on 2005-12-13
There is one major difference between Debian and Ubuntu.  Debian does not really have a prebuilt laptop configuration.  You pretty much have to configure all of the apps to optimize laptop functioning yourself.  Ubuntu, on the other hand is very laptop friendly, so many of the problems laptop users encounter with pure Debian, may not be an issue for Ubuntu users.

Joe

---

### Post by Patsoe on 2005-12-14
I found that this issue was registered as a bug, and is not yet resolved. To stay informed (and perhaps to draw attention to the problem), please add yourself to CC of

[http://bugzilla.kernel.org/show_bug.cgi?id=5534](http://bugzilla.kernel.org/show_bug.cgi?id=5534)
[http://bugzilla.ubuntu.com/show_bug.cgi?id=18164](http://bugzilla.ubuntu.com/show_bug.cgi?id=18164)

---

