---
title: "No Sound Whatsoever...help..."
date: 2005-11-15
forum: General Help
---

### Post by Mosey on 2005-11-15
So I just switched from Windows XP to Ubuntu on my home PC. But, to my disdain, there is no sound whatsoever. None. I went to ubuntuguide.org and went thru the steps to configure my sound. Restarted...still nothing. I'm running a Pentium IV with onboard sound...no card. I don't know my exact system specs...I'm sure there is a command to tell me...but I don't know it.

---

### Post by Remmelas on 2005-11-15
lspci will list your hardware, should even list your onboard chipset
lsmod will list the loaded drivers, these are two useful tools

You might try
sudo alsaconf
and see if alsaconf can pick up on your sound card.  I was pretty happy with my install, it picked up all 3 of my sound devices, and autoconfigured them.

also, I doubt this is the problem since it works in windows, but make sure your onboard sound didn't get disabled in the bios somehow.

---

### Post by Kyral on 2005-11-15
Could you give the output from lspci?

---

### Post by Mosey on 2005-11-15
0000:00:00.0 Host bridge: Intel Corp. 915G/P/GV Processor to I/O Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 915G/P/GV PCI Express Root Port (rev 04)
0000:00:02.0 VGA compatible controller: Intel Corp. 82915G Express Chipset Family Graphics Controller (rev 04)
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1c.0 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
0000:00:1c.1 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
0000:00:1c.2 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
0000:00:1c.3 PCI bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.2 IDE interface: Intel Corp. 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:06:00.0 Ethernet controller: VIA Technologies, Inc. VT6105M [Rhine-III] (rev 96)
0000:06:08.0 Ethernet controller: Intel Corp.: Unknown device 1064 (rev 01)

Theres the output...
I'll try the alsa thing

---

### Post by Kyral on 2005-11-15
What is that? Its Intel but not the AC97...

I'm not familier with the equipment on newer Mobos

---

### Post by Remmelas on 2005-11-15
Googling found me this
[http://64.233.187.104/search?q=cache:fNHGhim2LGUJ:ubuntuforums.org/showthread.php%3Ft%3D16454+Intel+Corp.+82801FB/FBM/FR/FW/FRW+(ICH6+Family)+High+Definition+Audio+Controller&hl=en&client=firefox](http://64.233.187.104/search?q=cache:fNHGhim2LGUJ:ubuntuforums.org/showthread.php%3Ft%3D16454+Intel+Corp.+82801FB/FBM/FR/FW/FRW+(ICH6+Family)+High+Definition+Audio+Controller&hl=en&client=firefox)

I'm not sure what version of alsa Breezy shipped with, but looks like it needs to be at lest 1.08 to support that chip

---

### Post by Mosey on 2005-11-15
I believe it's a pentium four...

...thats what I was told when I bought it. It's a custom build. I'm really not sure.

---

### Post by Mosey on 2005-11-15
So how to I upgrade ALSA?

---

### Post by Kyral on 2005-11-15
It has nothing to do with the Processor. The Motherboard is definately Intel. What I need to research is the chipset....

 0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)

---

### Post by Mosey on 2005-11-15
Is there anyway to upgrade ALSA to the version that compatible with my board? I'd need a pretty newbie friendly walk-thru.

---

### Post by Remmelas on 2005-11-15
I'd hold off and let Kyral work his magic if he's researching the chipset, it's possible that Ubuntu's version is current, or that your chipset is just not supported.

---

### Post by Mosey on 2005-11-16
Is "Sorry, your chipset is simply not supported" really a possible outcome?!

Cripes

---

### Post by Mosey on 2005-11-16
So I read that thread with the user with a similar problem...A person suggested that his/her Linux Kernel was outdated and that she should make sure that she has the 2.6.12 Kernel, which has Intel High Definition Audio support...

But I have the 2.6.12 Kernel. So I should have on board audio.

This is quite frustrating. Switching distros is not an option now. I love Ubuntu and will do whatever it takes to get this working...Should I just put down the cash for a soundcard? If so, then what make/model is best for Ubuntu?

Thanks.

---

### Post by Mosey on 2005-11-16
Would getting a soundcard work at all...or is it really a problem with my motherboard?

---

### Post by Kyral on 2005-11-16
I have bad news. The 915G chipset is NOT currently supported (according to Intel, I haven't looked in the recent Kernel) with ALSA's AC'97 codec. Its basically too new. Until Intel releases drivers or until the kernel is patched (and the 2.6.12 isn't it seems, I haven't checked the 2.6.14.2 yet) you won't be able to get sound outta that thing.

I know the cheap (read around $30) CMI8730 PCI card works, because I run one.

This is a ghost of Linux's long battle with hardware manufactors to get support

---

### Post by Stormspace on 2005-11-16
My box uses a Soundblaster Live! and I had to configure my sound for digital output before it would work.

---

