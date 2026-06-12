---
title: "Ubuntu (10.04 or 10.10) on Thinkpad x40 (or i830,i845,i855 video)"
date: 2010-11-29
forum: Hardware
---

### Post by deckoff on 2010-11-29
Hi
I have thinkpad x40 with i855 video.
i have used Ubuntu on my machine for almost an year now, and I am  quite happy with the result. The main issue I have is though, the video  driver issue -  on 10.04 I had to re-enable KMS and change to a generic  kernel.(the system used to go down with default kernel when trying to play  video)
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes#GTT%20Incoherency%20Patch](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes#GTT%20Incoherency%20Patch)
I  have no luck with Maverick up to now, though - The intel driver is  disabled, and vesa driver is enabled by default. Which means crappy  video and no Docky and other flashy effects. Re-enabling the intel  driver renders the system unusable.
[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus#Testing%20upstream%20patch%20for%20i855](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus#Testing%20upstream%20patch%20for%20i855)
So I have two questions:
1) Which kernel do you use in Ubuntu 10.04
2)  Has anyone been able to run Ubuntu 10.10 on Maverick with x40 or i855  video, with enabled intel driver. If so, how was it done?

---

### Post by fdm on 2010-12-03
I'd definitely go for 10.10. Try both the updated intel driver by itself, and with the patch. I am testing the updated 2.13git driver on my i845, and so far it is better then it has been since they dropped xaa a little more than two years ago. I really doubt the opengl portion is stable(for example, I experience a bug with glxgears where it renders only at the top left of the screen). I haven't got that horrid striped flashing gpu crash so far(it was the only major bug I experienced with Intel 2.12 on 10.04). It looks like it is at a point where I can feasibly abandon my 2-1/2 year old intel driver. Finally!

[http://ubuntuforums.org/showpost.php?p=10067580&postcount=7](http://ubuntuforums.org/showpost.php?p=10067580&postcount=7)

---

### Post by deckoff on 2010-12-04
Thanx for the answer.
I have only one question - You mention you use updated 2.13git driver. How do you install that, following the procedure described in the link below  your post??

---

### Post by fdm on 2010-12-16
> sudo add-apt-repository ppa:glasen/intel-driver 
sudo apt-get update && sudo apt-get upgrade

You may have to re-enable the Intel driver with the first part of that post and you may benefit from the i855 specific fix that is mentioned after the Intel upgrade. My i845 is still working great with perfect uptime, great video playback, and wifi that always works. In other words, flawless.

---

### Post by TheCan on 2010-12-22
I am happy to confirm the suggested fix on my Thinkpad X40. Although it did not work reliably in 10.04 (even with Glasen's Patch), re-enabling the Intel Driver on 10.10 makes fluent video playback work again, without crashes so far!

---

### Post by deckoff on 2010-12-26
Unfortunately the suggested fix does not wok for me. :(
Mouse pointer disappears, general other problems :(
Hope this is fixed with next Ubuntu, and problem solved once and for all for this chipset family. 
Happy Holidays

---

