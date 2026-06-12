---
title: "Battery life on HP pavilion series DV2xxx DV6xxx etc"
date: 2007-09-18
forum: Hardware &amp; Laptops
---

### Post by lots_of_entropy on 2007-09-18
I am getting quite annoyed by the short battery life of my HP pavilion DV2000t laptop.

My specs are:
Core2 Duo 1.8 Ghz
NVIDIA GeForce 7200 Go
6cell battery

I have speedstepping set up, wifi goes into power save when running on battery, bluetooth is off, laptop mode puts the hd to sleep and I have a tickless kernel and did some optimization with powertop.

Still ... my battery life does not exceed 2 hours while doing mostly nothing.
I talked to a pal having a dv2000z (AMD Turion, NVIDIA GeForce 61xx) and he has the same problem.

I looked into underclocking, undervolting the CPU and GPU but no luck there ... the CPU voltage and frequency apparently are limited by the hardware - so 1GHz is as low as it gets for the CPU. For the NVIDIA card it is even worse since it should have the potential to underclock but coolbits for mobile GPUs does not work in linux. (damn you NVIDIA)
Furthermore some posts in the forum mention "proprietary acpi BIOS extensions" that windows is possibly using to save power.

I think I looked at everything reasonable (sure I can by a 12cell battery but come on ...) and I am stuck!

The most thing is that my gf owns a fujitsu siemens laptop with a core duo processor that runs 3.5 hours on the standard ubuntu setup (damn).

Any comments on this? (It is ok to cry ... at least I am quite close to it) 

Dom

---

### Post by TheCanuck on 2007-09-18
When you're running powertop does it show if the CPU enters C3 /C4 sleep at all?  How many wakeups do you get?  Tickless kernel works well, but you may need to apply a few HRT patches and make sure HPET is enabled to get decent C3 /C4 residency.

It could also be the video card.  I think that the Nvidia's have a vblank issue that causes higher interrupts as well and I'm not sure if there is a patch.  If you disable DRI with some cards it also improves battery life but you won't have 3D acceleration then.

One other thing is it might be the DSDT doesn't have the right info to allow the processor to enter C3/C4.    Which might mean you'd need to hack the DSDT to get C3/C4 -- I did this on an older P4-m which allows me to get 4hrs battery life now, but it's tough to do on the newer dual core laptops (i.e. seems most don't use the CST objects that older P4-m / Centrino laptops used). Chances are you could add the code anyway and get C3/C4, but it takes some time to figure out, recompile the kernel.  Although I believe Ubuntu allows DSDT info to be added on the fly through the intramfs.

---

### Post by drachenstern on 2007-09-19
I followed most of that, could you PM me or post here some references as far as the DSDT and the C3/C4 states.  I've got an AMD sempron lappy, so I'm curious if these would help me?

I too do not want to purchase the larger celled battery

---

### Post by TheCanuck on 2007-09-19
One thing to try if you have a Sempron or Celeron-M is CPUPW:

[http://www.tuxamito.com.es/cpupw/index.php](http://www.tuxamito.com.es/cpupw/index.php)

Supposedly lets you undervolt the cpu which will save battery life.

Other things to look at for Athlon / Sempron lines is the PSS support in the DSDT file:

[http://wejp.k.vu/projects/howto_cnq_athlon_64_x2/](http://wejp.k.vu/projects/howto_cnq_athlon_64_x2/)

That how-to goes over adding the power states directly to the DSDT to get cool'n quiet working.

Finally, C3/C4 states appear tough to get with several laptops with Linux.  If C3 isn't supported you can change the DSDT to allow it, but I only have experience with Intel systems.  AMD might work, but difficult to predict.  First take a look at powertop:  [http://www.linuxpowertop.org/](http://www.linuxpowertop.org/)  You also want to be using a kernel that is 2.6.21 or higher and may want to use the hrt power saving patches.

What I'll post next is a little how-to that I made up to get C3/C4 states on a P4-M laptop.  I know that this would work on Pentium-Ms and probably Celeron-Ms as well....AMD is a toss up.  Benefits to C3/C4 are much lower power usage but drawbacks are slower response times (haven't noticed any), buzzing on some systems (mine does this but it's not that annoying), potential for instability.  My laptop froze occasionally while in C3 (once per day if running for 24+ hrs), and the way I have avoided this is to run a small app like atop in the background with an interval of 1 or 2 seconds and set AGP mode to 2X (have an older 7500M in the laptop).  I believe my laptop was falling into too deep a sleep occasionally which would cause the odd lockup --- running atop keeps the cpu active but uses a minimal load and allows the system to still reach C3 sleep:

This is how I was able to get C3 states on my old P4-m with an ICH3-m chipset 82801CA.  Not sure how successful it will be for others, but it seems like it should be reproducible.  I’ve looked through several dsdts on [http://acpi.sourceforge.net/dsdt/index.php](http://acpi.sourceforge.net/dsdt/index.php) and it seems that many manufacturers have left out the C-state coding.  Thus, no matter how hard you bang your laptop against the wall, patch it to high heaven, beg god etc, you won’t get C3 or C4.  My laptop (VPR 180B5 that is based off a Samsung P10) normally comes up with C1 & C2.  I noticed the CST information missing and decided to see if I could add it in.  So far I have had some success:  Pros; C3 or C4 states can be reached, power draw has dropped from 20+ watts to 15 watts during idle (with screen off I get 10.9 watts), C3 residency is 99%.  Cons; I’ve seen the occasional lockup – ie. GUI freezes completely, and keyboard is not responsive (this is been fixed using atop with an interval of 1 - 2 seconds).

How to get C3 States
1)	Obtain your DSDT:    cat /proc/acpi/dsdt > dsdt
			
2)	Download the latest iasl from intel and run: 

iasl -d dsdt ; this will create a file called dsdt.dsl

3)	Open dsdt.dsl with Vi , gedit etc, & find CPU info for C-State  

        Scope (\_PR)
        {
        Processor (CPU0, 0x00, 0x00001010, 0x06) {}  //Note the 0x06.  Some laptops have 0x07 which prevents the code from being read properly.  If you see 0x07, change it to 0x06 and that might be all you need.
        
4)	Add CST info for C-States if you do not see it in the dsdt (example only – taken from [http://www.acpi.info/spec30a.htm](http://www.acpi.info/spec30a.htm) pp255-267):

Name(_CST, Package(0x04)
{
0x04, // There are four C-states defined here with three semanticsThe third and fourth C-states defined have the same C3 entry semantics.  If only 3 C-states, use 0x03.
Package(0x04){ResourceTemplate(){Register(FFixedHW, 0, 0, 0)}, 1, 1, 1000},  //Cstate=1, latency=1, power=1000mA
Package(0x04){ResourceTemplate(){Register(SystemIO, 8, 0, 0x1013)}, 2, 1, 500}, //Cstate=2, latency=1, power=500 mA
Package(0x04){ResourceTemplate(){Register(SystemIO, 8, 0, 0x1014)}, 3, 85, 250},
Package(0x04){ResourceTemplate(){Register(SystemIO, 8, 0, 0x1015)}, 3, 185, 150}
})
}

Note with above code:  I have used standard decimals for specifying Cstate, latency and power.  Usually these are entered as hex but the iasl will compile regardless.  The higher the latency & lower the power = better power savings.  Also, C4 is usually mapped to a C3 states but C4 has less power and higher latency.  For my laptop I am just using one C3 at the moment.  Latencies and power will vary with different processors.

5)	Compile new DSDT with iasl:  iasl -tc dsdt.dsl
Make sure there are no errors as this creates two files – dsdt.hex and DSDT.aml (DSDT.aml is not created if you have an error).  You need the DSDT.aml for the next steps
 
6)	Recompile Kernel to allow initrd – intrafms
[http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml)

a.	Obtain intrd patch  [http://gaugusch.at/acpi-dsdt-initrd-patches/acpi-dsdt-initrd-v0.8.4-2.6.21.patch](http://gaugusch.at/acpi-dsdt-initrd-patches/acpi-dsdt-initrd-v0.8.4-2.6.21.patch)
First you need to patch your kernel: 
	         cd /usr/src/linux
	          patch -p1 < /tmp/acpi-dsdt-initrd-patch-v0.x-....patch
In kernel config enable the ramdisk (not as module!) and initrd (in Block Devices) and enable CONFIG_ACPI_CUSTOM_DSDT_INITRD at the ACPI options (General Setup|Power Management|ACPI Support|Read custom DSDT from initramfs). Recompile your kernel  (see #7)


7)	Make sure kernel is latest 2.2.22 with HRT Patches and includes patch for your ICHX if applicable – ICH3/4 patch important for P4 systems.   [http://www.tglx.de/projects/hrtimers/](http://www.tglx.de/projects/hrtimers/)


8)	Compile kernel to allow tickless, High resolution time support, HPET, 1000HZ etc, ram disk via, ACPI (check all relevant power savings,bios support, cpu translation stats etc – build into kernel), initramfs: make menuconfig, make all, make modules_install, make install

9)	Script to add DSDT to initrd:  [http://gaugusch.at/acpi-dsdt-initrd-patches/initrd-add-dsdt](http://gaugusch.at/acpi-dsdt-initrd-patches/initrd-add-dsdt)

	Usage: ./initrd-add-dsdt initrd-2.6.22x.img DSDT.aml



Cross your fingers and reboot.

Now if everything works you should have additional C-states.  If you want to make changes to your C-states, add, remove, modify latencies, power etc, then just redit the dsdt.dsl file, recompile to get a new DSDT.aml and re-add it to your initrd.

---

### Post by lots_of_entropy on 2007-09-19
Hi

Thanks for replying guys. As far as I know the DVxxxxx's bios automatically maps C3 to C4 when on battery - so no need to tweak. Furthermore powertop shows me that I am 95% in C3/C4 (250 wakeups/s). I think this is pretty good considering the fact that I am running KDE and a proprietary NVIDIA driver. (Running just a bash prompt is like 70 wakeups/s but does increase battery life only 5mins or so).

My suspicion is that the core2 duo is sucking loads of power even if idle and the NVIDIA graphics card seems to be quite hungry.as well. Also the fan is running constantly at low speeds. I am guessing that the problem is a mixture between hardware (airflow), software (nvidia driver - no dynamic clock) and bios fuckups .
Considdering the fact that the new santa rosa chipset based dv2500 seems to have similar problems I think the general lesson is: don't by HP if you want battery life.

What do you think?

Dom

---

### Post by TheCanuck on 2007-09-19
Open a command prompt and take a look at cat /proc/acpi/processor/CPUx/power , for both CPU0 and CPU1.  Might want to check if both cores spend most of their time in C3 -- I think powertop just shows information for one cpu.

Nvidia just released new linux drivers yesterday -- might want to check them out since they say the drivers have improved power management:

[http://www.nvidia.com/object/linux_display_ia32_100.14.19.html](http://www.nvidia.com/object/linux_display_ia32_100.14.19.html)

Linux Display Driver - x86

Version: 100.14.19
Operating System: Linux x86
Release Date: September 18, 2007

Release Highlights

    * Added support for new GPUs:
          o Quadro FX 290
          o Quadro FX 370
          o Quadro FX 570
          o Quadro FX 1700

    * Improved GLX_EXT_texture_from_pixmap out-of-memory handling.
    * Fixed a performance regression on GeForce 8 GPUs.
    * Added support for a 'NoScanout' mode to the X driver, useful for high performance computing environments and remote graphics; please see the 'UseDisplayDevice' option description for details.
    *** Improved power management support with GeForce 8 and older GPUs.**


Also, I believe you can disable one of the cores with :   echo 0 > /sys/devices/system/cpu/cpu1/online
To reenable you'd just type:  echo 1 > /sys/devices/system/cpu/cpu1/online

---

### Post by lots_of_entropy on 2007-09-20
I installed the new NVIDIA driver and disbaled one CPU. With all the other power saving stuff I described already I now get 1:45h while surfing the internet and chatting via skpe.

Still not very impressive - no?

---

### Post by TheCanuck on 2007-09-20
Yeah that's pretty bad.  What does powertop report as the battery usage in watts?  Also, did disabling the core actually lower the power usage?  Some have reported good power savings (2 watts or so) while others have reported that power usage went up.

It could also be certain modules draining power.  You could always have powertop running to observe the power usage and then start removing modules -- uhci_hcd etc are always big battery drainers.

---

### Post by lamborghiniwang on 2007-09-20
According to this **[article in Thinkwiki]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Tribe_5_on_a_ThinkPad_T61")**, the Thinkpad T61 consumes about 30% more power in Ubuntu than it does in Windows XP even with the tickless 2.6.22 kernel (Gusty Tribe 5).

---

### Post by aldeby on 2007-09-21
Just an advice, remove **pulseaudio** if its version is below 0.9.7 becuase it has a big problem with powersaving. it issues over 250 interrupts to Intel HDA audio even if you are not listening at anything.
This is a known bug and will be fixed in 0.9.7 release of pulseaudio.
Please note that removing pulseaudio only affects the logon sound, while listening to music is not affected at all.
```
sudo apt-get remove pulseaudio
```

---

### Post by darksizzle on 2007-10-14
Hey I pulled this out of a review over the dv2000z from this review
[http://www.notebookreview.com/default.asp?newsID=3032&review=HP+dv2000z](http://www.notebookreview.com/default.asp?newsID=3032&review=HP+dv2000z)

Yet the dv2000z, in its mediocre battery longevity, has a strict ceiling for its mobility. Although the HP site claims the regular battery will last 4 hours, my experience was much more limited. When reformatting the computer, reinstalling Windows, and generally setting it up that is, with the brightness at 7, all the hardware devices running, the CPU using both cores at 1.075 V, a USB flash stick sticking out, and the wireless switch turned on, the battery lasted only 1 hour and 36 minutes before going into stand-by with 6% left. Simply watching a movie in Windows (single core, .8 V) at level 5 brightness and without wireless yielded a still meager 2 hours before stand-by kicked in. Watching the movie in QuickPlay should make the battery last another 15 minutes, presumably. The problem can be solved with a 12-cell battery, but at the price of an added pound, $50, and a bulky design.

As a result, then, the dv2000 is a portable laptop without a portable battery.

So it seems like you're about right with what this is saying.  I'm picking one up next week so I'll be eyeing this thread for ideas haha.  I'm probably just going to bite the bullet and grab the 12 cell.

---

