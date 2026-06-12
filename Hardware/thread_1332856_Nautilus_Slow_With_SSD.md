---
title: "Nautilus Slow With SSD"
date: 2009-11-20
forum: Hardware
---

### Post by HalfEmptyHero on 2009-11-20
I just got an 80 GB SSD and for some reason nautilus runs incredibly slow with it. My boot time, and opening of other programs is a lot faster than before, but nautilus is barely usable. [This]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820157021") is the one I got.

Edit: It seems to only be happening when dealing with a lot of images. It slowed down like this with my old hard drive, but not by this much.

---

### Post by apocalypse80 on 2009-11-21
Can't say I have an issue like that.
The first time I open a folder with lots of pictures results in a cpu-induced delay until all thumbnails are produced - you could enable the system monitor applet to see what's happening in your case.
Opening the same folder again at any time goes really fast.

You could also try benchmarking your ssd, see how fast it really is.
Install iozone3 and run "iozone -I -a -s 256M -r 4k -r 64k -r 512k -r 8192k -i 0 -i 1 -i 2".

If you get very low performance at small reads/writes (and with an intel you REALLY shouldn't) then that may well be the problem.
Thumbnails are tiny files.

You could also try disabling thumbnails and whether the same problem occurs in folders with lots of videos or pdf/ps documents.

For reference, what my intel g2 gets running that iozone command;

```
                                                  random  random
    KB  reclen   write rewrite    read    reread    read   write
262144       4   55436   65711    79852    80149   19067   53292
262144      64  101396  106724   197531   202331  143772  106063
262144     512  107378  110893   233207   235219  233527  109245
262144    8192  111614  112405   250563   250567  238135  112355
```

---

### Post by HalfEmptyHero on 2009-11-21
This is what I got

```
                                   
              KB  reclen   write rewrite    read    reread    read   write
          262144       4   31636   38458    51168    51388   17595   35204
          262144      64   74013   71062   166081   208017  131860   76258
          262144     512   79259   80613   247084   247033  235745   80710
          262144    8192   80930   74756   167670   253024  238519   80663

```

It does become fast after it loads all the thumbnails, and I was dealing with a lot of icons, but should it take longer than my old 7200rpm SATA drive to load them all? Nautilus pretty much freezed while it was loading the thumbnails. If this is how it is, I can deal, but if its not normal than I'd like to know.

Also this only happens with image thumbnails. I have a folder with more than 300 movies in it and nautilus didn't significantly slow down while it was loading all of its thumbnails.

---

