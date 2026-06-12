---
title: "MyOwnLiveCD Beryl installation problem (to do with ati dirvers)"
date: 2007-04-17
forum: Hardware &amp; Laptops
---

### Post by Koziasty on 2007-04-17
Im in progress of doing my own personalised live cd. I would like it to run beryl. Funny thing is, I run beryl on my laptop with no problem, but cannot do so in the chroot environment. THe reason is, I cant install Tungsten drivers. I follow the very same guide I used making the laptop working. 

After doing 
```
sudo apt-get install libgl1-mesa-glx libgl1-mesa-dri
```
in the chrooted environment, I get the message its already installed. I use the very same xorg.conf I use on the laptop. 
And yet, instead of 
```
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

```

I get
```
OpenGL vendor string: Mesa (can't remember the numbers)
```

I would greatly appreciate any help :)


If its the wrong topic to put this post in, im sorry, could you please move it somewhere more appropiate?

---

