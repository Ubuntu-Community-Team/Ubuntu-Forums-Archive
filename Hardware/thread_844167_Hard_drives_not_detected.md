---
title: "Hard drives not detected"
date: 2008-06-29
forum: Hardware
---

### Post by b0ng0 on 2008-06-29
Hi, i'm not sure if this is the right forum so please move it if it isn't.

Basically, recently my computer crashed and now when I turn it on, in the BIOS screen (where it does the memory check, etc) it seems to either not detect or skip over detecting the HDDs (I have 2 of them).

The weird thing is, when I boot into Ubuntu using the live CD it can see the HDDs and I have also tried formatting and installing Ubuntu which seems to work without a hitch. However, upon rebooting from the live CD, again the BIOS does not seem to detect the HDDs or the Ubuntu install.

It goes to the motherboard boot agent (as no drives are detected) and just sits there until I put a bootable CD in.

I have a bad feeling the SATA controller on the motherboard is pooped but I'm really not sure and don't want to replace mobo, cpu and ram without being sure.

Thanks for any advice :confused:

---

### Post by Rocket2DMn on 2008-06-29
There should be an option in your BIOS to reset to defaults, this may help.  You may also consider setting the hard drives above the cdrom drive in the boot sequence.  You can also check witwh your computer's or motherboard's manufacturer to see if they have BIOS updates available.

---

### Post by b0ng0 on 2008-06-29
Thanks.

I have tried updating the BIOS and also resetting the CMOS but none of that seems to work. 

In the boot order in the BIOS the HDDs are just not an option, so it has to be the DVD drive.

Not sure what else I can do short of buying new gear... :(

---

### Post by Rocket2DMn on 2008-06-29
If it ever makes it to the GRUB screen, try some different kernel boot parameters, like one or more of these:
```
acpi=off noapic nolapic irqpoll irqfixup
```
I suggest starting with the first 3, then trying irqpoll only, then trying irqfixup only.  If these don't get you back on track, it may be time for new hardware.

If you aren't even getting to GRUB, then it does indeed seem like a BIOS, mobo, or controller failure.

---

### Post by elwin_windleaf on 2008-06-29
Some BIOS have the ability to set a HDD delay as one of the advanced options - try to poke around and see if you can delay disk detection for a couple of seconds. That might allow your SATA controller to initialize the drives in time for the BIOS to recognize them.

---

### Post by Odrodzona-Sarmacja on 2008-06-30
BIOS should have entire section dedicated for hd detection. Go there and try making BIOS to detect hds. Then set in BIOS for working with non plug&play computer and reconfigure itself to his new setup. I don't think there should be much trouble from plug&play OS after that.

---

