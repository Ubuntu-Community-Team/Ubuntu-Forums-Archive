---
title: "Help with Sound Driver Install."
date: 2010-09-22
forum: Hardware
---

### Post by utnubu23 on 2010-09-22
Totally new to ubuntu. My sound driver was recognized on install with 10.04 , but as soon as i installed my gfx card driver it for some reason made the sound not work and no longer recognizes it.  I got the driver on my desktop but don't know what to type in terminal to install it. It says in ReadMe 1) Goto source directory,2) Execute make command as root,
make 
make install

I think you get what im asking.:)Thx for any help.

---

### Post by lkjoel on 2010-09-24
> **utnubu23 said:**
> Totally new to ubuntu. My sound driver was recognized on install with 10.04 , but as soon as i installed my gfx card driver it for some reason made the sound not work and no longer recognizes it.  I got the driver on my desktop but don't know what to type in terminal to install it. It says in ReadMe 1) Goto source directory,2) Execute make command as root,
make 
make install

I think you get what im asking.:)Thx for any help.
In the Terminal:
```
sudo make
make
make install
sudo make install
```
These commands contain fallbacks.

---

