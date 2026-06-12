---
title: "External USB 3.0 hub -&gt; khubd and worker threads take 25% CPU"
date: 2015-02-24
forum: Hardware
---

### Post by warsev on 2015-02-24
I have a HP Pavilion 17-e049wm laptop running ubuntu 14.10. It has two USB 3.0 ports. Normally when the machine is idling it will use 0% to 1% of the CPU. Same with USB 3.0 external disks plugged into those ports.

As soon as I plug an external powered USB 3.0 hub into one of those ports, khubd starts using about 7% CPU and an additional 4 kworker threads appear that between them use another 18% of CPU. Total about 25% of CPU time. That's with just the external hub plugged in, no disks.

But it gets weirder. When I unplug the external hub, khubd and the kworkers *continue* to soak up 25% of the CPU. The only way to put things back to normal is to either reboot or manually shut down and restart the xhci_hcd driver for the internal hub that services those two USB 3.0 ports.

This is a real pain. I have to keep the external hub disconnected, and then after I've used it I have to manually stop and restart the driver for those ports.

Anyone have any idea what's going on and how to fix it?

Thanks!

---

