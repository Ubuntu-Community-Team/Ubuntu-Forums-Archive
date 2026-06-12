---
title: "Network Card Not Enabled"
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by hollystyles on 2008-02-13
Hi All,

So I want to join the Linux community. I am who I am because I know my limits so I went for the best distro currently available for ease of installation. I've worked in technical support and been a developer for 8 years now so I'm fairly savvy but this one has me stumped because I'm in foreign territory.

(Get to the point? yes ok sorry)

So I have a Network card (Lucky me eh!) it's a Netgear FA311 - RevB1 10/100 Ethernet PCI card. I understand this has National Semiconductor Corproation DP83815 (MacPhyter) blah chip and the correct Linux module to drive it is natsemi.o

So, I tend not to have my network card wired in when I'm installing an OS and that was the case here.

The installation was error free, cool. So I plug in my ethernet cable and I went to System -> Administration -. Network, entered my root password and.... no sign of the nic whatsoever ???

The fun begins!

Sigh... >lspci
00:0a.0 Ethernet Controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
-No problem there then

>lsmod | grep natsemi
natsemi                31328    0

ok not driving anything but at least it's loaded.

>ifconfig -a
lo              Link encap:Local Loopback
                inet addr:127.0.0.1 Mask:255.0.0.0
                :
                etc

NO eth0 !!!!! Wha????

ok >dmesg | grep eth
>

????? nothing, nada, Fanny Adams ???????

>grep natsemi /var/log/messages
Feb 13 15:00:33 COMPNAME kernel: [ 122.667776] natsemi dp8381x driver, version 2.1, Sept 11, 2006
Feb 13 15:00:33 COMPNAME kernel: [ 129.328933] natsemi: probe of 0000:00:0a.0 failed with error -16

Doesn't look good to me, of to Google several days later no hits for the mysterious error 16 I end up here.

So that's my story. I wonder if I have an IRQ issue or ??? I could use some help cos I have no idea how to do that in Linux.

Other things I've done is 
>sudo nano /etc/modprobe.d/natsemi.modprobe
and typed
alias eth0 natsemi

>sudo update-modules

No sign of any modprobe.conf or modules.conf or conf.modules being created ??

That's it I have exhausted all my knowledge, what next?

So  Linux Gurus, I humbly request your asisstance to bring this poor lost Win32 sheep out of the cold and into the fold.

](*,)

---

### Post by oldsoundguy on 2008-02-13
not a clue if this will work, but I installed 7.10 on three machines .. 2 with D-Link wireless cards  .. BUT when doing the initial install, hard wired them to the router via the nic.  THE ONBOARD nic!  So. to me, that indicates that network cards are really not that much a problem when the system sees them with an install.

IF you don't have a bunch of DATA already involved, just maybe a re-install will be the ticket.

Could be wrong, have been before.

---

### Post by Yellow Pasque on 2008-02-13
Try looking in /etc/network/interfaces. You should have something like this (and probably more interfaces that aren't in use and commented out):
```
dan@harvest:/etc/network$ cat interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```

Also, try sudo lshw -C network:
```
dan@harvest:/etc/network$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
      **logical name: eth0**
       version: 01
       serial: 00:19:db:b1:04:27
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no **module=r8169** multicast=yes port=twisted pair
```

---

### Post by hollystyles on 2008-02-15
Thanks for the suggestions. I have the machine at work currently and I'm on holiday for a couple of days. As soon as I'm back in on Monday I'll let you know how it goes.

To be continued...

---

### Post by hollystyles on 2008-02-27
Well I tried the re-install with my NIC wired into the LAN. The live-cd boot didn't detect my network card which worried me (I hadn't noticed this first time around) Also during instal Ubuntu tells me it can't get security updates suggesting networking was still a problem.

Anyway after the install is complete and it tells me to restart, I pressed ESC while Grub was loading and edited the Kernal line, adding acpi=off at the end of the line.

Now my network is up and running. so this would seem to be the solution for now.

---

### Post by hollystyles on 2008-02-27
And here I am posting from my now connected Ubuntu box! yipee !!!!

---

### Post by hollystyles on 2008-02-29
Ok just to be precise and provide all details for any other newbs.

My fix two posts up wasn't permanent. I had to edit the menu.lst file in /boot/grub/ using sudo nano, save and restart.

Now the setting survives restarts.

---

