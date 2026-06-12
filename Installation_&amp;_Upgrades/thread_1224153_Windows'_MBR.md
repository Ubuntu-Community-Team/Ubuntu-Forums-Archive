---
title: "Windows' MBR"
date: 2009-07-27
forum: Installation &amp; Upgrades
---

### Post by Tender Prey on 2009-07-27
Hallo,

I want to unistall Ubuntu 9.04 (since i made some mistake in installing it so that i want to installit from the begininning). I understood the first of all i have to restore the Windows' MBR. So i tried to proceed in this way: 

1- I  run an Ubuntu Live Version from CD
2- Run the terminal windows and then write
     a - wget [http://ftp.de.debian.org/debian/pool/main/m/ms-sys/ms- sys_2.1.0-1_i386.deb]("http://ftp.de.debian.org/debian/pool/main/m/ms-sys/ms-sys_2.1.0-1_i386.deb")
     b - sudo dpkg -i ms-sys_2.1.0-1_i386.deb

3- agin 
    sudo fdisk -l  and I get :

    Disco /dev/sda: 60.0 GB, 60011642880 byte
    255 testine, 63 settori/tracce, 7296 cilindri
    Unità = cilindri di 16065 * 512 = 8225280 byte
    Identificativo disco: 0x66d766d7

   Dispositivo Boot      Start         End      Blocks   Id  System
   /dev/sda1   *           1        6944    55777648+   7  HPFS/NTFS
   /dev/sda2            6945        7270     2618595    f  W95 Esteso (LBA)
   /dev/sda4            7271        7296      208845   88  Linux plaintext
   /dev/sda5            6945        7248     2441848+  83  Linux
   /dev/sda6            7249        7270      176683+  82  Linux swap / Solaris

4- i try this: sudo ms-sys -w /dev/sda1 and i get:
    /dev/sda1 has an x86 boot sector, it is an unknown boot record

5- then i try this one: sudo ms-sys -m /dev/sda1 and i get
   /dev/sda1 seems to be a disk partition device, use the switch -f to force writing of a master boot record

Well, before i commit a "dangerous" mistake, someone, please, could tell me what to do to restore Windows' MBR and then to remove Ubuntu from my PC?
Many thanks

---

### Post by moster on 2009-07-27
I do not know why people have so much problems with boot. Specially when have only one HDD.

I never had to tell ubuntu anything about boot and everything went just fine. I had vista/xp on first partition, linux on second. I do not really understand your 6 partitions.

Usually 1 partition is windows ntfs and boot, second and third is linux and installation by default put grub boot loader on first and everything is just fine.

Rule is if you get screwed and you want windows back, load windows installation from cd, select recovery and type "fixmbr". that should do. and if not type "fixboot". Last option is to get [Hirens]("http://www.hiren.info/pages/bootcd") boot cd, there are load of tools for that there.

If I were you and starting fresh. My partitions would look like this and you would not have any problem and do not have to tweak anything. Just install ubuntu second and do not alter his boot preference.

First install vista/xp
1. vista/xp (boot partition)
2. vista/xp data partition
3. ubuntu
4. swap

---

### Post by Tender Prey on 2009-07-27
Hi,
first of all thanks for your answer.
I agree with you, I don't understand my 6 partition, the only problem is that I did nothing to create them! I just put the installation CD for Ubuntu 9.04 and this is what I got! Don't ask me more!
About windows cd...unfortunately I lost the CD during my removal!!!!! Now I'm in trouble!

---

### Post by moster on 2009-07-27
I just do not dare to tell you what to do. I might screw your partitions.

You need some bigger expert then me who can operate from this. Your sda4 and sda5 confuse me, I do not know is it you system, home or what... I can now only suggest what you should do in future when you eventually get this right. Or you can everything backup on external disk and make it right this time.

Lets just say you have clean disk. You would install xp on first partition and make maybe on more for data. Then load Ubuntu and in setup select "manual partitioning" then make another partition there and set mount point "/". and another partition for linux data too. At last give swap partition. 

Ubuntu will automatically make dual boot. When you next time screw ubuntu and need reistalation just format that first ubuntu partition you mount as "/". Not touch anything else, and everything will be just fine.

It should look something like this
[http://www.serenux.com/~hyrax/snaps/UbuntuJauntyManuallyPartition2.png]("http://www.serenux.com/~hyrax/snaps/UbuntuJauntyManuallyPartition2.png")

edit:
In short. In your situation now, you need to find out on what partition you install linux, then load ubuntu setup, and in manual partitioning format that partition and make it mount point "/". Everything else will be fine.

---

### Post by Tender Prey on 2009-07-27
Thaks Monster. I really want to solve my problem and find the right way to install Ubuntu next time. I will follow your suggestions. I hope to solve my problem as soon as possible since i'd like to discover Linux world.
Ciao

---

