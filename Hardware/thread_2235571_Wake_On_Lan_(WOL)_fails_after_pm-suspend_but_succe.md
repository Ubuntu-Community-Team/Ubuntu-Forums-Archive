---
title: "Wake On Lan (WOL) fails after pm-suspend but succeeds after shutdown"
date: 2014-07-21
forum: Hardware
---

### Post by bufordsf on 2014-07-21
Hello! I've a old laptop teaching me how to make a server with Ubuntu server 14.04. Some years ago, updates allowed me to suspend and resume, so exciting. Hoping WOL can work out of suspend, too. I've followed a few threads, and there seem a few methods to set the network interface card (NIC) to enable WOL. Similarly there were a few approaches to allow this waking in acpi and pm-utils. I wonder if what I've tried is obsolete, or what more I need to learn in order to continue debugging. Anyhow, here is what I've observed and tried.

Expected behavior:
```
server$ sudo pm-suspend
# server suspends and ssh connection waits
# Now send the WOL packet to broadcast on local network where the server lives
client$ awake <server-mac-addr>
# (you can 'pip install awake', or 'sudo apt-get install etherwake', or wakeonlan, etc)
# server resumes and ssh connection resumes
```

Actual behavior:
[LIST]
[*]After pm-suspend, awake command does not resume the server (power meters indicates no activity, still in suspend).
[*]If instead of pm-suspend, we do a soft shutdown by (a) pressing power button, (b) 'sudo shutdown -h now', or (c) 'sudo shutdown -P now', then after 'awake', server resumes (but it dropped connections on power down).
[*]If we do a hard shutdown by (a) holding power button 5 secs, then power consumption is down to battery charge only and WOL does not work, as expected.
[/LIST]

So I ask, since WOL worked after shutdown, can I configure something (eg. acpi, pm-utils) to make WOL work after suspend?

**More background on setup steps.**

[LIST=1]
[*] BIOS: Found the Wake-On-Lan option and enable. There is no wake-on-pme or wake-on-pci, otherwise enable it, too.
[*] ```
server$ ifconfig
``` tells me I have an interface eth0, and gives me the MAC address.
[*] ```
server$ sudo ethtool eth0
	...
	Port: MII
	PHYAD: 32
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: d                  **# we want to change this to g**
server$ sudo ethtool -s eth0 wol g  # this will last until next resume

```
[*] For permanent change, make the ethtool command happend automatically. Some people did it in /etc/network/interfaces, some people in /etc/rc.local, and some in /etc/init.d. I chose the first place:
```
server$ cat /etc/network/interfaces
...
# The primary network interface
auto eth0
iface eth0 inet dhcp
        **post-up sudo /sbin/ethtool -s $IFACE wol g**
        **post-down sudo /sbin/ethtool -s $IFACE wol g**

```
[*] Try it out. (above "expected behavior", but server doesn't resume)
[*] Now start debugging power settings.
```
server$ cat /sys/power/state
freeze mem disk # same as another server where WOL works correctly
server$ cat /var/low/pm*.log
# nothing obvious about WOL or network
server$ sudo lshw
...
        *-network:0
             description: Ethernet interface
             product: RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
             vendor: Realtek Semiconductor Co., Ltd.
             physical id: 11
             [B]bus info: pci@0000:00:11.0
             logical name: eth0[/B]
             version: 10
             serial: ...
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.5 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
             resources: irq:11 ioport:1800(size=256) memory:d8014000-d80140ff
server$ lspci
...
**00:11.0** Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 10)

```
Some people expected to find that eth0 controller's address (00:11.0) in the following list of devices that can wake us:
```
server$ cat /proc/acpi/wakeup 
Device	S-state	  Status   Sysfs node
PCI0	  S4	*disabled  no-bus:pci0000:00
UAR1	  S3	*disabled  pnp:00:07
LID	  S4	*enabled 

```
If it were listed, they did ```
sudo sh -c 'echo *devname* > /proc/acpi/wakeup'
``` where *devname* is from the first column. But mine isn't listed there.
[*] Look in /sys. Some people manually found the pci device by address, then realized there was a nice symlink.
```
server$ cat /sys/class/net/eth0/device/power/wakeup
disabled
server$ sudo sh -c 'echo enabled > /sys/class/net/eth0/device/power/wakeup'
```
To make permanent, add this (skip the sudo sh -c) in /etc/rc.local before 'exit 0'. Anyhow, still no change in behavior for me.
[*] Look at /etc/init.d/halt. Some people felt this script would shutdown the network device because of the lines
```
NETDOWN=yes
...
        # Make it possible to not shut down network interfaces,
        # needed to use wake-on-lan
        netdown="-i"
        if [ "$NETDOWN" = "no" ]; then
                netdown=""
        fi

        log_action_msg "Will now halt"
        halt -d -f $netdown $poweroff $hddown

```
However, the same lines show on another computer where WOL works. Changing first line to NETDOWN=no does not change behavior of the server.
[/LIST]

So I've run out of leads ... is there any suggestion?

Some of the threads I've looked at:
[https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan)
[https://wiki.ubuntu.com/UnderstandingSuspend](https://wiki.ubuntu.com/UnderstandingSuspend)
[http://ubuntuforums.org/showthread.php?t=1798350](http://ubuntuforums.org/showthread.php?t=1798350)
[http://ubuntuforums.org/showthread.php?t=814939&page=4](http://ubuntuforums.org/showthread.php?t=814939&page=4)
[http://ubuntuforums.org/showthread.php?t=814939&page=7](http://ubuntuforums.org/showthread.php?t=814939&page=7)
[https://calomel.org/wakeonlan.html](https://calomel.org/wakeonlan.html)
[http://www.averyjparker.com/ubuntu-linux/](http://www.averyjparker.com/ubuntu-linux/)

---

### Post by tgalati4 on 2014-07-21
Install *acpitool* and post the output of:

```
acpitool -w
```

tgalati4@Mint14-Extensa ~/Desktop $ acpitool -w
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. LID0	  S3	*enabled   
  2. SLPB	  S3	*enabled   
  3. HDEF	  S3	*disabled  pci:0000:00:1b.0
  4. PXSX	  **S5	*enabled   pci:0000:02:00.0**
  5. USB1	  S3	*enabled   pci:0000:00:1d.0
  6. USB2	  S3	*enabled   pci:0000:00:1d.1
  7. USB3	  S3	*enabled   pci:0000:00:1d.2
  8. EHC1	  S3	*enabled   pci:0000:00:1d.7
tgalati4@Mint14-Extensa ~/Desktop $ lspci | grep Ethernet
**02:00.0** Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)

The bus that powers the network card (2:00.0 in this case) must be enabled in the correct sleep state (S5, Deep Sleep in this case).  "Enabled" means that power is kept on that device during sleep so it can act on the WOL packets.  The way you can tell is you will get flashing lights on the network port on both the laptop and on the router.  No flashy no wakey.

---

### Post by bufordsf on 2014-07-22
```
# looks like another way to see /proc/acpi/wakeup
server$ acpitool -w
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. PCI0	  S4	*disabled  no-bus:pci0000:00
  2. UAR1	  S3	*disabled  pnp:00:07
  3. LID	  S4	*enabled 
# make a change to the only PCI device listed. But my ethernet is not here.
server$ acpitool -W 1
server$ acpitool -w
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. PCI0	  S4	*enabled   no-bus:pci0000:00
  2. UAR1	  S3	*disabled  pnp:00:07
  3. LID	  S4	*enabled 

```

Still cannot wake-on-lan. Is there some way to make more devices show up in ACPI here?

---

### Post by bufordsf on 2014-07-22
Does anyone know more about ACPI or what is happening here? What code generates the /proc/acpi/wakeup list of devices? Why is the NIC powered up after soft shutdown? Can't I do the same after suspend?

---

### Post by tgalati4 on 2014-07-23
Each manufacturer implements ACPI differently.  So when a computer goes to sleep, the BIOS (ACPI subsection) controls what remains powered.  Some laptops allow you to leave USB ports with power--convenient for charging your phone through USB when the laptop lid is closed.  Others don't or only have one port with power.

If you want to play with a server, find some old server hardware--there's a lot floating around.  I have WoL working on a few Dell PowerEdge servers.  Trying to get WoL working on hardware that doesn't support it will be problematic.  You have done everything that I can think of.

Just because your network card/chip support WoL does not mean the motherboard/BIOS supports it.  Both parts need to support it for WoL to work.  Find another computer--preferably not a laptop and you may have better luck with WoL.  Find another use for the laptop.

---

### Post by bufordsf on 2014-07-25
Yep, I have unrealistic expectations often. Thanks for the realism and help. The advantage that drew me to re-using the laptop is its low power consumption since I don't have much of a load on it.

---

