---
title: "Ubuntu 7.10 not detecting new ATI graphics card"
date: 2008-01-04
forum: Hardware &amp; Laptops
---

### Post by Miotch on 2008-01-04
So, for Christmas, I bought myself an ATI Radeon HD2600 Pro. Nothing too fancy, but it's a nice step up from my on-board video. I've never been able to get "Advanced Desktop Effects" to work with my on-board in 7.10.

Beryl was a thing of beauty, and I loved being able to use the Desktop cube with my on-board video. In 6.10, it worked flawlessly. I now use 7.10.

Hence the need for the spiffy new card. I downloaded the latest Linux Proprietary Driver from ATI (ati-driver-installer-8.443.1-x86.x86_64) before I installed the card. 

On reboot, X insists that I use my on-board video, and doesn't detect the card. I have Sysinfo, because I like knowing what's on my computer, but that shows no ATI card. 

On-Board card: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller

PCIe card: VisionTek ATI Radeon HD2600 PRO (512MB)

I was going to "sudo dpkg-reconfigure xserver-xorg", but if 7.10 doesn't recognize the card, I can't tell X where the card is (X says that on-board is at PCI:0:2:0.

The ATI installer hijacks my xorg.conf, and I've made a backup for the on-board at a resolution of 1024x768 (The highest this particular monitor can take, as I don't need more). I've had to cp it back every time I reboot.

Can anyone help me get this card in working order? I want to be able to run FoF and Compiz without issue, and I don't want to go back to Windows (MCE.... ugh.)

Even when the ati xorg.conf file is loaded, only the on-board video works, and at a reduced resolution.:(

Attached are the two conf files for inspection.

Am I doomed to return to Windows for my card?:confused:

---

### Post by jespdj on 2008-01-04
Maybe you should disable the onboard graphics in the BIOS settings of your computer. So when you switch on your computer, go to the BIOS setup and look if there's an option to disable the onboard graphics.

---

### Post by Miotch on 2008-01-04
> **jespdj said:**
> Maybe you should disable the onboard graphics in the BIOS settings of your computer. So when you switch on your computer, go to the BIOS setup and look if there's an option to disable the onboard graphics.

I didn't think of that. But, I couldn't use them side by side? I'll check that out and get back to you. If I don't come back right away, it means I've lost all ability to use a monitor on my computer.

---

### Post by Miotch on 2008-01-04
> **jespdj said:**
> Maybe you should disable the onboard graphics in the BIOS settings of your computer. So when you switch on your computer, go to the BIOS setup and look if there's an option to disable the onboard graphics.

Nope. No option to disable the onboard. I can disable onboard LAN, boot-on-LAN wakeup, 1394 and onboard audio, but not the onboard video. 

Motherboard is standard on Sony Vaio VGC-RB50.

---

### Post by Miotch on 2008-01-04
Bump. Problem still exists. I might have to return the card.

---

### Post by aoliver-taylor on 2008-01-14
I'm having a similar problem with an ATI HD2400XT on my computer at work.  At home I have an NVIDIA 8800GTS and that was detected no problem, the ATI one just isn't detected (and the system is Dell!), and attempts to install both the proprietary and open source drivers manually have resulted in me buggering up the system...

So there must be some issue with these cards, I think the key is in getting Ubuntu to recognise the card.

If you are still yet to return the card I would recommend an NVIDIA one as I had absolutely no problems there.

---

### Post by captain_conrad on 2008-04-18
yeah i also have a ATI radeon HD 2400 XT and my acer extensa 7620G laptop will not allow me to enable any desktop effects at all! how do u get ubuntu tp recognise your graphics card? i just want my desktop cube to work!!!!!
any help will be appreciated

---

