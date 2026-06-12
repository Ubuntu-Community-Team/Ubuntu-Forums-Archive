---
title: "wireless card will not work."
date: 2005-01-24
forum: Hardware &amp; Laptops
---

### Post by Sham on 2005-01-24
Hi all,


I followed the instructions here  to get nidiswrapper working working with a Netgear MA521:
[http://www.ubuntulinux.org/support/documentation/howto/ndiswrapper](http://www.ubuntulinux.org/support/documentation/howto/ndiswrapper)

and all seemed to be well until i tried to connect.

After using "sudo modprobe ndiswrapper", I tried to configure the connection using the gui, but my card wasn't there for selection. According to the device manager, ubuntu can see the card as a RTL8180L 802.11b MAC.

I did a distro upgrade, so "uname -r" returns 2.6.8.1-4-386.

ndiswrapper -i Netgear/NETMA521.inf gives:
netma521 is already installed. Use -e to remove it

ndiswrapper -l gives:

Installed ndis drivers:
netma521        hardware present
windows hardware NOT present


dmesg gives:

NET: Registered protocol family 17
ndiswrapper version 0.10 loaded (preempt=yes,smp=no)
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02cc0c0(lo)
IPv6 over IPv4 tunneling driver
ACPI: Battery Slot [BAT1] (battery present)
ACPI: AC Adapter [ACAD] (on-line)
ACPI: Power Button (FF) [PWRF]
ACPI: Lid Switch [LID]
cs: IO port probe 0x0100-0x04ff: excluding 0x200-0x207 0x220-0x22f 0x330-0x337 0x388-0x38f
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: clean.
cs: IO port probe 0x0a00-0x0aff: clean.
eth0: no IPv6 routers present


iwconfig gives:

lo        no wireless extensions.
eth0      no wireless extensions.
sit0      no wireless extensions.

Can someone please shed some light on this? As you can imagine, Ubuntu is pretty useless without the net!!

---

### Post by Sham on 2005-01-24
bump

I really need this to work guys/gals :( If there is anything else you need to know then please say.

Sham

---

### Post by FX on 2005-01-24
have you tried editing the /etc/network/interfaces by hand using gedit?

sudo gedit /etc/network/interfaces

Here is what mine looks like for my card. I am using madwifi, but its the "auto wlan0" you want to add instead of 'auto ath0"

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto ath0
iface ath0 inet dhcp 
wireless_essid <what ever yours is>
wireless_mode managed

Replace my ath0 with your wlan0.

---

### Post by Sham on 2005-01-24
I did that, but using the gui in gnome. The resulting file looked just like the one you showed. When I hit apply, it tries and do something, but then gives up.

I'm not sure if my system can see the card properly. it doesn't seem to assign it to anything like eth1, wlan0 or whatever.

---

### Post by Sham on 2005-01-24
btw ifconfig gives:

eth0      Link encap:Ethernet  HWaddr 08:00:46:C0:57:73
          inet addr:129.67.56.72  Bcast:129.67.59.255  Mask:255.255.252.0
          inet6 addr: fe80::a00:46ff:fec0:5773/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:383177 errors:0 dropped:0 overruns:0 frame:0
          TX packets:225143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:460853922 (439.5 MiB)  TX bytes:20567319 (19.6 MiB)
          Interrupt:11 Base address:0x9c00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:168573 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168573 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:12232363 (11.6 MiB)  TX bytes:12232363 (11.6 MiB)

---

### Post by gt500 on 2005-01-24
Sham, maybe you oudda try this ... [img]http://www.ubuntuforums.org/images/smilies/icon_biggrin.gif[/img]
  
  [http://www.linuxant.com/driverloader]("http://www.linuxant.com/driverloader")
  
  PS: If you need the version modified for Ubuntu , contact me ;)
  
  greetz

---

