---
title: "No WiFi on Lenovo x121e AMD"
date: 2012-08-02
forum: Hardware
---

### Post by Ddamia on 2012-08-02
I've just bought a shiny new (well, matte new) Lenovo x121e without an  operating system, because I just wanted to stick Ubuntu on it, like I  have on all the other computers in the house. After a very smooth Lucid  install (I just happen to like Lucid and want to hold on to it), however,  unfortunately I get the "no network devices available" in the network  manager. 

$ sudo lshw -C network
gives me:
```

*-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:f0200000-f0203fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:f0100000-f013ffff ioport:2000(size=128 )
```I have followed [wep940's  instructions]("http://ubuntuforums.org/showpost.php?p=10670085&postcount=10") religiously from this [thread]("http://ubuntuforums.org/showthread.php?t=1727542"), to install Ndiswrapper and drivers, but nothing doing. 

Wireless Network Drivers manager shows hardware as present. But,

iwconfig gives me:
```
lo        no wireless extensions.

pan0      no wireless extensions.
```What I should be seeing somewhere is a Realtek 802.11b/g/n WiFi Adapter... Where is it?

Any help would be massively appreciated! I've been doing battle with this now for two days.


                                                                                                   [IMG]http://ubuntuforums.org/images/rebrand/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/rebrand/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=12145809")                                                                                    [[IMG]http://ubuntuforums.org/images/rebrand/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=12145809")

---

### Post by czgirb on 2012-08-02
This is only accordance to my experienced with **Lucid + CompaqCQ40-328TU**
And this is only **IF** I do not forget, OK?
Correct me if I'm wrong.

When I installed **Lucid** on my **CQ40** it has **no WiFi**.
So, I plugged the lappie to non-WiFi connection and run a **Hardware Support**.
And installed the **WiFi** ... after it was installed, unplugged the connection and restart the lappie ... and it's there.

---

### Post by Ddamia on 2012-08-02
It doesn't see **any** network connection. I tried hooking it on to the router directly. Nothing.

---

