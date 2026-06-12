---
title: "shutdown command with wake-on-lan results in reboot"
date: 2015-03-13
forum: Hardware
---

### Post by peridian on 2015-03-13
Hi,

The motherboard of this system is an Asus H87I-Plus, and ever since enabling the Wake-On-Lan feature in the motherboard, the shutdown command seems to result in a reboot instead.

If I physically switch the system off, it stays off until I send the magic packet to wake it up.  However, all calls to shutdown now reboot instead.

I have tried combinations of "acpi=off" (which actually stalls the boot up) and "noapic" (doesn't do anything).

```

ethtool em1
...
Supports Wake-On: pumbg
Wake-On: g

```

Any recommendations on working around this problem?

Regards,
Rob.

---

### Post by tgalati4 on 2015-03-13
Make a list of what parts of the motherboard bus remain powered during sleep:

```
sudo apt-get install acpitool
acpitool -w
```

---

### Post by peridian on 2015-03-14
Output below:

```

user@hostname:/$ sudo acpitool -w
   Device    S-state      Status   Sysfs node
  ---------------------------------------
  1. PS2K      S4    *enabled   pnp:00:0a
  2. GLAN      S4    *enabled   pci:0000:00:19.0
  3. EHC1      S4    *enabled   pci:0000:00:1d.0
  4. EHC2      S4    *enabled   pci:0000:00:1a.0
  5. XHC      S4    *enabled   pci:0000:00:14.0
  6. HDEF      S4    *disabled
  7. PEG0      S4    *disabled  pci:0000:00:01.0
  8. PEGP      S4    *disabled
  9. PEG1      S4    *disabled
  10. PEG2      S4    *disabled

```

Out of interest, is it possible for a BIOS to prevent the shutdown command from working on purpose?

I don't know how smart they are these days.  I was thinking that since you would want to put the system to sleep rather than switch it off when wake-on-lan is enabled, I wondered if the shutdown command has been deliberately switched to a reboot to avoid turning it off altogether.  That might also explain why physically pressing the button worked, I didn't switch it off it just went to sleep instead.

Regards,
Rob.

---

### Post by tgalati4 on 2015-03-14
Yes, the BIOS can control the behavior of the power button.  Some have a setting:  Shut down immediately, shut down after pressing for 4 seconds, go-to-standby.

Understand that Wake-on-Lan can be boot-on-lan on some systems that have a network card that will boot the system when off, but plugged in.  

Check the BIOS for "Wake from USB devies" and turn that off.

First, I would check the BIOS version and update it to the latest.  Then I would look in the log files to see what is preventing power off.

Remove any extraneous USB devies, they can draw power and feed that power back to the system during shutdown causing a wake/boot cycle.  If that is the case, then you need to disable power to that part of the bus using *acpitool.*

---

### Post by peridian on 2015-03-15
In the end I just replaced the shutdown command with "pm-suspend".

I installed powermanagement-interface but the command "pmi action suspend" kept giving me errors about a missing Hal lib.  Then I installed pm-utils, and found that pm-suspend works beautifully.

Furthermore, in the logs during the suspend, there are some very clean messages about syncing and shutting down disks, making it safer than my previous use of the shutdown command (see [here]("http://ubuntuforums.org/showthread.php?t=2268632")).

I've done some testing of this.  I needed to setup a wol command on my firewall, as the packet is local to the ethernet subnet and the target was on a separate VLAN from the script being fired.  Not a big deal, since the cron times are all pre-arranged.

However, the device powers up five minutes before the script fires, everything runs as expected, and at the end, the local script performs the suspend, and the whole thing goes to sleep cleanly.  It does not wake up again until the next cron job.

My guess is that something does change the nature of shutdown on this particular board, but since I've achieved what I am after, I am unlikely to need the shutdown command from here onwards.

Thanks,
Rob.

---

