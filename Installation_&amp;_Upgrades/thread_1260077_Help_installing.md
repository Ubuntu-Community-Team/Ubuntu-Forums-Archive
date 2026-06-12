---
title: "Help installing"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by 3000mik on 2009-09-07
I'm installing the drivers for my sound card Realtek ALC 883.
I've donwload them from the site and got the following instructions:

Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Turn on sound support from kernel config 
    (soundcore module, default turn on)

Step 3. Complied source code
    a. cd alsa-driver-1.0.xx
    b. ./configure
    c. make
    d. make install
    e. alsaconf
    f. ./snddevices (Only kernel 2.4 does it)


Could you help me with step 2 please? I really don't have any clue.

---

### Post by realzippy on 2009-09-07
**lsmod**

shows you the modules loaded,soundcore should be on by default.
If not,you can load it by:

**modprobe soundcore**

---

### Post by 3000mik on 2009-09-07
Thank you very much realzippy :)

---

