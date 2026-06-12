---
title: "Why should I use Ubuntu?"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by m5a5l3m on 2009-05-08
I installed Ubuntu for the first time thinking it will help me make my computer more responsive than Win XP.

However, after installation, I'm facing issue with networking.. I'm totally blocked and cannot think of anything to fix it.

I'm totally relying on the userbase here... if I still cannot fix it, I will have to move back to XP :-(

My setup is this:
Linksys router -> DLink Gigabit switch -> Old Dell PC (350 MHz, P2)

I tried to give it a static IP as well, that didn't work.

Please help me.

---

### Post by Hendronicus on 2009-05-08
Go back to using DHCP and reboot, if that doesn't work, reboot the router, that might get you a new lease. I've seen this kind of thing before, sometimes you don't get a new IP addy without re-starting the router, and without one, DHCP doesn't work.

---

### Post by m5a5l3m on 2009-05-08
would reboot help for a static IP as well?

---

### Post by Hendronicus on 2009-05-08
Rebooting the router might, but rebooting the PC probably won't. What static IP do you have it set to? If you're using a router it probably should not be 192.168.0.1

---

### Post by m5a5l3m on 2009-05-08
I'm using 192.168.9.12

---

### Post by Wiebelhaus on 2009-05-08
I don't understand if you have obtained an IP you have connectivity.

---

### Post by Hendronicus on 2009-05-08
OK, just a question - Why the "9"? It doesn't really matter, though. :)  Did you try to reboot the router?

---

### Post by Hendronicus on 2009-05-08
sx66gns, I think he'd like to use a static IP. I understand, it's what I do.

---

### Post by Hendronicus on 2009-05-08
I just got my CD of 9.04 today. I installed it a little while ago. It looks pretty good. I've got four OSes on my machine, not counting the ones I run under emulation. I know my profile says that I use Gutsy, and I do, because my install of it is very mature. My profile doesn't tell you that I've been using Linux since 1994 and that Slackware used to be my favorite distro. I use XP for games, Windows 98 for DOS apps, and Linux for everything else. Jaunty might become my favorite; who knows?

---

### Post by Wiebelhaus on 2009-05-08
> **Hendronicus said:**
> sx66gns, I think he'd like to use a static IP. I understand, it's what I do.

Ok , I missed that part (Or didn't read throughly) I thought he was using DHCP.

---

### Post by m5a5l3m on 2009-05-08
Ok. here is the update..
I tried to reboot the router etc... still no luck..

I tried to edit the interfaces file and I noticed that the device logical name was lo where as the output of the following command told me the name is "pan0"

sudo lshw -C network
The output of the above command also told me that the network is disabled..

So then I edited the file with the correct the logical name and set the static IP etc.. and then restarted networking. I got the following error:

SIOCADDRT:     No such process
Failed to bring up pan0.

---

### Post by issih on 2009-05-08
I am willing to bet that what you have done to that file is utterly wrong.

lo is the loopback interface, it should be there and it should not be messed with.

pan0 nearly always refers to a personal area network interface implemented via bluetooth, not a hardwire networking one.

you are almost certainly looking for eth0.

I'd put that file back as you found it and use the network manager until you know what you are doing to avoid messing things up.

As for your initial problem, what version of ubuntu are you using?

What is the ip of your router and what is the networks subnet mask?

---

### Post by m5a5l3m on 2009-05-08
I'm using Xubuntu 9.04 (jaunty..)

I was following instructions on this website:
[http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/](http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/)

If I use eth0 in that file, I get an error after I restart networking that there is no such device... even lshw command confirms that the name is pan0.

I used network manager and it didn't do a thing... so I switched to the file

My gateway IP: 192.168.9.1

> **issih said:**
> I am willing to bet that what you have done to that file is utterly wrong.

lo is the loopback interface, it should be there and it should not be messed with.

pan0 nearly always refers to a personal area network interface implemented via bluetooth, not a hardwire networking one.

you are almost certainly looking for eth0.

I'd put that file back as you found it and use the network manager until you know what you are doing to avoid messing things up.

As for your initial problem, what version of ubuntu are you using?

What is the ip of your router and what is the networks subnet mask?

---

### Post by issih on 2009-05-08
You need to give us more information, if you are certain you have exhasuted the possibilities of using network manager then you ened to post the output of:

ifconfig -a

sudo lshw -C network

and also post the contents of your /etc/network/interfaces file.

Hope that helps

---

### Post by albinootje on 2009-05-08
> **m5a5l3m said:**
> would reboot help for a static IP as well?

You're most likely much better off using DHCP if your router needs a restart.

And Ubuntu on a Pentium II is unlikely to give you better performance by default than a well installed MS-XP. Wherever I work with Linux on the desktop I want a Pentium III with at least 512 Mb of RAM as a minimum, and even then Ubuntu is a bit sluggish.

Installing the Xubuntu desktop can give you a bit better performance, but applications like OpenOffice, Firefox and Thunderbird will be heavy for it, you might want to try AbiWord (YMMV!), Claws-mail, and Galeon web browser.

---

### Post by albinootje on 2009-05-08
> **m5a5l3m said:**
>  Old Dell PC (350 MHz, P2)


Can you also post the output of this :
```

lspci
dmesg|tail

```

---

### Post by m5a5l3m on 2009-05-08
lspci:
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
00:07.0 ISA bridge: Intel Corporation  82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation  82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation  82371AB/EB/MB PIIX4 USB (rev 02)
00:07.3 Bridge: Intel Corporation  82371AB/EB/MB PIIX4 ACPI (rev 02) 
<<< I get a warning about ACPI during boot: BIOS (1998 )  fails cutoff (2000) ACPI=force required for ACPI >>>>
00:0e.0 Multimedia video controller: Zoran Corporation ZR36120 (rev 03)
00:0e.0 Multimedia audiocontroller: Aureal Semiconductor Vortex 1 (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)

dmesg:
spurious 8259A interrupt: IRQ7
Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Bluetooth: BNEP filters: protocol multicast
Bridge firewalling registered
ppdev: user-space parallel port driver
pan0: no IPv6 routers present ---> this is the logical name of my card (from lshw command)





> **albinootje said:**
> Can you also post the output of this :
```

lspci
dmesg|tail

```

---

### Post by m5a5l3m on 2009-05-08
Here is the info you requested...
[B]
ifconfig -a:[/B]
lo
[INDENT]Link encap:local loopback
inet addr:127.0.01 Mask 255.0.0.0
inte6 addr:  :: 1/128 Scope:Host
UP LOOPBACK RUNNING MTU: 16436 Metric:1
RX packets: 18 errors:0 dropped:0 overruns:0 frame:0
TX packets: 18 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:1350  Tx bytes: 1350
[/INDENT]
pan0
[INDENT]Link encap:Ethernet HWaddr 96:08:52:96:b0:bf
inet6 addr: fe80: :9408:52ff:fe96:b0bf/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets: 0 errors:0 dropped:0 overruns:0 frame:0
TX packets: 59errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 Tx bytes: 10691

[/INDENT]pan0:avahi Link ecap:Ethernet HWaddr 96:08:52:96:b0:bf
[INDENT] inet addr: 169.254.8.234 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
[/INDENT] 
**sudo lshw -C network**
*-network
[INDENT]description: Ethernet interface
physical id: 1
logical name: pan0
serial: 96:08:52:96:b0:bf
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

[/INDENT]**/etc/network/interfaces**
[INDENT]auto lo
iface lo inet loopback
iface pan0 inet static
address 192.168.9.11
netmask 255.255.255.0
gateway 192.168.9.1
[/INDENT]

> **issih said:**
> You need to give us more information, if you are certain you have exhasuted the possibilities of using network manager then you ened to post the output of:

ifconfig -a

sudo lshw -C network

and also post the contents of your /etc/network/interfaces file.

Hope that helps

---

### Post by albinootje on 2009-05-08
> **m5a5l3m said:**
> 
<<< I get a warning about ACPI during boot: BIOS (1998 )  fails cutoff (2000) ACPI=force required for ACPI >>>>

Thanks for the output
You're missing eth0 or eth1 etc...weird. (And, for the record, pan0 should be irrelevant, as someone mentioned earlier)

Can you boot with "acpi=off" or "acpi=force" ?
Here's more about alternative boot parameters :
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

The parameters "noapic nolapic" can sometimes do wonders, please try it too.

---

