---
title: "Hardware advice please..."
date: 2011-03-16
forum: Hardware
---

### Post by Varsel on 2011-03-16
I'm preparing to get PC via custom-build shop. It will have three HDDs (one for XP Pro, one for Ubuntu 9.04, and one for PC-BSD 8. I'm trying to design hardware for optimal benefit of each OS. I'm planning on either Phenom II (x2,x3, or x4), or Athlon II (x2,x3, or x4) CPU. Hopefully Gigabyte Dual-BIOS motherboard. I detest Intel and Geforce/NVIDIA....wish to avoid their components in this build, if at all possible. Advice welcomed!

---

### Post by IcarusR on 2011-03-17
> I detest Intel and Geforce/NVIDIA....wish to avoid their components in this build, if at all possible

Why ?

They are both well supported under linux. A lot of folk on here would recommend them both for graphics ahead of ATI. ATI drivers are not as good as the other two & are more problematic.

Personally I would go with Nvidia chipset & graphics.

I would probably use just on hdd & partition it 3 ways. More drives = more heat & power usage.

I'd also suggest you use Ubuntu 10.04 or 10.10 rather than 9.10. Newer & potentially more upto date & less bugs & are both still supported.

Just my thoughts & will probably get shot down by others !

---

### Post by gradinaruvasile on 2011-03-17
You should not detest them, they are not worse than AMD/ATI - it is just business (and they make quite good hardware too). I am an AMD fan BTW, but for now i favor nvidia cards because of their driver support which is the best around (AMD closes the gap slowly though).

On topic - 
CPU - If you have money, get a Phenom II, they are more powerful than the Athlon IIs. How many cores, that is your call/budget. If you game hard or use other demanding applications, go for 3-4. If not, 2 should be suffice. 

Some newer mobos have a feature called "core unlocker" - this lets you to use a 3 core AMD cpus 4-th core. I tried it once, it worked quite ok, but if i watched any movie, i got weird colors and artifacts (and if i reverted this setting, all was ok). So, the 4th core might not work well, do not count on that.

Anyway consider the fact that dual-core Athlon IIs are actually faster core/core than the tri/quad-core Athlon IIs because of their larger level 2 cache (1 MB per core vs 512 KB per core). The 2 low end dual cores (210 and 220) also have only 512 KB/core so if you decide to buy Athlon II, but at least the 240 or better.

Mobo - Get an Ati chipset with AT LEAST ATI 4200 GPU (this has hardware decoding). The chipset is AMD 785G/SB710 - these chipsets use DDR3 memory which is faster than the DDR2 and have HT3.
I personally favor Asus as a brand better - they dont have the amount of unneeded features and are more stable than the Gigabytes in my experience.

I have an Asus M3N78-VM mobo which has nvidia onboard graphics (nvidia 8200 with hardware decoding) and AMD cpu - it works really really well, way better stability-wise than an Ati 3000 in a somewhat similar build computer i tried.
But more recently i did not see this 78 nvidia chipset available, it seems it fell out of favor...

HDD - i have 2 HDDs now in my comp, there is really no problem having more than 1. I put my bigger wine games (LOTRO, Medieval II, Rome)  and my VirtualBox "HDDs" to the non-system disk and i have almost no impact on the systems speed (except CPU usage hit) if i run them.

SATA HDDs are fully hot-pluggable (EXCEPT THE SYSTEM DRIVE!!!). Make sure there are no processes that use them (no write jobs on them) and you can plug them out/in.

One thing to make sure - that the boot loader (GRUB2) is ACTUALLY on the system drive - i had this issue when i installed by mistake the grub loader on a HDD and i had the system on the another - i did not notice it until i plugged out one of the drives...

---

### Post by Varsel on 2011-04-09
> **IcarusR said:**
> Why ?
 
They are both well supported under linux. A lot of folk on here would recommend them both for graphics ahead of ATI. ATI drivers are not as good as the other two & are more problematic.
 
Personally I would go with Nvidia chipset & graphics.
 
I would probably use just on hdd & partition it 3 ways. More drives = more heat & power usage.
 
I'd also suggest you use Ubuntu 10.04 or 10.10 rather than 9.10. Newer & potentially more upto date & less bugs & are both still supported.
 
Just my thoughts & will probably get shot down by others !
 
 
Why is a big can of worms I'd rather not open (already got sucked into big DRM/HDCP debate once before, and not into a replay). Lets just say I don't like their business practices/agenda, and rather not deal with either if I can avoid it. Yes, I'm aware they are ahead of AMD/ATI....question is are any AMD/ATI products acceptable?
 
Already looked into partitioning stuff. As I understand it, if you put XP Pro & Ubuntu on one HDD via partition, and XP Pro goes into catastropic failure, it takes Ubuntu down with it. True?
 
Already have instructional books on Ubuntu 9.04. Not into constant updates. One reason to Kick Billy Gates to the curb!

---

### Post by Varsel on 2011-04-09
> **gradinaruvasile said:**
> You should not detest them, they are not worse than AMD/ATI - it is just business (and they make quite good hardware too). I am an AMD fan BTW, but for now i favor nvidia cards because of their driver support which is the best around (AMD closes the gap slowly though).
 
On topic - 
CPU - If you have money, get a Phenom II, they are more powerful than the Athlon IIs. How many cores, that is your call/budget. If you game hard or use other demanding applications, go for 3-4. If not, 2 should be suffice. 
 
Some newer mobos have a feature called "core unlocker" - this lets you to use a 3 core AMD cpus 4-th core. I tried it once, it worked quite ok, but if i watched any movie, i got weird colors and artifacts (and if i reverted this setting, all was ok). So, the 4th core might not work well, do not count on that.
 
Anyway consider the fact that dual-core Athlon IIs are actually faster core/core than the tri/quad-core Athlon IIs because of their larger level 2 cache (1 MB per core vs 512 KB per core). The 2 low end dual cores (210 and 220) also have only 512 KB/core so if you decide to buy Athlon II, but at least the 240 or better.
 
Mobo - Get an Ati chipset with AT LEAST ATI 4200 GPU (this has hardware decoding). The chipset is AMD 785G/SB710 - these chipsets use DDR3 memory which is faster than the DDR2 and have HT3.
I personally favor Asus as a brand better - they dont have the amount of unneeded features and are more stable than the Gigabytes in my experience.
 
I have an Asus M3N78-VM mobo which has nvidia onboard graphics (nvidia 8200 with hardware decoding) and AMD cpu - it works really really well, way better stability-wise than an Ati 3000 in a somewhat similar build computer i tried.
But more recently i did not see this 78 nvidia chipset available, it seems it fell out of favor...
 
HDD - i have 2 HDDs now in my comp, there is really no problem having more than 1. I put my bigger wine games (LOTRO, Medieval II, Rome) and my VirtualBox "HDDs" to the non-system disk and i have almost no impact on the systems speed (except CPU usage hit) if i run them.
 
SATA HDDs are fully hot-pluggable (EXCEPT THE SYSTEM DRIVE!!!). Make sure there are no processes that use them (no write jobs on them) and you can plug them out/in.
 
One thing to make sure - that the boot loader (GRUB2) is ACTUALLY on the system drive - i had this issue when i installed by mistake the grub loader on a HDD and i had the system on the another - i did not notice it until i plugged out one of the drives...
 
Many thanks for your advice. Well, to each his own. Everyone loves nVIDIA & Intel, but I do not. That said, my foremost consideration is picking known compatible hardware to run PC-BSD 8.1, Ubuntu 9.04, and XP Pro (on three dedicated HDDs) at optimal ability...if that means nVIDIA or Intel is unavoidable, I will reluctantly accept necessity. 
 
So are you certain _both_ PC-BSD 8.1 and Ubuntu 9.04 are compatible with Phenom II x4, and AMD 785G/SB710 chipset?
 
Regarding motherboard, I would like to have it with dual-BIOS, and onboard thermal sensor to monitor temperature. If possible, mobo should have PCIe, SATA2, eSATA, USB 2.0, FireWire, amd gigabit Ethernet. I have no interest in onboard graphics or sound. 
 
Graphics card: No idea how to pick best one that both Ubuntu and PC-BSD will run on. I would prefer it to have TV tuner, if possible.
 
Sound card: I like Asus Xonar D2, but cannot find out whether PC-BSD 8.1 and Ubuntu 9.04 will run on it. If not, any sound card will do.
 
I have been told on other forum that motherboard/chipset, CPU, graphics card, sound card, and NIC card must "support all three operating systems." But on another forum one says to "forget about hardware support, and just make sure Ununtu 9.04 and PC-BSD 8.1 has drivers for each component." I have had almost no success doing Google searches on either approach. I am ready to admit I need help picking components that are known to work with both PC-BSD 8.1 and Ubuntu 9.04 (I think XP Pro will work with anything those two will). By the way, I will be supplying most of the components to the custom-build shop, which means I will buy the components one at a time, and so can afford to get the best.

---

