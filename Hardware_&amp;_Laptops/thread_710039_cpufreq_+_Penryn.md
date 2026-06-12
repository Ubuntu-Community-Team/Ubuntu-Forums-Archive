---
title: "cpufreq + Penryn?"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by evan.rotert on 2008-02-28
I just received my new HP dv2700tse today, with the C2D T9300 CPU.  I'm trying to enable CPU frequency scaling, and I can't get it to work!  I've tried loading the speedstep-centrino module, but it gives me a fatal error.  When I tried installing a cpufreq applet, it told me frequency scaling wasn't available.  Does anyone know how I might go about this?  Is it a kernel thing that might be fixed for Hardy?

---

### Post by graingert on 2008-03-09
same laptop (ea version) can confirm this problem with the same intel chip any solutions?

I also tried that module but it is not available in gutsy

---

### Post by Yellow Pasque on 2008-03-09
You folks might have to roll your own kernel or use Ubuntu 8.04 Alpha 6.

---

### Post by chazdraves on 2008-03-09
Yup, same problem with a C2D E4300... Was just about to post a thread. There's no available fix until 8.04?

Thanks,
- Chaz

---

### Post by graingert on 2008-03-09
Do you know for certian 8.04 works with this processor?

---

### Post by sdennie on 2008-03-10
Are you sure this a Penryn problem and not an ACPI problem?  I'm using a 2.6.24 kernel at the moment for other reasons but, I'm 99.9% certain that the default gutsy kernel (both 32 and 64 bit) was doing CPU scaling on my T9300 (I keep the cpufreq applet up at all times).  What is the output of "lsmod | grep cpufreq"?  I ask about possible ACPI issues because I get this:

```

$ lsmod | grep cpufreq
acpi_cpufreq            9836  2 
cpufreq_ondemand        9292  1 
cpufreq_conservative     8264  0 
cpufreq_userspace       4836  0 
cpufreq_stats           6784  0 
freq_table              5344  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave       2304  0 
processor              36680  4 thermal,acpi_cpufreq
$ lsmod | grep centrino

```

So, I'm not using the speedstep-centrino module at all and "modinfo acpi-cpufreq" tells me that it's the "ACPI Processor P-States Driver" so, as far as I can tell, my BIOS is telling linux what the P-States are for the cpu.

---

### Post by graingert on 2008-03-10
cpufreq_ondemand       10896  0 
cpufreq_userspace       6048  0 
cpufreq_stats           8160  0 
cpufreq_conservative     9608  0 
cpufreq_powersave       3072  0 
freq_table              6464  2 cpufreq_ondemand,cpufreq_stats

mod info gives:

filename:       /lib/modules/2.6.22-14-generic/kernel/arch/x86_64/kernel/cpufreq/acpi-cpufreq.ko
alias:          acpi
license:        GPL
description:    ACPI Processor P-States Driver
author:         Paul Diefenbaugh, Dominik Brodowski
srcversion:     45DC605C5D70EB0CBCAA018
depends:        freq_table,processor
vermagic:       2.6.22-14-generic SMP mod_unload 
parm:           acpi_pstate_strict:value 0 or non-zero. non-zero -> strict ACPI checks are performed during frequency changes. (uint)

I am upgrading to the hardy kernel currently

---

### Post by graingert on 2008-03-10
```
graingert@ubuntu-laptop:~/Downloads$ sudo modprobe acpi-cpufreq
[sudo] password for graingert:
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.22-14-generic/kernel/arch/x86_64/kernel/cpufreq/acpi-cpufreq.ko): No such device

```

Upgrading to Hardy kernel did not allow me to use processor scaling.

---

### Post by sdennie on 2008-03-11
> **graingert said:**
> ```
graingert@ubuntu-laptop:~/Downloads$ sudo modprobe acpi-cpufreq
[sudo] password for graingert:
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.22-14-generic/kernel/arch/x86_64/kernel/cpufreq/acpi-cpufreq.ko): No such device

```

Upgrading to Hardy kernel did not allow me to use processor scaling.

It looks like you still booted into the Gutsy kernel though.  A Hardy kernel would have looked in /lib/modules/2.6.24-something for the modules whereas you are still looking in the 2.6.22 directory (which is what Gutsy uses).

---

### Post by graingert on 2008-03-11
Sorry the command output was run on the old kernel, installing the new kernel "hosed" my system; I did however attempt to use processor scaling although including this no hardware worked well.

---

### Post by evan.rotert on 2008-03-13
@vor: I'm not sure of anything really, whether it's an acpi problem or what, but here's the output of lsmod | grep cpufreq:

$ lsmod | grep cpufreq
cpufreq_powersave       2688  0 
cpufreq_userspace       5284  0 
cpufreq_ondemand        9740  0 
cpufreq_conservative     8712  0 
cpufreq_stats           7104  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats

modinfo acpi_cpufreq shows that it depends on the module "processor" as well, which I have loaded.  In any case, when I modprobe acpi_cpufreq, I get the following, same as other users:

FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.24-12-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device

As you can see, I'm using the 2.6.24-12 kernel on Hardy alpha 6.  Remember that this is a laptop and my BIOS options are not nearly as extensive as a desktop mobo might allow, but there's nothing in there to indicate that it's simply turned off.  Everything else works great, especially after the update I did 20 minutes ago, but I still can't scale my frequency.  Anyone else have any ideas?

---

### Post by sdennie on 2008-03-13
I'm not sure I can help with this but, does the following directory exist?

```

/sys/devices/system/cpu/cpu0/cpufreq/

```

If so, does it have scaling_driver and scaling_governor?

You could do a "locate acpi-cpufreq.ko" and look in the /lib/modules/whatever directory where it lives and try to manually insert the various other cpufreq drivers and then check scaling_driver and scaling_governor to see if any of them work but, I don't think that anything will come of that.  

You could also see if there is a BIOS upgrade available for your machine which might make the acpi-cpufreq work.  The Penryns are still new and it's possible that vendors have shoved them out the door without complete BIOS support.

---

### Post by evan.rotert on 2008-03-14
No, I don't have that directory.  I tried to check for BIOS updates, but the specific model number of my laptop isn't printed in the usual place, so I'll have to call HP to determine it.  In any case, if there is a BIOS update that I need, I may just pass on that because I'd rather lose some battery life than risk disabling my new laptop's motherboard!  I'll keep looking around- if anyone else has any ideas, let me know!

---

### Post by kjuliano on 2008-03-15
I have this same problem with another penryn based hp laptop it has a 9300.

dv 2756

I have read many posts of people saying feisty was find but in gutsy cpu throttling is a no go, why is their no acknowledgement of this on the part of any ubuntu people that might actually be able to help?

i am now trying other distributions on another partiition to see if it will work on them.

I get the feeling this issue is being completely ignored, as people say hardy has the same problem.

---

### Post by sdennie on 2008-03-15
The problem is not lack of support for a T9300 from the kernel (my Dell XPS m1330 with a T9300 works just fine) so, I'm inclined to believe that it's an ACPI problem with the laptop.  My previous laptop had such a poor BIOS that the GPU fan wouldn't turn on without building a custom DSDT.  No amount of work on the part of the distribution or kernel could have fixed this problem and the vendor (Toshiba) had no interest in fixing it so it was up to the user to build a custom DSDT to prevent the laptop from frying.

I don't have an HP laptop with a T9300 to test but, you may want to google for "custom dsdt" and see if a fixed DSDT will help you.  It's slightly complicated to fix a DSDT but, barring a new BIOS release for your laptop, it may be the only way to make frequency scaling work.

Of course, it could be completely unrelated to the BIOS but it's worth investigating.

---

### Post by graingert on 2008-03-16
It shouldn't be the bios because cpu scaling fine in windows, :-(

---

### Post by sdennie on 2008-03-16
> **graingert said:**
> It shouldn't be the bios because cpu scaling fine in windows, :-(

Unfortunately, that makes no difference.  Hardware vendors have been known to add hacks to a BIOS (think "if(OS == Vista) do_something_useful").  I can't say for sure if it's a BIOS problem but, it's worth looking into.

---

### Post by kjuliano on 2008-03-17
> **vor said:**
> The problem is not lack of support for a T9300 from the kernel (my Dell XPS m1330 with a T9300 works just fine) so, I'm inclined to believe that it's an ACPI problem with the laptop.  My previous laptop had such a poor BIOS that the GPU fan wouldn't turn on without building a custom DSDT.  No amount of work on the part of the distribution or kernel could have fixed this problem and the vendor (Toshiba) had no interest in fixing it so it was up to the user to build a custom DSDT to prevent the laptop from frying.

I don't have an HP laptop with a T9300 to test but, you may want to google for "custom dsdt" and see if a fixed DSDT will help you.  It's slightly complicated to fix a DSDT but, barring a new BIOS release for your laptop, it may be the only way to make frequency scaling work.

Of course, it could be completely unrelated to the BIOS but it's worth investigating.

thanks for the reply

i checked if the dst had errors or not by following this info...  [http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems](http://gentoo-wiki.com/HOWTO_Fix_Common_ACPI_Problems)


the section on using the intel compiler to disassemble and re-asseble the dsdt, but there were 0 errors.

so it appears not to be a DSDT issue.  perhaps the hp is using a different mainboard than the dell...

this seemed to have some promise, but now i am stuck
i think building a newer version of the acpi_cpufreq module would be good, but i can't seem to find a link to it.  perhaps such a stand alone package doesn't exist.

the other power saving things seem to work at least somewhat.

---

### Post by sdennie on 2008-03-17
Sometimes the BIOS will only enable certain features depending on what operating system it detects.  If frequency scaling is working in XP/Vista this could be the problem but, it's slightly more difficult to fix.  After my last laptop I have a lot of experience fixing DSDT problems and I'd be happy to look at your .dst to see if that's the case.

The other option would be to build a custom kernel and see if that helps (either 2.6.24.3 or an 2.6.25-rc kernel).  It's not trivial to do if you've never done it before but, it can be done without breaking your machine.  [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) is a good guide if you want to try it.

Note: If you build a custom kernel, the gutsy kernel seems to build iwlwifi and intel audio outside of the kernel source so, you'll have to explicitly enable those if you use the gutsy kernel config as your base.  They are both common things to need on a laptop.

---

### Post by kjuliano on 2008-03-18
i tried rolling a custom kernel in ubuntu with no luck.  ended up with a vfs related kernel panic during the boot....  i didn't actually change any fs related options though.

followed the exact same steps as in debian lenny and that kernel worked fine, i'm not sure  why the ubuntu kernel source had this problem.

used make-kpkg 
tried with --initrd, and tried without it.

i guess i will try installing the hardy kernel. 

perhaps that is what is missing. 

but i installed the pristine 2.6.24.3 kernel in debian testing  but still no go.

its odd because it recognizes the cpu, tells me its  t9300 says it supports all these features but then when its time to load the driver no go.

i get an error about no NUMA something or other also...

not sure how relevant any of it is.  on a side note, in gutsy the dimming keys for the lcd work fine, but in debian, even with 2.6.24 they are a no go.

i think this is the joy of installing linux on a laptop that just hit the market very recently.
its a dv2756tx sold in taiwan.  

does anyone know of any sort of linux on hp lapops project similar to the asus one?

thanks again... now to find that hardy kernel on gutsy howto.

---

### Post by evan.rotert on 2008-03-18
I've only compiled a kernel twice before (both Gentoo installations) but I gave it a shot earlier today on Ubuntu- I enabled everything I could see that was related to ACPI support (most things had already been enabled), including building acpi_cpufreq into the kernel rather than loading it as a module.  Bottom line, it caused screen resolution problems (from 1280 x 800 down to 800 x 600), but otherwise worked- except for cpu frequency scaling.  Still no luck.  It could be a BIOS problem, though I see nothing in the whole BIOS that has anything to do with ACPI, frequency scaling, or anything like that.  This is a dv2700 purchased a few weeks ago in the US (specific model number is nowhere to be found, believe me I've looked).  Let's keep this thread alive to see if anyone more knowledgeable about kernel updates, ACPI or other such things happens to see it...

---

### Post by kjuliano on 2008-03-18
> **evan.rotert said:**
> I've only compiled a kernel twice before (both Gentoo installations) but I gave it a shot earlier today on Ubuntu- I enabled everything I could see that was related to ACPI support (most things had already been enabled), including building acpi_cpufreq into the kernel rather than loading it as a module.  Bottom line, it caused screen resolution problems (from 1280 x 800 down to 800 x 600), but otherwise worked- except for cpu frequency scaling.  Still no luck.  It could be a BIOS problem, though I see nothing in the whole BIOS that has anything to do with ACPI, frequency scaling, or anything like that.  This is a dv2700 purchased a few weeks ago in the US (specific model number is nowhere to be found, believe me I've looked).  Let's keep this thread alive to see if anyone more knowledgeable about kernel updates, ACPI or other such things happens to see it...

is your laptop a custom build?

did  you have to pay the vista tax when you bought it?

if so, you can go into an hp program that tells you more details about your specific computer.

ubuntu seems to have some sort of patching done over debian testing or a pristine 2.6.24 kernel though, because in ubuntu the lcd brightness works, and in debian it does not.  i can't even use the function key in debian

this makes me think there is some sort of patch that is non-standard and fixes some of these issues.  if any more knowledgable people out there know of laptop or hp specific patches, please post links to the info.

---

### Post by kjuliano on 2008-03-18
i wanted to attack dmesg log incase that helps in some way.

i get a few things i think might mean something:


[    0.000000] No NUMA configuration found


this when the cpu 0 loads


 Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Extended CMOS year: 2000
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[   26.683978] time.c: Detected 2493.751 MHz processor.
[   26.685749] Console: colour VGA+ 80x25
[   26.685765] Checking aperture...
[   26.685776] Calgary: detecting Calgary via BIOS EBDA area
[   26.685777] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   26.685779] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[   26.721848] Placing software IO TLB between 0x103d000 - 0x503d000
[   26.757818] Memory: 4043036k/5242880k available (2274k kernel code, 149600k reserved, 1185k data, 296k init)
[   26.757853] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   26.835646] Calibrating delay using timer specific routine.. 4992.48 BogoMIPS (lpj=9984970)



lastly this looks interesting.

 ACPI: System BIOS is requesting _OSI(Linux)
[   27.648053] ACPI: Please test with "acpi_osi=!Linux"
[   27.648053] Please send dmidecode to [email]linux-acpi@xxxxxxxxx.org[/email]  [removed email address]

---

### Post by sdennie on 2008-03-18
> 
 ACPI: System BIOS is requesting _OSI(Linux)
[   27.648053] ACPI: Please test with "acpi_osi=!Linux"
[   27.648053] Please send dmidecode to [email]linux-acpi@xxxxxxxxx.org[/email]  [removed email address]

Did you try booting with acpi_osi=!Linux?  I had forgotten that newer kernels have this feature and it should be roughly equivalent to building a custom DSDT that forces the OS to identify itself as Vista.  You can test this out by hitting escape on the grub boot menu and then hitting "e" on the kernel you want to boot then again on the boot string of the kernel (should be the second menu option).  Add acpi_osi=!Linux to the end of boot string, hit enter and then "b" to boot.

---

### Post by kjuliano on 2008-03-19
> **vor said:**
> Did you try booting with acpi_osi=!Linux?  I had forgotten that newer kernels have this feature and it should be roughly equivalent to building a custom DSDT that forces the OS to identify itself as Vista.  You can test this out by hitting escape on the grub boot menu and then hitting "e" on the kernel you want to boot then again on the boot string of the kernel (should be the second menu option).  Add acpi_osi=!Linux to the end of boot string, hit enter and then "b" to boot.

i did try booting.  i added multiple entries into menu.lst so i could boot as not linux, tell the bios its window 2006 and tell the bios windows 2000.

not much of a difference, throttling still not supported.

but it seemed to run a little slower with the !linux on....  

i'm going to try rolling a pristine 2.6.24.3 kernel and see what effect that has i'm tempted to try 2.6.25-rc6 but not sure what that will break as its just a RC

---

### Post by graingert on 2008-03-19
Same laptop different processor works with cpu-scaling, not mine so not much detail

---

### Post by graingert on 2008-03-23
Check out the bug page [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201890]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201890")

---

### Post by evan.rotert on 2008-03-23
Hey, thanks for submitting a bug!  I commented on it and added the output of dmesg.  I hope someone addresses this!

---

### Post by graingert on 2008-03-24
Is there any way for us to add a bounty to this problem?

---

### Post by evan.rotert on 2008-03-25
How much? :-)

---

### Post by graingert on 2008-03-31
Has any-one tried to downgrade to a lower bios version? My current version is "F.26" the latest available is "F.25".  Could someone try this?

---

### Post by bennyvdc on 2008-04-14
i'm kind of new to all this but i seem to have the same problem with my HP DV2750eb laptop.

(It came installed with a vista premium with more faults then anything else so ... )

It has a T9300 intel cpu and a F.25 Bios version installed but

using the 7.10 (32bitt) linux version I get  :"it could be that your computer isn't configurerd right or changing cpu speed is not supported'

does anyone have a solution for this problem by now ?

---

### Post by graingert on 2008-04-14
hmm, have you tried any of the boot flags?

---

### Post by bennyvdc on 2008-04-14
boot flags?

---

### Post by graingert on 2008-04-15
bootflags!
> **vor said:**
> Did you try booting with acpi_osi=!Linux?  ....  Add acpi_osi=!Linux to the end of boot string, hit enter and then "b" to boot.

---

### Post by afxkenny on 2008-05-20
> **graingert said:**
> Has any-one tried to downgrade to a lower bios version? My current version is "F.26" the latest available is "F.25".  Could someone try this?

hi, i'm looking for the f.26 version of the bios, i have a dv2780. Could you send me that, please?

---

### Post by graingert on 2008-05-20
Good news everyone!:guitar:

[http://h10025.www1.hp.com/ewfrf/wc/previousVersions?softwareitem=ob-59671-1&lc=en&cc=uk&dlc=en&product=3667426&os=2093&lang=en](http://h10025.www1.hp.com/ewfrf/wc/previousVersions?softwareitem=ob-59671-1&lc=en&cc=uk&dlc=en&product=3667426&os=2093&lang=en)

F.2A is available! Skipping F.26 for some reason,  If anyone wants to give that a go?

---

### Post by afxkenny on 2008-05-20
> **graingert said:**
> Good news everyone!:guitar:

[http://h10025.www1.hp.com/ewfrf/wc/previousVersions?softwareitem=ob-59671-1&lc=en&cc=uk&dlc=en&product=3667426&os=2093&lang=en](http://h10025.www1.hp.com/ewfrf/wc/previousVersions?softwareitem=ob-59671-1&lc=en&cc=uk&dlc=en&product=3667426&os=2093&lang=en)

F.2A is available! Skipping F.26 for some reason,  If anyone wants to give that a go?
I'm using it right now, but i don't like cause it turns the fan on all the time

---

### Post by graingert on 2008-07-20
Yeah this solves the problem!

---

