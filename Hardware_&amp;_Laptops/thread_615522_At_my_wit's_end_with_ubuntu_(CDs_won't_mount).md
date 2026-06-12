---
title: "At my wit's end with ubuntu (CDs won't mount)"
date: 2007-11-17
forum: Hardware &amp; Laptops
---

### Post by zanes on 2007-11-17
Hi,

I've just about had it with ubunutu on this machine for various reasons (refusing to install,intermittently working network card, requiring 250mb download to install drivers, non-working cd drives.) but I'll give it another go. Everytime I cure one problem, another one pops up. You're probably thinking "spoilt windows user", and maybe you're right.

Anyway, onto todays problem. Yesterday the ancient cd-rw drive "gave up the ghost", refusing to mount cd's. Today I put in a new cd-rw/dvd rom drive. It's recognised in BIOS fine, as my secondary master (primary mast and slave are hdd,)
Linux recognises there is a drive there (CD-RW/DVD ROM DRIVE icon in "computer",) but whenever I put a disc in, the activty light flashes on and off, it makes a little noise after 10-15 seconds and nothing else happens, unless I click on the drive icon, when I get a unable to mount media error,
I'm suspecting this maybe a software problem, as this is what my old drive did yesterday, suddenly and without warning. I'd just written it off as sudden failure of an old drive, but now I'm not so sure.
Thanks,

Frustrated linux newbie.

---

### Post by PmDematagoda on 2007-11-17
Hello, sorry to hear about your problems.

Anyway, concerning your DVD-ROM, could you post the output of:-

```
cat /etc/fstab
```

After that we could make our next step.

---

### Post by zanes on 2007-11-17
Certainly, it gives this;

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=a1171ad5-5ea1-4638-8e4a-3560a964e60c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=d47ceebb-3843-4300-b9b1-be68d79b92b1 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Thanks,

Alex

---

### Post by PmDematagoda on 2007-11-17
> **zanes said:**
> 
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


This line is close to impossible as the part "/dev/hda" is usually "/dev/scd0". Open up the fstab file for editing using:-
```

sudo gedit /etc/fstab
```

And then change the part in [COLOR="Red"]red[/COLOR]:-

```
[COLOR="Red"]/dev/hda[/COLOR]     /media/cdrom0   udf,iso9660 user,noauto     0       0
```


to /dev/scd0. Save the file, reboot the PC and then see if the DVD-ROM works properly.

---

### Post by zanes on 2007-11-17
Ok, did that.now fstab reads,

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc1
UUID=a1171ad5-5ea1-4638-8e4a-3560a964e60c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=d47ceebb-3843-4300-b9b1-be68d79b92b1 none            swap    sw              0       0
/dev/scd0        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

And my dvd-rom/cd-rw icon still gives "cannot mount volume" also a CD-ROM 1 icon has appeared in computer, which also gives the unable to mount error, but with
mount: special device /dev/scd0 does not exist
under "show more details"

---

### Post by PmDematagoda on 2007-11-17
It seems like that the CD-ROM is not on scd0. Install gparted using:-

```
sudo apt-get install gparted
```

After install it can be found in System>Administration>Partition Editor. Open it while the CD is in the DVD-ROM. Then find out where the CD is found by GParted>Devices, the location must be given such as scd0. After that, replace the entry in fstab that you just edited with the one Gparted gave.

Then reboot the PC and try the DVD-ROM again.

---

### Post by zanes on 2007-11-17
Ok, it doesn't look like gparted can find it. Swapped the dvd/cd-rw to where my second disk (windoze 95) was (on the same cable as primary hdd is) so it's now primary slave. Still BIOS finds it ok, but not there in gparted.

---

### Post by PmDematagoda on 2007-11-17
Very strange, did you check if the DVD-ROM is clashing with any other components due to it's setup as a Primary Slave?

---

### Post by zanes on 2007-11-17
Well it looks like it is dead, just tried it in my flatmates windows machine with the same result. Will return it to web site, hopefully.

---

### Post by PmDematagoda on 2007-11-17
I'm very sorry about the DVD-ROM, where did you buy it from, was it recent and what brand is it?

---

### Post by zanes on 2007-11-17
It's an NEC CB1100B, manufactured in febuary 2007. Order from kikatek.com, excellent delivery speed but have yet to experience their returns procedure,

---

### Post by hessiess on 2007-11-17
always recertch before buying anything ;)

---

### Post by zanes on 2007-11-17
Whilst we're on the subject, it's not possible my other hardware could of damaged the drives, is it? (By not possible, I mean highly unlikely)

---

### Post by PmDematagoda on 2007-11-17
No, it is very unlikely that the other hardware would cause the DVD-ROM to malfunction. I do not think NEC is very reliable, why don't you go for something better like Samsung or if you can afford it, Plextor.

---

### Post by zanes on 2007-11-18
Yeah I'm going to try and get a refund (ie. not exchange) and go for a samsung.

---

### Post by nutter78 on 2007-11-18
I found LG wrters always to be very reliable!

---

