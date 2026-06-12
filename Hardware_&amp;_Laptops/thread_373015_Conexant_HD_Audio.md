---
title: "Conexant HD Audio"
date: 2007-02-28
forum: Hardware &amp; Laptops
---

### Post by szabodabo on 2007-02-28
I have a new HP dv2000 Laptop
With a Conexant HD Audio sound card (5047)
I have everything working beautifully on here...
EXCEPT THE AUDIO.
At my school, we have studyhall, and the sound isn't allowed to be on on our computers during this time, so I need headphones to work.
The built-in speakers perform fine on here, but when I plug in the headphones, the laptop speakers don't turn off.
I have ALSA 1.0.14RC2 installed.  There is no switch in the alsamixer to get the headphones working.  I'm using Ubuntu Edgy.  
Please help me?
I've tried all solutions I've found on these forums and elsewhere and none seem to work.
I'm a relative newbie, but I can do easier things such as apt-get and sudo and things like that.
Thanks.

---

### Post by sampohappelil on 2007-03-05
I had the same problem with my dv2000t. A recent [patch]("http://article.gmane.org/gmane.linux.alsa.devel/44604") to the alsa driver posted on the alsa-devel list solved it for me. I just downloaded the patch and ran it against the 1.0.14rc2 driver, compiled and after a restart the auto-muting worked.

If I remember correctly, I did something like this after downloading the patch (44604-001.bin):

```

tar -xjf alsa-driver-1.0.14rc2.tar.bz2 
cd alsa-driver-1.0.14rc2/alsa-kernel
patch -p1 < ../../44604-001.bin
cd ..
./configure --with-debug=full --with-cards=hda-intel --with-oss=yes --with-sequencer=yes
make
sudo make install
```

I might have had other options on the command line as well, don't remember.

Looking at the [alsa-devel mailing]("http://news.gmane.org/gmane.linux.alsa.devel") list it seems like a new version of the [alsa driver (1.0.14rc3)]("http://article.gmane.org/gmane.linux.alsa.devel/45323") is out with this (and probably other) patch. Reading the posts on the list, it seems there are however some problems with compiling the driver.

Hope this helps you. I'm not 100% sure about the code above but it was something like that which I did. I still don't have the internal mic working, but haven't bothered to really look into it.

---

### Post by lexarrow on 2007-05-26
maybe [this]("http://ubuntuforums.org/showthread.php?t=455147") could help

---

### Post by szabodabo on 2007-05-29
Ubuntu Feisty 7.04 fixes all the sound issues for me...
dv2000t CTO.

---

