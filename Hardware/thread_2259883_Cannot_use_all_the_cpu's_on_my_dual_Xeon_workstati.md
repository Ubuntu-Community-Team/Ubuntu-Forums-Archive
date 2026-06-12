---
title: "Cannot use all the cpu's on my dual Xeon workstation"
date: 2015-01-07
forum: Hardware
---

### Post by max-korobase on 2015-01-07
Hello there,
I recently started messing around with an old dual Xeon workstation. Each processor is a Xeon E5450 @ 3GHz, so in total I should have 8 cpu's:
```
$ lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                8
On-line CPU(s) list:   0-7
Thread(s) per core:    1
Core(s) per socket:    4
Socket(s):             2
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 23
Model name:            Intel(R) Xeon(R) CPU           E5450  @ 3.00GHz
Stepping:              10
CPU MHz:               1998.000
CPU max MHz:           3000,0000
CPU min MHz:           1998,0000
BogoMIPS:              6000.26
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              6144K
NUMA node0 CPU(s):     0-7
```
I unstalled Gnome Ubuntu 14.04 without a problem:
```
$ uname -a
Linux scrap 3.16.0-28-generic #38-Ubuntu SMP Fri Dec 12 17:37:40 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```
Now, what bugs me is that, apparently I cannot get all the cpu's to work.

I tried to run povray's benchmark with the Work_Threads flag enabled like so:
```
$ povray benchmark.ini Work_Threads=8
```
but all I get is:
[TABLE="width: 500"]
[TR]
[TD]CPU1: 100%[/TD]
[TD]CPU5: 100%[/TD]
[/TR]
[TR]
[TD]CPU2: 0%[/TD]
[TD]CPU6: 0%[/TD]
[/TR]
[TR]
[TD]CPU3: 0%[/TD]
[TD]CPU7: 0%[/TD]
[/TR]
[TR]
[TD]CPU4: 0%[/TD]
[TD]CPU8: 0%[/TD]
[/TR]
[/TABLE]

Mmmm...
Next thing I did was to compile a small c file containing only one infinite loop and launch, in sequence, the resulting executable file as distinct processes. My expectation was that each process would go on a different CPU and could eventually see all of them running.

The first one:
```
$ ./loop &
[1] 4349
```
resulting in CPU1: 100%. OK!

After launching the second one:
```
$ ./loop &
[2] 4353
```

I see both CPU1 and CPU5 at 100%. So far so good.

Then I launched 6 more processes and the result was disappointing:
Only CPU1 and CPU5 are being used at 100% and of course each process takes about 25% of CPU time:
[TABLE="width: 500"]
[TR]
[TD]CPU1: 100%[/TD]
[TD]CPU5: 100%[/TD]
[/TR]
[TR]
[TD]CPU2: 0%[/TD]
[TD]CPU6: 0%[/TD]
[/TR]
[TR]
[TD]CPU3: 0%[/TD]
[TD]CPU7: 0%[/TD]
[/TR]
[TR]
[TD]CPU4: 0%[/TD]
[TD]CPU8: 0%[/TD]
[/TR]
[/TABLE]

The remaining CPU are still lazily idling...

What's wrong in my reasoning?

Thanks
maxino

---

### Post by max-korobase on 2015-01-08
Some more interesting (at least for me) findings.
(in case helps, here's the topology of my dual xenons):
[IMG]http://i60.tinypic.com/rr58j5.png[/IMG]

Now, when I launch for 8 times my CPU-wasting loop using the taskset command:
```
$ taskset -c 0 ./loop &
```
with the flag -c value ranging from 0 to 7, I can see *all* of my CPUs are actually 100% loaded and everything works as expected but here I am "manually forcing" the threads to be assigned to all the CPUs in turn.

If I simply launch 8 times:
```
$ ./loop &
```
then apparently all the 8 process gets assigned *only* to CPU1 and CPU5 (which are both at 100%, as reported by htop, and each process gets 25% of CPU time).

Why doesn't the kernel, by default, assign the process to all of the available CPU?
Shouldn't the kernel tales care of balancing the load? It rather seems to favour only CPU1 and CPU5.

Perhaps that's also the reason why I cannot get povray to use all the 8 CPUs, even using the flag "[COLOR=#000000][FONT=Ubuntu Mono]Work_Threads=8".

[/FONT][/COLOR]Can anyone enlighten me?

thx
maxino

---

### Post by Doug S on 2015-01-08
> **max-korobase said:**
> Why doesn't the kernel, by default, assign the process to all of the available CPU?It should.> **max-korobase said:**
> Shouldn't the kernel tales care of balancing the load?Yes, it should.

The last time I was involved in a similar (yet different) [thread]("http://ubuntuforums.org/showthread.php?t=2251879"), the root issue was a BIOS setting and confusion between SMP and NUMA settings.

---

### Post by max-korobase on 2015-01-09
> **Doug S said:**
> The last time I was involved in a similar (yet different) [thread]("http://ubuntuforums.org/showthread.php?t=2251879"), the root issue was a BIOS setting and confusion between SMP and NUMA settings.

That's interesting, thanks. Very similar problem than mine, indeed.
Unfortunately, unlike that thread's OP, on my workstation I can't find any BIOS setting that have anything to do with SMP, NUMA, or stuff like that :-(

---

### Post by max-korobase on 2015-01-10
I bit the bullet and installed Fedora 21:
```
# uname -a
Linux scrap 3.17.7-300.fc21.x86_64 #1 SMP Wed Dec 17 03:08:44 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

Now everything works as it should.
All of the CPUs are being engaged after repeatedly launching cpuburners from the CLI and povray grinds happily through its benchmark making full use of all its threads.

I'm hesitant to mark this thread as SOLVED, though, because I still don't have a clue about what was wrong with my previous Ubuntu 14.10 (kernel 3.16.0-28-generic #38-Ubuntu SMP).

I'd be glad to get back to Ubuntu if I ever understand (and solve) the issue.

Now let's get acquainted with Fedora 21...

Cheers,
maxino

---

### Post by sudodus on 2015-01-10
Did you try Ubuntu ***14.04.1 LTS***? It is better debugged and polished compared to 14.10. Or did you try Ubuntu ***Vivid*** (to become 15.04)?

I'm still running Ubuntu ***12.04.5 LTS*** in my HP xw8400 workstation with xeon, and it works well for example to convert video with ffmpeg with all processors. End of life of standard Ubuntu, Kubuntu and Ubuntu Server 12.04.5 LTS is April 2017, so still several years to go.

I usually check the performance with ***htop***, which shows quite well how the CPUs are used.

```
sudo apt-get install htop
```

---

### Post by Doug S on 2015-01-10
We could compare the config files for the two kernels. You would also test a more recent kernel (currently 3.19RC3 is the latest release candidate) on an Ubuntu installation.

---

### Post by Yellow Pasque on 2015-01-10
This looks interesting, but I'm not sure if it's what's going on here:
[http://www.mjmwired.net/kernel/Documentation/IRQ-affinity.txt](http://www.mjmwired.net/kernel/Documentation/IRQ-affinity.txt)
[http://www.alexonlinux.com/smp-affinity-and-proper-interrupt-handling-in-linux](http://www.alexonlinux.com/smp-affinity-and-proper-interrupt-handling-in-linux)

What mobo are you using? Any BIOS updates available?

---

### Post by max-korobase on 2015-01-10
> **sudodus said:**
> Did you try Ubuntu ***14.04.1 LTS***? It is better debugged and polished compared to 14.10. Or did you try Ubuntu ***Vivid*** (to become 15.04)?

I just installed 14.04 LTS, and it was not smooth process - I had a few video problems ("black screen of death"), network config applet mysteriously disappearing and reappearing (now it's apparently gone for good, but I don't care since I managed to configure my NIC anyway).
The kernel is:
```
~$ uname -a
Linux scrap 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64
```
And I am happy to confirm that it works! The scheduler now distributes the load to all the processors no matter what I throw at it: bunches of cpuburners, multi-threaded povray benchmarks, mindless loops, etc :-)

I barely know what I am talking about, but it appears to me that Ubuntu's 14.10 kernel (3.16.0-28-generic #38-Ubuntu SMP) scheduler did not somehow agree with my system/motherboard.

This last 14.04 and Fedora 21 appear to work flawlessly.

[QUOTE=Doug S]We could compare the config files for the two kernels. You would also test a more recent kernel (currently 3.19RC3 is the latest release candidate) on an Ubuntu installation.[/QUOTE]
I am afraid that comparing config files is way above my noob-ness.
In a nutshell:

[TABLE="width: 500"]
[TR]
[TD]3.13.0-43-generic #72-Ubuntu SMP (14.04 LTS)[/TD]
[TD]OK[/TD]
[/TR]
[TR]
[TD]3.17.7-300.fc21.x86_64 #1 (Fedora 21)[/TD]
[TD]OK[/TD]
[/TR]
[TR]
[TD]3.16.0-28-generic #38-Ubuntu SMP (14.10)[/TD]
[TD]NOT OK[/TD]
[/TR]
[/TABLE]


[QUOTE=Temüjin]What mobo are you using? Any BIOS updates available?[/QUOTE]
Thanks for the docs links.
ABout the mobo:
```
$ sudo dmidecode -t 2
# dmidecode 2.12
SMBIOS 2.5 present.


Handle 0x0003, DMI type 2, 8 bytes
Base Board Information
    Manufacturer: Hewlett-Packard
    Product Name: 0A9Ch
    Version: NA
    Serial Number: CZC91860JY

```

I haven't investigated yet if there are BIOS updates, but will do.



Thanks everybody!!!

---

### Post by Yellow Pasque on 2015-01-10
If you really want to find the fault, then file a bug on Launchpad and someone will probably ask you to do kernel bisection (to see which commit caused the fault).

---

### Post by Doug S on 2015-01-10
So it is clear that there was a regression introduced. While much less clear, that regression may have been fixed, and just hasn't yet found its way back to the 3.16 series kernels.> **Temüjin said:**
> If you really want to find the fault, then file a bug on Launchpad and someone will probably ask you to do kernel bisection (to see which commit caused the fault).I don't think that is needed just yet, but ultimately yes.

@max-korobase: Are you willing to investigate further? (Note: an answer of "No" is perfectly acceptable.)

If yes, I would try some more kernels from the [kernel PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/") to attempt to determine if the issue persists through more recent kernels or not. The work can be done on your existing 14.04 installation.
Since kernel 3.16.0-28.38 is based on 3.16.7-ckt1, I would be tempted to try [3.16.7-ctk3]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.16.7-ckt3-utopic/") first. If it didn't work I would try [3.17.8-vivid]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.17.8-vivid/") next.

---

### Post by max-korobase on 2015-01-10
> **Doug S said:**
> @max-korobase: Are you willing to investigate further? (Note: an answer of "No" is perfectly acceptable.)

Yes.
Let me just dig up some noob-proof instructions on how to swap kernels without wrecking the whole thing...

---

### Post by Doug S on 2015-01-10
> **max-korobase said:**
> Let me just dig up some noob-proof instructions on how to swap kernels without wrecking the whole thing...If you want, I can help with that.

I would:

first, make it so that the grub menu was visible during boot and had a longer timeout, to give sufficient time to get to it and select which kernel to boot. For example, change the timeout line in /etc/default/grub to:```
GRUB_TIMEOUT=20
```And after editing grub run:```
sudo update-grub
```Perhaps test this before making any kernel changes.

second install the test kernel. The example is 3.19RC1 which had been downloaded from the PPA into the current duretory```
sudo dpkg -i linux-headers-3.19.0-031900rc1_3.19.0-031900rc1.201412210135_all.deb
sudo dpkg -i linux-headers-3.19.0-031900rc1-generic_3.19.0-031900rc1.201412210135_amd64.deb
sudo dpkg -i linux-image-3.19.0-031900rc1-generic_3.19.0-031900rc1.201412210135_amd64.deb
```Third re-boot, accessing the grub menu during boot to select the desired kernel.

Later on, you will want to clean up. Suggest to use this to get the list of stuff:```
dpkg -l | grep linux-
```You can use copy and paste to avoid typing.```
sudo dpkg -r linux-headers-3.19.0-031900rc1-generic
sudo dpkg -r linux-headers-3.19.0-031900rc1
sudo dpkg -P linux-image-3.19.0-031900rc1-generic
```

---

### Post by max-korobase on 2015-01-11
Here are some findings.

**Baseline test **(current kernel 3.13.0-43-generic)
Booting ```
Linux scrap 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:06 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```
The purpose of this test was only to confirm once again that in my current setup there are no problems of CPU usage.

After launching 8 times ```
burnK6 &
``` from the CLI, all of the 8 processors are being loaded at 100% -> OK
After launching ```
povray +WT8 benckmark.ini
``` from the CLI, all of the 8 processors are being loaded at 100% -> OK

**Test 1 **(new kernel  3.16.7-ctk3, as suggested)
Booting ```
Linux scrap 3.16.7-031607-generic #201412191035 SMP Fri Dec 19 10:36:57 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

After launching 8 times ```
burnK6 &
``` from the CLI, all of the 8 processors are being loaded at 100% -> OK
After launching ```
povray +WT8 benckmark.ini
``` from the CLI, all of the 8 processors are being loaded at 100% -> OK

**Test 2 **(here I go back to the kernel I originally had problems with)
Booting ```
Linux scrap 3.16.0-031600-generic #201408031935 SMP Sun Aug 3 23:36:11 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```
Please note that the description string is not identical to the one I indicated in my very first post, which was:
```
Linux scrap 3.16.0-28-generic #38-Ubuntu SMP Fri Dec 12 17:37:40 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```
Not sure if that makes any difference.
The purpose of this test was only to reproduce/confirm the fault.

*And here's the twist...*
After launching 8 times ```
burnK6 &
``` from the CLI, all of the 8 processors are being loaded at 100% -> OK
After launching ```
povray +WT8 benckmark.ini
``` from the CLI, all of the 8 processors are being loaded at 100% -> OK

*So... I am unable to reproduce again the problem, therefore I guess the analysis in invalid* :-(

On the bright side, I am a happy customer now since everything works as it should.

---

### Post by Doug S on 2015-01-11
Thanks for your thorough work on this.> **max-korobase said:**
> *So... I am unable to reproduce again the problem, therefore I guess the analysis in invalid* :-(Yes, quite right. If you couldn't reproduce the fail scenario then nothing has been proved for certain.

I wonder if I made a mistake when I said:> Since kernel 3.16.0-28.38 is based on 3.16.7-ckt1I determined that from looking at the config files.```
doug@desk-dev:/boot$ [COLOR=#ff0000]grep CONFIG_VERSION_SIGNATURE config*[/COLOR]
config-3.16.0-22-generic:CONFIG_VERSION_SIGNATURE="Ubuntu 3.16.0-22.29-generic 3.16.4"
config-3.16.0-23-generic:CONFIG_VERSION_SIGNATURE="Ubuntu 3.16.0-23.31-generic 3.16.4"
config-3.16.0-24-generic:CONFIG_VERSION_SIGNATURE="Ubuntu 3.16.0-24.32-generic 3.16.4"
config-3.16.0-28-generic:CONFIG_VERSION_SIGNATURE="[COLOR=#ff0000]Ubuntu 3.16.0-28.38-generic 3.16.7-ckt1[/COLOR]"
```Obviously work continued between the original PPA posting and the final release.
The very exact same release kernel can be fetched as .deb files from [the launchpad release page]("https://bugs.launchpad.net/~canonical-kernel-team/+archive/ubuntu/ppa/+build/6639809"). (Note: 4 files needed in this case)

---

### Post by max-korobase on 2015-01-11
[QUOTE=Doug S]Thanks for your thorough work on this.[/QUOTE]

Not thorough enough, Doug. There is one thing left do... go all the way back to where I started from!!!

I wiped off everything and installed again, from scratch, the Ubuntu 14.10 that gave me so much headache :-)
Now we are back to the "presumably faulty" kernel:
```
Linux scrap 3.16.0-28-generic #38-Ubuntu SMP Fri Dec 12 17:37:40 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

After launching 8 instances of the burner:
```
~$ burnK6 &
[4] 3977
~$ burnK6 &
[5] 3978
~$ burnK6 &
[6] 3979
~$ burnK6 &
[7] 3980
~$ burnK6 &
[8] 3981
~$ burnK6 &
[9] 3982
~$ burnK6 &
[10] 3983
~$ burnK6 &
[11] 3984
```
Only 2 CPUs (0 and 4) are being used!!!
See 'top' screenshot:
[IMG]http://i57.tinypic.com/2ed1i5e.jpg[/IMG]

Same thing with the multi-threaded povray benchmark:
```
~$ povray +WT8 benchmark.ini
```
Again only CPU 0 and 4 are loaded:
[IMG]http://i60.tinypic.com/5l6l1t.png[/IMG]

 *So the thing is misbehaving again!!!*

Interesting huh?!
I'd say that kernel 3.16.0-28-generic #38 definitely does not like me (and my poor old computer) :-)

---

### Post by Doug S on 2015-01-11
While I have searched for possible related bug reports before, sometimes it can be hard to get the correct keywords and get a hit. This time I think I got it. [This one]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1386473") sounds exactly like your issue.

---

### Post by max-korobase on 2015-01-11
Yes, that's it, Doug S.
Well, I had fun testing/reinstalling and even managed to learn a thing or two in the process.

Now I am running 3.16.7-031607-generic #201412191035 on top of my last Ubuntu 14.10 installation and everything's OK.

Thanks to all who chimed in.

---

