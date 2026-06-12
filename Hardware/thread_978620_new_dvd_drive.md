---
title: "new dvd drive"
date: 2008-11-11
forum: Hardware
---

### Post by jdmdelsol97 on 2008-11-11
can anyone help me. my friend gave me his old dvd drive which works, but it wont play or a tleast show a dvd  on my comp.....it loads spins and everything but it wont play...any ideas? all i want it to do is play dvds

---

### Post by taurus on 2008-11-11
Before you want to play a DVD movie on your machine, you need to install some codecs first.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by jdmdelsol97 on 2008-11-11
which ones do i need?
all i did was unplug my cd drive and swapped it in place of the dvd drive, all cables matched up. but it wont show a dvd or anything

---

### Post by taurus on 2008-11-11
So you mean that Ubuntu doesn't even detect your new DVD drive?  First, does the BIOS detect your DVD drive?  Then, wait until Ubuntu finishes booting, open a terminal, and post the output of this command here.

```
sudo cat /var/log/messages
```

---

### Post by jdmdelsol97 on 2008-11-11
i tried opening the bios and no go

---

### Post by taurus on 2008-11-11
So you mean the BIOS doesn't even detect that DVD drive?  If the BIOS can't even detect it, then it means there is something wrong with the DVD drive.  It's either dead or bad cable.

---

### Post by jdmdelsol97 on 2008-11-11
i thought by starting up and hitting the f12 or f10 would start up my bios....no matter which keys i hit it wont open up the bios...the drive it self spins, lights up, but wont show that a dvd is in there

** i'll make a video and post the link **

---

### Post by taurus on 2008-11-11
Try Del key or even <Ctrl><Alt>Del on some old system.  When you first turn on your machine, there should be a quick message saying something about pressing which key to access the BIOS.  Do you see that message at all?

Which brand is it?

---

### Post by jdmdelsol97 on 2008-11-11
i tried delete nothing....i get this screen about curb something i tried going into it but its something about booting generic mode or something....its a dell dimension 4500
i have accessed the bios many times before when installing ubuntu but i cant get get the bios to open up now

---

### Post by jdmdelsol97 on 2008-11-11
[http://www.youtube.com/watch?v=GVCpq_rD9Yk]("http://www.youtube.com/watch?v=GVCpq_rD9Yk")

this is what happens

---

### Post by sisco311 on 2008-11-11
open a terminal(Applications --> Accessories --> Terminal)
type:
```
lshw -C disk
```
and
```
cat /etc/fstab
```and post the output.

---

### Post by jdmdelsol97 on 2008-11-11
this is what the terminal tells me

johny@johny-desktop:~$ lshw -C disk
WARNING: you should run this program as super-user.
johny@johny-desktop:~$

---

### Post by jdmdelsol97 on 2008-11-11
i tried sudo infront of it and this is what the terminal read 

johny@johny-desktop:~$ sudolshw -C disk
bash: sudolshw: command not found
johny@johny-desktop:~$ sudo lshw -C disk
[sudo] password for johny: 
  *-disk                  
       description: ATA Disk
       product: WDC WD200EB-75CP
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 06.0
       serial: WD-WMAAU3127402
       size: 18GiB (20GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=9fcd9fcd
johny@johny-desktop:~$

then.....

johny@johny-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ec81f1d4-53e7-48e4-8f0b-7805f15d4a55 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=7c4aeeee-5756-4681-8e3f-c41341263118 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
johny@johny-desktop:~$

---

### Post by sisco311 on 2008-11-11
your drive is not detected in ubuntu.

reboot and press F2 to see if it's detected by the bios.

---

### Post by jdmdelsol97 on 2008-11-11
i tried and it wont show a dvd drive....just a removable device...i went and put the cd drive just to see what would happen and it wont recognize that either

---

### Post by taurus on 2008-11-11
Make sure the cable plugs into the mobo securely or you have a bad cable.

---

### Post by jdmdelsol97 on 2008-11-11
> **taurus said:**
> Make sure the cable plugs into the mobo securely or you have a bad cable.

i secured evertyhing well, its weird the cd drive was working fine the other day...the dvd drive spins and makes noises but wont recognize any disc

---

### Post by jdmdelsol97 on 2008-11-12
i got some pics of the drive for you guys showing you how i have it connected

[IMG]file:///home/johny/Desktop/photo(2).jpg[/IMG]
[IMG]file:///home/johny/Desktop/photo.jpg[/IMG]

---

