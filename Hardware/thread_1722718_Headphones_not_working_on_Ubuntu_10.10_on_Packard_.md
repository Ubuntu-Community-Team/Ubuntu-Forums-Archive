---
title: "Headphones not working on Ubuntu 10.10 on Packard Bell  with Wubi"
date: 2011-04-06
forum: Hardware
---

### Post by atticusfrost on 2011-04-06
Hello

New to Ubuntu, installed using Wubi. Everything workds fine except for headphones which won't work when plugged in. The built in speakers continue to play.

How can I fix this?

---

### Post by lidex on 2011-04-06
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

