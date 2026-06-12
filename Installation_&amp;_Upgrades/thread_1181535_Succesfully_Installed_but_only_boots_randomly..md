---
title: "Succesfully Installed but only boots randomly."
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by Faceless79 on 2009-06-08
I just installed xubuntu 9.04 and it went fine, but now when I boot the progress bar starts to move then it hangs. I booted without 'quiet splash' and it seems to hang when it loads the touchpad.

There are times it boots normally however and when it does it runs perfectly. Ive tried every concievable grub option but to no avail. 

Please help, thank you.

---

### Post by Faceless79 on 2009-06-08
Oh and i dont know if this is significant but according to the partition manager in the installation i have ubuntu not xubuntu

---

### Post by ronparent on 2009-06-08
Can you load the live cd? If not can you load it with deselcting apic & lapic with the F6 option on the boot menu? The noapic,nolapic options can be added to the kernel line in /boot/grub/menu.lst. Although this may be a likely cause of freeze it's not the only one. Then you will have to keep looking for solutions.

---

### Post by ManiDhillon on 2009-06-08
Agree with RonParent, I had the same problem a while ago with Xubuntu 6.06 on my laptop. acpi=off and noacip both option worked for me! Because sometime some BIOS have problem with power managment and they tend to conflict with Xubuntu loading!

---

### Post by Faceless79 on 2009-06-09
Ive tried nearly all grub options and the live cd also boots randomly, i saw a bug report in launchpad that suggests it may be an issue with the kernel itself.

---

### Post by Habboblob on 2009-06-09
Why don't you just use Ubuntu? Rather than Xubuntu?

And with Ubuntu in the partition manager, you don't need to worry about that really.

---

### Post by Habboblob on 2009-06-09
I also agree with RonParent.
Why don't you try that method?

---

### Post by Habboblob on 2009-06-09
Are bumps against the forum rules also?

---

### Post by Faceless79 on 2009-06-09
Im not using ubuntu cause my pc is pentium 3 650mhz and 192 ram i cant run ubuntu but i can run xubuntu. And im reinstalling now

---

### Post by Faceless79 on 2009-06-09
It seems when i reinstall i get around 4 or 5 log ins before it quits booting, im trying to downgrade to 7.10 but if i cant boot i cand downgrade

---

### Post by ronparent on 2009-06-09
If you can run the live cd you can downgrade.

---

### Post by Faceless79 on 2009-06-10
I got it now. I went back to 8.04, i think ill wait till the next LTS to upgrade again

---

### Post by Fraser67 on 2009-06-17
I have exactly the same problem with 9.04 Xubuntu on an old Dell CPx, very odd and very frustrating. At the moment it fails alot more often than it boot.

---

### Post by Fraser67 on 2009-06-17
I think this is something to do with 2.6.28-11 kernel, as when I boot using an older kernel 2.6.27-7, Xubuntu 9.04 it boots ok and all seems to work.

---

