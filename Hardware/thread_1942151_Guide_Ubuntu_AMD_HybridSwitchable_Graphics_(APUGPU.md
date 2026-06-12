---
title: "Guide: Ubuntu AMD Hybrid/Switchable Graphics (APU/GPU) (C2.2)"
date: 2012-03-17
forum: Hardware
---

### Post by gdea73 on 2012-03-17
Well I think I've finally found a way for AMD Hybrid Graphics users to be able to use either GPU on their machines running Ubuntu with AMD's proprietary fglrx driver (+ Catalyst 12.2).

The purpose of this thread is to discuss solutions for AMD Hybrid Graphics (AMD A-Series APU, with an additional discrete AMD Radeon HD card). This is somewhat common in newer laptops and until now I hadn't seen any Ubuntu discussions of how to do this on Linux; to get both adapters working separately and have the ability to switch between them.

The following is what I did, on my laptop, the Lenovo IdeaPad Z575, to get either graphics accelerator working. It requires a bit of work and a reboot to switch, but at least it works on either one. In my case, the hardware was an AMD A6-3420M APU with a Radeon HD 6650M GPU. I run Maverick (10.10) x86_64.

1. Download AMD's drivers ([url=http://www2.ati.com/drivers/linux/amd-driver-installer-12-2-x86.x86_64.run]link/url])

***Note**: I think the link provided is for both 32-bit *and* 64-bit Ubuntu, yet I'm not sure. It worked on my 64-bit install, and it is the same link if I select "Linux_x86" in the dropdown box. If it's not working for you, try to find another link yourself, and also please let me know via this thread.*

2. Once you've downloaded the file, move it to its own folder in your home folder, in this case "catalyst12.2". Now you have to run a few commands:

```
cd ~/catalyst12.2
sudo sh ./amd-driver-installer-12-2-x86.x86_64.run
```

***Note**: You can usually just type "sudo sh ./amd" followed by the [Tab] key to autocomplete the filename. My filename might not be the exact same as yours.*

3. You should get a (to some extent) graphical installation prompt. Select the top option (install the driver, 8.xx), not the distribution-specific deb option (the bottom one). When prompted, choose an automatic installation. The rest is straightforward; actually, it's just a short wait while the drivers are installed.

4. After installation, you can reboot. You shouldn't need to run the amdconfig command, unless you have further issues. For me, I had Catalyst working, but it was using my discrete GPU (the Radeon, not the APU). This is not great for battery life, and the point of this thread is to explain how to switch between the two. At this point, in my BIOS, I had the Hybrid Graphics option set to "Dynamic," i.e. both adapters, or the like (enable just the discrete graphics if possible, for me it was either UMA-Only or Dynamic).

***Note**: **DO NOT** use the "Switchable/Hybrid Graphics" tab in Catalyst or change settings within that tab! This for me causes purple-screen errors and other nasty things. It's important that you let Catalyst stay thinking that it's using the *most powerful* and *least power-efficient* adapter available; you control the actual setting in the BIOS.*

5. Now, if you wish to switch to using APU-only graphics, shut down your computer, and boot into the BIOS. (The hotkey for me was F2, so I held it down upon boot. Keys may vary, they're usually listed on-screen during the POST (Power On Self Test).) The BIOS option will also vary, but for me I changed "Graphic Device" to "UMA Only," from the default "Dynamic," completely disabling the discrete GPU and making it invisible to Catalyst. Afterward, save the changes and reboot.

If all goes well, Catalyst should (by step 5) recognize ONLY your APU's built in graphics processing unit, and think that that is the only GPU in your system; which to an extent produces the desired effect and elongated battery life, especially because the discrete graphics chip is completely disabled until you turn it back on in the BIOS.

I was lucky that the AMD drivers worked, with the discrete card, right after I installed them. Your mileage may vary, you *may* have to run the *amdconfig --initial* command, or a variation thereof, to get a usable desktop environment with fglrx. In that case, I suggest you consult the installation guide for fglrx hosted by [CCHTML](http://wiki.cchtml.com).

I wrote this guide in hopes that others with a similar laptop/chipset could have some hope in their hybrid graphics and other Linux endeavors; if you find any errors or have trouble on similar hardware, please don't hesitate to post back in the thread and we can discuss solutions together. Though on Windows with the proprietary drivers installed one may be able to switch graphics adapters more seamlessly, I'm really happy that I can at least get them working independently and preserve some battery life. Ultimately I hope that the next person frantically searching for a way to get their AMD/AMD hybrid graphics working will have something remotely resembling a solution, and I think that's what I've found. Good luck!

- gdea73 -

---

### Post by zaphod_es on 2012-04-15
Is that the same as this hardware?

[http://www.cpu-world.com/CPUs/K10/AMD-A6-Series%20A6-3420M.html](http://www.cpu-world.com/CPUs/K10/AMD-A6-Series%20A6-3420M.html)

I am getting nowhere trying to even install Mint 12 and will follow your instructions if they apply to my cpu/gpu

ZB

---

### Post by gdea73 on 2012-05-30
zaphod_es: If you're having other specific issues it may be more beneficial to open a separate thread; however, for the purpose of answering your initial question, yes the processor you linked to is I believe identical to the one in my laptop, and the guide should apply to Mint 12, AFAIK.

Granted my next project will be installing Arch on this, and that'll assuredly be its own challenge; well, that, after I fix my server, of which the southbridge died.

---

### Post by zaphod_es on 2012-05-31
I am afraid I took the coward's way out and dumped Mint and installed Ubuntu 12.04. This installed fine with no issues. I guess it was the later kernel that did the trick. I don't think it works with 3D but that is not an issue for this computers.

Thanks for the useful tip, I will have another go with Mint one day.

ZB

---

### Post by gdea73 on 2012-06-02
Alright, well I'm glad it seemed to work out for you. You mentioned that 3D didn't work and you hadn't installed proprietary drivers; while this may work, I recommend you do install AMD's drivers or at least disable the discrete graphics in BIOS (maybe both) to decrease power consumption. For me, the default installation of Ubuntu was not power-efficient because it used my discrete graphics card unless I disabled it in BIOS, and I'm not even sure if the open source drivers worked with the APU (3420M)...

---

### Post by Rexhunter99 on 2013-05-05
I found this thread (under a mountain of NVidia/Intel switchable graphics topics and blogs) and thought it was best to continue on in here the issue I am having since they seem to be one and the same.

First of all I'd like to start with the fact I used to have a laptop with Dual AMD graphics, an APU A6 with 6xxxG Radeon Graphics and a discreete 7xxx card, using the above methods (I discovered on my own) worked fine.  On my current laptop I use bumblebee as the laptop is an Intel HD 3000 + NVidia GT 630M setup, so no issues there.

Now on my gaming desktop I have a new A8 APU which is not part of the K architecture, the intergrated GPU is 7550D from what I recall and the brand spanking new Radeon HD 7750 card runs like a dream, I can get it to compete easily with my GTX card on another desktop.  Now on windows I have zero issue obviously since Catalyst works fine and allows me to use the APU as a second processor for graphics (PEG is default adaptor in BIOS)
I recently decided (last few months) to install Ubuntu on my desktop but I can't seem to do anything past the boot screen as the boot loader on the CD Rom for Ubuntu refuses to accept my PEG adaptor. I have to reboot with the HDMI in my IGD port and then I can install as normal.  Now I can't stand having to pull the machine out, reconnect cables just to switch OS.  I've tried various methods, I've tinkered with the XOrg config, told it to force load on the PEG card, but no go there.

Normally I'd be content with running on IGD and using the PEG as a booster card, but the 7750 card has certain OpenGL extensions not available on the APU and I'm a graphics programmer so I need these extensions.

Right now I'm just hitting my head against a wall and hoping I can butt the mortar out to dislodge the bricks, but its slow going.

---

