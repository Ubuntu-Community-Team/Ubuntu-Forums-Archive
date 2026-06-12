---
title: "ATI Radeon 7500 3D acceleration"
date: 2008-03-17
forum: Hardware &amp; Laptops
---

### Post by cptn. Cookie on 2008-03-17
Hi all,

I installed Ubuntu 7.10 a few days ago. I like to play some games, so I installed Cedega. The Cedega tests gave me an 'OpenGL rendering: succes', but 'Direct Rendering: Failed'. 

This:

```

$ glxinfo | grep rendering

```

gave me:

```

direct rendering: Yes

```

So I thought, the failed Direct Rendering must be some misconfigured setting or something. I reconfigured the X-server:

```

$ sudo dpkg-reconfigure xserver-xorg

```

But, when it was finished, it gave me:

```

direct rendering: No

```


It now uses the 'ati' driver, but it doesn't matter if I use the radeon driver instead. 

According to this site:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

the radeon 7500 should have full 3d acceleration with the opensource driver. Does anyone has an idea?

TIA,

--

EDIT:

I have Direct Rendering back, turns out I just had to remove the fglrx driver. Cedega now gives me the 'OpenGL rendering: Yes', but 'Direct Rendering: no'. Glxgears also just gives me an FPS of around 380fps. What should I do?

---

### Post by erginemr on 2008-03-17
For the 3D ATI driver, make sure that the driver inside xorg.conf file is "fglrx", not "ati".

As for the Cedega reporting erroneous direct rendering information, this has also happened to me when I tried Cedega. I think this is a bug and you should spend some time in Cedega forums. A quick Google search game me the following link, which may help:

[http://www.cedega.com/forum/viewtopic.php?t=5072](http://www.cedega.com/forum/viewtopic.php?t=5072)

---

