---
title: "Capabilities: &lt;access denied&gt;"
date: 2013-11-16
forum: Hardware
---

### Post by starving030 on 2013-11-16
Can someone please explain this to me. Does this have anything to do with why I'm getting my low graphics mode error. I don't know much about Linux other than installing it and goofing around with Compiz. Also, my "Hardware Drivers" list is empty.
> 02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550]
	Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device 2342
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fddf0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at bc00 [size=256]
	[virtual] Expansion ROM at fdd00000 [disabled] [size=128K]
	[COLOR="#FF8C00"]Capabilities: <access denied>[/COLOR]
	Kernel driver in use: radeon
	Kernel modules: radeon

02:00.1 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550 Series] (Secondary)
	Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device 2343
	Flags: bus master, fast devsel, latency 0
	Memory at fdde0000 (64-bit, non-prefetchable) [size=64K]
	[COLOR="#FF8C00"]Capabilities: <access denied>[/COLOR]
Not sure if this helps but the specs I got from the distro site say:
> Ubuntu 10.04 with,
GNOME 2.30.0 tweaked to resemble Microsoft Windows XP(Ylmf),
Linux kernel 2.6.32-22.33,
X.Org Server 1.7.6,
GCC 4.4.3.
Thanks

---

### Post by steeldriver on 2013-11-16
I'm assuming this is the output of an lspci -v command? it would have been useful to include that info

If that's the case, it probably just means you ran lspci without the necessary privileges - try again with 'sudo'

```
sudo lspci -vnn
```

You can also use lshw

```
sudo lshw -C display
```

I don't know why you're getting low graphics mode, but the 10.04 branch isn't really supported any more

---

### Post by starving030 on 2013-11-16
Your right. I needed to run with sudo. That <access denied>part is gone now. I just don't know what to do about the low graphics mode. It has something to do with modesetting. I posted about it but no replies thus far.
[http://ubuntuforums.org/showthread.php?t=2188165&p=12848986#post12848986]("http://ubuntuforums.org/showthread.php?t=2188165&p=12848986#post12848986")

Here running lspci with privileges.
> 02:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550] [1002:7146]
	Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:2342]
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fddf0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at bc00 [size=256]
	[virtual] Expansion ROM at fdd00000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Express Endpoint, MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Kernel driver in use: radeon
	Kernel modules: radeon

02:00.1 Display controller [0380]: Advanced Micro Devices, Inc. [AMD/ATI] RV515 [Radeon X1300/X1550 Series] (Secondary) [1002:7166]
	Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:2343]
	Flags: bus master, fast devsel, latency 0
	Memory at fdde0000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Express Endpoint, MSI 00

---

### Post by steeldriver on 2013-11-16
"something to do with modesetting" as in you're using a nomodeset grub option?

---

### Post by starving030 on 2013-11-16
Now that I can't say yes or no. I just installed from CD. But I assume I am since in the /etc/default/grub file I added "nomodeset" and it stopped the error. But that made me not able to use "Visual Effects" or adjust the Hz on my monitor.

I'm getting the low graphics error along with this.
> (EE) VESA: Kernel modesetting driver in use, refusing to load
(EE) No devices detected 

---

### Post by starving030 on 2013-11-16
This seemed to work.

> possible you still have an xorg.conf trying to load drivers.

look in /etc/X11

if you've got a xorg.conf file - rename it and reboot

ref:[http://ubuntuforums.org/showthread.php?t=1497063&p=9382520#post9382520]("http://ubuntuforums.org/showthread.php?t=1497063&p=9382520#post9382520")

---

