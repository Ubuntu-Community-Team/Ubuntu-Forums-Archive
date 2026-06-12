---
title: "TVTime with PixelView cards explained"
date: 2008-09-11
forum: General Help
---

### Post by patsymcox on 2008-09-11
I found these after long research, Sharing with you guys. 

First open Terminal and type 

```

sudo rmmod bttv
sudo rmmod bt878
sudo rmmod tuner

```

This is precaution, Remove if there any faulty configurations.

Then,

```

sudo modprobe bt878
sudo modprobe bttv card=? tuner=2 

```

Replace the ? with the value of your card, values for specific cards are below (Tuner=2 because assuming you are using PAL, If NTSC, you should find out the value for NTSC.)

```

  card=16 - Prolink Pixelview PlayTV (bt878)
  card=37 - Prolink PixelView PlayTV pro
  card=50 - Prolink PV-BT878P+4E /
            PixelView PlayTV PAK /
            Lenco MXTV-9578 CP
  card=70 - Prolink Pixelview PV-BT878P+ (Rev.4C)
  card=72 - Prolink Pixelview PV-BT878P+9B
            (PlayTV Pro rev.9B FM+NICAM)

```


And then, 

Edit modprobe.conf for bttv

```

sudo gedit /etc/modprobe.d/bttv

```

and insert

```

options bttv card=? tuner=2

```

Replace ? with the number of the card.

Search an Install TVTime with Synaptic Package Manager.

Select the frequency table as appropriate in the right click menu. If your country is not listed there, then close TVTime and open terminal and type

```

tvtime-scanner

```

It will scan the TV stations. After completing this, you should be getting TV in TvTime with PixelView Tuner cards.

---

### Post by C.S.Cameron on 2008-09-15
Thanks Pat:
I was starting to get frustrated setting up tvtime on a new thumbdrive.
I could not get a signal.
I had forgotten the part about:
sudo gedit /etc/modprobe.d/bttv
I have a Pixelview Play Tv XP 2.0 FM with BT878P+REV9F chip and live in Canada
so I added:
options bttv card=72 pll=1 radio=1
options tuner type=5
It is working great now

---

### Post by dandellion on 2009-01-16
Full list of arguments for cards and tuners can be found here: 
[http://www.tldp.org/HOWTO/BTTV/cards.html](http://www.tldp.org/HOWTO/BTTV/cards.html)
[http://www.tldp.org/HOWTO/BTTV/modprobe.html](http://www.tldp.org/HOWTO/BTTV/modprobe.html)


(got them via [http://mysettopbox.tv/phpBB2/viewtopic.php?t=11874](http://mysettopbox.tv/phpBB2/viewtopic.php?t=11874))

---

