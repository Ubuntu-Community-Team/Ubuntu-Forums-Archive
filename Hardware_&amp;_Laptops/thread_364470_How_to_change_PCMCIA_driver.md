---
title: "How to change PCMCIA driver"
date: 2007-02-18
forum: Hardware &amp; Laptops
---

### Post by Flayra on 2007-02-18
Hey

I'm a complete Ubuntu (and Linux for that matter) beginner when it comes to setting up hardware. I'm using an old Dell Latitude laptop (dunno what number, but it's a 400 Mhz to say something of how old it is).

This model doesn't come with network integrated so I'm using a PCMCIA card for this - Xircom CreditCard blablabla.

Anyway, the problem is it is not working - Ubuntu registers the card fine (with pccardctl ident and such) but I cannot use it for networking. It registers as using the driver "serial_cs". From looking around and using google (a lot) I've found out that I need it to use the xirc2ps_cs driver instead - how do I change it? I've done modproble xirc2ps_cs (which doesn't return anything) but I haven't been able to see anywhere how I can change which driver it uses.

I'm running Ubuntu 6.10.

On a small sidenote, which keyboard layout should I use for the Dell Latitude laptops? I can't seem to use the pageup/pagedown which gets frustrating when getting multiple-screen output (such as dmesg).

Any help appreciated :)

---

### Post by tgalati4 on 2007-02-20
Hello Flayra
Try using:  dmesg | more
That will page the dmesg file one page at a time.
Or: dmesg | grep _cs
to find all occurances of "_cs" in your dmesg file.  That will help get around the page up/down problem.

I can't help with the keyboard layout--I have an old Inspiron--the keys seems to work.  There are several keyboard remapping and keycode discovery tools available.  I assume that you have tried all of the standard keyboard types.

Share with us the output of:  lspci

I also have a working Xircom card with a loose dongle.  It sometimes causes the machine to lock up.  It also gets uncomfortably hot.  I replaced it with a wireless card that works well.

You might need to blacklist serial_cs first then modprobe xirc2ps.

Ubuntu 6.06 picked up my card automatically, so perhaps the card is not working?  Did it work previously under (shutter, Windows?)

Also, try complete shutdown and put the card in the second slot and reboot.

Good Luck,

Terry

---

### Post by Flayra on 2007-02-21
Hey, thank you for the reply.

The card was working fine just hours earlier with Windows 2k, but I have no way of testing now since I erased the entire harddrive (intentionally) - but still, I doubt that something is wrong with the card.

How do I blacklist serial_cs? I saw something earlier but I'm not entirely sure. Also, lspci won't do any good since it's a PCMCIA card (doesn't register there afaik).

---

### Post by tgalati4 on 2007-02-21
Try a quick search on "blacklist" in the blue forum search bar.

This might work, type in terminal:  sudo gedit /etc/modprobe.d/blacklist

add at the bottom of the file:  blacklist   serial_cs

Save the file and reboot.

lspci will give interrupt values for all pci devices including pcmcia, since it is an extenstion of the pci bus.

try dmesg | grep xirc       (to see if the card gets picked up automatically)

---

### Post by Flayra on 2007-02-21
Ok I blacklisted it and it seems to be almost working now ;)

I have a router acting DHCP server so I setup eth0 with:
auto eth0
iface eth0 inet dhcp

When I reloaded the network it called for the DHCP server and I got 6 lines of:
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval #

After those lines I get:
No DHCPOFFERS received.
No working leases in persistant database - sleeping.

Any idea why it won't pick up an address?

Another funny thing if I do 'sudo ifconfig' I get this for eth0:
Link encap:Ethernet  HWaddr 00:10:A4:E1:8C:B2
inet6 addr: fe80::210:a4ff:fee1:8cb2/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
blablabla

How come it has an ipv6 address and no ipv4?

Thanks for any help you can give ;)

---

