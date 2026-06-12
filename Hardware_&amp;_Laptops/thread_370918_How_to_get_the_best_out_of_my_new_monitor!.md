---
title: "How to get the best out of my new monitor!"
date: 2007-02-26
forum: Hardware &amp; Laptops
---

### Post by Julian David Pitt on 2007-02-26
I have just bought a new Belinea 10 20 35W monitor and I can only get it to run 1024 x 768. I wish to get it running at 1680 x 1050 which is its native resolution but have now manged to break xserver and I cannot boot at all. Can someone explain how to do this for me as I would be very grateful.

---

### Post by jethro10 on 2007-02-26
> **Julian David Pitt said:**
> I have just bought a new Belinea 10 20 35W monitor and I can only get it to run 1024 x 768. I wish to get it running at 1680 x 1050 which is its native resolution but have now manged to break xserver and I cannot boot at all. Can someone explain how to do this for me as I would be very grateful.

I probably can't help, but it does depend on the manufacturer of the graphics card. You'll need to post that here to get help.

J

---

### Post by Julian David Pitt on 2007-02-26
> **jethro10 said:**
> I probably can't help, but it does depend on the manufacturer of the graphics card. You'll need to post that here to get help.

J

Hi thanks for responding, my card is a Nvidia Geforce 6600GT 128 mb.

---

### Post by jethro10 on 2007-02-27
Right, i'm almost sure you'll need the Nvidia binary drivers rather than the open source ones.

Start here [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

If you get this working, afterwards make sure you have installed the nvidia-settings program from the repo's

If you do a search in the forums for "nvidia widescreen", i'm sure you'll be shocked at how much activity there is about this
good luck.

J

---

### Post by sheepshearer on 2007-02-27
```
less /var/log/Xorg.0.log
```

along with all the other stuff, you should see something like:
```

(II) R128(0): Supported Future Video Modes:
(II) R128(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) R128(0): #1: hsize: 1152  vsize 720  refresh: 60  vid: 113
(II) R128(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) R128(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) R128(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) R128(0): Supported additional Video Mode:
(II) R128(0): clock: 146.2 MHz   Image Size:  473 x 296 mm
(II) R128(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) R128(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) R128(0): Ranges: V min: 55  V max: 77 Hz, H min: 30  H max: 84 kHz, PixClock max 170 MHz

```

that gives you the information you need for a ModeLine entry in /etc/X11/xorg.conf

here's snippet of mine gleened from the above:

```

Section "Monitor"
        Identifier   "Monitor0"
        HorizSync    30.0 - 84.0
        VertRefresh  55.0 - 77.0
        ModeLine     "1680x1050" 146.2 1680 1784 1960 2240 1050 1053 1059 1089
        Option       "DPMS"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
                Modes    "1680x1050" 
        EndSubSection
EndSection

```

HTH

---

