---
title: "Acer Travelmate 800"
date: 2017-02-03
forum: Hardware
---

### Post by Roland_Msl on 2017-02-03
After I had installed Linux Ubuntu on 4 notebooks, I tested Ubuntu 16.10 on my old Acer Travelmate 800.

The fan was running nearly all the time, compiz used nearly 100% CPU.

I started Firfox and tested YouTube with [this video](https://www.youtube.com/watch?v=sLo3Pn4KC3w) full screen.

The Acer 800 was connected by WLAN.

About one frame per second, only about half the video shown, when the time of the video was finished.

I tested the same starting Windows XP and with Chrome:

The video showed with some  jerks, but far better than with Ubuntu 16.04 32 Bit version.

I read some pages found by "Acer travelmate 800 Linux" and all stated a better performance than with XP,
so what can be wrong, that I see the opposite?

---

### Post by DuckHook on 2017-02-04
The Travelmate 800 is definitely on the light side for a modern OS, but that would not account for the CPU racing that you saw. In my experience, this is usually caused by a driver or compiz issue&#8230; which leads us to your next statement&#8230;

Comparing Ubuntu Xenial/Yakkety to XP is comparing apples to spaceships. You are talking about a modern OS vs one first written *15 years ago.* For a fairer comparison, let us know how Windows 10 runs on that machine.

However, the truly amazing thing is that, had you stayed away from Ubuntu and used one of the light-weight flavours, your experience would have been far different. Lubuntu for example, despite being 15 years further evolved than XP, would probably still run reasonably well and furthermore, give you the option of a FOSS lightweight browser (try Midori) that combines for a level of performance actually superior to XP+Chrome. I don't know of any other modern OS that could come close to keeping that old laptop of yours even remotely relevant for today's use. Windows? MacOS? Not a chance.

Your laptop was a lightweight even for its own day. It is woefully, laughably underpowered today. For such machines, the ironclad rule is: don't run anything 3D on them. Your video card is only 64MB. All of your system resources get used up painting spinning icons and wobbly windows. That rules out Ubuntu, Ubuntu-Gnome and Kubuntu right from the get-go. Your choices are Lubuntu, Kubuntu or Ubuntu-Mate. If you want to go really light, leave the 'buntu family altogether and try Puppy, Slitaz or even Tiny Core. Those distros will just scream on your system and they are *still modern OSes!*

As for your last question: when were those "pages" written? The Linux of 10 years ago ran circles around XP. I should know. That performance difference was what brought me to Linux.

PS

You might consider reading the link in my signature: Resurrecting Old Hardware.

---

### Post by Roland_Msl on 2017-02-04
Until now, the oldest notebook, I installed Ubuntu 16.04 ASUS UL30A, has 4 GB RAM and a Dual Core Ultra Low Volt 1,3 GHz CPU. Perfect performance.
Was even better in the run time test, because Windows 7 startet a background job with 100% CPU usage.

So I was very surprised at the Acer Travelmate 800, 1,3 GHz Centrino with 2 GB RAM is such a problem.

---

### Post by DuckHook on 2017-02-04
You didn't provide specs. The website tells me it's native config is 256 or 512 MB with a single core CPU and 64 MB GPU. These would be very low specs by today's standards. The video system is especially anemic and was designed for the 2D graphics of its day.

But as mentioned, your CPU race condition is not normal, even for an underpowered machine. If you really want to try it on Ubuntu (not recommended for reasons already stated) you can try by investigating video bottlenecks.

---

