---
title: "Installer cannot connect to network; DHCP Problem or Network Card not supported?"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by searchesend on 2009-05-19
I'm trying to make an old laptop usable again with a minimal install of 8.04 but the installer can't connect to the internet to retrieve the repositories. I'm using an Edimax Ethernet PCMCIA card which works on Win XP. The laptop has 128MB RAM, 700MHz Processor and 40 GB Harddrive. My computer knowledge is poor - apologies. Any help would be very appreciated. Maybe you could recommend a suitable OS that isn't Ubuntu based and could recognise my hardware? Thanks

---

### Post by utnubuuser on 2009-05-19
Can you install without the network, then deal with the repos afterward?

---

### Post by searchesend on 2009-05-19
Because the system is so low spec'd, I was following a guide for a 'bare bones install'. I don't think this disc will let me continue without a working connection. I'm using a minimal 8.04 cd that's about 19MB and I guess it just gives you basics but needs to access the repositories to install window managers, browsers etc? The system can't run a heavy weight install with only 128MB RAM - bummer.

---

### Post by searchesend on 2009-05-19
[http://www.edimax.co.uk/en/produce_detail.php?pl1_id=2&pl2_id=9&pl3_id=30&pd_id=44#03](http://www.edimax.co.uk/en/produce_detail.php?pl1_id=2&pl2_id=9&pl3_id=30&pd_id=44#03)
This is the PC Card I'm using. When I plug it into another laptop with a full 8.04 install it just works out of the box.

---

### Post by dstew on 2009-05-19
I guess the minimal install CD you are using does not have the drivers needed to work the PCMCIA card. Maybe there is a way to drop to a command line, and install the correct driver, then try to use the net, but I don't know how to do that...

EDIT: You could try booting an Alternate Install CD, and installing a minimal command-line interface from there. Maybe then you could get the correct driver on a disk, and install it to the command-line installation, and use apt-get to get other packages that you need. See the post by snowpine in [this thread]("http://ubuntuforums.org/showthread.php?t=1137151").

---

### Post by searchesend on 2009-05-19
Thanks dstew, I've been trawling for ages but didn't think of searching minimal install. I was trying to follow this guide;
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)
I've tried using the 5.10 alternate install CD, but this got stuck on the same problem. Maybe there's support for the Edimax on more recent distributions? Regardless this is a step in the right direction - thanks.

---

### Post by searchesend on 2009-05-19
The error message I get is the following;

[!!] Configure the network
Network autoconfiguration failed
Your network is probably not using the DHCP protocol. Alternatively, the DHCP server may be slow or some network hardware is not working properly.

Could be a simple matter of adjusting the router settings? I tried to adjust it to dynamic IP addressing but it seems to only be static. Is there a way I can set the kernel to probe for my ethernet card specifically?

---

### Post by dstew on 2009-05-19
I really think the problem is the PCMCIA card. Can you get to a command line on the minimal install disk?

---

### Post by searchesend on 2009-05-19
You can enter 'boot parameters' if that helps. I've tried;
ether=0,0,eth1 cli
The problem being I don't have a clue what it means or what it does...

---

### Post by dstew on 2009-05-19
No, I'm talking about a Linux command line after the minimal CD linux kernel is booted. What you are talking about are kernel parameters. If the driver is not on the disk, you can't help the kernel to find it. I think the driver is not on the disk, so kernel parameters won't help. You will have to find some way to add the driver to the (very limited) Linux kernel after it has been booted and the system is running. If we can get a command line, we can see if PCMCIA support is present, and if not, maybe we can put it in.

---

### Post by searchesend on 2009-05-19
I've tried just now but it's getting late here. I will try again tomorrow and post if I manage it. Thank you for your help and you patience

---

### Post by searchesend on 2009-05-20
OK, when I'm booting with the minimal 8.04 cd it hangs for a while on;
35.916908 8139cp: 10/100 PCI Ethernet Driver
There's a built in Ethernet port on the laptop but it doesn't function (it doesn't show on Win Device Manager) and DELL don't provide a driver for it.
When the kernel has loaded I can press CTRL+ALT+F2 and get into 'BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)

Built-in commands include; bg break ch chdir command continue echo eval exec exit export false fg getopts hash help jobs kill let local pwd read readonly reurn set shift times trap true type ulimit umask unset wait

---

### Post by searchesend on 2009-05-20
typing lspci gave the following;
host bridge...
VGA compatible controller...
PCI bridge...
ISA bridge...
IDE interface...
USB controller...
Multimedia audio controller...
USB controller...
Cardbus bridge...
Cardbus bridge...
Ethernet controller: Realtek, RTL - 8139/8139c/8139C+ (rev10)

---

### Post by dstew on 2009-05-20
How did you try lspci? On the BusyBox line? Try **modprobe**, just to see if that function exists. Modprobe is the command line function that can be used to manage and load kernel modules (drivers). If modprobe is there, we might be able to find a driver for your PCMCIA card and load it into the kernel.

Do you know why the ethernet controller does not work? If it is a driver problem, maybe the Linux driver can operate it. Did you try it under your Linux minimal system? Another thing to think about is maybe the ethernet controller is disabled somehow in the BIOS. That might have happened when you originally installed the PCMCIA network card.

---

### Post by searchesend on 2009-05-20
I used lspci on BusyBox yeah. As for the PCI Ethernet, I have no idea why it doesn't function. I remember installing the driver from the DELL website but the Ethernet port doesn't show on the Device Manager. I looked into the BIOS before and it says 'Mini-PCI device - not installed'. 
I've been trying to modprobe but I don't understand it much. I've tried 'modprobe (filename)' whilst in the;
/lib/modules/2.../kernel/drivers/net 
...directory but it comes back with;
FATAL: Module (filename) not found. Could you help steer me in the right direction? Thanks so much for your help!

---

### Post by dstew on 2009-05-20
Try **lsmod** to list all the current modules. Do you see anything there that looks like it might be for the ethernet card, or for the PCMCIA card?

---

### Post by searchesend on 2009-05-20
pcmcia               40876  0

yenta_socket         27276  3

pcmcia-core          40596  3 pcmcia, yenta_socket,rsrc_nonstatic

8139cp               24704  0

8139too              27520  0

mii                  6400   2 8139cp,8139too

---

### Post by searchesend on 2009-05-20
Sorry if I bombard you with useless information and questions but why would the laptop have an ethernet port when you can't activate it in BIOS?
Also when I'm trying the install I can hit ALT+F4 and watch in more detail. When I try the install from the Edimax PCMCIA I can see data, e.g.
link up, 100 Mbps, full duplex, lpa0x41e1
DHCP discover on eth0 to 255
DHCP discover on eth0 to 255
DHCP discover on eth0 to 255
DHCP discover on eth0 to 255
port interval (12) {this number varies}
No DHCPOFFERS recieved
Unable to obtain lease on first try, exiting
Netdev Watchdog: eth0: transmit timed out
Eth0: Tx queue start entry 4 dirty entry

...and more

If I try the install again with the LAN connection in the built in Ethernet socket I get a similar string but the values are typically 'ffff'

---

### Post by searchesend on 2009-05-20
This has really confused me. I just tried the install on my newer laptop, with the WLAN switch off and the Edimax card in (and LAN connection). The install noticed I had multiple network interfaces;
eth0: Realtek Semiconductor Co., Ltd, RTL - 8139/8139C/8139C+
eth1: Realtek Semiconductor Co., Ltd, RTL - 8139/8139C/8139C+

The connection eth0 runs the same on both computers (results in DHCP error) but the eth1 connection works and connects to the internet?! Is this minimal install disk capable of accessing drivers on the newer PC's hard drive?

---

### Post by dstew on 2009-05-20
From your lsmod output it seems the kernel has the modules to operate the PCMCIA card. The DHCP log looks like the kernel believes that the eth0 interface is alive, and can be used, but you get no responses. This could be because the eth0 interface is mis-configured, or because the DHCP server is not responding.

If you want to keep trying on the first laptop, issue the command **ifconfig -a** to list the potential interfaces. Then we can look at the configurations.
> Is this minimal install disk capable of accessing drivers on the newer PC's hard drive?The CD has all the drivers on it for everything it can do. It ignores the software on the PC's hard drive.

---

### Post by searchesend on 2009-05-20
eth0;
Link encap:Ethernet HWaddr 00:50:FC:8E:##:##
UP BROADCAST RUNNING MULTICAST MTU:1500 METRIC:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:5 Base address:0x2400

lo;
Link encap:Local Loopback
inet
addr:###.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)


I substituted some address numbers - I don't know how this works so thought it might be safer. Out of interest, did you learn about Linux through messing around with computers in your spare time or have you done some courses or is it your profession?

---

### Post by dstew on 2009-05-20
There is the eth0 interface, it is set up, meaning there is hardware, and a driver that works the hardware. However, it has no assigned internet address, suggesting that the DHCP attempt failed, which is consistent with the messages received earlier.

You can try the DHCP directly with```
ifconfig eth0 dhcp start
```Then, you can check if it worked by ifconfig again, to list the interfaces, or```
ifconfig eth0 dhcp status
```

To see what piece of hardware has been assigned to the eth0 interface, you can look at the boot logs. This command might work:```
cat /var/log/dmesg|grep -i eth0
```You can also page through the boot messages with```
dmesg | more
```
As far as learning linux, I just do it as a hobby, no formal education. I just got a distro, installed it, and started learning. This web site helped a lot: [http://www.linux.org/](http://www.linux.org/) especially when it came to understanding the Linux distributions other than Ubuntu, and using the command line. There are some tutorials there under the Courses button that are good.

---

### Post by searchesend on 2009-05-20
I'm not sure if typing 
ifconfig eth0 dhcp start
did much. Tried the
ifconfig eth0 dhcp status
and it yeilded nothing. I changed the next to
cat /var/log/syslog|grep -i eth0
It states;
eth0: RealTek RTL8139 at 0x2400 00:50:fc:8e:7f:6e, IRQ 5
eth0: Identified 8139 chip type 'RLT-8139C'
Detected hotpluggable network interface eth0
Detected hotpluggable network interface eth0
Detected hotpluggable network interface eth0
I've started to look for busybox ways of enabling DHCP - if you reckon it's the place to start?
Do you manage to retain Linux knowledge or are you a bookmark fiend and master googler?

---

### Post by searchesend on 2009-05-20
[https://bugs.launchpad.net/ubuntu/+bug/351625](https://bugs.launchpad.net/ubuntu/+bug/351625)

What do you make of this? I tried;
dhclient -s -p
Changing port and IP numbers but it always ends up;
No DHCPOFFERS recieved.
No working leases in persistent database - sleeping

---

### Post by utnubuuser on 2009-05-20
Don't know much about networking/lan, but I don't suppose this would have anything to do with the key for the network?  Are you supposed to use a network-key at all?

And, blasphemy though it may be, have you tried a Debian *Lenny* minimal install cd?

I've had some low spec systems I couldn't get Ubuntu-alternate onto that accepted Lenny-minimal ok.

Also !#Crunchbang Linux is a Ubuntu-alternte-minimal OS that's quite good.

---

### Post by searchesend on 2009-05-21
Thanks for the Lenny recommendation - I'll look into it. I assume that Crunchbang uses the same installer and still won't work with the PCMCIA ethernet? As for the wireless key it did cross my mind but I think because there's a cable link between router and computer, there's no need for a key? The installer works the same way with a newer PC?!

---

### Post by searchesend on 2009-05-21
I still can't get this to work.
[https://bugs.launchpad.net/ubuntu/+source/netcfg/+bug/315231](https://bugs.launchpad.net/ubuntu/+source/netcfg/+bug/315231)
I don't know if this bug applies - could it be my slow system needs more time to establish the connection?
Would it be useful for me to type out the 
cat /var/log/syslog|grep -i eth0
for the working and non working systems?

---

### Post by searchesend on 2009-05-22
Lost my patience with it. I'll try and get some more RAM and try a different install. Thank you for trying to help - much appreciated.

---

### Post by utnubuuser on 2009-05-23
Sorry to hear.  Trying something different might work.  I've had different machines accept different distros or releases of the same distro while refusing newer/older releases - for no apparent reason.  Good Luck

---

