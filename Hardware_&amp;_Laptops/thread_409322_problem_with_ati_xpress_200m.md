---
title: "problem with ati xpress 200m"
date: 2007-04-14
forum: Hardware &amp; Laptops
---

### Post by inspiteofmyself on 2007-04-14
im sure you guys have seen tons of posts on ATI hardware in the past...and trust me, so have i...ive scoured this forum for information.

last night i installed ubuntu (first time ubuntu user, but im straight from debian so its not that much different)

anyway, i used envy last night after trying several custom package builds myself of the official current ATI drivers which got me nowhere. after doing whatever i did before running envy, and then getting to where i gave up on doing it manually and running envy...i had it all working fine. then for whatever reason i decided i wanted to reinstall ubuntu from the same cd, and use the same install of envy to get things going...all went well, and seems well to me, but when i get into the xserver, glxgears, and fgl_glxgears run just fine...the GL screensavers are running like they are not accelerated at all though.

here is the necessary output of the 2 glx info programs:

```

root@fluid-laptop:/home/fluid# fglrxinfo | grep vendor
OpenGL vendor string: ATI Technologies Inc.

```

```

root@fluid-laptop:/home/fluid# glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: ATI
OpenGL vendor string: ATI Technologies Inc.

```

i did try the stock open-source (ubuntu included) accelerated drivers, but they did not seem to work at all on my chipset, despite the fact that the guide for them claim it will do 2d acceleration. i also undid all of those changes to xorg.conf when i was done, so it was stock when i ran envy...and i let envy modify it just as i did last night when i had everything working.

the only funny thing i see above is that ATI is the client vendor, but SGI is still the server vendor...that may not be too funny, not sure if thats needed or not.

im almost positive that some GL library that should be used is not being used, or the wrong version is being used because of a bad symlink.

anyone able to help me out with this?

---

