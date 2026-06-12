---
title: "[resolved] Sound on HP4150a Onmibook"
date: 2004-12-01
forum: Hardware &amp; Laptops
---

### Post by DougInKY on 2004-12-01
I have a Hewlett Packard Omnibook 4150a laptop that I can't seem to be able to get sound running in Ubuntu with. I had been running Mandrake 9.2 on it and could (can) set the sound up by running sndconfig and telling linux that is was a ad1848 soundcard even though it showed as a MagicMedia 256AV when probed. I have been reading everything I could (Running Linux, Linux Power Tools, ALSA Howto) and am reaching the frustration point as I still cant get a squeak out of it under ALSA. My sound lines from my Mandrake 9.2 modules.conf (I think it is a OSS kernal) is listed below:

alias sound-slot-0 ad1848
options sound dmabuf=1
alias synth0 opl3
options opl3 io=0x388
options ad1848 io=0x530 irq=5 dma=1 dma2=0

Any help would be appreciated.
TIA, Doug

---

### Post by DougInKY on 2005-01-01
I have marked this thread resolved as I hadn't had any replies in quite a while. I gave up and went back to using Mandrake 9.2 which works like a champ on this old tired laptop. As I said in my original post, I can make sound work with a 2.4 kernel, just not with a 2.6 kernel. I guess this is another piece of older hardware that has lost support in the new kernel. I really hate that, but I guess this is the price of progress. I am running Ubuntu on my desktop computer so I still get to use this really nice distro. Just not on my laptop. :cry: 

Doug

---

