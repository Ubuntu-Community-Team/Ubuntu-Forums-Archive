---
title: "[SOLVED] HP nc4010 laptop and PRO Wireless 2200BG - How?"
date: 2008-08-07
forum: Hardware
---

### Post by G1ZmO65 on 2008-08-07
I've installed Ubuntu 8.04 desktop on my HP nc4010 laptop but don't know how to connect to my home network.

From the commands below I can see that the wireless nic can see the wireless network but I cant figure out how to connect to it.

Can someone please advise a linux newbie?

Thanks

Paul

lshw Output:```

        *-network:0
             description: Wireless interface
             product: PRO/Wireless 2200BG Network Connection
             vendor: Intel Corporation
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: eth1
             version: 05
             serial: 00:16:6f:3d:27:80
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
```

iwconfig Output:```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:""  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

iwlist scan Output:```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:15:E9:60:E6:BE
                    ESSID:"gizmonet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=56/100  Signal level=-67 dBm  
                    Extra: Last beacon: 344ms ago
```

---

### Post by G1ZmO65 on 2008-08-07
Sorry, should have also said that the wired connection is fine and that the wireless nic worked with WinXP on the same laptop (built in)

Paul

---

### Post by G1ZmO65 on 2008-08-08
Can anyone give me a suggestion on this please? 

My missus hates trailing lan cables across the livingroom so really need to get the wireless operational! :(

I found that the wireless card does have Lnux drivers which I downloaded but tbh I don't know how to install them.

Also installed ndiswrapper which I think allows the use of windows drivers (did this before I discovered the linux drivers for the card were available)

Thanks

Paul

---

### Post by tommyknocker. on 2008-08-08
Hi, i think you wifi card is already working, as the command *iwlist* see your home wifi network *"gizmonet"*.

isn't there a network icon near the time and date in your Gnome panel?

---

### Post by G1ZmO65 on 2008-08-08
When I was trying this last night (at work now) if I right clicked on the network icon on the task bar I had Wired and Wireless networks both enabled but couldnt see a way of entering what network to connect to. There was an EDIT WIRELESS NETWORKS option but it came up with an empty list and only a REMOVE option. No ADD option. Weird.

Btw I booted it this morning and the wireless option wasnt there in the networking options. Pressed the wireless button on the lappy but no change. 

I agree it did seem to be detecting the wireless network but couldnt see any way of connecting to it and to enter the wep key.

I'm a bit lost tbh! lol 

(Oh for a wizard! :P )

Paul

---

### Post by tommyknocker. on 2008-08-08
> **G1ZmO65 said:**
> if I right clicked on the network icon on the task bar

if you **left-click** on that icon, you should see the list of all available wifi networks

right click is just to set more options...


> **G1ZmO65 said:**
> Btw I booted it this morning and the wireless option wasnt there in the networking options. Pressed the wireless button on the lappy but no change. 

mmm don't know what happened here... maybe you disabled it in any way?

does
```
sudo iwlist eth1 scanning 
```
still give any output?

---

### Post by G1ZmO65 on 2008-08-08
OK when I left click on the networking icon I get "MANUAL NETWORK CONFIG"

Went into it and set the Wireless network name and the security key etc

It said something like "Updating config" and after that I pulled the ethernet cable and tried a webpage but nowt :(

```
paul@nc4010:~$ sudo iwlist eth1 scanning
[sudo] password for paul: 
eth1      Scan completed :
          Cell 01 - Address: 00:15:E9:60:E6:BE
                    ESSID:"gizmonet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=97/100  Signal level=-28 dBm  
                    Extra: Last beacon: 464ms ago
```

---

### Post by molochi on 2008-08-08
I use a notebook with a 2200bg, sometimes the taskbar icon doesn't display all wireless networks in range. This is esp true when a bunch of APs are running on the same channel. Generally I see about 20 and the most I've seen is 32 with about half of them on channel 6. Generally, though the process is pretty automagic.

I would suggest booting the system with the ethernet cable unplugged. Leave it unplugged while you setup wireless. Also, if you have a mac address whitelist running on your AP, remember to add your 2200bg's mac to it before you try to connect wirelessly. Lastly while you're there change the AP's wifi channel to 11 or 3 if you are in a congested area.

Click on the wireless icon. If you see "gizmonet" click on it. If not click on "Create new wireless network". A window should popup. Enter your ssid (gizmonet) and select your level of security (none, wpa, whatever is appropriate). At this point the icon should change from "disconnected" to a pair of rotating spheres indicating that it is trying to connect. Next it should prompt you for your network password/phrase and then connect. You'll now have a 4bar stairstep icon. That should be all it takes.

---

### Post by G1ZmO65 on 2008-08-08
Well I really didn't do anything much but it's working!

I disabled the wep security on the router and tried to connect. It kept connecting and disconnecting so I changed the channel from 6 to 11 as you suggested and hey presto it connected. 
Re-enabled the security and I'm up and running!

Conclusion, as you suggest molochi I think there must be too many other things around on channel 6 (though I'm not detecting any other networks)

I've also white-listed my MAC address and set the IP for it to be static.

Phew!

Thanks again molochi :)

Paul

---

### Post by G1ZmO65 on 2008-08-09
Gah! Realised something else! I had set a static IP on a new machine on the network which happened to be the same as the one set in the router for the MAC address of the laptop. Doh!

Solved now :)
Silly me.

Paul

---

