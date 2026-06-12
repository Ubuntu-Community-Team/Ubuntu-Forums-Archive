---
title: "ubuntu with kubuntu"
date: 2005-11-17
forum: General Help
---

### Post by whisper on 2005-11-17
hello i am a bit of a n00b to linux and ubuntu/kubuntu i was wondering if i could have ubuntu and kubuntu as a dual boot so i could switch i have both install cds  i have a 20gb hard drive

---

### Post by dcast on 2005-11-17
you don't need to they are teh exact same thing but with different window managers gnome vs kde

---

### Post by Specialsauce on 2005-11-17
easy, but they would both have limited space because you have such a small hard drive. you can easily edit the partition table in the ubuntu installer. probably the kubuntu one, too.

---

### Post by whisper on 2005-11-17
[QUOTE=Specialsauce]easy, but they would both have limited space because you have such a small hard drive. you can easily edit the partition table in the ubuntu installer. probably the kubuntu one, too.[/QUOTE]

well i am installing kubuntu at the mo (im on a differnt computer) when i install ubuntu how do i change the partition table (is there any gudie)

---

### Post by Specialsauce on 2005-11-17
it will ask you if you want to erase the entire disk, or if you want to edit the partition table. choose edit the partition table. when you have kubuntu installed, resize tht partition so that it is a little under ten gigs, and then install ubuntu on the free space.....    at least im pretty sure thats how it would go.

---

### Post by whisper on 2005-11-17
[QUOTE=Specialsauce]it will ask you if you want to erase the entire disk, or if you want to edit the partition table. choose edit the partition table. when you have kubuntu installed, resize tht partition so that it is a little under ten gigs, and then install ubuntu on the free space.....    at least im pretty sure thats how it would go.[/QUOTE]
woops i have gone past that now can i change it inside kubuntu or should i ask the kubuntu forum people for that?

---

### Post by Specialsauce on 2005-11-17
i take it your installing kubuntu first? if your installing ubuntu (with no K) second, then youll have the option of doing that when you install ubuntu. personally, i think kubuntu is a waste. if you really want kde, use a distro made specifically for it, like SUSE. but why would you want kde anyway? meh, just my worthless opinion.

---

### Post by whisper on 2005-11-17
[QUOTE=Specialsauce]i take it your installing kubuntu first? if your installing ubuntu (with no K) second, then youll have the option of doing that when you install ubuntu. personally, i think kubuntu is a waste. if you really want kde, use a distro made specifically for it, like SUSE. but why would you want kde anyway? meh, just my worthless opinion.[/QUOTE]
well i tried the live cds of them and i liked kde better but still liked GNOME so i want both of them :cool:

---

### Post by Corvillus on 2005-11-17
The metapackage for the Ubuntu-customized GNOME is ubuntu-desktop. The metapackage for the Kubuntu-customized KDE is kubuntu-desktop. You can have both installed in your ubuntu install without the need to dual-boot, and you just select the desktop you want when you log in.

---

### Post by Specialsauce on 2005-11-17
im not trying to start another 'kde vs. gnome' debate, but just from experience, i've found that kde is alot closer to windows dll hell than gnome, although it is spiffier looking and more polished off.

---

### Post by Adrian on 2005-11-17
[QUOTE=whisper]woops i have gone past that now can i change it inside kubuntu or should i ask the kubuntu forum people for that?[/QUOTE]

Why dual boot? They are the same operating system with different desktop environments. You can have both installed, and choose desktop environment (Gnome or KDE) at the login screen.

Just install the ubuntu-desktop package from Kubuntu, for instance by typing
```
apt-get install ubuntu-desktop
```
and you'll get them both.

You can as well install Kubuntu (KDE+applications) from Ubuntu by installing the kubuntu-desktop package.

---

