---
title: "Lubuntu 18.04, Dell e1505n and USB"
date: 2021-04-21
forum: Hardware
---

### Post by deck on 2021-04-21
I am inquiring here first before I post to the Hamlib email.

I have a Dell e1505n laptop purchased new in 2007 when Dell released this model with Ubuntu Linux on it from the factory.  An install of Ubuntu is a bit too much for the computing power of this computer.  I have upgraded it to the maximum of 4 GB installed (3 something GB usable) RAM but still regular Ubuntu performs too slowly.  So I installed Lubuntu 18.04.5 on it and it works pretty well.  My intent is to use this laptop for amateur radio purposes.  One of those is to control an ICOM IC9700 VHF/UHF radio to track satellites when I take the radio to other locations than my home station to operate.  To do that I need to use Gpredict  and Hamlib 4.0.  Gpredict provides solutions to the location of  a satellite and has an interface that controls the radio through Hamlib (libhamlib) to set the frequencies and provide compensation for doppler shift.

My problem is that I cannot get the Dell laptop to communicate with the radio using a USB to Serial converter that contains an FTDI FT232RL chip (or one that identifies as such, the cable is designed to use the 3.5 mm CI-V plug on the radio) or a direct USB connection to the radio.  I tried the communication with the radio using the Hamlib utility rigctl which is a command line interface.  I know I can communicate with the radio in either way from my radio stations computer wihich is a desktop running Ubuntu 20.04.  On the laptop I continually get timeouts after the program tries to talk to the radio.  To try to find out if Hamlib 4.0  was giving me problems since I had to compile it as the only *.deb file for 4.0 requires libc6-i386_29 or later and Lubuntu only had libc6-i386_27 installed.  So I reverted to Hamlib 3 which is the one available for Lubuntu 18.04.  Since Hamlib 3 does not have the IC-9700 in it, I used my ICOM IC-821 which is a 25 year old radio that works similar to the IC-9700.  Once again I got the same issue with Hamlib 3.0 getting no data back after multiple timeouts from a radio but only with the USB to Serial converter since there is no direct USB port on the IC-821.

The USB ports on the Dell laptop are USB 2.0 and the ones in my rather old desktop are also USB 2.0.  The laptop correctly recognizes the USB to Serial converter.  I have used dmseg and lsusb to confirm this.  The USB ports work with mice and keyboards and I have tried all of them with the USB to Serial converter cable.  I have /dev/ttyUSB0 which is the normally occurring port set with user group "dialout" and my user name in that group.  The only thing I can think of is there being some library or demon not installed.  The same libraries for USB though different versions are installed on both computers.

I really have no clue as to what may be the issue.

---

### Post by CelticWarrior on 2021-04-22
Lubuntu 18.04, because it's a flavor of Ubuntu, has only 3 years of support and it just ended.
You need to upgrade to 20.04 which is actually a good thing because what you need to work you already know it work in 20.04 so there's a good chance it'll work in the old laptop as well.

---

### Post by deck on 2021-04-22
> **CelticWarrior said:**
> Lubuntu 18.04, because it's a flavor of Ubuntu, has only 3 years of support and it just ended.
You need to upgrade to 20.04 which is actually a good thing because what you need to work you already know it work in 20.04 so there's a good chance it'll work in the old laptop as well.

1)  You need to recheck on the support for an LTS release. A mainline LTS release  is supported for 5 years not 3.  While flavors may only support for 3 they may support for longer.  Mainline Ubuntu 18.04 is good till 2023 and was the last LTS release with a 32 bit (i386) version.

2) The Inspirion e1505 is a dual 32 bit processor.  Ubuntu 20.04 and flavors are only released for 64 bit processors.  Therefore I can't upgrade to it.  I would have upgraded to the latest Lubuntu release (19.04) if it were in 32 bit but it isn't.  I have tried the latest Debian release in 32 bit but it is very slow on the hardware.

3) An accompanying issue is that future Linux releases may only be 64 bit per Linus Torvalds.

---

### Post by CelticWarrior on 2021-04-22
1) standard Ubuntu has 5 years; flavors only 3, that's exactly what I said. Lubuntu 18.04 supports end this month.

2) A Dell Inspiron E1505 is a laptop, not a CPU. It has a CPU which happens to be Intel Core 2 Duo, a 64-bit CPU. It may have come with a preinstalled 32-bit OS, typical on early 64-bit computers, but the original and/or current OS architecture is irrelevant. If it has a 64-bit CPU it can run a 64-bit OS.

---

### Post by Dennis N on 2021-04-22
>  The Inspirion e1505 is a dual 32 bit processor. Ubuntu 20.04 and flavors are only released for 64 bit processors. Therefore I can't upgrade to it.

I also bought the Inspiron e1505 from Dell in the Spring of 2007 with pre-installed Ubuntu 7.04. If you have the same processor mine has, you are right. It's 32-bit only. There could have been another processor option. I don't know about that. 

Check to find model:
```
dmn@Kayleigh:~$ inxi -C
CPU:       Dual core Intel T2080 (-MCP-) cache: 1024 KB
           clock speeds: max: 1733 MHz 1: 1263 MHz 2: 1191 MHz

```
and to see architecture and op-modes:
```
dmn@Kayleigh:~$ lscpu
Architecture:        i686
[COLOR="#FF0000"]CPU op-mode(s):      32-bit[/COLOR]
Byte Order:          Little Endian
CPU(s):              2

```
Right now, I am using Ubuntu MATE 18.04 32 bit.

And sorry, I can't offer any advice on your questions. Not something I know anything about.

---

### Post by Yellow Pasque on 2021-04-22
> **CelticWarrior said:**
> 1) standard Ubuntu has 5 years; flavors only 3, that's exactly what I said. Lubuntu 18.04 supports end this month.

This is what I used to think, but it's not that cut and dry. While Lubuntu devs will not be working on LXDE updates from this point on, users will still receive the same updates that Ubuntu users get and are still free to ask for support from the community. See the "Release Cycle" graphics at the bottom of: [https://lubuntu.me/downloads/](https://lubuntu.me/downloads/)

---

### Post by deck on 2021-04-22
Dennis N,

CPU op-mode may be 32-bit because the OS is 32 bit.  I did some checking and there seemed to be problems running a 64-bit OS on the e1505 because of some hardware in the system.  I am going to try a 64 bit Linux and see if it even works.  If it gives me grief then there are hardware issues. I still need a light weight Linux to operate within the hardware constraints.  One thing I did note in reading the Owner's Manual specifications is that the data bus is 64 bit  but the address bus is 32 bit (4 GB maximum address range)

---

### Post by Yellow Pasque on 2021-04-22
You will have to have a Core **2** Duo ("Merom") for 64-bit to have any chance of working. The original Core Duo ("Yonah") is not 64-bit capable.

---

### Post by CelticWarrior on 2021-04-22
> **Yellow Pasque said:**
> You will have to have a Core **2** Duo ("Merom") for 64-bit to have any chance of working. The original Core Duo ("Yonah") is not 64-bit capable.

Exactly.
I bought my last 32-bit hardware around 2006, a DualCore, but the same model had a 64-bit option with Core2Duo. That was exactly the turning point. I expect most laptops from known brands sold during 2007 to have been 64-bit already.

---

### Post by guiverc on 2021-04-22
> **deck said:**
> 1)  You need to recheck on the support for an LTS release. A mainline LTS release  is supported for 5 years not 3.  While flavors may only support for 3 they may support for longer.  Mainline Ubuntu 18.04 is good till 2023 and was the last LTS release with a 32 bit (i386) version.

2) The Inspirion e1505 is a dual 32 bit processor.  Ubuntu 20.04 and flavors are only released for 64 bit processors.  Therefore I can't upgrade to it.  I would have upgraded to the latest Lubuntu release (19.04) if it were in 32 bit but it isn't.  I have tried the latest Debian release in 32 bit but it is very slow on the hardware.

3) An accompanying issue is that future Linux releases may only be 64 bit per Linus Torvalds.

Ubuntu 18.04 LTS had 5 years only for packages in the 'main' repository, ie. those included on specific ISOs including Ubuntu Desktop 18.04 LTS, Ubuntu Server 18.04 LTS etc.  You can see [https://fridge.ubuntu.com/2018/04/27/ubuntu-18-04-lts-bionic-beaver-released/](https://fridge.ubuntu.com/2018/04/27/ubuntu-18-04-lts-bionic-beaver-released/) for details where you'll note

> Maintenance updates will be provided for 5 years for Ubuntu  Desktop, Ubuntu Server, Ubuntu Cloud, and Ubuntu Core. Ubuntu Studio  will be supported for 9 months. All the remaining flavours will be  supported
for 3 years. 

You'll read the same in Lubuntu's release notes too [https://lubuntu.me/bionic-5-released/](https://lubuntu.me/bionic-5-released/)
> 
Lubuntu 18.04.5 LTS, will be supported until April 2021.

In fact I just put up a [URL="https://discourse.lubuntu.me/t/lubuntu-18-04-lts-is-nearing-its-eol-end-of-life/2442"]warning about the approaching EOL on Lubuntu's discourse
[/URL]
> **deck said:**
> 
I would have upgraded to the latest Lubuntu release (19.04) if it were in 32 bit but it isn't. 

 I have tried the latest Debian release in 32  bit but it is very slow on the hardware. 

I don't really understand this, the [latest release is Lubuntu 21.04]("https://lubuntu.me/hirsute-released/") with Lubuntu 19.04 having been *end of life* for some time. ISOs were produced in x86/i386 for 19.04 and upgraded packages were provided the entire life of 19.04, but that was long ago & is of no consequence now.  Lubuntu 19.04 however was never officially supported at time of release, so only *alpha* or *test* ISOs were ever produced, those having been deleted now.

FYI:  I QA-test both Lubuntu & Debian (*as well as others, eg. Xubuntu also had i386 images in the disco or 19.04 cycle so tested them too*), and whilst in most boxes I find Lubuntu (LXDE or LXQt) pretty much equal to Debian (using same LXDE or LXQt desktop), I have one *resource challenged* box where Lubuntu 18.04.5 LTS (i386) clearly outperformed Debian 10.6 (Buster LXDE i386 *non-free*) last tested in August-2020 (*one box being out of nine i386 boxes used in QA-testing*)   My last x86 netbook was a early 2007 asus eeepc.

---

### Post by Dennis N on 2021-04-22
> CPU op-mode may be 32-bit because the OS is 32 bit. I did some checking and there seemed to be problems running a 64-bit OS on the e1505 because of some hardware in the system.
No, T2080 is definitely 32 bit architecture meaning it can't handle 64-bit length instructions. Note the width reported here, which is register width:
```
dmn@Kayleigh:~$ sudo lshw -class cpu
[sudo] password for dmn: 
  *-cpu                     
       description: CPU
       product: Genuine Intel(R) CPU           T2080  @ 1.73GHz
       vendor: Intel Corp.
       physical id: 400
       bus info: cpu@0
       version: 6.14.12
       serial: 0000-06EC-0000-0000-0000-0000
       slot: Microprocessor
       size: 1306MHz
       capacity: 1800MHz
       [COLOR="#FF0000"]width: 32 bits[/COLOR]
       clock: 133MHz
       capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc arch_perfmon bts cpuid aperfmperf pni monitor est tm2 xtpr pdcm pti dtherm cpufreq
       configuration: cores=2 enabledcores=2 id=1 threads=2
     *-logicalcpu:0
          description: Logical CPU
          physical id: 1.1
          [COLOR="#FF0000"]width: 32 bits[/COLOR]
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 1.2
         [COLOR="#FF0000"] width: 32 bits[/COLOR]
          capabilities: logical

```
So it won't run 64-bit OS with its 64-bit instructions.

---

### Post by Yellow Pasque on 2021-04-22
> **Dennis N said:**
> No, T2080 is definitely 32 bit architecture

Yeah, the Pentium T2080 looks like a Core Duo T2250 with half the cache disabled. It's still a Yonah core and it won't do 64-bit.

---

### Post by guiverc on 2021-04-22
I can only concur (as per 32-bit only), as I used a

```
dell inspiron 6400 (c2d-t2450, 2gb, intel 945gm)
```

for testing releases of Lubuntu/Xubuntu up to 19.04, but it was useless for later releases so I eventually recycled it (*or so I believe unless it's in a stack or used to elevate a monitor to the right height*).

Which kernel stack are you using?   I tested both and had no issues with either on any box except early 2004 IBM pentium M laptops (t42p, r50p) that were problematic on kernels >5.3 (ie. fine with 18.04.4 using HWE but not with the 5.4 of 18.04.5) On all (later boxes; eg. t43..) no issues.

The reason I mention this, is if you're on the GA stack (4.15 kernel), you may have more luck using the HWE stack (5.4 kernel fully updated) as it has many later kernel modules (ie. *drivers*). 

Adding the HWE stack is pretty easy, though if you don't want to install it, you can perform tests using *live* media (the Lubuntu 18.04.5 LTS ISO will use that stack) though that maybe hard to fully test your radio equipment, but may still be possible.  If you add it, I'd test it (not execute the removal of GA stack until you're happy) and remove the GA kernels only later (*you don't have to though; my IBM thinkpad t43 still has both as they were useful in comparison testing the issues with r50p/t42p with the 5.4 kernel*)

Going from HWE to GA stack I doubt would help (from description you need newer hardware support, not older).  For details on stack I'll provide

- [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
- [https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)

You can just use `uname -r` to view your kernel details; if it's 4.15 you're using GA (general), if it's 5.4 you're using the hardware enablement stack (which really is geared for later video support, but includes all later kernel modules (ie. *drivers*)

---

### Post by Yellow Pasque on 2021-04-22
> **guiverc said:**
> I can only concur (as per 32-bit only)

Well, that was for Dennis N's CPU. The OP needs to check what CPU s/he has because there were some 64-bit capable CPU's offered with the E1505.

> I used a
```
dell inspiron 6400 (c2d-t2450, 2gb, intel 945gm)
```


The T2450 was a Core Duo; not a Core 2 Duo.

---

### Post by guiverc on 2021-04-22
Thanks re: c2d & cduo...

It was just copy & pasted from my ubuntu_hw_test_specs sheet into iso.qa.ubuntu.com each time, and given the last i386 test no doubt was August-2020 (18.04.5) I'll have been wrong every time I used it :(

---

### Post by deck on 2021-04-23
So to settle things, the e1505 I have is a 32 bit processor.  I tried loading Lubuntu 20.04.2 which is 64-bit and got an error message to the effect that I needed an x86-64 processor but only have an i686 processor.  So we can go back to the original question of why my USB is not working correctly.

I may have to go to some other distribution with a 32 bit release and see what happens.

As to the Lubuntu releases, just a few days ago they only had 19.04 advertised as their latestest release, they now have 20.04 and 21.04 having dropped 19.04.

---

### Post by ajgreeny on 2021-04-23
> **deck said:**
> < Snip >
As to the Lubuntu releases, just a few days ago [COLOR="#FF0000"]they[/COLOR] only had 19.04 advertised as their latestest release, they now have 20.04 and 21.04 having dropped 19.04.
Who is the [COLOR="#FF0000"]they[/COLOR] you mention above; which site were you on?
It should have been [https://lubuntu.me/downloads/](https://lubuntu.me/downloads/) which is the Lubuntu download site everybody should be using, not any of the others, eg lubuntu.net, which even today has only 19.10 as the download version.
I suspect you were on the wrong site but it would be interesting to know.

---

### Post by deck on 2021-04-23
Interesting, there is Lubuntu.net and Lubuntu.me.  Lununtu.net uses much of the symbology of Lubuntu.me  but the .net version must have been the one I looked on.  It still has 19.04 listed as the latest release.  Who is who in this.

---

### Post by ajgreeny on 2021-04-23
I am not sure where the lubuntu.net website is from but it is most definitely a usurper and not the "real" Lubuntu site (lubuntu.me) that you should use.

The problem has arisen many times in the past where installations from lubuntu.net have caused many problems in the running of the systems.

More details of all of this at [https://ubuntuforums.org/showthread.php?t=2360662](https://ubuntuforums.org/showthread.php?t=2360662)

---

### Post by deck on 2021-04-23
I will try the  18.04.5 from Lubuntu.me and see if it makes any difference.  I will reformat my / and /boot partitions which will get rid of the bulk of the other load.  I will keep my /home partition; hopefully there is nothing malicious buried there.

---

### Post by Yellow Pasque on 2021-04-23
You'll be fine. There are a lot of EOL alarmists here.

---

### Post by guiverc on 2021-04-23
Lubuntu's web site is [https://lubuntu.me/](https://lubuntu.me/)

For Lubuntu links please see [https://lubuntu.me/links/](https://lubuntu.me/links/)

If you're unsure where Lubuntu is, go to ubuntu.com and search there, ie. [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours) will take you to the official site for each Ubuntu flavor.

Don't ask google, as it can offer up to three Lubuntu 'sites' depending on language used (all offering it for download) in search query. Its up to you work out the legitimate site, or what we tend to call a "*fan*" site.  We'd love to change this, but cannot (Ubuntu/Canonical/Lubuntu does not own the other sites)

If you downloaded your image from lubuntu.net, I wouldn't worry much, and if you're like me you'd detect you had an imperfect ISO after download when you verify the checksum ([https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)). Lubuntu.net (to avoid bandwidth costs) generally passes legitimate cdimage.ubuntu.com links for the actual download so you're downloading legitimate ISOs, but they maybe stale/outdated or not the one you expected/wanted (I'd expect your own checks to detect that, though newbies won't likely notice).


FYI: Lubuntu 18.04 LTS is almost at it's EOL. I use it on occasion when i use my IBM Thinkpad T43, a device I tested 18.10 & 19.04 on (but 18.04 is currently still supported so it runs 18.04).  Will I keep using Lubuntu or move to Debian Buster/10?  I suspect it'll remain Lubuntu beyond this month... One I'm lazy, but mostly with how I use it I don't see a problem. I'm rarely online (most of what I do is on local network), as all my online stuff is done on other boxes (like now).  The end of Lubuntu support I offer as a team member providing the official line.. In May I starting moving all Lubuntu (LXDE) stuff on wiki.ubuntu.com to a new LXDE location as Lubuntu will be LXQt only now in a matter of days.  It'll still work though, and I bet I for one, will still have LXDE on some boxes..

---

### Post by Yellow Pasque on 2021-04-23
> **guiverc said:**
> Thanks re: c2d & cduo...

You're welcome. It's confusing, but that's probably what Intel's marketing department wanted at that point in time after NetBurst mobile chips failed so badly.

---

