---
title: "change extended partitions into primary partitions"
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by miazma on 2009-01-10
Hello,

I've had Windows XP on two partitions (one FAT 32 and one NTFS partition) which I deleted via GParted. My partition table:

```

Festplatte /dev/sda: 9729 Zylinder, 255 Köpfe, 63 Sektoren/Spur
Warnung: erweiterte Partition beginnt nicht an einer Zylindergrenze
DOS und Linux werden den Inhalt unterschiedlich interpretieren.
Einheit = Zylinder von 8225280 Bytes, Blöcke von 1024 Bytes, Zählung beginnt bei 0

   Gerät  boot. Anfang   Ende  #Zyl.    #Blöcke   Id  System
/dev/sda1          0       -       0          0    0  Leer
/dev/sda2          0       -       0          0    0  Leer
/dev/sda3   *      0+   9728    9729-  78148161    5  Erweiterte
/dev/sda4          0       -       0          0    0  Leer
/dev/sda5       2163    9728    7566   60773895   83  Linux
/dev/sda6        191+   2162    1972-  15840058+  83  Linux
/dev/sda7          0+    190     191-   1534113   82  Linux Swap / Solaris

```

I wanted to change /dev/sda5 to /dev/sda1, /dev/sda6 to /dev/sda2, /dev/sda7 to /dev/sda3 and get a primary partition instead of an extended (which is also split into logical partitions)...

Any possibility to change the partitions?

greetings,
Johannes

---

### Post by chex_m8 on 2009-01-10
Yes it is easy 
1. use gparted and delete all your partitions 
2. repartition your disk how you want it 
3. reinstall OS's
now your ready to rock n roll

---

### Post by caljohnsmith on 2009-01-10
Based on the physical layout of your partitions, it looks like you could convert one or more of your logical partitions into primary partitions. How about posting the output of:
```
sudo fdisk -lu
sudo sfdisk -d 
```
And we can go from there if you want.

---

### Post by miazma on 2009-01-11
```

Platte /dev/sda: 80.0 GByte, 80026361856 Byte
255 Köpfe, 63 Sektoren/Spuren, 9729 Zylinder, zusammen 156301488 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Disk identifier: 0x1669c708

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda3   *          63   156296384    78148161    5  Erweiterte
/dev/sda5        34748595   156296384    60773895   83  Linux
/dev/sda6         3068478    34748594    15840058+  83  Linux
/dev/sda7             189     3068414     1534113   82  Linux Swap / Solaris

Partitionstabelleneinträge sind nicht in Platten-Reihenfolge

```

```

johannes@luna:~/Desktop/Thesis/Lichtenberger$ sudo sfdisk -d
Warnung: erweiterte Partition beginnt nicht an einer Zylindergrenze
DOS und Linux werden den Inhalt unterschiedlich interpretieren.
# Partitionstabelle von /dev/sda
unit: sectors

/dev/sda1 : start=        0, size=        0, Id= 0
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=       63, size=156296322, Id= 5, bootable
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 34748595, size=121547790, Id=83
/dev/sda6 : start=  3068478, size= 31680117, Id=83
/dev/sda7 : start=      189, size=  3068226, Id=82

```

/dev/sda6 is the root ("/") partition, /dev/sda5 is home ("/home")

---

### Post by caljohnsmith on 2009-01-11
OK, you'll need a Live CD in order to complete all the steps here, because you'll need to boot your Live CD after making the changes. So if you do have a bootable Live CD, how about first downloading the attached "partition_table.txt" file to your Ubuntu desktop, and then do:
```
sudo sfdisk -f /dev/sda -O ~/Desktop/sda_sectors_modified.save < ~/Desktop/partition_table.txt
```
That will produce a lot of output, including some warnings, so you don't need to be alarmed; but please post the output so I can check that everything went OK. Also, the above command will create a backup of the sectors being modified as a "sda_sectors_modified.save" file that will be created on your desktop, so that if for some reason anything were to go wrong, you can easily restore your original partition table with that file. Therefore, be sure to copy that file to a different drive, or you could for instance save it to your email account or something like that. 

Once you've run the above command, go ahead and boot your Live CD, open a terminal and do:
```
sudo fdisk -lu
sudo sfdisk -d
sudo grub
grub> root (hd0,1)
grub> setup (hd0)
grub> quit
```
And please post the output of all the commands before you do "quit". Next reboot, see if you can boot Ubuntu OK, and if not we may also need to modify your fstab or menu.lst depending on whether they use UUIDs or device names. So if you have any trouble booting, please download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, and we can work from there.

---

### Post by miazma on 2009-01-11
Firstly the output from `fdisk`...:

```

johannes@luna:~/Desktop/Thesis/Lichtenberger$ sudo sfdisk -f /dev/sda -O ~/Desktop/sda_sectors_modified.save < ~/Desktop/partition_table.txt
[sudo] password for johannes: 
Überprüfe, dass niemand diese Festplatte zur Zeit benutzt …
BLKRRPART: Device or resource busy

Diese Festplatte ist zur Zeit in Benutzung – Neupartitionierung ist vermutlich
eine schlechte Idee. Hängen Sie alle Dateisysteme auf dieser Platte aus und
deaktivieren Sie alle Swap-Partitionen (mit swapoff).
Benutzen Sie --no-reread, um diese Überprüfung zu unterbinden.

Festplatte /dev/sda: 9729 Zylinder, 255 Köpfe, 63 Sektoren/Spur
Warnung: erweiterte Partition beginnt nicht an einer Zylindergrenze
DOS und Linux werden den Inhalt unterschiedlich interpretieren.
Alte Aufteilung:
Einheit = Zylinder von 8225280 Bytes, Blöcke von 1024 Bytes, Zählung beginnt bei 0

   Gerät  boot. Anfang   Ende  #Zyl.    #Blöcke   Id  System
/dev/sda1          0       -       0          0    0  Leer
/dev/sda2          0       -       0          0    0  Leer
/dev/sda3   *      0+   9728    9729-  78148161    5  Erweiterte
/dev/sda4          0       -       0          0    0  Leer
/dev/sda5       2163    9728    7566   60773895   83  Linux
/dev/sda6        191+   2162    1972-  15840058+  83  Linux
/dev/sda7          0+    190     191-   1534113   82  Linux Swap / Solaris
Neue Aufteilung:
Einheit = Sektoren von 512 Bytes, Zählung beginnt bei 0

   Gerät  boot.   Anfang      Ende  #Sektoren Id  System
/dev/sda1      34748595 156296384  121547790  83  Linux
/dev/sda2   *   3068478  34748594   31680117  83  Linux
/dev/sda3           189   3068414    3068226  82  Linux Swap / Solaris
/dev/sda4             0         -          0   0  Leer
Warnung: Partition 2 beginnt nicht an einer Zylindergrenze
Die neue Partitionstabelle wurde erfolgreich geschrieben

Die Partitionstabelle wird erneut gelesen…
BLKRRPART: Device or resource busy
Der Befehl zum Neueinlesen der Partitionstabelle schlug fehl.
Starten Sie Ihr System jetzt neu, bevor Sie mkfs verwenden.

Wenn Sie eine DOS-Partition angelegt oder geändert haben, z. B. /dev/foo7,
dann nehmen Sie dd(1), um die ersten 512 Bytes auf 0 zu setzen:
„dd if=/dev/zero of=/dev/foo7 bs=512 count=1“ (siehe fdisk(8)).

```

Maybe I should switch Ubuntu to english from no on ;-)

But what does the sfdisk command really do? Repartition with the partition_table.txt and backup my old one?

So I'll do the live CD things rom now on :-)

greetings,
Johannes

---

### Post by miazma on 2009-01-11
Okay, it seems, it doesn't find a partition to boot... (I've executed the grub commands).

So I've appended RESULT.txt

---

### Post by caljohnsmith on 2009-01-11
Please post the contents of the RESULTS.txt file, for some reason they weren't included in your last post.

---

### Post by miazma on 2009-01-11
ok, but now ;-) see my post above :-)

---

### Post by caljohnsmith on 2009-01-11
Did the Grub commands complete successfully? If not, let me know (and please post the output), because it looks like that script had some problems executing. You will need to modify your menu.lst, so first do:
```
sudo mount /dev/sda2 /mnt
gksudo gedit /mnt/boot/grub/menu.lst
```
And change all the Ubuntu entries to use (hd0,1) instead of (hd0,5). Also change the "# groot=(hd0,5)" line to "# groot=(hd0,1)". In addition, it looks like your swap UUID in the fstab is incorrect, but before we modify that or any other necessary files, please post:
```
cat /mnt/etc/initramfs-tools/conf.d/resume
```
That should not prevent you from booting into Ubuntu though, so if installing Grub and modifying your menu.lst goes OK, go ahead and try booting Ubuntu again. We can go from there.

---

### Post by miazma on 2009-01-11
Now it's booting again, thank you :-)

I don't know if you still need the outputs from the grub commands (and fdisk, sfdisk -- same in RESULT.txt), but I've attached the file.

```

johannes@luna:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=6f5cac39-2461-4b69-b52d-c6c8ba28d12d

```

Now it's somehow strange that it still tries to mount the NTFS partition, which I've deleted some time ago with GParted (and resized my ext2 partitions)...

Also fsck dies with exit status 1 (which seems isn't really bad -- I've read the manpage, but it's strange because on my Live CD fsck finds no errors on both partitions and so doesn't need to correct them.

And somehow my system is really unstable (mh ok, I really can't work with it), but that's another problem I think.

---

### Post by caljohnsmith on 2009-01-11
Glad to hear Ubuntu is booting OK. :) It looks like at some point in the past your swap partition's UUID changed, because it currently doesn't match what is in your fstab or the resume file. To fix that should fortunately be easy, just do:
```
sudo swapoff -a
sudo mkswap -U "6f5cac39-2461-4b69-b52d-c6c8ba28d12d" /dev/sda3
sudo swapon -a
free
```
And please post the output of all the above commands. Next you could fix your fstab so that it doesn't attempt to mount the non-existent NTFS/FAT partitions:
```
gksudo gedit /etc/fstab
```
And edit it by deleting what is in red and changing what is highlighted in blue:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/[COLOR="Blue"]sda2[/COLOR]
UUID=850fd8a9-5012-45da-bef4-f47953e9edd4 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/[COLOR="Blue"]sda1[/COLOR]
UUID=7ba86bcf-6a33-48e3-9bd6-67f2d65b7355 /home           ext3    defaults,relatime        0       2
[COLOR="Red"]# /dev/sda1
UUID=36E4D14AE4D10CCD /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=E0A1-D6DC  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1[/COLOR]
# /dev/[COLOR="Blue"]sda3[/COLOR]
UUID=6f5cac39-2461-4b69-b52d-c6c8ba28d12d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```
Also, how is it you are running the fsck and getting an error message? Which exact command are you using, and which partition are you using it on?

---

### Post by miazma on 2009-01-11
That's a little bit strange (swapon -a):

```

johannes@luna:~$ sudo swapoff -a
johannes@luna:~$ sudo mkswap -U "6f5cac39-2461-4b69-b52d-c6c8ba28d12d" /dev/sda3
Setting up swapspace version 1, size = 1534108 KiB
kein Label, UUID=6f5cac39-2461-4b69-b52d-c6c8ba28d12d
johannes@luna:~$ sudo swapon -a
swapon: Konnte &#8222;stat&#8220; nicht auf /dev/disk/by-uuid/6f5cac39-2461-4b69-b52d-c6c8ba28d12d anwenden: No such file or directory
johannes@luna:~$ free
             total       used       free     shared    buffers     cached
Mem:       1015776    1005512      10264          0      37204     183512
-/+ buffers/cache:     784796     230980

```

Well, fsck isn't really running, but I can see these messages, when it's booting...

---

### Post by caljohnsmith on 2009-01-11
I think I see what happened; after changing the UUID of the swap partition to what it should be, that doesn't notify Ubuntu of the change, so Ubuntu still thinks the swap partition has the old UUID. You could fix it by simply rebooting, or this might also fix it:
```
sudo blkid -c /dev/null
sudo swapon -a
```
Let me know if that works or not.

---

### Post by miazma on 2009-01-11
Mh, strange, it doesn't work, but maybe I'll reboot ;-)

```

johannes@luna:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="7ba86bcf-6a33-48e3-9bd6-67f2d65b7355" TYPE="ext3" 
/dev/sda2: UUID="850fd8a9-5012-45da-bef4-f47953e9edd4" TYPE="ext3" 
/dev/sda3: UUID="6f5cac39-2461-4b69-b52d-c6c8ba28d12d" TYPE="swap" 
/dev/sdb1: LABEL="STORE N GO" UUID="2582-5FA3" TYPE="vfat" 
johannes@luna:~$ man blkid
johannes@luna:~$ sudo swapon -a
swapon: Konnte „stat“ nicht auf /dev/disk/by-uuid/6f5cac39-2461-4b69-b52d-c6c8ba28d12d anwenden: No such file or directory

```

---

### Post by caljohnsmith on 2009-01-11
So what happened after the reboot? If you do:
```
free
```
Does that show swap space? And how did modifying your fstab go?

---

### Post by miazma on 2009-01-11
Jep everything seems to be fine, thaaank you:

```

johannes@luna:~$ free
             total       used       free     shared    buffers     cached
Mem:       1015776    1005720      10056          0       5060     125328
-/+ buffers/cache:     875332     140444
Swap:      1534104     161480    1372624

```

As I'm booting I can't see the messages anymore, because now I see the progress bar... so I think there aren't any warnings or errors... but I've just enabled boot logging :-)

greetings and thanks,
Johannes

---

### Post by caljohnsmith on 2009-01-11
Glad to hear everything is working OK now. Cheers and have fun with your Ubuntu install. :)

---

