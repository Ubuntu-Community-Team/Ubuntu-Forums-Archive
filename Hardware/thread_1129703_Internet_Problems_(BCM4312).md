---
title: "Internet Problems (BCM4312)"
date: 2009-04-19
forum: Hardware
---

### Post by Musturd on 2009-04-19
I have Ubuntu 8.10, and a Broadcom Corporation BCM4312 802.11a/b/g wireless card. I have a Dell XPS M1530.
I went to System -> Administration -> Hardware Drivers, activated the Broadcom STA Wireless Driver, and restarted the computer.

BUT, when I click the network icon in the top-right corner the only things listed are:
Wired Network (greyed)
Auto eth0 (greyed)
VPN connections ->

My wireless network is working (I am accessing the net with a different laptop)

Can anyone help me?

---

### Post by jack_spratt on 2009-04-19
I have a problem with same chip on Dell inspiron 1545.

Chip info on my machine:

                description: Wireless interface                                                                                                                         
                product: BCM4312 802.11b/g                                                                                                                              
                vendor: Broadcom Corporation                                                                                                                            
                physical id: 0                                                                                                                                          
                bus info: pci@0000:0c:00.0                                                                                                                              
                logical name: eth1                                                                                                                                      
                version: 01                                                                                                                                             
                serial: 00:23:4e:a2:37:6e                                                                                                                               
                width: 64 bits                                                                                                                                          
                clock: 33MHz                                                                                                                                            
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless                                                                          
                configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg    


0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

Neither the official nor the free driver works for me. 

Jockey tries to use proprietary driver but always stalls or ignores the request - it never works.

I'm about to try using an ndiswrapper driver instead.

I'll let you know how I get on.

I'm using kubuntu 8.10 64bit.

---

### Post by Musturd on 2009-04-19
OK, please keep me posted.

---

