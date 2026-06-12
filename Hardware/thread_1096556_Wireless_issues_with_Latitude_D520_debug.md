---
title: "Wireless issues with Latitude D520 debug"
date: 2009-03-15
forum: Hardware
---

### Post by smeckley on 2009-03-15
I was following the "WirelessTroubleShootingGuide" here on the help.ubuntu.com site.  It seems like the driver is there as when I do the lshw command I do see "configuration: driver=b43-pci..." but when I look for that driver in the lsmod it is not there. So the questions would be:

  1. What does that mean?
  2. How do I fix it?

Here is the commands I ran and the relevant outputs:

stephen@stephen-laptop:/media/disk/WINDOWS$ lshw
 ...
           *-network
                description: Network controller
                product: BCM4311 802.11b/g WLAN
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=b43-pci-bridge latency=0 module=ssb
 ...
stephen@stephen-laptop:/media/disk/WINDOWS$ lsmod |grep 43
rfcomm                 44432  2 
pcmcia                 43052  0 
b43                   131356  0 
rfkill                 17176  2 rfkill_input,b43
mac80211              216820  1 b43
led_class              12164  1 b43
input_polldev          11912  1 b43
snd_seq_midi           14336  0 
pcmcia_core            43412  3 pcmcia,yenta_socket,rsrc_nonstatic
battery                18436  0 
cdrom                  43168  1 sr_mod
ehci_hcd               43276  0 
ssb                    40580  2 b43,b44
stephen@stephen-laptop:/media/disk/WINDOWS$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

stephen@stephen-laptop:/media/disk/WINDOWS$

---

### Post by smeckley on 2009-03-15
If anyone has any thoughts I would really appreciate it...

---

