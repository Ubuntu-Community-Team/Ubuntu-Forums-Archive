---
title: "Ubuntu On Thinkpad W520: Your Experiences"
date: 2011-06-12
forum: Hardware
---

### Post by sentraser165 on 2011-06-12
Hi everyone,

I am new to this wonderful forum, and I am already blown away by the amicability and willingness to help others (even with problems that are probably very easy to solve) that the people on this forum have.  Hopefully, I can take advantage of some of your experience.  Right now, I am 95% sure I am going to go for a new Thinkpad W520 in the near future; however, I wanted to get a feel for people's feelings toward it after having used the machine for awhile.  In particular, I have read a few threads about dealing with nvidia optimus, the wireless card, brightness controls, the sandy bridge architecture, and hibernate/sleep (perhaps there have been other issues as well).  For those who have had these or any other issues, have you found a way to correct them or at least some sort of a workaround?  From the threads I've seen, it isn't so clear whether or not these issues have been solved.  That, and in general, what has been your experience thus far with the W520?  Thank you all for your input.

-Steve

---

### Post by mörgæs on 2011-06-12
Hi, welcome to the fora. Good that you like the 'Ubuntu' spirit :-)

Does this help?
[http://ubuntuforums.org/showthread.php?t=1757821](http://ubuntuforums.org/showthread.php?t=1757821)

---

### Post by gatman3 on 2011-06-23
sentraser,

I have had a W520 for about a week now as an upgrade to my old W500 (I skipped the W510 generation).  I have to say that this W520 has been a little challenging, although I am writing into this forum using it so it's at least functional.

The thread cited by mörgæs above has about the only information I could find on configuring this machine with Ubuntu.  Some of the information in that thread is a little confusing because it's not clear in all cases if they are talking about the nvidia proprietary driver or the open-source nouveau driver.

Here is a brief summary of my experiences thus far:

Graphics configuration done in the BIOS.  Select "Integrated" for the Intel graphics built into the chipset and "Discrete" for the separate NVidia 1000M/2000M chip (whether you use the open-source nouveau driver or the proprietary nvidia driver).  Optimus is OS-switchable graphics and might be supported somewhat by the bumblebee project, but I haven't tried it and really have no need for it.  I figure it's just one more headache I don't need right now.

In short, if you don't need the NVidia graphics, you will be much happier with this machine.  The integrated (Intel) graphics pretty much works out-of-the-box with the Ubuntu 11.04 release.  However, there still seems to be a problem with the 2.6.38 kernel (the stock Ubuntu 11.04 kernel) that causes a "stuttering" problem in that the mouse freezes for a fraction of a second every few seconds or so.  I followed the directions provided by this link (cited at the end of the other thread) to upgrade the kernel to 2.6.39-0 which seems to solve the stuttering problems:

[http://www.addictivetips.com/ubuntu-linux-tips/how-to-update-ubuntu-11-04-kernel-to-2-6-39-0/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-update-ubuntu-11-04-kernel-to-2-6-39-0/)

However, upgrading the kernel to 2.6.39 breaks VMWare (if you care about that).  Fortunately I found a patch that fixes up VMWare to work with the 2.6.39 kernel.  There certainly may be other things that get messed up in the 11.04 distribution when you upgrade from the stock kernel.

On my setup, suspend-to-RAM also does not work reliably.  It seems to work 4 out of 5 times, but what good is unreliable resume, right?  I'm not certain if this is related to the 2.6.39-0 kernel upgrade I did, or if the stock 2.6.38 kernel exhibits the same problem.  It seems like others have gotten suspend/resume to work reliably, and I don't know yet what the difference is.

Meanwhile, the NVidia graphics seem to be poorly supported for this machine at the present time.  I'm actually using the proprietary nvidia driver at the present time (as I type), and the graphics are beautiful, however I had to boot with the "acpi=off" kernel parameter to get the machine to boot with either the nouveau or proprietary nvidia driver.  Otherwise, with the proprietary driver the machine hangs at boot.  With the nouveau it boots and runs well for about an hour at a time, and then hangs without warning.

The main problem with running without ACPI is that the kernel disables the multi-core CPU and drops the machine down to a single core.  Very, very sad considering this is a quad core with hyperthreading.  Regardless, even with a single core this thing runs way better than my old W500, so I've been limping along for now in single core mode when I use the dock with my dual monitor setup at work (dual DVI off the dock requires the NVidia graphics chip).  If I am at home and just using it as a laptop without external monitors I use the integrated graphics and the machine properly reports in /proc/cpuinfo as having all 8 cores (due to the hyperthreading).  But the integrated graphics only supports the built-in LCD and the external VGA connector, no DVI/Displayport.

I'm still searching for a better way to configure the machine to get the NVidia graphics without disabling ACPI and dropping the machine to a single core.  Ubuntu 11.04 ships with the proprietary NVidia driver version 270.41.19, and NVidia already has a 275.x.x release, so I may try upgrading the driver to see if the ACPI conflict is solved.  Otherwise, I might try the 2.6.39-1 kernel, but I'll probably be waiting for a new 3.0.0 kernel and/or Ubuntu 11.10 to see if these problems get fixed.

All that said, the W520 is WICKED fast when all 8 cores are enabled, and the NVidia graphics are beautiful with the desktop effects.  I just haven't figured out how to get both at the same time yet.

The machine also runs very cool, especially compared to my W500.  My dual-core W500 would easily reach the 95 degrees C throttling temperature even with the integrated graphics when running a heavy workload, and with the ATI graphics it would practically melt down (I had numerous thermal shutdowns running ATI graphics).  With the integrated graphics, the W520 idles at 35 to 40 C and barely cracks 60 C with two simultaneous compute jobs.  With the NVidia graphics using nouveau driver I have seen it hit 80 C, but that's it.  I think the proprietary nvidia driver runs cooler than nouveau, but I can't measure the temp because I can't boot it without turning off ACPI.

Plus, did I mention that it's fast?  When I run a single job on the W520, the job completes about 10% to 15% faster than on one of our big bad Xeon X5570 servers.  I have run 8 jobs simultaneously, and it's still pretty respectable running each job as long as you're not hitting the disk too often.

I look forward to better kernel and driver support in the coming months.

---

### Post by gatman3 on 2011-06-24
Update on my experiences...

64-bit is a no go, at least for me.  I tried 10.10 and 11.04.  10.10 was a total disaster; the machine would sometimes hang on boot, and sometimes ran at an incredibly slow speed (move the mouse, wait 30 seconds, etc.)  11.04 ran better at 64-bit, but the best I could get was to run with NVidia proprietary graphics with a kernel update (2.6.39-0) and disabling ACPI as a kernel boot option (acpi=off).  With intel graphics it worked better but it seemed sluggish at times and suspend was flaky.  There were various other problems, such as broken VMWare due to the 2.6.39-0 kernel.

When I switched to 32-bit on 11.04 the storm clouds parted and everything just worked.  Fortunately, 32-bit uses a PAE kernel that makes use of >4GB RAM (I have 8 GB, and all of the memory is available).  When I'm docked I used the NVidia proprietary driver with a dual-monitor display, and when I'm undocked I switch to the integrated (Intel) graphics (I have a boot script to auto-detect which graphics chip is present and auto-switch the xorg.conf, because intel barfs if the nvidia xorg.conf is present, and nvidia needs its own xorg.conf).  With the integrated graphics, suspend also seems to work fine now too, I was successful testing 10 out of 10 suspend cycles.

For me, at least, the 32-bit version of Ubuntu 11.04 is golden on this machine.  The 64-bit versions of Ubuntu are a mess on this machine.

---

### Post by wolfindersteppe on 2011-07-01
> **gatman3 said:**
> Update on my experiences...

64-bit is a no go, at least for me.  I tried 10.10 and 11.04.  10.10 was a total disaster; the machine would sometimes hang on boot, and sometimes ran at an incredibly slow speed (move the mouse, wait 30 seconds, etc.)  11.04 ran better at 64-bit, but the best I could get was to run with NVidia proprietary graphics with a kernel update (2.6.39-0) and disabling ACPI as a kernel boot option (acpi=off).  With intel graphics it worked better but it seemed sluggish at times and suspend was flaky.  There were various other problems, such as broken VMWare due to the 2.6.39-0 kernel.

When I switched to 32-bit on 11.04 the storm clouds parted and everything just worked.  Fortunately, 32-bit uses a PAE kernel that makes use of >4GB RAM (I have 8 GB, and all of the memory is available).  When I'm docked I used the NVidia proprietary driver with a dual-monitor display, and when I'm undocked I switch to the integrated (Intel) graphics (I have a boot script to auto-detect which graphics chip is present and auto-switch the xorg.conf, because intel barfs if the nvidia xorg.conf is present, and nvidia needs its own xorg.conf).  With the integrated graphics, suspend also seems to work fine now too, I was successful testing 10 out of 10 suspend cycles.

For me, at least, the 32-bit version of Ubuntu 11.04 is golden on this machine.  The 64-bit versions of Ubuntu are a mess on this machine.

Dear gatman3, are you able now to boot the Ubuntu 11.04 32-bit with discrete graphic running undocked and on battery?

---

### Post by gatman3 on 2011-07-01
> **wolfindersteppe said:**
> Dear gatman3, are you able now to boot the Ubuntu 11.04 32-bit with discrete graphic running undocked and on battery?

wolfindersteppe, yes I have done that, and yes it worked for me with 11.04 32-bit selecting "Discrete Graphics" in the BIOS.  But I only tried it one time a few days ago just to see if it would work, and it did.  I also tried one suspend/resume cycle, and that also worked, but I certainly didn't test it exhaustively.

When I booted undocked with Discrete graphics, my fonts were oversized for some reason -- kind of like X made a bad dpi choice without the monitors attached.  But that may also have something to do with my xorg.conf file.  I didn't mess with it, but I'm sure with some fiddling that could be solved.  I just let it boot with same xorg.conf I use for the dual monitors even though I wasn't docked and connected to any monitors, and it actually came up and used the LCD screen and set the resolution properly (1920x1080) but the fonts were kind of big.  It might have just solved itself if I ran the nvidia-xconfig utility and reconfigured everything for the LCD, I don't know for sure.

My recollection is that after about 5 minutes of operation it reported about 3 1/2 hours of remaining battery when running with the Discrete graphics.  When I run with integrated graphics it shows about 5 1/2 hours.  I have the 9-cell battery and the i7-2720QM CPU with a 500 GB mechanical hard drive, and I usually run the display about one tick lower than full brightness.

EDIT: FYI, I have not tried the open-source nouveau driver undocked on battery, just the proprietary nvidia driver.

---

### Post by wolfindersteppe on 2011-07-02
gatman3 - thank you, thank you, thank you very much for pointing out to Ubuntu 11.04 32-bit version!!!
I have performed extensive tests in any combination of W520 (i7-2820QM, 16 GB RAM, NVidia 2000M, Vertex3 240 SSD for OS, 2nd Vertex3 Pro 240 GB SSD in caddy) running docked, undocked, on battery, with GPU integrated only, discrete only and optimus. My conclusion so far:
- boot on battery works in any GPU combination - optimus, integrated only, dedicated only;
- 16 GB RAM (aka 15.7 usable) is fully recognized and usable - tested running several VMWARE virtual machines up to maximum RAM available, 
- suspend works in any given combination, heavily running virtual machines, flash, UMTS, wireless and then suspending docked, undocking, opening lid and resuming it or running on battery, suspending, putting in dock,resuming etc - works any time, extremely charming;
- if mouse focus was on external monitor, then suspended, detached second monitor and W520 resumed, it looks first that W520 is not resumed but actually it is, only the login screen is on the "invisible" external monitor, just typing blind the pwd brings the GUI back;
- hibernation does not work, but having SSD 6.0GBs/s it does not bothering me, the shut down / start / reboot is fast enough - who needs hibernation in case of SSD :D;
- once I have experienced external mouse cursor movement being extremely lagged after suspending on battery and discrete GPU (aka NVidia) and then resuming in the dock station but restarting the X server cured it.

Now I am going to backup my current installation before doing anything else. Next step is to test the Optimus support for Linux, have to install bumblebee [https://github.com/MrMEEE/bumblebee]("https://github.com/MrMEEE/bumblebee"). And tonight I will enjoy the box fight Klitscho vs. Haye ;)

---

### Post by dimm0k on 2011-07-02
Finally some W520 owners running Linux!  While Ubuntu is not my Linux distribution of choice, I find the Ubuntu community to be very helpful!

While my experience with this notebook and Linux is far from perfect, perhaps I may be able to shed some light on my dealings with this machine, as well as obtain some knowledge on this particular machine and Linux in general.  My distribution is Slackware 64-bit 13.37 and I'm currently running kernel 2.6.39.2 and BIOS 1.22.  I mention the BIOS version because it seems that BIOS 1.24/25 that this machine came with had some issues with Linux and ACPI.  Unfortunately I do not recall the specific nature of these ACPI issues, but it forced me to downgrade to 1.22.  I am also running the latest "stable" NVIDIA drivers, 275.09.07.  Haven't had any problems with 64-bit and NVIDIA's drivers other than what looked like compiz dying just now on me, forcing me to restart KDE.

I have tried putting the machine to sleep a total of 5 times consecutively, with all 5 times resuming successful.  Hibernation has been a little spotty for me however, as I am able to put the machine into hibernate and successfully resume maybe 2 out of 3 times.

In Windows 7 I have seen the CPU GHz go from 2.2 to a max of maybe 3.1GHz.  Under Linux however, I have never seen it go past 2.2GHz.  Not sure what's up there...

I am also having some difficulties reading CPU temps and suspect it's a combo between the BIOS and the Linux kernel.  Under BIOS 1.06 the CPU temps are all available for reading.  Under 1.22 and higher, I get only one reading and I'm not even sure if it's accurate or what it's actually reading from.

Lastly, I have tried Ubuntu 11.04 64-bit off of a Live CD to verify my findings with the CPU temps and during this time period I did not have any issues with Ubuntu.

---

### Post by gatman3 on 2011-07-05
dimm0k, welcome!

Interesting comments about BIOS version and ACPI.  I'm pretty sure I was running BIOS 1.22 when I had all those problems with Ubuntu 11.04 64-bit with Discrete graphics, although it might have been BIOS 1.21.  I'm not real motivated to mess with it any more at this point because things are running so well with 11.04 32-bit.

I have also noticed that the CPU frequency as reported in /proc/cpuinfo never exceeds 2.2 GHz, while Intel's "Turbo Boost" feature is supposed to allow my i7-2720QM to hit 3.3 GHz if only one core is under load.

I did a little research and found these links:

[http://ubuntuforums.org/showthread.php?t=1321028]("http://ubuntuforums.org/showthread.php?t=1321028")
[http://saveandrewgarib.com/201004/articles/767-dellie_iii_linux_and_turbo_boost]("http://saveandrewgarib.com/201004/articles/767-dellie_iii_linux_and_turbo_boost")

These articles suggest that (1) kernels newer than around 2.6.33 or so have Turbo Boost support, but (2) The Turbo Boost core speeds are not reported properly in /proc/cpuinfo, and you need to run a special Intel utility called "turbostat" to see the true core speed with Turbo Boost.

Intel's turbostat utility is included in the acpidump package:

```
sudo apt-get install acpidump
```

If you run turbostat in a terminal:

```
sudo turbostat
```

It displays something like this:

```
 CPU   GHz    TSC 
 avg   0.80   2.19
   0   0.80   2.19
   1   0.80   2.19
   2   0.80   2.19
   3   0.80   2.19

```

and updates every few seconds.

This is as far as I have gotten, though.  I still do not see any of the cores crank up to 3.3 GHz under load.  Still researching...

---

### Post by gatman3 on 2011-07-05
I also found the i7z utility for reporting CPU speed, apparently including Turbo Boost speed:

[http://code.google.com/p/i7z/]("http://code.google.com/p/i7z/")

(You'll need to install libncurses5-dev from the repository before making this).

This tool seems to work great.  Here is sample output:

```
Cpu speed from cpuinfo 2192.00Mhz                                                                                                                                                                       
cpuinfo might be wrong if cpufreq is enabled. To guess correctly try estimating via tsc                                                                                                                 
Linux's inbuilt cpu_khz code emulated now                                                                                                                                                               
True Frequency (without accounting Turbo) 2192 MHz                                                                                                                                                      
  CPU Multiplier 22x || Bus clock frequency (BCLK) 99.64 MHz                                                                                                                                            
                                                                                                                                                                                                        
Socket [0] - [physical cores=4, logical cores=8, max online cores ever=4]                                                                                                                               
  TURBO ENABLED on 4 Cores, Hyper Threading ON                                                                                                                                                          
  True Frequency 2291.64 MHz (99.64 x [23])                                                                                                                                                             
  Max TURBO Multiplier (if Enabled) with 1/2/3/4 Cores is  33x/32x/30x/30x                                                                                                                              
  Current Frequency 2192.35 MHz (Max of below)                                                                                                                                                          
        Core [core-id]  :Actual Freq (Mult.)      C0%   Halt(C1)%  C3 %   C6 %  Temp                                                                                                                    
        Core 1 [0]:       2192.07 (22.00x)      8.44    84.4    6.13       1    309                                                                                                                     
        Core 2 [2]:       2192.35 (22.00x)         1    98.7       1       0    308                                                                                                                     
        Core 3 [4]:       2191.95 (22.00x)      1.39      96    1.58       1    306                                                                                                                     
        Core 4 [6]:       2192.00 (22.00x)       100       0       0       0    311                                                                                                                     
                                                                                                                                                                                                        
                                                                                                                                                                                                        
                                                                                                                                                                                                        
C0 = Processor running without halting                                                                                                                                                                  
C1 = Processor running with halts (States >C0 are power saver)                                                                                                                                          
C3 = Cores running with PLL turned off and core cache turned off                                                                                                                                        
C6 = Everything in C3 + core state saved to last level cache                                                                                                                                            
  Above values in table are in percentage over the last 1 sec                                                                                                                                           
[core-id] refers to core-id number in /proc/cpuinfo                                                                                                                                                     
'Garbage Values' message printed when garbage values are read                                                                                                                                           
  Ctrl+C to exit
```

It shows that the max CPU speed is 33x of 100 MHz, which should be 3.3 GHz.  However, I still never see the speed crack 2.2 GHz under load.

One other interesting quirk:  I had disabled hyper-threading in the BIOS because I was seeing some undesirable behavior when running multiple compute jobs simultaneously (sometimes the jobs would get 50% of a CPU instead of 100%, even with 4 or fewer jobs running).  With hyper-threading disabled all cores were always running 2.2 GHz and never throttling down with no load.  With hyper-threading enabled, each core tends to run in the 800-1600 MHz range when not under load, and then with one compute job running all cores crank up to 2.2 GHz, even the ones not under load.  Weird.

Still, I never see any more than 2.2 GHz on any one core.

Seems like maybe proper Sandy Bridge support is lacking in the 2.6.38-8 kernel?

---

### Post by dimm0k on 2011-07-06
Looks like Lenovo has released "unofficially" 1.26 for the BIOS, which I have yet to try or hear anyone trying yet.  I'm probably going to give it a shot later this week, hoping to hear from others before doing so.

Funny because right after my previous post I actually read the same thing that Turbo Boost does work, it's that most things that read these readings aren't capable of determining Turbo Boost.  Another program you can try to check is Intel's powertop utility.  That actually just states Turbo Boost is used, but not the actual frequency.

I'm going to have to read up on hyper-threading myself.  I thought I read somewhere that hyper-threading behaves that way...

---

### Post by gatman3 on 2011-07-06
dimm0k, thanks a ton for sharing the info about BIOS 1.26.  After I read the release notes which list this fix:

> - Fixed an issue where the Turbo Boost function did not work on some processors
  when working by the AC adapter.

...then I couldn't help but try the BIOS update even though it's only a pre-release.

And....... SUCCESS!!!  Turbo Boost is working now!  I am finally seeing CPU frequencies up to 3.3 GHz on my i7-2720QM, as reported by the i7z utility.

Here are the links to the BIOS version 1.26, since they are not listed on Lenovo's support page:

[http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles/8buj06uc.iso](http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles/8buj06uc.iso)
[http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles/8buj06us.exe](http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles/8buj06us.exe)
[http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles/8buj06us.txt](http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles/8buj06us.txt)

As always, proceed at your own risk with BIOS updates.

Here is a comparative benchmark of a short but fairly intense verilog simulation running on a single core:

```
            Xeon X5570 @ 2.9 GHz ----- 578 seconds
Lenovo W520, i7-2720QM @ 2.2 GHz ----- 445 seconds (no Turbo Boost, BIOS 1.25)
Lenovo W520, i7-2720QM @ 3.3 GHz ----- 331 seconds (w/ Turbo Boost, BIOS 1.26) 
```

That result pretty much says it all.

Interestingly, when running this simulation I saw all four cores crank up over 3 GHz at times (even though the Cadence simulator I am using only utilizes a single core), but I also never saw the CPU temp get over 65 C.  Compared to my old W500 which would routinely throttle the CPU because the temperature would hit 95 C under load, this W520 seems to have excellent thermals.

---

### Post by dimm0k on 2011-07-06
Looks like wonderful news!  I'm gonna have to fast forward and update the BIOS now!  Hopefully I make it through this terrifying process of updating the BIOS...

EDIT: looks like I made it!  Process on the Thinkpads are still the scariest thing I have ever experienced in all my years of computing!  Weirdest thing for me before and after updating the BIOS.  I wanted to turn off the passwords and set the DVD to boot, but no matter how many times I pressed the F1 key it would not enter until I turned off the machine and then tried it.  Even tried pressing F12, but it just kept going to my boot loader.

Off to test this new BIOS!

---

### Post by gatman3 on 2011-07-06
dimm0k - you're right about the BIOS update being scary.  They could really use a progress bar.  Plus, that message after the update completes is hilarious - they tell you that you can (1) leave the CD in and reboot, and then get back into the BIOS update utility, and then remove the CD and reboot again, or you can (2) remove the CD and reboot.  Hilarious.

I have had some trouble entering the BIOS config on occasion too.  It's not like my older W500.  It seems like with the W520 you almost have to hold F1 down either right when the splash screen comes on, or maybe even slightly before that.

I have also noticed that the new BIOS allows the machine to crank up the processor to 3+ GHz even when running on battery.  Previously I could only get 800 MHz on battery, and the machine was really noticeably pretty slow.

Anyhow, enjoy the Turbo Boost, and thanks again for sharing the info on the BIOS 1.26 pre-release.  How often does a BIOS update come through that gives you 50% higher performance?  Excellent!

---

### Post by VValdo on 2011-07-07
Hey y'all...

Just found this thread.  I've had the w520 and been runing ubuntu w/integrated driver.  You can read my progress (it's rock solid now w/3.0rc5 kernel) on this [420 thread]("http://ubuntuforums.org/showthread.php?t=1748475"), including some info that might be of interest to people.

Anyway, since this thread exists I'm gonna stop updating to that one.... and off to try the new BIOS and I'm guessing an rc6 will be out if it's not already.

---

### Post by gatman3 on 2011-07-07
VValdo, thanks for pointing us to the other thread.  Sounds like there are others out there who are struggling with the recent 64-bit Ubuntu releases on both the W520 and the T420.  I'm glad to hear that you're having success with the 3.0rc5 kernel.  I'm not quite ready to go there yet myself, as 11.04 with the 32-bit 2.6.38-8 PAE kernel is working great for me right now with both nvidia (docked mode at the office for me) and intel graphics (standalone mode at home).

Good luck with the BIOS update.  Do you have an i7-2720QM ?  It's not really clear from the Lenovo readme for the 1.26 BIOS, but in the Lenovo users group thread on this topic I think someone said that the Turbo Boost problem only affected the i7-2720QM.  You might check your CPU performance with one of the previously mentioned utilities before upgrading the BIOS.  In any case, good luck, and keep us posted on other successes with 3.0rc6, etc.

---

### Post by VValdo on 2011-07-07
Well I almost had a heart attack as the BIOS update froze midway...  it only got one of the two firmware updates.  I think the CD may have been bad.  A subsequent try with a DVD worked fine.

So here I am back in ubuntu with my amd64 11.04 and downloading the rc6 kernel.  I don't know if there' sany differences.. my CPU is an i7-2820QM.   FWIW I have gkrellm up and it looks quieter than I remember it being.. sometimes it seemed the various cores would be up and running and doing god-knows-what...  now they seem calm...  temps are hovering around 47.  single fan at about 1980RPM and I'm doing an Android repo sync in the background.

I'll let you know how r6 goes.. but so far so good.  my freezing issue from 29 is gone.. I'm going to try to build android as well and see if I get hte same weird heat warnings in the logs (although temps don't exceed 75C or so...)

But yeah for anyone followin ghtis thread might as well jump to the other one I linked to above to see if there's anything to be gleaned there...

Update:  So I decided to build Android just to see how it goes.  Built nice and fast (not a fresh "make clobber", so I can't really make a fair comparison to previous builds...)  But anyway, as before I got these errors in the log:
> 
Jul  7 00:23:48 laptop kernel: [ 1498.128053] [Hardware Error]: Machine check events logged
Jul  7 00:24:39 laptop kernel: [ 1549.154449] CPU3: Package power limit notification (total events = 1282)
Jul  7 00:24:39 laptop kernel: [ 1549.154453] CPU2: Package power limit notification (total events = 1282)
Jul  7 00:24:39 laptop kernel: [ 1549.154457] CPU0: Package power limit notification (total events = 1282)
Jul  7 00:24:39 laptop kernel: [ 1549.154461] CPU1: Package power limit notification (total events = 1282)
Jul  7 00:24:39 laptop kernel: [ 1549.154465] CPU7: Package power limit notification (total events = 1282)
Jul  7 00:24:39 laptop kernel: [ 1549.154468] CPU6: Package power limit notification (total events = 1282)
Jul  7 00:24:39 laptop kernel: [ 1549.154472] CPU5: Package power limit notification (total events = 1282)
Jul  7 00:24:39 laptop kernel: [ 1549.154476] CPU4: Package power limit notification (total events = 1282)
Jul  7 00:24:39 laptop kernel: [ 1549.154566] CPU1: Package power limit normal
Jul  7 00:24:39 laptop kernel: [ 1549.154568] CPU0: Package power limit normal
Jul  7 00:24:39 laptop kernel: [ 1549.154571] CPU4: Package power limit normal
Jul  7 00:24:39 laptop kernel: [ 1549.154573] CPU3: Package power limit normal
Jul  7 00:24:39 laptop kernel: [ 1549.154575] CPU2: Package power limit normal
Jul  7 00:24:39 laptop kernel: [ 1549.154578] CPU6: Package power limit normal
Jul  7 00:24:39 laptop kernel: [ 1549.154580] CPU7: Package power limit normal
Jul  7 00:24:39 laptop kernel: [ 1549.154582] CPU5: Package power limit normal

And then mcelog gave me some more detail:

> HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 24
CPU 0 THERMAL EVENT TSC 3468dd9f36e 
TIME 1310023749 Thu Jul  7 00:29:09 2011
Processor 0 below trip temperature. Throttling disabled
STATUS c000000088190800 MCGSTATUS 0
MCGCAP c09 APICID 0 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
mcelog: Unsupported new Family 6 Model 2a CPU: only decoding architectural errors
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 25
CPU 4 THERMAL EVENT TSC 3468dda0bfb 
TIME 1310023749 Thu Jul  7 00:29:09 2011
Processor 4 below trip temperature. Throttling disabled
STATUS c000000088190800 MCGSTATUS 0
MCGCAP c09 APICID 4 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
mcelog: Unsupported new Family 6 Model 2a CPU: only decoding architectural errors
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 26
CPU 3 THERMAL EVENT TSC 3468dda242f 
TIME 1310023749 Thu Jul  7 00:29:09 2011
Processor 3 below trip temperature. Throttling disabled
STATUS c000000088190800 MCGSTATUS 0
MCGCAP c09 APICID 3 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
mcelog: Unsupported new Family 6 Model 2a CPU: only decoding architectural errors
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 27
CPU 2 THERMAL EVENT TSC 3468dda355a 
TIME 1310023749 Thu Jul  7 00:29:09 2011
Processor 2 below trip temperature. Throttling disabled
STATUS c000000088190800 MCGSTATUS 0
MCGCAP c09 APICID 2 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
mcelog: Unsupported new Family 6 Model 2a CPU: only decoding architectural errors
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 28
CPU 6 THERMAL EVENT TSC 3468dda4d41 
TIME 1310023749 Thu Jul  7 00:29:09 2011
Processor 6 below trip temperature. Throttling disabled
STATUS c000000088190800 MCGSTATUS 0
MCGCAP c09 APICID 6 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
mcelog: Unsupported new Family 6 Model 2a CPU: only decoding architectural errors
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 29
CPU 7 THERMAL EVENT TSC 3468dda5e63 
TIME 1310023749 Thu Jul  7 00:29:09 2011
Processor 7 below trip temperature. Throttling disabled
STATUS c000000088190800 MCGSTATUS 0
MCGCAP c09 APICID 7 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
mcelog: Unsupported new Family 6 Model 2a CPU: only decoding architectural errors
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 30
CPU 5 THERMAL EVENT TSC 3468dda7495 
TIME 1310023749 Thu Jul  7 00:29:09 2011
Processor 5 below trip temperature. Throttling disabled
STATUS c000000088190800 MCGSTATUS 0
MCGCAP c09 APICID 5 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42
mcelog: Unsupported new Family 6 Model 2a CPU: only decoding architectural errors
HARDWARE ERROR. This is *NOT* a software problem!
Please contact your hardware vendor
MCE 31
CPU 1 THERMAL EVENT TSC 3468dda8087 
TIME 1310023749 Thu Jul  7 00:29:09 2011
Processor 1 below trip temperature. Throttling disabled
STATUS c000000088190800 MCGSTATUS 0
MCGCAP c09 APICID 1 SOCKETID 0 
CPUID Vendor Intel Family 6 Model 42


I do think these are BS, but I'd still like to verify that others are seeing it too.  Gotta be doing something like building something to see it.

---

### Post by dimm0k on 2011-07-07
> **gatman3 said:**
> dimm0k - you're right about the BIOS update being scary.  They could really use a progress bar.  Plus, that message after the update completes is hilarious - they tell you that you can (1) leave the CD in and reboot, and then get back into the BIOS update utility, and then remove the CD and reboot again, or you can (2) remove the CD and reboot.  Hilarious.

I have had some trouble entering the BIOS config on occasion too.  It's not like my older W500.  It seems like with the W520 you almost have to hold F1 down either right when the splash screen comes on, or maybe even slightly before that.

I have also noticed that the new BIOS allows the machine to crank up the processor to 3+ GHz even when running on battery.  Previously I could only get 800 MHz on battery, and the machine was really noticeably pretty slow.

Anyhow, enjoy the Turbo Boost, and thanks again for sharing the info on the BIOS 1.26 pre-release.  How often does a BIOS update come through that gives you 50% higher performance?  Excellent!

A progress bar would be indeed nice, as it would show some signs of life during the sections where it looks like the machine froze.  Quite frightening during those stages.  Hah, that final message after the update is done is quite funny.  I had to read it twice to understand if it was a typo or if it really meant I had two options for a successful update process.

Well it may not be on Lenovo's site yet, but it looks like it's public now according to a Lenovo staff here [http://forums.lenovo.com/t5/W-Series-ThinkPad-Laptops/W520-TurboBOOST-not-working-on-battery-or-after-updates/m-p/475083#M16528](http://forums.lenovo.com/t5/W-Series-ThinkPad-Laptops/W520-TurboBOOST-not-working-on-battery-or-after-updates/m-p/475083#M16528)

I did a little more testing on the entering BIOS issue and it seems if you press the F1 key right when the message to do so pops up AND you hear a beep then it should take you to the BIOS.  Doing that a few times I was able to get in each time.  Will try it some more later tonight.

Interesting you're able to see the speed crank up to 3GHz while on battery.  While I have yet to try that, the release notes for the BIOS say it should not hit Turbo Boost while on battery.

The fan definitely sounds quieter, however I haven't looked much into the overall temps with this new BIOS.  Not even sure if the readings in Linux are reporting the right temps even before this update.

---

### Post by gatman3 on 2011-07-07
dimm0k, thanks for the link to the Lenovo thread on Turbo Boost.  I hadn't seen that before.  I didn't even realize that Turbo Boost had been working on BIOS < 1.25.  I guess in reality I broke it almost immediately after I got the machine when I upgraded the BIOS to 1.25.

Sounds like some of the people on that thread are still having trouble even after the 1.26 update.  So it goes when rushing out a brand new platform.  I foresee at least monthly updates for a while until they sort out all their problems.


vvaldo, scary story about your update.  Glad to hear it turned out OK in the end.  I bet you were sweating a little when it froze.

You may have also inadvertently proven that Lenovo actually has a pretty safe BIOS flash procedure.  As it should be.  If they do this the way we do it for our chips (I'm a SOC chip designer in my day job) they should be actually keeping two copies of the BIOS in flash memory - one which is the last known good version, and one which is the new version being flashed.  After flashing the new version to a different region in flash and checking its CRC, they should update the boot loader in one critical, atomic operation to point to the new image.  There's lots of ways to do that, but that's probably what they're doing on the first reboot after running the BIOS upgrade utility when the message flashes at the bottom of the Lenovo splash screen about updating the embedded controller.  Depending on how they do that, it's either done in a fairly safe, atomic way (i.e. "brick proof")... or they don't, and then that's the REAL critical time when you don't want to lose power.  But the point is to minimize as much as possible the amount of time when a power loss will brick the machine.

Either way, if anyone ever does brick their machine after a BIOS update, I would just call up Lenovo and tell them that you had a power loss during BIOS update and bricked your machine.  Almost certainly they'll repair or replace it without charge.  Not that it wouldn't suck to be down for a week or two.

---

### Post by VValdo on 2011-07-07
Yeah it was scary, esp since I hadn't done this before on a PC.  after 45 minutes of flashing for "several minutes" I figured something serious was wrong :)

It was locked in the "Still Updating..." phase, and I hoped it followed some kind of modern filesystem-like method of writing and then not activating the write until it was 100% sure it had gotten it right.  I hit power, and when it came back up i saw that the firmware was up to 1.26 but the embedded controller was only at 1.14 and not 1.16 (these #s are from memory but I think it's right).

So I redownloaded the fw, verified the md5sum, burned to a new DVD and tried again.  This time after about 2 minutes it came up with that strange reboot message ("either take out the CD now, or take out the CD later") and for the first time it did the embedded controller file on reboot...

so now I'm good, but yeah... scary.  I should probably throw these batch of CDs away.. or at least not use 'em for anything as critical as this...

So far btw everything seems to be good, aside from the kernel temp warnings when I did the compiling.  I also did notice slightly higher temps when cores are maxed out-- 75C was the previous high and it was getting up to 80 with fan at ~4000rpm.  I don't know if this is due to new anything or maybe it's just the summer and hotter overall, but figured I'd mention it in case anyone's comparing notes.

3.0RC6 too.  And up next is bumblebee!

---

### Post by dimm0k on 2011-07-07
@VValdo, first of thanks for that link to the other thread.  It provided me with some tidbits of info that will come in handy for the W520.  I had put together some info at work, but forgot to email it to myself when I left. (it's been a crazy day!)  Anyway you mentioned sensor readings were available at /sys/devices/platform/coretemp.?/temp1_input.  Any idea where those are created from?  I'm not seeing anything related to core temps under /sys/devices/platform and I'm running kernel 2.6.39.2.

also glad to hear that you made it out alive from the BIOS update.  When I got the W510, it had just come out so replacement parts required some wait to get them even for the service centers.  Needless to say I had to get my mainboard replaced, not once, but twice!  Both due to BIOS updates!!  Looks like from your dealing that Lenovo has made their BIOS updating process a little safer...  though until I hear of HOW their updating process is safer, I think there will always be fear when I update a Thinkpad.

I believe my kernel is compiled to warn me of thermal overheating, I was not able to replicate the messages you described in the other thread.  While I wasn't compiling a kernel I did run linpack64, which is supposed to be a great system stresser and none of those messages populated my /var/log/messages.

@gatman3, With linpack64, I was able to push my system to use Turbo Boost cranking all 8 threads on the CPU.  With the AC adapter Turbo Boost was in play.  When I unplugged the AC adapter to run on battery, the CPU speed dropped to 1.5GHz and stayed there all the while cranking on all 8 threads.  I have the i2720QM CPU just like you...  and you were definitely able to get over 3GHz while on battery?

---

### Post by VValdo on 2011-07-08
> **dimm0k said:**
> @VValdo, first of thanks for that link to the other thread.  It provided me with some tidbits of info that will come in handy for the W520.  I had put together some info at work, but forgot to email it to myself when I left. (it's been a crazy day!)  Anyway you mentioned sensor readings were available at /sys/devices/platform/coretemp.?/temp1_input.  Any idea where those are created from?  I'm not seeing anything related to core temps under /sys/devices/platform and I'm running kernel 2.6.39.2.

did you install lm-sensors and do you have coretemp in /etc/modules?

if you have, try running "sensors-detect" and answer yes to everything.

> I believe my kernel is compiled to warn me of thermal overheating, I was not able to replicate the messages you described in the other thread. While I wasn't compiling a kernel I did run linpack64, which is supposed to be a great system stresser and none of those messages populated my /var/log/messages.

Hmm.  I don't know what's going on then, then.  I hope it's not REALLY overheating.  I ran the mprime torture test for 1/2 hour without any errors.  I guess I'll try again now...  you built your own kernel or this is from ubuntu's PPA?

Update:  After 1 hour 45 minutes... no problems with mprime.  I haven't tried i7z yet, but that's mostly cuz I don't want to install subversion :/

---

### Post by gatman3 on 2011-07-08
> **dimm0k said:**
> @gatman3, With linpack64, I was able to push my system to use Turbo Boost cranking all 8 threads on the CPU.  With the AC adapter Turbo Boost was in play.  When I unplugged the AC adapter to run on battery, the CPU speed dropped to 1.5GHz and stayed there all the while cranking on all 8 threads.  I have the i2720QM CPU just like you...  and you were definitely able to get over 3GHz while on battery?

So, I just played with it some more and got some very odd results.  I suspect there is a bug in BIOS 1.26.

When I boot with the AC adapter plugged in, I see no difference in CPU Turbo Boost speed reported by i7z when I run a heavy load (single thread) either with or without the AC adapter plugged in.  Whether plugged in or on battery I can still get all cores up over 3 GHz.  When I unplug the AC adapter, I do see a momentary drop down into the low 1 GHz range, and then back up to 3+ GHz.

I attached a screen shot of the i7z output showing over 3 GHz operation while on battery.

But... and here's the weird thing... if I boot on battery I see odd, backwards behavior.  After I boot on battery I can still hit 3+ GHz while I'm running on battery, but when I plug in the AC adapter I see the speed drop down to 800 MHz on all cores.  Totally backwards, but it's very repeatable.

Must be a bug in the 1.26 BIOS.

FYI, here's my kernel version on Ubuntu 11.04:

```
Linux 2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686 i686 i386 GNU/Linux

```

EDIT:  Note that this occurred with integrated graphics.  I wonder if there isn't different behavior with discrete graphics due to power draw considerations.  I'll experiment when I get some time.

---

### Post by dimm0k on 2011-07-08
@VValdo, lm-sensors should be installed, however I don't think coretemp is, which might explain things.  I know when I ran "sensors-detect" previously it could not find anything despite answering Y to all.  Will check on the coretemp module when I get home.

@gatman3, interesting that you get speeds in the Turbo Boost range while on battery.  In your BIOS settings, did you set everything to Max Performance even when on battery?

---

### Post by wolfindersteppe on 2011-07-08
Dear Ubuntu W520 owners, sadly but true - Ubuntu 11.04, regardless of 32-bit or 64-bit is No-No for the fastest laptop on the world, see [http://www.phoronix.com/scan.php?page=article&item=intel_snb_natty&num=1]("http://www.phoronix.com/scan.php?page=article&item=intel_snb_natty&num=1"). 
32-bit PAE is also No-Go for me, W7 beats Ubuntu 11.04, unfortunately. I will report more on weekend, plan to upgrade kernel to 3.x...

---

### Post by VValdo on 2011-07-08
> **wolfindersteppe said:**
> Dear Ubuntu W520 owners, sadly but true - Ubuntu 11.04, regardless of 32-bit or 64-bit is No-No for the fastest laptop on the world, see [http://www.phoronix.com/scan.php?page=article&item=intel_snb_natty&num=1]("http://www.phoronix.com/scan.php?page=article&item=intel_snb_natty&num=1"). 
32-bit PAE is also No-Go for me, W7 beats Ubuntu 11.04, unfortunately. I will report more on weekend, plan to upgrade kernel to 3.x...

Hmmm.  Old article is old.  The hangcheck bug is fixed as of 2.6.39 (there is a workaround for .38).  I haven't had problems with missing fonts or anything as described in the May story.  But I will say that in the last 3 weeks i've had this machien it's gone from having a ton of issues to being rock-solid...  Although I did have to get new versions of things... and there is always room for improvement... and when i say the above I have my fingers firmly crossed and my wood fully knocked.. (hmm that doesn't sound exactly right..)

But things aren't as bad two months later as that article implies...

/just sayin'.

---

### Post by dimm0k on 2011-07-09
Thanks VValdo!  The coretemp module was exactly what I was missing!  Also I just compiled the latest 2.6.39 kernel, 2.6.39.3, and still no messages like you've seen in /var/log/messages.  Temps hovered just above 91 degrees during this process however!

---

### Post by VValdo on 2011-07-09
Glad it's working.. which CPU are you using?  Maybe that's related to the error reports I'm seeing...

---

### Post by dimm0k on 2011-07-09
> **VValdo said:**
> Glad it's working.. which CPU are you using?  Maybe that's related to the error reports I'm seeing...

I have the i7-2720QM CPU and kernel 2.6.39.2...

---

### Post by VValdo on 2011-07-09
Ah I'm using i7-2820QM w:

Linux laptop 3.0.0-0300rc6-generic #201107050905 SMP Tue Jul 5 09:08:58 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Wonder from anyone else w/this or a similar setup-- are you seeing thermal or other errors in the logs when cpu at full.

The hottest temp, even when maxed out, that I get is about 81C...

---

### Post by gatman3 on 2011-07-13
> **dimm0k said:**
> @gatman3, interesting that you get speeds in the Turbo Boost range while on battery.  In your BIOS settings, did you set everything to Max Performance even when on battery?

dimm0k, here are power management settings in the BIOS config:

Intel (R) SpeedStep Technology
  Mode for AC = Maximum Performance
  Mode for Battery = Battery Optimized

Adaptive Thermal Management
  Scheme for AC = Maximize Performance
  Scheme for Batter = Balanced


It seems like I have seen many other quirks with this 1.26 BIOS.  The machine also seems to run a fair amount hotter as well.  In fact, yesterday I was running two compute jobs with nvidia graphics and the temp hit about 83 or 84 C.  Just for grins, I turned on the desktop effects and started playing with the desktop cube effect, and I was able to get it all the way up to 92 C.  Now granted, when I was seeing it run in the cool 65 to 70 C range it was with the 1.25 BIOS and the CPU speed wasn't going over 2.2 GHz.

Here's another quirk:  I tried booting up with my Android phone plugged into a USB port to charge the battery, and the machine absolutely would not boot.  Wouldn't even go to the Thinkpad splash screen.  Once I unplugged the phone, everything came up normally.  All I can figure is that it was treating the phone as a mass storage device and trying to boot off it.  But why didn't it even provide the Thinkpad splash screen so I could go into the config pages?  Weird.  You'd think it would not see a MBR and give up and go to the next boot device... and do that AFTER showing the Thinkpad splash screen.

I have also seen a lot of odd behavior with the screen brightness.  I'm not sure how much of this is Ubuntu related or BIOS related, but I never saw this behavior with the same Ubuntu version on my W500.  Basically, if you close the lid while on AC and leave it closed for a long time, once you open it the screen won't return to the previous brightness level and stays very dim.

I'm sure there are other quirks, but I don't remember them all.  Maybe I'll start keeping a journal on it.  Seems like Lenovo has some issues to sort out with their BIOS development.

I have read that the 1.22 BIOS works much better.  I may consider donwgrading.

---

### Post by dimm0k on 2011-07-13
gatman3, From the looks of it and if my memory serves me correctly, you did not make any changes to any of the settings you listed and they were exactly those when you got the system?  I know with 1.26 I got a little brave and changed the battery settings you've listed from Optimized/Balanced to Max Performance.  I might switch them to what you have on the next reboot and see if that may be cause of my issues.

Well I can answer the change in temperature quirk you've mentioned.  With 1.26 they supposedly lowered the speed of the fan so you may want to tweak them with thinkfan if you want to keep 1.26.  This was done apparently to fix the problem people were getting with the fan making "pulsating" noises.  I have to admit that I heard it somewhat with BIOS 1.22, but it didn't really bother me much.  Looks like it bothered enough people to get Lenovo to "fix" this.

Which USB port are you plugging your Droid into?  Not sure how much of this holds true for the W520, but when I had my W510 certain devices would cause the system to freeze on boot if you had it connected to the USB 3.0 ports.  You might want to also check in the BIOS, as if I remember correctly there are some settings that pertain to plugging in phone devices.  Might have been something I remembered from W510's BIOS settings, but it should have made it to W520 as well.

When you close the lid in Ubuntu, I assume it's putting the system to sleep?  Not sure what would cause the screen to stay dim when you open up the lid, but it would seem that mine does the opposite.  Mine actually jumps back to the brightest setting after coming back from sleep.

1.22 worked well for me, but compared to 1.26 I think the latter is just a teensy better with the fix to the "pulsating" fan noise.  My only issue with 1.26 is that occasionally the system would get stuck at 800MHz for no apparent reason, but this also occurred with BIOS 1.22 for me.  The other issue is the CPU not being able to hit it's highest possible Speedstep when on battery.  While I would like it fixed, it's not that big of a deal to me since I rarely use battery anyway.

---

### Post by dimm0k on 2011-07-13
> **VValdo said:**
> Ah I'm using i7-2820QM w:

Linux laptop 3.0.0-0300rc6-generic #201107050905 SMP Tue Jul 5 09:08:58 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Wonder from anyone else w/this or a similar setup-- are you seeing thermal or other errors in the logs when cpu at full.

The hottest temp, even when maxed out, that I get is about 81C...

Nothing conclusive yet, but I'm beginning to believe that there are some things in the BIOS that are specific to the CPU type.  This may or may not be releated to your issues with the i7-2820QM that I don't have and vice versa.

---

### Post by gatman3 on 2011-07-14
dimm0k,

> gatman3, From the looks of it and if my memory serves me correctly, you did not make any changes to any of the settings you listed and they were exactly those when you got the system?  I know with 1.26 I got a little brave and changed the battery settings you've listed from Optimized/Balanced to Max Performance.  I might switch them to what you have on the next reboot and see if that may be cause of my issues.

Yes, I think that's right.  I did play around with the settings, but I think the ones I'm using are the defaults.

> Well I can answer the change in temperature quirk you've mentioned.  With 1.26 they supposedly lowered the speed of the fan so you may want to tweak them with thinkfan if you want to keep 1.26.  This was done apparently to fix the problem people were getting with the fan making "pulsating" noises.  I have to admit that I heard it somewhat with BIOS 1.22, but it didn't really bother me much.  Looks like it bothered enough people to get Lenovo to "fix" this.

OK, that makes sense.  I remember reading about the fan "pulsating" with 1.22.

> Which USB port are you plugging your Droid into?  Not sure how much of this holds true for the W520, but when I had my W510 certain devices would cause the system to freeze on boot if you had it connected to the USB 3.0 ports.  You might want to also check in the BIOS, as if I remember correctly there are some settings that pertain to plugging in phone devices.  Might have been something I remembered from W510's BIOS settings, but it should have made it to W520 as well.

I had the phone plugged into the USB port on the back right side of the unit.  I haven't looked at the BIOS settings tonight, but I don't remember anything about phone devices.  I'll look next time I boot. It's not that big of a deal, I just thought it was kind of odd.

> When you close the lid in Ubuntu, I assume it's putting the system to sleep?  Not sure what would cause the screen to stay dim when you open up the lid, but it would seem that mine does the opposite.  Mine actually jumps back to the brightest setting after coming back from sleep.

No, this is with the AC power attached and I am not putting the system to sleep.  I think what's happening is that the screen is timing out due to inactivity while the lid is shut and dimming the screen, as per the Ubuntu power control settings.  Then when I open the lid it's not restoring them to the previous brightness before shutting the lid.  If I just shut the lid and open it relatively quickly this doesn't happen.  Could be a Ubuntu-specific interaction, but again, it never happened on my W500.

> 1.22 worked well for me, but compared to 1.26 I think the latter is just a teensy better with the fix to the "pulsating" fan noise.  My only issue with 1.26 is that occasionally the system would get stuck at 800MHz for no apparent reason, but this also occurred with BIOS 1.22 for me.  The other issue is the CPU not being able to hit it's highest possible Speedstep when on battery.  While I would like it fixed, it's not that big of a deal to me since I rarely use battery anyway.

I've seen the stuck at 800 MHz problem as well.  At first I thought it happened always when I booted on battery and then plugged into AC, but it didn't happen when I tested that tonight.  So it probably is some kind of intermittent thing, or else I haven't figured out what specifically triggers it.

It does seem from reading others' experiences that the 2720 CPU that I have behaves a little differently than the others.

Thanks for the info, dimm0k.  Take care.

---

### Post by dimm0k on 2011-07-14
gatman3, Well it looks like even among i7-2720QM CPUs with the same BIOS version and settings, things can still vary then as well.  I changed my settings to match yours, discharged the CMOS and booted the computer off of battery.  Still can't pass 1.5GHz!  Supposedly booting off of battery should get you at least the max CPU speed with no Turbo Boost, but I can't even achieve that.  Not a big deal since I rarely run on battery, but still I would like the option to!

---

### Post by Andrei.Pozolotin on 2011-07-20
in case you have kubuntu 11.04 32 bit nvidia brightness problem
here is a workaround
[http://forums.gentoo.org/viewtopic-t-883277-start-0.html](http://forums.gentoo.org/viewtopic-t-883277-start-0.html)
Option "RegistryDwords" "EnableBrightnessControl=1"

---

### Post by GigaRoc on 2011-07-29
Has Anyone been able to the get the 64-bit version of Ubuntu to work?

---

### Post by VValdo on 2011-07-30
> **GigaRoc said:**
> Has Anyone been able to the get the 64-bit version of Ubuntu to work?

Yes I've been using it for weeks.

---

### Post by hemmecke on 2011-08-01
My experience with W520 is somewhat related to this thread. However, I want my i7 core processor reduce its normal frequency for idle times.

A detailed problem description you can find here.
[http://askubuntu.com/questions/55215/lenovo-thinkpad-w520-cpufreq-frequency-scaling-not-working-on-ubuntu-natty-narwha](http://askubuntu.com/questions/55215/lenovo-thinkpad-w520-cpufreq-frequency-scaling-not-working-on-ubuntu-natty-narwha)

I've already googled a lot, but I seem to be the only one that cannot get "/sys/devices/system/cpu/cpu0/cpufreq" in sysfs. :(

My fan is running all the time and it's annoyingly loud. (Temperature is around 46 C.)

Any idea how I can make my processor consume less electricity for the time it is basically doing nothing?

---

### Post by Andrei.Pozolotin on 2011-08-01
1) re: "processor reduce its normal frequency for idle times"
if you use ubuntu 11.04 i386 default install, it will reduce it automatically;
to verify:
```

sudo apt-get install powertop
sudo powertop

```2) re: "fan is running all the time and it's annoyingly loud. (Temperature is around 46 C.)"
use "gkrellm" or "sensors" to verify actual speed and temperature
```

sudo apt-get install gkrellm lm-sensors
gkrellm &
sensors

```I am also using thinkfan, changing its temperature table allowed to reduce noise a bit;
[http://ubuntuforums.org/showthread.php?t=1749186](http://ubuntuforums.org/showthread.php?t=1749186)

room temperature=25 C;

IDLE:
fan speed=2700;  temperature=42 C; (nvidia on, single display only)

STRESS:
fan speed=3800;  temperature=96 C; (nvidia on, single display only)
also shows lots of thermal interrupts in powertop
```

sudo apt-get install stress
stress --cpu 8

```

---

### Post by hemmecke on 2011-08-02
> **Andrei.Pozolotin said:**
> 1) re: "processor reduce its normal frequency for idle times"
if you use ubuntu 11.04 i386 default install, it will reduce it automatically;


Thank you for your reply. However, I find the suggestion rather strange. Why should I want 32bit ubuntu on a 64bit laptop?
Can you point me to particular issues similar or different to mine?

> **Andrei.Pozolotin said:**
> 
```

sudo apt-get install powertop
sudo powertop
...
sudo apt-get install gkrellm lm-sensors
gkrellm &
sensors

```
I've installed that on my 64bit ubuntu. All 4 cpu's show 0% if idle and 100% for the stress test.

Still, I my issue is that the frequency is not going below 2.2 GHz. At least I haven't seen a tool that makes me believe that my laptop is running with less frequency.

I know that there are cpuidle and cpufreq, but as far as I understood from the documentation they have different purposes. cpuidle seems to work on my laptop as powertop seems to indicate (I don't know exactly what powertop measures), but since there is no respective cpufreq directory in sysfs, I must believe that frequency scaling does not work.

In fact, I wanted to see that at least in windows the frequency goes down, but I haven't yet found an appropriate tool to show me on which frequency the processors are running under Windows.

> **Andrei.Pozolotin said:**
> 
2) re: "fan is running all the time and it's annoyingly loud. (Temperature is around 46 C.)"
use "gkrellm" or "sensors" to verify actual speed and temperature

 
"gkrellm" looks pretty nice, but "speed" does not seem to be the same as "frequency". I have the impression gkrellm is rather showing similar results as "top" does.

> **Andrei.Pozolotin said:**
> 
I am also using thinkfanal interrupts in powertop


Yes, I think I can manage the fan. But I hope that I run even cooler and with less fan frequency, if I have that cpufreq problem solved.

Attached are my output of powertop and sensors (under stress and one minute after) all on 64bit ubuntu.

I have also tried a livecd with natty. The cpufreq directory does not automatically show in sysfs.

Should I really try out 32bit Ubuntu? Maybe there is just a BIOS issue? As I said, maybe I have the same problem under Windows.

---

### Post by dimm0k on 2011-08-02
What BIOS version are you running?  Not being able to go under 2.2GHz on idle is very strange.  In Windows 7 you can get the rather crude Intel Turbo Boost Monitor to give you an idea of what your CPU speed is at currently.

---

### Post by Andrei.Pozolotin on 2011-08-02
@hemmecke:

I had too many issues with 64 bit:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/776999](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/776999)

I decided to use 32 bit for now and switch to 64 bit in October:
[https://wiki.ubuntu.com/OneiricOcelot](https://wiki.ubuntu.com/OneiricOcelot)

most fixes for w520 power, nvidia, hang, etc are already on the oneric trunk,
but oneric currently is way too unstable to my taste;

re: "bios" - I have 1.26

---

### Post by Andrei.Pozolotin on 2011-08-02
@hemmecke:

your [powertop64.txt]("http://ubuntuforums.org/attachment.php?attachmentid=199110&d=1312308912") shows that power management is disabled (probably in bios?)

you should have extra column under "P-states (frequencies)" which shows frequencies

---

### Post by Andrei.Pozolotin on 2011-08-02
@hemmecke:

your sensors.txt shows temp and rpm which is consistent with mine fan levels 5 and 6, under load:
[http://ibm-acpi.sourceforge.net/README](http://ibm-acpi.sourceforge.net/README)

fan level 5:
temp1:       +52.0°C  (crit = +99.0°C)
fan1:       3024 RPM

fan level 6:
temp1:       +74.0°C  (crit = +99.0°C)
fan1:       3331 RPM

---

### Post by hemmecke on 2011-08-02
> What BIOS version are you running?1.25

> Not being  able to go under 2.2GHz on idle is very strange.Exactly, it's strange. And Speedstep is enabled in BIOS. In fact, I have reset to the default values.

> In Windows 7 you can  get the rather crude Intel Turbo Boost Monitor to give you an idea of  what your CPU speed is at currently.I cannot check "Intel Turbo Boost Monitor" right now, since I don't currently have the laptop next to me. But [http://www.youtube.com/watch?v=GOninr4ddg0](http://www.youtube.com/watch?v=GOninr4ddg0) doesn't look as I am going to see something below 2.2GHz.

I've made a check with the Lenovo ThinkVantage tool. And there it tells me that TurboBoost works. But I haven't yet seen an indication that Speedstep works.

I don't know why it shouldn't given that the CPU certainly supports it, but I want to **see** the frequencies going down. And I want cpufreq to work.

---

### Post by hemmecke on 2011-08-02
> **Andrei.Pozolotin said:**
> @hemmecke:

your [powertop64.txt]("http://ubuntuforums.org/attachment.php?attachmentid=199110&d=1312308912") shows that power management is disabled (probably in bios?)

you should have extra column under "P-states (frequencies)" which shows frequencies

Exactly. That looks suspicious. But I really have everything enabled!
Very strange indeed.

---

### Post by Andrei.Pozolotin on 2011-08-02
I remember somewhere in this extremely long thread
[http://forums.lenovo.com/t5/W-Series-ThinkPad-Laptops/W520-TurboBOOST-not-working-on-battery-or-after-updates/td-p/442909](http://forums.lenovo.com/t5/W-Series-ThinkPad-Laptops/W520-TurboBOOST-not-working-on-battery-or-after-updates/td-p/442909)

some people had their power management problems cured by "magic reset"

---

### Post by hemmecke on 2011-08-02
Yes, i've read that last night. But a BIOS update is not for me until I'm really, really sure that the BIOS is the reason for not having cpufreq.

Somebody else having a ThinkPad W520 (4282W16) with BIOS 1.25 and a working cpufreq (no matter which kind of Linux). I'd first like to nail down the actual reason.

---

### Post by Andrei.Pozolotin on 2011-08-02
please confirm if ubuntu 11.04 x 32 bit & window 7 have same problem

---

### Post by gatman3 on 2011-08-02
hemmecke, have you disabled acpi?  I'm not sure, but perhaps that could prevent the CPU from speed stepping.

FYI, my experiences are very similar to what Andrei is reporting.  I'm also on 1.26 and switched to Ubuntu 32-bit because of too many problems with the 64-bit on this machine, and I too am waiting and hoping for improvements in the October 11.10 release.

---

### Post by dimm0k on 2011-08-03
> **hemmecke said:**
> 1.25

Exactly, it's strange. And Speedstep is enabled in BIOS. In fact, I have reset to the default values.

I cannot check "Intel Turbo Boost Monitor" right now, since I don't currently have the laptop next to me. But [http://www.youtube.com/watch?v=GOninr4ddg0](http://www.youtube.com/watch?v=GOninr4ddg0) doesn't look as I am going to see something below 2.2GHz.

I've made a check with the Lenovo ThinkVantage tool. And there it tells me that TurboBoost works. But I haven't yet seen an indication that Speedstep works.

I don't know why it shouldn't given that the CPU certainly supports it, but I want to **see** the frequencies going down. And I want cpufreq to work.

Yeah, like I said the Intel Turbo Boost Monitor is really crude.  Seems like the version released earlier this year shows even less information than it did with prior versions, however it still does the job of telling you what speed you're at.  Once you hit the max for SpeedStep, the monitor starts displaying some details.

I strongly suggest you update your BIOS to 1.26 as I firmly believe the issue you're experiencing with the missing cpufreq is due to the broken 1.25 BIOS.  When I purchased my system it came with 1.25 and after installing Slackware I remember having some issues with ACPI.  I use conky to monitor my system's stats and one of them was to tell me the output of /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor.  With BIOS 1.25 that was missing/broken and with no other recourse, I downgraded my BIOS to 1.22 and everything was okay again.  Before downgrading I did upgrade my kernel to see if that would fix it, but unfortunately it did not.  With 1.26 I can say that things for me and the W520 are working okay especially with regard to cpufreq.  Still have some minor issues here and there, but everything that worked in 1.22 works in 1.26 for me.  Also of note, I'm using the 64-bit version of Slackware and my current kernel is 2.6.93.3.  My graphics is set to discrete only.

---

### Post by hemmecke on 2011-08-03
> **Andrei.Pozolotin said:**
> please confirm if ubuntu 11.04 x 32 bit & window 7 have same problem

Let's make this stepwise.
My Laptop is a Lenovo Thinkpad W520 (4282W16) with BIOS 1.25.
[https://www.lenovocampus.at/offer.php5?cid=3&aid=403&name=W%20Serie&keepThis=true&TB_iframe=true&height=293&width=554](https://www.lenovocampus.at/offer.php5?cid=3&aid=403&name=W%20Serie&keepThis=true&TB_iframe=true&height=293&width=554)

Maybe I shouldn't post this Windows related information here but rather at the long thread at the lenovo.com site
([http://forums.lenovo.com/t5/Linux-Discussion/HowTo-Running-Linux-on-W520/td-p/453327](http://forums.lenovo.com/t5/Linux-Discussion/HowTo-Running-Linux-on-W520/td-p/453327)), but I think, it is valuable information also for the Ubuntu folks since it says that BIOS 1.25 seemingly works fine with Windows. ("Seemingly", because I don't know how much I can trust the tools I used below.)

I've installed Intel Turbo Boost Monitor ([http://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=19105](http://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=19105)) and also CPU-Z ([http://www.cpu-z.de/](http://www.cpu-z.de/)).

ITBM showed a 2.2 GHz processor (the blue bar was right at the bottom which probably meant 800MHz) while CPU-Z gave me BusSpeed 99.7MHz with a factor of 8. (And it wouldn't change while I was under Windows Energy plan "Maximale Lebensdauer des Akkus" (max life of battery)... at least I haven't seen it jump up temporarily while I was running the windows provided videos and having 4 youtube movies open and running the "Schnelle Hardwareüberprüfung" (Quick hardware test).

This changed immediately after I changed my energy saving plan to "Höchstleistung" (full speed). ITBM showed TurboBoost up to 2.4GHz (which at least shows that TurboBoost is working).

Of course, removing the plug, i.e. now on battery, brought the laptop back to 800 MHz and even under full load it wouldn't go above. This is with standard BIOS settings.

And then something that surprised me after having read the above lenovo thread. Some have complained about Turboboost not working on battery and the Lenovo guy gave some reason why it shouldn't work. But even on battery (with "Höchstleistung" as energy scheme) I saw ITBM and CPU-Z going up to 2.4GHz. Remember 2.2 is my default. Actually, I should now doubt at what the tools say (since the lenovo thread suggests that there would be not TurboBoost on battery), but I don't know exactly what BIOS 1.25 allows and what not. I don't worry too much about Turboboost on battery at the moment.

I haven't yet seen anything higher than 2.4GHz.

And last...

I've installed natty (32bit). And... NO SUCCESS. :(
Kernel 2.6.38-10-generic-pae.
Even worse. When it starts, it tells me, it doesn't have enough graphics capabilities. :-( That's actually very very strange, since Unity works fine from the very same LiveCD.

This installation has been done by overriding the existing 64bit natty  from the livecd. No formatting, since I already have some user data I did not want to destroy. I don't know whether this matters, but in any case I don't see a /sys/devices/system/cpu/cpu0/cpufreq and cpufreqd tells mit at installation time that it fails. In other words:

```

/etc/init.d/cpufreqd start
 * Starting CPU Frequency daemon cpufreqd                      [fail]

```So it looks like on my machine Natty in 64bit runs better. No cpufreq but I don't have it on 32bit either.

Is there someone from Ubuntu who reads this thread or where exactly should I report my issues? I'd like to find a developer who would go with me through my issues.

And before someone asks... I have already tried this:
[http://ubuntuguide.net/how-to-install-linux-kernel-3-0-rc2-in-ubuntu-11-04-natty-narwhal](http://ubuntuguide.net/how-to-install-linux-kernel-3-0-rc2-in-ubuntu-11-04-natty-narwhal)
cpufreq directory in sysfs still missing.

---

### Post by Andrei.Pozolotin on 2011-08-03
re: "When it starts, it tells me, it doesn't have enough graphics capabilities"
for i386 install, in bios: use only "integrated" (intel) or "discrete" (nvidia); do NOT use "optimus"
?

---

### Post by Andrei.Pozolotin on 2011-08-03
re: "reset to defaults" - in bios this does not reset anything in my case; 
you have to use "magic reset", which is something like: disconnect power, battery, 
then 10 times x (press power button 10 sec; release power button 10 sec)
(see long lenovo thread above)

if reset works, your bios date/time should reset back to some past values, away from your current date/time;

---

### Post by hemmecke on 2011-08-03
I've now inserted the livecd for Maverick (2.6.35-22-generic). It also doesn't come up and showing me /sys/devices/system/cpu/cpu0/cpufreq. Looks like P-states are not recognised under Linux.

Which part of the system is actually responsible for detecting kernel properties?
Aren't P-states connected to SpeedStep? The "est" flag is set when I look at the flags from /proc/cpuinfo.

[http://www.ubuntu.com/certification/hardware/201103-7374](http://www.ubuntu.com/certification/hardware/201103-7374)
The W520 is officially supported by Ubuntu, so somebody should know how to make cpufreq work. Where can I find this person?

---

### Post by hemmecke on 2011-08-03
OK, "integrated" set.
When I log in I only see as session types: Ubuntu, Ubuntu Classic, Ubuntu Classic (no effects), Ubuntu (Safe Mode), User Defined Session.
There is no "Unity". I run with "Ubuntu" choice and arrive at gnome2.

But let's not discuss graphics here. It's not my issue at the moment. And from what I read somewhere else, a beamer/projector doesn't work with integrated graphics. That will be another problem to be solved once I've done this cpufreq stuff. Such be another thread though.

Add-on:
In BIOS I've set graphics to "discrete" and OS detection "disabled". Voila, now I have Unity with 32bit Natty. (no projector working, though)

---

### Post by hemmecke on 2011-08-03
> **Andrei.Pozolotin said:**
> re: "reset to defaults" - in bios this does not reset anything in my case; 

Well, it resets the values locally. (Not the time/date of course.) I had to "save" these "default" values.

> **Andrei.Pozolotin said:**
> you have to use "magic reset", which is something like: disconnect power, battery, 
then 10 times x (press power button 10 sec; release power button 10 sec)
(see long lenovo thread above)

if reset works, your bios date/time should reset back to some past values, away from your current date/time;
Well, apart from this thread is there some reliable (official) place where I can read about "magic reset" and what exactly it does?

---

### Post by Andrei.Pozolotin on 2011-08-03
the official way to reset cmos is to disconnect "backup battery"
[http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles_pdf/0a60078_03.pdf](http://download.lenovo.com/ibmdl/pub/pc/pccbbs/mobiles_pdf/0a60078_03.pdf)

How to remove the power-on password
(A) If no SVP has been set:
To remove a POP that you have forgotten, do the following:
1. Turn off the computer.
2. Remove the battery pack. For how to remove the battery pack, see “1010 Battery pack” on page 60.
3. Remove the backup battery. For how to remove the backup battery, see “1120 Backup battery” on
page 79.
4. Turn on the computer and wait until the POST ends. After the POST ends, the password prompt does
not appear. The POP has been removed.
5. Reinstall the backup battery and the battery pack.

---

### Post by dimm0k on 2011-08-03
> **hemmecke said:**
> I've now inserted the livecd for Maverick (2.6.35-22-generic). It also doesn't come up and showing me /sys/devices/system/cpu/cpu0/cpufreq. Looks like P-states are not recognised under Linux.

Which part of the system is actually responsible for detecting kernel properties?
Aren't P-states connected to SpeedStep? The "est" flag is set when I look at the flags from /proc/cpuinfo.

[http://www.ubuntu.com/certification/hardware/201103-7374](http://www.ubuntu.com/certification/hardware/201103-7374)
The W520 is officially supported by Ubuntu, so somebody should know how to make cpufreq work. Where can I find this person?

Your CPU problems will not be fixed by changing kernels or even versions of Ubuntu.  It is a BIOS PROBLEM!  See here [http://ubuntuforums.org/showpost.php?p=11113391&postcount=52](http://ubuntuforums.org/showpost.php?p=11113391&postcount=52)

---

### Post by Andrei.Pozolotin on 2011-08-03
yes. I bet you my $1 you need to upgrade/downgrade away from bios v 1.25 to resolve this :-)

---

### Post by dimm0k on 2011-08-03
> **hemmecke said:**
> Well, it resets the values locally. (Not the time/date of course.) I had to "save" these "default" values.


Well, apart from this thread is there some reliable (official) place where I can read about "magic reset" and what exactly it does?

The "magic reset" simply discharges the CMOS.  When you turn off your computer, there's usually residual electricity still sitting in certain components.  The "magic reset" clears everything so that you start fresh.

---

### Post by GigaRoc on 2011-08-03
> **VValdo said:**
> Yes I've been using it for weeks.

I've read threw this thread, and i can't seem to find an answer, but how did you do it?  i can't seem to get it to boot 64 with out using either nomodeset or disable acpi, both of which limit the functionality of the notebook.
So i suppose the better question is, has anyone been able to get 64 bit running with all 4 cores and the nvidea graphics card enabled?  if so, how did you do it?

---

### Post by hemmecke on 2011-08-03
> **dimm0k said:**
> Your CPU problems will not be fixed by changing kernels or even versions of Ubuntu.  It is a BIOS PROBLEM!  See here [http://ubuntuforums.org/showpost.php?p=11113391&postcount=52](http://ubuntuforums.org/showpost.php?p=11113391&postcount=52)

> **Andrei.Pozolotin said:**
> yes. I bet you my $1 you need to upgrade/downgrade away from bios v 1.25 to resolve this :smile:

Interesting opinion. But though it might solve **my** problems, it is totally unacceptable for the majority of the world or even for the ubuntu developers.

1) I will not change my bios unless a) it is 100% clear that 1.26 solves my problem and b) it is impossible to have another option.
(Maybe you both find it safe to upgrade the bios. But given that some slight mistake makes the whole computer unusable, it is simply not a generic option for people who have never done that.)

2) Since Win7 seems to be able to deal with speedstep and turboboost
[http://ubuntuforums.org/showpost.php?p=11114194&postcount=53](http://ubuntuforums.org/showpost.php?p=11114194&postcount=53),
it is a clear indication that a BIOS upgrade is unnecessary. Even if there were/are bugs in BIOS 1.25, Windows runs with Speedstep and TurboBoost. Why should Ubuntu forever be unable to do so as well? Those people at the Lenovo thread have to complain about BIOS bugs, because they are locked into a closed source OS.

I wholeheartedly believe that some clever Ubuntu, Debian, ACPI, or linux kernel guy/girl will find a way around my problem so that everyone with a W520 will be happy with Ubuntu and not just you and me. I've therefore opened a bug report.
[https://bugs.launchpad.net/ubuntu/+bug/820489](https://bugs.launchpad.net/ubuntu/+bug/820489)

Actually, would somebody of you just downgrade to BIOS 1.25 and tell me if Natty then also reports a missing cpufreq dir? If it works for you, that would at least bring us closer to tracking down a proper solution without BIOS upgrades/downgrades. Isn't that the open source spirit to help others?

In fact, I haven't seen your exact system specification (model number and such), i.e. if you do not have the exact same laptop as me, how can I believe that what works for you also works for me?

---

### Post by hemmecke on 2011-08-03
> **GigaRoc said:**
> I've read threw this thread, and i can't seem to find an answer, but how did you do it?  i can't seem to get it to boot 64 with out using either nomodeset or disable acpi, both of which limit the functionality of the notebook.
So i suppose the better question is, has anyone been able to get 64 bit running with all 4 cores and the nvidea graphics card enabled?  if so, how did you do it?
Actually, 4 cores is not a problem. I had a 64bit natty running (except for this cpufreq problem)... you find my system specification here... [http://ubuntuforums.org/showpost.php?p=11114194&postcount=53](http://ubuntuforums.org/showpost.php?p=11114194&postcount=53)

 I haven't properly verified nvidea, but I remember, installing the nvidea driver caused problems (system did not boot into GUI -- rather a black screen).
When i looked at "lsmod" (standard 64bit natty install), it seemed that nouveau was running. (That was started back then with the original BIOS 1.25 with no modifications.)

Interestingly for this thread, nobody posts enough and clear information about their system. It should be clear that people can only help if they have enough information. Otherwise, they just turn away and spend their valuable time somewhere else.

---

### Post by dimm0k on 2011-08-03
> **hemmecke said:**
> Interesting opinion. But though it might solve **my** problems, it is totally unacceptable for the majority of the world or even for the ubuntu developers.

1) I will not change my bios unless a) it is 100% clear that 1.26 solves my problem and b) it is impossible to have another option.
(Maybe you both find it safe to upgrade the bios. But given that some slight mistake makes the whole computer unusable, it is simply not a generic option for people who have never done that.)

2) Since Win7 seems to be able to deal with speedstep and turboboost
[http://ubuntuforums.org/showpost.php?p=11114194&postcount=53](http://ubuntuforums.org/showpost.php?p=11114194&postcount=53),
it is a clear indication that a BIOS upgrade is unnecessary. Even if there were/are bugs in BIOS 1.25, Windows runs with Speedstep and TurboBoost. Why should Ubuntu forever be unable to do so as well? Those people at the Lenovo thread have to complain about BIOS bugs, because they are locked into a closed source OS.

I wholeheartedly believe that some clever Ubuntu, Debian, ACPI, or linux kernel guy/girl will find a way around my problem so that everyone with a W520 will be happy with Ubuntu and not just you and me. I've therefore opened a bug report.
[https://bugs.launchpad.net/ubuntu/+bug/820489](https://bugs.launchpad.net/ubuntu/+bug/820489)

Actually, would somebody of you just downgrade to BIOS 1.25 and tell me if Natty then also reports a missing cpufreq dir? If it works for you, that would at least bring us closer to tracking down a proper solution without BIOS upgrades/downgrades. Isn't that the open source spirit to help others?

In fact, I haven't seen your exact system specification (model number and such), i.e. if you do not have the exact same laptop as me, how can I believe that what works for you also works for me?

I can tell you now that you will be waiting a LONG time, if not forever if you are looking for a fix for your issues through software.  If there is even a fix, it wouldn't be a true fix as it would only be a workaround and it is mainly because of this...  I've already told you that my notebook came with BIOS 1.25 where I had ACPI and cpufreq issues, which should be a clue that 1.25 is bad.  Another clue, 1.22 works fine and does not have any ACPI/cpufreq issues.  Want another clue?  1.26 also does not have any ACPI/cpufreq issues.  I don't know what other proof you need before you realize that 1.25 is BAD!  Read the Lenovo forum, as well as [http://forum.notebookreview.com/lenovo-ibm/](http://forum.notebookreview.com/lenovo-ibm/) to hear from others that verify that 1.25 is broken, bad, fscked, crap.  Oh and another reason to go to 1.26?  The loud sometimes "stuttering" fan noise is fixed.

I understand that upgrading the BIOS is a scary task, but if you look through the forums you'll see that no one has had any bad issues upgrading the BIOS on the W520, as Lenovo has made it a safer process.  As long as you are patient and follow the directions letting the update do it's thing you should be fine.

Unfortunately the way manufacturers work these days is they release hardware with minimal testing before they make it widely available.  This saves cost and time that would have been used for the testing process and we the users have become the real test cases.  If there's an issue and there's enough complaints then the manufacturers verify the issue and then release a software (BIOS in this case) to fix.

---

### Post by dimm0k on 2011-08-03
> **GigaRoc said:**
> I've read threw this thread, and i can't seem to find an answer, but how did you do it?  i can't seem to get it to boot 64 with out using either nomodeset or disable acpi, both of which limit the functionality of the notebook.
So i suppose the better question is, has anyone been able to get 64 bit running with all 4 cores and the nvidea graphics card enabled?  if so, how did you do it?

Just curious...  what BIOS version is your system at?


> **hemmecke said:**
> Interestingly for this thread, nobody posts enough and clear information about their system. It should be clear that people can only help if they have enough information. Otherwise, they just turn away and spend their valuable time somewhere else.

While information is nice, the ones you seek are irrelevant to your issues simply because I have witnessed those same issues on my system, which shipped with BIOS 1.25 and those issues disappeared when I downgraded my BIOS to 1.22 because 1.26 was about 1-1.5 months away.  Now with 1.26 I still have not seen those very issues you're seeing now.

---

### Post by Andrei.Pozolotin on 2011-08-03
re: "nobody posts enough and clear information about their system"

fair enough;

```

#!/bin/bash

echo `date` > info.txt

echo "### dmidecode " >> info.txt
sudo dmidecode | grep -v -E 'Serial Number|UUID' >> info.txt

echo "### lsb_release" >> info.txt
lsb_release -a >> info.txt

echo "### uname" >> info.txt
uname -a >> info.txt

echo "### xorg.conf" >> info.txt
cat /etc/X11/xorg.conf >> info.txt

echo "### xorg.log" >> info.txt
cat /var/log/Xorg.0.log >> info.txt

echo "### lsmod" >> info.txt
lsmod | sort >> info.txt

echo "### lspic" >> info.txt
sudo lspci -v >> info.txt

echo "### lshw" >> info.txt
sudo lshw -sanitize >> info.txt

echo "### sensors" >> info.txt
sensors >> info.txt

echo "### powertop" >> info.txt
sudo powertop -d >> info.txt

echo "### sysfs cpu info" >> info.txt
sudo find  /sys/devices/system/cpu/ -type f -exec sh -c "echo {} && cat {}" ';' >> info.txt

```

attached

---

### Post by hemmecke on 2011-08-04
> **dimm0k said:**
> I can tell you now that you will be waiting a LONG time, if not forever if you are looking for a fix for your issues through software.

Maybe you are right. Then I have to wait. But I remember that I had an issue with a ACER Travelmate. it has 1400x1050 resolution and the BIOS table wouldn't say so. So in the beginning, it was on 1280x960 (which looked, of course totally bad). Then I've found the i815 kernel module. And now the i915 kernel module is seemingly standard any new kernel boots just fine into 1400x1050.

> **dimm0k said:**
>  If there is even a fix, it wouldn't be a true fix as it would only be a workaround and it is mainly because of this...

Suppose, there will be a "workaround" in the kernel or whereever it is needed so that in a newer ubuntu i wouldn't have a problem with BIOS 1.25. Then practically, I wouldn't even realize that BIOS 1.25 has a but, right? It's irrelevant whether you call it workaround or bugfix.

> **dimm0k said:**
>  I've already told you that my notebook came with BIOS 1.25 where I had ACPI and cpufreq issues, which should be a clue that 1.25 is bad.  Another clue, 1.22 works fine and does not have any ACPI/cpufreq issues.  Want another clue?  1.26 also does not have any ACPI/cpufreq issues.  I don't know what other proof you need before you realize that 1.25 is BAD!  Read the Lenovo forum, as well as [http://forum.notebookreview.com/lenovo-ibm/](http://forum.notebookreview.com/lenovo-ibm/) to hear from others that verify that 1.25 is broken, bad, fscked, crap.  Oh and another reason to go to 1.26?  The loud sometimes "stuttering" fan noise is fixed.

1) Why does Win7 not show problems with Speedstep? (Remember, some people wanted TurboBoost on battery which is not an issue for me.) And also look at the changelog for 1.26. It doesn't say anything about speedstep.

2) Since you had issues, you have surely reported them to the Ubuntu folks. Can you please give a pointer to your report?

---

### Post by hemmecke on 2011-08-04
> **Andrei.Pozolotin said:**
> re: "nobody posts enough and clear information about their system"

fair enough;


You seem to be quite knowledgable about what to provide. Thank you.
Since when I ran your script, I've noticed a few lines that went to stderr, I've remove the '>>info.txt' part and rather used the following script (info.sh):
```

#!/bin/bash

echo `date`

echo "### dmidecode "
sudo dmidecode | grep -v -E 'Serial Number|UUID'

echo "### lsb_release"
lsb_release -a

echo "### uname"
uname -a

echo "### xorg.conf"
cat /etc/X11/xorg.conf

echo "### xorg.log"
cat /var/log/Xorg.0.log

echo "### lsmod"
lsmod | sort

echo "### lspic"
sudo lspci -v

echo "### lshw"
sudo lshw -sanitize

echo "### sensors"
sensors

echo "### powertop"
sudo powertop -d

echo "### sysfs cpu info"
sudo find  /sys/devices/system/cpu/ -type f -exec sh -c "echo {} && cat {}" ';'

```with the call
```

bash info.sh > info.txt 2>&1

```I've then manually added "%%% " in front of the stderr lines to make them easier recognizable.

I somehow find it interesting, that I get
```

cat: /sys/devices/system/cpu/probe: Permission denied
 cat: /sys/devices/system/cpu/release: Permission denied

```But since I also see this on another laptop, there is probably not much to care about.

Another thing I noticed is
```

[    15.582] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)

```in the xorg.log section.

Furthermore, I don't see the kernel modules
```

tpm                    21251  1 tpm_tis
tpm_bios               13460  1 tpm
tpm_tis                18089  0 

```in your output. I've seen people having issues with suspend when having loaded that. Did you explicitly remove them?

And then in the "lshw" section you have "cpufreq" in the " *-cpu capabilities". I haven't.

You have...
```

fan1:       3022 RPM

```You have cpufreq and cpuidle running. Is your fan ever switching off completely? (Well you cpu is a bit more powerful than mine, but still...That's what I want to achieve in the end.)

---

### Post by Andrei.Pozolotin on 2011-08-04
in your lshw -> cpu -> capabilities : cpufreq is NOT detected

mine:
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt aes xsave avx lahf_lm ida arat epb xsaveopt pln pts tpr_shadow vnmi flexpriority ept vpid **cpufreq**

yours:
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt aes xsave avx lahf_lm ida arat epb xsaveopt pln pts tpr_shadow vnmi flexpriority ept vpid

---

### Post by Andrei.Pozolotin on 2011-08-04
well, lshw result means nothing - it merely reads sysfs
[http://ezix.org/project/browser/packages/lshw/development/src/core/cpufreq.cc](http://ezix.org/project/browser/packages/lshw/development/src/core/cpufreq.cc)

---

### Post by Andrei.Pozolotin on 2011-08-04
I suggest you contact
[http://www.kernel.org/pub/linux/utils/kernel/cpufreq/cpufreq.html](http://www.kernel.org/pub/linux/utils/kernel/cpufreq/cpufreq.html)
[Dave Jones]("http://www.codemonkey.org.uk/") [http://codemonkey.org.uk/](http://codemonkey.org.uk/) [email]davej@codemonkey.org.uk[/email]
and ask him to give you info how to differentiate bios vs kernel cpufreq detection failure

---

### Post by dimm0k on 2011-08-04
> **hemmecke said:**
> Maybe you are right. Then I have to wait. But I remember that I had an issue with a ACER Travelmate. it has 1400x1050 resolution and the BIOS table wouldn't say so. So in the beginning, it was on 1280x960 (which looked, of course totally bad). Then I've found the i815 kernel module. And now the i915 kernel module is seemingly standard any new kernel boots just fine into 1400x1050.


Suppose, there will be a "workaround" in the kernel or whereever it is needed so that in a newer ubuntu i wouldn't have a problem with BIOS 1.25. Then practically, I wouldn't even realize that BIOS 1.25 has a but, right? It's irrelevant whether you call it workaround or bugfix.


1) Why does Win7 not show problems with Speedstep? (Remember, some people wanted TurboBoost on battery which is not an issue for me.) And also look at the changelog for 1.26. It doesn't say anything about speedstep.

2) Since you had issues, you have surely reported them to the Ubuntu folks. Can you please give a pointer to your report?

I don't know enough about the Acer Travelmate or the ix15 kernel module to comment, but if the resolution issue you had was caused by the BIOS and fixed with a kernel module, do you know if a newer BIOS was ever released for that particular notebook to fix that issue?  What I'm trying to get at is if you have users with the same issue that gets resolved with a BIOS update, what reason would there be for a Linux developer to "reinvent the wheel" by creating a fix/workaround?

You have to understand that Windows 7 and Linux are different and probably take different approaches at handling things so just because it works in Windows does not ever guarantee it will work in Linux.  I'm just as clueless as you when developers create vague Changelogs that barely give you any clue that they do any actual work other than change the version number and release!  With that in mind, only the developers know what they actually did in BIOS 1.22 to 1.25 that broke ACPI for Linux but not for Windows and then fixed when going to 1.26.  A lot of times BIOS, even software gets fixes/changes that are left for the users to discover.

To answer your number 2, unfortunately I have not made any reports to the Ubuntu folks, not because I use Slackware and not Ubuntu, but because I see these issues as a problem with the BIOS and not Linux itself.  When I went from kernel 2.6.37 to 2.6.38, with 2.6.39 following and these issues still persisted it gave me an idea that there's a good chance Linux is not at fault.  Then when I downgraded the BIOS from 1.25 to 1.22 and the issues went away, it told me then and there that the BIOS was the one at fault.

I hope you don't take all I've said the wrong way.  I'm not forcing you to update your BIOS...  I'm trying to give you reasons to enjoy your notebook now instead of waiting for a fix for something that's already fixed.

---

### Post by hemmecke on 2011-08-05
> **dimm0k said:**
> I don't know enough about the Acer Travelmate or the ix15 kernel module to comment, but if the resolution issue you had was caused by the BIOS and fixed with a kernel module, do you know if a newer BIOS was ever released for that particular notebook to fix that issue?

I've no idea. And, to be honest, at that time, it never occured to me that one can upgrade the bios. I've just learned all that while dealing with the cpufreq issue.

> What I'm trying to get at is if you have users with the same issue that gets resolved with a BIOS update, what reason would there be for a Linux developer to "reinvent the wheel" by creating a fix/workaround?
Haven't i already stated that? Ubuntu/Canonical wants (ehm actually we all want) that a Laptop can be run with free software and is easily usable by kids and elder people alike. If that is the goal then developers have to "reinvent the wheel" (or better said "fix manufacturers' bugs"). A BiOS upgrade involves user interaction that no Linux developer can control or make simpler or less risky. What would you do if you were head of Canonical? Open up a website and ask your users to upgrade the BIOS?

> You have to understand that Windows 7 and Linux are different and probably take different approaches at handling things so just because it works in Windows does not ever guarantee it will work in Linux.
I know what you try to say, but, come on, if there were no licensing issues, then Linux could just copy the way that Win7 uses.

You've probably read that in some cases Linux and driver developers take the route of being bug-compatible with Windows just to work around the fact that most manufacturers only care for Windows.


> 
To answer your number 2, unfortunately I have not made any reports to the Ubuntu folks, not because I use Slackware and not Ubuntu, but because I see these issues as a problem with the BIOS and not Linux itself.  When I went from kernel 2.6.37 to 2.6.38, with 2.6.39 following and these issues still persisted it gave me an idea that there's a good chance Linux is not at fault.  Then when I downgraded the BIOS from 1.25 to 1.22 and the issues went away, it told me then and there that the BIOS was the one at fault.

I hope you don't take all I've said the wrong way.  I'm not forcing you to update your BIOS...  I'm trying to give you reasons to enjoy your notebook now instead of waiting for a fix for something that's already fixed.

I hope you don't take all I've said the wrong way.  I'm not forcing you I thank you for your hints. That all helps to track down the problem to its true source and to (maybe) find a proper workaround.

---

### Post by dimm0k on 2011-08-05
@hemmecke: I'll be monitoring this thread even after I've replaced my W520...  I'm curious to see how long you're willing to wait for a fix and if a fix ever comes.

---

### Post by robertorc87 on 2011-08-06
Hi all, another W520 owner here. I bought it. Must wait the delivery... it's a two weeks hard wait! :(
Can't wait to try ubuntu 11.04 on it (well, that and some "win" CAD software :P)

I'll keep reading quietly on here. When it'll be here I'll surely have some questions.

:popcorn:

bye,
Roberto.

---

### Post by hemmecke on 2011-08-11
> **dimm0k said:**
> @hemmecke: I'll be monitoring this thread even after I've replaced my W520...  I'm curious to see how long you're willing to wait for a fix and if a fix ever comes.

:) Good. Maybe you'll win.

Can someone on this thread (who apparently managed to get cpufreq working) tell me whether you also managed to convince your fan to run slower than the seemingly standard 3000? Or even managed to configure your machine that the fan even stops if nothing is done on this machine or if I simply type something into a forum like this? (How did you do it?)

Even in the post [http://ubuntuforums.org/showpost.php?p=11116461&postcount=68](http://ubuntuforums.org/showpost.php?p=11116461&postcount=68) of Andrei.Pozolotin it shows "3022 RPM". It's actually surprising, since his computer seems to run  99.2% on 800MHz, but his temperature is 56 C. Strange.

Note, that I know how to turn my fan off, but then my computer becomes an oven and heats to 80 degree even if idle. I'd like to keep the temperature reasonable, of  course.

I can probably manage to setup thinkfan (or would you suggest something else?), but I'd like to hear other people's experience with respect to using speedstep. What temperature does your computer run at (when idle) and does your fan turn on and off as appropriate? For how long is the fan usually off? On which frequency runs your cpu when the fan turns off?

---

### Post by VValdo on 2011-08-11
I'm using thinkfan.  It works fine.

---

### Post by hemmecke on 2011-08-11
> **VValdo said:**
> I'm using thinkfan.  It works fine.
Thanks. But, please, I've asked more questions. Can you also  answer the other ones?

---

### Post by VValdo on 2011-08-11
> **hemmecke said:**
> Can someone on this thread (who apparently managed to get cpufreq working) tell me whether you also managed to convince your fan to run slower than the seemingly standard 3000?

Yes by running ThinkFan.

> **hemmecke said:**
> Or even managed to configure your machine that the fan even stops if nothing is done on this machine

Yes, thinkfan can be configured to turn the fan off at lower temps.

> **hemmecke said:**
>  or if I simply type something into a forum like this? (How did you do it?)

Not sure what you mean by this.

> **hemmecke said:**
> I can probably manage to setup thinkfan (or would you suggest something else?),

I recommend thinkfan.

> **hemmecke said:**
>  but I'd like to hear other people's experience with respect to using speedstep. What temperature does your computer run at (when idle) and does your fan turn on and off as appropriate?

Idle it's ~48C.  It goes up to maybe 82C or so, at which point the fan is up 100%.

> **hemmecke said:**
> For how long is the fan usually off?

For how long?  I actually think I set it to run ever-so-slowly even at the low speeds.  I can't remember why, but I did.

> **hemmecke said:**
> On which frequency runs your cpu when the fan turns off?

I am seeing a frequency of 800 MHz right now... at semi-idle.  See [here]("https://launchpad.net/indicator-cpufreq") for an indicator for Unity that lets you change the frequency and governor.

---

### Post by hemmecke on 2011-08-11
Thank you, Waldo, your post is much appreciated.

> **VValdo said:**
> 
> *or if I simply type something into a forum like this? (How did you do it?)*Not sure what you mean by this.

Simply typing or writing a letter is basically like an idle computer. So I meant a task that doesn't cost much.

Can you post your thinkfan configuration? What actually are your system specifications? Can you post something similar to [http://ubuntuforums.org/showpost.php?p=11116461&postcount=68](http://ubuntuforums.org/showpost.php?p=11116461&postcount=68)?

> For how long?  I actually think I set it to run ever-so-slowly even at the low speeds.  I can't remember why, but I did.
OK, then what is your usual fan speed for an idle machine? Does the fan disturb you at that speed?

> I am seeing a frequency of 800 MHz right now... at semi-idle.  See [here]("https://launchpad.net/indicator-cpufreq") for an indicator for Unity that lets you change the frequency and governor.You don't seem to have read the most recent posts of this thread. I am the guy who cannot get cpufreq running. My computer runs always at 2.2GHz.

---

### Post by Andrei.Pozolotin on 2011-08-11
[http://thinkpad-wiki.org/Thinkfan](http://thinkpad-wiki.org/Thinkfan)

---

### Post by VValdo on 2011-08-11
I hadn't read/noticed that you didn't have cpufreq running.

Here's a checklist of stuff to make sure is correct.

**Update your BIOS to [1.26]("http://forum.notebookreview.com/lenovo-ibm/566338-lenovo-w520-owners-thread-321.html#post7676016")** -- boot off a CD, it'll do the update.  Bam. Done.

**Update the kernel to [3.0.1]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0.1-oneiric/")** -  If you are running the x86_64 ubuntu (which you should be), it's a matter of getting these three files:

linux-headers-3.0.1-030001-generic_3.0.1-030001.201108060905_amd64.deb	 
linux-headers-3.0.1-030001_3.0.1-030001.201108060905_all.deb
linux-image-3.0.1-030001-generic_3.0.1-030001.201108060905_amd64.deb

put those files on the desktop and then do this:

```
sudo dpkg -i linux-headers-3.0.1-030001-generic_3.0.1-030001.201108060905_amd64.deb linux-headers-3.0.1-030001_3.0.1-030001.201108060905_all.deb linux-image-3.0.1-030001-generic_3.0.1-030001.201108060905_amd64.deb
```

(if someone is reading this in the future, just be using a new kernel)

**Install lm-sensors** --

```
sudo apt-get install lm-sensors

```
and when you're done with that:

```
sudo sensors-detect
```
and say yes to everything.

**Install [thinkfan](http://thinkpad-wiki.org/Thinkfan)** - sudo apt-get install thinkfan.

Here are various configuration files on my system:

/etc/default/thinkfan
```
# Should thinkfan be started automatically on boot?
# Only say "yes" when you know what you are doing, have configured
# thinkfan correctly for *YOUR* machine and loaded thinkpad_acpi
# with fan_control=1 (if you have a ThinkPad).
START=yes

# Additional startup parameters
DAEMON_ARGS="-q"

```

/etc/thinkfan.conf
```
######################################################################
# thinkfan 0.7 example config file
# ================================
#
# ATTENTION: There is only very basic sanity checking on the configuration.
# That means you can set your temperature limits as insane as you like. You
# can do anything stupid, e.g. turn off your fan when your CPU reaches 70°C.
#
# That's why this program is called THINKfan: You gotta think for yourself.
#
######################################################################
#
# IBM/Lenovo Thinkpads (thinkpad_acpi, /proc/acpi/ibm)
# ====================================================
#
# IMPORTANT:
#
# To keep your HD from overheating, you have to specify a correction value for
# the sensor that has the HD's temperature. You need to do this because
# thinkfan uses only the highest temperature it can find in the system, and
# that'll most likely never be your HD, as most HDs are already out of spec
# when they reach 55 °C.
# Correction values are applied from left to right in the same order as the
# temperatures are read from the file.
#
# For example:
# sensor /proc/acpi/ibm/thermal (0, 0, 10)
# will add a fixed value of 10 °C the 3rd value read from that file. Check out
# http://www.thinkwiki.org/wiki/Thermal_Sensors to find out how much you may
# want to add to certain temperatures.

#  Syntax:
#  (LEVEL, LOW, HIGH)
#  LEVEL is the fan level to use (0-7 with thinkpad_acpi)
#  LOW is the temperature at which to step down to the previous level
#  HIGH is the temperature at which to step up to the next level
#  All numbers are integers.
#

# I use this on my T61p:
#sensor /proc/acpi/ibm/thermal (0, 10, 15, 2, 10, 5, 0, 3, 0, 3)

sensor /sys/devices/platform/coretemp.0/temp1_input
sensor /sys/devices/platform/coretemp.0/temp2_input
sensor /sys/devices/platform/coretemp.0/temp3_input
sensor /sys/devices/platform/coretemp.0/temp4_input
sensor /sys/devices/platform/coretemp.0/temp5_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input
sensor /sys/devices/virtual/thermal/thermal_zone0/temp


(0,	0,	55)
(1,	48,	60)
(2,	50,	61)
(3,	52,	63)
(4,	56,	65)
(5,	59,	66)
(7,	63,	32767)

```

/etc/modprobe.d/thinkfan.conf 
```
options thinkpad_acpi fan_control=1

```

Start with that.  If you've set up as above, and it still doesn't work, let me know.  I may update this post if I can think of more to suggest.

---

### Post by tannerwatson on 2011-08-11
Has anyone else had any problems with the W520 not outputting sound from the dock's headphone jack? This is an issue that I've found to be a little annoying. Sound coming out of the on-board headphone jack works fine, just not through the dock. I don't think it's a hardware issue since it works fine in Windows 7.

---

### Post by Andrei.Pozolotin on 2011-08-11
re: "problems with the W520 not outputting sound from the dock's headphone jack"
yep; does not work for me also.

---

### Post by Andrei.Pozolotin on 2011-08-11
FYI: this:
```

echo level 127 >/proc/acpi/ibm/fan

```

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=610722](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=610722)

also applies to w520; you can run at 100% cpu load:
```

stress --cpu 8

```

at "mere 70 C" temperature when fan is "disengaged"

---

### Post by VValdo on 2011-08-12
Thought-- If you want to jack your CPU up 100% for testing your fan or maybe that your cpu works, get [mprime]("http://www.mersenne.org/freesoft/default.php"), and run the torture-test on it:

mprime -t

also, I recommend grabbing gkrellm (via sudo apt-get install gkrellm) as it gives you a nice view of your cores, temps, and fan speeds all in once nice graphic.

---

### Post by Andrei.Pozolotin on 2011-08-12
yes, "mprime" runs more hot then "stress" for the same thread count;

---

### Post by lucid weaver on 2011-08-19
Hi, I've been having some issues with my w520 that no one seems to have mentioned yet. I can't get hard disk protection to work and more importantly, it doesn't reliably recover from suspend/hibernate or even just from the screensaver. I am running the latest Kubuntu with the BIOS upgraded to 1.26 (which worked great, by the way).

As a side note, it seems every other upgrade breaks the flash install. I'm thinking of downgrading it and holding it there. I think that is more of a general linux problem though.

---

### Post by lucid weaver on 2011-08-21
I forgot to mention that the wireless card seems to be running at half speed. That is, it's half as fast as other laptops connected to the same network.

---

### Post by lucid weaver on 2011-08-23
**bump**

I probably shouldn't have waited so long before posting my first question above.

Is it considered bad etiquette here to PM the users who participated in this thread to let them know it's still alive?

---

### Post by mörgæs on 2011-08-24
Yes. 

People in here use the search function, where they see a list of active threads in which they participated. That is, they have already seen that this thread is active.

If they still do not post, they don't have an answer - it is as simple as that.

---

### Post by robertorc87 on 2011-08-27
hi, I got my W520 this week. I7 2720QM, quadro 1000M, 8GB ram, 1920x1080.
----
Here it's what I've done last days:
- installed ubuntu 11.04 32bit pae. The notebook came with 1.22  bios IIRC. I wasn't able to throttle the CPU with the gnome cpu applet.  It was stuck to 2.2GHz.
- update bios to 1.26. CPU auto-throttling was working fine as showed by cpu gnome applet from 800MHz to 2.2GHz.
- tried bumblebee and made a mess.
- removed natty 32bit and installed 64bit. Installed nvidia proprietary drivers.
- installed all available updates and solved the small issues like brightness not working, bluetooth always on, ultranav fixes, hdaps etc.

so far no serious issues with 64bit on w520. I don't have huge fan issues as other said so I'm not using thinkfan, for now. The system is cool at idle and under normal office use. I should try it with some serious apps next days.

The things I have to do are:
- fixing console resolution and boot screen when using NVIDIA because it shows in FHD only when using Integrate graphics. not a serious issue
- use optimus? don't know if I'll try bumblebee soon, I need to read more before to make another mess :confused: as now I choose in bios intel or nvidia when I need it.
- turbo boost, how can it goes over 2.2GHz under Ubuntu?  is gnome cpu applet indicating wrong when it maxes at 2.2ghz?
- screen calibration, the reds are too saturated at high brightness. I don't have the pantone integrated, so are there profiles for this FHD screen and how to use them in ubuntu?
- the power button. it's configured to ask what to do when I push it, but it does nothing.

regards,
Roberto

---

### Post by Jason P on 2011-08-27
Would it be possible for someone who has gotten the tp_smapi working on a W520 to write a small tutorial about it. I have tried and am unable to get it working. I followed the advice here, [http://ubuntuforums.org/showthread.php?t=1752993](http://ubuntuforums.org/showthread.php?t=1752993) , as well as at ThinkWiki.

---

### Post by gatman3 on 2011-08-30
Roberto,

> **robertorc87 said:**
> 
- turbo boost, how can it goes over 2.2GHz under Ubuntu?  is gnome cpu applet indicating wrong when it maxes at 2.2ghz?


I don't have very many answers, but I can at least tell you that Turbo Boost frequency is not reported in /proc/cpuinfo, so most if not all typical linux applets won't report it correctly.

There has been a fair amount of discussion on this in other places, but here is a short summary:

1. Speed Step.  This feature reduces the frequency below 2.2 GHz (or whatever your nominal frequency is) to save power.

2. Turbo Boost.  This feature increases the frequency above 2.2 GHz (or nominal) for higher performance on demand.

There are numerous quirks with the W520 related to which frequencies are permitted by the Speed Step and Turbo Boost functions depending on whether you have booted on AC or on battery, running on AC or battery, etc.  It also seems like different BIOS versions and maybe even different CPU types may behave differently.  There is a thread on the Lenovo forums that covers much of this, and it seems like it is also not yet all resolved (latest BIOS is 1.26, but stay tuned for more BIOS updates).

I have found this utility to be handy for reporting the correct CPU frequency:

[http://code.google.com/p/i7z/](http://code.google.com/p/i7z/)

Good luck.

---

### Post by wolfindersteppe on 2011-09-05
Dear community, does anybody experience randomly shut down with W520? More and more W520 owner running W7 are reporting randomly shut down, see [http://lnv.lithium.com/t5/W-Series-ThinkPad-Laptops/W520-shuts-off-intermittently-no-BSOD-or-shut-down/td-p/459785]("http://lnv.lithium.com/t5/W-Series-ThinkPad-Laptops/W520-shuts-off-intermittently-no-BSOD-or-shut-down/td-p/459785") and I somehow suspect W7 faulty drivers and not HW. I was running Ubuntu for maximum 3 weeks without dual booting to W7. Now I had to run W7 for 5 weeks in the row and yesterday I have got the shut down, out of idle. Would be very nice if you guys who run permanently Ubuntu for months and months could report if you have experienced the similar issue? That would help to isolate the issue - HW or faulty W7 drivers related?

---

### Post by gatman3 on 2011-09-05
> **wolfindersteppe said:**
> Dear community, does anybody experience randomly shut down with W520? More and more W520 owner running W7 are reporting randomly shut down, see [http://lnv.lithium.com/t5/W-Series-ThinkPad-Laptops/W520-shuts-off-intermittently-no-BSOD-or-shut-down/td-p/459785]("http://lnv.lithium.com/t5/W-Series-ThinkPad-Laptops/W520-shuts-off-intermittently-no-BSOD-or-shut-down/td-p/459785") and I somehow suspect W7 faulty drivers and not HW. I was running Ubuntu for maximum 3 weeks without dual booting to W7. Now I had to run W7 for 5 weeks in the row and yesterday I have got the shut down, out of idle. Would be very nice if you guys who run permanently Ubuntu for months and months could report if you have experienced the similar issue? That would help to isolate the issue - HW or faulty W7 drivers related?

wolfindersteppe,

I have been running Ubuntu 11.04 32-bit PAE on my W520 for nearly 3 months now, and I have never experienced a sudden unexpected shutdown.  There are plenty of other quirks with this machine for sure, and I would say in general it's nowhere near as solid as my old W500.  I have even experienced occasional lockups, maybe one per week, but never a shutdown (when locked up, the screen is on and the wifi light blinking, but the machine is unresponsive and I can't go to an F1 console or remotely login).  I attribute the lockups and other quirks to immature BIOS and immature Linux drivers, but I never see unexpected shutdowns.

Model 4182-W1T
CPU: Intel(R) Core(TM) i7-2720QM CPU @ 2.20GHz
8 GB RAM (2 modules)

---

### Post by Andrei.Pozolotin on 2011-09-06
> **wolfindersteppe said:**
> Dear community, does anybody experience randomly shut down with W520? More and more W520 owner running W7 are reporting randomly shut down, see [http://lnv.lithium.com/t5/W-Series-ThinkPad-Laptops/W520-shuts-off-intermittently-no-BSOD-or-shut-down/td-p/459785]("http://lnv.lithium.com/t5/W-Series-ThinkPad-Laptops/W520-shuts-off-intermittently-no-BSOD-or-shut-down/td-p/459785") and I somehow suspect W7 faulty drivers and not HW. I was running Ubuntu for maximum 3 weeks without dual booting to W7. Now I had to run W7 for 5 weeks in the row and yesterday I have got the shut down, out of idle. Would be very nice if you guys who run permanently Ubuntu for months and months could report if you have experienced the similar issue? That would help to isolate the issue - HW or faulty W7 drivers related?
yes, I had random lock ups on battery, like once a week; they seem to be gone after upgrade to 

# uname -a
Linux wks002 2.6.38-11-generic-pae #48-Ubuntu SMP Fri Jul 29 20:51:21 UTC 2011 i686 i686 i386 GNU/Linux

---

### Post by Andrei.Pozolotin on 2011-09-06
> **gatman3 said:**
> 
I have found this utility to be handy for reporting the correct CPU frequency:
[http://code.google.com/p/i7z/](http://code.google.com/p/i7z/)


nice utility; thanks for the link;

---

### Post by MeikelP on 2011-09-12
Hi Gatman3, I am struggeling in setting up displays for the W520 and I have seen your post on switching by script between Nvidia and Intel when docked. I would kindly ask you - if you would share your scripts, as this would help a lot!

I have a second question on enabling an external monitor:
While using integrated graphics I did not yet manage to use an external monitor, "VGA1 disconnected". Did anyone manage to connect an external monitor with integrated graphics? What setup is required to do so? (maybe in xorg.conf)?

I am running on Ubuntu 11.04 / 2.6.38-11-generic-pae

Thank you very much in advance!

---

### Post by Andrei.Pozolotin on 2011-09-12
there is a table here

[http://www.lenovo.com/psref/pdf/tabook.pdf](http://www.lenovo.com/psref/pdf/tabook.pdf)

which shows that external monitor works only with nvidia (discrete), not with intel (integrated)

---

### Post by MeikelP on 2011-09-14
Thanks Andrei. 

I am not sure how to interpret the data in the document - I cannot find a definite statement that the Intel bridge does not support external monitors. E.g. If I look at the following statement: 
```
 NVIDIA® OptimusTM technology, auto-switch between discrete and integrated graphics, Intel HD Graphics 3000 in processor, and NVIDIA NVSTM 4200M, PCI Express® x16, 1GB memory, external analog monitor support via VGA DB-15 connector and digital monitor support via DisplayPort (supports single-link DVI-D via cable 45J7915); supports three independent displays; Maximum external resolution: 2560x1600 (DisplayPort)@60Hz; 2048x1536 (VGA)@85Hz; 1920x1200@60Hz (single-link DVI-D via cable 45J7915) 
``` 
I do not see a indication that external monitors will only work with NVidia. Did I miss something? 

Nevertheless - testing with SystemRescueDisk and different graphics modes do proof your statement.

---

### Post by gatman3 on 2011-09-14
On the W520 you can use an external monitor with Integrated (intel) graphics, but VGA only.  To use DVI (digital) monitors you need to run Discrete (nvidia) graphics.  I believe the Lenovo table posted by Andrei makes vague reference to this, although it isn't clear about VGA being available for intel graphics.

It's been a while since I ran intel graphics with an external monitor, but I believe that if I just boot up with the monitor connected to the VGA port (or VGA on the dock) and the monitor is powered on, Ubuntu automatically chooses the VGA monitor as the primary.  This is probably configurable in the System Settings as well.

I believe it is also possible to run a dual monitor setup with Integrated graphics using the laptop's built-in LCD as one monitor and an external VGA as the other.  Doesn't appeal to me, but I believe it's possible.

When I get some time I'll confirm all this.

Also, I responded directly to MeikelP on scripting the auto-switch of the xorg.conf between Integrated and Discrete (undocked vs. docked, for me) but I'll post it to a new thread and link it here when I get some extra time.

EDIT:  I started a new thread to share my method for auto-switching graphics drivers:
[http://ubuntuforums.org/showthread.php?t=1844022](http://ubuntuforums.org/showthread.php?t=1844022)

---

### Post by gatman3 on 2011-09-14
One additional point:  The Lenovo text posted by MeikelP also suggests that the W520 could actually drive 3 independent monitors (!) using nvidia graphics.  I believe this is true based on my recollection of the nvidia configuration utility, although I've never tried it, but you should be able to configure for two DVI monitors plus a VGA monitor.  When I have run in VGA mode with nvidia graphics, the picture quality seemed remarkably crisp, too (older machines I have had were noticeably poorer quality running VGA vs. DVI), so this might be an attractive thing to do if someone wants 3 monitors driven off the dock.

---

### Post by marspokane on 2011-09-14
I have been using Ubuntu 11.04 64bit and have lockups or session restarts randomly with no apparent pattern. I would like to know if I should just be reloading with 32 bit (really don't want to) or if there is another better fix that is a fix instead of work around. It is interesting that this is also happening with W7.

> **wolfindersteppe said:**
> Dear community, does anybody experience randomly shut down with W520? More and more W520 owner running W7 are reporting randomly shut down, see [http://lnv.lithium.com/t5/W-Series-ThinkPad-Laptops/W520-shuts-off-intermittently-no-BSOD-or-shut-down/td-p/459785](http://lnv.lithium.com/t5/W-Series-ThinkPad-Laptops/W520-shuts-off-intermittently-no-BSOD-or-shut-down/td-p/459785) and I somehow suspect W7 faulty drivers and not HW. I was running Ubuntu for maximum 3 weeks without dual booting to W7. Now I had to run W7 for 5 weeks in the row and yesterday I have got the shut down, out of idle. Would be very nice if you guys who run permanently Ubuntu for months and months could report if you have experienced the similar issue? That would help to isolate the issue - HW or faulty W7 drivers related?

---

### Post by VValdo on 2011-09-14
> **marspokane said:**
> I have been using Ubuntu 11.04 64bit and have lockups or session restarts randomly with no apparent pattern. I would like to know if I should just be reloading with 32 bit (really don't want to) or if there is another better fix that is a fix instead of work around. It is interesting that this is also happening with W7.

I'm using integrated (Intel) video w/64 bit Ubuntu-- the latest 3.1 kernel...  and do not have lockups or session restarts.

I do have an issue with wifi, where if I'm downloading a ton at high speed it seems to lock up not only my wireless but most other wireless devices on the LAN.  I'm guessing something is screwed up either at the router or in my network setup somewhere...

---

### Post by wolfindersteppe on 2011-09-20
> **marspokane said:**
> I have been using Ubuntu 11.04 64bit and have lockups or session restarts randomly with no apparent pattern. I would like to know if I should just be reloading with 32 bit (really don't want to) or if there is another better fix that is a fix instead of work around. It is interesting that this is also happening with W7.
marspokane, meanwhile there are more and more facts to support the suspicion that about 10% of delivered W520's are suffering the random shut downs, at least running W7. Going even deeper into details, it seems to be somehow related to CPU power management and some faulty W520 motherboards, i.e by disabling the CPU power management option in BIOS several user are reporting not to experience random shut down for now, further observation is necessary, see [http://forums.lenovo.com/lnv/board/message?board.id=W_ThinkPads&message.id=19866#M19866]("http://forums.lenovo.com/lnv/board/message?board.id=W_ThinkPads&message.id=19866#M19866"). Further information can be found here [http://www.techsupportforum.com/forums/f299/thinkpad-visual-bsod-no-dump-file-created-595476.html#post3430969]("http://www.techsupportforum.com/forums/f299/thinkpad-visual-bsod-no-dump-file-created-595476.html#post3430969") where the MS moderator Jonathan_King is explaining that this event "**The speed of processor 5 in group 0 is being limited by system firmware. The processor has been in this reduced performance state for 71 seconds since the last report.**" would be the reason why random shut downs are occurring and no dump is being made.
Nevertheless, it has to be said that all this was found by the users itself, Lenovo is either ignoring the issue or taking same lukewarm action like "send to support" and support simply replaying back not being able to reproduce the issue (sic!), eventually replacing the motherboard what in several cases did not solve the problem. Even further, Lenovo is blocking the voting on W520 reliability. 
I cannot argument with Ubuntu to Lenovo since Ubuntu is not recognized by Lenovo as official supported system, so any issue has to be reproduced under W7. Bad, bad situation for the users like me suffering the random shut downs.

---

### Post by wolfindersteppe on 2011-09-20
@ALL - could you please be so kind to vote on W520 reliability here [http://forum.notebookreview.com/lenovo-ibm/611616-please-vote-do-you-have-any-issues-your-w520.html]("http://forum.notebookreview.com/lenovo-ibm/611616-please-vote-do-you-have-any-issues-your-w520.html")? Please post that you are running your W520's with Ubuntu. If the co-owners see that the majority of W520 machines running Ubuntu is not affected by any reported issue, wouldn't it be a great commercial in favor of Ubuntu?

---

### Post by VValdo on 2011-09-20
I'm not sure what to say-- I am using this kernel:

```
Linux laptop 3.1.0-0301rc4-generic #201108290905 SMP Mon Aug 29 09:11:07 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

w/o any issues.  W520 w/ubuntu 64 bit latest non-beta (except for kernel).  Only issue I'm having has to do with networking, and I'm pretty sure it's software...

I'm using the latest firmware (I think it was 1.30?) but I didn't have issues with the previous (1.26? I think) either.

---

### Post by marspokane on 2011-09-26
I have the latest (1.30) firmware updated. I have changed the video to each of the 3 options with same or slightly worse results. I will try changing the CPU setting now and see what, if any, difference occurs. Thanks for pointing to the other forums.

---

### Post by dfarrell07 on 2011-10-27
I'm running a W520 with Ubuntu 11.10. I've occasionally had some fairly minor issues that were not too difficult to fix. 

Since upgrading to 11.10, my resume from suspend has been very slow, like must be an error slow. I can boot twice in the time it takes to resume from suspend. It might have to do with my custom setup, which involves storing /tmp/ in RAM, along with the browser cashes. Anyway, I'm sure I'll have that fixed fairly soon.

---

### Post by Andrei.Pozolotin on 2011-11-06
Hi;

just tried to boot from external usb cd - and it hands the w520 bios completely;

the only way to boot at all (say from internal hdd) with external usb cd still connected
is to disable uefi usb cd support in bios, which makes cd unusable for boot, 
but then this external usb cd still works ok under linux;

I am curious if anyone has a workaround for this?

I am running on bios v 1.32

thanks;

Andrei.

---

### Post by otakuj462 on 2011-12-14
Hi,

I just received my Thinkpad W520 today, and I've been extremely happy with my experience running 64-bit Ubuntu 11.10 on it. Almost everything "just works", with both Optimus under nouveau, and just running the Intel graphics (disabling Optimus in the BIOS). 

One thing I have not gotten to work, however, has been the external monitor support via the VGA port. When using Optimus and nouveau, the external VGA monitor shows the Ubuntu boot screen, and when using Intel graphics, the external VGA monitor does not show anything; for both xrandr indicates that X does not detect that a monitor has been plugged into the VGA port.

I have read some posts here that indicate that it is possible to get external monitor support working, possibly even with just the Intel graphics. I'd appreciate it if someone could confirm this, and if possible, let me know how you may have gotten it working. Alternatively, if there's a technique to get the external monitor working with nouveau, I'd like to hear about that too.

I'd prefer to stay away from the proprietary drivers, as I've heard they can be unstable, particularly on the 64-bit kernel.

I'd appreciate any guidance anyone can offer. Thanks.

---

### Post by hemmecke on 2011-12-15
> **otakuj462 said:**
> 
One thing I have not gotten to work, however, has been the external monitor support via the VGA port. When using Optimus and nouveau, the external VGA monitor shows the Ubuntu boot screen, and when using Intel graphics, the external VGA monitor does not show anything; for both xrandr indicates that X does not detect that a monitor has been plugged into the VGA port.


Oh yes. Would be nice if somebody could produce a step by step instruction.

> **otakuj462 said:**
> 
I'd prefer to stay away from the proprietary drivers, as I've heard they can be unstable, particularly on the 64-bit kernel.


Can you cite where exactly you've read that?

Anyway. The standard settings in the BIOS are "Optimus" and detection of the OS whether to use the integrated (intel) or discrete (nvidia) graphics "enabled". Maybe it is of no relevance to Ubuntu, but with these standard settings I only can switch to "TwinView" under Windows.  "Dual" does not work, but I could choose "external only". All of that is a bit annoying.

Setting "discrete graphics" and os detection to "disabled" in the BIOS, let's me have all possible options (including "dual view") under windows.

I've not yet been able to satisfactorily get an external monitor working under Ubuntu. (BIOS: "discrete graphic" and "os detection disabled")

Some time ago I experimented with nvidia-xconfig and nvidia-settings, but I only managed to get twinview with an xorg.conf that would not switch to graphics mode if the external monitor was not connected. The xorg.conf settings didn't look appropriate to me. I did not yet have time to figure out the details.

Any help is appreciated, whether nouveau or the proprietary driver I don't care so much, but it would be wonderful to get **detailed **hints of how the setting must be done.

Anyone, who has it working and would like to share his/her xorg.conf and other setup parameters to make an external monitor work?

Ralf

---

### Post by hemmecke on 2011-12-15
> **VValdo said:**
> Yes by running ThinkFan.
Yes, thinkfan can be configured to turn the fan off at lower temps.


Waldo or anybody who has setup thinkfan... my I ask you to share your thinkfan configuration?

sensors-detect  suggested to add "coretemp" to /etc/modules. "sensors" now shows:

```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +52.0°C  (crit = +99.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +53.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +51.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +52.0°C  (high = +86.0°C, crit = +100.0°C)
Core 2:         +48.0°C  (high = +86.0°C, crit = +100.0°C)
Core 3:         +46.0°C  (high = +86.0°C, crit = +100.0°C)

thinkpad-isa-0000
Adapter: ISA adapter
fan1:        2548 RPM

```Since I don't see /proc/acpi/ibm/thermal for my Ubuntu 11.10 (64bit), I tried with the following in /etc/thinkfan.conf.
```

sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input
sensor /sys/devices/platform/coretemp.0/temp1_input
sensor /sys/devices/platform/coretemp.0/temp2_input
sensor /sys/devices/platform/coretemp.0/temp3_input
sensor /sys/devices/platform/coretemp.0/temp4_input
sensor /sys/devices/platform/coretemp.0/temp5_input

(0,    0,    55)
(1,    48,    60)
(2,    50,    61)
(3,    52,    63)
(4,    56,    65)
(5,    59,    66)
(7,    63,    32767)

```But that doesn't switch of the fan even if the temperatures are below 48C.

I am also not completely sure where or what is the temperature for my HDD. It doesn't seem to appear on the output of "sensors".

And yes, I have
/etc/modprobe.d/thinkfan.conf with
```
options thinkpad_acpi fan_control=1

```
but still, my fan is not going below 2000rpm.

Ralf

---

### Post by dimm0k on 2011-12-15
> **hemmecke said:**
> Oh yes. Would be nice if somebody could produce a step by step instruction.



Supposedly the VGA output is only connected to the discrete graphics and not the integrated so the VGA is not functional if you have the BIOS set to integrated.  Since Optimus doesn't work under Linux, I believe you'll need to have it set to discrete...

---

### Post by hemmecke on 2011-12-15
> **dimm0k said:**
> Since Optimus doesn't work under Linux, I believe you'll need to have it set to discrete...

If this sentence is for the VGA output, I tend to agree.

Otherwise, my Laptop runs fine with Optimus and "os detection enabled". Even 3d acceleration works. (I guess, Optimus means "integrated with the option of switching if there is a signal from the OS".)

I've just problems with a non-working VGA output.

Ralf

---

### Post by VValdo on 2011-12-26
> **hemmecke said:**
> Waldo or anybody who has setup thinkfan... my I ask you to share your thinkfan configuration?

sensors-detect  suggested to add "coretemp" to /etc/modules. "sensors" now shows:

```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +52.0°C  (crit = +99.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +53.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +51.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +52.0°C  (high = +86.0°C, crit = +100.0°C)
Core 2:         +48.0°C  (high = +86.0°C, crit = +100.0°C)
Core 3:         +46.0°C  (high = +86.0°C, crit = +100.0°C)

thinkpad-isa-0000
Adapter: ISA adapter
fan1:        2548 RPM

```

Mine:

```
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +56.0°C  (crit = +99.0°C)

nouveau-pci-0100
Adapter: PCI adapter
temp1:        +55.0°C  (high = +100.0°C, crit = +110.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +58.0°C  (high = +86.0°C, crit = +100.0°C)
Core 0:         +56.0°C  (high = +86.0°C, crit = +100.0°C)
Core 1:         +56.0°C  (high = +86.0°C, crit = +100.0°C)
Core 2:         +55.0°C  (high = +86.0°C, crit = +100.0°C)
Core 3:         +54.0°C  (high = +86.0°C, crit = +100.0°C)

thinkpad-isa-0000
Adapter: ISA adapter
fan1:        2704 RPM
```

For the last few months I've been using this:

```
sensor /sys/devices/platform/coretemp.0/temp1_input
sensor /sys/devices/platform/coretemp.0/temp2_input
sensor /sys/devices/platform/coretemp.0/temp3_input
sensor /sys/devices/platform/coretemp.0/temp4_input
sensor /sys/devices/platform/coretemp.0/temp5_input
sensor /sys/devices/virtual/hwmon/hwmon0/temp1_input
sensor /sys/devices/virtual/thermal/thermal_zone0/temp

(0,     0,     30)
(1,     27,     50)
(2,     50,     55)
(3,     52,     60)
(4,     59,     63)
(5,     62,     64)
(6,     63,      65)
(7,     63,     32767)
```

As you can see from the numbers, they don't quite make sense...  I'm still figuring it out.  I'm also annoyed still by these incredibly annoying messages in dmesg that appear even when my reported temps are 55C...

```
[96287.773585] CPU0: Package power limit notification (total events = 130258)
[96287.776576] CPU0: Package power limit normal
```

They appear when I'm building something.  They appear when I'm idle... go figure.

Also, no it doesn't look like:

sensor /sys/devices/virtual/thermal/thermal_zone0/temp1_input

exists any more

I probably should go through this again with the current kernel and fix everything.  The current kernel btw:


$ uname -a
Linux laptop 3.2.0-030200rc6-generic #201112162235 SMP Sat Dec 17 03:36:15 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Looks like there's an [rc7]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc7-precise/") too.

If I get a chance, I'll play with it and report back.

---

### Post by sunbergzach on 2012-01-12
Hello everyone,

I have prepared a blog post that I think will help people understand the graphics situation:

[http://zachstechnotes.blogspot.com/2012/01/tri-head-display-on-linux-thinkpad-w520.html](http://zachstechnotes.blogspot.com/2012/01/tri-head-display-on-linux-thinkpad-w520.html)

I am using kubuntu 11.10, so there may be some minor differences regarding how well things work for people using regular ubuntu, but hopefully this will help people... I have spend alot of time figuring these things out.

---

### Post by mmludin08 on 2012-02-10
> **gatman3 said:**
> Update on my experiences...

64-bit is a no go, at least for me.  I tried 10.10 and 11.04.  10.10 was a total disaster; the machine would sometimes hang on boot, and sometimes ran at an incredibly slow speed (move the mouse, wait 30 seconds, etc.)  11.04 ran better at 64-bit, but the best I could get was to run with NVidia proprietary graphics with a kernel update (2.6.39-0) and disabling ACPI as a kernel boot option (acpi=off).  With intel graphics it worked better but it seemed sluggish at times and suspend was flaky.  There were various other problems, such as broken VMWare due to the 2.6.39-0 kernel.

When I switched to 32-bit on 11.04 the storm clouds parted and everything just worked.  Fortunately, 32-bit uses a PAE kernel that makes use of >4GB RAM (I have 8 GB, and all of the memory is available).  When I'm docked I used the NVidia proprietary driver with a dual-monitor display, and when I'm undocked I switch to the integrated (Intel) graphics (I have a boot script to auto-detect which graphics chip is present and auto-switch the xorg.conf, because intel barfs if the nvidia xorg.conf is present, and nvidia needs its own xorg.conf).  With the integrated graphics, suspend also seems to work fine now too, I was successful testing 10 out of 10 suspend cycles.

For me, at least, the 32-bit version of Ubuntu 11.04 is golden on this machine.  The 64-bit versions of Ubuntu are a mess on this machine.

Hi, 
I am newbe to Linux. i have used debian for while, but i am  moving to ubuntu. I just bought the Thinkpad W520. I am having bit  issues with my graphic cards. I installed the Ubuntu 11.10 - 32-bit. I  was wondering if you have upgraded from 11.04 to 11.10 or not? if yea,  is everything working with your machine? 

Also, I am doing  CS-major. but not very good in programming yet. need to take more  classes i guess. If you dont mind could i take look at your scrip for  switching the graphic cards? that will be amazing. 

in my  machine, xbmc, celestial, and some other softwares that needs  accelarated opengl rendering doesnt work, and it ask to install  appropriate graphic drivers. 

I found you the most expert on this issue. And i would really appreciate your help. Thanks in advance.

---

### Post by nightalon on 2012-03-15
I think suspend-to-RAM is still broken when a DisplayPort/HDMI monitor is attached.  Please confirm!

---

### Post by pipehappy on 2012-04-10
I just install ubuntu 11.10 64bit on company's w520. It works in most part. But you have to set the graphical card to discrete mode to use to dock to drive external monitor. And I have tried the proprietorial driver option. It doesn't work and even cannot dim the main monitor. I haven't try to figure the bio figure print sensor. Other stuff works fine in general.

---

### Post by sunbergzach on 2012-04-30
Here's a way to get an external monitor to work in nvidia optimus bios mode without having to restart X or use separate X servers:

[http://zachstechnotes.blogspot.com/2012/04/post-title.html](http://zachstechnotes.blogspot.com/2012/04/post-title.html)

---

### Post by sunbergzach on 2012-04-30
Here's a way to use an external monitor with xrandr. i.e. you won't need to restart X or use a separate X server for each screen:

[http://zachstechnotes.blogspot.com/2012/04/post-title.html](http://zachstechnotes.blogspot.com/2012/04/post-title.html)

---

