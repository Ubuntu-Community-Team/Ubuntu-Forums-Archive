---
title: "Ubuntu 12.04 doesn't recognize Intel HD 3000"
date: 2012-08-04
forum: Hardware
---

### Post by tehwizardd on 2012-08-04
Hi!

I have MSi620 GX laptop with Intel HD 3000 and Nvidia Geforce GT635M gfx cards. Yes, I know, I have Nvidia Optimus.

My problem is that 12.04 or 12.10 Ubuntu doesn't notice my Intel HD 3000, that is on as default in my system. In the system info, it says unknown for graphics.

It does give my full resolution, but doesn't allow me to run any 3d application. I can't run Unity 3d or Gnome 3. Always fallback mode. 

Now, I downloaded Fedora 17 and installed it. Everything working out of the box. It does have 3.4 kernel, while Ubuntu has 3.2. Actually Fedora 17 did update to 3.5 last night. I do not believe that this is about kernel, since Intel HD 3000 is one of the most used graphics cards out there and it sure has been supported from 2.x.xx kernel.

I have been told to install mesa-utils and no help.

This is quite weird since Fedora 17 I am able to use Intel HD 3000 and then switch to Nvidia with bumblebee when ever needed. No problems at all. I just use optirun [software] to get the Nvidia card running.

---

### Post by tehwizardd on 2012-08-06
Anyone?

---

### Post by pldaniels on 2012-09-23
Have a Toshiba C665 with HD3000, also comes up as "unknown" and has the same problem you're experiencing, everything goes in to fallback mode :(

I've tried the  apt-get remove mesa-utils  and then reinstalled to no avail (after a reboot between each).

---

### Post by tehwizardd on 2012-09-25
> **pldaniels said:**
> Have a Toshiba C665 with HD3000, also comes up as "unknown" and has the same problem you're experiencing, everything goes in to fallback mode :(

I've tried the  apt-get remove mesa-utils  and then reinstalled to no avail (after a reboot between each).
Yeah, I sold my laptop. It worked only under Fedora 17, it recognized HD3000. You should also try it.

---

