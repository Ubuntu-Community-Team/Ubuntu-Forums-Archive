---
title: "Crippled frequency scaling on a desktop pentium 4"
date: 2007-01-08
forum: Hardware &amp; Laptops
---

### Post by bossanova on 2007-01-08
Some while ago I was running a gentoo installation with a 2.6.15 kernel I had rolled myself and frequency scaling worked very nicely. I could switch to the ondemand governor and watch the processor change from 12.5% (350Mhz) to 100% (2.8GHz). Unfortunately I accidentally trashed that system so the kernel config has disappeared.

When I installed edgy I found that frequency scaling wasn't working at all (perhaps I just needed to load some modules, but anyway...). Because I had trouble compiling a working kernel with the edgy sources I started building kernels with the vanilla 2.6.19.1 sources.

The first kernel I built with these behaved as well as the one I had been using in the gentoo installation, but then I built another one and overwrote the config file. However that second kernel and all subsequent ones have had their frequency scaling severely crippled. Generally they only scale between 75% and 100%. These values (i.e. 2100000 and 2800000) are set in /sys.../cpuinfo_min_freq and ,,,/cpuinfo_max_freq and can't be changed from userspace.

I have tried all kinds of options in the kernel config, but I just can't seem to find out what's wrong. What kernel options determine the difference between being able to scale down to 75% and being able to scale right down to 12.5% speed on a Pentium 4 desktop cpu?

I am attaching the config for the kernel I am using right now, in which scaling is limited to between 75% and 100%

---

### Post by RandomJoe on 2007-01-08
Which driver are you using?  The one that lets my P4 systems scale waaay back like you mention is p4-clockmod, the one that only gives a couple of steps is the speedstep-XXX one.  In my case, only my laptop can use the speedstep one, but perhaps some desktops will as well.

I have found that the speedstep driver results in much lower power consumption (since it also adjusts CPU voltage) than the p4-clockmod driver, which only scales speed.

I notice in your config you have p4-clockmod compiled into the kernel, but the speedsteps are modules.  Perhaps one of the modules is being loaded and used instead?

---

### Post by bossanova on 2007-01-08
cpufreq-info tells me I'm using p4-clockmod. I tried loading the speedstep drivers and they don't work ("no such device"). One thing that puzzles me is that acpi-cpufreq won't load once p4-clockmod is loaded because 
[INDENT]FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.19.1standard-config/kernel/arch/i386/kernel/cpu/cpufreq/acpi-cpufreq.ko): Device or resource busy
[/INDENT]
However it won't load before p4-clockmod is loaded because "no such device".

Are you sure there's not something really weird to be set somewhere completely different, perhaps under "kernel hacking"? That happened to me once when I was trying to get suspend2 or realtime-lsm (I forget which) working.

---

### Post by RandomJoe on 2007-01-08
Nothing that I know of, but it's been quite a while since I last compiled a kernel.  I installed Ubuntu 6.06 on my P4 server a few months back, and I got the expected performance from p4-clockmod with the stock kernel.

---

### Post by bossanova on 2007-01-08
Thank you for taking the time to help me over this. :grateful:

Do you know whether I can get hold of the config for the stock dapper kernel? That may not be possible, judging by [this]("http://ubuntuforums.org/showthread.php?t=123935") but it doesn't hurt to try :) 

Or failing that I wonder if you might be able, if you've got a moment, to lsmod on your P4 server and grep for "step" "freq" and "acpi" (assuming you've still got dapper installed on it). That would at least help me to narrow things down a bit.

Meanwhile I should probably take another look at the stock edgy kernel and see if there are any modules that didn't load and should have.

---

### Post by RandomJoe on 2007-01-09
```
:~$ lsmod | grep step
speedstep_lib           4580  1 p4_clockmod

~$ lsmod | grep freq
cpufreq_ondemand        7752  1
freq_table              4928  1 p4_clockmod

~$ lsmod | grep acpi
sony_acpi               5580  0
pcc_acpi               12416  0
dev_acpi               11236  0
acpi_sbs               20172  0
battery                 9988  1 acpi_sbs
ac                      5220  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               22848  2 i2c_acpi_ec,i2c_piix4

```
And attached is the config for 2.6.15-27-686, the configs are all handily located in /boot.

---

### Post by bossanova on 2007-01-09
Thanks again! I realised after my last post that the configs were actually really easy to find.

I installed the dapper stock kernel and I got frequency scaling from 25% to 100%. (Maybe I was mistaken about the 12.5% minimum). However when I took the same config and used it to build against the edgy sources and the vanilla 2.6.19.1 sources (with a few changes such as building in IDE and ext3 support to make it bootable), I was still stuck with the limited 75% to 100% range.

I then tried to build a kernel from the dapper linux sources, using a modified stock dapper config and it failed at built-in.o, which is not one you can work around. Then I tried to build the vanilla 2.6.15.7 kernel and that failed too at the same place. Not being able to test configs against the 2.6.15 sources makes it very difficult to do any more troubleshooting. It also means I can't use a 2.6.15 kernel as a workaround because the stock dapper kernel build won't support my webcam.

Time for a smiley I think... ](*,)

---

### Post by bossanova on 2007-01-09
Ah. Just found [this bug report]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/51847") . The reporter says that the problem stems from a change to the breezy kernel, which doesn't quite square with having frequency scaling working properly in dapper. It sounds like I'll need to do a minor edit to the source code myself to get scaling down to 700MHz again.

---

### Post by bossanova on 2007-01-10
It's working now. Here's what you do to get Pentium 4 frequency scaling working properly:

**EITHER** install the old Dapper kernel package. For most people that will probably do fine.
[INDENT]$ wget [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-image-2.6.15-27-686_2.6.15-27.50_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-image-2.6.15-27-686_2.6.15-27.50_i386.deb)
$ sudo dpkg --install linux-image-2.6.15-27-686_2.6.15-27.50_i386.deb[/INDENT]

**OR**, if you need to build your own kernel for whatever reason, then you will need either to install the Edgy sources
[INDENT]$ apt-get install linux-sources
$ cd /usr/src
$ untar linux-sources*bz2[/INDENT]
or grab some kernel sources from somewhere else, such as [here]("http://kernel.org/pub/linux/kernel"), and, once you have unpacked the sources, open (kernel source directory)/arch/i386/kernel/cpu/cpufreq
/p4-clockmod.c in a text editor and find the line
[INDENT]if (has_N60_errata[policy->cpu] && p4clockmod_table[i].frequency < 2000000)[/INDENT]
Change '2000000' to something more appropriate, such as '700000' (i.e. 700MHz).
Then configure, build and install your kernel.

**IMPORTANT:**
The reason for the 2GHz limit is to deal with a hardware problem affecting a small minority of Pentium 4 processors that causes instability at low speeds. Try the Dapper kernel image first to make sure that this doesn't affect your machine. You may need to run
[INDENT]sudo modprobe p4-clockmod[/INDENT]

I adjusted the minimum speed in my kernel to 700MHz, but I think you might be able to push it lower than that. So you might want to try it. Please add a comment here to let people know if it works or not.

**USEFUL TIP:**
You can use the Gnome CPU Scaling Monitor applet to set the performance governor or processor speed by running 
[INDENT]$ sudo dpkg-reconfigure gnome-applets[/INDENT]
and answering "yes" to the question about suid for cpufreq-selector.

---

