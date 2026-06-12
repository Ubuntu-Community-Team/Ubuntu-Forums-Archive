---
title: "GSynaptics problem"
date: 2009-02-28
forum: Hardware
---

### Post by MarkenK on 2009-02-28
Hello!
I'm a newbie at linux. My Dell Inspiron 1525's touchpad is rather vague. I hoped to improve that by downloading GSynaptics. I can't start the problem because it says, that i cave to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

I found xorg.conf at /etc/x11/ but there is no Synaptics section. I haven't found XF86Config at all.

here's the link for GSynaptics. It says pretty much the same thing: 
[http://gsynaptics.sourceforge.jp/](http://gsynaptics.sourceforge.jp/)

I could really use some help with that, or if that's not at all the correct way to improve my touchpad, then any help on that.

Thanks in ahead!

---

### Post by Tweak42 on 2009-03-05
Starting with 8.10, I think they stopped using xorg.conf for enabling "SHMConfig"

I got my gsynaptics running following the guide here:

[https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig](https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig)

---

