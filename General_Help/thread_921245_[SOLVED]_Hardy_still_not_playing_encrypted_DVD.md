---
title: "[SOLVED] Hardy still not playing encrypted DVD"
date: 2008-09-16
forum: General Help
---

### Post by lviggiani on 2008-09-16
Hi All,
sorry for posting another thread about DVD playback... I know that the web is full of tutorial and I think I've followed almost all but still not luck.

I've installed ubuntu-restricted-extras, libdvdcss2, libdvdcss3, gstreamer (all plug-ins) and this is what happen when I try to play an encrypted DVD (I've tryed three different DVD but the result is still the same):

Totem (GStreamer): becomes grey for few seconds then some numbers appear on the menu (not always) and finally I get the error message "I cannot read from the resource"

Totem (xine): error message: "The source seems encrypted, and can't be read. Are you trying to play encrypted DVD without libdvdcss?"

MPlayer: for few second the program freezes, then the playback starts but is incredibly slow (it renders one one frame per second with squares all around).

vlc: this is the output on terminal:

```
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: INC0EIW1
libdvdnav: DVD Serial Number: 32222d39
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/lviggiani/.dvdnav/INC0EIW1.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000156
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x00049630
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_0.VOB (0x00049630)
libdvdread: Elapsed time 0
...
libdvdread: Found 9 VTS's
libdvdread: Elapsed time 1
[00000283] main playlist: nothing to play
```


I'm running Hardy with Compiz and nVidia 8400.
The language of my ubuntu is English UK and the DVD's are Italian.

Please HELP!!!
Thanks in advance!

---

### Post by nowshining on 2008-09-16
turn off compiz alas do you have the win32codecs isntalled as well? if all else fails exit all programs and in a terminal run sudo ldconfig and then logout and back in and re-try your request again..

---

### Post by lviggiani on 2008-09-16
Hi,
I did what you wrote but nothing changed.
Yes, I have w32codecs package installed too.
My computer is a Dell XPS M1330. Reading some forums it seems that the DVD device has no DMA support. COuld it be the cause?

---

### Post by nowshining on 2008-09-16
how old is this DVD rom drive? ol' model, newer model ??

---

### Post by lviggiani on 2008-09-16
It's definitely a newer model...

---

### Post by nowshining on 2008-09-16
hmmm should have dma and should be enabled my default.... alas the no DMA part shouldn't hurt much :)

are you perhaps trying to auto insert the DVD into the drive with totem - if so totem has this bug  from way back in the days - that you much manually find the drive and play thru the main file..


Yes Yes mplayer plays it just fine, is this DVD dirty? is the DVD drive dirty - try getting a DVD/CD cleaner disc and running it.. 

Can you also return this drive for another one?? This one may be defective or get urself a better one...hmmmm

---

### Post by lviggiani on 2008-09-16
I've tried with three different DVD's and nothinbg changes.
The DVD's play fine in other players....
I'll try to get a DVD cleaner even if I don't really think this is the problem since data DVD are read without any problem...
Thanks

---

### Post by nowshining on 2008-09-16
it never hurts to clean the drives once in awhile and i know u said it's new, however i don't exactly know what new is to u, a month, year??

---

### Post by lviggiani on 2008-09-16
8 months... I'll clean it and see what happens...
:)

---

### Post by nowshining on 2008-09-16
ah! hehe.

---

### Post by lviggiani on 2008-09-16
:(
I used a lens cleaner CD but nothing changed...
VLC still give me the same error...
at the end I read
```
libdvdread: Can't allocate memory for file read!
libdvdnav: ifoRead_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:214: ifoOpenNewVTSI: Assertion `0' failed.
Aborted
```

---

### Post by nowshining on 2008-09-16
http://search.yahoo.com/search?p="libdvdread%3A+Can't+allocate+memory+for+file+read!"&ei=UTF-8&iscqry=&fr=sfp&sourceid=Mozilla-search

---

### Post by Absolut Newbee on 2008-09-16
Had the same problem with DVDs bought in the UK, but it is working using kaffeine media player (don't ask me why).

---

### Post by lviggiani on 2008-09-16
Hey at the end I got it working!!!!!!! :) :)

The answer is regionset!!!!

```
sudo apt-get install regionset
```

...then insert your dvd...

```
regionset
```

and select the region of your DVD (IT is 2)

Thanks!!!!! :)

---

