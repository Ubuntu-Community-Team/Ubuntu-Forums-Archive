---
title: "Problem upgrading to Jaunty-can't reach login screen (with photo)"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by evans5000 on 2009-04-25
Hello,

Am currently logged via an 8.04 (HH) Live CD as have run into a problem.

I ran the upgrade from 8.10 to Jaunty 9.04 this morning using upgrade manager. Ubuntu has been working fine up until then. I'd successfully upgraded Hardy to Intrepid a few weeks back, so I thought I'd have a crack at upgrading Hardy to Jaunty. Things went a bit wrong when I rebooted at the end of the upgrade process.  Ever since then:

-The new Ubuntu logo screen comes up, with the moving bar. It then freezes, moves a little way along and then this happens- 

[http://f.imagehost.org/view/0384/1240651646]("http://f.imagehost.org/view/0384/1240651646")

As you can see it's throwing up a lot of errors, such as 'bus error', 'dbus error', it's trying to start system log daemon, but will spool out  dbus/bus/ata errors information, eventually ending with a red 'fail' message.
(Also does this while trying to start other processes before and after system log daemon shown in the photo), same thing dbus/bus/ata errors
After about 5-10 mins of running through this it ends up stopping with a terminal command line prompt.

I can't even get to the login screen.

Has anyone got any idea what is going on and is it possible to fix?


Acer Travelmate C310 Laptop
Intel Pentium 1.73 Ghz
Memory 512 
Ubuntu is the sole OS (no window or dual boot going on)
(It's a rubbish old laptop, perhaps that got something to do with it!)

---

### Post by Big_Croc7 on 2009-04-25
I've no idea what might be wrong.  However, in case it's a package that didn't upgrade properly, when you're at the terminal prompt you could try doing a sudo aptitude update and sudo aptitude install (or apt-get, if you use that instead).  That should act on any outstanding packages that haven't installed properly.  Though you might want to wait for someone with a better idea to chip in!

---

### Post by evans5000 on 2009-04-25
Had an idea..

---

### Post by evans5000 on 2009-04-26
Had an idea. 

Is it possible for me to boot an 8.10 Live CD and then reinstall the 9.04 upgrade installation files using commands from the Live Terminal? If so, what would be the commands?

(It's clear to me that the installation files downloaded ok, but something quite major did not successfully install).

---

