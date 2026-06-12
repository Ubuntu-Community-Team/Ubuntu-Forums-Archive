---
title: "Where is rc.conf"
date: 2008-10-13
forum: General Help
---

### Post by alberto ferreira on 2008-10-13
Isn't Ubuntu supposed to have a rc.conf file?

I mean, in other distros like Arch there is a "main" system configuration file with this path:
/etc/rc.conf
OR
/etc/X11/rc.conf

If Ubuntu hasn't got this file how does it configure the parameters that are usually stored in there? :s

---

### Post by bodhi.zazen on 2008-10-13
no, rc.onf is fairly unique to Arch.

What are you trying to configure ?

---

### Post by cdenley on 2008-10-13
Maybe you want /etc/rc.local?

---

### Post by bodhi.zazen on 2008-10-13
> **cdenley said:**
> Maybe you want /etc/rc.local?

no, in arch system configuration (networking and such) is all in one large file, rc.conf

> The rc.conf file (/etc/rc.conf) is the core system configuration file used in Arch Linux. It puts several commonly edited settings such as timezone, keymap, kernel modules and daemons to load at start-up, etc. into one convenient text file to streamline system administration. 

[http://wiki.archlinux.org/index.php/Rc.conf](http://wiki.archlinux.org/index.php/Rc.conf)

rc.local is an empty file where one can add commands to run as part of the boot process as an alternate to writing a more complex boot script.

---

### Post by Yellow Pasque on 2008-10-13
I don't remember everything that's in rc.conf off the top of my head, but here's some key Ubuntu/Debian files:
/etc/modules - kernel modules you want loaded at boot
/etc/blacklist - blacklisted modules
/etc/network/interfaces - network configuration
/etc/timezone

---

### Post by alberto ferreira on 2008-10-14
Thanks, everyone. :)

Don't flame me, but wouldn't you agree that Arch's rc.conf is A LOT more streamlined than having all those settings spread around your pc?
Don't you think that Ubuntu could learn something from Arch?
I mean, for assistance and maintenance purposes having a single file that stores critical system information would be preferable to Ubuntu's spread around conf files

---

### Post by bodhi.zazen on 2008-10-14
> **alberto ferreira said:**
> Thanks, everyone. :)

Don't flame me, but wouldn't you agree that Arch's rc.conf is A LOT more streamlined than having all those settings spread around your pc?
Don't you think that Ubuntu could learn something from Arch?
I mean, for assistance and maintenance purposes having a single file that stores critical system information would be preferable to Ubuntu's spread around conf files

LOL

Arch does not have a single configuration file.

I would say that most of the time the vast majority of Ubuntu users do not edit config files all that often and appreciate that Ubuntu configures things "automagically" (as opposed to having to edit configuration files as part of the installation process).

By one big configuration file are you suggesting one should :

cat /etc/*.* > one_big_file

That would be a big mess, who wants to skim through a config file that is several thousand lines long ?

Arch, like Ubuntu, has advantages and disadvantages (don;'t get me worng here, Arch is one of my favorite distros). IMO bickering about the exact structure of config files in /etc is pointless. By that I mean each distro has slightly different ways of structuring config files in /etc (ie Fedora is different then Debian is different form Gentoo, etc) and if you run different distros you need to learn to adapt without the arrogence to suggest that one is better then another :lolflag: .

---

### Post by iponeverything on 2008-10-14
rc.conf is pretty old school -- it been around for a long time.

I don't agree though that it is better system. Splitting things out became necessary very early on not only because of size, but also because of flexibility. 

Every new type of interface that's built on an existing interface, usually requires rc type configuration mechanisms that to have to parse the information from the existing interface configuration files. For an idea of what talking about run:
```

find /etc |grep \\.d$

```

Those are all directories of what are essentially rc configuration files.

-- and while I too am somewhat change adverse -
What I learned is that finding and learning the new configuration mechanisms is fairly easy and in the majority of cases -- the new system is better than the last.

---

### Post by barryd3 on 2011-05-16
> **cdenley said:**
> Maybe you want /etc/rc.local?

In arch we do it like this too!

---

