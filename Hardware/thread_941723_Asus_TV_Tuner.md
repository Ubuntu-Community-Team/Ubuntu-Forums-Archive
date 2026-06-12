---
title: "Asus TV Tuner"
date: 2008-10-08
forum: Hardware
---

### Post by Levo on 2008-10-08
I have a PCI Asus TV tuner and I would like to know how to use it (which application, if a driver is required,...). I haven't used since I were a Windows user (about a year ago).

---

### Post by cariboo on 2008-10-08
More information would be helpful. In a terminal type:

```
sudo lshw -C multimedia
```

This should list useful information about your Tv tuner card. Please post the resulting information in your next post.

Jim

---

### Post by Levo on 2008-10-10
It says I have two multimedia controllers, the one is the TV Tuner and the other one my sound card. Here is TV Tuner part:

```
  *-multimedia:0          
       description: Multimedia controller
       product: SAA7133/SAA7135 Video Broadcast Decoder
       vendor: Philips Semiconductors
       physical id: 7
       bus info: pci@0000:01:07.0
       version: d0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=saa7134 latency=32 maxlatency=32 mingnt=84 module=saa7134
```

What do I need to do now?

---

### Post by Levo on 2008-10-11
Which program/driver do I need to install?

---

### Post by Levo on 2008-10-12
Anybody?

---

### Post by Levo on 2008-10-15
Anybody?

---

### Post by RudyLie on 2008-10-16
```
*-multimedia
       description: Multimedia controller
       product: SAA7130 Video Broadcast Decoder
       vendor: Philips Semiconductors
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=saa7134 latency=64 maxlatency=40 mingnt=16 module=saa7134
```

looks like we have the same problem... I can't make my tv tuner works in ubuntu hardy heron...

have you tried mythtv ? apt-get install mythtv ( don't work for me ) maybe it will work for you, because it's recommended so far...

---

### Post by Levo on 2008-10-17
> **RudyLie said:**
> looks like we have the same problem... I can't make my tv tuner works in ubuntu hardy heron...

have you tried mythtv ? apt-get install mythtv ( don't work for me ) maybe it will work for you, because it's recommended so far...

Neither for me, because I can't configure it.

---

### Post by AliG on 2008-10-26
Following are the output for the respective command on my system now how do i load the drivers for it to work in MythTV?

Myth TV is already intalled but it cannot "see" any tv tuner cards.

Help!!!

> lspci
02:01.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)


sudo lshw -C multimedia

  *-multimedia            
       description: Multimedia controller
       product: SAA7134/SAA7135HL Video Broadcast Decoder
       vendor: Philips Semiconductors
       physical id: 1
       bus info: pci@0000:02:01.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=saa7134 latency=32 maxlatency=32 mingnt=84 module=saa7134


---

### Post by Levo on 2008-12-27
Can anybody help? Does this TV Tuner work? If yes, how to configure Mythtv?

---

