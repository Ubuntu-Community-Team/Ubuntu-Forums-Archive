---
title: "[SOLVED] USB Problem, &amp;quot;PCI: No IRQ known for interrupt pin A of device...&amp;quot;"
date: 2007-03-01
forum: Hardware &amp; Laptops
---

### Post by Simon G Best on 2007-03-01
Hello!

I've got a problem trying to get USB working (which I've never had working with Xubuntu 6.10 (Edgy Eft)).  As I need to print out a letter, I now really do need to get USB working.

lsusb gives this:-

```
sgbest@olympus:~$ lsusb
sgbest@olympus:~$
``` 

(Nothing, in other words.)

lshw gives this (edited):-

```
sgbest@olympus:~$ sudo lshw
Password:
olympus                   
    description: Desktop Computer
    width: 32 bits
    capabilities: dmi-2.0
    configuration: chassis=desktop
  *-core
       description: Motherboard
       product: 5600
       vendor: SiS
       physical id: 0
       version: 0.00
...
     *-pci
          description: Host bridge
          product: 5600 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: e8000000
          bus info: pci@00:00.0
          version: 11
          width: 32 bits
          clock: 33MHz
          resources: iomemory:e8000000-efffffff
...
        *-usb UNCLAIMED
             description: USB Controller
             product: USB 1.0 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1.2
             bus info: pci@00:01.2
             version: 11
             width: 32 bits
             clock: 33MHz
             capabilities: ohci
             resources: iomemory:e7fff000-e7ffffff
        *-pci
             description: PCI bridge
             product: Virtual PCI-to-PCI bridge (AGP)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
...
```

lsmod gives this (edited):-

```
sgbest@olympus:~$ lsmod
Module                  Size  Used by
...
ohci_hcd               22532  0 
usbcore               134912  2 ohci_hcd
...
```

And dmesg gives this (edited):-

```
sgbest@olympus:~$ dmesg
...
[17179569.184000] Kernel command line: root=/dev/mapper/VolGroup01-LogVol00 ro acpi=off noacpi quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
...
[   41.890888] usbcore: registered new driver usbfs
[   41.894976] usbcore: registered new driver hub
[   41.909718] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[   41.913665] PCI: No IRQ known for interrupt pin A of device 0000:00:01.2. Please try using pci=biosirq.
[   41.913707] ohci_hcd 0000:00:01.2: Found HC with no IRQ.  Check BIOS/PCI 0000:00:01.2 setup!
[   41.913737] ohci_hcd 0000:00:01.2: init 0000:00:01.2 fail, -19
...
```

(ACPI (not to be confused with APIC (yeah?)) is disabled at boot time, because there were terrible problems with the mouse and keyboard otherwise.  (The problems aren't entirely solved by disabling ACPI, but are sufficiently mild not to be much of a problem in practice.))

I tried the "Please try using pci=biosirq" suggestion, but it made no difference (except that it no longer made that suggestion).

Any ideas?

:)

---

### Post by davidmit on 2007-03-18
At least somebody else is having my problem then :0), My system freezes when i connect a USB device, does yours??

Anybody help us??

---

### Post by Simon G Best on 2007-03-19
> **davidmit said:**
> At least somebody else is having my problem then :0), My system freezes when i connect a USB device, does yours??

I did plug a camera in a while ago, but it didn't freeze anything.  I'll try it again, and see what happens...

Nothing.  No freezes, no messages when I looked at dmesg, just nothing.

> Anybody help us??

I hope so, but so far you're the only respondent :-(

---

### Post by Simon G Best on 2007-05-11
Hooray!

I've finally solved my USB problem.

After a bit of playing around, trying different combinations of things, including BIOS settings, I found I could get USB working by telling the BIOS that I'm using a "Plug'n'Play aware OS" (or however it was it actually worded it).  USB now works, and I am happy.

---

### Post by Owlman on 2007-05-13
Same problem. None of my USB ports seem to work, nor my parallel port (with a scanner plugged into it).  Is there anyway to verify that the ports are actually physically working? The only way I can figure to check for sure is to install Windoze and see if it can see them.

Went through my BIOS with a fine tooth comb. There is nothing in it that says anything to do with a PnP OS.

All help and advice gratefully received,
Ian

---

### Post by Simon G Best on 2007-05-14
> **Owlman said:**
> Is there anyway to verify that the ports are actually physically working?

How about booting a Knoppix CD?  Perhaps an older version of Knoppix, with an older kernel?  (Since my USB ports worked fine with RedHat 9 (and I don't think I'd changed the BIOS setting I mentioned), I'm thinking that there might have been a relevant kernel change at some point.)  If your ports work with Knoppix, then you'll know your hardware's working.  Otherwise, well, you'll have established that your ports aren't working with those versions of Knoppix, either.

By the way, my PC is old.  It has a 1998 BIOS.  I believe my PC will be nine years old sometime this year (but I don't know when, exactly).

---

### Post by Owlman on 2007-06-24
Thanks for the idea, I'll definitely give it a belt. One of those "why didn't I think of that" ideas...
My machine is pretty new, AMD64 X2 3600+ (the source of many of my problems I'm sure...)

Cheers, Ian

---

### Post by Owlman on 2007-06-26
Booted with a Knoppix live CD. Plugged my USB memory stick into a USB slot, and....

Zip, zero, zilch, nada, nuthin'. Think my USB slots have had the RIchard, burgered, NBG, no longer functional....

---

### Post by webcamkid on 2007-07-07
where is the bios at.what is the bios:confused:

---

### Post by Owlman on 2007-07-09
It's a Gigabyte mobo (for AMD64 X2) with an Award bios. Not sure what version... it's a relatively new mobo so I imagine the bios would be fairly recent. How do I get the bios version? Do I have to go into bios setup (on boot) or is there a way to do it from within Linux?

Thanks,
Ian

---

