---
title: "MSi GE620 - Graphics drivers"
date: 2011-09-21
forum: Hardware
---

### Post by exonwarrior on 2011-09-21
I am having trouble with graphics acceleration on my laptop. I installed Ubuntu 11.04, it boots OK. However, I have trouble with the drivers. I can use the Recommended driver, and then Unity doesn't work, or I can use Nouveau, but I can use any of the flashy cool stuff. I believe that the "GPU Boost" that it has, that is, an Intel integrated GPU and a nVidia dedicated GPU is screwing it up. Any ideas?

Thanks,
Dave

---

### Post by realzippy on 2011-09-21
Unity should run also run on your intel device,you need kernel 2.6.38.11
and the latest mesa,libdrm,intel driver aso....
Make sure to uninstall the nvidia-driver....

post output from

```
uname -a
```

```
lspci | grep VGA
```

---

### Post by exonwarrior on 2011-09-21
uname -a
```
Linux dave-msi-ubuntu 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```
grep
```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1)
```

I'll try playing around with drivers. That'll suck though if I try to play any games...

Thanks,
Dave

---

### Post by realzippy on 2011-09-21
Install bumblebee to use your nvidia card for games...
Eg the procedure given here:
[http://ubuntuforums.org/showpost.php?p=11264875&postcount=26](http://ubuntuforums.org/showpost.php?p=11264875&postcount=26)

---

