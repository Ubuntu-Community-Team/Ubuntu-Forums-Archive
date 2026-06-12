---
title: "Conky GPU Usage"
date: 2011-04-08
forum: Hardware
---

### Post by motonnerd on 2011-04-08
First off:  I've loved conky almost ever since I've started running Ubuntu.  I recently got my hands on AMDOverdriveCtrl and started looking at my idle GPU usage.  I noticed (through conky dying on me as I messed with settings) that conky pushes my graphics card (ATi Radeon Mobility 5000 series) from the lowest clock setting to the highest, and that's about a 3-degree C change in temperature, and a .3-volt increase to the card.

Whether or not this will make a noticeable difference in battery life, I don't know; however I dislike it on principle and am interested to hear if someone has dealt with this problem.  I find that disabling double buffering in conky's configuration, while making Conky flicker at every update, seems to ease the load on the graphics card, merely creating a small spike every time conky refreshes.  I like to think I've ruled out AMDOverdriveCtrl itself causing the spikes due to monitoring; varying the monitoring interval an order of magnitude produced no positive change in the readout.  Something else the reader may find interesting:  when double-buffering, conky would 'hide' (until mouseover, then they would flicker) my desktop icons, whereas with single-buffering they are constantly visible.  As I think about it, I suspect some interplay between conky and compiz, however even in windowed mode conky still clocked up the GPU.  Maybe there's a way to change the criteria for which the fglrx driver will clock up the GPU?  (Didn't see anything of interest in /etc/ati/)

For anybody interested, I'll include the output of lspci, lshw, and lsmod in a tarball.  Any more information you want or suggestions you have I will happily test, but I realize that I'm likely to have to choose between conky and that small reduction in heat and power usage.

As mentioned before, I'm running fully-updated Ubuntu 10.10, conky, compiz, and now Guake (though the problem existed before guake, and the test which showed the radical contrast was done with everything running)

Thanks for your help!

---

