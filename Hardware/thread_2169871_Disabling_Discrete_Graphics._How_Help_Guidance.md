---
title: "Disabling Discrete Graphics. How? Help? Guidance?"
date: 2013-08-23
forum: Hardware
---

### Post by barry.of.smithgmail.com on 2013-08-23
Hello,

My situation is quite complex, and has been bugging me for some time so I would be really glad if someone could help. I'm sure there is a solution though, because I worked it out before on a previous install. I just can't remember how. Let me explain.

Currently I am running Ubuntu 13.04 x64 on a Dell Inspiron 15R laptop with AMD Radeon HD 7xxx (I think) graphics and discrete Intel Ivybridge Mobile graphics.

I used to run Linux mint on this PC too, but I removed it for other reasons. HOWEVER, I found a way to disable the discrete graphics previously on my Mint install, and I managed to install fglrx proprietary drivers successfully, with the computer running off just the Radeon HD graphics card.

However, since installing Ubuntu I have been unable to remember how or what I did to achieve this - attempting to disable discrete graphics with vga_switcheroo simply doesn't work (*lspci | grep VGA *still shows both graphics and the laptop fan continues to run at top speed even when the computer is idle - apart from anything else, this means I have a crap battery life). When I try to install fglrx drivers (both from AMD and the Ubuntu repos) the XServer simply doesn't start correctly, no window decoration is shown, and the computer becomes unusable. I have to drop to the terminal to remove fglrx. (I suspect that this is due to the fact that Ivybridge Intel graphics are still active, and the driver is not compatible with it.)

I need this fixed for a number of reasons:

1) My fan is far too loud and it has become very annoying
2) I am afraid that the fan running at 100% for large periods of time (I use my PC very often) is likely to damage it
3) My laptop battery is rubbish, often getting less than an hour from full charge when the manufacturer tells me that 4 hours is common
4) I cannot install AMD fglrx drivers, meaning that some 3D games or 3D effects (compiz, etc.) do not work due to the lack of shader support in the opensource drivers.

The results of ```
lspci | grep VGA
``` are as follows:
```

00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Chelsea LP [Radeon HD 7730M] (rev ff)

```

I love Ubuntu and I think it's great, but this problem is starting to seriously drive me away from it due to how ruined my experience with it is.

Thanks so much for reading,

Barry Smith

P.S: Please try to keep things in simple terms - I'm generally good with Linux, but I want to make sure I get this right :)

---

### Post by buzzingrobot on 2013-08-23
Check your BIOS settings for an option to enable/disable the discrete card (AMD) or the Intel. Optimus might be there, too.

---

### Post by barry.of.smithgmail.com on 2013-08-23
No, there's nothing in the BIOS graphics-related, I've already checked several times :( Thanks for the suggestion though!

---

