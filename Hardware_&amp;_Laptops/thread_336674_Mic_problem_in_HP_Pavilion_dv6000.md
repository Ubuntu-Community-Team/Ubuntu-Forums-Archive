---
title: "Mic problem in HP Pavilion dv6000"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by chinthaka on 2007-01-11
I have Ubuntu Edgy installed in my HP dv6000 series laptop. Speakers in my laptop are working fine but mic seems to be not working. 
I followed this [thread]("http://ubuntuforums.org/showpost.php?p=1914583&postcount=16") and installed the latest version of alsa driver. 
alsamixer doesn't list my internal mic and mic still doesn't work.

Here is my configuration.

lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

cat /proc/asound/card0/codec#0 | grep -i codec
Codec: Conexant CXT5045

Any help to fix this is very much appreciated as now I must log in to windows to use Skype ](*,) 

Thanks,
Chinthaka

---

### Post by tommcd on 2007-01-12
There is another thread on the very same HP computer. See this from the wiki:
[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29](https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29)
EDIT: Here is the thread:
[http://ubuntuforums.org/showthread.php?t=321187](http://ubuntuforums.org/showthread.php?t=321187)

---

### Post by chinthaka on 2007-01-21
I followed those two threads also. But the problem is still there :(

---

### Post by olavjunior on 2007-02-14
I have the problem with my dv2130. 

I tried installing the rc2 drivers from alsa, but it didn't change a thing :(

I need help!! And I'm a newbie :(

---

### Post by arnomuhren on 2008-02-08
I have a HP DV6000-series laptop and had to enable the capture-element in the alsa-mixer Edit-Preferences. You might have already tried that?

---

