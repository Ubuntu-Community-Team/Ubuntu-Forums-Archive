---
title: "What computer for ubuntu"
date: 2014-07-28
forum: Hardware
---

### Post by rosswmcgee on 2014-07-28
I was unable to install Ubuntu 14.04 lts on any of my older computers that are amd athlon LE-1640 with 1.8gb. I am told ubuntu 14.04lts will not use these amd

 drivers and the drivers are the problem. If I change drivers it crashes the system. So after 10 years or so of never buying a new machine and using 

 linux distros I am ready to try a new machine. Question AMD vs. intel and will ubuntu work with AMD at all? I am currently running Mint qiana mate 17 on one computer

 the other maya. The older maya is more stable than the qiana, but at least I could install it. Opera works perfectly in Qiana but FF and Tbird often cause

 crashes. 

 Example Best buy has a dell inspirion with 1tb and 4gb for 329 dollars, do I need more? I am not partial to dell but HP mostly uses AMD. Any sugesstions appreciated. Ross

---

### Post by ibjsb4 on 2014-07-28
I have Dell desktop and laptop, there both 5 years old but I really like them and would go with Dell again.  In the past I have had IBM (Livorno), cost more, but worth it IMO.  Both have ran Linux without issue.

HP has two classes of machines.  There business machines which are built with identical parts and there consumer machines which use whatever parts that are at hand.  I have had bad luck with there consumer machines (both new and used) and would not buy another one.  They run Linux just fine, but I have had hardware problems with them in the pass.

And that old machine of yours, try Lubuntu on it, it uses less resources.  About AMD processors and video, I do not know.  I run only Intel and prefer Xeon processors.

[http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by rosswmcgee on 2014-07-28
You know I think you are right. I spent some time at Best Buy and looked at the dells one for 449 1 tb 8gb and fooled around with win 8.1 good grief!! Who needs it

simplicity of mate is superb.

---

### Post by grahammechanical on 2014-07-28
> [COLOR=#000000]Question AMD vs. intel and will ubuntu work with AMD at all?[/COLOR]

Of course it will. The CPU is not the cause of problems with installing any Linux distribution on the latest hardware. It does not matter whether the CPU is Intel or AMD, Ubuntu 14.04 will run on either.

The areas that have the potential for being a pain are:

a) a machine with Hybrid graphics. This is where the issue of drivers comes up. 

[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

Note: the issue is not with the CPU but having a graphic system that automatically switches between an integrated Intel graphic adapter and either a Nvidia graphic card or an AMD graphic card and needing Linux drivers that will switch between the two adapters.

2) a machine with Windows 8 installed. We need to understand the advice given here:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.[FONT=inherit][/FONT]
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[FONT=inherit][/FONT][/FONT]

[*=left]if Ubuntu is the only operating system on your computer, then it does not matter, you can install Ubuntu in EFI mode or not.
[/LIST]

Regards.

---

### Post by mastablasta on 2014-07-29
assuming you are after laptop here - get HP or Dell (or other brand) "business machine". they built are more sturdy and often work with Linux out of the box. they may even come Linux preloaded.

if you need a desktop have a look at mint box maybe.

plenty laptops have hybrid graphics - AMD supports at leats some of them. for NVidia there is bumblebee project.

Intel and AMD also make GPU on CPU option called APU. AMD marks them with A I am not sure how intel marks their but usually it would say what intel GPU chip the processor has. intel GPU drivers are opensource and the chip is not as good as AMD's. AMD has closed source drivers for their chips, but it seems they are moving towards having opensource only as well (porting stuff fro0m closed source driver to opensource...).


win8.1 is not that bad. the main issue is the menu. but that is not much different to the way gnome does it or maybe Active plasma. once you see it is really not that much different than previous desktops. ok it has touch and programs in those tiles, but it also has what is basicallya start menu. not much different to unity. you can easilly search the app and launch it. or pin it top desktop or to taskbar.

---

### Post by mörgæs on 2014-07-29
Did you try Lubuntu 14.04.1 as mentioned in post #2? 
It's a K8 processor so I would still consider it useable.

---

### Post by kurt18947 on 2014-07-29
I just 'renewed' a desktop machine with an AMD A6-6400K dual core APU on an ASRock FM2A88M-HD+ motherboard, 4 GB RAM.No issues with Ubuntu-Gnome 14.04 to date, it's working well.   I did not install the proprietary AMD drivers, didn't see the need.  The machine I'm composing this on is a Gigabyte M.B. with Athlon II X2 240 processor,  Nvidia 210 graphics card 4 GB. RAM. , no issues.  ATI/AMD proprietary drivers have been a sore point in the past, I thought that was improving.  Point being in desktops at least I don't see any reason to shy away from AMD powered machines and the first machine I mentioned cost me U.S. $140 reusing case, power supply and drives.

---

