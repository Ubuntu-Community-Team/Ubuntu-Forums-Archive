---
title: "strange sound problem"
date: 2010-05-23
forum: Hardware
---

### Post by frriction on 2010-05-23
well I have dell studio 1555 
some time when I boot my ubuntu sound doesn't work at all. 

so I have to go to sound preference > output and select rv710/730 digital stereo and again select my original device internal audio analog stereo and sound starts working.

I have to do it manually at every start is there any work around for that?

---

### Post by inso_741 on 2010-05-24
research 'amixer'
```
man amixer
```
find your device and pass it as a parameter to amixer
add it to startup programs.....hope it helps

---

