---
title: "Help me with my Build for Ubuntu"
date: 2016-08-12
forum: Hardware
---

### Post by RJLiberator on 2016-08-12
Hi all,

I'm making a big purchase and wanted to make sure that I'd be able to run Ubuntu/Linux based Operating systems flawlessly with my hardware.

CPU: Intel Core i7-6800K 3.4GHz 6-Core Processor  ($409.99 @ Newegg) 
CPU Cooler: Cooler Master Hyper 212 EVO 82.9 CFM Sleeve Bearing CPU Cooler  ($24.88 @ OutletPC) 
Motherboard: Asus X99-A II ATX LGA2011-3 Motherboard  ($225.99 @ SuperBiiz) 
Memory: G.Skill Ripjaws V Series 32GB (2 x 16GB) DDR4-2133 Memory  ($124.99 @ Newegg) 
Storage: Samsung 850 Pro Series 512GB 2.5" Solid State Drive  ($220.70 @ NCIX US) 
Case: Fractal Design Define S w/Window ATX Mid Tower Case  ($79.99 @ Newegg) 
Power Supply: EVGA SuperNOVA G2 550W 80+ Gold Certified Fully-Modular ATX Power Supply  ($79.49 @ SuperBiiz) 
Total: $1165.03

NO GPU YET.

I'm deciding between GPU's currently as my final piece to the puzzle. Thinking between GTX 950, 960, 970, 750 Ti or Radeon r7 370, r9 380 or the newest GTX 1060  (doubtful as it is out of stock everywhere and getting pricey).

Essentially, my post here is to confirm that my hardware choices will allow me to run Ubuntu or different linux based OS with no major problems (would suck to get this going and find out I cant run my os!) .

Thank you.

---

### Post by oldfred on 2016-08-12
I have seen a couple of X99 systems and they have had issues installing video drivers.
I have build both Skylake & Haswell systems without issue. 
At least one user used internal video (which your X99 does not have) to install & boot. Manually install a nVidia driver and then used nVidia without issue.

I do not use AMD, but currently it proprietary driver will not work in 16.04 and the rest of your system needs 16.04 or even perhaps ppas to get even newer versions of kernel & drivers.
 [http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04](http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04)
[https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)
16.04 Release notes
When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware). 
With 15.10 Release notes
AMD's fglrx driver does not work with the current kernel
The fglrx driver is now deprecated in 16.04, use radeon and amdgpu 

This site often does video card reviews with Linux.
This is older, I am sure he now has newer ones.

 22-Way Comparison Of NVIDIA & AMD Graphics Cards On SteamOS For Steam Linux Gaming Oct 2015
[http://www.phoronix.com/scan.php?page=article&item=steamos-22-gpus&num=1](http://www.phoronix.com/scan.php?page=article&item=steamos-22-gpus&num=1)
(link not working, but entire site seems down, I was in it yesterday so assume temporary issue)

This thread with x99 says he was able to install 14.04.
[https://ubuntuforums.org/showthread.php?t=2299349](https://ubuntuforums.org/showthread.php?t=2299349)
This user has not come back to say if he ever got it to work or not.
[https://ubuntuforums.org/showthread.php?t=2332209](https://ubuntuforums.org/showthread.php?t=2332209)

---

### Post by RJLiberator on 2016-08-12
*bow*
Thank you for your kind guidance.

Since the x99 seems to have issues installing video drivers, you are suggesting that there may be a problem in reaching my display if I boot with linux OS? 

> I do not use AMD, but currently it proprietary driver will not work in 16.04 and the rest of your system needs 16.04 or even perhaps ppas to get even newer versions of kernel & drivers.

Therefore, it is likely a safer bet to go with Nvidia GPU for my linux OS build.

---

### Post by oldfred on 2016-08-12
This site working again for AMD, he only uses the open source driver which is all that works, currently:
 18-Way GPU Linux Benchmarks, Including The Radeon RX 460 & RX 470 On Open-Source
[http://www.phoronix.com/scan.php?page=article&item=amd-rx460-rx470&num=1](http://www.phoronix.com/scan.php?page=article&item=amd-rx460-rx470&num=1) 

With nVidia, the most common way to install is to use nomodeset to get low quality graphics and then install nVidia driver from repository (or if newest nVidia card, add ppa first). If gui working you can go to System Settings, Software & Updates & drivers tab.
If only command line, you can manually add nvidia driver from there. But if it does not boot to command line then major issues.

With my Haswell Asus build I must have changed 8 or 10 UEFI settings to get it to boot in UEFI mode.

My first SSD was 60GB as Microcenter had an its own on sale relatively cheap. But I had two copies of Ubuntu on SSD in 27GB / (root) and all data on HDD.
My Haswell build has 120GB SSD and I do not know what to do with all the space.
And Skylake has M.2 SSD and I was surprised by how small that is.

---

### Post by RJLiberator on 2016-08-12
> But if it does not boot to command line then major issues. 

This is exactly what I'd like to avoid at all costs. 

Is there any way to predict this from different GPU's or setups? [COLOR=#000000]

[/COLOR]

---

### Post by oldfred on 2016-08-12
I have only seen a couple X99, so not sure.
It may be different brands work better. 
I might search Internet or the Phoronix site where users post results to see if any X99 systems?

Do not know difference to Z170 as that was my last build in a SFF case. I do not game so just wanted Intel video.
Google has some comparisions:
[https://www.google.com/search?client=ubuntu&channel=fs&q=Intel+X99&ie=utf-8&oe=utf-8#channel=fs&q=Intel+X99+vs+z170](https://www.google.com/search?client=ubuntu&channel=fs&q=Intel+X99&ie=utf-8&oe=utf-8#channel=fs&q=Intel+X99+vs+z170)

---

### Post by CatKiller on 2016-08-12
You don't say what you'll be using the computer for. For all of the games I play in Linux, my 960 has been fine and caused no problems. TBH, the 560 Ti I had before was also perfectly fine. My laptop with integrated Skylake graphics also had no problems.

---

### Post by RJLiberator on 2016-08-12
Hi CatKiller, sorry I didn't add purpose.Purpose of build:

This will be a school computer (undergrad/graduate for the next 6-8 years). I will be doing data calculations, numerical analysis, some minor 3d modelling, running physics based applications, etc. Also some video editing.I would like to be able to play some games, but this is, at the moment, secondary.
I want to run a Linux based environment (likely Ubuntu)
I want to have a dual monitor set up, so a GPU that allows this is a must.

---

### Post by RJLiberator on 2016-08-12
This is killing me. I've searched some 6-8 GPU's relentlessly in the past day or so.

I keep hearing AMD is not so good for Linux which puts me towards the 750 Ti for bargain, 950 or 960 for better performance, or even 970 for my best performance.

---

### Post by RJLiberator on 2016-08-12
Right now I'm looking at buying a GTX 960 for $180 before rebates.

---

### Post by CatKiller on 2016-08-12
Your build seems fine for the purposes you've listed. Any moderately recent GPU will be fine. Multi-monitor is potentially fiddly whichever GPU you go with, although they are all capable of it. If you're using CUDA for your modelling you'll need an NVidia card and the proprietary driver, but you'll probably already know if you need that.

I haven't checked the specs of your motherboard, but some onboard network interfaces have historically been fiddly. Intel ones have always been fine, and I have no idea if it's even an issue these days.

---

### Post by RJLiberator on 2016-08-12
Nevermind, just found a GTX 1060 (new) for either $270 or $300.00 hmm..... These with 6GM Vram seem awesome.

---

