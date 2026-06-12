---
title: "ASUS F3Sv Dual Boot problem"
date: 2008-02-18
forum: Hardware &amp; Laptops
---

### Post by pyrocloud on 2008-02-18
I have recently started to dual boot my F3Sv-A1 laptop, and everything is going well to a point.

After resizing the partitions and reinstalling Vista and Kubuntu Gutsy, GRUB was able to automatically edit menu.lst to include the vista install, which is nice.

However after rebooting a Vista session to enter a Linux session, I find that GRUB is stuck in a boot loop. GRUB shows stage 1.5 for just under a second and then reboots = infinity.

So I boot to the live CD, and in a terminal as root I run GRUB, set the root with " root (hd0,6) ", as Linux is on the 7th partition, then fix it with " setup (hd0) " then reboot. After that everything goes well, I get the normal GRUB loader menu. Both OSs boot fine.

However I find that every time I reboot Vista while the laptop is running on battery the same problem happens again. I know how to fix it, but it's a pain in the A** to do this over and over just to dual boot. It happens so often that I have made a GRUB script that fixes the problem on boot to the live CD, but it takes 10 minutes to boot and run the script. Plus I'm worried about rewriting the MBR so many times.

I suspect it has something to do with the way vista handles the MBR. It happening only on battery power suggests that it has something to do with the ASUS power extreme software. I don't want to remove the power management software as it does save on power consumption while using the battery, as without it my battery only lasts for about an hour.

Can anyone offer me any insights or possible solutions?

---

