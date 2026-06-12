---
title: "Upgrading my motherboard..."
date: 2016-09-02
forum: Hardware
---

### Post by SagaciousKJB on 2016-09-02
I was thinking about upgrading my motherboard. I am still using DDR2 memory and a Phenom X4 9950, and it's getting just a little too old to handle all these resource-greedy applications being made. It's amazing what a news site full of ads does to slow it down...

Anyway I was wondering if I put in a new motherboard, how would my currently installation react to this? I would assume it would need to load different drivers, but would it detect which ones and load them automatically or would I have to do some work in the recovery mode to tell it what has changed?

---

### Post by QIII on 2016-09-02
Hello!

If you remove any proprietary drivers you may have installed, there is a high likelihood that things will go smoothly.  I've done this very thing many, many times without problems.

Unfortunately, there are no guaranties in life and your mileage may vary.

Cheers.

---

### Post by DuckHook on 2016-09-02
> **QIII said:**
> If you remove any proprietary drivers you may have installed, there is a high likelihood that things will go smoothly.+1

@OP

I regularly swap HDDs from one machine into another and the Linux OS that is on the HDD manages to boot up without any problems whatsoever. Like QIII says, you must be sure to stay away from proprietary drivers, but otherwise, Linux OSes are very platform agnostic. The drivers that are needed for most HW are baked right in to the kernel.

---

### Post by Bucky Ball on 2016-09-03
> **DuckHook said:**
> ... Linux OSes are very platform agnostic. The drivers that are needed for most HW are baked right in to the kernel.

+1. Never had an issue for this very reason. Built a new desktop at the beginning of the year and ripped the SSD with 14.04 installed out of the old one, smacked into the new and booted up with no issue (except I had to install drivers for my new whizz-bang GPU).

The SSD came out of a ten year old box with a P4 processor, 4Gb of RAM and an ASRock MBoard into a machine with an i7 6700 and 16Gb of RAM on a motherboard from a totally different manufacturer and with ten more years advance in technology up its sleeve. Not a hiccup, so doubt you'll have too many issues, either. Good luck.

---

### Post by SagaciousKJB on 2016-09-03
Sweet good news. I am currently running Nvidia proprietary drivers, but I'm not too unfamiliar with having to fall back to the OS ones. I use the proprietary drivers though because I like to run two X screens for TV out and a normal working desktop, and from what I have seen the OS drivers don't support that too well.  Something kind of similar, but not two X screens. 

This might be a different topic all together...  But my video card is also pretty antiquated, it's a Nvidia GeForce 7950 and it's been serving me well for quite some time, but it only has an S Video out and I just recently got an HDTV.  Yeah I know, I hold on to old technology like it was a family member or something. So I am thinking that if I instead get one of these new nifty "APU" processors that do graphics and normal processing in one ( this is all new to me ) that I might save some money and get a HDTV experience finally. Just not sure which is more Linux friendly between AMD and Intel these days, and how my weird preference of using dual X screens might effect it.

I mostly use my computer for a basic desktop plus media machine. I have Myth TV installed with a ATSC tuner card, as well as a Windows MCE edition remote control and I basically have things scripted so that I can press different colored corresponding buttons on the remote to bring up Myth TV, VLC or Chrome, the last being used to stream Hulu, Netflix, and Amazon Prime. All of the media uses still run great, but oddly enough it's just simple web browsing that seems to be whooping the CPU's butt. Maybe using a more lightweight web browser than FireFox would help, because basically a lot of the time ( as I'm typing this as a matter of fact ) I am browsing the web in FireFox on one X Screen, and on the other X screen I have Chrome streaming something (Star Trek Enterprise, the geek runs deep in me).  So yeah given my unusual use model I'm not really sure what kind of hardware I should be looking at...  Honestly I should be giving the CPU props, because I am running two VirtualMachines on top of all of this as well.

---

### Post by mörgæs on 2016-09-03
In stead of buying more gear I suggest that you first try to disable Flash and other kinds of ads in the browser. It's not a given fact that more hardware is necessary.

---

### Post by SagaciousKJB on 2016-09-04
> **mörgæs said:**
> In stead of buying more gear I suggest that you first try to disable Flash and other kinds of ads in the browser. It's not a given fact that more hardware is necessary.

Yeah I do try to do some things like that but flash block and ad block become meddlesome at times, especially since I use a mix of different browsers for different tasks. Besides that it just seems like the GUI in general is pretty laggy so I just suspect that my hardware is a little aged for this.  I mean, it wasn't even brand new in 2008 when I bought it. My motherboard doesn't even support booting off of USB!

I thought about just getting a Phenom II but I have a DFI board and as far as I am aware they do not offer any kind of support any more and i would have to flash the BIOS to be able to use AM3 CPUs. Besides that, it seems that I could get a pretty decent new mother board, CPU and RAM that would out perform even a Phenom II for about 200 bucks. Seems kind of worth it just to get a new motherboard with USB 3.0 not to metion booting capabilities.

Plus this system would probably make a good little Windows gaming machine if I put it into a new case, got a newer graphics card for it. I don't really play anything too fancy or demanding, I just need a Windows system since most of the games I like to play don't seem to work on wine.

---

### Post by gordintoronto on 2016-09-05
Another alternative to consider is replacing your hard drive with an SSD. The Samsung 750 EVO series is not very expensive, and it made my Phenom II system fly.

---

### Post by SagaciousKJB on 2016-09-05
> **gordintoronto said:**
> Another alternative to consider is replacing your hard drive with an SSD. The Samsung 750 EVO series is not very expensive, and it made my Phenom II system fly.

I did just finally upgrade from an IDE to a SATA drive and things seem zippier so that might be something to explore. On the other hand that was right at the same time I went up from 2 gigs to 4 gigs of RAM so maybe I just reduced my swap time...

---

### Post by Bucky Ball on 2016-09-05
Replacing or adding an SSD to install the OS to is what gordintoronto was suggesting, not a HDD. The speed will turn old machines into new ones!

---

### Post by Yellow Pasque on 2016-09-06
> on the other X screen I have Chrome streaming something .... I am running two VirtualMachines on top of all of this as well. 

Are you always running the VM(s)? If you don't watch video and browse, do things get better? In other words, have you tried to methodically eliminate tasks to see if one of them has a more significant impact than the others? I'd suspect the video could be the major factor, since the 7950 doesn't provide the CPU with a lot of help when decoding modern formats. So, the first thing I would do is get a video card and see how the system runs, especially if you planned to get one to turn this into a Windows box anyway.

> Replacing or adding an SSD to install the OS to is what gordintoronto was suggesting, not a HDD. The speed will turn old machines into new ones! 

I don't think an SSD is going to make a big difference with what the OP is struggling with. It makes things like booting, loading an application, and package management a lot faster, but it's probably not going to do much for streaming video or running VM's (unless there's a lot of disk I/O going on in the VM).

---

### Post by Bucky Ball on 2016-09-06
> **Temüjin said:**
> I don't think an SSD is going to make a big difference with what the OP is struggling with. It makes things like booting, loading an application, and package management a lot faster, but it's probably not going to do much for streaming video or running VM's (unless there's a lot of disk I/O going on in the VM).

True.

---

