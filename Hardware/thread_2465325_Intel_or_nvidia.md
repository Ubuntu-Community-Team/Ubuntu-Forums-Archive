---
title: "Intel or nvidia?"
date: 2021-07-29
forum: Hardware
---

### Post by ants-karner on 2021-07-29
Hello everyone at ubuntu forums!
I have two video cards. One is dedicated discrete Asus Nvidia GT 710. Second card is integrated Intel HD4400 . I have desktop PC. And what I want to know: which of them is better for Ubuntu? I have been googled a little bit, but no proper and clear info found. Right nod I am using GT 710 with proprietary drivers, and so far everything is working normally. But there are lots of talks about problems with Nvidia on Linux. How good are intel drivers nowadays? Sorry if what I wrote is badly understandable. I'm not English speaking person. Thans for advance!

---

### Post by oldfred on 2021-07-29
You can compare:
[https://www.videocardbenchmark.net/compare/GeForce-GT-710-vs-Intel-HD-4400/2910vs2643](https://www.videocardbenchmark.net/compare/GeForce-GT-710-vs-Intel-HD-4400/2910vs2643)
But may depend on exactly what you are doing to see any difference.

---

### Post by Autodave on 2021-07-29
I have no issues with any of my 9 machines and they all run nVidia cards.  If you have a VERY new nVidia card, you may have some issues, but you are good with that one that you have.

---

### Post by mikewhatever on 2021-07-29
Both should work well. Nvidia is obviously more powerful, both are quite old, but not depricated. I am not sure which one is better. It depends on you particular needs.

---

### Post by TheFu on 2021-07-29
It depends.

I've had 5 issues with nvidia over the last 5 yrs and 1 issue with intel iGPUs in the same time.  

The low end nvidia is definitely more capable than any of my Intel iGPUs, but for playback of 1200p and less videos, the iGPUs are quite good going back to 2012-ish.  Only once did I even have to do anything with the driver on Intel.  With nvidia, I ended up setting up a automatic re-install process after each new kernel was installed. Until I did that, the resolution would be stuck at something like 800x600 on my 1030 GT.  I don't have any 7xx series nvidia.  I know that legacy driver support for my 7200gs was dropped after 16.04.  Support for my 430GT isn't the best, but that could be due to other hardware issues with that old GPU. It is on a system that seldom gets used except over the network via ssh.

So ... which is better depends on what you use it for, and what you'd like to use it for.  If you want GPU-based h.265 encoding, I don't think any iGPUs from Intel support that on Linux. I could be wrong.  My video playback devices don't support h.265, so I'm still encoding to h.264 and using the CPU for that effort.  We likely have different needs.

I don't game.

For a work desktop that does light video playback, the GPU really shouldn't matter in the last 5 yrs. They all have hardware decoding for mpeg2 and h.264.  If you are watching 4k or 8k video, then you'll probably want a newer GPU that supports h.265 decoding in hardware.

---

