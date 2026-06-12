---
title: "Seamless transfer from wire to wireless?"
date: 2005-10-10
forum: Hardware &amp; Laptops
---

### Post by gila_monster on 2005-10-10
I have Hoary installed on a Gateway 4525GZ. Most everything works (except having a left-handed touchpad configuration), so I'm pretty happy.

One area that annoys me is the way it handles wireless connections. I normally work at my desk with a LAN cable plugged in. But when I pull the cable to go work in another part of the house, the system does not automatically start using the wireless connection. Instead, I have to go into the configuration and meddle a bit to get it to recognize the WAP. Is this normal? Should it be able to automatically switch?

I have the wire (eth0) set up as the default device. And yes, I do remember to turn on the laptop's wireless card before I pull the plug. ;)

Thanks.

Gila.

---

### Post by ranf on 2005-10-11
[QUOTE=gila_monster]I have the wire (eth0) set up as the default device. And yes, I do remember to turn on the laptop's wireless card before I pull the plug. ;)
[/QUOTE]
Just an idea: how about pulling the plug **and then** activating wireless? I have no idea if that really makes a difference. Worth a try anyway.

---

### Post by gila_monster on 2005-10-11
[QUOTE=ranf]Just an idea: how about pulling the plug **and then** activating wireless? I have no idea if that really makes a difference. Worth a try anyway.[/QUOTE]

Yeah, tried that. The only thing that seems to work is going into network configuration and deactivating the wire (eth0). Have a similar issue going from wireless to wired as well.

Gila

---

### Post by skirkpatrick on 2005-10-11
Upgrade to Breezy and install Network-Manager.  I've got it on two laptops and it will automatically switch between wired and known wireless networks with a preference given to a wired connection.

---

### Post by knappen on 2005-10-12
[QUOTE=skirkpatrick]Upgrade to Breezy and install Network-Manager.  I've got it on two laptops and it will automatically switch between wired and known wireless networks with a preference given to a wired connection.[/QUOTE]

Yes, that networkmanager is absolutely perfect. When I unplug my cable, after about 5 seconds it connects automatically to my wireless network. It works the other way around as well. It switches from wireless to the cable automatically when detected.

I am using that with Fedora 4 on one of my laptops :-)

---

