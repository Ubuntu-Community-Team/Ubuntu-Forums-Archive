---
title: "Emerging Beryl 0.1.9999.2 in Sabayon/Gentoo(without negative dbus factors)"
date: 2007-02-21
forum: Gentoo and derivatives
---

### Post by RAV TUX on 2007-02-21
[COLOR=Red]First and foremost before you do anything do:[/COLOR]
> emerge --sync && layman -S && emerge portage<surfed>

[quote="ewiget"]Thought I would share this - also posted to gentoo forums too (I post under tSp there though)

I ran into a problem after an emerge upgrade to system and world that has been driving me crazy for a few days. The error was related to libdbus-1.so.2 and practically every gnome package depended on it. Just wanted to share this fix so others don't go through what I did (by the way, this is a sabayon install and not gentoo but figured since dbus and libdbus came from the gentoo repo that it would be same error for both distros).

Running revdep-rebuild was listing almost all gnome packages linked against libdbus-1.so.2 and they would all fail during emerge with the same error, missing. Gnome wouldn't work, kde wouldn't work (different problem fixed with post at MLUG -- Maysville--  website) 

I tried many different things to fix it - you can read all about it mess here - [http://www.maysville-linux-users-group.org/ftopicp-376.html](http://www.maysville-linux-users-group.org/ftopicp-376.html) but the final fix ended up being this (so simple, yet overlooked for so long):

cd /usr/lib
ln -s libdbus-1.so.3.2.0 libdbus-1.so.2
cd /root
rm -rf .revdep*
revdep-rebuild
[/quote] 
[http://www.sabayonlinux.org/forum/posting.php?mode=quote&p=16627](http://www.sabayonlinux.org/forum/posting.php?mode=quote&p=16627)

then:
> [22:27] <surfed> USE="dbus" emerge beryl

[22:29] <surfed> edit your /etc/make.conf
[22:30] <surfed> make sure it says dbus in the line USE=

[22:32] <surfed> use:
[22:32] <surfed> nano -w /etc/make.conf
[22:32] <surfed> it is important
[22:32] <surfed> not to have linebreaks
[22:32] <surfed> so thats what the -w does
[22:32] <surfed> ctrl+o saves
[22:33] <surfed> ctrl+x exits

[23:10] <surfed> then emerge -pv berylthen emerge beryl


I am still doing revdep-rebuild, but I will post this for archival reference and discussion.

also reference:
[http://sabayonlinux.org/wiki/index.php?title=HOWTO:_Install_Packages_on_Sabayon_/_The_Complete_Portage_Guide](http://sabayonlinux.org/wiki/index.php?title=HOWTO:_Install_Packages_on_Sabayon_/_The_Complete_Portage_Guide)

---

### Post by manmower on 2007-02-22
Seems like a lot of hoops to jump through for something so simple.

---

### Post by RAV TUX on 2007-02-22
> **manmower said:**
> Seems like a lot of hoops to jump through for something so simple.it normally isn't needed....it is sort -of a patch....Ubuntu and all distros have had their fair share(remember the Ubuntu X incident)

not that hard to copy and paste or even edit one line.

normally you would just

> emerge beryl

---

### Post by RAV TUX on 2007-02-22
note: this is only for version 0.1.9999.2

for version 0.1.9999.1 just:
> 
emerge =beryl-0.1.9999.1

---

### Post by RAV TUX on 2007-02-22
> **RAV TUX said:**
> [COLOR=Red]First and foremost before you do anything do:[/COLOR]
<surfed>

 
[http://www.sabayonlinux.org/forum/posting.php?mode=quote&p=16627](http://www.sabayonlinux.org/forum/posting.php?mode=quote&p=16627)

then:
then emerge beryl


I am still doing revdep-rebuild, but I will post this for archival reference and discussion.

also reference:
[http://sabayonlinux.org/wiki/index.php?title=HOWTO:_Install_Packages_on_Sabayon_/_The_Complete_Portage_Guide](http://sabayonlinux.org/wiki/index.php?title=HOWTO:_Install_Packages_on_Sabayon_/_The_Complete_Portage_Guide)

Edit to the OP...Beryl is all fixed just do:

>  emerge =beryl-0.1.9999.2

---

### Post by RAV TUX on 2007-02-22
note: if <config files in '/etc'> need updating :

> etc-update or dispatch-conf

---

### Post by zaratustra on 2007-02-22
i have 1.9999.2 for a few weeks and everything was compiled flawlessly... It is an overlay from Xeffects

---

### Post by mysticrider92 on 2007-02-24
Thanks for the how to. On my Sabayon install, I can't get it to show anything above Beryl 1.4 even after "emerge --sync" and "emerge portage". Also, do  you have a guide on setting up the Aquamarine window decorator for KDE?

---

### Post by zaratustra on 2007-02-24
```
emerge layman
```
```
layman -a xeffects
```
```
echo "source /usr/portage/local/layman/make.conf" >> /etc/make.conf
```
optionaly```
update-eix
```
--unmask everything that is required-- 
```
emerge beryl
```
update to post: 
I'd just like to add, that if kde useflag is on, aquamarine will be installed automaticaly. (also needs to be unmasked)
If it is not which I doubt:
```
emerge aquamarine
```

---

### Post by RAV TUX on 2007-02-25
> **zaratustra said:**
> ```
emerge layman
``````
layman -a xeffects
``````
echo "source /usr/portage/local/layman/make.conf" >> /etc/make.conf
```optionaly```
update-eix
```--unmask everything that is required-- 
```
emerge beryl
``````
emerge aquamarine
```

Thanks for the howto I will have to do this.:)

---

