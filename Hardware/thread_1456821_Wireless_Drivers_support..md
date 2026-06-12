---
title: "Wireless Drivers support."
date: 2010-04-17
forum: Hardware
---

### Post by The Thunder Chimp on 2010-04-17
I have asked this question on Debian Forums without any replies, and this is why I come here. I recently installed Debian on my laptop, and I am having trouble finding wireless drivers. Anyone got any clue where I could find them? Thanks.

The computer's specs are:

Sony Vaio CS-390J.
Debian 5.04 Lenny
4GB RAM
100 GB Partition for Debian

Any suggestions? Thanks!

---

### Post by Yellow Pasque on 2010-04-17
The output of the following command would be helpful (so we know what wireless chipset we're working with).
```
sudo lshw -C network
```

---

### Post by The Thunder Chimp on 2010-04-19
Allright, I'll do that as soon as soon as I'm home tonight. By the way, if my disk died right now, I'd switch to another school computer... :D
 
Thanks, I'll get back to you.

---

### Post by 1337_snic on 2010-04-19
I cant get my wireless card to even install. Is debian a little more supportive of wireless networking. I hear that kubuntu/ubuntu dont really like the wireless world and try to stick to hardwired. Or is it the other way around?

---

### Post by The Thunder Chimp on 2010-04-19
> **Temüjin said:**
> The output of the following command would be helpful (so we know what wireless chipset we're working with).
```
sudo lshw -C network
```


Alright, so the output of the command gives me (on Ubuntu, same computer):

```

 sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:ba:78:b9:80
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=192.168.2.15 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:d5700000-d5703fff ioport:4000(size=256)
  *-network DISABLED
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 00
       serial: 00:22:fb:95:7d:ea
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:d4600000-d4601fff

```> **1337_snic said:**
> I cant get my wireless card to even install. Is  debian a little more supportive of wireless networking. I hear that  kubuntu/ubuntu don't really like the wireless world and try to stick to  hardwired. Or is it the other way around?

It works for me on Ubuntu and Windows by the way, I just have trouble with my Debian partition.

---

### Post by grege on 2010-04-19
Debian do not load firmware by default. Using an Ethernet connection install "firmware-linux" - if you have non-free and contrib repositories active this dummy package will install both the free and non-free firmware files needed by lots of hardware.

Then restart and see if you hardware is now found.

The firmware files from /lib/firmware in you Ubuntu will also work with Debian if you know how to manually copy them across.

---

### Post by The Thunder Chimp on 2010-04-19
> **grege said:**
> Debian do not load firmware by default. Using an Ethernet connection install "firmware-linux" - if you have non-free and contrib repositories active this dummy package will install both the free and non-free firmware files needed by lots of hardware.

Then restart and see if you hardware is now found.

The firmware files from /lib/firmware in you Ubuntu will also work with Debian if you know how to manually copy them across.


Yeah, I'll try doing that as soon as I have the chance. By the way, do you have good repositories for Debian? I can't find any valuable ones. Additionally, in Ubuntu, you can turn of clicks with touchpad. This is very annoying because it always clicks at most random moments while typing and causes you to start typing at a random place. Anyway of doing this under Debian? Thanks for any possible help!

---

### Post by grege on 2010-04-20
Perhaps those questions are best asked in the Debian forums. The touchpad thing is annoying and I cannot say that I have yet got a satisfactory answer. I even tried re-mapping the pad to turn off the bottom third. Synaptics have released a closed source driver, but only to OEMs. I await it's appearance in Dell support - hopefully. Remember 99% of Ubuntu is Debian, you just have to work a bit harder to install and configure stuff. I don't have Debian on my notebook at the moment, but the same tool to control the pad is probably available, use synaptic (the program) and search on "synaptic" and install what is missing.

For Debian all I have ever needed is main non-free contrib, just edit /etc/apt/sources.list and add "non-free contrib" after each mention of main. Then add this one

[http://debian-multimedia.org/](http://debian-multimedia.org/)  if you need extra multimedia stuff or just grab the packages you need from there and install them manually.

cheers

---

### Post by grege on 2010-04-20
Further to the touchpad issue I am currently using a program called touchfreeze - that disables the pad when you are typing and re-enables when you stop. The delay is adjustable from hundredths of a second up to two seconds (for two fingered typists).

It is also available in Debian.

---

