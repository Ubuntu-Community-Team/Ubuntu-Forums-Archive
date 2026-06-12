---
title: "GRRR-After kernel compile, HDD is inaccessible!"
date: 2006-05-20
forum: Hardware &amp; Laptops
---

### Post by Lucho on 2006-05-20
](*,) ](*,) ](*,) ](*,) ](*,) 
Ok, after 5 (yes, five) attempts to compile a new kernel, I'm giving up if
I don't get any info here. Everything about the new kernel- using the
2.6.16.16 kernel source from Kernel.org -seems to work fine, and is
tangibly faster than the 2.6.12-10-amd64-k8 kernel I got from synaptic.
Not bad for the first kernel I compiled myself, EXCEPT  that my hda is
inaccessible! After five compiles, even using the configuration from the 
old kernel, this continues. The system says (in System administration =>
disks) that hda is present, all partitions are fine, but no enabling. At all.
Here are the stats:

AMD64 3400
1 GB RAM
Abit kv8 pro mobo
Nvidia NX 6200
             Hda:
                 hda1: jfs- root (Debian Etch :D) 
                 hda2: reiserfs -Debian Sid (old, I'll be erasing soon)
                 hda3: xfs- /home (Debian Etch :D)
                 hda4: reiserfs - misc. data
             Hdb:
(the installation with  the new kernel)==>hda1:reiserfs- Ubuntu 64-bit 5.10
                  hdb3: reiserfs-Ubuntu 6.06 32-bit Dapper Drake 
                  hdb5: swap
  So, I see two choices:
1) I know I'm still a noob; any number of mistakes are possible, but can someone
tell me WTF happened (or didn't)?
2) Is the solution to chalk it up to experience, and return to the 
2.6.12-10-amd64-k8  kernel, that plays nice with everything, even Nvidia?

    Thanks for being patient with yet another noob who can't compile the kernel
correctly. 
          PAZ

---

### Post by Lucho on 2006-05-21
Bump...

     It seems that I have my answer: don't stray from the path. Stick
to Synaptic.

---

### Post by sputnik.1956 on 2006-05-22
Hi,

As I understand you installed Debian on hda and Ubuntu on hdb? 

Compile the ReiserFS Filesystem into the kernel not as a module (or use a initrd) and XFS, JFS as a module.
Set your Boot Disk with your self compiled kernel in grub. E.g  /boot/vmlinuz-2.6.16.16 root=/dev/hdb1 ro 

Please post also post your /var/log/dmesg or the kernellog of /var/log/messages if it fails with your own kernel.

HTH

---

### Post by Lucho on 2006-05-22
yeah, Debian on hda, and Ubuntu on hdb. It just kind of happened;
distros were installed as space permitted (hda1 and hda4 used to be 
WinXP). My hard drives are disorganized :roll: 
         Actually, all of the distros use initrd; one of the things I noticed was
that Ubuntu compiled reiserfs as a module. It was one of the first things
I changed in the kernel. After the third compilation, I gave up and left the 
original configuration because it didn't seem to make any difference :confused: 
         Boot disk? Grub is installed in Etch; to boot into the new kernel, I
first boot into Etch, configure grub accordingly, and then boot into the new
Breezy. If (when) it's a no-go, I reboot into Etch, reconfigure grub, reboot into
the old Breezy, etc... Is the lack of a boot disk a factor? 
     I'll get the /var/log/dmesg, I'll have to reset grub for the misbehaving kernel;
I had to put the old one so my girlfriend could work (she doesn't trust Debian).
I'll put it up ASAP.
     Thanks

---

### Post by sputnik.1956 on 2006-05-23
Ahh,

I understand you boot your systems out of Debian Etch. So you must make your changes in grub of Etch. You can change this later if you want boot Etch out of Ubuntus Grub. Have a look at following link: 

[http://www.faqs.org/docs/Linux-mini/Multiboot-with-GRUB.html](http://www.faqs.org/docs/Linux-mini/Multiboot-with-GRUB.html)

HTH

---

### Post by Lucho on 2006-05-23
Sorry for the delay, I got caught without Internet  (crappy provider
crashed last night ](*,) ). Here's the dmesg file- If I read it right, though
the problem must be with Grub. Dmesg seems to working as it should.
        I'm reading the link, but it seems to say more or less what I'm
already doing- except that I use grubconf (in Etch though; I never even
installed grub in Ubuntu).

---

### Post by sputnik.1956 on 2006-05-24
Ok now it is everything clear

If you install grub also on Ubuntu (hdb) then you could boot your system out of Ubuntu and you have the ability to choose Debian/Etch and Windows (if you have) in the menu. Otherwise you must always set your Ubuntu Kernel in Debian Etch which will not get easy over a long period if you compile and test a lot of kernels (e.g. Kernel from kernel.org, the git tree or the MM kernels). However it is up to you what you would like to do. However you partition layout is interesting :-).

---

### Post by Lucho on 2006-05-25
Sorry for the delay in replying; my provider decided to crash and burn. I
passed the last 36 hour without internet- my girlfriend in particular was not
pleased to lose internet on the eve of finals...
     Interesting? My partition layout is a jumbled mess ;)  But seriously,
I'm thinking of erasing Sid to move Breezy 64 to hda, esp. since the combo
JFS/root and XFS/home seems to have made a noticable difference- Etch
is *fast*! Then again, maybe it seems so because I edit and encode DVDs
and other gargantuan files (XFS territory).
     Installing Grub to hdb is a good idea, but this is a good incentive to 
organize my partitions. Either way, thanks for the help.
         PAZ

---

