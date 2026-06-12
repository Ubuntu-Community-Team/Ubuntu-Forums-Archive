---
title: "trying to setup ati radeon r7 a8-7650"
date: 2018-04-05
forum: Hardware
---

### Post by jgw on 2018-04-05
I am trying to setup ati radeon r7 a8-7650 graphics.  When I booted the system up it automatically used the 'radeon' driver.  Here is the info on that:
 *-display     (sudo lshw -c video)
       description: VGA compatible controller
       product: Kaveri [Radeon R7 Graphics]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:39 memory:c0000000-cfffffff memory:d0000000-d07fffff ioport:f000(size=256) memory:feb00000-feb3ffff memory:c0000-dffff
amd apu  a8-7650K w/radeon r7 graphics

The problem is, I think, that this may not deal with hdmi audio and I read someplace that I should actually install a proprietary driver from ati   So, I started reading and its very confusing.  [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver), for instance, tells me that my graphics are fully supported.  There are other links, however, that says that there are no known drivers for this.  Since I have it installed, and its working, I was wondering if I should try and download and install a proprietary driver and, if so, which proprietary driver should I use?  

I am connecting all of this to a 4K tv (samsung).  This is a challenge.  I did get it to kinda run on the tv but there was no sound.  It did, however, give me a 3840x2160 (16:9) picture with no problem.  Samsung support, however, is chancy at best.  Soon as you tell them that you are running linux they just stop answering any questions.  I have also noticed that if the resolution drops below the 3840x2160 the picture gets very strange but, I suspect, I can deal with that one.  One of the problems with the samsung is that its got all this wonderful software that gets VERY confused.  Its too bad they don't have a setting that abandons all the 'special' software and just takes a signal and displays it.  I have, incidentally, a different motherboard and apu which I do have working on my 4k tv.  It just doesn't give me a picture over 1920x1080 so I thought I would try (I had to trick the tv to get this one done.  Swapped out drivers until I found one that would work.  That was with an nvidia card)

Thank you.....................

---

### Post by QIII on 2018-04-05
Hello!

Which release of Ubuntu are you running?

---

### Post by jgw on 2018-04-06
thank you for the reply..........

I am running with ubuntu 16.04.4

I should add that this is not the machine with the problem as that is a moving target.  I have to swap out the motherboard on this machine to get there but the ubuntu is the same

---

### Post by Yellow Pasque on 2018-04-07
> **jgw said:**
>  I was wondering if I should try and download and install a proprietary driver 

No. AMDGPU-Pro doesn't support your APU/GPU.

Start with the simple stuff. Make sure you selected the correct device in pavucontrol.
```
pavucontrol
```
Make sure your TV has appropriate audio/volume settings.

Get more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by jgw on 2018-04-13
Thank you for the replies.

This was my problem because I, obviously, didn't think the whole thing through.  My passthrough receiver was the problem because it was too old to deal with this.  I am swapping that out and it should take care of the problem.

I apologize to everybody on this one.

---

### Post by QIII on 2018-04-13
No apologies needed!  :)

The point here is that we all help each other sort things out.  Your discovery might be very helpful for another user.

Cheers!

---

