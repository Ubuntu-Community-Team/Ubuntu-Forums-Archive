---
title: "Reverting back to open-source AMD video drivers"
date: 2015-05-03
forum: Hardware
---

### Post by sbennettgso on 2015-05-03
I have an AMD A6-3500 Llano processor with Radeon HD 6530D embedded graphics.

I just installed 15.04 and, as is what I normally do, switched to the proprietary driver using the "Additional Drivers" tool.  But it's giving me some issues, particularly with Chrome, so I tried to switch back to the open source display driver wrapper from xserver-xorg-video-ati.

When I first installed 15.04 and I presume the open-source wrapper was being used, my monitor resolution was detected correctly.  But when I switched back to it, I only have one resolution and it's lower than it was previously.  In troubleshooting, the "Additional Drivers" tool says I'm using a manually-installed driver, not the one I wanted.  And all my options to switch are greyed out.

So how do I get back to the default install configuration?

Thanks,
Scott

---

### Post by sbennettgso on 2015-05-03
OK, was able to fix this based on information here:

[https://mwop.net/blog/2014-11-03-utopic-and-amd.html]("https://mwop.net/blog/2014-11-03-utopic-and-amd.html")

Basically I opened a terminal and entered these three lines:

> $ sudo apt-get purge 'fglrx*'
$ sudo update-alternatives --remove-all x86_64-linux-gnu_gl_conf
$ sudo apt-get install --reinstall libgl1-mesa-dri libgl1-mesa-glx

After a reboot, it seems to be working properly now with the right resolution, monitor detection, and all that.

Thanks,
Scott

---

### Post by Bashing-om on 2015-05-03
sbennettgso; Great !

such an elegant solution - update-alternatives -

Appreciation for adding to our store of knowledge.

[INDENT][INDENT]good things do happen
[/INDENT][/INDENT]

---

