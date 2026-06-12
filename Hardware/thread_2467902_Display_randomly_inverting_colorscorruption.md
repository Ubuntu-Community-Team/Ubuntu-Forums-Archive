---
title: "Display randomly inverting colors/corruption"
date: 2021-10-11
forum: Hardware
---

### Post by lowang2 on 2021-10-11
Hello, 

I've been experiencing random display corruption issues across 2  different distros where the image suddenly and randomly inverts in color.
**(Picture at bottom of post!)**

I switched over to Ubuntu 20.04 hoping it would solve things but the same thing happens.

Previous to this I was using Pop!OS 20.10 and 20.04. 

I've tried adding the "nomodeset" kernel boot parameter using these instructions:
[https://wiki.ubuntu.com/Kernel/Kerne...er_for_Testing]("https://wiki.ubuntu.com/Kernel/KernelBootParameters#Temporarily_Add_a_Kernel_Boot_Parameter_for_Testing")

*(I removed it after the frame rate drastically dropped)*

I've also tried these instructions found here (though they're specific to Pop!OS?): 
[https://www.reddit.com/r/pop_os/comm...eb2x&context=3]("https://www.reddit.com/r/pop_os/comments/jq96nk/graphics_corruption_on_window_resize_pop_2004_and/gblp3lb/?utm_source=share&utm_medium=web2x&context=3") 

[I](They didn't work)

[/I]My system specs are as follows: 
HP ProBook 640 G1.RAM= 12GB, CPU= Intel I5-4300M, Graphics= Intel HD Graphics 4600 (HSW GT2), HDD= 256GB.

What seems to "help"/temporarily resolve it is to "lock" my screen. As  soon as I click "Lock" the display corruption goes away and everything  is normal, until the problem shows up again randomly.

If someone could help me solve this issue, that would be great as I  really want to enjoy Linux without having to lock/unlock my screen every  time this happens.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=288057&d=1614916841[/IMG]

---

### Post by QIII on 2021-10-11
First eliminate hardware issues with peripherals.

Have you checked the video cable to be sure it is fully seated both at the board and the monitor?  Do you have another known-working cable to try?

Do you have another monitor to test with?

Does this happen when both the computer and the monitor have had a chance to cool completely before turning them back on?  Does this appear after some time, or immediately on startup?

---

