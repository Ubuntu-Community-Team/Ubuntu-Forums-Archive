---
title: "2 CD drives not working"
date: 2010-02-28
forum: Hardware
---

### Post by cheinze5719 on 2010-02-28
Let me start off my saying that I am completely new to the Linux world. 

I recently put Ubuntu 9.10 (from cd) on an older desktop computer. Everything seems to work well except neither of my cd drives work. I have looked all through the forums and have found similar problems but have not been able to fix mine. I started off with 8.10 and upgraded to 9.10. I noticed that my cd drives did not work in 8.10 but upgraded thinking that there would be a fix. Before installing Ubuntu on this system I was running XP and the drives both worked fine. When I go to Places --> Computer it shows that I have the two drives but double clicking on them does nothing even if a cd is in the drive. The only time I have gotten the drives to work is when I put a Ubuntu cd in and it fires up immediately. Other than that I can here it spin a couple times and then nothing. 

Not sure if this helps but I'll include it anyways:
fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0c02a312-2576-4ade-9707-2d9892c6e2d0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a7cf8ca2-653a-43a6-bf64-48b31aeeb259 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

UPDATE: Found out it will play an audio cd but not a DVD or burned disc.

---

### Post by wmichaelb on 2010-02-28
Hi, I have a similar issue with an HP laptop. I left a post at #post8896977, maybe we can get two solutions for one answer.

---

### Post by bart.vanaudenhove on 2010-05-01
On my HP Laptop any data cd or DVD would read  and write fine, but audio cds and movie dvds would not be recognized.

For me the solution was to physically slip the optical drive out of the  computer (unscrew a vise in the back and push the drive a bit out) =  unplugged and power off off course =, plug it back in, and at next  startup everything was fine. (I found it in another post somewhere)

From time to time the same problem reappears and the same solutions  works for a while...

This is in Ubuntu 9.10.

---

