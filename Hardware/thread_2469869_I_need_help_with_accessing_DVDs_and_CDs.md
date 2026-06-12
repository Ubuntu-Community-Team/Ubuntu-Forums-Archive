---
title: "I need help with accessing DVDs and CDs"
date: 2021-12-11
forum: Hardware
---

### Post by archimedes1981 on 2021-12-11
I've always had issues with DVDs and CDs on Ubuntu but this time I'm stuck. I've used linux a lot but I'm still not very good at it. 
Long story short my fstab is
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=tttttttt-aaaa-bbbb-cccc-iiiiiiiiiiii /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=yyyyyyyy-cccc-bbbb-aaaa-pppppppppppp /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=999999-bbbb-gggg-7777-oooooooooooo none            swap    sw              0       0
/dev/disk/by-id/ata-PIONEER_DVD-RW_DVRTD11RS_MLQC020788WL /mnt/ata-PIONEER_DVD-RW_DVRTD11RS_MLQC020788WL auto nosuid,nodev,nofail,x-gvfs-show 0 0
U

```
while
```
myself@desktopA:~$ sudo lshw -C disk
  *-disk                    
       description: SCSI Disk
       product: STORAGE DEVICE
       vendor: Generic
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: 9451
       capabilities: removable
       configuration: logicalsectorsize=512 sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sdb
  *-disk
       description: ATA Disk
       product: HGST HTS721010A9
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: A3B0
       serial: JG40006PGS53NC
       size: 931GiB (1TB)
       capabilities: removable
       configuration: ansiversion=5 logicalsectorsize=512 sectorsize=4096
     *-medium
          physical id: 0
          logical name: /dev/sda
          size: 931GiB (1TB)
          capabilities: partitioned partitioned:dos
          configuration: signature=00077777
```

```
myself@DesktopA:~$ ls /dev
autofs           kvm           mcelog    tty19  tty56      ttyS6
block            lightnvm      mem       tty2   tty57      ttyS7
bsg              log           mqueue    tty20  tty58      ttyS8
btrfs-control    loop0         net       tty21  tty59      ttyS9
bus              loop1         null      tty22  tty6       udmabuf
char             loop10        nvram     tty23  tty60      uhid
console          loop11        port      tty24  tty61      uinput
core             loop12        ppp       tty25  tty62      urandom
cpu              loop13        psaux     tty26  tty63      userio
cpu_dma_latency  loop14        ptmx      tty27  tty7       vcs
cuse             loop15        pts       tty28  tty8       vcs1
disk             loop16        random    tty29  tty9       vcs2
dri              loop17        rfkill    tty3   ttyprintk  vcs3
ecryptfs         loop18        rtc       tty30  ttyS0      vcs4
fb0              loop19        rtc0      tty31  ttyS1      vcs5
fd               loop2         sda       tty32  ttyS10     vcs6
full             loop20        sda1      tty33  ttyS11     vcsa
fuse             loop21        sda2      tty34  ttyS12     vcsa1
hidraw0          loop22        sda5      tty35  ttyS13     vcsa2
hidraw1          loop23        sda6      tty36  ttyS14     vcsa3
hidraw2          loop24        sdb       tty37  ttyS15     vcsa4
hidraw3          loop25        sg0       tty38  ttyS16     vcsa5
hidraw4          loop26        sg1       tty39  ttyS17     vcsa6
hpet             loop27        shm       tty4   ttyS18     vcsu
hugepages        loop28        snapshot  tty40  ttyS19     vcsu1
hwrng            loop29        snd       tty41  ttyS2      vcsu2
i2c-0            loop3         stderr    tty42  ttyS20     vcsu3
i2c-1            loop30        stdin     tty43  ttyS21     vcsu4
i2c-10           loop31        stdout    tty44  ttyS22     vcsu5
i2c-2            loop32        tty       tty45  ttyS23     vcsu6
i2c-3            loop33        tty0      tty46  ttyS24     vfio
i2c-4            loop34        tty1      tty47  ttyS25     vga_arbiter
i2c-5            loop35        tty10     tty48  ttyS26     vhci
i2c-6            loop4         tty11     tty49  ttyS27     vhost-net
i2c-7            loop5         tty12     tty5   ttyS28     vhost-vsock
i2c-8            loop6         tty13     tty50  ttyS29     zero
i2c-9            loop7         tty14     tty51  ttyS3      zfs
initctl          loop8         tty15     tty52  ttyS30
input            loop9         tty16     tty53  ttyS31
kfd              loop-control  tty17     tty54  ttyS4
kmsg             mapper        tty18     tty55  ttyS5
```

Basically the drive works because it can boot from it. This complete inaccessibility to the drive has probably happened since I changed mobo. It's a complete different kind. I had a Pentium before and now it's an AMD A4-5000.
I really would like to solve this soon cos I have a lot of xmas movies that i need to watch before it's too late and I don't get in the spirit in time.
thanks

---

### Post by sudodus on 2021-12-11
Have you installed the restricted extras?

```

sudo apt update
sudo apt install ubuntu-restricted-extras

```

---

### Post by archimedes1981 on 2021-12-11
I did now, restarted but nothing.

---

### Post by sudodus on 2021-12-11
Next thing to try: Boot from a live USB with some light-weight Ubuntu community flavour (to avoid too heavy downloads), for example Lubuntu 16.04 and 18.04 and 20.04: "Try Lubuntu" and check if you get access to the optical media.

Then maybe borrow a computer with an optical drive and test there because it happens that the optical drives fail (it has happened to me at least twice if I remember correctly).

---

### Post by rsteinmetz70112 on 2021-12-12
That you can boot from a DVD means it's probably working.

What are you trying to do with the CD or DVD?
What king of media do you want to use in it?
What do you expect to happen when you put a disc in the drive?

Can you see the mount point of the drive?
```
/mnt/ata-PIONEER_DVD-RW_DVRTD11RS_MLQC020788WL
```
If you can see it can you see file in that directory when a CD or DVD is on the drive?
That mount point seems an extraordinarily long name.

---

### Post by CatKiller on 2021-12-13
> **archimedes1981 said:**
> Long story short my fstab is
You don't need an fstab entry for optical media. Your DE will automatically mount optical media under /media when you put a disc in.

---

