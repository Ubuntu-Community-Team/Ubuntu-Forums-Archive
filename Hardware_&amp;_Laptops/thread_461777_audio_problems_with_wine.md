---
title: "audio problems with wine"
date: 2007-06-02
forum: Hardware &amp; Laptops
---

### Post by joy83 on 2007-06-02
when i configure wine it tells me that there are some audio problems since the driver is not installed??, this is the error that it gives me

fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

I started installing Rise of nations, before installing it tells me that it will install but i wont be able to hear the sound.

how do u rectify that.

---

### Post by joy83 on 2007-06-02
now i installed that library and it didnt give me an error when i went to the audio options of winecfg, but when i started to install rise of nations, it tells me that no sound card is detected. whats the problem?

---

### Post by cptcrunch on 2007-06-02
wine is not perfect, and in fact won't run every windows app. There is CrossOver Linux. The problem is it's not free software :(

I see Rise of Nations is untested.

codeweavers.com

---

### Post by crimsun on 2007-06-03
> **joy83 said:**
> when i configure wine it tells me that there are some audio problems since the driver is not installed??, this is the error that it gives me

fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

I started installing Rise of nations, before installing it tells me that it will install but i wont be able to hear the sound.

how do u rectify that.

The libjack.so symlink is provided by the libjack0.100.0-dev package.

---

### Post by YokoZar on 2007-06-03
Select ALSA or OSS for your sound driver in winecfg, you shouldn't need Jack anyway.

---

