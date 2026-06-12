---
title: "USB trouble"
date: 2007-03-14
forum: Hardware &amp; Laptops
---

### Post by inthedark on 2007-03-14
I'm really having trouble with this -  USB is not working well at all.

1. USB storage devices (external Seagate HDD, Disgo flash drive) are only detected if they are plugged in when Ubuntu starts - you can eject them, but can't get them back on after that.

2. My Epson scanner is recognised under the Device Manager but not by sane. Actually I think that sane is not recognising it because:

3. lsusb just hangs - comes up with no results and I have to close the terminal window to stop its process. Therefore I guess that sane is a red herring at this point. Basically USB ain't working.

Can anyone help me with this?

---

### Post by teaker1s on 2007-03-15
while I'm not sure of the reason, most of your usb devices appear to be usb 2.0.
 Supposed to be backwards compatible with usb1.0 -I've found some things that are usb2.0 take an age to work on 1.0 or just don't work. could this possibly be the issue?

---

### Post by inthedark on 2007-03-15
First of all, thanks for taking the trouble to reply.

All the devices are USB2.0, I don't think I have anything that's only 1.0 / 1.1 so probably won't be able to test this theory. The USB buses on the PC are part of a nvidia chipset and are definitely 2.0. 

The thing I can't get my head around is that the Device Manager can see the devices, and allows hot plugging/unplugging no problem. It's just that anything trying to list the devices (even if there's nothing plugged in) just hangs. This goes for lsusb and sane.

Any ideas how to start to look for a solution - what would you look for if it happened to you?

---

### Post by teaker1s on 2007-03-15
i'd be looking for bug report or hotplug or nvidia driver update for these, I don't know the answer to your issue but that's what I'd do. 

Not the same but I have a debian etch system laptop for weeks I've tried to get sound out of the speakers and people suggested setting model etc for alsa/compiling alsa and no joy- out of shear last ditch effort. I disabled esd and system sounds. completely uninstalled alsa, rebooted and reinstalled=sound. I can only guess that system beep/esd blocked it.

If you figure out what effects completely removing hotplug will do, uninstall,reboot reinstall-maybe it just installed badly

---

### Post by inthedark on 2007-03-15
Thanks. I've already installed different nvidia drivers and raised the issue over on the nvidia forums (no reply as yet).

I'll have a look to see if hotplug can be reinstalled.

---

### Post by inthedark on 2007-03-15
Hmm, can't find anything to do with hotplug. 

```
paul@SylvesterLinux:~$ dmesg|grep hotplug
[   67.890295] pci_hotplug: PCI Hot Plug PCI Core version: 0.5


```

Anywhere else to look? There's nothing in Synaptic Package Manager.

---

### Post by inthedark on 2007-04-25
Well, I've upgraded to Feisty and the problem still remains:

1. external drives and memory sticks are recognized fine if they are plugged in when you boot the machine or restart X. If you eject them, they will not be recognized if you plug them back in.

2. Unloading the ehci_hcd module and then reloading it reconnects the external drives or memory sticks, but they wont work if that module is not there.

3. Other USB devices (camera, scanner, mouse) get no response. They appear in the Device Manager, but there's no way of accessing them.

4. using the lsusb command at any time hangs the terminal window - no difference if there are no usb devices plugged in, only drives, only non-storage devices or a mixture of both.

5. tried disabling acpid and apic on boot - no change.

I've attached output from lspci which shows what the controllers are. Happy to upload any other text files if necessary to get an idea of what's going wrong on this. Can anyone help?

---

### Post by inthedark on 2007-04-29
*bump*

Anyone have any ideas?

---

### Post by franco_bez on 2007-05-01
Hi, I seem to have quite similar trouble here.

On my Notebook I recently upgraded from Edgy to Feisty and now the USB devices are no longer reliably hotplugable.

With Edgy all worked fine.

But with Feisty the USB Devices work when connected at boot time.
When a device gets connected afterwards it's most often NOT detected at all.
Espescially USB Storage Devices are not detected.

I did a little testing and came up with no solution so far.

The Problem is the same with Feisty i386 and amd64, also the Feisty (install) Live CD has the same Problem on my machine.

Hardware: FSC Amilo A1630 (Athlon64 3700  1GB Ram)

STRANGE !!!!:confused: 
I just did a little additional testing while typing in this post and I seem to have found a clue to my problem:

My USB Bluetooth Adapter (working fine both with Edgy and Feisty) seems to be some kind of trigger to all the trouble.

When I remove the USB-BT Sticks , all seems to work fine !!!!:confused: 
When the Stick is connected - autodetection seems to be blocked - no device removal, and no device addition is logged.
Unplugging / Plugging the USB-BT Stick changes all - very very strange ...

Even more strange is the fact that ALL of my USB Devices do work fine (once they are detected) INCLUDING the USB BT Stick !!:confused:

---

### Post by inthedark on 2007-05-01
That's interesting, when I tried to run the upgrade from Edgy to Feisty, it hung when trying to stop the Bluetooth driver - and I don't have Bluetooth at all. I wonder whether there's something up with the BT stuff under Ubuntu?

Can't check it now - I got fed up with this in the end and have migrated to Suse. No problems whatsoever with USB on that.

---

### Post by ender42 on 2007-05-21
Yeah, I was having issues (and got no love here), am migrating backwards to Hoary to get my USB back.

---

