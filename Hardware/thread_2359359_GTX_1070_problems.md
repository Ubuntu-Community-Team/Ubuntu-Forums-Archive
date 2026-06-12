---
title: "GTX 1070 problems?"
date: 2017-04-23
forum: Hardware
---

### Post by MikeCyber on 2017-04-23
Hi
I've not yet tried on Widnows but on 16.04 about every half hour Alien Isolation, X-Plane, Tomb Raider crash. AI almost regularly.
Is this a know bug with gtx1070? Should I return the card? A complete freeze followed by a auto reboot.
Thanks

---

### Post by Bucky Ball on 2017-04-23
> **MikeCyber said:**
> Is this a know bug with gtx1070?

Not that I know of or have seen, no. You are sure you have the correct driver installed for that card? Did you install it from Additional Drivers? Did you do an update/upgrade after installing the new hardware?

```
sudo apt update
sudo apt full-upgrade
```

(The last command will not upgrade your OS to a newer release, just the software.)

If not, run the above commands, reboot and check the Additional Drivers and see if anything new pops up. If you simply jammed in the new card and booted up it may be using whatever driver it was using for the last or getting confused by its absence. Or something ... 

Post the output of this command, please.

```
sudo lshw -C video
```

---

### Post by Autodave on 2017-04-23
When it reboots on its own, does it then function normally?

Rebooting on its own makes me think that it is more more likely a hardware problem: memory chip failing or overheating would be my first guess.

---

### Post by Bucky Ball on 2017-04-23
> **Autodave said:**
> Rebooting on its own makes me think that it is more more likely a hardware problem: memory chip failing or overheating would be my first guess.

That's also where my brain's leading me. Works fine then crash. Overheating? :-k

---

### Post by efflandt on 2017-04-23
Does /var/log/syslog or any other log in /var/log give any clue what happened just before the spontaneous crash/reboot? Which nvidia driver package are you running? There is a graphics-drivers ppa for more recent nvidia driver packages. Once you add the ppa Additional Drivers would show newer driver packages.

I am running Asus Dual GTX 1060 OC with nvidia-378 drivers without any issues (including Steam games), have not tried nvidia-381 yet. I only have (1) 6-pin power connector, not power connector(s) suitable for a GTX 1070. But I am running Ubuntu 64-bit 16.10 because 16.04 would blank out all text during cold boot or reboot until something did graphics (blank BIOS splash and grub menu, until gui login). I did not have that trouble w/16.04 on any other computer, so I guess I should try 16.04 again and see if that still happens.

---

### Post by MikeCyber on 2017-04-23
Just played over an hour AI on Windows10 without crash. Hence Ubuntu related. Updated as above:
michael@michael-ubuntu:~$ sudo lshw -C video
[sudo] password for michael: 
  *-display               
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:31 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
michael@michael-ubuntu:~$ 

Will play tomorrow again Alien Isolation on Ubuntu. nvidia-settings says that I'm using the latest nvidia: 375.39
Thanks

---

### Post by Bucky Ball on 2017-04-23
Mine looks like this.

```
sudo lshw -C video
  *-display               
       description: VGA compatible controller
       **product: GM204 [GeForce GTX 970]**
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:129 memory:de000000-deffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:e000(size=128) memory:df000000-df07ffff
```

Notice the product? It defines the GTX 970 specifically. Yours does not identify the card specifically. Which driver do you have enabled in 'Additional Drivers'?

---

### Post by Yellow Pasque on 2017-04-23
> **Bucky Ball said:**
> Notice the product? It defines the GTX 970 specifically. Yours does not identify the card specifically.

That should not affect the function of the card/driver. All that means is the GTX 1070 was not yet in the database of PCI names when Ubuntu 16.04 was released. This will probably "fix" it: 
```
sudo update-pciids; sudo update-usbids
```

---

### Post by MikeCyber on 2017-04-24
sudo update-pciids; sudo update-usbids
didn't help. Still no name in lshw. Additional software says that I 
use a manually installed driver and can't change it there.
In first Ubuntu install I installed default nvidia and later updated 
with drivers from Nvidia site.
Well I did update yesterday Ubuntu and now also the driver. Hopefully 
this helps, else I'll report back later in the day.
Thanks

---

### Post by Bucky Ball on 2017-04-24
> **MikeCyber said:**
> Additional software says that I use a manually installed driver and can't change it there.

It doesn't tell you which? We still don't know which version of the driver you're actually using right now. All we know is an 'nvidia driver'.

---

### Post by MikeCyber on 2017-04-24
The latest nvidia: 375.39
Probably updating fixed it. Played an hour Alien Isolation without crash. I feel relief that I don't need to return my card.
Thanks

---

