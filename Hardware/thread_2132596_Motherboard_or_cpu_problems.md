---
title: "Motherboard or cpu problems?"
date: 2013-04-05
forum: Hardware
---

### Post by mezga0153 on 2013-04-05
[COLOR=#000000][FONT=verdana]Hi,[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]I have dx79to using HyperX Blu 8GB 1600MHz ram and i7 - 3930k cpu and even with the latest 0559 bios update ubuntu doesn't boot if I enable more than 1 cpu in bios, kernel stops at: Booting Node 0, Processors #1[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]If I enable all cores system boots only if I set maxprocessors=1 or acpi=off kernel options, even if I set acpi=ht kernel doesn't boot :(

The same thing happens if I use linux 3.2 (default 12.04LTS kernel) or 3.5 (backport from the latest ubuntu) Here is how the screen looks when it stops booting: [http://osebje.famnit.upr.si/~tine.mezgec/IMG_20130404_155331.jpg](http://osebje.famnit.upr.si/~tine.mezgec/IMG_20130404_155331.jpg)[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]the system runs windows 7 just fine but that's not what I bought it for :(

Any ideas?[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Thanks![/FONT][/COLOR]

---

### Post by matt_symes on 2013-04-05
Hi

Try this.

Go into the BIOS and disable the dynamic power technology. Save the BIOS settings and reboot.

It is an issue that has affected the intel 3930X so it's worth a try.

Also what microcode are you running ? Boot using 1 cpu if you have tpo and then, from the terminal...

```
dmesg | grep microcode
```

```
lsmod | grep microcode
```

```
apt-cache policy intel-microcode
```

Post back results.

Kind regards

---

### Post by mezga0153 on 2013-04-06
disabling dynamic power technology setting actually worked!
thank you!

For reference, the data you asked for (while running with all cpus enabled):
```

me@machine:~$ dmesg | grep microcode
[   12.659825] microcode: CPU0 sig=0x206d7, pf=0x4, revision=0x70c
[   13.001301] microcode: CPU1 sig=0x206d7, pf=0x4, revision=0x70c
[   13.002093] microcode: CPU2 sig=0x206d7, pf=0x4, revision=0x70c
[   13.002870] microcode: CPU3 sig=0x206d7, pf=0x4, revision=0x70c
[   13.003631] microcode: CPU4 sig=0x206d7, pf=0x4, revision=0x70c
[   13.004513] microcode: CPU5 sig=0x206d7, pf=0x4, revision=0x70c
[   13.005305] microcode: CPU6 sig=0x206d7, pf=0x4, revision=0x70c
[   13.006061] microcode: CPU7 sig=0x206d7, pf=0x4, revision=0x70c
[   13.006786] microcode: CPU8 sig=0x206d7, pf=0x4, revision=0x70c
[   13.007520] microcode: CPU9 sig=0x206d7, pf=0x4, revision=0x70c
[   13.008342] microcode: CPU10 sig=0x206d7, pf=0x4, revision=0x70c
[   13.009080] microcode: CPU11 sig=0x206d7, pf=0x4, revision=0x70c
[   13.009815] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
me@machine:~$ lsmod | grep microcode
microcode              23030  0 
me@machine:~$ apt-cache policy intel-microcode
intel-microcode:
  Installed: (none)
  Candidate: 0.20111110-1
  Version table:
     0.20111110-1 0
        500 http://sk.archive.ubuntu.com/ubuntu/ precise/multiverse amd64 Packages

```

This is probably a bug in the motherboard that the kernel doesn't have a workaround for? Can you please suggest where can I report this so that it will be fixed in the future? Intel doesn't seem to care about linux support: [http://intelopenport.hosted.jivesoftware.com/thread/38692](http://intelopenport.hosted.jivesoftware.com/thread/38692)

---

### Post by matt_symes on 2013-04-06
Hi

> **mezga0153 said:**
> disabling dynamic power technology setting actually worked!
thank you!

Excellent. It's a workaround but i believe you lose turbo boost on the CPU by doing it. But at least you have all cores.

> 
For reference, the data you asked for (while running with all cpus enabled):
```

me@machine:~$ dmesg | grep microcode
[   12.659825] microcode: CPU0 sig=0x206d7, pf=0x4, revision=0x70c
[   13.001301] microcode: CPU1 sig=0x206d7, pf=0x4, revision=0x70c
[   13.002093] microcode: CPU2 sig=0x206d7, pf=0x4, revision=0x70c
[   13.002870] microcode: CPU3 sig=0x206d7, pf=0x4, revision=0x70c
[   13.003631] microcode: CPU4 sig=0x206d7, pf=0x4, revision=0x70c
[   13.004513] microcode: CPU5 sig=0x206d7, pf=0x4, revision=0x70c
[   13.005305] microcode: CPU6 sig=0x206d7, pf=0x4, revision=0x70c
[   13.006061] microcode: CPU7 sig=0x206d7, pf=0x4, revision=0x70c
[   13.006786] microcode: CPU8 sig=0x206d7, pf=0x4, revision=0x70c
[   13.007520] microcode: CPU9 sig=0x206d7, pf=0x4, revision=0x70c
[   13.008342] microcode: CPU10 sig=0x206d7, pf=0x4, revision=0x70c
[   13.009080] microcode: CPU11 sig=0x206d7, pf=0x4, revision=0x70c
[   13.009815] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
me@machine:~$ lsmod | grep microcode
microcode              23030  0 
me@machine:~$ apt-cache policy intel-microcode
intel-microcode:
  Installed:** (none)**
  Candidate: **0.20111110-1**
  Version table:
     0.20111110-1 0
        500 http://sk.archive.ubuntu.com/ubuntu/ precise/multiverse amd64 Packages

```


```
matthew-S206:/home/matthew % apt-cache policy intel-microcode
intel-microcode:
  Installed: (none)
  Candidate: **0.20120606-1ubuntu1**
  Version table:
     0.20120606-1ubuntu1 0
        500 http://gb.archive.ubuntu.com/ubuntu/ quantal/multiverse amd64 Packages
matthew-S206:/home/matthew % 
```

> 
matthew-S206:/home/matthew % apt-cache show intel-microcode
<snip>
Description-en_GB: Processor microcode data file for Intel CPUs
 The microcode data file for Linux contains the latest microcode
 definitions for all Intel processors. Intel releases microcode updates to
 correct processor behavior as documented in the respective processor
 specification updates. While the regular approach to getting this
 microcode update is via a BIOS upgrade, Intel realizes that this is an
 administrative hassle; the Linux Operating System has a mechanism to
 update the microcode after booting the OS.
 .
 This package contains only the microcode, so it needs the loader provided
 in the package microcode.ctl

You have no version of the intel-microcode installed. 

Maybe they have fixed the BIOS bug in this version of the intel microcode. There is an even newer version in 12.10; as i highlighted.

This does assume that the microcode is loaded before bringing the other CPU's online. You'll have to check dmesg to see.

You may want to look into that. I will say that it's something i have never had to worry about though.

> 
This is probably a bug in the motherboard that the kernel doesn't have a workaround for? Can you please suggest where can I report this so that it will be fixed in the future? Intel doesn't seem to care about linux support: [http://intelopenport.hosted.jivesoftware.com/thread/38692](http://intelopenport.hosted.jivesoftware.com/thread/38692)

Intel are actually pretty good in the open source world and i would tend to ignore that response in that thread, although they may not fix it directly.

As for raising a bug, for _**mainline kernel only:**_

[www.bugzilla.kernel.org]("http://www.bugzilla.kernel.org") 

(This is the Kernel Tracker system (based on Bugzilla) for posting bugs against the **mainline** Linux kernels) 

or for Ubuntu read this.

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Kind regards

---

### Post by Yellow Pasque on 2013-04-06
Before raising a bug, you should install the latest microcode and try a 3.8 kernel (either installing one on your current system or running a 13.04 LiveUSB/CD). It's possible that it's already been fixed upstream.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.6-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.6-raring/)
[https://launchpad.net/ubuntu/+archive/primary/+files/intel-microcode_1.20120606.v2.2ubuntu1_amd64.deb](https://launchpad.net/ubuntu/+archive/primary/+files/intel-microcode_1.20120606.v2.2ubuntu1_amd64.deb)

---

