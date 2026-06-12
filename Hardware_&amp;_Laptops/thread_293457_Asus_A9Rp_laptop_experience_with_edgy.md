---
title: "Asus A9Rp laptop experience with edgy"
date: 2006-11-05
forum: Hardware &amp; Laptops
---

### Post by shelleycat on 2006-11-05
Since there is not a lot about this machine on the forums, and I'm still trying to get it working fully, I thought I would share my experiences.

Machine is an Asus A9Rp laptop,
Using 6.10 Edgy. Installed fresh, dual booting with XP.  No problems with the install.

Needs acpi=off on the boot menu to start (and on live cd), current boot setting is
root=/dev/hdc3 ro quiet splash hpet=disable pci=assign-busses

Wireless lan, the built in one needs the driver from
[http://zd1211.ath.cx/](http://zd1211.ath.cx/),
this needs the usb for the build in card adding, then compiling according to the instructions on that page. I added the usb address into the zd1211b section.  I removed the existing zd1211rw drivers.  I've downloaded later zd1211rw drivers, added the usb address, but this does not work (so far).  I've tried ndiswrapper, but this just crashes.

Apart from that, function keys mostly work, suspend to hibernate partly works (network does not come up again).  Suspend did not work.
acpi seems to respond to different power.

I've got no idea whether I should be changing video drivers yet.
The synaptics touchpad works.

(On dapper, the same boot settings were needed.)

---

### Post by dysko on 2006-12-13
Sorry for bothering... :)
I also have ASUS A9Rp and problem is that ubuntu (kubuntu and xubuntu) does not recognize battery on the laptop? Did you maybe found some solution... Im strating laptop with acpi=off...

---

### Post by shelleycat on 2006-12-13
I could have been a bit clearer, I started out with acpi=off, but have found that with the boot setting line in the original post (hpet=disable etc), I have no problem seeing the battery and switching from battery to ac and vice-versa. At the moment I am running with acpi on but with the exact boot setting in the original post.

---

### Post by Pennywise1 on 2006-12-24
@shelleycat
Did you try a bios update to version 215? Found it on [http://www.asustreiber.de/download.php?view.331](http://www.asustreiber.de/download.php?view.331) I did not read the changelog, but after that it was not nessesary to turn acpi=off.
My system is working, but I wonder what the startup message "Cannot allocate resource region 3 of device 0000:00:00.0" means.
I am from the german forum of ubuntuusers.de. Sorry for my english and merry christmas.

---

### Post by rytmisk on 2007-01-10
Hi fellow asus sufferers...

Anyway - here are my little contribution:

Updating the bios solved the acpi boot parameters for me -. but suspend to ram still only works halfway - the screen is cray when I restart it. I'll see if I can investigate that further. 

Wireless I fixed by following a French howto at [http://forum.ubuntu-fr.org/viewtopic.php?pid=649014](http://forum.ubuntu-fr.org/viewtopic.php?pid=649014)

I don't speak French, but by looking at the French page and at an automatic translation by google
[http://www.google.com/translate?u=http%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fpid%3D649014&langpair=fr%7Cen&hl=en&ie=UTF8](http://www.google.com/translate?u=http%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fpid%3D649014&langpair=fr%7Cen&hl=en&ie=UTF8)
I managed to make it work quite easily,

Good lock!
Ketil

---

### Post by rytmisk on 2007-01-11
- oh one question though. 

What does "PS: Copiez ce tutoriel quelque par sur une clef USB ou autre car a chaque mise a jour du noyeau il vous faudra re-modifier les options de boot et re-compiler le pilote."

Does it by any chance mean that I will have to redo this for every new kernel I install? I tried a different kernel you see, and the wireless stopped working.

Best
Ketil

---

### Post by rytmisk on 2007-01-14
Oh - a few ore things:

I screwed up once and reinstalled the whole os. I then discovered that I had to do a few more things: 

Blacklist the zd1211rw and zd1211 driver in /etc/modprobe.d/blacklist by adding two lines at the end of the file saying:
```

blacklist zd1211rw
blacklist zd1211
```

I still do not get very stable speed, but at least it always works. Somehow these different drivers inflicted upon each others. There is a bunch of other tips at [http://www.ubuntuforums.org/showthread.php?t=288753]("http://www.ubuntuforums.org/showthread.php?t=288753")


For some reason I am not able to make it work on a 2.6.19 kernel - yet...

For now - good luck!
Ketil

---

### Post by rytmisk on 2007-03-08
Good news!

With the latest bios from Asus software suspend finally works! (go to [http://support.asus.com]("http://support.asus.com")to download.
And according to th 1211rw mailinglist, our wireless will be supported by the default kernel from kernel 2.6.22. Then our a9rp's will be completely working!

Best regards
Ketil Thorgersen

---

