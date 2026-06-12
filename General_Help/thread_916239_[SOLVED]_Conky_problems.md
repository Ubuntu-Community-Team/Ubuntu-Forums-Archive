---
title: "[SOLVED] Conky problems"
date: 2008-09-10
forum: General Help
---

### Post by lighthammer on 2008-09-10
Ok, I have read many threads about how to customize conky and for some reason, it is not working for me. I used apt-get to get conky and when I open up a terminal and type in conky, I get the generic default version.

I found in another post various conky configurations. I copied one of them to a text file. How do I substitute the nicer one over the default?

---

### Post by easybake on 2008-09-10
> **lighthammer said:**
> Ok, I have read many threads about how to customize conky and for some reason, it is not working for me. I used apt-get to get conky and when I open up a terminal and type in conky, I get the generic default version.

I found in another post various conky configurations. I copied one of them to a text file. How do I substitute the nicer one over the default?

You have 2 options.

1. in terminal type ```
gedit .conkyrc
``` then paste the configuration you want over the one default one.

or

2. If you want to use multiple conkys at the same time, just save the configurations you want in any folder. Just change the path in this code to where the 1st config is located. ```
conky -c ~/CHANGE/THIS/TO/THE/PATH/WHERE/THE/FIRST/CONFIG/IS/LOCATED
```
--------------------------

---

### Post by JECHO on 2008-09-10
> **lighthammer said:**
> Ok, I have read many threads about how to customize conky and for some reason, it is not working for me. I used apt-get to get conky and when I open up a terminal and type in conky, I get the generic default version.

I found in another post various conky configurations. I copied one of them to a text file. How do I substitute the nicer one over the default?



just rename the text file you made to ".conkyrc" and save it in your home directory. then run conky and your config file will be loaded.

---

