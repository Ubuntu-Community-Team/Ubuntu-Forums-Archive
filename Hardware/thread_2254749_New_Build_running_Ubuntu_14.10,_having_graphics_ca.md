---
title: "New Build running Ubuntu 14.10, having graphics card issues"
date: 2014-11-29
forum: Hardware
---

### Post by letsrockthisplace on 2014-11-29
Hello everyone,

First off, my apologies if I'm posting in the incorrect forum or if there's another thread that can solve my issues that I missed. I did some searching and couldn't find the same problem I'm experiencing. I'm also essentially brand new to Ubuntu (other than booting it from a USB drive a couple times to mess around, I've never used it).

So, I went out and took advantage of some Black Friday deals to purchase the components to get my old desktop up and running again. The new components I purchased:

[LIST]
[*]Intel Core i5 4690K CPU
[*]Gigabyte Z97X-Gaming 7 motherboard
[*]WD Blue 1TB 7200rpm Sata3 HDD
[*]Kingston HyperX Fury 8GB (2x 4GB) DDR3-1600 RAM
[/LIST]

In addition, I'm reusing some old components from when my desktop was last running:
[LIST]
[*]Antec P182 case
[*]OCZ ModXStream-Pro 700W Modular PSU
[*]Some DVD burner (it's been a long time, shouldn't matter for my issue)
[*]Nvidia GeForce GTX 550 Ti Graphics Card (purchased it quite a while ago, I used it in my desktop when it last ran in August 2012, don't remember what brand)
[/LIST]

So, I've gone ahead and installed Ubuntu 14.10 onto the hard drive, and now I'm running into graphics card issues. For some reason, when I try and use the GTX 550 Ti graphics card, I get nothing displayed on the monitor. I dont even see the Gigabyte logo on the post screen. It just stays black and the monitor displays "No Signal". This might not even be a Ubuntu issue, but frankly I'm not 100% sure either way and I'm hoping the Ubuntu community can provide some insight for me. So far, the only way I've gotten any display on the monitor is with the integrated graphics. I've tried multiple configurations and setups with no luck:
[LIST]
[*]GPU in first PCI Express slot, checked that it's seated properly, 6 pin power cable is connected
[*]GPU in second PCI Express slot, again checked power connection and that it's seated properly
[*]Tried both DVI slots on the graphics card
[*]Disabled integrated graphics in BIOS
[*]Tried a known good Radeon HD5450 from our other older desktop (no power connector required)
[*]Tried installing the latest nvidia drivers
[*]Checked in the BIOS that the initial display output corresponded to the correct slot the GPU was installed in, when in both the first slot and second slot
[*]Tried both each BIOS as the primary, and also tried single BIOS mode with each BIOS
[/LIST]

And so far I think that covers everything I've tried. We had the issue when first building the computer last night and thought it was the board, so we exchanged the motherboard for a new (identical) one. We've had the same issue.

I did discover the lspci command and ran that, and the only VGA controller shown was the integrated graphics card. My friend and I are both completely out of ideas, aside from trying his GTX 660 Ti from his computer. Sorry for the long wall of text, I just wanted to try and be as thorough as possible.

Thanks,
Jonathan

---

### Post by oldfred on 2014-11-29
Aother Gigabyte motherboard and nVidia card. 
[http://ubuntuforums.org/showthread.php?t=2254738](http://ubuntuforums.org/showthread.php?t=2254738)

Your nVidia should not require the very newest driver and the one in the Ubuntu repository should work.

My older nVidia cards always needed nomodeset, until I installed nVidia driver from repository. But current install and my somewhat newer 620GT works with the open source driver with only minor tearing. And that tear only seems to appear, so far in replies like this:

Check UEFI/BIOS for iommu settings:
 turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)

Are you installing in BIOS or UEFI boot mode?

---

### Post by letsrockthisplace on 2014-11-29
Thanks for your response.

With regard to IOMMU, if my Google-fu has worked, that should be the VT-d setting in the BIOS which is already enabled.

As for UEFI vs BIOS boot mode, my friend that helped informed me it was UEFI mode.

---

### Post by oldfred on 2014-11-29
Are you booting with nVidia or using the internal Intel chip? 
Yours is not switchable except by moving connection on back of computer.

If you only have Ubuntu installed, you have to press escape key at UEFI screen. If in BIOS mode, you press & hold shift key from BIOS until grub menu appears.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by letsrockthisplace on 2014-11-29
When I move the DVI connector from the integrated graphics to the nvidia card, I only get a black screen. Not even a UEFI screen, leading me to believe it might not necessarily be a Ubuntu issue. I'm not able to get to the grub menu at all. Even when I disable the integrated graphics, I still get nothing from the nvidia card.

Is there any possibility it's the motherboard itself yet again even though we already exchanged it?

---

### Post by oldfred on 2014-11-29
Several years ago when they changed things around and I needed nomodeset with my nVidia, I only had a black screen, but I was installing from a flash drive and saw it was still loading.
Since then when every I forget the nomodeset I still get black screen.
A few laptops get  black screens from screen brightness settings.

I added nomodeset to all my boot & live boots before I even start now.

If you press escape key during BIOS screen (perhaps several times) do you get grub menu? If so add nomodeset.
If not you can try pressing down arrow once, right after UEFI/BIOS as grub menu remembers key press as soon as it starts and before you even see a menu. The recovery mode is the second entry and has nomodeset built in.

---

### Post by letsrockthisplace on 2014-12-01
I'll pass along the information to my friend and have him give it a shot. I actually just returned to school in NY for the final 2 weeks of the semester, but my desktop is at home in CO. I left it with a more computer-savvy friend than myself to work on while I'm finishing up the semester. I'll pass along the link and have him let me know how it goes.

Many thanks for all your assistance oldfred :)

---

