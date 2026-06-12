---
title: "stuttering with 7600GT"
date: 2007-02-09
forum: Hardware &amp; Laptops
---

### Post by notto on 2007-02-09
My problem is that when i load glxgears or anything 3d.

every few seconds i get stuttering but that lasts for only maybe 2 seconds.

My computer specs:
Cpu: Amd athlon 64 3200+
Ram: 1gb ram
hdd: 250gb
optical: lg dvd burner
mobo: Foxconn NF4UK8AA (nforce 4 ultra)
video: inno3d nvidia geforce 7600gt 256mb pci-e 16x
o/s: ubuntu 6.10 edgy and winxp. (dual boot)

i seem to be missing the command fglrxinfo.
and i run glxgears and i dont seem to be getting a report (in the terminal) on how many fps there is.

any help greatly aprreciated

also any tweak guides would be lovely to get maximum performance for games as well as drivers.

---

### Post by renzokuken on 2007-02-09
try 
```
glxgears -printfps
```

---

### Post by notto on 2007-02-09
thx for that info.
although i still get stuttering.

41380 frames in 5.0 seconds = 8275.905 FPS
60315 frames in 5.0 seconds = 12051.840 FPS
62127 frames in 5.0 seconds = 12425.276 FPS
68764 frames in 5.0 seconds = 13752.783 FPS
72934 frames in 5.0 seconds = 14586.686 FPS
70668 frames in 5.0 seconds = 14133.571 FPS
41380 frames in 5.0 seconds = 8275.905 FPS
60315 frames in 5.0 seconds = 12051.840 FPS
62127 frames in 5.0 seconds = 12425.276 FPS
68764 frames in 5.0 seconds = 13752.783 FPS
72934 frames in 5.0 seconds = 14586.686 FPS
70668 frames in 5.0 seconds = 14133.571 FPS

thats what its saying now.
anyone got any idea on how to get rid of stuttering? as of i want to play 3d games on ubuntu but when it stutters its quite annoying e.g. tuxkart it stutters than i crash into a wall.

update:
3d working great!!! now.
no more stuttering.
i aint got a clue what i did to make it work but it works.
i enabled ntfs support read and write.
made sure the right kernels were on here.
and a few other things.
but now im a happy penguin gamer :) now i just need to get all my windows games to work on ubuntu then ill be a microsoft free man!!

---

