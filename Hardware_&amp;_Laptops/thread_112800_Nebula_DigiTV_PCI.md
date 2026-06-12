---
title: "Nebula DigiTV PCI"
date: 2006-01-05
forum: Hardware &amp; Laptops
---

### Post by luiska on 2006-01-05
Hi

I am trying to get this Nebula DigiTV PCI card working. It is a DVB-T card. I have looked at linuxtv.org and some other sources. Someone said in another post that they got it working.

I also made a custom 2.6.15 kernel which should have the latest drivers for the card according to linuxtv.org.

Please can someone give some pointers on getting dvb card going on ubuntu?

I have done these:
modprobe dvb-btxx
modprobe mt352

What else needs to happen or being installed.

Another question is these modules in the ubuntu 2.6.12-10 kernel?

Thanks

---

### Post by bneuro1 on 2006-01-05
post your dmesg after modprobe it and you can see if everythings is right!

---

### Post by luiska on 2006-01-05
$ dmesg | grep bttv
[4294684.232000] bttv: driver version 0.9.15 loaded
[4294684.232000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[4294684.236000] bttv: Bt8xx card found (0).
[4294684.236000] bttv0: Bt878 (rev 17) at 0000:01:01.0, irq: 21, latency: 64, mmio: 0xcfffe000
[4294684.236000] bttv0: detected: Nebula Electronics DigiTV [card=104], PCI subsystem ID is 0071:0101
[4294684.236000] bttv0: using: Nebula Electronics DigiTV [card=104,autodetected]
[4294684.236000] bttv0: gpio: en=00000000, out=00000000 in=00ffffcb [init]
[4294684.280000] bttv0: using tuner=-1
[4294684.293000] bttv0: registered device video0
[4294684.306000] bttv0: registered device vbi0
[4294684.306000] bttv0: PLL: 28636363 => 35468950 .. ok
[4294684.330000] bttv0: add subdevice "dvb0"
[4294684.408000] DVB: registering new adapter (bttv0).

$ dmesg | grep dvb
[4294684.330000] bttv0: add subdevice "dvb0"
[4294684.411000] dvb-bt8xx: A frontend driver was not found for device 109e/0878 subsystem 0071/0101

$ cat /etc/modules
bttv
dvb-bt8xx
mt352


The problem is there obviously, no frontend found. How to fix it?

Thanks

---

### Post by bneuro1 on 2006-01-07
I found on : dvb-kernel/linux/Documentation/dvb/bt8xx.txt

2) Loading Modules
==================
In general you need to load the bttv driver, which will handle the gpio and
i2c communication for us, plus the common dvb-bt8xx device driver.
**The frontends for Nebula (nxt6000)**, Pinnacle PCTV (cx24110), TwinHan (dst),
FusionHDTV DVB-T Lite (mt352) and FusionHDTV5 Lite (lgdt330x) are loaded 
automatically by the dvb-bt8xx device driver.

3a) Nebula / Pinnacle PCTV / FusionHDTV Lite
---------------------------------------------

   $ modprobe bttv (normally bttv is being loaded automatically by kmod)
   $ modprobe dvb-bt8xx

(or just place dvb-bt8xx in /etc/modules for automatic loading)

In fact in card.txt there is:
frontend 
DVB-T:
   - alps_tdlb7		: Alps TDLB7 (sp8870 demodulator, sp5659 PLL)
   - alps_tdmb7		: Alps TDMB7 (cx22700 demodulator)
   - grundig_29504-401	: Grundig 29504-401 (LSI L64781 demodulator), tsa5060 PLL
   - tda1004x		: Philips tda10045h (td1344 or tdm1316l PLL)
   - **nxt6000** 		: Alps TDME7 (MITEL SP5659 PLL), Alps TDED4 (TI ALP510 PLL),
               		  Comtech DVBT-6k07 (SP5730 PLL)
               		  (NxtWave Communications NXT6000 demodulator)


I hope this help

---

### Post by luiska on 2006-01-08
Cheers

The thing is that there is two cards:

Old one is using the NXT6000
The new one is using the MT352

Now.... bttv and dvb-bt8xx modules are loaded! Somehow it doesnt seem to connect to the MT352 frontend I assume.

thanks

---

### Post by Rusna on 2006-02-14
I have the same problem.
When I type: 
```

scan /home/timppa/dvb/fi-Turku -v -v -5 > channels.conf

```
it says:
```

scanning /home/timppa/dvb/fi-Turku
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:1882: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 19 No such device

```

dmesg prints following:
```

[timppa@oppy dvb]$ dmesg | grep bttv
[4294701.716000] bttv: driver version 0.9.15 loaded
[4294701.716000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[4294701.719000] bttv: Bt8xx card found (0).
[4294701.719000] bttv0: Bt878 (rev 17) at 0000:03:05.0, irq: 16, latency: 64, mmio: 0xfddff000
[4294701.719000] bttv0: detected: Nebula Electronics DigiTV [card=104], PCI subsystem ID is 0071:0101
[4294701.719000] bttv0: using: Nebula Electronics DigiTV [card=104,autodetected]
[4294701.719000] bttv0: gpio: en=00000000, out=00000000 in=00ffffcb [init]
[4294701.734000] bttv0: using tuner=-1
[4294701.734000] bttv0: registered device video0
[4294701.735000] bttv0: registered device vbi0
[4294701.735000] bttv0: PLL: 28636363 => 35468950 .. ok
[4294701.759000] bttv0: add subdevice "dvb0"
[4296137.026000] DVB: registering new adapter (bttv0).

```
and
```

[timppa@oppy dvb]$ dmesg | grep dvb
[4294701.759000] bttv0: add subdevice "dvb0"
[4296137.039000] dvb-bt8xx: A frontend driver was not found for device 109e/0878 subsystem 0071/0101

```

I have also typed
```

modprobe bttv 
modprobe dvb-bt8xx

```

What can I do?

---

### Post by bneuro1 on 2006-02-15
You don't load the frontend:
Try:

modprobe bttv
modprobe mt352

and look at the dmesg.

---

### Post by Rusna on 2006-02-15
[QUOTE=bneuro1]You don't load the frontend:
Try:

modprobe bttv
modprobe mt352

and look at the dmesg.[/QUOTE]
Thanks for your reply, but it still complains the same:

```

$ sudo scan /home/timppa/dvb/fi-Turku -v -v -5 > channels.conf
scanning /home/timppa/dvb/fi-Turku
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
main:1882: FATAL: failed to open '/dev/dvb/adapter0/frontend0': 2 No such file or directory
$

```

I noticed that dmesg says among other things: 
```

[4294701.734000] bttv0: registered device video0
[4294701.735000] bttv0: registered device vbi0

```
Is there some conflict that "scan" tries to use "/dev/dvb/adapter0/frontend0" and there's none. But my DVB card is at video0 and vbi0? //See my previous post, dmesg

---

### Post by bneuro1 on 2006-02-15
Try 
modprobe modprobe nxt6000
look at dmesg and find if the frontend is recognized

---

### Post by Rusna on 2006-02-15
```

sudo modprobe nxt6000

```
Doesn't help. Any other ideas?

---

### Post by Nabu on 2006-12-11
I managed to get my Nebula working (I had exactly the same issue), with a whole lot of searching..this is what I did.

First create the directories in /dev with this script I found MAKEDEV.sh, can't remember where now:
#!/bin/sh
# Create device nodes for the Linux DVB API with DVB_API_VERSION 2.
# The devices created are suitable for most current PC DVB cards,
# i.e. cards having one frontend, one demux and optionally one
# MPEG decoder.
# The script creates devices for four cards by default. 
if [ -e /dev/.devfsd ]; then
        echo "It seems you are using devfs. Good!"
        exit 0
fi 

# get rid of old DVB API devices; do it twice for good measure...
rm -rf /dev/ost
rm -rf /dev/ost
rm -rf /dev/dvb
rm -rf /dev/dvb 
mkdir /dev/dvb
chmod 755 /dev/dvb 

for i in `seq 0 3`; do
        echo "Creating DVB devices in /dev/dvb/adapter$i"
        mkdir /dev/dvb/adapter$i
        chmod 755 /dev/dvb/adapter$i
        mknod -m 0660 /dev/dvb/adapter$i/video0    c 212   `expr 64 \* $i + 0`
        mknod -m 0660 /dev/dvb/adapter$i/audio0    c 212   `expr 64 \* $i + 1`
        mknod -m 0660 /dev/dvb/adapter$i/frontend0 c 212   `expr 64 \* $i + 3`
        mknod -m 0660 /dev/dvb/adapter$i/demux0    c 212   `expr 64 \* $i + 4`
        mknod -m 0660 /dev/dvb/adapter$i/dvr0      c 212   `expr 64 \* $i + 5`
        mknod -m 0660 /dev/dvb/adapter$i/ca0       c 212   `expr 64 \* $i + 6`
        mknod -m 0660 /dev/dvb/adapter$i/net0      c 212   `expr 64 \* $i + 7`
        mknod -m 0660 /dev/dvb/adapter$i/osd0      c 212   `expr 64 \* $i + 8`
        chown root.video /dev/dvb/adapter$i/*
done

Cut and paste into a file called makedev.sh (or whatever you want) directory, become root user with sudo:
sudo -s -H 
Change file permission to execute:
chmod 755 makedev.sh
Then run it:
./makedev.sh

This should create the directories.

Then execute (I found this on a Polish Ubuntu forum I think):
modprobe bttv i2c_hw=1 card=0x71
modprobe dvb-bt8xx
modprobe dst
chmod 666 /dev/dvb/adapter0/* 

Once this was completed I could execute:
scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/au-Melbourne > /root/.tzap/channels.conf

I found that (while following the [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php) guide) to see the stream with dvbstream my pid was not 600 and 601 but 102 and 103 (its shown in Hex when you start: tzap -r "BBC ONE"

Hope this helps.

N.

---

