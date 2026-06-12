---
title: "[SOLVED] Automatix"
date: 2008-12-04
forum: Installation &amp; Upgrades
---

### Post by jmacx81 on 2008-12-04
Whatever happened to Automatix?  I guess I haven't seen it since 7.10 but I do miss it.

---

### Post by ibutho on 2008-12-04
I think they ceased development (I maybe wrong). Automatix was really not required in Ubuntu 7.04+ and it was heavily criticised for breaking some things in Ubuntu, so thats probably why the developers decided to call it a day.

---

### Post by jmacx81 on 2008-12-04
> **ibutho said:**
> I think they ceased development (I maybe wrong). Automatix was really not required in Ubuntu 7.04+ and it was heavily criticised for breaking some things in Ubuntu, so thats probably why the developers decided to call it a day.

Wow I never knew it was causing problems. I used to really like it but I guess my system was a little buggy.

---

### Post by taurus on 2008-12-04
What do you need to install?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by jmacx81 on 2008-12-05
> **taurus said:**
> What do you need to install?

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

nothing really I was just remembered Automatix and started looking for it for some reason and couldn't find it. Thanks for the links though I will bookmark them and keep them

---

### Post by howefield on 2008-12-05
Someone has resurrected Automatix under a different name, was reading it a few weeks ago but can't remember the details, I'll have a look around and post back shortly.

---

### Post by jmacx81 on 2008-12-05
> **howefield said:**
> Someone has resurrected Automatix under a different name, was reading it a few weeks ago but can't remember the details, I'll have a look around and post back shortly.

Awesome, let me know the name when you find it and then maybe we can figure out if it is worth getting.

---

### Post by howefield on 2008-12-05
[http://ultamatix.com/](http://ultamatix.com/)

Might only be good for hardy though, but you can have a look and work out whether you can use it or not.

I used to love Automatix but don't miss it all now having had to find an alternative, using the links the guys above have posted, and others. There is a decent script on category5.tv called "perfectbuntu" which does a good job of automating installing codecs ect.

---

### Post by jmacx81 on 2008-12-05
> **howefield said:**
> [http://ultamatix.com/](http://ultamatix.com/)

Might only be good for hardy though, but you can have a look and work out whether you can use it or not.

I used to love Automatix but don't miss it all now having had to find an alternative, using the links the guys above have posted, and others. There is a decent script on category5.tv called "perfectbuntu" which does a good job of automating installing codecs ect.

Yeah that was, and still is my biggest problem if it isn't in Synaptic then I don't know how to deal with it.

---

### Post by NuBiXx on 2008-12-13
how do I uninstall this program (Ultamatix)?

---

### Post by Elfy on 2008-12-13
If you installed it with a deb

```
sudo apt-get remove --purge ultmatix
```

Check there's nothing left in your sources list

```
gedit /etc/apt/sources.list
```
if there are references in there remove them using gedit as root, either delete the lines or comment them out with a #

```
gksudo gedit /etc/apt/sources.list
```

After editing the sources list update

```
sudo apt-get update
```

---

### Post by NuBiXx on 2008-12-15
forestpixie, thanks much appreciate.

---

