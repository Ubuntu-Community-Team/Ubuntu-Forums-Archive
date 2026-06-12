---
title: "can't find lpt port"
date: 2010-04-16
forum: Hardware
---

### Post by MaxwellWR on 2010-04-16
Hi all!

I'm new in ubuntu.

Install Ubuntu 9.10 for using JTAG throw LPT port and can't find /dev/parport0 or /dev/lp0.

Motherboard:  GA-P43-ES3G 

How can i solve this problem?

---

### Post by IcarusR on 2010-04-16
Silly suggestion ..... is parallel port enabled in the bios ?? 
Both /dev/parport0 & /dev/lp0 are present on my server box, which has port enabled. 
Neither are present on my laptop which has port disabled in bios.

---

### Post by MaxwellWR on 2010-04-16
Yes. Port is enabled in the BIOS with the following parameters:
Address: 378 / IRQ7
Mode: SPP

Result of lsmod | grep lp
```

maxwell@Maxwell-pc:~$ lsmod | grep lp
lp                      8964  0 
parport                35340  2 ppdev,lp

```

Result of ls /dev
```

maxwell@Maxwell-pc:~$ ls /dev
adsp             mem                 rtc0        tty0   tty4   urandom
audio            mixer               scd0        tty1   tty40  usb
binder           net                 sda         tty10  tty41  usbmon0
block            network_latency     sda1        tty11  tty42  usbmon1
bus              network_throughput  sda2        tty12  tty43  usbmon2
cdrom            null                sda5        tty13  tty44  usbmon3
cdrw             nvidia0             sda6        tty14  tty45  usbmon4
char             nvidiactl           sdb         tty15  tty46  usbmon5
console          oldmem              sdb1        tty16  tty47  usbmon6
core             pktcdvd             sdb2        tty17  tty48  usbmon7
cpu_dma_latency  port                sdb3        tty18  tty49  usbmon8
disk             ppp                 sdb5        tty19  tty5   vcs
dsp              psaux               sdc         tty2   tty50  vcs1
dvd              ptmx                sdd         tty20  tty51  vcs2
dvdrw            pts                 sde         tty21  tty52  vcs3
ecryptfs         ram0                sdf         tty22  tty53  vcs4
fd               ram1                sequencer   tty23  tty54  vcs5
full             ram10               sequencer2  tty24  tty55  vcs6
fuse             ram11               sg0         tty25  tty56  vcs7
hidraw0          ram12               sg1         tty26  tty57  vcs8
hidraw1          ram13               sg2         tty27  tty58  vcsa
input            ram14               sg3         tty28  tty59  vcsa1
kmsg             ram15               sg4         tty29  tty6   vcsa2
log              ram2                sg5         tty3   tty60  vcsa3
loop0            ram3                sg6         tty30  tty61  vcsa4
loop1            ram4                shm         tty31  tty62  vcsa5
loop2            ram5                snapshot    tty32  tty63  vcsa6
loop3            ram6                snd         tty33  tty7   vcsa7
loop4            ram7                sndstat     tty34  tty8   vcsa8
loop5            ram8                sr0         tty35  tty9   zero
loop6            ram9                stderr      tty36  ttyS0
loop7            random              stdin       tty37  ttyS1
mapper           rfkill              stdout      tty38  ttyS2
mcelog           rtc                 tty         tty39  ttyS3

```

---

### Post by MaxwellWR on 2010-04-16
Problem solve.
```

maxwell@Maxwell-pc:~$ modprobe parport
maxwell@Maxwell-pc:~$ sudo modprobe parport_pc io=0x378 irq=7
maxwell@Maxwell-pc:~$ lsmod | grep par
parport_pc             31940  1 
parport                35340  3 parport_pc,ppdev,lp
maxwell@Maxwell-pc:~$ sudo rmmod lp

```

---

