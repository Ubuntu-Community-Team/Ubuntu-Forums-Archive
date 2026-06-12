---
title: "Workaround to deactivate ATI-Card for HP Touchsmart tm2 with  10.10"
date: 2010-10-10
forum: Hardware
---

### Post by BernieB on 2010-10-10
Hello Everybodey

I just installed 10.10rc1 on my HP TM2 2060ez.
Unfortunately the workaround to deactivate the ATI-Cart as found here:

[http://ubuntuforums.org/showpost.php?p=7933876&postcount=11](http://ubuntuforums.org/showpost.php?p=7933876&postcount=11)

doesn't seem to work at all.

After i add the Kernel-Module i still get this Output from "lspci -v":


01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series] (prog-if 00 [VGA controller])
Subsystem: Hewlett-Packard Company Device 1486
Flags: bus master, fast devsel, latency 0, IRQ 46
Memory at a0000000 (64-bit, prefetchable) [size=256M]
Memory at c4400000 (64-bit, non-prefetchable) [size=128K]
I/O ports at 3000 [size=256]
Expansion ROM at c4440000 [disabled] [size=128K]
Capabilities: <access denied>
[COLOR="Red"]Kernel driver in use: radeon[/COLOR]
Kernel modules: radeon

Still the Notebook gets very hot compared to Windows 7 and proper Driver.

Is there another way to deactivate the ATI-Card?

Thanks.

PS: I asked the HP-Support if there will be a Bios-Update which will allow you to deactivate the ATI-Card. But no answer yet...

---

### Post by M42 on 2010-10-15
I have a tm2 also.  The radeon driver may be active but may be set to a state of powered off after inserting the lenovo module.  Check to see if you have something similar to this in your dmesg file.

[    8.832610] radeon 0000:01:00.0: power state changed by ACPI to D0
[    8.848058] radeon 0000:01:00.0: Refused to change power state, currently in D3
[    8.848091] radeon 0000:01:00.0: power state changed by ACPI to D0

The last state is D0.  I believe the D0 state is very low power or off.  One way to check is to see how long you battery lasts.  If it last more than 6 hours I'm fairly sure the radeon video is either very low or off.

---

### Post by mirroalex on 2010-10-20
Any news regarding to deactivating ati? i'm also interested ...

---

### Post by Boni2k on 2010-11-24
Hello,

as I couldn't find a way to disable the ATI card either I tried this:

1. Follow [http://ubuntuforums.org/showpost.php?p=7933876&postcount=11](http://ubuntuforums.org/showpost.php?p=7933876&postcount=11)
2. If after restart "dmesg | grep lenovo" reports an error like "handle not found" continue
3. find out which handle is the correct one: "dmesg | grep switche" It will tell you something like "detected switching method \_SB..."
4. Replace the last part \_SB... into your lenovo_acpi.c. I have " status = acpi_get_handle(root_handle, "\\_SB_.PCI0.GFX0.ATPX", &handle);" now.
5. compile and so on

At least "dmesg | grep lenovo" tells me "in discrete graphics mode" now. However I'm not sure if this damn thing really is turned off...

Good luck and tell me if it worked for you.

---

### Post by roberto.pierpaoli on 2010-12-01
Hi guys,
has any of you tried to use the switcheroo module that is built in inside kernel 2.6.35?

I switch off my ATI discrete card just executing:

#> echo DIGD > /sys/kernel/debug/vgaswitcheroo/switch
#> echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

I am sure it works since I can read a value of 10W less consumption through “powertop” command-line tool.

Just one drawback: if I shutdown the laptop before re-activating the card a ton of log messages slows down the shutdown process. So anytime before shutting down I execute:

#> echo ON > /sys/kernel/debug/vgaswitcheroo/switch

I have tried to include this commands inside start-up and shut-down scripts, but it does not work properly, so I do it manually after a complete boot and before the shutdown.

My battery life has been doubled this way and the fan is quite always off.

You can find more about this method googling for “ubuntu swticheroo” or directly for “echo OFF > /sys/kernel/debug/vgaswitcheroo/switch”.

Hope it helps, have fun!

---

