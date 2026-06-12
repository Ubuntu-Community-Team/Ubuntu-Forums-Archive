---
title: "mount swap as ram?"
date: 2010-09-30
forum: Hardware
---

### Post by trj021782 on 2010-09-30
I have a PS3 running Ubuntu 9.10 - The ps3 has 256m of system ram and 256 video ram - I have already found out how to mount my video ram as swap but i would rather have the system recognize it as system ram and shunt the swap to my hard drive (even better if I could make the system run it as dual channel but this I do not think will happen) or is there perhaps a priority setting that will cause the system to fill this vram at the same time as the system ram?

---

### Post by kerry_s on 2010-09-30
that don't make since, swap is already used as extra ram. swap is used to off load/cache other programs to make more memory available when needed. you should not be mounting any ram as swap, as swap is used as a last resort since its slower. you want to use actual memory as much as possible.

---

### Post by trj021782 on 2010-09-30
hello again kerry

Yes all of those things are accurate - here is the kicker the swap i have mounted is not read as system ram but can be read as storage so in order to use it at all someone coded it to be able to be mounted as swap so that you could, in effect, double the woefully insufficient memory of the PS3 I would prefer it be read as system ram

---

### Post by Dark_Stang on 2010-09-30
You'd be reading and writing, at best, a hundred MB/s on the hard drive. The most you could hope for by doing this is not getting a kernel panic. There wouldn't be any real performance gains in doing this, if anything you would lose performance.

---

### Post by trj021782 on 2010-10-01
> **Dark_Stang said:**
> You'd be reading and writing, at best, a hundred MB/s on the hard drive. The most you could hope for by doing this is not getting a kernel panic. There wouldn't be any real performance gains in doing this, if anything you would lose performance.


you are foolish and do not pay attention - I HAVE RAM MOUNTED AS SWAP- I WANT IT MOUNTED AS RAM - I do not know how to do this or if it has ever been done before but given the scalability of Linux I must assume it is possible - If you decide to respond foolishly again please remember that i am using a PS3 and that is why i currently have swap mounted as ram

EDIT:

as an after thought, if oyu are wondering why I have ram mounted as swap it is because it is the Video RAM for the PS3 and because there is no access to the PS3 video (no drivers so I hear) somebody found a way to mount that ram as a drive to be used as swap

---

### Post by psusi on 2010-10-01
It isn't possible since you have to go through the video card to reach the video ram.

FYI, you can still add more swap on a hard disk and it will use that once the video ram is full.

---

### Post by trj021782 on 2010-10-03
> **psusi said:**
> It isn't possible since you have to go through the video card to reach the video ram.

FYI, you can still add more swap on a hard disk and it will use that once the video ram is full.


I kinda figured this was the case.

and I know I can add more swap but I was hoping to utilize it as system ram because the page filing used in swap is criminally inefficient compared to normal system ram - but who knows, maybe since the vram is GDDR3 (or 2 maybe) the speed of it will offset the page filing - we shall see

thanks anyway

---

### Post by P4man on 2010-10-03
This would need hardware support to work, its not just a software issue. virtual memory addressing is done by the CPU/memory controller, if that doesnt support addressing the videoram in the same address space as the system ram, then you can forget it. No doubt thats why they wrote the driver to mount it as swap, its actually a clever trick to have some use for it at least.

---

