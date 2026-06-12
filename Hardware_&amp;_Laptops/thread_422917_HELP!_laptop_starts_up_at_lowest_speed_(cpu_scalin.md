---
title: "HELP! laptop starts up at lowest speed (cpu scaling)"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by BungaMan on 2007-04-25
I have a fujitsu-siemens Amilo M1424 1.7GHz

when powering on the computer I see that it is at 600MHz and it stays that way until X is loaded with gnome-power-manager in action.  Then it starts to scale properly.

This is to show that the kernel (or acpi if you like) detects cpu throttling correctly at startup:

Apr 25 18:02:12 lapper kernel: [    0.000000] Detected 600.069 MHz processor.
...
Apr 25 18:02:12 lapper kernel: [   38.800103] ACPI: Processor [CPU1] (supports 8 throttling states)

Before my upgrade, Edgy did not have this problem and took about 34 seconds to boot compared to 2:30 minutes.  

1. is there a way to force the bios to boot up at maximum speed?
2. is there a way to get the cpu scaled to max much sooner in the process? like with a startup script that is executed before all others? (and how do I do that?)

To be honest I think something is wrong with my laptop.  Booting up with kernel param acpi=off doesn't help and makes X very slow in response (screen updates, mouse movement, keyb).  Although my battery is in, it doesn't charge anymore (0%!).  If I work without the battery, my laptop does something like a soft power off, maybe suspend to ram or something but there's no way to wake it up again.  This happens for example when repartitioning with gparted (risky business!).

---

### Post by BungaMan on 2007-04-26
*push*

---

### Post by BungaMan on 2007-05-02
not a single answer?  I'd even appreciate a hint!

---

### Post by jjordan on 2007-05-03
Wow, It does sound like a BIOS update is in order.  I use a Fujitsu P1510 and have almost no issues.  

Anyway, lets take a stab at the original issue:

under the directory /etc/init.d/acpi/start.d are the scripts that are run when you start the computer the number at the left of the name indicates what order they will run.  In theory you could add a script to set the processor speed here.

Unfortunately, I don't know what you are using for frequency scaling so I can't tell you what to put in the file.

A simpler fix may be to set your CPU policy to  dynamic or performance before you shut down in what ever power management front end you are using.  (I am using "Power Manager" the default under KDE.)

-j

---

### Post by BungaMan on 2007-05-03
jjordan, thanks for your help.  Actually it isn't such a bad idea to try and flash the bios.  I already have the latest version but who knows it might help when overwriting it.  I'll try that first.

I already tried setting the policy to performance and shutting down like that, but the next boot it started at 600 again.

---

### Post by BungaMan on 2007-05-22
well... finally gave it a try and no luck in fixing this issue.  laptop still starts up at a boring 600Mhz...

---

### Post by BungaMan on 2007-05-23
WOW fixed !! I have a usb drive as well.  By all the bad luck in the world, its power connector and my laptop's fit on eachother (!!!) but the adapter for the usb drive gives a lower output.  When plugged into my portable, it can still run but slow as hell and as soon as more power is requested it does a hard shutdown.  How did I found out?  I turned on my usb drive and it didn't respond anymore... it got too much power (ac adapter from laptop) so it is probably fried :(

---

### Post by stchman on 2007-05-23
> **BungaMan said:**
> I have a fujitsu-siemens Amilo M1424 1.7GHz

when powering on the computer I see that it is at 600MHz and it stays that way until X is loaded with gnome-power-manager in action.  Then it starts to scale properly.

This is to show that the kernel (or acpi if you like) detects cpu throttling correctly at startup:

Apr 25 18:02:12 lapper kernel: [    0.000000] Detected 600.069 MHz processor.
...
Apr 25 18:02:12 lapper kernel: [   38.800103] ACPI: Processor [CPU1] (supports 8 throttling states)

Before my upgrade, Edgy did not have this problem and took about 34 seconds to boot compared to 2:30 minutes.  

1. is there a way to force the bios to boot up at maximum speed?
2. is there a way to get the cpu scaled to max much sooner in the process? like with a startup script that is executed before all others? (and how do I do that?)

To be honest I think something is wrong with my laptop.  Booting up with kernel param acpi=off doesn't help and makes X very slow in response (screen updates, mouse movement, keyb).  Although my battery is in, it doesn't charge anymore (0%!).  If I work without the battery, my laptop does something like a soft power off, maybe suspend to ram or something but there's no way to wake it up again.  This happens for example when repartitioning with gparted (risky business!).

Apparently your CPU is doing exactly what it is supposed to.  It will only clock up to the full Ghz when needed.  My Athlon 64 does the exact same thing.  The long bootup time I cannot explain.

---

