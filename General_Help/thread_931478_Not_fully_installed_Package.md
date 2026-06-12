---
title: "Not fully installed Package"
date: 2008-09-27
forum: General Help
---

### Post by chris.tkd on 2008-09-27
Hello, When i do a sudo apt-get upgrade, I get a message 2 not fully installed or removed. The program in question works perfectly, Is it possible to remove these from aptitudes "to-do" list?

---

### Post by Atsuko on 2008-09-27
[B]APT HOWTO
Chapter 7 - How to deal with errors [/B]

[http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html)

Have a read there .

---

### Post by chris.tkd on 2008-09-27
That page dosnt load, is the link correct?

---

### Post by kokkus on 2008-09-27
I know at least 2 ways to fix this problems.

The clever way - you can figure out which package(s) are causing the problem and resolve the conflict, thereby breaking the logjam. This may be time-consuming. Start by comparing the output between the following two commands to get clues:
Code:

sudo apt-get -sv dist-upgrade
sudo apt-get -sv dselect-upgrade

The brute force way - install one of the meta-packages and upgrade.
Code:

sudo apt-get install ubuntu-desktop && sudo apt-get dist-upgrade

Since your system is probably customized (you removed a meta-package, for example) this approach might undo some of your customization, and might break any specialty packages or .debs that were relying on specific dependencies that you just upgraded from.

I would use method 1 since that's the controlled way to do this.
It takes forever to install every single system package again. At least if your internet speed it unstabile or slow.

---

### Post by kokkus on 2008-09-27
Method 2 should be done from terminal session.

Good Luck:)

---

