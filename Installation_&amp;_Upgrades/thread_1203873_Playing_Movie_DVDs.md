---
title: "Playing Movie DVDs"
date: 2009-07-03
forum: Installation &amp; Upgrades
---

### Post by henrywm on 2009-07-03
I wiped and reinstalled Windows XP MCE on my Dell Inspiron 6000 laptop and then used wubi-installer to make a dual-boot system with Ubuntu. Apparently the reinstall did not include a DVD decoder. The computer would detect and read data DVDs, but it could not detect movie DVDs. I was able to install a driver to make it detect movie DVDs in Windows but not the decoder. In Ubuntu it won't even detect movie DVDs. Any advice?

---

### Post by starcraft.man on 2009-07-03
Uh, even encrypted DVDs should detect and mount in Linux. You can't play the content properly, that's a separate issue. If it persists after the below step post back and we'll try and figure that out.

To playback such movies, install libdvdcss2 from the medibuntu repos. [Details here]("https://help.ubuntu.com/community/Medibuntu"), just give a quick read and follow the applicable instructions. Has a few other handy packages ya might like too.

---

### Post by ad_267 on 2009-07-03
You don't need to use medibuntu. Just install the libdvdread4 package then open a terminal and run:
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

See [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by henrywm on 2009-07-04
I aready had libdvdread4, but I ran the command. I could not find libdvdcss2 in the package manager, and so I installed ubuntu-restricted-extras.

Now the computer will try to play DVDs, but then I get the following error: "Could not open location; you might not have permission to open the file." I tried this on two movie DVDs.

---

### Post by henrywm on 2009-07-04
I installed "Totem Player (xine backend)" from the Add/Remove dialog. That seemed to fix it at first for one movie DVD, but after a few moments the Totem Movie Player would fade to gray and stop playing and say it could not read the resource. It still would not detect the other movie DVD.

---

### Post by henrywm on 2009-07-04
When it cannot detect the DVD it will not even mount.

---

### Post by howefield on 2009-07-04
Any DVDs I have a problem playing in Movie Player or other programs never seem to fail when played in VLC.

You could give that a go.

---

### Post by henrywm on 2009-07-04
It still works for only a few seconds.

---

### Post by ad_267 on 2009-07-04
libdvdcss2 is installed using that script from the libdvdread4 package. Have you tried any other dvds? Does that dvd work fine on another computer? Do you have another operating system installed on the same computer that it works on?

---

### Post by henrywm on 2009-07-06
I have Windows XP MCE 2005 on the same laptop. At first DVDs did not work in either OS. I lacked a DVD decoder, and so I installed VLC in Windows. I am using Totem in Linux.

I tried different DVDs. They worked fine in both OS. This all started after I reformatted the drive and reinstalled.

All DVDs work fine on my other computer.

---

### Post by henrywm on 2009-07-07
Actually the other DVDs do not work so well. They will play for a while, and then the player fails because it cannot read the disk.

---

### Post by Ric_NYC on 2009-07-22
> **ad_267 said:**
> You don't need to use medibuntu. Just install the libdvdread4 package then open a terminal and run:
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

See [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Thank you! Now my notebook can play DVDs.
:popcorn:

---

