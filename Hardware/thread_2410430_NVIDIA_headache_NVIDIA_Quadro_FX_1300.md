---
title: "NVIDIA headache: NVIDIA Quadro FX 1300"
date: 2019-01-15
forum: Hardware
---

### Post by incorporeo on 2019-01-15
Hello, team!

I'm newbie at Linux ):P. However, so far, I'm somehow resilient (others say I'm masochist...)

My System is this:
Version Of Ubuntu : kubuntu-18.04.1-desktop-amd64
Type Of Hardware: HP Workstation XW6200; 2x Intel XEON 3.2MHz; 8GB Ram
Graphics card: NVIDIA Quadro FX 1300
OS installed: Windows Vista 64-bit; Windows 7 64-bit; Kubuntu

Let's talk about the graphics card:

After some reading and frustrating attempts to put this NVIDIA card functioning properly, I got a wired feeling that this card is strange...

First, I tried to install Ubuntu (not Kubuntu), and it was impossible to forward the instalation because, when I tried to assign my username/password, the keyboard didn't answer at all, in spite of CAPS-LOCK and NUM-LOCK be functioning through the leds.
I tried a second instalation of Ubuntu, then with a NVIDIA Quadro NVS 285 (less powerful) and the instalation was "properly" done, apart of the screen didn't function properly with picture desktops, and the recurrent system freeze not showing all the icons.

I gave up Ubuntu and opted to try Kubuntu with NVIDIA Quadro FX 1300.
The instalation succeeded.
However, some problems persist such as:
- In some windows, its content appears totally black, though I know there are icons and functionalities. I guess it when I pass the mouse inside it, and some pop-up information appears.
- However, the most frustrating happens on the 'System Settings' panel, where I only see a black rectangle in it, and the 'Discover' panel, where I can only see some black squares ordered in a white background with absolutely no characters.

So...
I believe the problem is related to the graphics card.

I know also that NVIDIA cards have been a recurring source of problems on Linux.
However, as I spent time enough aroun this process, and found (as someone wise told me) that many Linux sites are not trustful or simply outdated, I request from you some help about this, such as guidelines or trustful documentation, what I thank you in advance!

Cheers!

---

### Post by TheFu on 2019-01-15
According to [https://www.nvidia.com/object/IO_32667.html](https://www.nvidia.com/object/IO_32667.html), there isn't any proprietary driver support for this card.
The last working version was ... 
```
The 173.14.xx driver supports the following set of GPUs:
Note: Support for the 173.14.xx series is discontinued. No further releases from this series are planned.
NVIDIA GPU product 	Device PCI ID
GeForce PCX 5750 	0x00FA
GeForce PCX 5900 	0x00FB
Quadro FX 330/GeForce PCX 5300 	0x00FC
Quadro FX 330/Quadro NVS 280 PCI-E 	0x00FD
Quadro FX 1300 	0x00FE
```

I didn't see the 173.x package in the nvidia drivers PPA, so your only hope would be nouveau drivers.
I removed a Quadro 580 and 7200GT after being stuck at 768p with both and put in a GT 1030 to get a current GPU on a new system build.  Can't say that I'm happy about the results. I do have 2nd thoughts about switching to AMD GPUs.

All my other machines use onboard Intel iGPUs and life is so much easier.  But my new build is a Ryzen 5 CPU, which doesn't have any onboard GPU.

---

### Post by incorporeo on 2019-01-15
@TheFu, thanks for your info.

However I'm a bit confused since NVIDIA has a Linux64 compatible driver for [Quadro FX 1300]("https://www.nvidia.com/Download/driverResults.aspx/71303/en-us").
it is 'NVIDIA-Linux-x86_64-173.14.39-pkg2.run', released on 2013. Ok, it was discontinued.
I'm not intend to install this thing as it is, however. I don't have enough knoledge for that, as my last attempt leaded to a mess, resulting in a useless desktop.
(I used too much 'sudo apt-get' stuff before the system assumed to instal that nvidia.run thing.)

My next questions are:

How can I install an adequate driver from nouveau driver library?

or

how can I 'try' the proprietary drive mentioned above, with a safegard to do a secure uninstall using the shell in recovery mode?

or

what was the last stable version of Ubuntu (or other Linux platform) where this drive worked properly?



Thanks in advance.

---

### Post by TheFu on 2019-01-15
I don't have any good answers, sorry.

Installing a video driver from 2013 on a modern Linux would be bad. Don't attempt that, it won't work.

Nouveau is already installed on the system if you see any GUI at all.  It had poor performance and usually doesn't support the same resolutions that proprietary drivers support. Is this adequate?  I don't know, it wasn't for my desires.

No.

Probably an ubuntu from before it was release in 2013, so 12.04, which has been out of support almost 2 yrs.

I think you have 2 choices.
* use whatever nouveau provides
* buy a new GPU that has current drivers

---

### Post by CatKiller on 2019-01-15
> **TheFu said:**
> Probably an ubuntu from before it was release in 2013, so 12.04, which has been out of support almost 2 yrs.

nvidia-173 was included in 14.04, so *technically* it's still just-about-kinda supported for another couple of months.

The card, however, is 15 years old. Proprietary support for it has long ended, and it seems that nouveau doesn't meet the OP's needs.

Time to throw in the towel, I would say.

---

### Post by incorporeo on 2019-01-16
I would be happy if this card works simply as a **VGA** card on Linux.

It is fully functional in Windows Vista 64-bit and Windows 7 64-bit.

My intent was to reborn an old **PCI PCTV analogic card** which (funny!) is detectable in Ubuntu and Kubuntu.


There is an obvious contradiction in Linux philosophy.
If, for one side, it is assumed that Linux can reborn older machines, on the other side, newer versions of Linux simply compromise the first assumption.

[I]----

sudo apt-get install nvidia-173[/I]

gives me the final info: "*Unable to locate package nvidia-173*"


Of course is out of the question to spend any coin in newer hardware simply to put this particular system working.
So far, this have been a hobby for myself, and a way to learn something new like Linux.
I must say that *at work* I use a 6-core machine with Windows 10, and a 3GB VRAM NVIDIA Quadro.

Returning to the issue, probably I shall install Ubuntu 14.04 (is there any modern distro which can solve my issue?)

I believe installing an old license of Windows XP SP3 is giving a step backwards in technology...


I would thank to anyone any more clues on this.

> [COLOR=#000000]Time to throw in the towel, I would say.[/COLOR]

:) Probably yes, CatKiller! However, my problem is to be a little bit stubborn on things. The damn PCTV capture card will work, somehow!

Cheers!

---

### Post by CatKiller on 2019-01-16
> **incorporeo said:**
> 
There is an obvious contradiction in Linux philosophy.
If, for one side, it is assumed that Linux can reborn older machines, on the other side, newer versions of Linux simply compromise the first assumption.

The issue is entirely of Nvidia's making: they want you to buy a new graphics card.

They don't want to support a card that old with their proprietary driver, and they've hampered efforts to produce an open source driver so we can do it ourselves.

---

### Post by incorporeo on 2019-01-16
I found this info about **nvidia-173**, digging on this Forum:

[https://packages.ubuntu.com/trusty/misc/nvidia-173](https://packages.ubuntu.com/trusty/misc/nvidia-173)

Since I'm just interested in putting the 'NVIDIA Quadro FX 1300' to work as a **VGA** card, is it wise to go forward and try an installation using these files ou Kubuntu 18.04?

Thanks in advance for any clue.

---

### Post by CatKiller on 2019-01-16
It might work, it might break everything :)

If you aren't attached to the stuff that's already installed, it's worth a try. The 173 driver itself hasn't changed since it was released in 2010, and the part that interfaces with the kernel is DKMS, so there is a chance it will still work.

---

### Post by TheFu on 2019-01-16
If nouveau drivers work, that's the best answer.  Nouveau did work on my system, just at an undesirable, low, resolution.
 
Running a kernel from over a year ago is a terrible security decision. There are multiple remote attacks in the wild.

---

### Post by CatKiller on 2019-01-16
> **TheFu said:**
> Running a kernel from over a year ago is a terrible security decision. There are multiple remote attacks in the wild.
If installing those packages works, it would be using a recent kernel, with DKMS as the glue for the modules. It's what DKMS was invented for.

It will work until there is a binary incompatibility change between the kernel and the modules (which may have already happened). Neither the people responsible for the blob nor the people responsible for the kernel are going to fix it after that, so then it's nouveau or nothing.

---

### Post by Yellow Pasque on 2019-01-17
> **incorporeo said:**
> Since I'm just interested in putting the 'NVIDIA Quadro FX 1300' to work as a **VGA** card, is it wise to go forward and try an installation using these files on Kubuntu 18.04?

Absolutely not. The 173.xx driver won't work on 18.04 (the kernel and Xserver versions are too new for it). Dead end.

> I'm just interested in putting the 'NVIDIA Quadro FX 1300' to work as a VGA card.

I'm not sure what you mean by this. You can prevent the nouveau driver from loading and use a generic vesa driver, but you will lose video acceleration and performance will suffer greatly. That's probably not what you want.

[QUOTE=CatKiller]It will work until there is a binary incompatibility change between the kernel and the modules (which may have already happened)[/QUOTE]

Yes, it already happened. The kernel changes aren't so problematic because patches can often be made since that part of the nvidia driver is open source. It's the Xserver changes that really stop community effort from moving forward.

---

### Post by incorporeo on 2019-01-17
Sorry to interrupt your conversation, fellows, but I solved the problem \\:D/

Please follow this link [HERE]("https://askubuntu.com/questions/1110365/nvidia-173-on-ubuntu-kubuntu-18-04/1110669#1110669"), where I explain in detail what I did.

If this may lead to any security risks, I would be thankful if you say so.

Best regards, and beers for all! :D

---

### Post by TheFu on 2019-01-17
There are security risks whenever it is possible for the wrong code to be called o a program to crash or random code to be invoked.  

Finding a way to cause a program to crash is the first step in security testing. From that point, either inserting other "bad" code or just causing crashes over and over to deny the program from running can often be the goal.

Video driver issues are some of the worst because they run inside the kernel and are access by Xorg running as root.

If all the code entry points align and all the parameters align with correct types and boundary limits, then only normal driver issues would exist. I don't know how stable those APIs are and because nVidia is closed source, there isn't much we can do to analyze it.  On my system, there are 13 libraries, each would need to be checked.   [https://www.cs.swarthmore.edu/~newhall/unixhelp/compilecycle.html](https://www.cs.swarthmore.edu/~newhall/unixhelp/compilecycle.html) might be helpful, if someone was interested.  It will be hard, since all the symbols will be stripped from any commercial code.

But in the end, if you think this is a viable solution, great.  Please mark the thread as solved using the threat tools button near the top.

---

### Post by Yellow Pasque on 2019-01-18
> **incorporeo said:**
> Sorry to interrupt your conversation, fellows, but I solved the problem 
Please follow this link [HERE]("https://askubuntu.com/questions/1110365/nvidia-173-on-ubuntu-kubuntu-18-04/1110669#1110669"), where I explain in detail what I did.

It looks like you blacklisted nouveau and are using generic vesa driver (and you unnecessarily played around with dead end 173 driver). I guess if you have dual Xeons, they make up for lack of graphics accel. Look at glxinfo to see which driver you are using:
```
glxinfo -B
```

---

### Post by incorporeo on 2019-01-18
Hello @[COLOR=#000000]Temüjin

I ran ```
glxinfo -B
``` and the following report appears:

[/COLOR]```
name of display: :0
display: :0  screen: 0
direct rendering: Yes
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: VMware, Inc. (0xffffffff)
    Device: llvmpipe (LLVM 6.0, 128 bits) (0xffffffff)
    Version: 18.0.5
    Accelerated: no
    Video memory: 7977MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 3.3
    Max compat profile version: 3.0
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.0
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: llvmpipe (LLVM 6.0, 128 bits)
OpenGL core profile version string: 3.3 (Core Profile) Mesa 18.0.5
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile


OpenGL version string: 3.0 Mesa 18.0.5
OpenGL shading language version string: 1.30
OpenGL context flags: (none)


OpenGL ES profile version string: OpenGL ES 3.0 Mesa 18.0.5
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00

```

Please feel free to give me an opinion about it.

---

### Post by TheFu on 2019-01-18
Are you running Ubuntu inside a VM?  If so, the physical GPU doesn't have anything to do with that.

---

### Post by incorporeo on 2019-01-18
Actually I never used any Virtual Machine.
I even don't know how such thing can be done.

The only thing I have in this particular PC is a 3-boot with Windows Vista 64-bit, Windows 7 64-bit, and recently, Kubuntu.

I realized, however, that the driver was signed as VMware...
But this was now, when I saw the report on my last post.

I believe this may be strange, but it's a fact.

UPDATE:
I believe this may be due to a known bug. Just a thought.
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1752938](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1752938)

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1802353](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1802353)

---

### Post by TheFu on 2019-01-18
The point is that you aren't using nvidia drivers as Temüjin guessed.

---

