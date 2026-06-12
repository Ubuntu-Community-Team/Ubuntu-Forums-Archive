---
title: "Does not detect all RAM"
date: 2019-12-27
forum: Hardware
---

### Post by daniel-pbt on 2019-12-27
Hello, I just bought a laptop,  asus D509DA, and for reasons of the software I am going to use, I have put another module of Ram, having a total of 8G. The BIOS detects 8G, but the system detects only 5.8G, leaving the rest for other functions that I don't know. Is the correct configuration of the equipment? Is it possible to modify the RAM allocation so that the computer uses its full potential?
I have updated the BIOS to its latest version, and I don't see the possibility of touching that option.
I have also obtained some results that may be helpful for the response. The system is Ubuntu 18:04.
Attached photos

Thanks in any case[ATTACH=CONFIG]284701[/ATTACH][ATTACH=CONFIG]284702[/ATTACH][ATTACH=CONFIG]284703[/ATTACH]

---

### Post by CelticWarrior on 2019-12-27
The remaning is assigned as video RAM. You may or may not change it in BIOS/UEFI.

---

### Post by CatKiller on 2019-12-27
> **daniel-pbt said:**
> The BIOS detects 8G, but the system detects only 5.8G, leaving the rest for other functions that I don't know. Is the correct configuration of the equipment?  

The various memory reporting tools show the amount of memory that is *available to be allocated* to the applications that want it. The memory space that the kernel itself uses (around 300 MB or so) cannot ever be allocated to other applications, so that would not be included. Memory space that is allocated to a graphics device (entirely dependent on your integrated graphics configuration) cannot also be allocated to an application, so that is not included. 

> Is it possible to modify the RAM allocation so that the computer uses its full potential?

The optimal balance between how much of your RAM is allocated to your graphics device and how much is avaliable for general purposes depends entirely on how you're using your machine, and would generally be a setting in your BIOS if you're able to change it at all. Given that you've got a reasonably hefty graphics device in there it's going to need a fair chunk of video RAM allocated to work to its "full potential."

---

### Post by crip720 on 2019-12-27
Just checking on what Catkiller and CelticWarrior said, I have a Dell with 16GBs of memory and nivida graphics card and my system reports between 15, 15.5 and 16GBs memory.  The OPs numbers seem low.  My numbers are reverse to the pictures the OP posted.

---

### Post by CatKiller on 2019-12-27
> **crip720 said:**
> Just checking on what Catkiller and CelticWarrior said, I have a Dell with 16GBs of memory and nivida graphics card and my system reports between 15, 15.5 and 16GBs memory.  The OPs numbers seem low.  My numbers are reverse to the pictures the OP posted.

Nvidia don't do integrated graphics. Dedicated cards (obviously) and Optimus setups have dedicated video RAM without having to share system memory. OP has a pretty standard ~200 MB used by the kernel and 2 GB used by their integrated Vega graphics by the looks of it.

---

### Post by crip720 on 2019-12-28
I also have an older laptop with only integrated graphics(baytrail) has 8GB of memory and reads 7.7GB.  Think all my laptops read all or very close to the installed memory, even the ones with slightly mis-match memory sticks.  Only one has dedicated graphic card.  Maybe vega graphics work differently, the only AMD laptop used the drivers supplied by ubuntu, The AMD driver was no longer supported.

---

### Post by Yellow Pasque on 2019-12-28
> **CatKiller said:**
> Dedicated cards (obviously) and Optimus setups have dedicated video RAM without having to share system memory.

I don't think Optimus setups have dedicated VRAM. Don't quote me on that.

> OP has a pretty standard ~200 MB used by the kernel and 2 GB used by their integrated Vega graphics by the looks of it.

If it really is the GPU allocating that memory, allocating 2GB is a bad idea. It is better to allocate a smaller amount of RAM and let the OS dynamically allocate more as needed. Hopefully, there is a BIOS setting to change it. I know there is on my desktop (for example:

---

### Post by CatKiller on 2019-12-28
> **Yellow Pasque said:**
> I don't think Optimus setups have dedicated VRAM. Don't quote me on that. 

[https://blogs.nvidia.com/blog/2010/02/09/world-meet-optimus/](https://blogs.nvidia.com/blog/2010/02/09/world-meet-optimus/)

> Optimus transfers the display surface from the **GPU frame buffer** over the PCI Express bus to the **system memory-based frame buffer used by the IGP**.  


>  If it really is the GPU allocating that memory, allocating 2GB is a bad idea. It is better to allocate a smaller amount of RAM and let the OS dynamically allocate more as needed. Hopefully, there is a BIOS setting to change it. I know there is on my desktop (for example:

OP asked what his RAM was being used for. That's what it's being used for. "Oh, but my completely different system behaves completely differently" is not helpful. From either of you.

It will be useful to the OP if their hardware allows them to configure the allocation more to their liking, of course, but we won't know if their machine will let them do that until they look for the setting and get back to us.

---

### Post by Yellow Pasque on 2019-12-28
> **CatKiller said:**
> OP asked what his RAM was being used for. That's what it's being used for. "Oh, but my completely different system behaves completely differently" is not helpful. From either of you.

I beg to differ. I posted the screenshot as an example of what terminology a BIOS might use. I looked through the manual for the OP's model and it does not give a detailed description of the BIOS layout, so that was the best example I could provide. I thought it might be helpful to the OP because terminology of BIOS settings can be confusing (especially when different languages are involved). I probably should have given this link, but I didn't want to get too far ahead:
[https://www.techspot.com/article/1578-amd-raven-ridge-reserved-memory-explainer/](https://www.techspot.com/article/1578-amd-raven-ridge-reserved-memory-explainer/)

---

### Post by daniel-pbt on 2019-12-28
Hello again. First of all, tell you that I thank you very much for your  help on this topic. I am learning a lot from my new laptop.
First of all I wanted to comment that my bios does not let me change the  allocation of memory destined for the GPU. I have put two photos of the  various possibilities in the menu that shows the BIOS.
On the other hand, as I am understanding, it would be better to dedicate  less RAM to VGA. I imagine that from the terminal it is only possible  to check how the memory is assigned, but not to change the assignment.  Therefore, it seems that I have to comply with my situation, until ASUS  increases the options of the BIOS. It also occurs to me (I don't know if  this is possible, or if it can be very complicated), that maybe it can  be put another BIOS that is compatible, and that has that option.
Thank you.     [ATTACH=CONFIG]284708[/ATTACH]

---

### Post by daniel-pbt on 2019-12-28
Here is another photo of the BIOS

---

### Post by CatKiller on 2019-12-28
> **daniel-pbt said:**
> On the other hand, as I am understanding, it would be better to dedicate  less RAM to VGA. 
It's moot anyway without an option in the BIOS, but not necessarily. It all depends on what you're using the computer for. For gaming with low details 2 GB of video RAM is pretty much the minimum of what you'd want, and your remaining 6 GB of system RAM is fine for general personal computing tasks of the sort you're likely to do on a laptop, and the kind of gaming that you can do on an integrated GPU. If you never wanted to do gaming and you were doing hardcore video editing or working with massive databases then you'd probably want to adjust the balance a bit, but you'd probably prefer to do those tasks on a desktop machine anyway.

---

### Post by CatKiller on 2019-12-28
> **daniel-pbt said:**
> It also occurs to me (I don't know if  this is possible, or if it can be very complicated), that maybe it can  be put another BIOS that is compatible, and that has that option.

The BIOS is entirely specific to the model (and revision) of motherboard, especially for a platform as tightly integrated as a laptop. Putting the wrong BIOS on there would just brick it. Which is why BIOS images are signed so that you can't put the wrong one on. They might put the option there with a future update - if the commercial case is there from the manufacturer's point of view - but I wouldn't hold out hope for that.

---

### Post by Yellow Pasque on 2019-12-28
> **CatKiller said:**
> For gaming with low details 2 GB of video RAM is pretty much the minimum of what you'd want, and your remaining 6 GB of system RAM is fine for general personal computing tasks of the sort you're likely to do on a laptop, and the kind of gaming that you can do on an integrated GPU.

I think you should look at the link I provided. If you have a choice, it's better to reserve a small amount of RAM and let the OS dynamically allocate more as needed.

---

### Post by daniel-pbt on 2019-12-30
I understood that I didn't have a problem on my laptop, and yes, a lot of support from people defending against the current, the importance of freedom in software.
Thank you all so much

---

### Post by Yellow Pasque on 2019-12-31
> **daniel-pbt said:**
> I understood that I didn't have a problem on my laptop

It's not a problem so much as a possibly sub-optimal configuration. Unfortunately, I don't think there's anything you can do about it without BIOS control. The amdgpu kernel module does have some parameters involving VRAM size, but I have no personal experience with them. [https://dri.freedesktop.org/docs/drm/gpu/amdgpu.html](https://dri.freedesktop.org/docs/drm/gpu/amdgpu.html)

Maybe I'll play around with the graphics on my 2400G this afternoon and see if I can figure anything out.

---

### Post by Yellow Pasque on 2019-12-31
> **Yellow Pasque said:**
> Maybe I'll play around with the graphics on my 2400G this afternoon and see if I can figure anything out.

It didn't go so well. Lots of segfaults when trying to set vramlimit, but this was on KDE Neon. *Shrug*

---

### Post by daniel-pbt on 2020-01-02
>  It didn't go so well. Lots of segfaults when trying to set vramlimit, but this was on KDE Neon. *Shrug*
Thank you  so much  for your effort

---

### Post by QIII on 2020-01-02
This is an English speaking area of the Forums.  Please post in English only.

Thanks.

---

