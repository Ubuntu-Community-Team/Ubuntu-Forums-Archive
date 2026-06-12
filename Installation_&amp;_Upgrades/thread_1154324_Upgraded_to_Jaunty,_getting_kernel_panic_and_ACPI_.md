---
title: "Upgraded to Jaunty, getting kernel panic and ACPI aborting"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by Omicron Machine on 2009-05-09
So I had Intrepid, and I do the usual upgrade-manager -d, everything *seems* to be going fine. I reboot. It boots up with a series off messages about xserver, and ends up in low graphics mode. Since the same thing happened when I went from Hardy to Intrepid, I knew what to do. GRUB was still looking up the Intrepid kernel, so I update menu.lst to use the new jaunty kernel and rebooted again. Now I'm getting these two messages, which are both very, very scary. After some research I found out what the second one means, but the first is still a mystery. When I try to start it up, it shows these two messages right away and there's no option to do anything else.

These are the messages in question:

> 0.020788 ACPI: Aborted because bad gzip magic numbers

3.216875 Kernel panic - not syncing: VFS: Unable to mount root FS on unknown block (0,0)


Did I break it? Please help!

---

### Post by Omicron Machine on 2009-05-09
Sorry to do this, but I haven't got the slightest clue. I can't find anything else addressing this and am kinda scared for my machine. Just bumping up to the first page. I promise to keep it to a minimum.

---

### Post by ronparent on 2009-05-09
Try booting with noapic & nolapic. You can use live cd to add these instructiond to /boot/grub/menu.lst (ie ...ro quiet splash noapic nolapic). Or temporarily from the grub manu by pressing e and adding to your boot instructions.

---

### Post by Omicron Machine on 2009-05-09
Thanks for responding!

I tried you suggestion just now, and the message changed to something still more ominous:
> 
0.020788 ACPI: Aborted because bad gzip magic numbers

0.028059 BIOS bug, local APCI #0 not detected!

0.028111 ...forcing use of dummy APIC emulation (tell your hw vendor)

49.400881 kerbnel panic - not syncing : VFS: Unable to mount root fs on unknown block (0,0)


I tried booting again without those options and it did return to the original message from my first post. Can you think of anything else? I'm whipping up a Jaunty liveCD as I type this, and have a Knoppix CD, a Super Grub Disk and a GParted disk on hand, an alternate machine I'm on right now, and a decent stack of DVD-r's.

---

### Post by ronparent on 2009-05-09
I routinely get the 1st three messages on one of my computers with 9.04 installed and running with noapic/nolapic. I had no prior success installing 8.10 on it beccause of consistent kernel panic problems with it with any remedy I could find. In my case telling the vendor (motherboard) would be futile because they no longer market in the US and haven't upgraded the bios in probably five years. The kernel panic may not be related to the apci problems?! None of the advice I've studied on fixes for kernel panic have made much sense or been useful to me yet. So, I wish you luck. I'm still looking for rational answers.

---

### Post by Omicron Machine on 2009-05-09
I'm off to see if the live CD has the same or similar problems, and if not, maybe back up my stuff and install fresh. I remain hopefull as previous releases had no real problems.

---

### Post by macabro22 on 2009-05-18
> **Omicron Machine said:**
> I'm off to see if the live CD has the same or similar problems, and if not, maybe back up my stuff and install fresh. I remain hopefull as previous releases had no real problems.

Don't forget to tell us if that solved your problem please

---

### Post by guzjd on 2009-05-21
To resolve the ACPI issue shouldn't he be using acpi=off not APIC or nolapic. These are different options. I am having similar issue with Jaunty but will post my fix as soon as I find the cause. I am going to try reinstalling grub, as this has worked for some users in the past.

---

### Post by Omicron Machine on 2009-05-21
It did! Everything's wrapped up neatly (in that regard, anyways) and I've learned my lesson about trying to "upgrade-manager -d" instead of install fresh like sane people. ;)

Note: The liveCd and reinstalling Ubuntu was the fix to which I was referring, though I note that doing that would have had the side effect of also changing that ACPI option (I now remember changing it when I had Intrepid to fix an unrelated issue at startup).

---

### Post by guzjd on 2009-05-21
I was really surprised that that took care of both issues. I am having issues with my grub but doesn't appear to be related to this thread. I'll start a new one.

---

### Post by ravana_ravana on 2009-08-02
Are you using some keyboard settings other than default?
If yes disable it!

I just added some language support and keyboard layout.
I applied one of the layout systemwide

Next time I boot, I got similar messages.
Tried everything ( noapic , nolapic , acpi=off, irqpoll ), all failed.
Finally i booted up one of my earlier kernel version

And removed all layout of keyboard.
It worked.
I got back to default kernel

---

