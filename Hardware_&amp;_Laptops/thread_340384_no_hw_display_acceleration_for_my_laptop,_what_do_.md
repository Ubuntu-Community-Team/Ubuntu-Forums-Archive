---
title: "no h/w display acceleration for my laptop, what do i do?"
date: 2007-01-17
forum: Hardware &amp; Laptops
---

### Post by erv2 on 2007-01-17
my laptop is a Compaq Armada M300

its display module is the:  ATI Rage LT Pro video chip (4Mb video SGRAM)

i installed xbuntu-desktop on top of my basic server install (6.10) yesterday. everything else works out of the box (network card, wireless card, sound...), but for display, there's no hardware acceleration. even when i scroll down firefox, i can see the screen reflashing.

how do i find the correct driver and config it to work with xubuntu? i am a newbie to the linux world, so please excuse of my lack of knowledge and be as specific as you can.

thank you very much in advance.

---

### Post by Eugene RIMMER on 2007-01-17
First, engage all available repositories (look Ubuntu Wikis or Help for this). 

Update/install drivers, do something like this in your console:
```

sudo -s
apt-get update
apt-get install xserver-xorg-driver-ati

```
... and reconfigure x.org (you will be asked lots of questions on this step)
```

dpkg-reconfigure xserver-xorg
exit

```

or (if this doesn't help) do almost the same to another driver

```

sudo -s
apt-get update
apt-get install xorg-driver-fglrx
dpkg-reconfigure xserver-xorg
exit

```

If things went ok, reboot and enjoy!

---

