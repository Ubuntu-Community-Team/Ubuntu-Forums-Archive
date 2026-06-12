---
title: "Wake-on-Lan help"
date: 2013-01-06
forum: Hardware
---

### Post by zkvvoob on 2013-01-06
Hi guys,

I've been trying to configure WOL on my 12.04 Ubuntu server. Here's what I've already done:
- installed ethtool
- added script to run on boot (as per this guide: [https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan) )
- checked that wake is g on eth0
- installed acpitool

However, the acpitool in questions returns no results when run with the -W parameter:

   Device       S-state   Status   Sysfs node
  ---------------------------------------

I am almost completely new to the Ubuntu universe and I need some guidance what to check next and how to actually get WOL successfully working.

Please help me!

P.S. Just found that my NIC is Broadcom Corporation NetXtreme B CM5704 Gigabit Ethernet. Don't know if this helps.

---

### Post by ahallubuntu on 2013-01-06
There isn't much to setup.  The ethtool is used to find the capabilities of your ethernet card, but once you find them out you don't need it anymore (and it's very likely your card is ready to go - perhaps enable it in your BIOS Setup).  I use the acpitool to put it to sleep.

To wake up a sleeping machine, I use the "wakeonlan" command.  On a machine that is already awake (the one from which you will wake up your sleeping machine), install the command:

```
sudo apt-get install wakeonlan
```

Then, to wake up the sleeping machine, on the awake machine issue the command:

```
wakeonlan aa:bb:cc:dd:ee:ff
```

where "aa:bb:cc:dd:ee:ff" is the MAC address (hardware address) of the network card you are trying to wake up.  You can find this with the "ifconfig" command ("HWaddr") on the (to be) sleeping machine.

You could also add the broadcast address for the network, if needed:

```
wakeonlan -i 192.168.1.255 aa:bb:cc:dd:ee:ff
```

If your network subnet is 192.168.1.1/24 (a typical network).

If you don't like command line tools, try the gWakeOnLan tool.

I have OpenVPN installed on my home router which is running DD-WRT firmware.  So if I'm out in the world and want to wake up my sleeping machine at home, I first connect to my VPN, then issue the wakeonlan command.  DD-WRT has WOL built-in too, so I don't even have to use the command - after connecting to my VPN, I can go to the DD-WRT admin page on my router and use WOL right on the page to wake up the sleeping machine.

[https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan)

---

### Post by zkvvoob on 2013-01-06
Hi, ahallubuntu!

Thanks for the reply and for the extensive explanation. From what I gather, the reason for my issues could be the fact that I am not putting the server to sleep properly. All my other machines are running Windows and even when they are shut down, WOL would bring them back on. So, based on this assumption, I used 

```
shutdown -P now
```

to power off the server.

Was I wrong? Is there a different command I should be using?

---

### Post by ahallubuntu on 2013-01-06
That ought to work, yes.  I use "acpitool -s" to put my machine to sleep instead of shutdown; standby works reliably for me and consumes about as much power as "shutdown" with the power plugged in, anyway.  

Have you checked your BIOS Setup?  There should be a power management section.  If this is a PCI card, you have to enable wake-up from PCI cards or however they phrase it...

---

