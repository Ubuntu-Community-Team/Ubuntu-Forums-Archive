---
title: "How get powernow to work?"
date: 2005-10-22
forum: Hardware &amp; Laptops
---

### Post by TTL on 2005-10-22
Hello,
I am trying to use frequency changing with powernowd on my laptop (AMD Mobile Sempron  2800+):
**modprobe cpufreq_powersave**   ->   is loaded successfully
**modprobe powernow-k8**   ->   *FATAL: Error inserting powernow_k8 (/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/cpu/cpufreq/powernow-k8.ko): No such device *
when looking into **dmesg** i see:
[I]powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.40.4)
powernow-k8: BIOS error: maxvid exceeded with pstate 1[/I]

Trying to start **powernowd**  I get an error:
[I]powernowd: PowerNow Daemon v0.96, (c) 2003-2005 John Clemens
powernowd: Found 1 cpu:  -- 1 thread (or core) per physical cpu
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory
PowerNowd encountered and error and could not start.[/I]

In fact, /sys/devices/system/cpu/cpu0 is an empty folder.
I am using the 2.6.12-9-386 kernel and need to boot with the noapic options since otherwise everything (like the system clock) is running twice as fast as normally.

I guess that I need to load the powernow-k8 module before starting nowernowd but I did not figure out how to get around the error message in dmesg.

Could anyone help me? Thank you in advanced.

Update:
I have solved my problem, see solution on the next page.

---

### Post by blackpaw on 2005-10-23
Hi!

I have the same problem, together with this user:
[http://ubuntuforums.org/showthread.php?t=73974]("http://ubuntuforums.org/showthread.php?t=73974")

We both have a coppermine-cpu and ACPI says that there are 8 throttling-levels
> [4294678.935000] ACPI: Processor [CPU0] (supports 8 throttling states)
But Powernowd complains that there is
> powernowd: Found 1 cpu:  -- 1 thread (or core) per physical cpu
/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq: No such file or directory
PowerNowd encountered and error and could not start.
Please make sure that:
 - You are running a v2.6.7 kernel or later
 - That you have sysfs mounted /sys
 - That you have the core cpufreq and cpufreq-userspace
   modules loaded into your kernel
 - That you have the cpufreq driver for your cpu loaded,
   and that it works. (check dmesg for errors)
If all of the above are true, and you still have problems,
please email the author: [email]clemej@alum.rpi.edu[/email]

Do I have to compile a new kernel now?

thanks for any help!


andreas

---

### Post by davmac on 2005-10-23
Exactly same problem here on a Dell Inspiron 510m...

Dave Mac

---

### Post by jamieson on 2005-10-27
Powernowd is running on my Dell L400 notebook, but there's a 1 second pause whenever it changes the CPU frequency.  Very annoying, and no error or warning messages in the /var/log files.  Anyone else having this problem?

---

### Post by invalid on 2005-10-27
[QUOTE=jamieson]Powernowd is running on my Dell L400 notebook, but there's a 1 second pause whenever it changes the CPU frequency.  Very annoying, and no error or warning messages in the /var/log files.  Anyone else having this problem?[/QUOTE]

I am.. and the only thing I can do to stop it is to kill powernowd..
I would like not to do this.. and it has been a problem all the way back since pre-Hoary

---

### Post by TTL on 2005-10-29
Um.., since we now know how to stop powernow (by killing the process) ;) , may I come back to my original question how to get it working :confused: 

Thank you.

---

### Post by Chrissss on 2005-10-29
@blackpaw

I posted the solution at the bottom of the last article :)

---

### Post by TTL on 2006-01-05
Looks like
```
powernow-k8: BIOS error: maxvid exceeded with pstate 1
```
is the main problem. I read that this has todo somthing with the DSDT table. Does anyone how to fix this?

---

### Post by blackpaw on 2006-01-05
Hey Chrissss!

[QUOTE=Chrissss]@blackpaw

I posted the solution at the bottom of the last article :)[/QUOTE]

You mean this article?
[http://ubuntuforums.org/showthread.php?t=73974]("http://ubuntuforums.org/showthread.php?t=73974")

My problem is: with default ubuntu-Kernels I don't have the speedstep-modules in my /kernel/arch/i386/kernel/cpu/cpufreq/

UPDATE:
I compiled myself a new 2.6.12 Kernel with suspend2 compiled in and all powersave-modules active, now I have both modules but when I try to reload the -smi, I get 
> FATAL: Error inserting speedstep_smi (/lib/modules/2.6.12-hibernate/kernel/arch/i386/kernel/cpu/cpufreq/speedstep-smi.ko): No such device

Somehow I feel like I am really close ;)
What else could have gone wrong? 

And: How do I load a driver for cpufreq? cpufreq-info complains about "no or unknown driver is active on this CPU"

---

### Post by TTL on 2006-08-06
After trying to fix my problem over 9 months long I finally succeed. I had to extract the DSDT, decompile it, fix an error in the table, recompile it, apply a patch to my custom compiled kernel, put the fixed dsdt into the initrd image and finally it is now working. The result of this: around 20% longer battery power and a more silent laptop :-D

---

### Post by mmanzato on 2006-08-29
TTL,

how did you manage that? I have the very same problem with my ASUS W3Z: modprobe powernow-k8 gives this unfriendly BIOS Error message and stops there... ](*,)

Thanks a lot

---

### Post by TTL on 2006-09-01
Ok, I will give you some hints: Since I think this is only something for someone with already some Linux knowledge I will not describe every step in detail.
[LIST]
[*]First aptget the the Intel compiler **iasl**. It is available in uni- or multiverse.
[*]Then cat your DSDT from **/proc/acpi/dsdt** into a file.
Decompile the file you saved, with iasl by calling **iasl -d yourfilename **
[*]Then recompile by calling ** iasl -tc dsdt.dsl** and watch which errors were generated.
[*]Fix this error by searching for the error messages in the net. _ Warning: wrong values in the file will damage you CPU (Overvoltage + Overclocking) _ I found a solution for my errors at:
[http://katherina.student.utwente.nl/~matthijs/cgi-bin/blosxom/Hardware/S270/BrandNew.html](http://katherina.student.utwente.nl/~matthijs/cgi-bin/blosxom/Hardware/S270/BrandNew.html)
[*]Try fixing the errors until the compiler works without warnings and errors any more.
[*]In the case you use a vanilla kernel you have to apply the patch from [http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml) and recompile. I heard that the common Ubuntu kernel has this patch already included, but I am unsure about this.
[*]Copy the new compiled DSDT.aml file to /etc/mkinitramfs/
[*]Create a new mkinitramfs image. I forgot how this worked exactly I guess it was something with ** mkinitrd ** and some parameters.
Reboot and hope it works.
[/LIST]
Please note that that in the case something went wrong your Linux might not start (running an allredy installed older, not modified Kernel might help then) anylonger and that wrong values in the DSDT Table have a relative high possibility to permanently damage your computer.

Please tell me if you had success with this.
TTL

Update:
Since there were differences from the procedure above with Kubuntu 7.04:
You should create the file now by
**iasl dsdt.dsl**
(so leave the -tc parameters away).
Then the name of the directory where the DSDT.dsl should be stored has changed and is now:
**/etc/initramfs-tools**
Then finally you can create the initramfs image with the command
**sudo dpkg-reconfigure linux-image-2.6.20-16-generic**
fit this command to the current kernel name report by uname -r.
Then reboot and enjoy.

---

### Post by mmanzato on 2006-09-01
Thank you very much.
I will try and let you know what happens.
Michele

---

### Post by mmanzato on 2006-09-24
Sorry for the long silence. I had to find some spare time to sit and try  it out.

Indeed at last I succeeded, thanks to your suggestions! Now when I load the powernow-k8 module I get no error at all and dmesg says:

```

powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.60.2)
powernow-k8:    0 : fid 0xa (1800 MHz), vid 0xa (1300 mV)
powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xc (1250 mV)
powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x16 (1000 mV)

```

Editing the dsl code isn't that complicated. I still have no knowledge of AML at all but I manage to fix errors and warnings quite easily by referring to the various resources that are pointed out in the link that you provided.

Dirreferntly from what you did, I put the compiled DSDT directly into the kernel by following "way #3" in the Gentoo Wiki HOWTO.

Now the fan is much less noisy when the CPU load is low, although the fan itself seems "always on". I'll check if battery lasts any longer.

TTL, thanks a whole lot for your support!!!

Michele

---

### Post by grahams on 2006-09-29
I had similar problems and found that powernowd was not starting correctly. Try running powernowd from the command line (sudo). In my case it would not start, but the error text was helpful. After checking I found cpufreq was not running (lsmod | grep cpu), even though libcpufreq0 claimed to be installed. After I reinstalled libcpureq0, powernowd and frequency scaling work correctly. 

This is what I have running

:lsmod |grep cpu 
cpufreq_stats           6688  0
cpufreq_conservative     9000  0
cpufreq_ondemand        7752  0
cpufreq_powersave       1920  0
freq_table              4928  2 cpufreq_stats,speedstep_ich
cpufreq_userspace       6496  1

---

