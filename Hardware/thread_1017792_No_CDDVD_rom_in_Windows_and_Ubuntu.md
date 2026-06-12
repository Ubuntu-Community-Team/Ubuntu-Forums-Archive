---
title: "No CD/DVD rom in Windows and Ubuntu"
date: 2008-12-21
forum: Hardware
---

### Post by kram_italy on 2008-12-21
Hello everyone, I'm really down.

I'm using Ubuntu 8.10 & Win Vista Ultimate on an Hp Pavilion Dv2700.
My problem is that both in Windows (device manager) and in Ubuntu I cannot find my DVD rom!

Actually I tried booting from Ubuntu Live CD and it works, so I suppose there's no problem with the DVD unit.
And when I try booting from cd and then I reboot, I can see my DVD rom both in Vista and Ubuntu; but if I switch my pc off and then on again, everything disappeared.

I tried all I could...

in Win I checked for Upperfilter and Lowerfilters in the registry, but I do not have them...
there's no driver listed in the device manager and even in Ubuntu I see nothing at all.

I have an idea but i'm not sure about it: can the problem be caused by Grub loader?

Try to help me please, it is so annyoing...

Thanks for any reply, and sorry for my English!

---

### Post by xelxel on 2008-12-21
sounds like the CD/DVD for some reason isn't mounted when booting from
HDD.

Make your way to the commandline, run the following command, and paste the
result here.

```
sudo lshw -c disk
```

---

### Post by kram_italy on 2008-12-23
well this is what I get:

  *-disk                  
       description: ATA Disk
       product: WDC WD2500BEVS-6
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 01.0
       serial: WD-WXEZ07N63117
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000eae29


thanks for your answer

p.s. this seems to be the report of my hard disk, not of my dvd rom.. is it ok?

---

### Post by kram_italy on 2008-12-30
please..no solution?

---

### Post by BatsotO on 2008-12-30
uhm.. BIOS?

---

### Post by kram_italy on 2008-12-30
what do you mean, if I see it in bios?

---

### Post by meierfra. on 2009-01-02
You might have to use Lilo instead of Grub to get your DVD drive to work:

[URL="http://ubuntuforums.org/archive/index.php/t-616046.html"]
http://ubuntuforums.org/archive/index.php/t-616046.html[/URL]

Information on Lilo:
[URL="http://users.bigpond.net.au/hermanzone/p4.html"]
http://users.bigpond.net.au/hermanzone/p4.html[/URL]

---

