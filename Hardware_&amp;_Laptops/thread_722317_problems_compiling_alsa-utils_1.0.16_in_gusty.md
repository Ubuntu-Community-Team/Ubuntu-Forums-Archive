---
title: "problems compiling alsa-utils 1.0.16 in gusty"
date: 2008-03-12
forum: Hardware &amp; Laptops
---

### Post by mab1376 on 2008-03-12
im trying to compiling the new alsa utils with the new alsa dirver and it just not working.
i installed the :

build-essential linux-headers-generic libncurses5 libncurses5-dev libasound2 libasound2-dev 

and i get this error

```
mark@mark-laptop:~/alsa/alsa-utils-1.0.16$ make
Making all in include
make[1]: Entering directory `/home/mark/alsa/alsa-utils-1.0.16/include'
make  all-am
make[2]: Entering directory `/home/mark/alsa/alsa-utils-1.0.16/include'
make[2]: Leaving directory `/home/mark/alsa/alsa-utils-1.0.16/include'
make[1]: Leaving directory `/home/mark/alsa/alsa-utils-1.0.16/include'
Making all in alsactl
make[1]: Entering directory `/home/mark/alsa/alsa-utils-1.0.16/alsactl'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/mark/alsa/alsa-utils-1.0.16/alsactl'
Making all in alsaconf
make[1]: Entering directory `/home/mark/alsa/alsa-utils-1.0.16/alsaconf'
Making all in po
make[2]: Entering directory `/home/mark/alsa/alsa-utils-1.0.16/alsaconf/po'
mv: cannot stat `t-ja.gmo': No such file or directory
make[2]: *** [ja.gmo] Error 1
make[2]: Leaving directory `/home/mark/alsa/alsa-utils-1.0.16/alsaconf/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mark/alsa/alsa-utils-1.0.16/alsaconf'
make: *** [all-recursive] Error 1
```

what can i do?

---

