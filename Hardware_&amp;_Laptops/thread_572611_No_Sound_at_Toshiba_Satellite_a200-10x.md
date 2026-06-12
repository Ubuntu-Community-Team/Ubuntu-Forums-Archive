---
title: "No Sound at Toshiba Satellite a200-10x"
date: 2007-10-10
forum: Hardware &amp; Laptops
---

### Post by ShadowDeath on 2007-10-10
Hello everyone...
well i just installed Ubuntu and i have some problems...

first of all i have no sound at all... as i searched inside the OS i found that i m using a Realtek ALC861-VD "mixer" or something...
i downloaded the realteck sound drivers from the official site of Realtek.... and instead of fixing it i had another problem at reboot... a file was missing (libasound.so.2) well i downloaded that file again and got access at X11 again...

i searched the threads here in forum for some help and i found a guide about Satellite L35 i think... well i tried to follow that guide... and another error appeared... the one i can't fix it :(

i downloaded the latest alsa drivers but when i m about to configure it i get this message:

```
shadowdeath@ShadowDeath:~/alsa-driver-1.0.14$ ./configure
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
```

I have the installed the latest linux-kernel-headers & build-essential packages but nothing at all....

Also i read another post that someone made a link to /usr/bin from "gcc" to "gcc-4.1" i checked that and it is done already!

what else do i have to do?!

---

### Post by ShadowDeath on 2007-10-11
Well at last no problem :) i fixed it...

i just had to re-install "gcc" + "gcc-4.1" and that's all... everything worked fine! :)

Please close that topic...

Regards,
*ShadowDeath*

---

