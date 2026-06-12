---
title: "CD/DVD drive unmounted while burning a CD; how to remount?"
date: 2011-09-29
forum: Hardware
---

### Post by hreichgott on 2011-09-29
Hi,

I was burning a CD and Brasero crashed, while trying to read a scratched track on the source CD, I think. 
After the crash the CD/DVD drive was no longer mounted. The physical eject button does not work, either. The light on the side of the drive is steadily flashing. Physically ejecting the drive with a paper clip does work.
Rebooting changes nothing.

The /media directory is now empty. It used to have /cdrom and /cdrom0.

There are no entries for CD-ROM drives in fdisk or in /etc/fstab or in lspci. 

I tried mount but I can't remember which of the codes in /dev/ is supposed to be the CD drive. Here is what I have in /dev/
```
heather@Data:/dev$ ls
ati              network_throughput  sdb       tty30  tty61      ttyS5
autofs           null                sg0       tty31  tty62      ttyS6
block            oldmem              sg1       tty32  tty63      ttyS7
bsg              pktcdvd             shm       tty33  tty7       ttyS8
btrfs-control    port                snapshot  tty34  tty8       ttyS9
bus              ppp                 snd       tty35  tty9       uinput
char             psaux               stderr    tty36  ttyprintk  urandom
console          ptmx                stdin     tty37  ttyS0      usbmon0
core             pts                 stdout    tty38  ttyS1      usbmon1
cpu              ram0                tty       tty39  ttyS10     usbmon2
cpu_dma_latency  ram1                tty0      tty4   ttyS11     usbmon3
disk             ram10               tty1      tty40  ttyS12     usbmon4
ecryptfs         ram11               tty10     tty41  ttyS13     v4l
fb0              ram12               tty11     tty42  ttyS14     vcs
fd               ram13               tty12     tty43  ttyS15     vcs1
full             ram14               tty13     tty44  ttyS16     vcs2
fuse             ram15               tty14     tty45  ttyS17     vcs3
hpet             ram2                tty15     tty46  ttyS18     vcs4
input            ram3                tty16     tty47  ttyS19     vcs5
kmsg             ram4                tty17     tty48  ttyS2      vcs6
log              ram5                tty18     tty49  ttyS20     vcsa
loop0            ram6                tty19     tty5   ttyS21     vcsa1
loop1            ram7                tty2      tty50  ttyS22     vcsa2
loop2            ram8                tty20     tty51  ttyS23     vcsa3
loop3            ram9                tty21     tty52  ttyS24     vcsa4
loop4            random              tty22     tty53  ttyS25     vcsa5
loop5            rfkill              tty23     tty54  ttyS26     vcsa6
loop6            root                tty24     tty55  ttyS27     vga_arbiter
loop7            rtc                 tty25     tty56  ttyS28     video0
mapper           rtc0                tty26     tty57  ttyS29     zero
mcelog           sda                 tty27     tty58  ttyS3
mem              sda1                tty28     tty59  ttyS30
net              sda2                tty29     tty6   ttyS31
network_latency  sda5                tty3      tty60  ttyS4

```

Hardware: Acer Aspire 5253. CD-ROM drive is a Matsushita of some kind. (I don't know how to find the model number if the computer doesn't know the drive is there.)

Can anyone help?

---

### Post by hreichgott on 2011-09-29
Weirdly, this one solved itself after a couple hours of being powered off.

---

