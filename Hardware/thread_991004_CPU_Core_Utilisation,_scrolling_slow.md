---
title: "CPU Core Utilisation, scrolling slow"
date: 2008-11-23
forum: Hardware
---

### Post by skyh on 2008-11-23
Okay, so I've done a good amount of searching on this topic, but haven't found anything in particular, so I'm posting here.

I'm running Ubuntu 8.10, and the GUI is slow in general, especially scrolling, and particularly in Firefox. Disabling Compiz helps this, however it's still slow and very CPU intensive. I know that part of the reason, I'm sure, is the quality of the ATI drivers (I have the XPress 1250, using fglrx), however there's little reason it should be so bad.

Anyways, onto the real issue.. When I want to scroll quickly, my CPU Scaling has to jump from 800 MHz to at least 1.6 GHz, ideally max at 1.9 GHz. HOWEVER, when I look at the System Monitor, the firefox process is only using 7% CPU!

So, if you look at the graph for CPU Core utilisation, you see that (in my case) the second core is around 75-80% usage, while the first is sitting around 10% or less. Keep in mind, this is with me continually scrolling up and down on a webpage quickly... and not even a page that is terribly complicated.. I even test it on the composition page for this post!
Then, looking at the graph overall, it seems like the second core is usually being utilised a lot more, especially when it comes to graphical things.

Anyways, any suggestions or insights from anyone, as far as if there's anything I can do?

---

### Post by Yezinki on 2008-11-23
Hi there,

Try keeping both CPUs i.e 0 & 1 ON DEMAND......not one on Performance & other On Demand.

It helped me when I was using 8.10.

The scrolling & FF were very sluggish, when I had kept them on different settings.

Good Luck.

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-23
On Demand, with Normal visual effect but not using Compiz, it was always around 55%CPU usage for both.

---

### Post by skyh on 2008-11-25
Yezinki, thanks for the responses.

I haven't played around with individually setting the scaling for each core, and although I'm not terribly sure how to do that, I'll go check it out.

And I see you said about 55% usage for both cores... that's the biggest thing with mine, is that it's so lopsided on one core. Cause then when one core is getting used up around 80%, it has to change the frequency to compensate. I'm going to go plunk around more, and I'll let you know what comes up..

---

### Post by skyh on 2008-11-25
Alright, as far as I can tell (according to the frequency scaling gnome app), both cores are set to the same scaling profile -- OnDemand. I don't know of a way to set them individually, and it'd be strange that they would be different from each other at this point, although I not sure of how to know for certain.

---

### Post by Yezinki on 2008-11-25
Hi there,

Rt click on the top panel> add gadget> CPU scaling & than configure.

Regards,

Yezinki.

---

### Post by skyh on 2008-11-26
That's what I did.. and I have two gadgets on my panel, one per core. However, if I change the governor or frequency for one core, the other changes as well.

Is this not the way it should work?

---

### Post by markbuntu on 2008-11-26
I would suspect from the symptoms you describe that fglrx is misinstalled and has reverted to the indirect mesa drivers instead of using direct rendering. What does fglrxinfo have to say?

---

### Post by skyh on 2008-11-27
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon X1200 Series
OpenGL version string: 2.1.8087 Release

$ glxinfo | grep 'direct'
direct rendering: Yes

I'm not confident that direct rendering is being utilised correctly anyways, as I would assume my gui wouldn't need my processor running at 100% at 1.9 GHz to work smoothly, but the system tells me otherwise, so I'm not sure what to think.

---

### Post by skyh on 2008-12-01
Okay, I cannot seem to be able to set the frequency or governor for individual cores as Yezinki suggested.. if I change the frequency or governor of one core, the other core changes right with it.

Now, I don't know if that's supposed to be the correct behavior, or if it should be otherwise.. any ideas?


EDIT:

Nevermind, I found cpufreq-info, and according to it is says that my cores must change frequency at the same time, so that's obviously a non-issue... now it's just a matter of figuring out why the firefox gui when I try to scroll zaps away at my second cpu core, and uses it at 80%, and practically leaves the first core alone..

---

