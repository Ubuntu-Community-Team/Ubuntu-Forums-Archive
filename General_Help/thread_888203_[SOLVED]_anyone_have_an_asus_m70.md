---
title: "[SOLVED] anyone have an asus m70?"
date: 2008-08-12
forum: General Help
---

### Post by Mgiacchetti on 2008-08-12
I'm wondering if anyone has ubuntu installed on an Asus M70, and if so, were there any issues?

I'm getting one in the near future, and was just wondering.

---

### Post by salacious_crumb on 2008-08-22
I have one.  I have only noticed 2 issues, both minor.  The first thing I noticed was that their "multimedia touchpad" feature doesn't seem to do anything in Ubuntu.  I still don't know how to get that working. 

The second issue was with alsa.  I couldn't get sound out of the headphone jack.  I used module assistant to recompile alsa, which seems to have fixed the problem.

I haven't even bothered with the fingerprint reader, so I can't comment on that.

Overall, I've found it to be an excellent system.  I think you'll enjoy it.

---

### Post by oxsyn on 2008-09-09
I have the Asus M70Vm-X1.  I installed Ubuntu 8.04 64bit on this thing, and NOTHING was recognized out of the box.  The Atheros Wireless chip is completely unsupported with the current linux kernel (from what I've read), the sound doesn't work, the 9600M drivers wouldn't install via Envy, so I had to install the Nvidia X Server directly from the Nvidia site, the fingerprint reader & webcam don't work either.

I'm also having problems with the wired ethernet picking up on DHCP, not sure why but sometimes I have to restart the laptop a few times to get an IP.

---

### Post by t.rei on 2008-09-14
I have an asus m70v.

needed to install the nvidia driver using envy. (manually, did not autodetect)

Everything is working fine, except pluggin in the headphone not muting the internal speakers. must google more. ;)

---

### Post by jestemradek on 2008-09-25
Hello
I have M70VM and Gentoo Linux 64 bit.

I'm using kernel 2.6.27 (rc7)

WIFI (intel 5100) - works (drivers in kernel) only firmware from intel wireless site
Sound - works (headphone output works too)
Light sensor - works
Finger reader - works but very bad
Camera - works very well (uvc drivers) from 2.6.27 in kernel
Bluetooth - works


Not working:
advanced functions of touchpad
FN's

---

### Post by Mgiacchetti on 2008-09-25
Well, so far, i have gotten the nvidia  9600m gs working without envy, i used [this thread]("http://ubuntuforums.org/showpost.php?p=4768072&postcount=1")  and all went well.  No problems with that.. Although my Atheros dont work at all.  It halfway sees the router, but wont connect.  

Sound is a no so far, (although I havent messed with that yet)  have not even thought about the webcam, fingerprint reader, etc.

However, i would like to add that if one can find a way into the linux that asus puts on it in the factory, we could probably get all the drivers and solve all these issues.

turn your notebook off and hit one of the buttons near the left speaker.  Mine is the one that looks like a music/video button.   You will be brought into asus's version of linux.

---

### Post by jestemradek on 2008-09-25
> **Mgiacchetti said:**
> It halfway sees the router, but wont connect..


When I use kernel 2.6.26 I have this same problem...
But in 2.6.27 this card work very well ;-)

---

### Post by Mgiacchetti on 2008-09-25
see thats the funny thing, i was using 2.6.27.4  the latest and greatest, i even tried the firmware thing mentioned above and when i did that i got this defaning beep coming from the speakers at boot time.  Ditched that install. willing to try it again if anyone can figure this problem out.

Another thing, I guess I can finally say I have sound :)

---

### Post by Mgiacchetti on 2008-09-26
```

sudo su
echo 0 > /sys/devices/platform/asus-laptop/bluetooth
echo 1 > /sys/devices/platform/asus-laptop/wlan

```

---

### Post by t.rei on 2008-10-03
I got rid of mad booting sounds by disabling usplash. Works fine now. I have to replug my MX Revolution Mouse to get my buttons the way I want them once per boot, but thats something I can live with.

---

### Post by Mgiacchetti on 2011-06-02
Resurrected.  Need info on getting the undersub (it's got dolby 2.1 surround sound) working with 11.04

---

