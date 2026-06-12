---
title: "Is my External HDD broken?"
date: 2011-09-16
forum: Hardware
---

### Post by sakibmoon on 2011-09-16
I tried to format my Toshiba 1 TB External HDD a few days ago. It got stuck after completing about 90%. Now it is not showing on my Ubuntu. I tried with Windows too.

Then I installed Gparted. Gparted takes a great amount of time when I plug in the HDD, but if fails to show the device. Later I tried to mount it using terminal.
At first I tried 'fdisk' command. But it didn't show the device connected. Later when I tried 'udisks' command to mount the a specific device and searched for the available device with tab it showed a extra device named 'sdb' . It showed only when the HDD is connected. So, I tried to mount it from terminal, but it failed. Later I tried to format it from terminal. Failed again. Do you think it's broken?

Is there anything that I can try to make it work? Is it possible to repair it?

---

### Post by sakibmoon on 2011-09-18
I just want answer if it is possible to repair it or is it completely useless. Any clue would be fine.

---

### Post by sanderd17 on 2011-09-18
How many internal drives do you have?

Can you give the output of
```

ls /dev

```

If the external drive is an USB drive, can you give us the output of

```

lsusb

```

---

### Post by sakibmoon on 2011-09-18
The output of the *ls /dev is following*

```
agpgart          loop5               ram8      tty12  tty40  ttyS2
autofs           loop6               ram9      tty13  tty41  ttyS3
block            loop7               random    tty14  tty42  uinput
bsg              mapper              rfkill    tty15  tty43  urandom
btrfs-control    mcelog              root      tty16  tty44  usbmon0
bus              mem                 rtc       tty17  tty45  usbmon1
cdrom            net                 rtc0      tty18  tty46  usbmon2
cdrw             network_latency     scd0      tty19  tty47  usbmon3
char             network_throughput  sda       tty2   tty48  usbmon4
console          null                sda1      tty20  tty49  usbmon5
core             oldmem              sda2      tty21  tty5   vcs
cpu              pktcdvd             sda3      tty22  tty50  vcs1
cpu_dma_latency  port                sda5      tty23  tty51  vcs2
disk             ppp                 sda6      tty24  tty52  vcs3
dri              psaux               sda7      tty25  tty53  vcs4
dvd              ptmx                sda8      tty26  tty54  vcs5
dvdrw            pts                 sda9      tty27  tty55  vcs6
ecryptfs         ram0                sg0       tty28  tty56  vcs7
fb0              ram1                sg1       tty29  tty57  vcsa
fd               ram10               shm       tty3   tty58  vcsa1
full             ram11               snapshot  tty30  tty59  vcsa2
fuse             ram12               snd       tty31  tty6   vcsa3
hpet             ram13               sr0       tty32  tty60  vcsa4
input            ram14               stderr    tty33  tty61  vcsa5
kmsg             ram15               stdin     tty34  tty62  vcsa6
log              ram2                stdout    tty35  tty63  vcsa7
loop0            ram3                tty       tty36  tty7   vga_arbiter
loop1            ram4                tty0      tty37  tty8   zero
loop2            ram5                tty1      tty38  tty9
loop3            ram6                tty10     tty39  ttyS0
loop4            ram7                tty11     tty4   ttyS1
```



The output of the [I]lsusb is 

[/I]```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0480:a004 Toshiba America Info. Systems, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


The device is 1 TB external hard disk drive. So, of course it is connected via usb. The HDD was connected when I performed the commands.

---

### Post by desnaike on 2011-09-18
Do you have any other usb devices such as keyboard,mouse card reader attached.

---

### Post by sakibmoon on 2011-09-18
No. I don't use USB keyboard or mouse. Only USB that was attached was the HDD.

---

### Post by sakibmoon on 2011-09-18
I think you should look at the fifth line of the second output

```

Bus 001 Device 004: ID 0480:a004 Toshiba America Info. Systems, Inc.
```

My HDD is of Toshiba.

---

### Post by desnaike on 2011-09-18
What file system did u try to format the drive as and did u reboot the system after the failed attempt.

---

### Post by sakibmoon on 2011-09-18
I tried to format it to NTFS file system. I didn't reboot after the failed attempt. I reconnected it and it wasn't working anymore.

---

### Post by sanderd17 on 2011-09-19
The drive is visible on the USB port, but it isn't recognised as a hard drive.

Maybe the USB controller is broken.

If the HDD is still under warranty, return it to the shop.

Otherwise, open the case of the hard drive and put the drive directly into your computer (maybe replace your current drive and use a live CD to boot if you don't have enough cables).

If you can work with your hard drive via this method, you could consider to buy another case, they aren't that expensive. Or you could use the 1TB drive as internal drive.

Watch out: opening the case probably voids the warranty.

---

