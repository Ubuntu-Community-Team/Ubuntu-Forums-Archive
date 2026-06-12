---
title: "VAIO s260 cd ripping trouble"
date: 2005-08-25
forum: Hardware &amp; Laptops
---

### Post by uncle vernon on 2005-08-25
i have a sony vaio vgn-s260, running hoary.  when i try to rip a cd using sound juicer, it takes a painfully long time, an hour or so.  in windoze it takes maybe five minutes.  dmesg tells me:

```

Probing IDE interface ide1...
hdc: UJDA755 DVD/CDRW, ATAPI CD/DVD-ROM drive
...
hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache
Uniform CD-ROM driver Revision: 3.20

```

lsmod shows this related info:

```

cdrom                  36508  2 sr_mod,ide_cd
ide_core              118988  4 ide_cd,ide_generic,piix,ide_disk

```

even the prefs in sound juicer say that it's using a "UJDA755 DVD/CDRW".

so it appears that it's identifying the drive correctly.  also, cd's and dvd's *play* perfectly.  something else?  maybe a drive parameter?

thanks,
casey

---

### Post by s_p_a_r_k_y on 2005-08-25
I haven't used your ripper program, try using grip? I have had lots of success with that... also what I sometimes do it first rip a bunch of songs to .wav files then run a script over them to convert all the .wav files to mp3s or ogg instead of converting from cd -> wav -> mp3 in one step. It saves time as the encoding of mp3s takes  a while. Thus you can rip many cds to wav quickly, then just encode over night.

EDIT
also make sure that you have dma turned on for your hdc

in /etc/hdparm.conf
/dev/hdc {
     dma = on
     interrupt_unmask = on
     io32_support = 0
}
is what I have

---

