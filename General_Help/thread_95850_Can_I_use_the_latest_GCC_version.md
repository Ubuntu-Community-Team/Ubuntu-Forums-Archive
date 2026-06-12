---
title: "Can I use the latest GCC version?"
date: 2005-11-27
forum: General Help
---

### Post by eXSBass on 2005-11-27
Hi! In order for my modem to work I need to install GCC version 3.4 because the GCC version that came with Ubuntu 5.1 was wrong. My question is can I install GCC version 4.1 because it seems to be the latest one? Furthermore, is GCC 3.4 the same as GCC 3.4.4 on the GCC website?

Cheers :)

---

### Post by hw-tph on 2005-11-27
gcc 4.0.1/4.0.2 is available in the official repositories, so is 3.4.4. Just type **sudo apt-get install gcc-4.0** or **sudo apt-get install gcc-3.4** to download and install them. In most cases you can specify which one to use using the CC environment variable, like this: **CC=/usr/bin/gcc-3.4.4. ./configure**.


Håkan

---

### Post by jdong on 2005-11-27
4.1 is not packaged in Ubuntu yet... I'm unsure if it's planned for Dapper or not...

Typically compiler updates are extreme enough that it takes a new release to get them. Remember that it's not just another program, but rather the program that builds the rest of the system!

---

### Post by eXSBass on 2005-11-27
[QUOTE=hw-tph]gcc 4.0.1/4.0.2 is available in the official repositories, so is 3.4.4. Just type **sudo apt-get install gcc-4.0** or **sudo apt-get install gcc-3.4** to download and install them. In most cases you can specify which one to use using the CC environment variable, like this: **CC=/usr/bin/gcc-3.4.4. ./configure**.


Håkan[/QUOTE]


I need GCC for my modem to work therefore I don't have the internet :p But as regards to your post, I am so terribly sorry I didn't understand a word of it :p
All I need is GCC 3.4. Is it the same as GCC 3.4.4? Because I was told the wrong GCC version was shipped with Ubuntu 5.1 so I need GCC version 3.4, the same one Ubuntu 5.1 was made with, if that makes any sense.

Thanks alot tph for the reply though, it is appreciated.

---

### Post by jdong on 2005-11-27
Use Synaptic to install the package called **gcc-3.4**.... That is the correct version.

---

### Post by eXSBass on 2005-11-27
[QUOTE=jdong]Use Synaptic to install the package called **gcc-3.4**.... That is the correct version.[/QUOTE]


Cheers, what's Synaptic and how do I go about getting it?

---

### Post by jdong on 2005-11-27
under SYstem, Administration, towards bottom.

---

### Post by eXSBass on 2005-11-27
Thanks dong, i'll try that in a bit.

---

