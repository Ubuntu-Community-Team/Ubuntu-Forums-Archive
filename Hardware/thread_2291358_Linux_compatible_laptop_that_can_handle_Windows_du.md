---
title: "Linux compatible laptop that can handle Windows dualboot"
date: 2015-08-19
forum: Hardware
---

### Post by Anders_Makowicz on 2015-08-19
Hello!

I`m looking for Linux compatible laptop which can handle dual boot with Win7 and has big screen (17inch)

I will mostly use Xubuntu or other Linux on it just to browse internet or watch videos and stuff like that, but sometimes i would like to play some games so i want it to have no problem to run games like GTA 5 smoothly.

I know that gaming PC is better option, but i will be changing my living place like one time per month

I don`t even know if it`s possible for processor to run GTA 5 on Windows and run Linux at the same time but sometimes i will play lighter games like Diablo 2 and i don`t want to mess with Wine anymore

I`m planning to get out unnecesary crap out of Win7 to reduce CPU usage and use it only as ``game playing machine``.

What`s best price=quality option? (i don`t want to buy a Macbook just because of apple on it)

I live in England if that could help with price comparision.

Thank you very much! ;)

---

### Post by Bucky Ball on 2015-08-19
Jeez, where do you start! Erm, look for 17inch laptops and post back a few that look good? They probably dual-boot fine. Anything with a 17inch screen is going to have enough grunt to dual-boot anything.

Incidentally, you can dual-boot on the dinkiest of specs. The two operating systems don't run at the same time. Probably best to read up on dual-boot. Xubuntu will boot on a machine with an ARM processor and 1Gb of RAM.

If you are thinking Wubi, Ubuntu installed in Windows, don't go there. Not supported. 

So look for something with 4Gb of RAM at least and 17inch screen and you're good to go. Of course, if there are the four virtual machines you are intending to run but haven't mentioned, then you'd better up the RAM considerably. :)

---

### Post by ajgreeny on 2015-08-19
As you are in UK, have a look at [http://www.pcspecialist.co.uk/](http://www.pcspecialist.co.uk/) who certainly make machines that will run Linux without a problem; I have a desktop machine and my wife a laptop both running Ubuntu with no difficulty out of the box, though I bought both with no OS installed.

The great thing is that you can configure the hardware they put together for you and make sure it is all Linux compatible.

There are several others who will do more or less the same, eg, 
[http://www.novatech.co.uk/novatech/home.html](http://www.novatech.co.uk/novatech/home.html)
[http://www.cclonline.com/page/pc-finder/?id=67](http://www.cclonline.com/page/pc-finder/?id=67)

---

### Post by Anders_Makowicz on 2015-08-19
So it`s impossible to run Windows and Linux at the same time simply switching them?
I don`t want to install Linux on virtual machine as i will mainly use it and when i install Windows on VM inside Linux it wouldn`t play games especially like GTA 5.
So i have to restart my laptop every time i guess..


So i change my question:

What exact laptop would you choose if you`ll needed to buy 17inch Linux full compatible laptop that can handle GTA5?

I don`t have much knowledge about hardware and i don`t know which is best compatible that`s why i`m asking you to choose

Thanks

---

### Post by ajgreeny on 2015-08-20
Choose mainly Intel hardware, and as you will most likely need a dedicated graphics card, go with nvidia for that; it has better Linux drivers generally than AMD.

Apart from that I can not help much as I no longer have Windows other than an old XP in VirtualBox.
However, be aware that some manufacturers do not use a standard UEFI mode, but lock it down to boot only to Windows EFI boot files in the EFI reserved partition.  This can be overcome by renaming the Ubuntu EFI boot file in that partition but it shows how complicated using some makers' UEFI systems, eg HP, can be.

If you are installing Win 7 yourself you can, of course, overcome these potential problems by installing both OSs in legacy MBR (BIOS) mode, thereby not subjecting yourself to the potential problems of dual booting in UEFI mode.

---

### Post by Anders_Makowicz on 2015-08-21
[http://az-europe.eu/en/acer-aspire-v17-nitro-vn7-791g-509z-i5-4210h-3-50-ghz-8-gigabytes-1tb-8gb-ssd-17-3-hd-dvdrw-nv860m-p1118750/e](http://az-europe.eu/en/acer-aspire-v17-nitro-vn7-791g-509z-i5-4210h-3-50-ghz-8-gigabytes-1tb-8gb-ssd-17-3-hd-dvdrw-nv860m-p1118750/e)

What do you think of that?

It has Intel, can run GTA 5 and is 17inch, but is it a good choice?

---

### Post by ajgreeny on 2015-08-21
Looks reasonable, but the spec does not give enough detail of things like the wifi chip, only that it is 802.11ac, so it is difficult to know abut the driver situation for that chip.

I am also not the right person to talk about the different nvidia graphics as I've never used nvidia.  The optimus cards are now apparently working better when using bumblebee, which can switch between the nvidia and the less power hungry integrated chip that comes with the i5-Intel CPU but I do not speak from personal experience, only from what I've read.

If you go to a site such as the [PCSpecialists]("http://www.pcspecialist.co.uk/laptops/") that I mentioned before you may find a very similar spec machine for a lower cost, and I can vouch for the quality of their machines, having bought two.

---

