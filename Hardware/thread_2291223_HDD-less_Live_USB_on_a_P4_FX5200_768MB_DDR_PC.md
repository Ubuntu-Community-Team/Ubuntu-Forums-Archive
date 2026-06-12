---
title: "HDD-less Live USB on a P4 FX5200 768MB DDR PC"
date: 2015-08-18
forum: Hardware
---

### Post by 180-pedro on 2015-08-18
Heya.
So, when I was formatting a friend's old PC, it reminded me of my old machine and got curious if I could get it to work. So I connected everything, and put everything in place except for the HDD, which went bad long ago and finding an IDE drive now won't be neither practical nor cheap (especially where I live, where PC components are worth their weight in gold and I'm broke because of the college). Back when it was my main PC, I couldn't think of a way to make it work without an HDD, but now that I learned about Live USBs  and used them on my main PC (AMD Phenom II X4/Gigabyte 970A-D3P (I think)/2GB RAM DDR3 OCZ 1333 MHz (the second 2GB stick went bad)/XFX Radeon HD5850 on UEFI ElementaryOS Freya + Windows 10 DualBoot), I figured I could use a dedicated USB drive as a replacement of sorts.
The problem is, I tested the Live USB on my friend's PC (an Athlon 64 with 1GB DDR400 and NVIDIA FX5500) and it ran just fine (SliTaz, elementary OS had the same problem, however). However, when I ran it on mine, it didn't. It boots, shows the language selection and I can choose any options (like test RAM, etc) without a problem, but if I choose "Try Lubuntu without installing" or "Install Lubuntu", it freezes right there. No error message, nothing. I tried it with multiple distros (Peppermint 6, Lubuntu, SliTaz and elementary OS) and none of them worked, all had the same problem.

Here's the hardware:
ASUS P4S800-MX
Intel Pentium 4 1.8GHz Prescott
2 Sticks of DDR RAM (the slowest is 200MHz, if I'm not mistaken): 512MB and 256MB. 768MB in total.
NVIDIA GeForce FX 5200 128MB
Creative SoundBlaster Audigy SE
and a PCI wireless internet adapter I had laying around
450W Fan Hung Power Supply

Temperatures are normal and everything is properly seated and clean. I tried removing each of the RAM stick, GPU (without it, it doesn't even POST. The onboard GPU may have gone bad, gonna test it just in case), sound card and wireless adapter but the result was the same every time.

---

### Post by weatherman2 on 2015-08-18
Are you using 32 bit or 64 bit Linux distros?

Is it a 1.8GHZ Pentium 4?  Or is it a Prescott?  Prescott is 64 bit but didn't operate at frequencies that low:

[https://en.wikipedia.org/wiki/List_of_Intel_Pentium_4_microprocessors#Prescott_.2890.C2.A0nm.29](https://en.wikipedia.org/wiki/List_of_Intel_Pentium_4_microprocessors#Prescott_.2890.C2.A0nm.29)

If it's really a 1.8GHZ Pentium 4, it's probably a Northwood - which is only 32 bit.  In other words, if you installed 64 bit Ubuntu (?), it won't work on this CPU.  If so, try the 32 bit version.

(Where I live, PATA/IDE drives are easy to find, cheap.  I've given a bunch of them away for recycling.)

---

### Post by 180-pedro on 2015-08-18
The motherboard supports Prescott CPUs, but I was not sure if mine was of that family, my mistake. It has been a while since I last checked its hardware, so my memory is a bit fuzzy. It's a Pentium 4 1.8GHz, of that am I quite sure. And I used 32 bit distros, made the Live USB with Rufus on MBR mode.
About the drivers, last time I checked a PATA 120~160GB drive was about US$100~150. I'll check it again (it has been a while), but I don't think it got any cheaper now that it's old technology. I can't even buy RAM for my main PC (which I desperatedly need), just to exemplify how poor I am right now lol.

---

### Post by weatherman2 on 2015-08-18
Well, around here you can get PATA drives of that size used for about $5 to $10 USD if no one will give you one.  I probably have a few at least that big still laying around.  If you live in any sort of town with a Craigslist, check the "free" section - people are throwing away computers that old.  I know I've dumped/recycled a couple of that vintage or even faster.  Nothing with less than a dual core CPU is worth anything anymore.

---

### Post by weatherman2 on 2015-08-18
As for your problem: hard for me to debug from your description.  Have you tried running Memtest to make sure your RAM is good?  Try booting a distro that isn't stuck in a Gui mode that may show you some debugging text as you boot.  FYI, I've seen more than a few cases where after you hit Enter to start the "Try Ubuntu" path it will sit there for several seconds and do nothing for a while.

And I've also seen cases where one of those old P4-class motherboards doesn't boot from USB reliably or very well.  Sorry, I've played with lots of old systems of that vintage, and they can be tricky.

---

### Post by oldfred on 2015-08-18
With nVidia I always needed nomodeset. To boot installer and boot from grub until I installed proprietary driver. Your is old so one of the older legacy drivers will be the correct on. Check to make sure.

 Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
      
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132

[/URL]
 Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

[URL="http://ubuntuforums.org/showthread.php?t=1613132"]
[/URL]

---

### Post by 180-pedro on 2015-08-18
Oh, I forgot to mention. I also tried to boot with **nomodeset, ****acpi=off, ****Noapic and nolapic,** No dice.
Will try the tip to boot on text mode, though. Any specific distros that are useful for debugging or any with text mode will do? Meanwhile, I'll keep trying and I'll check the RAM while I'm at it (never hurts to check, but I doubt that's the case. If it is, then BOTH of them are bad and I'm screwed).
About the Craiglist, I just checked. Couldn't find anything related to PC components (but there are some offers that are really hilarious), but I'll keep an eye out for people trying to sell used parts.

---

### Post by sudodus on 2015-08-19
When you use the boot option **text**, any Ubuntu flavour boots into text mode (does not start graphics mode). I think the problem is the graphics (the old nvidia card).

Lubuntu has the lightest foot-print of the Ubuntu flavours. It should work with 768 MB RAM and Pentium 4. Try the 32-bit version 14.04.2 LTS, **lubuntu-14.04.2-desktop-i386.iso**

Knoppix is good at recogizing hardware, so it is also worth testing. Try also the ultra-light distros Wary Puppy, TahrPup and Tiny Core. It is also worth trying some community re-spin based on Ubuntu 12.04 LTS, for example Bento, Bodhi, LXLE or ToriOS (beta).

See these link and links from it for more tips:

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")

---

### Post by 180-pedro on 2015-08-20
Thanks, I'll try that.
Yesterday I tried booting SliTaz. It extracts all the files, then says "Decompressing Linux" and gets stuck there. Really weird. I'll try the distro you recommended today.

---

