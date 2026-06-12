---
title: "HD checked every time in boot (Ubuntu 10.04 LTS)"
date: 2012-01-01
forum: Hardware
---

### Post by HiDrake on 2012-01-01
My HD is detected and checked every time I switch on my laptop, and this normal?

Image >>> [http://postimage.org/image/nz41z0xcx/](http://postimage.org/image/nz41z0xcx/)

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=3567c7ba-3f3d-420a-bdc4-156ca719594e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=d844b127-f627-4322-8a7f-14fcc08a7e7b /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=4bde7d61-f4eb-461c-9f1f-2500d9369240 none            swap    sw              0       0

---

### Post by abtekk on 2012-01-01
I too had this trouble on my old system, it started when I began to get bad sectors. To get rid of it, boot into a Live CD of the same distro (U 11.04) and for the point and click way, open GParted and right-click on the  partition you want to have a file system check run in and click 'check'  from the right-click menu, then click 'apply' in a couple of different  places and wait a few minutes for the process to complete.

That worked for me.

---

### Post by HiDrake on 2012-01-01
> **abtekk said:**
> I too had this trouble on my old system, it started when I began to get bad sectors. To get rid of it, boot into a Live CD of the same distro (U 11.04) and for the point and click way, open GParted and right-click on the  partition you want to have a file system check run in and click 'check'  from the right-click menu, then click 'apply' in a couple of different  places and wait a few minutes for the process to complete.

That worked for me.

I'll try this.
Thanls

---

### Post by HiDrake on 2012-01-01
Failed.
_Ubuntu_ still checking HD

---

### Post by LinuxFan999 on 2012-01-01
How old is your laptop?

---

### Post by HiDrake on 2012-01-02
> **LinuxFan999 said:**
> How old is your laptop?

Dell Inspiron Mini 1018


[LIST]
[*]Intel Atom N455 Processor (1.66GHz, 512KB Cache)
[*]1GB DDR3 Memory at 667MHz (1x1GB)
[*]250GB Hard Drive; Wireless-N Mini-Card
[*]10.1" Widescreen Display; Intel GMA 3150 Graphics
[*]6-Cell Lithium Ion Battery
[/LIST]


BIOS in ATA Mode

---

