---
title: "[SOLVED] Immediate reboot once GRUB has started to load"
date: 2008-09-20
forum: General Help
---

### Post by wieman01 on 2008-09-20
Hello, 

I am experiencing a strange issue here. I had to replace my mainboard's battery and consequently all the original BIOS settings got lost. Well, I tried my best picking the right settings, however, when I now try to run (K)Ubuntu the system immediately restarts after selection the corresponding entry in GRUB. Weird. 

I am on Kubuntu 8.04. Is there a way I can fix the install without having to reinstall? I would hate that.

---

### Post by defishguy on 2008-09-20
Try looking in your bios setup for your SATA drive settings.  You should see something like Compatibility Mode or AHCI.  If you see Compatibility Mode turn it on or if you get an option to disable AHCI try turning it off.

---

### Post by wieman01 on 2008-09-21
Thanks for your answer. I checked once again, but I did not see anything like AHCI or Compatibility Mode. All I get is:

Type, LBA/Large Mode, Block, PIO Mode, DMA Mode, SMART, 32Bit Data Transfer.

Guess that does not help.

---

### Post by unutbu on 2008-09-21
Perhaps just to give us more clues:

[list=1]
[*]Can you boot a LiveCD? This would show the current BIOS settings are at least okay for booting some OS.
[*]Can you boot using a SuperGRUB disk? ([http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/))
[*]What happens when you select recovery mode from the GRUB menu?
[*]What happens when you select memtest86+ from the GRUB menu?
[*]Perhaps try taking out the memory chips, letting it rest, clean some dust (if any) and then put it back in. See 
[http://www.dslreports.com/forum/r20910864-my-computer-keeps-rebooting-itself](http://www.dslreports.com/forum/r20910864-my-computer-keeps-rebooting-itself)
[*]Finally, perhaps systematically try one-by-one all reasonable options offered by the BIOS?
[/list]

---

### Post by wieman01 on 2008-09-21
Hello Unutbu, 

Nice to see you again.

1. Yes, I can boot using the Ubuntu Live CD.
2. I have not tried Super GRUB yet, but that's an option. I will give it a try.
3. Immediate reboot.
4. Immediate reboot.
5. I doubt it's the memory. But if Super GRUB fails on me, I will try that as well.
6. I have tried every possible option... to no avail.

I won't be able to try Super GRUB for a while, because I am moving... But I will report back as soon as I get my hands on my computer.

Thanks, guys!

---

### Post by wieman01 on 2008-09-21
Hello Unutbu, 

I just tried Super GRUB... Thank you very much, it worked right away. I was always wondering what Super GRUB might be useful for. :-)

I am writing this from my work station.

---

### Post by unutbu on 2008-09-21
Oh, that is excellent news! Glad to hear you are up and running again.

---

### Post by wieman01 on 2008-09-21
:-)

All I need to do now is fixing Grub, but that should be a piece of cake.

---

