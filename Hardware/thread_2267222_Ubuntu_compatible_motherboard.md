---
title: "Ubuntu compatible motherboard?"
date: 2015-02-28
forum: Hardware
---

### Post by newholm1 on 2015-02-28
Hi there. I find myself in the unenviable position of having to replace my motherboard (a 1156) and possibly my cpu, if I can't find a reasonably priced 1156 which runs Ubuntu. If I have to get a 1155 or 1150, I will. Can anyone suggest boards that work well with Ubuntu 14.04?

---

### Post by TheFu on 2015-02-28
Pretty much any of the most popular vendor boards should work provided you don't want overclock.

I just ordered a Pentium G3258 and Gigabyte MB combo for under $130-ish total. It is socket-1150. Parts haven't arrived. It is replacing a C2D E8400 and freeing up very lower-power another machine to be used as a router here.  4000 passmarks was almost 2x the AMD alternative, but the AMD had a much better onboard GPU.

Generally when I've decided to update a system, I do the following:
* set a budget
* know the purpose for the system - a desktop, server, virtual machine host, XBMC player, router, ... is graphics or I/O important? Does it need ECC RAM?
* pick a CPU performance range ... passmark is good enough for me - 4000 is what that pentium above does, so it isn't a screamer for a gaming desktop, but for any other typical home desktop use, it is fine. A 1st-gen Core i5 passmark is 3740, so this Pentium CPU isn't slow either. A modern Core i5 will be 2x faster for about 3x the cost. [http://www.cpubenchmark.net/cpu.php?cpu=Intel+Pentium+G3258+%40+3.20GHz](http://www.cpubenchmark.net/cpu.php?cpu=Intel+Pentium+G3258+%40+3.20GHz) shows a few comparisons. 
* list the desired motherboard features - PCIe ports, PCI ports, SATA speed/plugs, USB3, RAM amount/slots, video out type (hdmi/DVI/vga/display-port?), audio needs, SDHC, wifi,  if any.

then I go hunting - newegg, pc part picker, amazon.

After I pick a MB, then I web search for linux incompatibility ... I'll never use FakeRAID, so that is never a concern.  Pretty much any onboard GPU is fine for me too.

Based on the 1156 socket CPU you have today, if you don't need much different performance, then that G3258 CPU should be close for any Core i5 you have, slightly slower for any Core i7 you might have and use half (or more) the electric power.

---

### Post by kurt18947 on 2015-02-28
I decided to "tickle the dragon's tail" a bit on my last effort, plus budget was an issue. I bought an AMD processor/bundle from Microcenter (US chain). I wanted to see what did and didn't work with an AMD FM2 MoBo and processor. I bought this MoBo [http://www.microcenter.com/product/424749/FM2A88M-HD_Socket_FM2-FM2_mATX_AMD_Motherboard](http://www.microcenter.com/product/424749/FM2A88M-HD_Socket_FM2-FM2_mATX_AMD_Motherboard) and this processor [http://www.microcenter.com/single_product_results.aspx?sku=331785](http://www.microcenter.com/single_product_results.aspx?sku=331785). Buying them as a bundle saved $40. The MoBo seems to have some sort of hybrid UEFI BIOS. I was able to plug the hard drive from the old MoBo into the new machine and Xubutu worked as if nothing had changed. Windows had to be reinstalled as expected. I did switch the video driver from Nvidia to Nouveau and purged any PPAs before disconnecting the old MoBo. The drive maintained its 'MSDOS' file settings. A 3rd party boot manager I use on non-UEFI machines did not work, GRUB works fine.

I haven't found any incompatibilities that I can attribute to the hardware.  I also just-for-grins installed the Nvidia G210 PCIe video card to see if it would coexist with AMDs APU/GPU. It seems to have no issues. This machine is not used for graphically challenging tasks so it hasn't been stress tested. Going all-Intel is usually regarded as 'safer' but I have no complaints with the AMD setup so far.

---

### Post by TheFu on 2015-02-28
Nice AMD deal from Micro Center.  They do have the cheapest CPUs and being able to walk out with everything "today" is excellent.  However I think the Brits have it better with their PC World & Currys chain - how could that possibly be bad?!!! 2 of my favorite things, in 1 place!  (Yes, I know this isn't really a food place, but one can hope). ;)

I've moved HDDs between systems many times P4 --> Core i7; AMD K6-200 --> Core 2 Duo. Generally, the only thing that needs to be reset for new MB is the network udev rule(s) so eth0 will be used, not eth1. Those device numbers are based on the MAC and only when switching machines is removing the /etc/udev/rules.d/70-persistent-net.rules usually wanted. Just delete the old lines.

Of course, switching between BIOS and EFI boot will be an issue - efi needs a tiny partition at the beginning for both grub and/or Windows. For Windows-Vista or later, efi requires a GPT disk. Linux doesn't care - GPT works fine with BIOS boot.  GPT is a much more flexible disk partitioning method - highly recommended. No more extended/logical partitions and there are 2 copies of the partition table so corruption isn't the same "lose everything" problem as with MS-DOS/MBR partitioning.

Nice job Kurt!

---

