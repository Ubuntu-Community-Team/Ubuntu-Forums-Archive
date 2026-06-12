---
title: "Second attempt at getting help"
date: 2008-11-01
forum: General Help
---

### Post by buzzforb on 2008-11-01
i mistakingly tried to install automatix on ubuntu 8.04. I was unaware that it was not compatible. As a result of the attempted command line install, i am now getting this error mesage:

E:Type 'http://www.getautomatix.com/keys/automatix2.key' is not known on line 16 in source list /etc/apt/sources.list, E:The list of sources could not be read

As a result i can no longer use synaptic manager. does anyone know how to remove this failed command so that my system will work as it should

---

### Post by taurus on 2008-11-01
Open a terminal and edit your /etc/apt/sources.list.  Remove that line from it.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

p.s.  Remember to close Synaptic Package Manager window first before editing /etc/apt/sources.list.

---

### Post by tvtech on 2008-11-01
The advice above is good advice

p.s. automatix is something like evil so unless you want your computer taken over by evil, I suggest avoiding it.

---

