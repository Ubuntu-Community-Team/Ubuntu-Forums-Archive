---
title: "3D accelaration on Nvidia gt 320"
date: 2010-04-18
forum: Hardware
---

### Post by bprins on 2010-04-18
Hi,

After weeks of exploring the internet and reading stuff about ubuntu linux I thought it was time to open a topic myself. 

Problem1: 
I've bought a laptop, and my hate toward windows overgrew myself hence I installed ubuntu 9.10 karmic. After some heroic effort I got everything to work, except I'm pretty sure my 3D rendering is still done on the CPU instead of on my GPU. Running World Of Warcraft and checking top says it all: 80% CPU usage for Wow.exe.

Problem2: 
I know too little about ubuntu linux to really understand all the terminal output I get from stuff like lspci.

Q1:
Does the following mean that my ubuntu installation does not fully understand which video card is installed in my laptop?:

```

01:00.0 VGA compatible controller: nVidia Corporation Device 0a2d (rev a2)

```I would have expected at least something like "GeForce GT 320". 
PS: I read about the fact that this specific video card is not very well supported for linux. Is that really true?

Q2: 
After installing the nvidia driver:
```

sudo apt-get install nvidia-glx-185

```I retrieve the following information from my Xorg.conf

```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Unknown"
EndSection

```Does this mean that my nvidia card is not reckognized?

An extra check in the NVidia X Server app tells me that:
- GPU(0) = Unknown
- Graphic Processor = Unknown

I've read the following sites on help.ubuntu (and tried the best I could):
[https://help.ubuntu.com/community/NvidiaTroubleshooting](https://help.ubuntu.com/community/NvidiaTroubleshooting)
[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)
[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

Google-ed a lot and met loads of forums which helped me to get where I am now. Who can help me with the very last part :=)?

Thanks a million in advance.

Bas

---

### Post by cascade9 on 2010-04-18
Q1 and Q2- Yes, the video card is unrecognised. 

nVidia has no offical support for linux with the 3XX sereis cards. Strange, really, considering that they are just 2XX cards rebadged.

---

### Post by bprins on 2010-04-18
Thanks for the reply.

How unfortunate. And I thought nVidia was the way to go for ubuntu (or linux in general). If only... I would have checked the details for this specific video card.

Does this mean end of story for me?
- Will they ever support this video card in the near future?
- Is there a work around for this problem?
- If 3xx are kind of the same cards as 2xx, could I install the 2xx driver? Or will that cause other problems instead?

Also Compiz (useless, I know, but it looks fancy anyway :-)) claims 40-50% of my CPU power (seems a waste for my lovely i5 processor).

Still in hope of a bit of luck.

Best rgrds, Bas

---

### Post by cascade9 on 2010-04-18
You are normally fine with nVidia, but there are some cards that dont have offical support (GT3XX, GT230). A real pain....

They should have support for it coming. No idea when though. I would guess it would come with the 197 drivers, when they come out. 

I dont know of any workarounds, sorry :( 

You might eb able to install the newest drivers that support the GT2XX card (currently the 195 series). 

Yeah, compiz is usign that much CPU because its doing all the work that h video car would normally do.

---

### Post by bprins on 2010-04-18
You've been a great help. Thanks a lot.

I'll give the 2xx a try, and I'll keep my eyes open for nvidia updates.

At least I know it was not some user error by me. 

Thanks again.

Best regards, Bas

---

### Post by cascade9 on 2010-04-18
No problem, good luck. Hopefully nVidia releases the drivers soon ;)

---

