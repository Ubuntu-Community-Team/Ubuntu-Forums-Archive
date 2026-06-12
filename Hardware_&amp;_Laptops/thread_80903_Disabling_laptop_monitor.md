---
title: "Disabling laptop monitor"
date: 2005-10-23
forum: Hardware &amp; Laptops
---

### Post by damaged on 2005-10-23
Hi,

I am currently trying to use an Acer 521iT laptop as a terminal box and
have a Polyview monitor and a keyboard and mouse which I have configured
to run with the laptop. 

I am having a problem getting the display to be anything other than
800x600 at 85hz. I tried fiddling with xorg.conf to allow other resolutions
and VertRefresh rates but apparently the laptop "panel" won't allow this and the logs contain this :

(II) ATI(0): Not using default mode "1024x768" (exceeds panel
dimensions)

This causes both monitors to run at 800x600 and 85Hz. So the laptop
monitor is capping off what both monitors run at. 

How can I get the Polyview to run at a higher resolution?

I get the feeling that I have to disable the laptop's monitor in order to prevent this
from occurring. The Polyview would then be free to run at higher res/refresh rate. Or is there another way?

Can anyone shed light on this problem? Any help would be appreciated.

I can provide the log files if they will help.

Thanks

---

