---
title: "ubuntu repositories"
date: 2009-09-20
forum: Installation &amp; Upgrades
---

### Post by muniek on 2009-09-20
Hi,

I was installed screenlets and try to use youtube module but it doesn't work.
I don't have Gtkmozembed. Where can I find repository with this package?
I looking for repository with this package and qt 4.5.2. 
Can you help mie?

I will be very grateful. 
muniek

---

### Post by stlsaint on 2009-09-20
do you have the universe/multiverse repos installed and set to receive updates.

---

### Post by muniek on 2009-09-21
Yes I have. 
This is my source.list:

```
## -------------------
## UBUNTU REPOSITORIES
## -------------------

## +++ Ubuntu 9.04 Jaunty (stable) +++
deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ jaunty-security main restricted universe multiverse

## +++ Backports & Proposed (not as stable) +++
deb http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-proposed main restricted universe multiverse

## +++ Source Repositories +++
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu/ jaunty-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-proposed main restricted universe multiverse

## ------------------
## OTHER REPOSITORIES
## ------------------

## +++ Canonical (stable) +++
deb http://archive.canonical.com/ubuntu/ jaunty partner

## +++ Medibuntu (stable) +++
#deb http://packages.medibuntu.org/ jaunty free non-free


#deb cdrom:[Ubuntu 8.10 _Jaunty Jackalope_ - Release i386 (20081029.1)]/ jaunty main restricted
# Zobacz http://help.ubuntu.com/community/UpgradeNotes jak zaktualizowa&#263;
# nowsz&#261; wersj&#281; dystrybujcji.

deb http://gb.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Uaktualnienia naprawiaj&#261;ce b&#322;&#281;dy wersji finalnej
## dystrybucji.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## Oprogramowanie z tych repozytoriów NIE JEST WSPIERANE przez Grup&#281;
## Ubuntu. Nale&#380;y równie&#380; pami&#281;ta&#263;, &#380;e oprogramowanie to NIE B&#280;DZIE
## sprawdzane przez twórców pod k&#261;tem bezpiecze&#324;stwa.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## Oprogramowanie z tych repozytoriów NIE JEST WSPIERANE przez Grup&#281;
## Ubuntu i mo&#380;e nie posiada&#263; licencji GPL. Nale&#380;y równie&#380; pami&#281;ta&#263;, 
## &#380;e oprogramowanie NIE B&#280;DZIE sprawdzane przez twórców pod k&#261;tem 
## zabezpiecze&#324;.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Poni&#380;sze dwie linijki zawieraj&#261; 'backporty'.
## Oprogramowanie mog&#322;o nie by&#263; testowane.
## Mog&#322;o nie by&#263; sprawdzane pod k&#261;tem zabezpiecze&#324;.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Oprogramowanie od 'partnerów' Canonical.
## Oprogramowanie to nie jest cz&#281;&#347;ci&#261; Ubuntu.
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner

#deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
#deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
#deb http://security.ubuntu.com/ubuntu jaunty-security universe
#deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
#deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
#deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse

## Medibuntu - Ubuntu 8.10 "jaunty jackalope"
deb http://packages.medibuntu.org/ jaunty free non-free
deb-src http://packages.medibuntu.org/ jaunty free non-free

## Repozytoria Google
deb http://dl.google.com/linux/deb/ stable non-fr
```

---

