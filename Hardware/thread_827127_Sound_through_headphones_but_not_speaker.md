---
title: "Sound through headphones but not speaker"
date: 2008-06-12
forum: Hardware
---

### Post by -=WaLrUs=- on 2008-06-12
Hello,

Still trying to get sound working on my laptop, Samsung R45.

I have just discovered the sound is working through the headphone jack but not the built in speakers.

Any tips on how to get it to come out of the speakers?

Many thanks.

---

### Post by pedrogfrancisco on 2008-06-12
Ubuntu version?

---

### Post by sdennie on 2008-06-12
One thing you could try would be to bring up a terminal and type "alsamixer".  It's possible that one of your sound channels is muted.

---

### Post by -=WaLrUs=- on 2008-06-12
tried alsamixer, everything up to max.  Still no joy.
Using Gutsy Gibbon.

---

### Post by pedrogfrancisco on 2008-06-13
Try backport-modules .

```

apt-get install linux-backports-modules-gutsy-generic

```

I may have told you the wrong pacakge name, can't remember now and I'm using Hardy.

The "lspci" might be a nice extra information.

---

### Post by -=WaLrUs=- on 2008-06-13
can't seem to get it to work, I get this respsonse:

holmes@holmes-laptop:~$ apt-get install linux-backports-modules-gutsy-generic
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by -=WaLrUs=- on 2008-06-13
ok, my mistake now get this error:

root@holmes-laptop:~# apt-get install linux-backports-modules-gutsy-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-gutsy-generic

---

### Post by pedrogfrancisco on 2008-06-13
As I said I might have told you the wrong package name since I don't use Gutsy anymore.

try

```

apt-cache search backports |grep modules

```
and tell us the results.

P.S.: no need to be root for this.

---

### Post by -=WaLrUs=- on 2008-06-15
Tried it and got this back:

linux-backports-modules-2.6.22-14-rt - Ubuntu supplied Linux modules for version 2.6.22 on x86/x86_64
linux-backports-modules-2.6.22-14-ume - Ubuntu supplied Linux modules for version 2.6.22 on Embedded/Mobile
linux-backports-modules-2.6.22-14-xen - Ubuntu supplied Linux modules for version 2.6.22 on x86
linux-backports-modules-rt - Backported drivers for realtime kernel image
linux-backports-modules-ume - Backported drivers for 386 Embedded/Mobile kernel image
linux-backports-modules-virtual - Backported drivers for virtual kernel image
linux-backports-modules-xen - Backported drivers for Xen kernel image
linux-backports-modules - Generic Linux backported drivers.
linux-backports-modules-2.6.22-14-386 - Ubuntu supplied Linux modules for version 2.6.22 on i386
linux-backports-modules-2.6.22-14-generic - Ubuntu supplied Linux modules for version 2.6.22 on x86/x86_64
linux-backports-modules-2.6.22-14-server - Ubuntu supplied Linux modules for version 2.6.22 on x86/x86_64
linux-backports-modules-386 - Backported drivers for 386 kernel image
linux-backports-modules-generic - Backported drivers for generic kernel image
linux-backports-modules-server - Backported drivers for server kernel image


still no sound though.

---

### Post by babisnet on 2008-06-15
I have exactly the same problem with sound..
I use 8.04 and my sound chip set is realtek ALC 883..
any ideas?

---

### Post by pedrogfrancisco on 2008-06-15
**-=WaLrUs=-**
```
sudo apt-get install linux-backports-modules
```

**babisnet**
```
sudo apt-get install linux-backports-modules-hardy-generic
```

**babisnet**
It's not the "same" issue, at least you can't be sure since it isn't the same Linux version, you force me to answer differently as you can see.

Anyway, if **both of you** still get no sound after what I said (don't forget to REBOOT and to run alsamixer after rebooting to check sound levels) just then we can start thinking it's the same issue.

Check ALSA mailing lists (searching engines A.K.A. Google and such are your friends) and come back here.

---

### Post by argail1980 on 2008-06-15
try following the steps here:

[http://ubuntuforums.org/showthread.php?t=823552]("http://ubuntuforums.org/showthread.php?t=823552")

it's a different card but might work

---

### Post by -=WaLrUs=- on 2008-06-18
Still no joy :confused:

---

### Post by pedrogfrancisco on 2008-06-21
You did what I said?

---

### Post by -=WaLrUs=- on 2008-06-21
yep, still no joy!

---

### Post by pedrogfrancisco on 2008-12-01
Upgrade Ubuntu? :p

(better to answer late than never :p)

---

