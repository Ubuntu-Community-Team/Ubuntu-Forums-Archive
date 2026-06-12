---
title: "Apt-get extremely slow"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by cptn. Cookie on 2008-12-16
Hi there,

I recently installed Xubuntu. The system runs fine, but when installing or updating something, my whole computer becomes unusable. It is sooooo slow. It doesn't matter if I install something via the cli, with synaptic or 'add/remove programs'. 

Does anyone know why? The problem persists with compiz off.

---

### Post by taurus on 2008-12-16
How much RAM and swap space does it have?

```
free -m
```

---

### Post by cptn. Cookie on 2008-12-16
> **taurus said:**
> How much RAM and swap space does it have?

```
free -m
```

I get this:

```

sander@Klaptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           492        481         10          0          3         57
-/+ buffers/cache:        420         72
Swap:          972        349        622
sander@Klaptop:~$ 

```

---

### Post by taurus on 2008-12-16
What's the spec of your machine and how much space does it have?

```
df -h
```

---

### Post by cptn. Cookie on 2008-12-16
> **taurus said:**
> What's the spec of your machine 

Intel T2300 1,6Ghz (2 core)
512MB ram
Intel mobile 945GM
(Toshiba Satellite A100)

> **taurus said:**
> and how much space does it have?

```
df -h
```

```
sander@Klaptop:~$ df -h
Bestandssysteem            Grtte   Gebr Besch Geb% Aangekoppeld op
/dev/sda6              50G   21G   28G  43% /
tmpfs                 247M     0  247M   0% /lib/init/rw
varrun                247M  304K  247M   1% /var/run
varlock               247M     0  247M   0% /var/lock
udev                  247M  2,7M  244M   2% /dev
tmpfs                 247M     0  247M   0% /dev/shm
lrm                   247M  2,0M  245M   1% /lib/modules/2.6.27-9-generic/volatile
sander@Klaptop:~$ 


```

---

### Post by taurus on 2008-12-16
It shouldn't be slow on your machine.  What are the outputs of these comands?

```
sudo fdisk -l
cat /etc/fstab
top
```

---

### Post by cptn. Cookie on 2008-12-16
```

sander@Klaptop:~$ sudo fdisk -l
[sudo] password for sander: 

Schijf /dev/sda: 120.0 GB, 120034123776 bytes
255 koppen, 63 sectoren/spoor, 14593 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0xe799ab83

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1               1         192     1536000   27  [onbekend]
Partitie 1 eindigt niet op een cilindergrens.
/dev/sda2   *         193        7841    61440592+   7  HPFS/NTFS
/dev/sda3            7842       14593    54235440    5  Uitgebreid
/dev/sda5            7842        7965      995998+  82  Linux wisselgeheugen
/dev/sda6            7966       14593    53239378+  83  Linux

```

and

```

sander@Klaptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=f6d78d14-5e41-4d57-be8d-a472987199b4 /               ext3    relatime,errors=remount-ro 0       1
/dev/sda2 /mnt/Windows nts ro,noauto,user 0 0
# /dev/sda5
UUID=e2870520-917d-4d61-86ca-3c8430989246 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

and finally :)

```

sander@Klaptop:~$ top

top - 15:58:59 up  2:01,  2 users,  load average: 0.52, 0.82, 1.25
Tasks: 122 total,   1 running, 121 sleeping,   0 stopped,   0 zombie
Cpu(s): 50.0%us,  0.0%sy,  0.0%ni, 50.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    504580k total,   498828k used,     5752k free,     5484k buffers
Swap:   995988k total,   325340k used,   670648k free,    75464k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
13580 sander    20   0  2416 1152  884 R  196  0.2   0:00.18 top                
 6186 sander    20   0  173m  43m  10m S   98  8.8  13:54.69 banshee-1          
    1 root      20   0  3056  516  460 S    0  0.1   0:01.52 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.04 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:01.64 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.04 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.76 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.68 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.06 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0      
   52 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1      
   54 root      15  -5     0    0    0 S    0  0.0   0:02.14 kblockd/0          
   55 root      15  -5     0    0    0 S    0  0.0   0:00.06 kblockd/1          
sander@Klaptop:~$ 

```

---

### Post by taurus on 2008-12-16
I assume this is just a type for your ntfs partition.

```
/dev/sda2 /mnt/Windows **nts** ro,noauto,user 0 0
```
It should be 

```
/dev/sda2 /mnt/Windows **[COLOR="Blue"]ntfs[/COLOR]** ro,noauto,user 0 0
```
Maybe that's why your ntfs partition, /dev/sda2, is never mounted.

Meanwhile, you can try something like

```
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by cptn. Cookie on 2008-12-16
Haha, thx for the fstab note. I wondered why it didn't worked before :')

I only don't think the commands will work, my system was already up to date and it only removed some old kernels (and while it was doing that, the music stuttered and my mouse froze for a few seconds).

But still, thx for your help so far :)

---

### Post by cptn. Cookie on 2008-12-17
Hmm, no-one else? :(

---

### Post by cptn. Cookie on 2008-12-20
bump

---

### Post by cptn. Cookie on 2008-12-22
Last bump for this topic.

This problem is really annoying me. I guess I won't be using Xubuntu much longer if I can't fix the problem.

---

### Post by upchucky on 2008-12-22
port forwarding if behind router and or firewall?

---

### Post by cptn. Cookie on 2008-12-23
> **upchucky said:**
> port forwarding if behind router and or firewall?

That cannot be the problem... While downloading my system runs fine, but while installing/removing/upgrading the packages it's like having a 386 :')

---

### Post by hyperdude111 on 2008-12-23
This happens to me as well. I realised the problem was that i was running a media player called songbird which was using too much ram (100mb +) check if you are running any resource hogs and close them before using apt.

-Hyper-

---

