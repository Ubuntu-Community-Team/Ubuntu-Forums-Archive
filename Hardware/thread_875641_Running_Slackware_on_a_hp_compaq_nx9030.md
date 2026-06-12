---
title: "Running Slackware on a hp compaq nx9030"
date: 2008-07-31
forum: Hardware
---

### Post by SZF2001 on 2008-07-31
So I'm ready to move on to bigger nd better things (not being rude, honestly) and ubuntu just seems too slow for my laptop. I've *heard* that Slackware is quicker and all around more customizable.

A few questions;

1 - How does Slackware handle wireless internet? I've heard it comes with KWifiManager but will I need to be editing files to get WPA and other types of passwords in?

1a - Is there a network program like in ubuntu (I think it's network-something) that can make connecting wirelessly easier?

2 - Does Slackware have a big repository? Or will I need to be searching for all my RPMs and building by source? Does Slackware use RPMs or deb files? Does Slackware have apt-get, or use yum...?

3 - This latest Slackware should have the latest kernel, yes? So it should work with my wireless card thats in my nx9030?

---

### Post by mikjp on 2008-07-31
You should consider reading [Slackware book]( http://www.slackbook.org/). In Slackware you basically configure everything by editing text files.

Slackware does not use debs or rpms. It uses tgz packages, and does not have out of the box any support for dependency handling.  You can, however, install programs like slapt-get or swaret to handle your dependencies. [Linuxpackages.net](http://www.linuxpackages.net/) is the place to look for Slackware packages.

If you want to upgrade an existing installation, you always do a fresh installation.

Slackware is famous for not including the latest kernels and desktop environments. Slackware prefers stability over latest software. In fact, some might think Slackware uses obsolete software. For example, it used kernels of series 2.4 when the rest of the world had been using 2.6 for ages. AFAIK, even nowadays it uses lilo instead of grub.

Slackware is pretty much plain vanilla. It leaves you in full control of everything. If you want chocolade or strawberries, you either add them yourself or decide for another distro :-)

Slackware is a great distro. It might be good for you, or it might not be your choice.

Greetings,

mikko

---

