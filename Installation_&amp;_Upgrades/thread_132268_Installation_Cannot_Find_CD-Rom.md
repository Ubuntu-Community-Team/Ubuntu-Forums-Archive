---
title: "Installation Cannot Find CD-Rom"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by ajcoon on 2006-02-18
Hello,

I'm already running Breezy on two other computers provided by my employer, and now I'd like to install it on one of my own at home.  I have a relatively new Dell system, purchased in the last six months.  It's a Dimension E510.  The basic specs are:

Intel P4 3.0 GHz HT
1GB RAM
SATA Hard Drive (Maxtor 6L160M0)
PATA (IDE) DVD+/-RW (Philips DVD8701)

So I get to the point of the installation where it's let me select my language and keyboard settings, and after that it tries to detect the CD-ROM and then scans it.  As soon as it says "Loading additional components: Retreiving libc6-udeb" it goes to another screen that says "There was a problem reading data from the CD-ROM..."

I checked the integrity of the disc and it says it was successful.  So that confuses me...

I got ambitious and went to the tty at Ctrl+Alt+F2 and started reading /var/log/syslog.  I ran across this (save the timestamps, etc.):

ATA:  abnormal status 0x7F on port 0xFE27
ata2: disabling port

I'm not sure if this is of significance to my problem or not...but I thought I'd throw it out there in case it is.

If anyone could help me get the Breezy installation working I would appreciate it.  I'm not a kernel hacker, but I'm a programmer and I've been using Linux for development and application server platforms for years now.  If you need me to dig deeper, bring it on.  Installation of software is something I guess I take for granted...help!!!

---

### Post by emperor on 2006-02-18
The kernel option "ide=nodma" would probably fix the problem but I understand that this option does not work in Breezy but is fixed in Drapper. So you might want to install a Drapper preview instead.

---

### Post by ajcoon on 2006-02-18
[QUOTE=emperor]The kernel option "ide=nodma" would probably fix the problem but I understand that this option does not work in Breezy but is fixed in Drapper. So you might want to install a Drapper preview instead.[/QUOTE]

I actually did try this in one particular attempt.  I also tried:

- expert mode
- a different cd

Any other ideas would be appreciated.

So, if I were to get Drapper, how new is that?  Do I really want to install it before it's released officially?

---

### Post by emperor on 2006-02-21
There are some people using Drapper already. It will be released in April.

---

