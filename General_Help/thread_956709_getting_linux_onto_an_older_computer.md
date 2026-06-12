---
title: "getting linux onto an older computer"
date: 2008-10-23
forum: General Help
---

### Post by hockeyhead019 on 2008-10-23
ok guys so i have an old deskpro from compaq in my attic and i was wondering if any of these linux distos would load up on it... it's got a pentium 2 and i really don't know too much else about it haha... i'm trying to get my ubuntu live cd to load up but i have to set the machine up first haha... and will it be too old to run the ubunu? i'll look up anymore info if you need it thanks

---

### Post by scragar on 2008-10-23
If it's old I would go for a small distribution like puppy or DSL(which is about 50MB in size).

---

### Post by kartoshka on 2008-10-23
CPU speed, amount of RAM, HDD capacity?

Check [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements). If your desktop is powerful enough, you may be able to us the Live CD to install, otherwise you'll have to use the text-based installer.

---

### Post by zvacet on 2008-10-23
How much ram do you have and how many free space on HD?You can try [Xubuntu]("http://www.xubuntu.org/get") alternate or [DSL]("http://www.damnsmalllinux.org/") and [Puppy]("http://www.puppylinux.com/").

---

### Post by snowpine on 2008-10-23
The odds are unlikely that Ubuntu would give you good performance on a pentium 2-era computer.  However, there are lots of other Linux "distros" that have more modest hardware requirements. This thread is the mother-lode: [http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

Good luck!

---

### Post by ju2wheels on 2008-10-23
Requirements: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

You should be able to, I have it installed on an 800mhz laptop with around 256mb of ram, I used Xubuntu however, which I would recommend over vanilla Ubuntu if your computer is slow. Also consider alternative distributions which are optimized or designed for slow machines like Damn Small Linux, which you can also configure to use APT and get access to the regular Debian repositories.

[Edit] Wow people are fast, sorry, my information was the same as those who beat me to the post lol.

---

### Post by hockeyhead019 on 2008-10-23
ok well i'll check the specs when i get home but as for the lighter distro's what are the advantages/disadvantages of them?

ps thanks for all the quick answers

---

### Post by snowpine on 2008-10-23
> **hockeyhead019 said:**
> ok well i'll check the specs when i get home but as for the lighter distro's what are the advantages/disadvantages of them?

ps thanks for all the quick answers

Advantages to lighter distros: They work on older hardware.
Disadvantages: They can't turn old hardware into new hardware. :)

Serious answer: Lighter distros tend to be less full featured, don't necessarily give you the latest and greatest, and may require more text/command line interface to configure things. They tend to give you the basic tools you need (web browser, file manager, text editor, etc) rather than everything you may necessarily *want*.

---

### Post by Calmatory on 2008-10-23
Ubuntu will NOT work. Xubuntu MAY work, slowly. This is due to the limited amount of RAM. It probably has 32 MB, 64 MB at most, unless someone has upgraded the RAM.

Using Arch Linux and a lightweight window manager like Fluxbox could possibly be usabe with that low amount of RAM.

I've used a similar machine, 333 MHz Celeron with 256 MB, later 448 MB and then 512 MB of RAM. It was slow due to the programs I used, not due to the distro itself. E.g there is no way to watch youtube videos without stuttering. Neither can VLC play videos without stuttering. These are program-specific and the distro does not play a big role. Old hardware, it's old, slow and obsolete.

---

### Post by Iowan on 2008-10-23
I've got some pretty old machines running as servers (Vectra VL5/200)... my router is a '486, but all my servers are CLI-only.

---

### Post by mikjp on 2008-10-25
I tried to use Xubuntu on an HP-vectra 1 GHz. First I thought it was OK, but it really wasn't. No I'm happily using Vector Linux on it. Works like a charm!

See my blog for more info about lightweight linux distributions.

---

