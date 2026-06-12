---
title: "No audio on Intel 915 GAV"
date: 2005-10-07
forum: Hardware &amp; Laptops
---

### Post by almostlinux on 2005-10-07
I'm reposting the thread here (the original thread is on the Warty section)

my motherboard is Intel 915 GAV ... HD audio (realtek chipset)


I've followed this 'Howto'...

[https://wiki.ubuntu.com/HdaIntelSoundHowto](https://wiki.ubuntu.com/HdaIntelSoundHowto)


```
# apt-get install alsa-source

# apt-get install linux-headers-2.6.10-5-686

# apt-get install kernel-package ## installs make-kpkg

# apt-get install ncurses-dev ## I am not sure if this is really needed

$ less /usr/share/doc/alsa-source/README.Debian

# dpkg-reconfigure alsa-source ## choose azx as driver

# apt-get install fakeroot

# cd /usr/src

# tar jxf alsa-driver.tar.bz2

# cd linux-headers-2.6.10-5-686

# make-kpkg --rootcmd=fakeroot --append-to-version=-5-686 modules-image
[B]
# dpkg -i alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb [/B]
```

I seem to have problem with the last line. I get this output when i execute the last line..
```


$:/usr/src/linux-headers-2.6.10-5-686 # dpkg -i alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb
dpkg: error processing alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb

```

I checked the directory /usr/src there was this file:

alsa-modules-2.6.10-5-686_1.0.8-4ubuntu4+10.00.Custom_i386.deb

do i have to move it to the linux-headers-2.6.10-5-686 directory? :???:

tia ...

---

