---
title: "A question about hardware for video transcoding"
date: 2012-07-18
forum: Hardware
---

### Post by 0011235813 on 2012-07-18
I've read an article on Anand Tech that talks about how handbrake is going to release their program with OpenCL and GPGPU video transcoding support: 
[http://www.anandtech.com/show/5835/testing-opencl-accelerated-handbrakex264-with-amds-trinity-apu](http://www.anandtech.com/show/5835/testing-opencl-accelerated-handbrakex264-with-amds-trinity-apu)
Apparently the x264 encoder for h.264 is going to use the graphics card to boost transcoding speeds (not sure about VP8 ) . So here's the question: Assuming the handbrake developers implement this properly, which hardware configuration would be more ideal: an I5 3450 with a GTX 560 Ti, or an I7 3770K with a GT 640 card for VDPAU decoding? 
I'm wondering because for some reason, the writers of the article though this development would apply to mobile chipsets (why on Earth would anyone choose a laptop over a dekstop for video transcoding unless they really needed portability?) with integrated graphics (the whole point is GPGPU transcoding here guys, don't you think this is going to interest users with high-powered graphics cards instead of users with Integrated ones? Because you know, **they're going to see the biggest benefit?!**) and they didn't do any other comparisons.
So what do you guys think?

---

### Post by JohnAStebbins on 2012-07-18
> **0011235813 said:**
> Assuming the handbrake developers implement this properly,

A bit off topic, but... the HandBrake developers first learned of this wonderful new work they are doing when Anand announced it.  I.e. it's pure fiction.  There may be somebody somewhere deep in the bowels of the AMD or Intel machine that has written a patch to add such capability.  But they have *not* so much as mentioned it to us.

We've heard rumors (through Anand and other channels) that work is happening in secret. There haven't even been rumors regarding an nvidia specific port. There is someone working on OpenCL support for x264 with source available (HandBrake uses x264, but x264 is a different project with different developers).  But so far there is *no* proof that any of this makes things faster.  And lots of evidence that it will result in substandard quality.  So if I was investing money in an encoding machine, I would still be looking for the fastest CPU I can afford.

If you are interested in serious comparisons of software and hardware encoders, you should read this.
[http://www.compression.ru/video/codec_comparison/h264_2012/](http://www.compression.ru/video/codec_comparison/h264_2012/)

It's very enlightening an shows just how poorly the hardware encoders are performing.  If you are too impatient to plow through all the statistics in the report.  The summary is that software encoders on a fast CPU are just as fast as hardware encoders once you dial down the settings of the software encoder till it produces equivalently quality as the hardware encoder you are comparing against.  There are no settings in the hardware encoder to "dial up" to reach the same quality that the software encoders can achieve (albeit at a slower rate).

---

### Post by 0011235813 on 2012-07-18
> **JohnAStebbins said:**
> A bit off topic, but... the HandBrake developers first learned of this wonderful new work they are doing when Anand announced it.  I.e. it's pure fiction.  There may be somebody somewhere deep in the bowels of the AMD or Intel machine that has written a patch to add such capability.  But they have *not* so much as mentioned it to us.

We've heard rumors (through Anand and other channels) that work is happening in secret. There haven't even been rumors regarding an nvidia specific port. There is someone working on OpenCL support for x264 with source available (HandBrake uses x264, but x264 is a different project with different developers).  But so far there is *no* proof that any of this makes things faster.  And lots of evidence that it will result in substandard quality.  So if I was investing money in an encoding machine, I would still be looking for the fastest CPU I can afford.

If you are interested in serious comparisons of software and hardware encoders, you should read this.
[http://www.compression.ru/video/codec_comparison/h264_2012/](http://www.compression.ru/video/codec_comparison/h264_2012/)

It's very enlightening an shows just how poorly the hardware encoders are performing.  If you are too impatient to plow through all the statistics in the report.  The summary is that software encoders on a fast CPU are just as fast as hardware encoders once you dial down the settings of the software encoder till it produces equivalently quality as the hardware encoder you are comparing against.  There are no settings in the hardware encoder to "dial up" to reach the same quality that the software encoders can achieve (albeit at a slower rate).
Wow. Just wow. Anand Tech is publishing rumor as fact?!! Jeez, that significantly lowers their credibility, and it makes me scared. I can't imagine the amount of fake news sites there must be going around here. So all of the Anand results are mythical?! Is some secret project going on here? LOL, I'm not going to bother reading that site again for sure.

So the x264 developers are trying to implement hardware acceleration? Well that's very interesting, but I'm a little doubtful about all this "hardware acceleration is ineffective and produces sub-standard results" FUD. I mean sure, I've seen some pretty crappy accelerated software programs, but I think the real problem is on the difficulty of producing software as opposed to the hardware itself. I don't know, but I've seen hardware programs that produce results almost as good as the CPU ones, and much faster. I'm not an expert on encoding, but even so, I know GPUs have a lot more computing power in TFLOPS and much faster memory, so using it would be faster than CPU alone. Adobe Premiere Pro does it, although that's for editing and not transcoding from what I gather. Even if the GPU isn't faster, considering how many hours it takes to encode long 1080p videos, it would seem stupid to just completely ignore the powerful GPU that may be available on the computer.

Also, some questions about handbrake:

- Why doesn't the new ppa work, and why are the no packages for any other distributions beside Ubuntu/Mint and Fedora? I don't think most people are happy to compile it like I did, because it's complicated and slow if they have a lower end PC.

-VP8/WebM support? Why do I have to use FFmpeg and it's front-ends to make videos for the web? Are there any plans to include this in future releases?

Thanks, hopefully you can answer some of my questions :)

---

### Post by JohnAStebbins on 2012-07-20
> **0011235813 said:**
> So the x264 developers are trying to implement hardware acceleration?

Not quite what I said.  "There is someone working on OpenCL support for x264."  Singular not plural and he's not a core x264 developer, but is someone who is interested in OpenCl and wanted to make an attempt at accelerating some x264 functions.  He's not the first to try this and will likely fail as the rest have.

Anand likely made the same kind of mistake and read more into an innocent comment than it should have.

> 
Also, some questions about handbrake:

- Why doesn't the new ppa work, and why are the no packages for any other distributions beside Ubuntu/Mint and Fedora? I don't think most people are happy to compile it like I did, because it's complicated and slow if they have a lower end PC.

-VP8/WebM support? Why do I have to use FFmpeg and it's front-ends to make videos for the web? Are there any plans to include this in future releases?

Thanks, hopefully you can answer some of my questions :)
There is a snapshot PPA that is update nightly and a releases PPA that is updated when we make an official release.  They are both fully functional.  If you are running ubuntu 12.04, there was no release for you until the last couple of days when we kicked version 0.9.8 out the door.

VP8? meh!  There are only 4 active developers on the HandBrake team.  Only 2 of us regularly work on the core library where codec and container support is done.  None of us have any personal interest in VP8 or WebM. And we don't have time to waist on uninteresting things.

---

### Post by 0011235813 on 2012-07-21
> **JohnAStebbins said:**
> Not quite what I said.  "There is someone working on OpenCL support for x264."  Singular not plural and he's not a core x264 developer, but is someone who is interested in OpenCl and wanted to make an attempt at accelerating some x264 functions.  He's not the first to try this and will likely fail as the rest have.

Anand likely made the same kind of mistake and read more into an innocent comment than it should have.


There is a snapshot PPA that is update nightly and a releases PPA that is updated when we make an official release.  They are both fully functional.  If you are running ubuntu 12.04, there was no release for you until the last couple of days when we kicked version 0.9.8 out the door.

VP8? meh!  There are only 4 active developers on the HandBrake team.  Only 2 of us regularly work on the core library where codec and container support is done.  None of us have any personal interest in VP8 or WebM. And we don't have time to waist on uninteresting things.
Pessimistic much are we? Ah well, I don't blame you. GPU transcoding has been a bit disappointing  so far.

No VP8? It's a pity, because I can't put just mp4s on a website without having 60% of browsers not be able to play it. I guess an MKV file will do fine for desktop purposes, but hey maybe the guys at Google will develop it and I'll just use kdenlive for WebM.

---

