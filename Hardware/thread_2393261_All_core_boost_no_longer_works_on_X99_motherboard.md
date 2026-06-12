---
title: "All core boost no longer works on X99 motherboard"
date: 2018-05-31
forum: Hardware
---

### Post by Keith Myers on 2018-05-31
Something got changed in the OS between early April and now.  I haven't done a thing to the hardware or BIOS.  I used to get an all core boost to my 42 multiplier across all cores by simply setting Sync all cores in the BIOS.  Run Prime95 and have all cores boost to 4200Mhz.  This is the screenshot from i7z.
[[IMG]https://farm1.staticflickr.com/817/40299511435_cb69bac645_b.jpg[/IMG]]("https://flic.kr/p/24p8wJF")[Screenshot of i7z while Prime95 running]("https://flic.kr/p/24p8wJF")

Now this is what I get.


[[IMG]https://farm2.staticflickr.com/1745/42484537841_88ed9e1b9e_b.jpg[/IMG]]("https://flic.kr/p/27JdmXK")[Screenshot from i7z 2018-05-31 17-59-45]("https://flic.kr/p/27JdmXK")

The motherboard is an ASUS X99-E-10G-WS workstation motherboard with the latest 0801 BIOS.  I spent the entire day yesterday looking at the cpufreq governors and trying any and all configurations.  The cpufreq scaling governor is set to performance.  It doesn't matter.  All I get is one core boosting to 4 Ghz and the rest falling down to 3.8Ghz.

Can anyone point me in the right direction to get my all core boost back to 4200Mhz please.  Thanks in advance.

---

### Post by Keith Myers on 2018-06-05
Update.  I flashed the newest 0903 BIOS for the motherboard that has all the manufacturer fixes for Meltdown/Spectre.  That forced me to start from scratch with the BIOS settings.  The new BIOS set up the memory via a BCLK of 125Mhz at XMP memory profile and Sync All Cores multiplier of 32 to produce a 4000Mhz core clock and 3000 XMP setting. All the other BIOS settings were the normal default Auto when starting from a new BIOS reload.

What I found out was that the All Core Boost was working now.  I had the Turbo On by default.  The Multi-Core Enhancement was on by default.  I disabled the Intel Speed-Step setting as I never want the system to downclock to save power.  This is an 24/7 math processor after all.

I also found that I could get back to my All Core Boost of 4200 or close enough of 4250 Mhz that the 125 Mhz BCLK setting and the 34 Sync All Cores multiplier produces.  I was happy. But . . . . . . 

The reason that the BIOS chose the 125 BCLK route was that is presupposes that any memory kit of greater than stock XMP 2400 needs to use BCLK to achieve >> 2400 Mhz XMP profiles.  The BIOS also suggests that it is better to use the stock and standard 100Mhz front side bus frequency to achieve a rated XMP value if the kit supports it over the artificial 125Mhz BCLK setting at a lower multiplier.

This is the way I had set the 3000Mhz XMP memory kit up originally.  The front side bus at 100Mhz and a cpu core mulitplier of 42 to achieve my 4200Mhz cpu core clock and a choosing of the standard 3000Mhz XMP memory strap in the BIOS.

So I set up the BIOS the original way that I had the BIOS when it worked correctly on the earlier 4.13 kernels.  BCLK of 100Mhz and multiplier of 42.  Memory profile of kit rated 3000Mhz and everything else as Auto just as before.

But what I found out was that I once again lost my All Core Boost of my original post.  Only two cores would boost to the max of 4000Mhz and the rest at 3800Mhz.  This was with no other changes to the OS.  The same scaling driver and governor that defaults to intel_pstate.

So whatever the cpu registers throw out to the OS in the MSR's with a BCLK of 125Mhz is different from what is put out by the cpu registers with a BCLK of 100Mhz.  I did not expect this at all and I have no explanation of how the scaling mechanism works differently with different BCLKS.  Maybe someone more knowledgeable can educate me.

So for now, I am running with the BCLK at 125Mhz and Sync All Cores at 34 to achieve an All Core Boost of 4250Mhz when fully loaded.  This is a screenshot of the running system currently.

[[IMG]https://farm2.staticflickr.com/1756/28724114008_c2c3afb76e_c.jpg[/IMG]]("https://flic.kr/p/KLfAmY")[i7Z Screenshot from 2018-06-05 13-19-47]("https://flic.kr/p/KLfAmY"):P

---

