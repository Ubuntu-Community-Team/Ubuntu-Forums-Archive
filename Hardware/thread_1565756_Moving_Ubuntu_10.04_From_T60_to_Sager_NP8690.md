---
title: "Moving Ubuntu 10.04 From T60 to Sager NP8690"
date: 2010-09-01
forum: Hardware
---

### Post by swatkat1076 on 2010-09-01
Hi,
I have an old work laptop Lenovo T60 with Ubuntu 10.04 and my Java/oracle based development environment on that machine.

I have purchased a Sager NP8690 and Wanted to move the Ubuntu from Lenovo T60 to Sager.

Will my new hardware be detected automatically ?

Or will I have to do the dirty work

Please help.

Thanks

---

### Post by gabrielshier on 2010-09-01
hey,
not that recommended. actually almost no chance it will work. not when you're replacing the entire chipset. 
just make a fresh install, you can use APTonCD to copy all your packages which are installed and copy the home directory for settings. don't try just coping the entire system to a different motherboard and architecture. rarely works and not in these extremes... 
best of luck.

---

### Post by lukeiamyourfather on 2010-09-01
I'll second that, a fresh install is the way to go. Copy the home directory and reinstall the software packages you need (or use an automated tool to install them).

---

