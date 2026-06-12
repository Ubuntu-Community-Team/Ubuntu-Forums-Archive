---
title: "Any one with a Screem 0.16.0 package?"
date: 2005-11-05
forum: General Help
---

### Post by monotux on 2005-11-05
Hello everyone...

I can't build the new version of screem on my computer (it's complaining about missing dependencies, altho I ran a "apt-get build-dep screem") - so is there anyone out there with a built package of screem 0.16.0?
I haven't tried screem in a while, and this new stable version looks promising...

```
checking for SCREEM... configure: error: Package requirements (                 gtk+-2.0 >= 2.6.0                                               glib-2.0 >= 2.6.0                                            libgnome-2.0 >= 2.2.0                                           libgnomeui-2.0 >= 2.6.0                     libxml-2.0 >= 2.4.3                                              libglade-2.0 >= 2.3.0                                           gconf-2.0 >= 2.2.0          gnome-vfs-2.0 >= 2.8.3                                           gdk-pixbuf-2.0 >= 2.2.0                                         gthread-2.0 >= 2.2.0        libgtkhtml-2.0 >= 2.2.0                                          gmodule-2.0 >= 2.2.0                                            libgnomeprint-2.2 >= 2.2.0  libgnomeprintui-2.2 >= 2.2.0                                     gtksourceview-1.0 >= 1.1.90                                                                 libgnome-menu >= 2.9.2           ) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

```

That's the error msg, btw.

---

### Post by David A Knight on 2005-11-06
apt-get install libgnome-menu-dev

and that should be the only missing dependancy, I don't think any others were added since the version that is in breezy.

apt-get install libenchant-dev  

and configure with --enable-enchant is a good idea as well.

---

### Post by vasdee on 2005-11-07
has anyone got a deb package of a version greater than 0.12?
David, you wrote the program - do you happen to have a deb package for it? :smile:

---

### Post by thechitowncubs on 2005-11-07
The default configuration could not be found, this means that screem doesn't appear to have been installed correctly and can not continue.  If you have just installed screem then try restarting gconfd.

I can only run as root, and I don't know what to restart :/ in order to get it to work.

I have a package that i made with checkinstall, i'm not sure if that will work for others though.

---

### Post by David A Knight on 2005-11-07
[QUOTE=thechitowncubs]The default configuration could not be found, this means that screem doesn't appear to have been installed correctly and can not continue.  If you have just installed screem then try restarting gconfd.[/QUOTE]

gconftool-2 --shutdown

this will only apply to that login though, if you have logged out since then this shouldn't be an issue.

---

### Post by David A Knight on 2005-11-07
[QUOTE=vasdee]has anyone got a deb package of a version greater than 0.12?
David, you wrote the program - do you happen to have a deb package for it? :smile:[/QUOTE]

Probably not a good idea suggesting it, but sid has 0.14.2 packaged, and debian experimental has 0.15.1.

I don't have a deb package available no.  I don't really want to start either as it would be stepping Rob's toes a bit and I don't want to have to deal with packaging issues.

Dapper repos should get newer packages in soon I would have thought, which then might be candidates for backports to breezy.

---

### Post by denisesballs on 2005-11-11
[QUOTE=David A Knight]apt-get install libgnome-menu-dev

and that should be the only missing dependancy, I don't think any others were added since the version that is in breezy.

apt-get install libenchant-dev  

and configure with --enable-enchant is a good idea as well.[/QUOTE]

I installed those and still get that error. Is it really missing all these things?

---

### Post by David A Knight on 2005-11-11
[QUOTE=denisesballs]I installed those and still get that error. Is it really missing all these things?[/QUOTE]

not sure which dev packages you are missing then.  however 0.16.0 has just entered the Dapper repositories, so ask the backport team for a version in Breezy.

---

### Post by denisesballs on 2005-11-11
[QUOTE=David A Knight]not sure which dev packages you are missing then.  however 0.16.0 has just entered the Dapper repositories, so ask the backport team for a version in Breezy.[/QUOTE]

I changed my repos to dapper and looked for a newer Screem, but non to be found. Am I missing a repo?

```
root@jesseubuntu:/home/jesse# sed -ie "s/breezy/dapper/" /etc/apt/sources.list
root@jesseubuntu:/home/jesse# apt-get update
Get:1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://security.ubuntu.com dapper-security Release [19.6kB]
Get:4 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:5 http://archive.ubuntu.com dapper Release [30.9kB]
Get:6 http://security.ubuntu.com dapper-security/main Packages [14B]
Get:7 http://archive.ubuntu.com dapper/multiverse Packages [90.2kB]
Get:8 http://security.ubuntu.com dapper-security/restricted Packages [14B]
Get:9 http://security.ubuntu.com dapper-security/main Sources [14B]
Get:10 http://security.ubuntu.com dapper-security/restricted Sources [14B]
Get:11 http://security.ubuntu.com dapper-security/universe Packages [14B]
Get:12 http://security.ubuntu.com dapper-security/universe Sources [14B]
Get:13 http://us.archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:14 http://us.archive.ubuntu.com dapper Release [30.9kB]
Get:15 http://archive.ubuntu.com dapper/multiverse Sources [45.0kB]
Get:16 http://us.archive.ubuntu.com dapper-updates Release [19.6kB]
Get:17 http://us.archive.ubuntu.com dapper/main Packages [577kB]
Get:18 http://us.archive.ubuntu.com dapper/restricted Packages [5062B]
Get:19 http://us.archive.ubuntu.com dapper/main Sources [236kB]
Get:20 http://us.archive.ubuntu.com dapper/restricted Sources [1453B]
Get:21 http://us.archive.ubuntu.com dapper/universe Packages [2326kB]
Get:22 http://us.archive.ubuntu.com dapper/universe Sources [928kB]
Get:23 http://us.archive.ubuntu.com dapper-updates/main Packages [14B]
Get:24 http://us.archive.ubuntu.com dapper-updates/restricted Packages [14B]
Get:25 http://us.archive.ubuntu.com dapper-updates/universe Packages [14B]
Get:26 http://us.archive.ubuntu.com dapper-updates/multiverse Packages [14B]
Get:27 http://us.archive.ubuntu.com dapper-updates/main Sources [14B]
Get:28 http://us.archive.ubuntu.com dapper-updates/restricted Sources [14B]
Fetched 4311kB in 33s (129kB/s)
Reading package lists... Done
root@jesseubuntu:/home/jesse# apt-get install screem
Reading package lists... Done
Building dependency tree... Done
screem is already the newest version
```

---

### Post by David A Knight on 2005-11-12
[QUOTE=denisesballs]I changed my repos to dapper and looked for a newer Screem, but non to be found. Am I missing a repo?[/QUOTE]

either the packages list hasn't updated on the mirror or you just missed the mirror updating as it is there for i386, amd64, and ppc.

[http://us.archive.ubuntu.com/ubuntu/pool/main/s/screem/](http://us.archive.ubuntu.com/ubuntu/pool/main/s/screem/)

I'd better add that unless you are prepared for possible major system breakage it isn't wise to update to dapper, just incase you blame screem for anything that happens :D

---

### Post by denisesballs on 2005-11-12
[QUOTE=David A Knight][http://us.archive.ubuntu.com/ubuntu/pool/main/s/screem/](http://us.archive.ubuntu.com/ubuntu/pool/main/s/screem/)

I'd better add that unless you are prepared for possible major system breakage it isn't wise to update to dapper, just incase you blame screem for anything that happens :D[/QUOTE]
 How do I add that to my sources.list?

---

### Post by David A Knight on 2005-11-13
[QUOTE=denisesballs]How do I add that to my sources.list?[/QUOTE]

you already have the source added as

[http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main

it should become available with your next update

---

### Post by denisesballs on 2005-11-13
[QUOTE=David A Knight]you already have the source added as

[http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main

it should become available with your next update[/QUOTE]

Well since when I update it doesn't think there's a newer Screem package, can I add just that mirror you gave me which definitely has it?

---

