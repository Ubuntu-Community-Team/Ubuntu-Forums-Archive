---
title: "Use Bumblebee with NVIDIA drivers from nvidia.com"
date: 2015-02-02
forum: Hardware
---

### Post by Samarth_Brahmbhatt on 2015-02-02
Hi, can you help me with using the latest NVIDIA drivers from the NVIDIA website (using a .run file) with Bumblebee? Bumblebee project webpage recommends us to use drivers from apt-get, and does not talk about this. I suppose one needs to make some changes to /etc/bumblebee/xorg.conf.nvidia and /etc/bumblebee/bumblebee.conf.

I need the drivers from the website because
[LIST=1]
[*]I want to use the latest CUDA toolkit
[*]CUDA installed through the ubuntu package nvidia-cuda-toolkit does not seem to work with proprietary drivers from the ubuntu package nvidia-331-dev (the deviceQuery example fails).
[/LIST]

Thanks!

---

