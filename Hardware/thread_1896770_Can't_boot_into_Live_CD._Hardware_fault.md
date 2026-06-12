---
title: "Can't boot into Live CD. Hardware fault?"
date: 2011-12-17
forum: Hardware
---

### Post by tetsura on 2011-12-17
Hi,

I seem to have some kind of hardware problem. Windows crashed one day and I can't boot into it any more. Dell diagnostics give an error relating to hard drive failing/failure.

The Windows CD wouldn't work so I tried to boot up a Ubuntu live CD, but that won't work either. Just get a blank screen after choosing to boot into linux :/

Anyone have any ideas? Surely if it were just a hard drive problem then I could still boot into the live CD? And then run a repair on the hard drive or something?

Thanks in advance

---

### Post by JC Cheloven on 2011-12-17
> **tetsura said:**
> 
The Windows CD wouldn't work so I tried to boot up a Ubuntu live CD, but that won't work either. Just get a blank screen after choosing to boot into linux :/ 
It could be of help to know which version of ubuntu are you trying, and what your hardware is. Also, have you tried to boot from live cd with some kernel options (noapic nolapic, for instance)? You can choose that after being asked for your language, by pressing F6.

>  Anyone have any ideas? Surely if it were just a hard drive problem then I could still boot into the live CD? And then run a repair on the hard drive or something?

Yes, it should boot despite your hard drive. And yes, the idea should be to recover data and trying to repair the filesystem or at least recover that disk space for future use. For repairing a NTFS filesystem you could consider some windows based program as a better option though (as ntfs is a windows filesystem).

---

### Post by dandnsmith on 2011-12-18
> The Windows CD wouldn't work 
If by this you mean you couldn't boot from the Windows CD, then you should consider that the CD device may have developed a fault.

---

### Post by tetsura on 2011-12-19
> **dandnsmith said:**
> If by this you mean you couldn't boot from the Windows CD, then you should consider that the CD device may have developed a fault.

Well the windows CD is actually on a USB stick so it's not a CD drive problem, also it loads ok but gets stuck on a black screen, like it does when I try to boot into Windows. It's a known issue but apparently with no solution..


> **JC Cheloven said:**
> It could be of help to know which version of ubuntu are you trying, and what your hardware is. Also, have you tried to boot from live cd with some kernel options (noapic nolapic, for instance)? You can choose that after being asked for your language, by pressing F6.

Yes, it should boot despite your hard drive. And yes, the idea should be to recover data and trying to repair the filesystem or at least recover that disk space for future use. For repairing a NTFS filesystem you could consider some windows based program as a better option though (as ntfs is a windows filesystem).

11.10. My laptop is an Alienware M11X R1. I will try the kernel options you mentioned.

Yeh I thought it should boot despite the hard drive.. That's what is confusing me, does that mean another part of the hardware has died as well? At the same time as my hard drive? I don't want to pay for a new hard drive and then discover that I have to pay for another part!

I've tried windows based programs as you've suggested, some on Hiren's Boot CD, they couldn't read the hard drive though so it seems to be completely dead :(

---

### Post by tetsura on 2011-12-19
Edit - Ok it boots into the live cd without the hard drive plugged in, so it would seem it's a dead hard drive which has been causing the problems :(

Cheers, this can be locked/deleted/whatever now

---

### Post by JC Cheloven on 2011-12-19
> **tetsura said:**
> 
Cheers, this can be locked/deleted/whatever now
Even better: if you have a moment please mark the thread as solved, so that other people can do searchs more efficiently. It is done at the "thread tools" link at the top of the page.
Thanks.

---

