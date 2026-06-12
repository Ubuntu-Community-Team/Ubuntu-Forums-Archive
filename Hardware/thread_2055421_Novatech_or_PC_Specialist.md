---
title: "Novatech or PC Specialist?"
date: 2012-09-09
forum: Hardware
---

### Post by Deeday on 2012-09-09
Which supplier would you recommend for a new, OS-free laptop that would run Ubuntu with the highest possible degree of compatibility?

By browsing the forum it sounds like Novatech laptops have problems with wireless card drivers; I see that there is a fix, but it requires the configuration files to be recompiled each time the kernel is updated, which is a bit of a hassle.

On the other hand, someone recommended Intel wireless adapters as the most compatible ones, so maybe PC Specialist is preferable, if it offers the Intel cards as an available option.

Any suggestion welcome! (also about other suppliers, as long as they don't force you to buy Windows pre-installed).

Cheers.

---

### Post by einonm on 2012-09-11
I think wireless card issues would be the same across the board with most generic PC vendors. This is mainly because the laptops sold would have the latest wifi cards / chips and the kernel drivers would take a while to catch up. If there is an issue like this, I don't believe it would be forever - just until the kernel changes required to support the new cards make it to your distro released kernel.

I'm more than happy with the three Novatech laptops I've bought in the past - only one of them had an unsupported wifi card for a short while, but I used Fedora and their akmod package to automatically update the driver for a while (Does Ubuntu have a similar thing?). 

Saying that. It's not difficult, or expensive, to use a USB wireless dongle or even replace the internal laptop PCI card for a while...

---

### Post by Deeday on 2013-02-16
So, here is how it went: in the end I got a laptop from PC Specialist (see specs below) and am pretty happy with it - now.

However, it wasn't easy at the beginning; I tried to install Ubuntu 12.10 and it was a **disaster**: neither the Live CD nor the Install process would go past a blank screen.
Setting acpi=off allowed it to boot, but with all fans blowing away like crazy. I am far from an IT novice but it took me a fair while to figure out that the problem might have been lying in the nvidia graphics card and related drivers.
I really went this close to returning the laptop and ask for a refund.

Then I stumbled on some interesting articles, like [this one]("http://www.dedoimedo.com/computers/ubuntu-quetzal-high-end.html") and it was and eye-opener.

To cut a long story short, Ubuntu 12.04 runs like bliss (long live LTS!): wireless, webcam, touchpad, everything worked straight out of the box. One less headache for myself (and PC Specialist...)

P.S. In my naivety, I was hoping to set up an Ubuntu/Windows XP dual boot, but the manufacturer doesn't offer any driver for XP, so no audio, no networking etc.
So in the end I guess I'll still have to buy a copy of Windows 7, if I want a workable Windows system.

=================================================================

[LIST]
[*]PC Vortex Series: CLEVO P151EMX, 15.6" LED Widescreen (1920x1080)
[*]Intel CoreTMi5 Dual Core Mobile i5-3320M (2.60GHz) 3MB
[*]8GB RAM Kingston HYPER-X GENESIS 1600MHz SODIMM DDR3
[*]nVIDIA GeForce GTX 670MX - 3.0GB DDR5 Video RAM
[*]Hard Disk 250GB WD SCORPIO WD2500BEKT, SATA 3 Gb/s, 16MB cache (7200 rpm)
[/LIST]

---

### Post by Deeday on 2013-02-17
...I spoke slightly too early: the SD card reader and subwoofer do *not* work out-of-the-box: for the SD card reader I found the solution [here]("https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/971876"); the subwoofer is still work in progress.

---

