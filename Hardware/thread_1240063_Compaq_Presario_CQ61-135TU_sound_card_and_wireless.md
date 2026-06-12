---
title: "Compaq Presario CQ61-135TU sound card and wireless internet issues"
date: 2009-08-14
forum: Hardware
---

### Post by pauljdunn on 2009-08-14
I have a Compaq Presario CQ61-135TU purchased specifically to run Ubuntu Linux or similar I can load Ubuntu but no joy getting the sound card or wireless internet working or (Web cam or Data card these are not so important)can anyone help me to get the right drivers to get the sound card or wireless internet working?

Even if I have to pay someone to write the drivers.

---

### Post by Joppe4899 on 2009-08-19
The wireless worked for me after this.

sudo apt-get install linux-backports-modules-jaunty

---

### Post by pauljdunn on 2009-08-23
Any idea how to get the wireless card working? funny thing is it works with Fedora but no Ubuntu is there a solution or do I just have to wait for the next release?

---

### Post by astrex on 2009-10-30
Compaq Presario CQ61 sound card solution!

install latest alsa
add following lines to /etc/modprobe.d/alsa-base.conf

```

options snd-pcsp index=-2
options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1

```This worked for my Compaq Presario CQ61-214TX


read more here 
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
and here
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)

---

### Post by xtrumanx on 2010-01-26
@Joppe4899

I tried downloading the package but got this message:

E: Couldn't find package linux-backports-modules-jaunty

Do I need to add some sources. I'm using Ubuntu 8.10.

**Edit**: I changed the package name from ...-jaunty to -intrepid because that's the codename of my version of ubuntu. The packages (and some dependencies) were downloaded and installed but I still haven't got a wireless connection.

---

### Post by Joppe4899 on 2010-02-02
@xtrumanx

Sorry, can't help you with that, not that experienced with linux.

Found that solution at another forum, can't remember where.

P.S. It worked for me out of the box with Ubuntu 9.10
Got a CQ61-215SO, don't know if there are any differences with the wireless hardware, havn't checked, but I don't think there are any major differences

---

