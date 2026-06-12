---
title: "Cannot use ethernet"
date: 2010-11-09
forum: Hardware
---

### Post by sgvaibhav on 2010-11-09
[Solved]
Hi,

i recently got this d-link router.
D-link DIR-600
( [http://web.dlink-me.com/index.php?navigation=products&owner=24&product=33&product_details=276](http://web.dlink-me.com/index.php?navigation=products&owner=24&product=33&product_details=276) )

I have ubuntu 9.10 in my desktop and laptop.
I can connect wirelessly/wlan using laptop
but to connect to net via LAN(wired) ..... i cannot do so. (i googled some pages.. for solution... but nothing worked)...

how do i go about
what is the basic thing that needs to be done to use the net.... when u connect the router to the pc via LAN.

---

### Post by Cheesehead on 2010-11-09
Start with the basics:

Does your system work with other ethernet routers?
Do other systems work with this router? In every jack?
Are you sure the cable is good? Does it work with other systems?

Don't assume your hardware is good. TEST IT.
Most connectivity problems are hardware problems - pinched cords, shorts or cuts in the cord, bad connectors, burned out chips, etc.

More advanced:
When you hook up your known good system to your known good router using your known good cable, what happens? Blinky lights on the ethernet jacks? Blinky lights on the router? What color lights on the jacks? Are they the lights and blinking rate you expect?

Let us know once you have ruled out hardware. Then we'll go into /var/log/syslog and dmesg and see what's happening in software.

---

### Post by sgvaibhav on 2010-11-10
i used to connect to the net using PPPOE before i got the router.
i have ubuntu 9.10 and win xp in the same desktop

internet works fine... in windows XP
it used to work perfect till i used pppoe (sudo pppoeconf).... but i am not able to connect to the net after i got the router  (or perhaps i dont know how to do that so.)
how do i go about now??
P.S..  i searched and googled for an hour... but i could not come up with a solution, so im asking here.... (i tried my best before asking here)


Or in simple words....
i use a router now... (i used PPPOE before).
net used to work properly in win xp and ubuntu  while using  PPPOE           (desktop)
it still works properly in win xp... but it does not in ubuntu.

---

### Post by Cheesehead on 2010-11-10
The router should be handling PPPoE for you (and everyone else on your network). That's one of the things they do, that makes them different from simply a switch.

Generally, you only need PPPoE on your system if you are talking directly to the modem - you are not, you have a router.

How did you set up your router? Using the included disk in XP? Or via the web interface? Or not at all yet?

Have you tried connecting normally? (without PPPoE)

---

### Post by sgvaibhav on 2010-11-10
> **Cheesehead said:**
> The router should be handling PPPoE for you (and everyone else on your network). That's one of the things they do, that makes them different from simply a switch.

Generally, you only need PPPoE on your system if you are talking directly to the modem - you are not, you have a router.

How did you set up your router? Using the included disk in XP? Or via the web interface? Or not at all yet?

Have you tried connecting normally? (without PPPoE)
i dont know how to connect normally... (without PPPOE)
i dont need PPPOE anymore because i have a router now...which does the work.

---

### Post by dogbite3000 on 2010-11-10
Hey there, im using 10.10, but i had a problem where my Ethernet stopped working.  I would plug the cable in, but it would not connect.

This is what worked for me.  Turn off your computer.  If it is a laptop, after it is powered off, take off the battery.  Unplug the charger, and unplug the Ethernet cable from your computer AND wall.

Let it sit for a minimum of 5 minuets.  Then, put battery back on, put back on charger, and power on.  once it is booted up, plug your Ethernet cable back into the wall and back into your computer.

I hope this helps you, it was the problem with my internet.

---

### Post by dineshs on 2010-11-11
Please connect your ethernet cable and post the results of
```
sudo lshw -C network
```and```
ping 4.2.2.1 -c3
```

---

### Post by sgvaibhav on 2010-11-11
:(

vaibhav@vaibhav-desktop:~$ sudo lshw -C network
[sudo] password for vaibhav: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:1f:d0:65:22:82
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:d000(size=256) memory:f5000000-f5000fff memory:80000000-8001ffff(prefetchable)



vaibhav@vaibhav-desktop:~$ ping 4.2.2.1 -c3
connect: Network is unreachable

i used the same hardware/lan port before i got router... and it worked alright.

now what :( .....

---

### Post by Cheesehead on 2010-11-11
Next step, run the command 'ifconfig' and post the result.

---

### Post by sgvaibhav on 2010-11-11
output for ifconfig just in case

vaibhav@vaibhav-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:d0:65:22:82  
          inet6 addr: fe80::21f:d0ff:fe65:2282/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:564 (564.0 B)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

---

### Post by sgvaibhav on 2010-11-11
I found it out :D

Solution

type these in root terminal

root@vaibhav-desktop:/home/vaibhav# ifconfig eth0 down
root@vaibhav-desktop[URL="http://www.linuxforums.org/forum/#"][COLOR=blue][COLOR=blue ! important][FONT=Verdana][COLOR=blue ! important][FONT=Verdana][/FONT][/COLOR][/FONT][/COLOR][/COLOR][IMG]http://konac.kontera.com/javascript/lib/imgs/grey_loader.gif[/IMG]
[/URL]:/home/vaibhav# ifconfig eth0 up
root@vaibhav-desktop:/home/vaibhav# dhclient

Thanks for supprt everyone =)

[Solved]

---

### Post by sgvaibhav on 2011-03-26
it was solved pretty long ago...
but i faced a problem since that time.

everytime i turned off my desktop; the next time i would turn it on, i always had to go root terminal and type dhclient.
then only it would work properly.


it gets very annoying now...
how can this be avoided??


however, if i connect the cable to my other computer (laptop), it automatically used to detect the connection, and say connection established.

---

### Post by sgvaibhav on 2011-03-26
Actually, i messed around with some of the laptop settings.... and i have been facing the same problem in laptop (if i connect wired using LAN)...

i am adding some screenshots, which could help understand my situation.

so what do i do, so that when i plug in the LAN cable, it automatically connects to my router.

---

