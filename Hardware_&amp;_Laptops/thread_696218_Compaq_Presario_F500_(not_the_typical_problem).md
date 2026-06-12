---
title: "Compaq Presario F500 (not the typical problem?)"
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by Aktariel on 2008-02-13
I am reinstalling Ubuntu 7.10 on a friends Compaq Presario F500 laptop after their hard drive crashed data unrecoverable and they had it replaced. When it was still working, it had been running 7.10 exclusively, with no problems (blew them away - they loved it so much more than vista, especially on a lower end laptop.)

The problem that I am running into is I think related to the graphics/irqpoll/apic problems posted [here,]("http://cro.alienpants.com/index.php/2007/05/05/getting-ubuntu-running-on-my-compaq-f500") [ here, ]("http://ubuntuforums.org/showthread.php?t=504255") [here,]("http://ubuntuforums.org/showthread.php?t=545976") and [here.]("http://justindow.com/")

I've tried booting noapic, nolapic, nosmp, irqpoll, vga=792, vga=771, and all different combinations thereof. Originally, it would hang at the ubuntu load visual (the bouncing orange bar), but with nosmp and irqpoll it gets all the way through that and then displays a blinking cursor in the upper left corner. Also, it intermittently (haven't been paying real close attention) kicks up a PCI BIOS #81 error, but boots anyway.

I know this works; they've had it running before. It's so frustrating. I do remember having to append the boot configuration file; I just can't remember what I appended.

Can anyone help me out or throw some suggestions my way? Much appreciated!

---

### Post by AlbertRetro on 2008-03-07
[http://h10061.www1.hp.com/ccsearch/search?pname=Compaq+Presario+F545EA+Notebook+PC&opname=Compaq+Presario+F545EA+Notebook+PC&qry=PRESARIO+F500&submit.x=10&submit.y=8&method=prodFinder&ctry=pl&lang=en&dlc=en&sni=3352153&search=0](http://h10061.www1.hp.com/ccsearch/search?pname=Compaq+Presario+F545EA+Notebook+PC&opname=Compaq+Presario+F545EA+Notebook+PC&qry=PRESARIO+F500&submit.x=10&submit.y=8&method=prodFinder&ctry=pl&lang=en&dlc=en&sni=3352153&search=0)
Checked your Bios-update soon...

---

### Post by zerobravo on 2008-03-20
Hi,

I have the Compaq Presario F500 (F503AU) 

I upgraded BIOS to F.1F from within Windows XP using the HP Winflash

I booted with Ubuntu (AMD64) Live CD 7.10

Had to press F6 for other options and add 

vga=792 noapic nolapic

to the end of the string wouldn't boot to the live cd another way.

This was the only way i could get Live CD to boot and then be able to install.

I also had to have a Lan cable plugged in during the install process....as at the end it failed once when looking for security updates.

I am now using the following as a guide to get wireless to work.

[http://cro.alienpants.com/index.php/2007/05/05/getting-ubuntu-running-on-my-compaq-f500/]("http://cro.alienpants.com/index.php/2007/05/05/getting-ubuntu-running-on-my-compaq-f500/")

---

