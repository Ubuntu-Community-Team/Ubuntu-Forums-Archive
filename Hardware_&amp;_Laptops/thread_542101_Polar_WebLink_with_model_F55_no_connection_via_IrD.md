---
title: "Polar WebLink with model F55: no connection via IrDA"
date: 2007-09-03
forum: Hardware &amp; Laptops
---

### Post by bierholen on 2007-09-03
I would like to use the WebLink tool provided by Polar to transfer the data from my heart rate monitor F55 to the online personal trainer service.

I got the WebLink software installed using wine ([http://appdb.winehq.org/appview.php?iVersionId=7704&iTestingId=11134](http://appdb.winehq.org/appview.php?iVersionId=7704&iTestingId=11134)) and it seems to run fine. 

The F55 is well recognized by ubuntu via my laptop's FIR IrDA adapter and I can establish a connection:

> 
# cat /proc/net/irda/discovery
IrLMP: Discovery log:

nickname: Polar F55, hint: 0x8204, saddr: 0x614559ef, daddr: 0xd4f81e92
__________________________________________

# ifconfig irda0
irda0   Link encap:IrLAP  HWaddr 61:45:59:ef
           UP RUNNING NOARP  MTU:2048  Metric:1
           RX packets:451 errors:0 dropped:0 overruns:0 frame:0
           TX packets:7861 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:8
           RX bytes:12628 (12.3 KiB)  TX bytes:245937 (240.1 KiB)
__________________________________________

# irdadump
[...]
19:03:42.961753 xid:rsp 614559ef < d4f81e92 S=6 s=4 Polar F55 hint=8204 [ PDA/Palmtop IrCOMM ] (26)
[...]


Despite this successful connection WebLink does not receive any data and says

Error starting connection!

I have the feeling that wine can't deal with the infrared connection the way it is configured right now. Unfortunately, I don't have any clue what to change to make it work. 

Any ideas?

---

### Post by dbloom on 2007-11-05
i'm having the same problem in Ubuntu 7.10 (gutsy).  I'm curious if you figured this out or if anyone else has any ideas.

i'm using a usb irda and it seems to be recognized in the device manager as such.  i also installed irda-utils, but no help.  

any help would be great.  thanks!

---

### Post by GrumpyBob on 2007-12-02
Same here with 7.10 Gutsy, Crossover Office, Polar 720i, Polar USB IR receiver.

As far as I can tell, the message "Error starting connection!" refers to connecting to the watch via the IR device.

Would be good to get the weblink working...

Robert

Robert

---

