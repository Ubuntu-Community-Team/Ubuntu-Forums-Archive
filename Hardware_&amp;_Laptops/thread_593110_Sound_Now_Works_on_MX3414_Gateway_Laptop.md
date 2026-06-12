---
title: "Sound Now Works on MX3414 Gateway Laptop"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by PBK on 2007-10-26
I finally got sound to work on my Gateway MX3414 laptop!! I'm running ubuntu 7.10 Gutsy, but I don't know if that matters. I first downloaded alsa's latest 1.0.15 (driver, lib, util) this morning. I sort of followed the notes from:

[http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel](http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel)

I did have to apt-get a few packages that you may already have installed:

```
sudo apt-get install build-essential
sudo apt-get install libncurses5-dev

```

  After that, in the appropriate directories, I basically:

 ```
bunzip2 alsa-driver-1.0.15.tar.bz2
cd alsa-driver-1.0.15
./configure --with-cards=hda-intel --with-sequencer=yes
make
sudo make install

```

  I then:

```
chmod a+rw /dev/dsp /dev/mixer /dev/sequencer

```

```
cd ..
bunzip2 alsa-lib-1.0.15.tar.bz2
cd alsa-lib-1.0.15
./configure
make
sudo make install
```

```
cd ..
bunzip2 alsa-utils-1.0.15.tar.bz2
cd alsa-utils-1.0.15
./configure
make
sudo make install
```

  I had errors working with the utils, but maybe this isn't essential because it works.

After I rebooted, there is now sound. Speakers work, headphone jack works. I assume the microphone works because it worked in earlier, but not tested today.

  I hope this work for you. 

Paul

---

