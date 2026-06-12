---
title: "Hardware for Gimp and Darktable"
date: 2022-01-21
forum: Hardware
---

### Post by Cadryc on 2022-01-21
Hi

I am thinking about building a new computer. My current one is a Core2duo with 4GB Ram and it is beginning to show signs of the hickups...

For Darktable, Gimp, web surfing and wobbly windows (love those and plays around with other effects with gnome extensions), do you recommend a Ryzen 5700G or an Alder Lake, ie 12600K or 12700 with integrated graphics?

Would I reap the benefits from Vega with those tasks, or is an Alder Lake a better bet?

Ryzen 5700G only utilizes pci3 while Alder Lake uses pci4, if I got it right?, which maybe will make a difference with nvme performance?

Or should I bite the bullet and invest in a graphics card as well?

(I am aiming at 16GB RAM if the budget allows. I have zero interest in gaming and don't watch film on the computer)

---

### Post by jimmy-frydkaer on 2022-01-21
You'll be better off with dedicated graphics and not some onboard solution, GIMP takes a lot of RAM, and the more RAM and dedicated graphics you've got the better.

---

### Post by Cadryc on 2022-01-21
So dedicated graphics makes that much of a difference then. Even ie GeForce GT 2GB? Only affordable one I found. Or should I go for something that cost about the same as the cpu? Or more....

Are AMD of Nvidia to prefer?

---

### Post by Cadryc on 2022-01-21
My current setup have a Radeon HD4870 (RV770). lspci -v -s reports 256M so I am guessing this graphichs card is to be considered non existent in modern days...

I'm thinking, maybe I'll get a dedicated gpu later on. In the mean time I would go with the integrated stuff. Would Vega give a noticable performance jump over Intel UHD 770?

I have done very little in gimp and darktable this far, but I would like to do a bit more (dreams, you know) Thou time for this is not guaranteed of course...

Update glxinfo reports
Video memory 1024 MB
Dedicated video memory 1024 MB
Total available memory 2045 MB

(I got 4GB RAM)

---

### Post by Autodave on 2022-01-21
You are really going to need a dedicated GPU even if it is not the one of your dreams at the moment.  A 2 gig would be OK depending on the speed of it.  As always, more is better.

---

### Post by Cadryc on 2022-01-21
Thanks both of you for your help.

Just one last thing, are Nvidia or AMD gpu working best in Ubuntu nowadays?

---

### Post by jimmy-frydkaer on 2022-01-22
I'd go with AMD since the drivers for that are in the kernel.

---

### Post by Perfect Storm on 2022-01-22
I'll go for Nvidia for better performance

---

### Post by Autodave on 2022-01-22
+1 for nVidia.  The newest drivers are always available.  Now, having said that, AMD is always easier to get working.  Personally, I have only ever had one issue with nVidia and it was simple to overcome.

---

### Post by Cadryc on 2022-01-22
What about this?
[https://github.com/RadeonOpenCompute/ROCm/issues/1397](https://github.com/RadeonOpenCompute/ROCm/issues/1397)
Relevant?

---

### Post by &amp;KyT$0P# on 2022-01-22
> **Cadryc said:**
> What about this?
[https://github.com/RadeonOpenCompute/ROCm/issues/1397](https://github.com/RadeonOpenCompute/ROCm/issues/1397)
Relevant?

Only if you plan to do machine learning / AI stuff with this computer.

For me AMD graphics have always worked best with Ubuntu for the type of things you mentioned in the first post.  Just make sure the specific AMD GPU you choose is fully supported by your Ubuntu version's kernel.  If your Ubuntu version is a LTS there is the option of the HWE kernel if the stock kernel is not recent enough.

---

### Post by Cadryc on 2022-01-22
Tank you very much for your insight

---

### Post by Yellow Pasque on 2022-01-23
If it was me, I'd build around a Ryzen 5600/5700G and see if that met my needs. They have very good integrated graphics. You can always throw in a discrete GPU later.

---

### Post by mIk3_08 on 2022-01-23
> **Cadryc said:**
> Hi
I am thinking about building a new computer. My current one is a Core2duo with 4GB Ram and it is beginning to show signs of the hickups...
For Darktable, Gimp, web surfing and wobbly windows (love those and plays around with other effects with gnome extensions), do you recommend a Ryzen 5700G or an Alder Lake, ie 12600K or 12700 with integrated graphics?
Would I reap the benefits from Vega with those tasks, or is an Alder Lake a better bet?
Ryzen 5700G only utilizes pci3 while Alder Lake uses pci4, if I got it right?, which maybe will make a difference with nvme performance?
Or should I bite the bullet and invest in a graphics card as well?
(I am aiming at 16GB RAM if the budget allows. I have zero interest in gaming and don't watch film on the computer)
16 GB ram is already a good one for Linux Ubuntu Operating System. Much better if  you don't go for Nvidia video card cause it might gives you headaches. actually, your plans for your hardware can already perform a better system specially Linux Ubuntu Operating System. So good Luck and Cheers.  Welcome to Linux World.

---

### Post by Perfect Storm on 2022-01-23
> Nvidia video card cause it might gives you headaches.

I have seen my fair share of headache with AMD cards even it's open source, so there's no guarantee.

---

### Post by TheFu on 2022-01-24
> **Yellow Pasque said:**
> If it was me, I'd build around a Ryzen 5600/5700G and see if that met my needs. They have very good integrated graphics. You can always throw in a discrete GPU later.

+1.

A few months ago, I built a $420 system with 
* Asus B450 ROG Strix MB - intel NIC
* Ryzen 5600G - the built-in GPU is/was less expensive than **any** GPU I was willing to buy extra.
* 16G DDR4 RAM.

As for NVMe x3 vs x4 ... there's the theory and then there's reality.  In reality, you'll likely never use the extra performance.

but you haven't said any budget limits, so that makes it hard.  I was trying to build a $300 system with a 65W CPU (my days of 100W+ CPUs are long over). It just isn't necessary for non-gamers.

Heck, LTT had a video today about used/cheap system upgrades and was recommending a B450 + Ryzen 1500 or 2600 CPU as a starter.  In a few years, the higher end CPUs will drop 50% and just a CPU swap using the same RAM and MB will enable 40%-100% faster performance.  That's the great thing about AMD sockets - their entire line of CPUs use the same socket so there is an upgrade path for much longer than with Intel.

Last week, LTT did a comparison of a 5600G with an external $200 GPU and using just the internal GPU. This was from a gaming perspective.  Which was all about FPS ... he wanted to see 100 fps in some game nearly all the time.  The external, overpriced GPU was an AMD 6500 XT and did get 100fps 98% of the time in the game he used.  The onboard iGPU was less fps, but on the screen I couldn't see the difference.

My Ryzen 5600G is mainly a server. I haven't looked at the screen it connect to in a few weeks.  That screen is on an HDMI switch which usually shows some other devices output.

My Ryzen 2600 has an nVidia 1030 GPU (DDR5 version).  I can't tell the difference (1030 GT vs 5600G GPU), except that nvidia drivers are a hassle to maintain. I've added special update steps to my weekly system patching to deal with nVidia. Have another box with a GT 430 (another low end nVidia). It is much more hassle.  I know that the 5600G needs a kernel at least 5.10+ or later for the AMD GPU drivers to work. That's when the AMD drivers for the 5000 series Ryzen APUs was included.  The video worked before I moved to a kernel with the amd GPU support, just not great. At this point, 21.10 and 22.04 and 20.04 HWE kernels all support AMD 5000-series APUs, so for a new Ubuntu system, it will be fine and it much more cost effective than buying a separate GPU.  

If cost isn't the primary concern, then I don't know. It always is for me.  I only need a GPU to do minimal stuff - run at the native resolution of my monitors, support video playback (h.264/h.265 in HW decoding) and mostly have the correct colors. Anything more just doesn't matter to me.  I worry more about audio output clarity than video and that doesn't matter too much either.

I've only played with gimp and never touched darktable.  Most of my photos are from travels and since I haven't traveled much the last 2 yrs, there hasn't been much photo editing here.

---

### Post by aug7744 on 2022-01-25
Dedicated video card have better color and frame rate quality.
Today the minimum is 2 GB VRAM, but if is cheap a video card with 4 GB VRAM is better choice.

---

### Post by Cadryc on 2022-01-26
I have stuck with Ubuntu LTS and will probably do so in the future as well.

I have more or less decided to go with a dedicated graphics card. Therefor I'll pick Alder Lake Over Ryzen, it seems to have the edge over Ryzen atm.

I'll take more ddr4 RAM over less ddr5 RAM for equal or less price. 

I'm leaning towards the Asus Z690M-Plus D4 motherboard. It got Intel networking, looks better than the Gigabyte mobos, plus the D4 moniker gives me Klingon vibes. Also, being pcie5 I can upgrade to a cutting edge nvme in a couple of years and save myself a couple of microseconds in boot time. Of course you remember what Jobs said about boot time to the tormented and sleep deprived developer.

And, my preferred webshop have RAM that are on Asuses qvl fot that mobo.

I mined old reciets and found that my current computer is from 2007, 14.5 years old. I have only replaced the PSU and upgraded to SSD over the years

---

### Post by TheFu on 2022-01-26
Early releases of new HW tech often doesn't actually perform all that great.  This is about the PCIe stuff.

You are like me and keep systems far too long, to the point that they can't be sold or handed down to anyone when we are finished. Guess that's a liability, but it also means that over a 10+ year period, the extra $100-$200 isn't all that important.  I'm trying to include cheap CPU upgrades in my game plans going forward. With Intel, that's next to impossible.  But when a Ryzen 5800 is $100, I'll easily be able to replace my 2600 for it and get, let me check, 

2600 Passmarks: 13198 
5800X Passmarks: 28442 
So more than 2x the performance without changing anything else.  My 2600 is 2 yrs old now and replaced a 2009 Core i7. No regrets. None. In 2 more years, a much faster Ryzen will easily be available for cheap and the game-at-any-cost people upgrade.
LTT about saving money on CPUs: [https://youtu.be/LmA0FtDHlss](https://youtu.be/LmA0FtDHlss) (new this week).

---

