---
title: "Update a &quot;dual-boot&quot; laptop"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by knguyen144 on 2009-01-02
Hi,

I have a laptop with dual-boot setup for Ubuntu Linux and Window XP.
Now I wish to upgrade from Window XP to Window Vista. Does anyone know anything I need to pay attention during this process ?
I assumed that I need to follow the Micrsoft's instruction to upgrade and/or clean install New Window Vista on NTFS logical volume, then edit file "/boot/grub/menu.lst" to change the line "Microsoft Windows XP Home Edition" to  "Windows Vista Home Premium" ?

So far, I have a good and healthy dual-boot system, expecially the Ubuntu Linux. I hope to keep it this way.

Any suggestion/warning is greatly appreciated.

KN

---

### Post by itix on 2009-01-03
Microsoft Windows will eat your bootloader when you install windows. Therefor you will not be able to boot into Ubuntu after the install. To fix this, you will need something called the super grub disc.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Just donwload and burn that disc. After the windows install, just load the CD and it will restore your bootloader and Ubuntu with it.

And here comes a sh*tload of my personal opinions; why the hell would you want to install Vista over XP?? It is slow as hell, unstable as hell, crashes a lot, it is hard to navigate in, it supports almost nothinng properly etc, etc.

You will NOT gain any functionality by installing Vista, so why would you? It is above else slow. A zip-file of about 100 Mbs takes 12 minutes to unzip on my sisters Vista machine (and about 10 sec on my ubuntu machines). It is ridiculously slow. It really redefines the term snail pace.

The only reason to install Vista is because it supports better hardware than XP, and we're talking quite heavy hardware such as +4 Gbs Memory, Quadcore+ (i.e Octacore, Hexadecacore) etc.

---

### Post by logos34 on 2009-01-03
As Itix said, Windows will overwrite the MBR with it's own bootloader, so you will need to restore Grub.  But you don't even need the SGD--you can do it from the Ubuntu Live cd (see link in my signature).   OTH, being a dual-booter you probably should have a copy of SGD on hand--handy tool.

But I don't think you'll need to change the windows boot entry in menu.lst (i.e the 'root' line) if you're merely installing vista on the same partition over the existing XP.

---

