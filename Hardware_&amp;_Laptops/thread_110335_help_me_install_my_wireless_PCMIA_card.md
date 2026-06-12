---
title: "help me install my wireless PCMIA card"
date: 2005-12-30
forum: Hardware &amp; Laptops
---

### Post by taseal on 2005-12-30
I cant install it :(

this is for my parent's laptop... its a microsoft MN-520 

i've looked at this

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

and dont really understand how i'm supposed to install a driver or such... 

if you can guide me through, i'd really appreciate it, thx!

ps. i dont know what ndiswrapper is eiter...

---

### Post by Lambert on 2005-12-30
Put the install cd back in the pc and do this from a terminal.

```
sudo apt-get install linux-wlan-ng
```

Now plug the card in.

Go to system>administration>networking if you see the wireless device in the list try to configure and activate.

You may also want to reboot so the card allocates the driver if it doesn't when plugged in.

If not then post output of these commands here.

```
sudo lshw -C network
```

```
lspci -v | grep Ethernet
```

---

### Post by taseal on 2005-12-31
ok trying

---

### Post by taseal on 2005-12-31
ok, it was no go, i will post the stuff now

---

### Post by taseal on 2005-12-31
```

  *-network
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 78
       serial: 00:08:74:97:36:64
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 1 00bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=3c59x driverversio n=LK1.1.19 duplex=full ip=192.168.2.2 link=yes multicast=yes port=MII speed=100M B/s
       resources: ioport:ec80-ecff iomemory:f8fffc00-f8fffc7f irq:11
  *-network
       description: Wireless Notebook Adapter MN-520
       vendor: Microsoft
       physical id: 0
       version: 1.0.3
       slot: Socket 0

```

and

```

0000:02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
        Subsystem: Dell 3C920 Integrated Fast Ethernet Controller [Latitude C640]

```

hope that helps :(

---

### Post by taseal on 2005-12-31
well i'm trying to find the pci businfo on it, but I cant get it on the wireless card... I did the lspci command but the wireless card wont show up on there


ya know, trying to find the thing that says like 104c:8400 and stuff

---

### Post by taseal on 2005-12-31
how come linux-wlan doesnt work? I dont get it... they show this card as supporting

[http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)

---

### Post by taseal on 2005-12-31
this is pretty much the same exact problem everyone else is having... seems like people just give up and go back to xp once they find out 520 is not supported with ubuntu, as this will be the case with me I guess...

[http://www.ubuntuforums.org/showthread.php?t=96360&highlight=mn-520](http://www.ubuntuforums.org/showthread.php?t=96360&highlight=mn-520)

we cant use ndiswrapper because we cant find a inf/sys file for mn-520 and wlan-ng does not work...

we cant find PCI id for this card either...

---

### Post by Lambert on 2005-12-31
Not sure if this will work but you can try this.

open up this file

```
sudo gedit /etc/config.opts
```

At the bottom of the page add this.

```

product info: "Microsoft", "Wireless Notebook Adapter MN-520", "", "1.0.3"
manfid: 0x02d2, 0x0001
function: 6 (network)
bind "linux-wlan-ng"

```

Now reboot the pc to see if you get a bus location. And rerun the lshw command to see if the driver binds to the device.

---

### Post by taseal on 2005-12-31
[QUOTE=Lambert]Not sure if this will work but you can try this.

open up this file

```
sudo gedit /etc/config.opts
```

At the bottom of the page add this.

```

product info: "Microsoft", "Wireless Notebook Adapter MN-520", "", "1.0.3"
manfid: 0x02d2, 0x0001
function: 6 (network)
bind "linux-wlan-ng"

```


Now reboot the pc to see if you get a bus location. And rerun the lshw command to see if the driver binds to the device.[/QUOTE]

I dont have anything in that file? I

---

### Post by Lambert on 2005-12-31
My bad wrong file

```
sudo gedit /etc/pcmcia/config.opts
```

---

### Post by taseal on 2005-12-31
still nogo :(

any other ideas to get a PCI ID?

did I need a # or anything before I pasted that stuff though?

---

### Post by Lambert on 2005-12-31
I'm from the new computer age where all I've ever dealt with has been  PnP. I've seen a few posts here about adding devices but never that much detail there.

Two things you may want to research are the commands MAKEDEV and mknod.

Hopefully somebody else who knows more then I will see this thread.

---

