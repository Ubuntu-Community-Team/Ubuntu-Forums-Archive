---
title: "Re-Building an Old PC"
date: 2013-02-06
forum: Hardware
---

### Post by gerowen on 2013-02-06
So I'm re-building an old emachines I was given, and I have a couple of questions.

It has 1 GB of RAM and an Intel Pentium 4 @ 3.00 Ghz that reads "EM64T Capable".  I installed the 64 bit version of Ubuntu 12.10, but it seems to be "really" sluggish at times, particularly if I try watching a full screen flash video from pretty much any website.  I see in the BIOS that Hyperthreading is available and enabled.

Anyway, I'm wondering if the 32 bit version would offer better performance, or if it wouldn't make a difference since this processor is apparently 64 bit.  It's an emachines W3615 that was given to me by a neighbor who didn't want it, so I replaced the CPU fan because the old one had worn out and was rattling around inside its housing, put some fresh thermal paste on it and cleaned it out, and I'm giving it to my mother-in-law to use as a general web browsing computer, but it's performance is not all that pleasing at times.

I guess my question is, given the information above, what could I do to improve performance of Ubuntu?  I'm currently using Unity, but in my experience using 12.04 a while back, switching from Unity to Ubuntu's version of Gnome 2 didn't really make any difference as far as system performance, so I'm hesitant to start messing around with other desktop environments.

**Edit:** Another question.  I've applied fresh thermal paste and put a new fan on top of the heat-sink blowing down.  When I first started the computer the CPU was at around 52 degrees celsius according to the "Hardware Monitoring" section in the BIOS.  That was after having been shut off for a few days and having just had the thermal paste and heat-sink re-applied, so that was as cold as it was going to get.  I booted Ubuntu, played a few high def videos on YouTube to get the CPU cranking and the fan speed has increased, then I rebooted to get into the BIOS and look at the temps. (lmsensors says there are no sensors installed that it supports)  I've had it sitting there for about 10 minutes now and it has hung right around 90 degrees celsius, meanwhile my own personal desktop is hanging out at a cool 18 degrees celsius(also running Ubuntu 12.10 64 bit).  It's worth mentioning I guess that the CPU fan came out of a Dell PC and had a different wiring configuration so I had to splice the connector from the old fan onto the new fan since the new one wouldn't plug onto the connector on the motherboard.  The connections are insulated from each other and the fan is running fine and even changes speed when the CPU is under load, so I don't think that's the issue, and the wires on the two fans were all the same color and the fans were the same size, they just had different connectors so I had to swap them out.

---

### Post by AntumDeluge on 2013-02-06
The Lubuntu desktop is more lightweight than Unity and Gnome. I use it quite often on older hardware. It doesn't have near as many features as the other desktops and at times can be a pain to configure.

To be honest, I've been disappointed with the performance of all Linux desktops on old hardware. Though Lubuntu is lighter on resources I don't know if it would help you with the flash issue.

I don't know about the switching to 32-bit. I myself have only been using 64-bit for about half of a year now so I'm not an expert on it.

---

### Post by papibe on 2013-02-06
Hi gerowen.

Ubuntu 12.04, both Unity and Gnome Shell, is more demanding in graphics than previous versions.

I have a couple of pentium 4 laptops, with 1.5Gb and 750MB of RAM respectively. Neither of them run smoothly Ubuntu 12.04

I would recommend testing the different desktops, as both Xubuntu and Lubuntu run great on one of the laptops (the other one is a test server now).

Another consideration is video acceleration, since Ubuntu 12.04 uses it extensively. If you add, let say an Nvidia 210 (about $40), your desktop experience will improve.

Having said that, IMHO you need both a faster processor to run it. I would say a Dual Core, equivalent or faster.

Just my thoughts.
Regards.

---

### Post by QIII on 2013-02-06
You might try Enlightenment 17 (E17).  It's in the repo, but I don't know how old the packages are.

E17 is a very lightweight window manager rather than a full-blown DE.

Alternatively, you might look into Bodhi Linux 2.0 (bodhilinux.com), which is based on Ubuntu 12.04 and installs with E17.  It comes in both 32 and 64 bit versions.

---

### Post by AntumDeluge on 2013-02-06
I can't find any information about that computer in the [support pages]("http://support.gateway.com/us/en/emac/product/default.aspx?modelId=1454"). But I agree with papibe, if the mainboard on that computer supports a dual-core processor and if you put in some kind of dedicated graphics card (even an older one) you will probably get pretty snappy performance even on the heavier desktops.

**----- Edit -----**

If it uses a socket 775 Pentium 4 then it may support Pentium D, Pentium Dual Core, or Core 2 Duo processors. But that's not a guarantee. It would be well worth it to upgrade. Core 2 Duos can be purchased for around $30 on Ebay (don't know what that is in pounds if you're in the U.K. :p).

---

### Post by gerowen on 2013-02-06
> **AntumDeluge said:**
> I can't find any information about that computer in the [support pages]("http://support.gateway.com/us/en/emac/product/default.aspx?modelId=1454"). But I agree with papibe, if the mainboard on that computer supports a dual-core processor and if you put in some kind of dedicated graphics card (even an older one) you will probably get pretty snappy performance even on the heavier desktops.

**----- Edit -----**

If it uses a socket 775 Pentium 4 then it may support Pentium D, Pentium Dual Core, or Core 2 Duo processors. But that's not a guarantee. It would be well worth it to upgrade. Core 2 Duos can be purchased for around $30 on Ebay (don't know what that is in pounds if you're in the U.K. :p).

I'm in the U.S., according to sysinfo it is dual core, so I may drop a few dollars on a dedicated graphics card and see if that helps, :-)

---

### Post by AntumDeluge on 2013-02-06
I don't know of any dual-core Pentium 4 processors. I know that hyper-threaded single-core processors show up as 2 processors in Windows device manager. Could this be the same in sysinfo?

---

### Post by phthano on 2013-02-07
Ubuntu will detect hyper threaded cores as two individual cores rather than one. It's easy to check how many threads you are running by running in the terminal:

```
cat /proc/cpuinfo | grep processor
```

---

### Post by snowpine on 2013-02-07
Adobe Flash Plugin has its own hardware requirements (above and beyond what's required for the operating system) so you must take those into consideration if you plan to watch Flash videos: [http://www.adobe.com/products/flashplayer/tech-specs.html](http://www.adobe.com/products/flashplayer/tech-specs.html)

> Linux

    2.33GHz or faster x86-compatible processor, or Intel Atom 1.6GHz or faster processor for netbooks
    Red Hat® Enterprise Linux® (RHEL) 5.6 or later (32 bit and 64 bit), openSUSE® 11.3 or later (32 bit and 64 bit), or Ubuntu 10.04 or later (32 bit and 64 bit)
    Mozilla Firefox 4.0 or Google Chrome
    512MB of RAM; 128MB of graphics memory

If you do not have a dedicated graphics card with 128mb+ of graphics memory, that would be a good upgrade for watching full screen video.

That being said, it is always a tough decision whether to throw more money at old hardware, or save that money toward upgrading the entire system. My main problem with Pentium 4's is not that they're slow, but that they are hot, loud, and power-consuming compared to efficient newer hardware. :(

---

### Post by PowerBarry43 on 2013-02-07
Hi

> new fan on top of the heat-sink blowing down

Generally you would want the fan to be blowing up or from the cpu, this is to carry the hot air out and away from the cpu. You will probably find that if you switch the fan over the cpu will be cooler however as has already been said Pentium 4s do run very hot.

Hope this helps!

Barry

---

### Post by ahallubuntu on 2013-02-07
~

---

### Post by tgalati4 on 2013-02-07
It's also possible that your motherboard is interrupting the processor at high temperatures.  This is part of the protection circuit.  90C is too hot.  You want to stay below 60C and ideally 45C.  A 3GHz Pentium4 with a 50% interruption cycle is now a 1.5GHz effective processor, and flash only uses single-thread, single core, so yes you will get crappy performance.

---

### Post by ahallubuntu on 2013-02-07
~

---

### Post by tgalati4 on 2013-02-07
P4's don't support throttling, so the motherboards that support them use different strategies to reduce heat load, and that includes stopping the processor during a duty cycle.  So it is really a safety measure, and not considered throttling--which is reducing the CPU or front side bus clock speed.

---

### Post by Yellow Pasque on 2013-02-07
A dedicated GPU will probably not help with Flash. Flash is supposed to be able to use VDPAU for acceleration on Nvidia cards, but that has its own issues and may not work. (The last time I checked, Flash VDPAU acceleration only worked on 32-bit, but don't quote me on that as still being true.)

As for temps, you should recheck the heatsink installation. How did you reinstall it exactly? Did you clean the CPU and heatsink properly to remove old thermal material?

---

### Post by ahallubuntu on 2013-02-07
~

---

### Post by tgalati4 on 2013-02-07
You make some good points, and only the "Retail Box" processors have this feature, something I doubt that eMachines have--being low-cost hardware.  Regardless, a hot processor will not run correctly.

---

### Post by surfstylee on 2013-03-28
> **gerowen said:**
> It has 1 GB of RAM and an Intel Pentium 4 @ 3.00 Ghz 

Honestly, try Lubuntu. It is much easier on the hardware. Cruchbang and Peppermint are as well. Peppermint is especially good if the PC will be used more for web use--email, video, streaming music  reading the news, etc.

I never use Unity on my Ubuntu machines. Before you install something else like those above--I always install [GNOME Classic (No effects)]("http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-10/ubuntu-12-10-installing-gnome-session-fallback") and boot into Gnome Classic after a restart.

---

### Post by eddier on 2013-03-28
Pretty sure the fan should be sucking up (!) so air is drawn in to the heatsink from the sides and up through the fan. Remove the fan and turn it over.

eddie

---

