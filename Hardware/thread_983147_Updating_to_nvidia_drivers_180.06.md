---
title: "Updating to nvidia drivers 180.06"
date: 2008-11-15
forum: Hardware
---

### Post by AndersAA on 2008-11-15
I wanna keep this system as clean as possible, it's my non experimental system, and I want to stay as far away from dirty hacks as possible and keep all stable packages, the nvidia driver in ubuntu however has some bugs that makes things rather unpractical for me, which apperantly have been fixed in 180.06.

Now I've found ways to update using the nvidia installer, but that doesn't look like a very clean approach, especially if I find other issues with the new driver and need to revert to the officially supported one.

Whats the clean way of using a non supported driver?
If a bug is tracked, the fix in the nvidia driver is upstream and a developer needs people to test it, whats the suggested way of doing so, without screwing with future updates?

---

### Post by Skripka on 2008-11-15
Which version of Ubuntu are you using?  I find that the 177.80 driver in the Ibex repos works like a charm on my GTX260.


If you want to use an unsupported driver, you'll need to download the *.run installer of Nvidia's website, and get thee to a Terminal.  Synaptic or envy, or *.run are your only options for installing Nvidia drivers.

---

### Post by oldsoundguy on 2008-11-15
Envy does not work for Intrepid right now .. they are working on it, but nothing thus far.  The drivers for NVidia in Intrepid are all incomplete at present.  Bare bones that work but no bells and whistles. (no screen rotate, difficulties with programs such as Compiz, Problems with resolution and refresh rates and wide screen and so on.

The blog on the Envy site has an explanation and more complete information.

So those of us that have gone to Intrepid "make do" right now.

---

### Post by Skripka on 2008-11-15
> **oldsoundguy said:**
> Envy does not work for Intrepid right now .. they are working on it, but nothing thus far.  The drivers for NVidia in Intrepid are all incomplete at present.  Bare bones that work but no bells and whistles. (no screen rotate, difficulties with programs such as Compiz, Problems with resolution and refresh rates and wide screen and so on.

The blog on the Envy site has an explanation and more complete information.

So those of us that have gone to Intrepid "make do" right now.

So 'tis an Ubuntu thing then-without a need for Compiz I wasn't even aware of that.

---

### Post by oldsoundguy on 2008-11-15
It is actually the NVidia drivers FOR Ubuntu, not Ubuntu itself that is at fault according to that blog.  NVidia does not write legacy drivers for Linux anymore.  They turned that job over to Alberto and his crew at Envy (that blog will tell you all about it.)

There also seems to be SOME issues with ATI and 8,10, but I have not kept abreast of those.

I have the NVidia Linux forum and the Ubuntu Launchpad in tabs on my browser and thus far have received NO response from Launchpad and it's supposed gurus and no official response from NVidia (just a couple of replies to questions asking why? and stating they had the same issues.)

---

### Post by AndersAA on 2008-11-15
I'm not talking about legacy drivers, I'm talking about bugs in the current drivers, specifically huge delays on resume from suspend 2 ram (I'm having resume triggered through wake on lan, and the huge delays are causing network timeouts).

---

### Post by oldsoundguy on 2008-11-15
legacy drivers = drivers for cards older than 6 months that have gone out of production.  
In other words, if they are not the hot new item and came out 6 months ago or longer, NVidia no longer writes the drivers for Linux.  They have farmed that out.

---

### Post by AndersAA on 2008-11-15
I'm fully aware of that, since topic start I've listed 180.06 which is not the legacy drivers.  And do work on ubuntu intrepid.  The problem is installing them will screw up symlinks etc for current opengl versions, making it impossible to cleanly reset to the officially supported drivers.

---

