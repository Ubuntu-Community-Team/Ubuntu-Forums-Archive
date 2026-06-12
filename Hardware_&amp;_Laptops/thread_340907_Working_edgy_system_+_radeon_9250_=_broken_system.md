---
title: "Working edgy system + radeon 9250 = broken system"
date: 2007-01-17
forum: Hardware &amp; Laptops
---

### Post by one_stinky_bum on 2007-01-17
Hi folks, I had a working edgy (latest updates and all) install on my dell dimension 2350 and I went ahead and installed a PCI ATI radeon card I got today. The card works just fine in windows, but on linux I get the following error message:

[COLOR="DarkRed"][B]EIP: [<c0110579>] smp_apic_timer_interrupt +0x9/0x30 SS: ESP 0068: efec1ee0
kernel panic - not syncing: attempted to kill init![/B][/COLOR]

When I remove the ati pci graphics card, everything boots fine. I tried to re-install edgy, but I got the same kernel panic message, with an additional line saying:

[COLOR="DarkRed"]**<1>BUG: unable to handle kernel paging request at virtual address ffffd320**[/COLOR]

Any help? I've spent some good time searching the fora/google and after 4 hours I still have not made any progress.

Thanks.

---

### Post by Fitzy_oz on 2007-01-17
> **one_stinky_bum said:**
> Hi folks, I had a working edgy (latest updates and all) install on my dell dimension 2350 and I went ahead and installed a PCI ATI radeon card I got today. The card works just fine in windows, but on linux I get the following error message:

[COLOR="DarkRed"][B]EIP: [<c0110579>] smp_apic_timer_interrupt +0x9/0x30 SS: ESP 0068: efec1ee0
kernel panic - not syncing: attempted to kill init![/B][/COLOR]

When I remove the ati pci graphics card, everything boots fine. I tried to re-install edgy, but I got the same kernel panic message, with an additional line saying:

[COLOR="DarkRed"]**<1>BUG: unable to handle kernel paging request at virtual address ffffd320**[/COLOR]

Any help? I've spent some good time searching the fora/google and after 4 hours I still have not made any progress.

Thanks.

Couple of quick checks - Check in your bios and see there is option that says init display first: PCIe or AGP or onoard or something similar to that.  Set it accordingly.  Check the aperature also and set it to double what your video card memory is.  

Try pressing escape at the grub prompt and boting into failsafe mode.  


Try these and let me know how you go.

---

### Post by one_stinky_bum on 2007-01-18
Thanks for the quick response. The card is the PCI version and the BIOS only has the options Video: a) onboard b) auto. I left it at auto and I can get video going through the Ati card (instead of the onboard intel) even when both have monitors attached to them. (so I'm happy with that). I have tried safemode and also adding the "noapic" term to the boot options but those actions didn't solve the problem. (same kind of error).

Am I missing something simple?

---

### Post by Fitzy_oz on 2007-01-18
> **one_stinky_bum said:**
> Thanks for the quick response. The card is the PCI version and the BIOS only has the options Video: a) onboard b) auto. I left it at auto and I can get video going through the Ati card (instead of the onboard intel) even when both have monitors attached to them. (so I'm happy with that). I have tried safemode and also adding the "noapic" term to the boot options but those actions didn't solve the problem. (same kind of error).

Am I missing something simple?

Try disabling the agpgart module as your using a PCIe video card. 

sudo gedit /etc/modules

DISABLED MODULES="agpgart", "nvagpgart"

---

### Post by one_stinky_bum on 2007-01-18
After implementing the changes in /etc/modules, this is the error message I get:

[COLOR="DarkRed"]**EIP: [<c0110579>] smp_apic_timer_interrupt +0x9/0x30 SS: ESP 0068: ec139de8**[/COLOR]

Does that suggest anything?

---

### Post by one_stinky_bum on 2007-01-21
Finally figured it out. I won't even attempt counting how many hours I've spent on this. The trick is to add the following to the "kernel" line in the grub boot options:

```
noapic nolapic apic=off
```

To do this, hit "e" when the grub menu comes in, select the line that says "kernel", hit "e" again and then type it right in. Hit escape and then type "b".

Hope this helps.

---

### Post by dorgan on 2007-02-05
Dude you dont know how long i've been searching for this solution.  I tried for two days to get any distro to work on my dimension 2350 with my PCI ATI card, and have had no luck even getting it to install when not using the onboard video, so now I will go home tonight and try these options when booting the install.

Please let me know if you have found anything else.

---

### Post by one_stinky_bum on 2007-02-05
I returned the radeon card and I'm now rocking an AMD X2 box. I totally wasted my time trying to get the radeon to work. It eventually did, but beryl wasn't the greatest, so I just got a new computer.

---

### Post by dorgan on 2007-02-05
hmm seems it doesnt like apic=off option, and just the noapic nolapic option still gives me the same error.

---

### Post by tny5357 on 2007-02-09
im having the same trouble except i have a pny geforce fx 5200, i get this error before the setup even loads up, im  new to linux, so can someone enlighten me on what the grub menu is and where to put the above commands, "noapic nolapic apic=off", thank you

---

### Post by dorgan on 2007-02-09
If you are using a dimension 2350 then, i think we are out of luck seems the latest kernel doesnt like that board when it has a PCI card plugged into it.

---

### Post by one_stinky_bum on 2007-02-10
the grub menu is the list that pops up when you turn on your computer and before you get into Ubuntu. It shows the various operating system options to boot. If you have windows installed, you'll see it listed along with Ubuntu, safe/recovery mode Ubuntu and memtest (a memory testing program). When the menu shows up, select Ubuntu and press the "e" key. Then go to the line that starts with "kernel", press "e" again, go to the end of the line and then add the lines "noapic nolapic apic=off" without the quotes. When done, hit the "b" key. If the changes worked and you want to make it permanent, edit the following file: /boot/grub/menu.lst , adding the noapic stuff at the end of the appropriate line that starts with "kernel"

Hope this helps. I switched to nVidia.

---

