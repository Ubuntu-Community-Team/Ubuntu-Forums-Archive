---
title: "Dual Booting 2 Ubuntu Distributions"
date: 2009-10-01
forum: Installation &amp; Upgrades
---

### Post by IAmNotAUser on 2009-10-01
I'm planning to dual boot between 2 different Ubuntu based distributions. I'm planning to have the following separate partitions:

/ - Root for Distro1
/ - Root for Distro2
/home - Shared between the 2
/boot
SWAP

Is there a way to make the 2 distributions share the /boot partition. I recently did this as a test to figure out if the /home could be shared (which it can, with no problems using the same username in each), however, I set up the first distribution to use /boot, and didn't supply one to the second, which promptly forced a 2nd install of grub and menu.lst, with the other kernel present.

However, I cannot find a way to force the original menu.lst (which I have edited to contain my preferences already) to recognise distro2. I don't want to be booting from the menu.lst contained in Distro2 when I have created a dedicated /boot that won't be being used.

Would it simply be enough to just reinstall both distros, specifying the same /boot to each or is that dangerous?

---

### Post by louieb on 2009-10-02
> **IAmNotAUser said:**
> Would it simply be enough to just reinstall both distros, specifying the same /boot to each or is that dangerous?

You could - I did it once - will never ever do it again - kernel updates will cause breakage.  

last OS installed by default will control the MBR. 

most trouble free - keep /boot inside each installs / (root) and let each have it own copy of GRUB too.  I prefer to chainload my Linux distros from [a dedicated GRUB partition]("http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_Grub_Partition_")  

All this is subject to change when V9.10 rolls out and using GRUB2 begins. lol Downloading the beta now - going to setup laptop to dual boot Jaunty and Karmic beta tomorrow.

---

### Post by IAmNotAUser on 2009-10-02
Ok, excellent. So, what I've now established is that I'm getting /boot and a hypothetical "/grub" confused. That helps a lot, especially with the link you've provided. Many thanks for your help.

So, if I was to install Distro2 first, and then Distro1, and then follow that guide... the menu.lst I have copied will be in the correct order of Distro1, Distro1 (recovery), Memtest, Distro2, Distro2 (recovery) and I can remove the 2nd memtest.

Then I take it there is no way of auto-updating the kernel information inside the new grub menu.lst when kernel updates occur? Maybe I could mount the new partition at /boot/grub in the first distro and then I only have to update the second manually stealing the info from its menu.lst when it updates?

---

### Post by oldfred on 2009-10-02
The advantage of the dedicated Grub and chainbooting is you do not have to manually update anything except when you add a new distribution to the menu.

You can do what you want with one menu.lst in control and do the full edit or you can use it to chainboot to the second. The advantage is no manual updating, but you end up going thru two menus. I prefer the two menu approach. When you install the second distro you have to click advanced on the install to MBR and not install to the MBR but to the partition so you can chainboot and not overwrite the MBR from you first install.

I installed grub to every bootable partition so I actually can chainboot back if I click on the wrong one. My install of Karmic to the partition now gives me a warning that I should not have and it has to use blocklist, but it works.

---

### Post by carnagex420x on 2009-10-02
Agreed, Id keep the /boot inside your /root for each distro to avoid kernel issues and chainload from GRUB. Also you end up with less partitions to manage. I have never tried sharing a /home but I'd expect permission problems depending on the setup. But I also never did it... Also I'd install the second distro first then the other distro to the begining after, so GRUB is booting from the right active partition without having to reinstall GRUB or booting from the second partition.

---

