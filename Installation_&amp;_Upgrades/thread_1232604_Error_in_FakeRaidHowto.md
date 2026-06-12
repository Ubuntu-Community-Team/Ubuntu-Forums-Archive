---
title: "Error in FakeRaidHowto"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by Flapse on 2009-08-05
Hello!

While trying to install Ubuntu on my raid configured computer with the guide [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) an error occured in step number 9. L) iii. (the grub prompt)
As Im typing in the command, the terminals states that "Uknown partition table signature" "Error 15 file not found"

Anyone's got any idea whats going on? 


This is what it looks like in my terminal, anyway.
> 
ubuntu@ubuntu:~$ sudo mount /dev/mapper/isw_bghcfjbicb_Volume031
mount: can't find /dev/mapper/isw_bghcfjbicb_Volume031 in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$ sudo mount /dev/mapper/isw_bghcfjbicb_Volume03
mount: /dev/mapper/isw_bghcfjbicb_Volume03 already mounted or /target busy
mount: according to mtab, /dev/mapper/isw_bghcfjbicb_Volume03 is already mounted on /target
ubuntu@ubuntu:~$ sudo mount --bind /dev /target/dev/
ubuntu@ubuntu:~$ sudo mount -t proc proc /target/proc/
mount: proc already mounted or /target/proc/ busy
mount: according to mtab, proc is already mounted on /target/proc
ubuntu@ubuntu:~$ sudo mount -t sysfs sys /target/sys/
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /target/etc/resolv.conf 
ubuntu@ubuntu:~$ sudo chroot /target/
root@ubuntu:/# apt-get update 
Bra [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty Release.gpg
Ign [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty/main Translation-sv_SE
Ign [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty/restricted Translation-sv_SE
Ign [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty/universe Translation-sv_SE
Ign [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty/multiverse Translation-sv_SE
Bra [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty-updates Release.gpg
Ign [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty-updates/main Translation-sv_SE
Ign [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty-updates/restricted Translation-sv_SE
Bra [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security Release.gpg
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/main Translation-sv_SE
Ign [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty-updates/universe Translation-sv_SE
Ign [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty-updates/multiverse Translation-sv_SE
Bra [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty Release
Bra [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty-updates Release             
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/restricted Translation-sv_SE
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/universe Translation-sv_SE
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/multiverse Translation-sv_SE
Bra [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security Release
Bra [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty/main Packages
Bra [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty/restricted Packages
Bra [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty/main Sources
Bra [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty/restricted Sources
Bra [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty/universe Packages
Bra [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty/universe Sources
Bra [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty/multiverse Packages
Bra [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty/multiverse Sources
Bra [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty-updates/main Packages
Bra [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty-updates/restricted Packages
Bra [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty-updates/main Sources
Bra [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty-updates/restricted Sources
Bra [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/main Packages
Bra [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty-updates/universe Packages
Bra [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty-updates/universe Sources
Bra [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty-updates/multiverse Packages
Bra [http://se.archive.ubuntu.com]("http://se.archive.ubuntu.com/") jaunty-updates/multiverse Sources
Bra [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/restricted Packages
Bra [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/main Sources
Bra [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/restricted Sources
Bra [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/universe Packages
Bra [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/universe Sources
Bra [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/multiverse Packages
Bra [http://security.ubuntu.com]("http://security.ubuntu.com/") jaunty-security/multiverse Sources
Läser paketlistor... Färdig
root@ubuntu:/# apt-get install -y dmraid
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
dmraid är redan den senaste versionen.
0 att uppgradera, 0 att nyinstallera, 0 att ta bort och 184 att inte uppgradera.
root@ubuntu:/# apt-get install -y grub
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
grub är redan den senaste versionen.
0 att uppgradera, 0 att nyinstallera, 0 att ta bort och 184 att inte uppgradera.
root@ubuntu:/# mkdir /boot/grub
mkdir: kan inte skapa katalog "/boot/grub": Filen existerar
root@ubuntu:/# cp /usr/lib/grub/x86_64-pc/* /boot/grub/
root@ubuntu:/# grub --no-curses
Probing devices to guess BIOS drives. This may take a long time.
Unknown partition table signature
Unknown partition table signature

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> device (hd0) /dev/mapper/isw_bghcfjbicb_Volume03
device (hd0) /dev/mapper/isw_bghcfjbicb_Volume03
grub> find /boot/grub/stage1 
find /boot/grub/stage1
Unknown partition table signature

Error 15: File not found
grub> 
Really appriciate any help, thanks!

---

### Post by Flapse on 2009-08-05
double post..

---

### Post by Flapse on 2009-08-06
bump :(

---

