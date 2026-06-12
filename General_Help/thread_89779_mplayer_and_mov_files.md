---
title: "mplayer and mov files"
date: 2005-11-13
forum: General Help
---

### Post by superprotta on 2005-11-13
Hi, first of all i want to say sorry for my english..i know it's not perfect :( 
My problem is that mplayer won't play mov files and the problem seems to be the audio codec because that's the output i receive:

```
Trying to force audio codec driver family libmad...
Opening audio decoder: [faad] AAC (MPEG2/4 Advanced Audio Coding)
MPlayer interrupted by signal 11 in module: init_audio_codec
- MPlayer crashed by bad usage of CPU/FPU/RAM.
  Recompile MPlayer with --enable-debug and make a 'gdb' backtrace and
  disassembly. Details in DOCS/HTML/en/bugreports_what.html#bugreports_crash.
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
```

I tried reinstalling libfaad and recompiling mplayer a lot of times but that didn't help. Searching with google i found [this]("http://wiki.koeln.ccc.de/index.php/21C3_Videos#Debian_Sarge_Setup")  and it seems that this is a problem related to debian.
Anyway i coudn't find any solution so maybe you cold help me :) 
thanks

---

### Post by taurus on 2005-11-13
Not so sure what kind of movie you are talking about but my mplayer (installed with apt-get) never has any trouble playing anything that I throw at it, even .bin...

---

### Post by superprotta on 2005-11-13
it's a quicktime movie, one of those from apple movie trailers.
Probably there's something wrong i do installing mplayer, but i don't understand what since i installed it also using synaptic

---

### Post by taurus on 2005-11-13
Did you happen to install codecs for your mplayer as well???

---

### Post by superprotta on 2005-11-13
yes..i downloaded them from the official site and copied them to /usr/lib/win32
Anyway this doesn't seem to be the problem because, seeing the output, it seem that mplayer finds the faad decoder but fails loading it as if the package was broken.  So i tried reinstalling libfaad from marillat repository and recompiling mplayer with external faad, but it still didn't work.

---

### Post by taurus on 2005-11-13
Okay, give me the link to the site that you've downloaded those mov trailers and I will check to see if I can play them with my mplayer...

---

### Post by superprotta on 2005-11-13
thanks :) ! [http://movies.apple.com/movies/wb/harry_potter_goblet/harry_potter_goblet_h480p.mov]("http://movies.apple.com/movies/wb/harry_potter_goblet/harry_potter_goblet_h480p.mov") (ehm...yes ..a harry potter trailer :oops:  )

---

