---
title: "Wake on Lan"
date: 2010-01-14
forum: Hardware
---

### Post by huangyingw on 2010-01-14
Hello,
     Has someone successfully wake up your PC through Lan?
     I had a rougher confusing experience. That is: the same machine and same hardware, same bios setting, with windows 2003 system, I could remotely wake up that machine through a tool called wol.exe, 
     While, after switching to Ubuntu system, that same machine and without any bios setting change, could not wake up. Just simply no resonose to my wol.exe's network message.
     I am confused: does the WOL function has something to do with OS ?

---

### Post by Cheesemill on 2010-01-14
WOL has nothing to do with the OS, it's implemented completely in the motherboard and BIOS.

---

### Post by huangyingw on 2010-01-14
> **Cheesemill said:**
> WOL has nothing to do with the OS, it's implemented completely in the motherboard and BIOS.
Yes, I also think so. While, what confused me is the fact that after switching to Ubuntu from Windwos 2003 on the same hardware, the WOL function totally not work now...:(

---

### Post by tgalati4 on 2010-01-14
Ubuntu can control what stays awake during shutdown.  So there is some control with the OS.  Search the forums for some decent tutorials.

Make sure your /etc/network/interfaces is set up correctly:  (for example)

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
# Changed 4 Jan 2010 to static
# iface eth0 inet dhcp
iface eth0 inet static
address 192.168.1.252
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
post-up /usr/sbin/ethtool -s eth0 wol g
post-down /usr/sbin/ethtool -s eth0 wol g

Install acpitool if you haven't already done so:

sudo apt-get install acpitool

Run it:

acpitool -w

Make sure it looks something like:

tgalati4@gc-development:~$ acpitool -w
   Device       S-state   Status   Sysfs node
  ---------------------------------------
  1. PCI0         S5     disabled  no-bus:pci0000:00
  2. RTC          S5     disabled  pnp:00:06
  3. PCI3         S5     disabled  no-bus:pci0000:03
  4. PCI2         S5     enabled   no-bus:pci0000:02
  5. PCI1         S5     disabled  no-bus:pci0000:01

To enable device #4 for wakeup (i.e. leave enough power on after shutdown so it will reactivate):

$ sudo acpitool -W 4
  Changed status for wakeup device #4 (PCI2)

   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. PCI0	  S5	 disabled  no-bus:pci0000:00
  2. RTC	  S5	 disabled  pnp:00:07
  3. PCI3	  S5	 disabled  no-bus:pci0000:03
  4. PCI2	  S5	 enabled   no-bus:pci0000:02
  5. PCI1	  S5	 disabled  no-bus:pci0000:01

You need to leave part of your motherboard bus powered.  Obviously the pci slot that contains your network card. (lscpi -vv to discover)

When you shut down your machine, you need to make sure that the network light on your router port stays on.  If not, then make changes.  No router light, no WOL.

Helpful site if you have a Dell Poweredge 1750: [http://www.htgi.ca/node/25](http://www.htgi.ca/node/25)

---

### Post by huangyingw on 2010-01-16
> **tgalati4 said:**
> Ubuntu can control what stays awake during shutdown.  So there is some control with the OS.  Search the forums for some decent tutorials.

Make sure your /etc/network/interfaces is set up correctly:  (for example)

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
# Changed 4 Jan 2010 to static
# iface eth0 inet dhcp
iface eth0 inet static
address 192.168.1.252
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
post-up /usr/sbin/ethtool -s eth0 wol g
post-down /usr/sbin/ethtool -s eth0 wol g

Install acpitool if you haven't already done so:

sudo apt-get install acpitool

Run it:

acpitool -w

Make sure it looks something like:

tgalati4@gc-development:~$ acpitool -w
   Device       S-state   Status   Sysfs node
  ---------------------------------------
  1. PCI0         S5     disabled  no-bus:pci0000:00
  2. RTC          S5     disabled  pnp:00:06
  3. PCI3         S5     disabled  no-bus:pci0000:03
  4. PCI2         S5     enabled   no-bus:pci0000:02
  5. PCI1         S5     disabled  no-bus:pci0000:01

You need to leave part of your motherboard bus powered.  Obviously the pci slot that contains your network card.

When you shut down your machine, you need to make sure that the network light on your router port stays on.  If not, then make changes.  No router light, no WOL.

Helpful site if you have a Dell Poweredge 1750: [http://www.htgi.ca/node/25](http://www.htgi.ca/node/25)
Great, your guidance is very usefull to me. Now, my WOL on Ubuntu has worked.

---

### Post by Pitel on 2011-11-12
Um, I think I have a problem:

According to lspci, my eth0 is PCI device 04:00:0 (I don't have any other network cards)

```
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
```

But acpitool -w gives me:

```
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. P0P2	  S4	*disabled  pci:0000:00:01.0
  2. P0P1	  S4	*disabled  pci:0000:00:1e.0
  3. PS2K	  S4	*enabled   pnp:00:08
  4. PS2M	  S4	*disabled  pnp:00:09
  5. USB0	  S4	*disabled  pci:0000:00:1d.0
  6. USB1	  S4	*disabled  pci:0000:00:1d.1
  7. USB2	  S4	*disabled  pci:0000:00:1d.2
  8. USB5	  S4	*disabled  pci:0000:00:1d.3
  9. EUSB	  S4	*disabled  pci:0000:00:1d.7
  10. USB3	  S4	*disabled  pci:0000:00:1a.0
  11. USB4	  S4	*disabled  pci:0000:00:1a.1
  12. USBE	  S4	*disabled  pci:0000:00:1a.7
  13. P0P4	  S4	*disabled  pci:0000:00:1c.0
  14. P0P5	  S4	*disabled  
  15. P0P6	  S4	*disabled  
  16. P0P7	  S4	*disabled  
  17. P0P8	  S4	*disabled  pci:0000:00:1c.4
  18. P0P9	  S4	*disabled  pci:0000:00:1c.5
```

There is no 04 device! I have PCI wake enabled in BIOS. Am I screwed? :(

---

### Post by coffeecat on 2011-11-12
@Pitel, please start your own support thread.

Old thread closed.

---

