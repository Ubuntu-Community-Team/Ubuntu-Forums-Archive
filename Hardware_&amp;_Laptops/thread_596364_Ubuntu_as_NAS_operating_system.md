---
title: "Ubuntu as NAS operating system"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by azelter on 2007-10-29
Has anyone had much experience with running NAS devices as more full featured servers?
I am looking to replace an old pc that I use as an http/ssh/music/print server with something smaller and less power hungry.
I have been looking at the SLUG ([http://www.nslu2-linux.org/](http://www.nslu2-linux.org/)) from Linksys, which appears to be able to run debian, however, I have come to the conclusion I would be better off with something that has abit more power. For example, I know a slug can run gallery2/mysql/apache and ssh, but it will struggle when I put backuppc on it and anyway it is rather underpowered to be asking so much from it. I also want to run a slimserver if I can.
There seem to be a lot of more powerful devices on the market (e.g. the QNAP TS-209, the netgear ReadyNAS NV+). All these devices run their own version of linux as standard, but most don't have alot of info that I can find for installing a more generic version (like debian or ubuntu). Whatever device I buy I'm guessing I'd want to wipe and put something like ubuntu on as the provided os's that come installed generally don't take full advantage of the hardware but are built to be nice network storage/backup devices. I like the idea of being able to run what ever I like.
Suggestions?
Thanks!

---

### Post by pieisgood4589 on 2007-10-29
LOL, NAS? That'll never run Ubuntu.:guitar:

---

### Post by yopnono on 2007-10-29
I have had 2 SLUG and they are crap truly crap. Dropping network corrupting files over network copy etc,etc...

---

### Post by ddrichardson on 2007-10-29
I can't really see any advantage in what you're proposing. Embedded Linux versions are stripped to the necessary, especially the kernel. You are asking quite a lot of most any server to run that many services, whilst considering increasing overheads with unnecessary kernel modules.

If power is a consideration and you want a number of services beyond the realm on NAS, then personally I'd consider an Epia based solution.

---

### Post by andyfromtucson on 2007-10-29
If your goal is simply to have a smaller and less power hungry server you should consider an old laptop.  I got an old (circa 2001) laptop from a neighbor for free and installed the command line version of Ubuntu from the alternate CD (the laptop didn't have enough memory to handle the Gnome desktop).  It works great running SSH/Apache/MySQL etc, and if I turn off the screen and  backlight  it pulls like 13 watts or so according to my  Kill-A-Watt meter. Hard to beat $0 and 13 watts for a home server.

---

### Post by azelter on 2007-11-02
Probably right. A laptop may be the way forward. thanks for the comments.

---

### Post by toma222 on 2007-11-02
Hi,
I have a SLUG, I use it as a wireless to ethernet gateway, printer server and some over little things and I'm very happy with it.

Most NAS uses ARM architecture, that's mean you can't use Ubuntu on it (only Debian, Gentoo and some other special distributions).

It's not very powerfull (only 266 MHz and 32 Mb of RAM) but it's noiselesss and it doesn't consume lots of power (only 6W I think).

---

