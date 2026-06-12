---
title: "GPU Monitoring Tool Ubuntu 15.10/Zorin OS 11"
date: 2017-07-14
forum: Hardware
---

### Post by goostech on 2017-07-14
I daily use a Thinkpad T61p and I think my CPU is Bottlenecking my GPU but I cant tell whenever i use 720P HD video the CPU is pegged at 100% vs 480P where the peak CPU usage is 48%, but i have no way of monitoring the GPU, I need a tool that will monitor my GPU usage, a GUI would be preferred, Memory Usage and GPU Frequency. Nvidias X.Serve Tool doesn't work and I have about 3.0% experience in the Terminal my Specs are below.


Model: Thinkpad T61p 6459-CTO
CPU: Core 2 Duo T9500
GPU: Nvidia Quadro FX570M
RAM: 4GB DDR2

---

### Post by again? on 2017-07-15
You can try this command in terminal although what you want may be unavailable.
```
watch -n 0.5 nvidia-smi
```
ctrl+c to exit.

---

### Post by dragonfly41 on 2017-07-15
GKrellM System Monitor is a GUI which monitors many variables.

If you have Synaptic Package Manager search for "gkrellm".

You can extend with plugins.

Setup Configuration by right click on the GKrellM popup widget.

---

### Post by efflandt on 2017-07-15
**psensor** can be useful for monitoring CPU and GPU. In my case it indicates that maybe I should get a better cooler since upgrading my old i5 650 to i7 870 with the stock Dell cooler from the i5. It also shows that I am making use of upgrading my RAM from 8 GB to 16 GB with no swap and using tmpfs for /tmp with my SSD. Although, a vast majority of that is caching things I have done and could be freed up if needed. I was able to up graphics settings in games since upgrading my CPU without losing speed, but not sure if the max 71% of CPU use was due to thermal throttling. I have seen at least one core temp as high as 87 C with 59% max CPU use.

It also tells me that the 3 GB GTX 1060 works fine for me @ 1080p using 40% of its VRAM, so I would not really take advantage of the 6 GB model. Even Unigine Heaven benchmark in Extreme settings with full tessellation used 75% of its VRAM. And it works fine with my old PCIe 2.0 bus which never goes to 100%.

A terminal program that can show core use of multi-core processors is **htop**.

But your OS no longer has support, so you might consider Ubuntu 16.04 LTS (long term support) version or something based on it.```
~$ free -h
              total        used        free      shared  buff/cache   available
Mem:            15G        1.6G        2.9G        320M         11G         13G
Swap:            0B          0B          0B
```

---

