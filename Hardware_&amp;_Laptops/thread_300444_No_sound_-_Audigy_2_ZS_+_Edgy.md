---
title: "No sound - Audigy 2 ZS + Edgy"
date: 2006-11-15
forum: Hardware &amp; Laptops
---

### Post by gtom on 2006-11-15
I did a clean install of Ubuntu Edgy 6.10 a few days ago and everything is great apart from I haven't managed to get the sound working yet. I'm posting from it now. 8) 

I have tried a number of ways to play sounds and none have worked so I believe it's something to do with drivers/alsa.

```
tom@tom-linux:~$ cat /proc/asound/cards
 0 [SAA7134        ]: SAA7134 - SAA7134
                      saa7130[0] at 0xfdefe000 irq 66
 1 [Audigy         ]: Audigy - Audigy 1 [Unknown]
                      Audigy 1 [Unknown] (rev.5, serial:0x20051102) at 0x9c00, irq 58

```

The first item is something to do with my TV card. On the volume control I have set the Audigy to be the device it controls. None of the items are muted and all the volume levels are set sufficiently high.

lspci -v contains this:

```
05:06.0 Multimedia audio controller: Creative Labs SB Audigy (rev 05)
        Subsystem: Creative Labs Unknown device 2005
        Flags: bus master, medium devsel, latency 32, IRQ 58
        I/O ports at 9c00 [size=64]
        Capabilities: <access denied>

```

One thing I did notice is that my wireless card is also using IRQ 58. :-k 

Any help/suggestions appreciated!

---

### Post by gtom on 2006-11-16
Morning bump. :)

---

### Post by Decade on 2006-11-16
Sharing IRQ should be fine, though I would check dmesg to make sure the Audigy's driver actually is working. However, the not working seems to be with PowerPC, so you should be fine.

Last time I heard of a problem with Audigy 2 ZS, a day or so ago, it was because the sound output was set to digital instead of analog. Try changing that switch.

---

### Post by gtom on 2006-11-16
Thanks for the reply. I will try your suggestions when I get home and post back with the results.

---

### Post by gtom on 2006-11-16
I've attached some of the output from dmesg. There were lots of lines after what's in the file - most were something like this:

```
[17181543.600000] wlan0: association FAILED: peer sent response code 12 (Assoc denied (reason outside of 802.11b scope), maybe MAC filtering by peer?)
[17181548.608000] wlan0: tx error 0x20, buf 08!

```

:-? 

Anyway I couldn't see anything related to the Audigy in the output of dmesg. There's some stuff going on with my TV card though (saa7130 and saa7134).

Optical/digital output is unticked in the switches tab of my volume control.

---

### Post by Decade on 2006-11-17
Right. I said change it. I don't know which position it's supposed to be in. Some sources say on, some say off.

Your kernel ring buffer filled with other stuff, and it automatically removes the first messages to make space. I think Ubuntu stores what it said in some log file in /var/log/, but I don't remember which one.

---

### Post by gtom on 2006-11-18
Wicked! Got it working!

I enabled the switch for "Audigy Analog/Digital Output Jack" and my sound works now.

Now to get a few other bits and pieces working and I may be able to leave Windows behind for everything but gaming. :)

---

### Post by M0nk3yM4n on 2006-12-07
I have an Audigy ZS where do I even get started on installing this thing?

---

