---
title: "New Ethernet card doesn't get IP address via DHCP"
date: 2006-12-01
forum: Hardware &amp; Laptops
---

### Post by weresheep on 2006-12-01
Hello,

Mods: I'm not sure if this belongs in the hardware or netowrk forum becuase I am not sure if the hardware is working or not. If I chose wrong please move the thread. Thanks.

I had a weird problem last night when I tried to replace a PCI network card in one of my machines. I'll explain what I did so this may get long, sorry.

I have two machines running Dapper. The first is my main desktop and the the other is a backup machine with a Dapper server installation. Both work well but the server machine has had a niggling wee problem that I wanted to fix.

The server machine has its Kernel ring buffer constantly filled with "PCI Error 0x800000" messages and so any time I run dmesg thats all I see. Even when rebooting the machine, all the startup messages are replaced before I can see them. I searched google for the PCI error message and found that it may be the network card. The server machine has a Netgear FA311 PCI 10/100Base-TX Ethernet card which otherwise works fine, but I want rid of these messages and to free the CPU from having to constantly write to the log buffer (seems to be the reason why dd and syslogd are constantly consuming CPU time).

I bought a new Ethernet card with a Realtek chip and swapped the cards over. I then powered on the server and tried to ssh in. After failing to log in via ssh I plugged in a keyboard and monitor and logged in. I found that the new Ethernet card wasn't getting an IP address. Running "ip addr" showed a listing for "eth1" but no "eth0". In the eth1 listing there was an IPv6 address but no IPv4 stuff was listed at all. I ran dmesg and got all the startup Kernel messages etc. There was mention of the system finding the PCI card and Realtek chipset but no error messages. I looked in /etc/network/interfaces and found that there was no reference to eth1, only eth0. I tried running ifdown and ifup but no change.

Now, here comes the really weird part. I plugged the monitor etc. back into my desktop and powered it on (was going to do some googling) but now it was reporting the same problem. Running "ip addr" showed that it wasn't getting an IP address either. It was working a few minutes earlier and I hadn't touched the desktop machine at all. I eventually managed to get my iBook to boot up without crashing (it has a broken monitor / motherboard connection and any slight movements corrupt the screen/  crash the computer) and found that it was configured by DHCP no problem.

I tried everything I could think of but could not get my desktop machine to get an IP address. Even after manually assigning it a 192.168.0.* address it failed to ping the router with a "host unreachable" error, and yet the laptop was working fine. All this time the server was powered off. I eventually gave up and took the new network card out of the server and replaced the old one and powered it on. It worked with no problem. I then powered on my desktop and it also now worked. I am at a loss to explain this.

If you've managed to read this far then I have some questions for you...

1) When replaced a network card with another (supported) network card in Ubuntu Dapper do you need to install new drivers, load them etc? i.e. is this a problem with changing a network card. I mean, if I installed the OS with that new card in from the start would I get any different behaviour?

2) What could have happened to stop the desktop machine from working?

3) What else could I have tried, is there a way to see if the system was running a driver for the new network card as opposed to just detecting its presence?

Big thanks for any help becuase I am really stumpted.

-weresheep

---

### Post by lloyd_b on 2006-12-01
1.  If you install a supported network card, with a stock Ubuntu install it should automatically load the driver for you.  If the kernel detects the card (which dmesg seems to indicate that it does) you would normally be good to go.  However, I have seen several threads involving problems with the Realtek drivers (which sound similar to what you've encountered).

2.  I have no clue on that one....

3.  Run "sudo lshw"  You'll see an entry simlilar to this for the Ethernet card (this is for a different type of card!):

```
 *-network
             description: Ethernet interface
             product: W89C940
             vendor: Winbond Electronics Corp
             physical id: c
             bus info: pci@00:0c.0
             logical name: eth0
             version: 00
             serial: 00:20:78:12:fd:dc
             width: 32 bits
             clock: 33MHz
             capabilities: ethernet physical
             configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 ip=192.168.0.65 multicast=yes
             resources: ioport:da00-da1f irq:9
```

Note on the "configuration" line it lists "driver" - if Linux isn't loading a driver for this, then you won't see this.....

Before you use that Realtek card again, I would suggest doing a search for Realtek in the forums, and read through what others have had to do to get them to work properly.

Lloyd B.

---

### Post by weresheep on 2006-12-01
Hello, Lloyd

Thanks for the great reply.

1) Your answer was what I thought would happen but I didn't know for sure thats what should happen. Thanks for clearing that up.

2) Yeah, I suspect I may never know what caused that weirdness :-k 

3) Ah, I didn't know about lshw, cool. A problem with the driver would explain things. I'll go and find the threads about Realtek you mentioned and see what others have done, though I may just buy another brand of card if the driver isn't reliable and put this Realtek one down to experience.

Thanks again for your help.

-weresheep

---

