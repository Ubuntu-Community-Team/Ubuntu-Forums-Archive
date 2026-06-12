---
title: "FireFox Error"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by emoguitarist06 on 2009-10-09
**I ran this in the terminal:**
*sudo apt-get update && sudo apt-get upgrade*

**and it told me:**
[I]The following packages will be upgraded:
  firefox firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support
  firefox-gnome-support xulrunner-1.9.1 xulrunner-1.9.1-gnome-support[/I]

**and at the end I got.**

[I]Error: #include <abstractions/private-files> not found at line 84 in /etc/apparmor.d/usr.bin.firefox-3.5.
Error: #include <abstractions/ubuntu-email> not found at line 177 in /etc/apparmor.d/usr.bin.firefox-3.5.
Error: #include <abstractions/ubuntu-console-email> not found at line 178 in /etc/apparmor.d/usr.bin.firefox-3.5.
Error: #include <abstractions/ubuntu-gnome-terminal> not found at line 182 in /etc/apparmor.d/usr.bin.firefox-3.5.
Please restart all running instances of firefox-3.5, or you will experience problems.

Setting up firefox-3.5-gnome-support (3.5.5~hg20091008r26464+nobinonly-0ubuntu1~umd1~jaunty) ...

Setting up firefox (3.5.5~hg20091008r26464+nobinonly-0ubuntu1~umd1~jaunty) ...
Setting up firefox-gnome-support (3.5.5~hg20091008r26464+nobinonly-0ubuntu1~umd1~jaunty) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place[/I]


**Did I make a mistake? is something wrong? Of course I DIDN'T have firefox running while upgrading**
Running Ubuntu 9.04

---

### Post by rippin on 2009-10-09
> **emoguitarist06 said:**
> **I ran this in the terminal:**
*sudo apt-get update && sudo apt-get upgrade*

**and it told me:**
[I]The following packages will be upgraded:
  firefox firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support
  firefox-gnome-support xulrunner-1.9.1 xulrunner-1.9.1-gnome-support[/I]

**and at the end I got.**

[I]Error: #include <abstractions/private-files> not found at line 84 in /etc/apparmor.d/usr.bin.firefox-3.5.
Error: #include <abstractions/ubuntu-email> not found at line 177 in /etc/apparmor.d/usr.bin.firefox-3.5.
Error: #include <abstractions/ubuntu-console-email> not found at line 178 in /etc/apparmor.d/usr.bin.firefox-3.5.
Error: #include <abstractions/ubuntu-gnome-terminal> not found at line 182 in /etc/apparmor.d/usr.bin.firefox-3.5.
Please restart all running instances of firefox-3.5, or you will experience problems.

Setting up firefox-3.5-gnome-support (3.5.5~hg20091008r26464+nobinonly-0ubuntu1~umd1~jaunty) ...

Setting up firefox (3.5.5~hg20091008r26464+nobinonly-0ubuntu1~umd1~jaunty) ...
Setting up firefox-gnome-support (3.5.5~hg20091008r26464+nobinonly-0ubuntu1~umd1~jaunty) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place[/I]


**Did I make a mistake? is something wrong? Of course I DIDN'T have firefox running while upgrading**
Running Ubuntu 9.04

Maybe there was an instance of FF bin running in the background and you were unaware of it - a crashed instance that would have shown in 'top'. Have you  tried **sudo apt-get update && sudo apt-get upgrade*** again? BTW, FWIW, I removed **apparmor without hazard.*

---

