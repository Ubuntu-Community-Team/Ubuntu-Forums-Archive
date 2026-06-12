---
title: "I thought this wasn't possible......."
date: 2009-01-10
forum: Installation &amp; Upgrades
---

### Post by grey-radio on 2009-01-10
Well, a while ago my ex and i threw together some old parts to get a pc running.

WELL, she needed her WoW..... cause she's lame.

And i needed my Linux.... cause im awesome (^_^)

Anywho, on point here.

It was the first time i've dual booted.

and i knew windows first, linux distro second.  otherwise windows gay *** will overwrite grub with its MBR.

Well, when installing these OS's  i seperated the drive down the middle.

she told me it was a 40gb drive.  so i allocated windows 20, and myself 20.

turns out its an 80gb drive.  

Now, i know this isn't suppossed to be possible.

but i have ubuntu installed on an NTFS file system.

and its running like hellen keller on a hefty dose of lysergic acid.

I'm already planning on just backing up stuff on an FTP and re partitioning.

but im a little stuck.

i just want to make sure i do this right.

so, i boot gparted live

i should...

decrease the size of the NTFS partition to basically nothing  (i want to keep this windows copy because its free ya know.)

and then i should just make the rest of the space ext2 or 3

but what about that old installation of ubuntu....

how do i get rid of that....

im gonna have to just reformat totally aren't i...


crap.

nvm.

---

### Post by avtolle on 2009-01-10
You don't need to totally reformat the drive; just the partition that Ubuntu is on.

---

### Post by chex_m8 on 2009-01-10
real quick can we get the output of  "sudo fdisk -l"     ,thanks. Can you also be a little more clear about what it is you want?
side note : -l is a lower case L not a # 1

---

