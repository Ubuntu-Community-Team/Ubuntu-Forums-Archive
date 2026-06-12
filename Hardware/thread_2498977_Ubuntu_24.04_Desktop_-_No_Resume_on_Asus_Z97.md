---
title: "Ubuntu 24.04 Desktop - No Resume on Asus Z97"
date: 2024-07-06
forum: Hardware
---

### Post by tedman2 on 2024-07-06
I have installed Ubuntu 24.04 Desktop on a ASUS Z97 WS Motherboard.
Very pleased with it and happy to escape from Microsoft.

Unfortunately the resume after suspend function does not work, and my PC just hangs until I do a hard reset.

I am also experiencing very long boot times.

Has anyone else had this problem ?

---

### Post by tedman2 on 2024-07-06
Situation sorted !

There is a modified GPU driver available on my system, and now all works well.

Also, I have taken the SSD out of my Z97 machine, and put it into a Asus B85M machine, and it all worked just fine too, complete with resume.
It was seeing this that got me to make the connection with the GPU, as on the B85M machine the system automatically selected the appropriate driver.

---

### Post by oldfred on 2024-07-06
Some suggestions for tuning for faster boot.
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2496312&p=14183456#post14183456](https://ubuntuforums.org/showthread.php?t=2496312&p=14183456#post14183456)

[https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster](https://askubuntu.com/questions/1284302/is-it-possible-to-make-ubuntu-20-04-boot-faster)

I had an Asus Z97, that died a couple of years ago.
Now using Z170.
Stopped using GPU back with Z97 as found the Intel video was faster than the older video card I was using. I do not game, so just want decent performance.

```
https://www.videocardbenchmark.net/low_end_gpus.html 
GeForce GT 620              430
 Intel® HD Graphics 4600    712  Haswell                 
Intel HD Graphics 620       927  Skylake


```

---

