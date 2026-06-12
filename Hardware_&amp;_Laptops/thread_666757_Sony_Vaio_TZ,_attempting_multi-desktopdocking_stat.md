---
title: "Sony Vaio TZ, attempting multi-desktop/docking station killed my resolution!"
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by Kache on 2008-01-13
Exactly like the title says.

Ubuntu on my laptop doesn't like being plugged in/unplugged from the dock, so I'll avoid that until I hear more about it, but I can't undo the damage it did to my screen resolution!

Ubuntu no longer has 1366x768 as an option in Screens and Graphics, perhaps after attempting to use my monitor, the screen drivers and stuff were forgotten?

---

### Post by Kache on 2008-01-13
Okay, nevermind. I managed to get this fixed by diff comparing xorg.conf from a backup and a liveCD.

man phew. I was totally freaked out.

Does anyone know of a way to safely dual monitor and dock/undock?

when I dock, (i think) nothing happens.

If I boot up with the dock on, ubuntu detects stuff and tries to make it work, however unsuccessfully (maybe I can get it to dual monitor correctly manually somehow), and if i undock, the system freezes, my caps on and scroll lock flash, and I have to take out the battery.

---

### Post by vishketan on 2008-02-17
Hi!

I have a sony vaio vgn sz483n and I have exactly the same problem. If I undock when X is running in speed mode with the proprietary drivers the machine freezes. The only way to unfreeze it is to disconnect the battery. 

BTW did you get suspend/hibernate to work? 

vishy

---

### Post by JohnHughes on 2008-02-21
Yup, I have a Vaio TZ (a TZ31WN/B to be precise) and I have exactly this problem:

Boot on docking station - ok
remove from docking station - dead as a dodo, caps & scroll lock flashing, have to take the battery out.

Boot without docking station - when plug into dock only the USB and power is recognised, the ethernet on the docking station doesn't work.

Neither suspend nor hibernate works - they seem to crash the machine.

Help!

---

### Post by JohnHughes on 2008-02-21
Ok, the crash on undock problem is simply that the kernel is unhappy about one of the ethernet ports disappearing!

When the TZ is plugged into the docking station it has two NIC's:

 02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
+08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 14)

Unpluging it causes one of the NIC's to disappear.  If it's using it at the time that makes the kernel panic.

Looks like some kind of hotplugging is needed.

---

### Post by JohnHughes on 2008-02-21
Well, lets see how far we can get with hotplug.

```
# modprobe acpiphp
# ls /sys/bus/pci/slots
4
```

Yow, we've found a hot-pluggable pci slot

```
# cat /sys/bus/pci/slots/4/address
0000:08:00
# lspci -s 0000:08:00
08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 14)
```

And it contains our disappearing card.

Let's try powering it off:

```
# echo 0 > /sys/bus/pci/slots/4/power
# cat /sys/bus/pci/slots/4/power
1
```

Didn't seem to do anything.

Press the "undock" button on the docking station - in use light goes out,

```
# cat /sys/bus/pci/slots/4/power
0
# dmesg
[...]
[  613.488000] sky2 eth1: disabling interface
[  613.800000] ACPI: PCI interrupt for device 0000:08:00.0 disabled
[  613.800000] ACPI: undocking
```

Yow!  The card has vanished but the system hasn't crashed!  We can now remove the machine from the docking station and everyone is happy.

Now how the hell do we get it back again?

---

### Post by JohnHughes on 2008-02-21
So, in our last episode we managed to undock without a crash.

Now we just slip the machine back into the docking station, wait a tick and:
```

# echo 1 >/sys/bus/pci/slots/4/power
# cat /sys/bus/pci/slots/4/power
1
# dmesg
[...]
[  440.672000] decode_hpp: Could not get hotplug parameters. Use defaults
[  440.672000] PCI: Enabling device 0000:08:00.0 (0000 -> 0003)
[  440.672000] ACPI: PCI Interrupt 0000:08:00.0[A] -> GSI 19 (level, low) -> IRQ 19
[  440.672000] PCI: Setting latency timer of device 0000:08:00.0 to 64
[  440.672000] sky2 0000:08:00.0: v1.18 addr 0xfa000000 irq 19 Yukon-EC Ultra (0xb4) rev 3
[  440.672000] sky2 eth1: addr 00:13:a9:e6:f4:51
[  440.760000] sky2 eth1: enabling interface
[  440.768000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  442.580000] sky2 eth1: Link is up at 100 Mbps, full duplex, flow control rx
[  442.588000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  460.508000] eth1: no IPv6 routers present

```
It's back!

One oditty - the "in use" light is still unlit.

Let's try undocking again...

Hum, the undock button does nothing.

But now we can power off from the linux side.  How odd.

---

### Post by JohnHughes on 2008-02-22
So here's a couple of scripts to allow safe undocking and redocking of a Vaio TZ.

How to undock:
```

#! /bin/sh

# script to undock Vaio TZ laptop

modprobe acpiphp

# Poweroff all slots

for s in /sys/bus/pci/slots/*; do
        echo 0 > $s/power
done

# Wait till devices turn off

OFF=0

while [ $OFF -eq 0 ]; do
        OFF=1
        sleep 1
        for s in /sys/bus/pci/slots/*; do
                if [ "`cat $s/power`" != "0" ]; then OFF=0; fi
        done
        if [ $OFF -eq 0 ]; then
                echo "Press undock button"
                sleep 1
                for s in /sys/bus/pci/slots/*; do
                        echo 0 > $s/power
                done
        fi
done

echo "Safe to undock"
```

And how to redock & get access to the docking stations ethernet port.

```
#! /bin/sh

# script to redock Vaio TZ laptop

modprobe acpiphp

# Wait till devices turn on

ON=0

while [ $ON -eq 0 ]; do
        ON=1
        for s in /sys/bus/pci/slots/*; do
                if [ "`cat $s/power`" != "1" ]; then ON=0; fi
        done
        if [ $ON -eq 0 ]; then
                for s in /sys/bus/pci/slots/*; do
                        echo 1 > $s/power
                done
                sleep 1
        fi
done

echo "Docking finished"
```

---

### Post by vishketan on 2008-02-22
Hi!

Do you know if an ACPI event is raised when the undock button is pressed or if the machine itself is undocked?

Then your scipts could be associated with those events.

vishy

---

### Post by JohnHughes on 2008-02-25
Well, in order to fix the hibernate/suspend problems I've updated to kernel 2.6.24.2

Since I did that when I press the undock button the "in-use" light goes out.

And I see "ACPI: \_SB_.DOCK - undocking" in the dmesg output

But acpid seems not to get any event.

---

### Post by JohnHughes on 2008-02-25
Well, having the acpiphp (ACPI PCI HotPlog) module loaded makes the undock button [I]just work[/I with kernel 2.6.24.2.

Don't yet know how to correctly re-dock.  My script re-enables the ethernet port. but doesn't turn the in-use light back on, or re-enable the undock button.

---

### Post by vishketan on 2008-02-25
Hi!

I migrated to 8.04 alpha 5 and now suspend and hibernate almost work. 

See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/188455](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/188455) for details.

I am still searching for the elusive acpi event that dock/undock generates. If you make any progress please let me know.

BTW I have a question about nvidia drivers. Does anybody know how I can force the display to switch to my external monitor when I dock the laptop and switch it back to the LCD display after I undock it? It works automatically on windows.

vishy

---

### Post by vishketan on 2008-02-26
BTW this bug is tracked here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/194617](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/194617)

If you also provide details of your system it might help the kernel developers isolate the problem and possibly fix it :)

vishy

---

### Post by JohnHughes on 2008-02-26
Will add details to bug

---

### Post by JohnHughes on 2008-02-26
Ok, an overly complicated way of doing re-dock:

1. Put the machine in suspend-to-ram

2. Stick it on the docking station

3. wake it up

  - the "in use" light comes back, but the ethernet port is not visible,

4. Use my "redock" script to get the ethernet port back.

The "undock" button is now non-functional.

The system can be undocked with "echo 1 > /sys/devices/platform/dock.0/undock"

So near and yet so far.

---

### Post by vishketan on 2008-02-26
Please add your information to the bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/194617](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/194617) so that it can be tracked.

Is your suspend/hibernate working fine? 

Mine works well with the new Hardy alpha 5 release but with one minor glitch. If I logout after doing a suspend or hibernate then the screen becomes completely garbled. Can you please confirm if the same happens to you too?

I did not make any changes to acpi-support etc. I only had to add uvcvideo to the list of modules to be unloaded and added Option NvAGP "1" to my xorg.conf.

vishy

---

### Post by JohnHughes on 2008-02-28
Suspend/hibernate work ok with kernel 2.6.24.2

I see no screen problem.

In summary, on a VGN TZ31 with kernel 2.6.24.2 everything works except re docking (and the memory card slots).

Unfortunately I no longer have the machine, so I probably won't be able to contribute anything more to this thread.

---

