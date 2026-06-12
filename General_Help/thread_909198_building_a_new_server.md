---
title: "building a new server"
date: 2008-09-03
forum: General Help
---

### Post by eppo on 2008-09-03
i'm going to be setting up a new home server. it will be serving media to my ps3 and my xbox. i'll also be using it for fileserving other stuff, and running multiple VM's.
i bought 5 500gig sata hdds. really what i want to do is be able to set up the raid before the install. i saw something that said i can do it in the server version of ubuntu. can i do the same with the regular 64bit version? i will also be using GUI from time to time, does X get set up in the server version or is it mainly for headless servers?
any help would be great.
thanks

---

### Post by cszikszoy on 2008-09-03
If you install from the server iso it will not install any desktop environment.  You can easily "fix" this though.

After the complete install of your server system, it will basically dump you out into the shell.  From here, just type: 

```
sudo apt-get install ubuntu-desktop
```

Which will install the full ubuntu desktop (and all associated applications).  You can then use your server like any other install of ubuntu.

Note that if you want other desktops replace "ubuntu-desktop" with whatever you prefer.

I think the other packages are:
```
sudo apt-get kubunut-desktop
sudo apt-get gobuntu-desktop
sudo apt-get xubuntu-desktop
sudo apt-get edubuntu-desktop
```

---

### Post by eppo on 2008-09-03
will both installs be able to install onto a software raid5?
my motherboard does do sata raid, but i've heard in the past linux software raid is better.

---

### Post by kpatz on 2008-09-03
I don't believe that you can boot from a software RAID (unless it's RAID 1).  But you could set up a small non-RAID or RAID1 partition that houses the root filesystem, or maybe just /boot, install the OS and then set up the RAID for your data.

---

### Post by eppo on 2008-09-03
hmm, i'll give that a try. given that i'm using 500gig hdds, i dont want to waste most of the drive i have the OS on, i want to include most of the space on my raid.

---

### Post by kpatz on 2008-09-03
I've been reading this:

[http://tldp.org/HOWTO/Software-RAID-HOWTO.html#toc5](http://tldp.org/HOWTO/Software-RAID-HOWTO.html#toc5)

and it looks like you can boot from a RAID5 array provided you set it up with a persistent superblock and autodetection.  You'll need to make sure that your kernel has RAID support compiled in (I'm not sure offhand if the Hardy kernel does or not, but it probably does).

---

### Post by cszikszoy on 2008-09-03
> **eppo said:**
> will both installs be able to install onto a software raid5?
my motherboard does do sata raid, but i've heard in the past linux software raid is better.


Hardware raid will always, always, always be better than software raid.  Actually, that goes for any other hardware vs software application.  Hardware is ALWAYS faster than hardware.

But, chances are your mother board doesn't actually do true hardware raid.  The sataraid that I have on my motherboard, I think it's a Silicon Image chip does raid 0,1 0+1 and 5 but I believe it's just  basically a software raid chip.  True hardware raid solutions are usually pretty expensive.  I think Marvell makes some "cheap" hardware raid PCI cards.  "Cheap" means about $200-300.

Do you know the name and model of the raid chip on your motherboard?

As I said earlier, the majority of these mother board raid chips are just sata controllers that use device drivers to emulate raid, and make you think that you have raid.  If this is the case, it might be easier to use native linux software raid, instead of trying to mess with the device drivers for your raid chip.

---

### Post by kpatz on 2008-09-03
One problem with hardware RAID is if your motherboard or RAID controller goes belly-up, you would have to replace it with an identical one to retain your array.  Software RAID will work even if the underlying hardware changes.

But, you should be backing up your data anyway, so as long as you have the backup, you can always rebuild the array.

---

### Post by WRDN on 2008-09-03
> **cszikszoy said:**
> If you install from the server iso it will not install any desktop environment.  You can easily "fix" this though.

After the complete install of your server system, it will basically dump you out into the shell.  From here, just type: 

```
sudo apt-get install ubuntu-desktop
```

Which will install the full ubuntu desktop (and all associated applications).  You can then use your server like any other install of ubuntu.

Note that if you want other desktops replace "ubuntu-desktop" with whatever you prefer.

I think the other packages are:
```
sudo apt-get kubunut-desktop
sudo apt-get gobuntu-desktop
sudo apt-get xubuntu-desktop
sudo apt-get edubuntu-desktop
```

I wouldn't recommend this. On a server, the user may rarely need a GUI, so it would be better to install the server edition, then a very lightweight window manager like [Fluxbox]("http://fluxbox.org/"). This can be installed with a single simple command:

```
sudo apt-get install fluxbox
```

This can then be started when needed. There is no point installing a "ubuntu-desktop" (etc) because it will contain loads of unneeded programs.

---

### Post by eppo on 2008-09-03
i'm using the  ASUS P5E-VM DO motherboard. i'm going to have about 2 terabytes of storage, how do you guys back that up? i am running raid5 so at least if 1 drive goes, i'll still be ok.

---

### Post by fjgaude on 2008-09-04
I do on-line backups to a single drive that can hold all the data, the same for near-line backups.

Backups are absolutely necessary even when using raid5. Data cannot be lost, period.

---

