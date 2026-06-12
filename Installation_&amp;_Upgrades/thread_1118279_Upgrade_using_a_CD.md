---
title: "Upgrade using a CD"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by MadnessRed on 2009-04-06
Hi, I have Ubuntu 8.04 and I am intending to update, I have been intending to update since I got 8.10 about 5 months ago.

Anyway rather than a new restart, I would like to just upgrade. So here is the problem. My internet is very slow. And downloading a distro is not really an option. For that reason I am restricted to the Request a CD. (The main reason I use Ubuntu to be honest, rather than other distros).

What I would like to know is can you upgrade using a CD rather than a download? And if so could someone please post how.

Many thanks

---

### Post by dtoronto on 2009-04-06
You should be able to put in the alternate CD and run
```
Alt+F2
gksu "sh /cdrom/cdromupgrade"

```

I assume you are using desktop Ubuntu and not the server version.

---

### Post by MadnessRed on 2009-04-06
> **dtoronto said:**
> You should be able to put in the alternate CD and run
```
Alt+F2
gksu "sh /cdrom/cdromupgrade"

```

I assume you are using desktop Ubuntu and not the server version.

Wow, that was a quick response? Many thanks.

Edit: it doesn't work.
> 
madnessred@anthony-desktop:~$ gksu "sh /cdrom/cdromupgrade"
sh: Can't open /cdrom/cdromupgrade
madnessred@anthony-desktop:~$ gksu "sh /cdrom0/cdromupgrade"
sh: Can't open /cdrom0/cdromupgrade
madnessred@anthony-desktop:~$ sudo sh /cdrom/cdromupgrade
sh: Can't open /cdrom/cdromupgrade
madnessred@anthony-desktop:~$ sudo sh /cdrom0/cdromupgrade
sh: Can't open /cdrom0/cdromupgrade


I have Ubuntu 8.04 i386 32bit Desktop Edition,upgrading to Ubuntu 8.10 i386 32bit Desktop Edition, both were requested bia the "Request a free CD"

---

### Post by spongypants23 on 2009-04-20
I believe that CD-ROM upgrades are only possible using the Alternate Installer...

[http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD](http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD)

I could be wrong.

---

### Post by MadnessRed on 2009-04-20
> **spongypants23 said:**
> I believe that CD-ROM upgrades are only possible using the Alternate Installer...

[http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD](http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD)

I could be wrong.

ok I was hoping that wouln't be the case. Thanks anyway

---

