---
title: "GTX 970 wrong displayed clock in X server setings"
date: 2014-12-26
forum: Hardware
---

### Post by barkerson on 2014-12-26
Previous steps that might be relevant...
```
So, I've got a small isue with using coolbits with the EVGA GTX 970 SC I got for christmas, overclocking won't work.
To be more percise, performance settings stop working when coolbits 8 is enabled(or 12 for fan support also).

Yesterday I went through the most pleasure and pain trying to get a gpu up and running for the first time in about 4 years, after I got the drivers(343) and cuda working I thought overclocking souded cool so I decided I was going to try that. Several hours later of complete torture later I figured out why my pc started running even worse than with the old gpu(gtx 560), performance was locked.

Before coolbits was enabled the performance settings(auto, adaptive, and prefer maximum performance) did their job and switched between the four settings I had with no issues at all, then the orture began...
Enabeling the coolbits made auto and adaptive lock the gpu at 405mhz max(level 0) and prefer maximum showed the gpu getting up to 1392mhz(level 1), normally the prefer maximum would lock the gpu in level 3(1506 mhz!).

How do I fix this? Cooling isn't an issue if I enable coolbits 4(manual fan speed), or use the script from _[here.]("https://github.com/MisterPup/Nvidia-Dynamic-Fan-Control")_
```

EDIT: Look at comment #4 in this post(since I can't remove posts).

---

### Post by osmanb on 2014-12-26
I also have a 970 gpu. I'd like to know which version of ubuntu you are using and what did you do to get it working (even without oc).
Thanks in advance.

---

### Post by barkerson on 2014-12-26
I use ubuntu 14.04, I got only background and cursor after login. So according to some instructions I pressed ctrl + alt + f2(tty2, tty1 was busy for me), added x edgers ppa, sudo update, and apt-get the nvidia-343 driver. then I installed cuda via synaptic

---

### Post by barkerson on 2014-12-27
Ok, now after randomly switching between coolbits 4, 8, and 12 and logging in/out the overclocking and fan control seems to work. But now I have another issue...

I ran the ungine valley benchmark to test the waters with the overclocking, and found out that the gpu "only" goes up to 1353MHz, as opposed to the X server settings that said 1506MHz. Overclocking the GPU with 100MHz gives me 1606MHZ in X server settings and 1453MHz in ungine valley, this leads me to believe there is something wrong with the way the X server settings way of reading the GPU's max frequency.
The default levels is: 0 (135-405MHz), 1 (135-1392MHz), 2 (135-1506MHz), and 3 (135-1506MHz). the difference between the last two performance levels is the memory clock, which is 6008MHz and 7010MHz(what it should be).

---

