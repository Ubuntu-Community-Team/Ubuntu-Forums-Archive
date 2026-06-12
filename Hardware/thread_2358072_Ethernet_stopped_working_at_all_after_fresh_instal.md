---
title: "Ethernet stopped working at all after fresh install (Ubuntu Mate 16.04)"
date: 2017-04-09
forum: Hardware
---

### Post by fredmbarros on 2017-04-09
I know it looks like a common problem, but the thing is: after having  normal network connectivity during the live session, install and the  still after the first reboot, it all stopped working after a night in  suspend mode.
  I usually have Wi-Fi connectivity enabled, but never bother  connecting to my wireless network as I have ethernet connected too.  That's how it went during live, install and first boot. When  installation was finished I did a reboot, installed some software* then  put the machine on 'suspend' and went to bed.
  As I woke up the following day I had no connectivity. The ethernet  interface could not be found and strangely Wi-Fi could only see one  obscure network - and it wasn't mine. Restarted the computer and Wi-Fi  came back to normal, but I still have no ethernet at all. I did a lot of  research on Google, switched cables, reset BIOS/UEFI to factory  defaults, flashed BIOS, tried live sessions and reinstalled Debian,  vanilla Ubuntu and Mate again, upgraded it to 16.10 and still I have no  ethernet, only Wi-Fi.
  I read somewhere that the ethernet port on Gigabyte MBs has  durability issues. So the fact that ethernet now doesn't work with other  distros too makes it look like a physical problem. The only thing that  leaves me still wondering is that Wi-Fi stopped too, but got back to  properly funcioning after a reboot, whereas ethernet didn't.
  Well, that's it. Does anybody have at least an idea of what happened and if there's a solution?
  Thanks a lot!
  *I don't know if it's of any use, but the software I installed was  Chromium, Chrome, Tor browser, Atom Text Editor and Musescore. My MB is a  GA-Z97M-D3H, with onboard ethernet, sound and graphics. 8GB RAM.

---

### Post by TheFu on 2017-04-09
Suspend is a common issue. Devices have to be cleanly shut down, then brought back up cleanly. That doesn't always happen.

So - to begin, disable wifi and concentrate on getting the wired ethernet working.  On Linux, everything depends on the specific chips used. What model ethernet chip is being used?  Did you search for driver issues with that?

To start, please post output (using "code tags" as shown below):
```
$ sudo lshw -C network
```

This will show which network devices your system has and which drivers have been loaded.  Then you can search for the correct driver for the specific chip used. Sometimes the wrong driver is loaded and we need to help the kernel figure out the correct one to load. Sometimes a few driver options are helpful - especially with wifi.  Realtek has a bunch of issues like this.  The intel NICs generally "just work", for future reference. And intel NICs have better off-loading from the CPU, so network traffic doesn't use much CPU at all, unlike other NIC makers.  These days, it is less than $10 difference in price to get intel NICs (or onboard).

So ... for example, here's what my chromebook says:
```
$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: **Wireless 7260**
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: bb
       serial: 4c:eb:42:cb:20:01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=**iwlwifi** driverversion=4.4.0-71-generic firmware=17.352738.0 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:45 memory:e1000000-e1001fff
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: virbr0-nic
       serial: 52:54:00:20:20:01
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=**tun** driverversion=1.6 duplex=full link=no multicast=yes port=twisted pair speed=10Mbit/s
  *-network:1
       description: Ethernet interface
       physical id: 2
       bus info: usb@2:1.1
       logical name: eth0
       serial: 00:23:55:3c:20:01
       size: 100Mbit/s
       capacity: 1Gbit/s
       capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=**ax88179_178a** duplex=full link=yes multicast=yes port=MII speed=100Mbit/s
```

The 1st and 3rd devices are real - a wifi chip and USB GigE ethernet (chromebooks don't have wired ethernet, so I use a USB adapter).  The 2nd device is a virtual bridge that I setup for virtual machines to use. It isn't used right now, so "disabled" is fine. My chromebook is powerful enough for KVM VMs.

So I'd google for "ax88179_178a ubuntu" if my GigE wasn't working at all to see if there are known issues AND known solutions. BTW - looking at this, I see the "size" of 100Mbit/s - which isn't correct. I have an issue. My wired network is all GigE capable and I've tested the connection from this machine to others and seen 920Mbit/s connection. Something isn't correct.  Ran that same test a few seconds ago ... 94.3 Mbits/sec - not good.  I definitely have an issue.   Was a loose cable - tested at 921 Mbits/sec again. Solved and it is just the connector on the USB-2-GigE device.

Hope this explanation helps you to go fishing. ;)

---

### Post by fredmbarros on 2017-04-09
Thanks for all the help for solving this by myself. I appreciate it and I'm willing to go by myself, for sure, but I'm afraid I'll need some more help. I ran lshw and it doesn't detect ethernet, only the Wi-Fi interface.

I'm more and more inclined to think that my onboard ethernet chip just went south, but why did it? Could an OS install do it? I don't think so, but what do you people think?

Anyway, here's the output of "lshw -C network". As you can see, there's only Wi-Fi there.

*-network               
       description: Wireless interface
       product: AR93xx Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 01
       serial: c0:4a:00:17:96:47
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=4.8.0-46-generic firmware=N/A ip=192.168.0.32 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:f7c00000-f7c1ffff memory:f7c20000-f7c2ffff

From the motherboard manual, I can only see that my ethernet chip is Realtek GbE LAN, no further info about it.

---

### Post by TheFu on 2017-04-10
Could be almost anything that breaks onboard ethernet. I've never seen it, but I have seen a cracked motherboard lead to corrupted file transfers 1-time in my career. Listing all the reasons something has failed isn't very productive - there are thousands. power spike, filaments causing a short, overheating, incorrectly wired cable, the machine could have been jarred/bumped. Anything.  Might try blowing out any dust inside the machine to see if that helps.

To fix it, you can insert an addon card - get an intel PRO/1000 type card (many reasons) for $25 
or
get a USB3-to-GigE adapter for $22. Probably should get one with a few USB3 ports, so you don't loose a port. Stay with USB3 for GigE.
or
live with slower, wifi, connections and lesser security.

---

### Post by fredmbarros on 2017-04-11
Ok, I see. Thanks! I was just curious to know if the Ubuntu Mate installation could have by any means caused it...

Well, I'll see what I'll do about the addon card. Those 25-dolar-cards are ridiculously expensive here in Brazil. There are less expensive ones by Intel, but they do not explicitly state PRO/1000, like, for instace, EXPI9301CTBLK. This ones won't have the same advantages, will they?

---

### Post by TheFu on 2017-04-11
$26 - [https://www.amazon.com/Intel-Gigabit-Network-Adapter-EXPI9301CTBLK/dp/B001CY0P7G](https://www.amazon.com/Intel-Gigabit-Network-Adapter-EXPI9301CTBLK/dp/B001CY0P7G) should work fine. According the the questions about the specific driver used for Linux, it uses the same e1000e driver that works so well with the PRO/1000 NICs.

Make certain that is the driver (or newer) for the card you get.

Mine have intel 82574L or i210AT chips. My point is that I don't have 1st-hand knowledge of that chip.

---

