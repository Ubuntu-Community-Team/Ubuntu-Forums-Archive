---
title: "Atom N280 with Jaunty == 1.33Ghz Max speed and lag"
date: 2009-07-09
forum: Hardware
---

### Post by SnappyU on 2009-07-09
**See post #11 for solution ;)**
**Solved for MSI but not for Acer or other vendors with unsupported BIOS**

Hi folks,

I have Jaunty installed on a MSI Wind u100+E, with Atom N280, 2gb ram and 160gb hdd.  The cpu do not seem to be fully supported as the max clock speed is limited to 1.33 GHz and not the 1.66 GHz clock that the cpu is supposed to be running at.

Besides that, I also experience frequent lags when scrolling and clicking.

Am I alone or is this common?
Is this due to the N280 not being fully supported?

Is there a fix?

EDIT:
Others with similar problem:
[http://ubuntuforums.org/showthread.php?t=1201352&highlight=n280](http://ubuntuforums.org/showthread.php?t=1201352&highlight=n280)

---

### Post by SnappyU on 2009-07-19
*bump*

---

### Post by pugopugo on 2009-07-30
I have the same problem on my Acer Aspire One D250. As far as I can see it affect all Linux kernels running on Atom N280. I find it a bit amazing that there aren't more writings about it.

---

### Post by thezood on 2009-07-31
> **SnappyU said:**
> Hi folks,

I have Jaunty installed on a MSI Wind u100+E, with Atom N280, 2gb ram and 160gb hdd.  The cpu do not seem to be fully supported as the max clock speed is limited to 1.33 GHz and not the 1.66 GHz clock that the cpu is supposed to be running at.

Besides that, I also experience frequent lags when scrolling and clicking.

Am I alone or is this common?
Is this due to the N280 not being fully supported?

Is there a fix?

EDIT:
Others with similar problem:
[http://ubuntuforums.org/showthread.php?t=1201352&highlight=n280](http://ubuntuforums.org/showthread.php?t=1201352&highlight=n280)

Do you have cpufreqd installed?

---

### Post by pugopugo on 2009-08-07
I tried with cpufreqd, but no difference. The kernel seems to think that the maximum speed is 1.33GHz. Maybe I am stupid, but how can any user space daemon override that?

I get the impression that this is a kernel thing. Or am I wrong? 

Here is the output from cpufreq-info:

```
root@Pacman:/home/pugo# cpufreq-info 
cpufrequtils 004: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to cpufreq@lists.linux.org.uk, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 800 MHz - 1.33 GHz
  available frequency steps: 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1.33 GHz and 1.33 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.33 GHz (asserted by call to hardware).
  cpufreq stats: 1.33 GHz:0,00%, 1.07 GHz:0,00%, 800 MHz:0,00%  (12)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 800 MHz - 1.33 GHz
  available frequency steps: 1.33 GHz, 1.07 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1.33 GHz and 1.33 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 1.33 GHz (asserted by call to hardware).
  cpufreq stats: 1.33 GHz:0,00%, 1.07 GHz:0,00%, 800 MHz:0,00%  (6)

```

---

### Post by SnappyU on 2009-08-25
So anyone has any update on this?

---

### Post by ringe on 2009-09-01
Report your issues here: [https://bugs.launchpad.net/ubuntu/+source/cpufreqd/+bug/422858](https://bugs.launchpad.net/ubuntu/+source/cpufreqd/+bug/422858)

---

### Post by Eberbachl on 2009-09-07
I understand from some posts I've read elsewhere that the N280 does the same thing under Windows XP. Perhaps it's an Intel Speedstep/BIOS things rather than a kernel issue?

Not sure...

If you disable Intel Speedstep in BIOS cat /proc/cpuinfo will report 1667mhz, and 1800+ with the built in overclocking feature turned on.

---

### Post by 00b00nt00 on 2009-11-21
I can report that this problem is also so with my Aspire One D250.

However, Geekbench reports a score of 1053, vs 950 for my old N270 laptop, so despite seemingly being underclocked, it still performs faster. I wonder if this is actually an error in the reported CPU speed rather than the CPU being underclocked.

Update:

Disabling ACPI results in the CPU speed increasing to 1.66Ghz. Interestingly, the Geekbench score actually >DROPS< to 850 points!

---

### Post by SnappyU on 2009-11-23
Just read the thread at launchpad bug reporting site.  So it is a bug with the BIOS ACPI table.  Guess we will need a new BIOS from our netbook manufacturer to fix this.

Meanwhile, just wondering why Windows XP can still somehow get the correct values from the same BIOS?  An app like rmclock is also able to overclock (for some CPU) and configure p-steps settings etc.  Is there anyway this can be done in Linux, in Ubuntu?

It cannot be that Ubuntu / Linux, for all its customizability, should loose out to Windows on this one right? hmmm ... :popcorn:

---

### Post by SnappyU on 2009-12-04
It is not Acer ... it is Intel Atom's N280 processor that is not totally supported by *all* the BIOS out there.

I have an MSI u100+ that has the same N280 cpu and have the same problem in Ubuntu Jaunty as well.

**EDIT:**
I just updated my MSI u100+ with the latest BIOS from [http://eu.msi.com/index.php?func=downloaddetail&type=bios&maincat_no=135&prod_no=1784](http://eu.msi.com/index.php?func=downloaddetail&type=bios&maincat_no=135&prod_no=1784)  ... found it at launchpad shared by "rkagan wrote on 2009-12-02". 

It works fine in Jaunty now!!  CPU Freq Scaling Monitor 2.26.1 now reports 1GHz, 1.33GHz and 1.67GHz.
Not sure if it is just a label change or an actual speed change.  But consider it fixed! :)

**Steps to do it with USB stick in Ubuntu:**

1. Install Unetbootin if you have not.

2. Run Unetbootin and select Freedos as distro.  Select your USB stick.  WARNING, if you select your hdd, your bad!

3. After flashing your USB stick, copy the latest MSI BIOS (meant for MSI Wind U100+) into the flash drive and unzip it.

4. Dismount your USB stick, reboot your MSI u100+ with the usb stick.

5. Select one of the FreeDOS LiveCD boot which should get you to an A:> prompt in a few secs time.

6. Your flash files are in C:>

7. Goto the directory you unzipped earlier.

8. Make sure your AC power is in, and your usb stick is stable.  Run flash.

**WARNING**
The batch file has not further prompts.  Once you start it, it erases the existing flash and updates your BIOS with the latest one.


Have fun! :)

**Reference:**

[Freedos on usb thumbdrive via Unetbootin in linux](http://tuxtweaks.com/2009/09/create-a-bootable-freedos-usb-drive-on-linux-with-unetbootin/)

[Launchpad bug trail on Atom N280 support](https://bugs.launchpad.net/ubuntu/+source/cpufreqd/+bug/422858)

[MSI BIOS download page for MSI Wind U100+](http://eu.msi.com/index.php?func=downloaddetail&type=bios&maincat_no=135&prod_no=1784)

---

### Post by 00b00nt00 on 2009-12-04
Let's keep this thread alive until Acer get around to releasing a BIOS update for the D250 as well. MSI's move may be a good sign that Acer (and Lenovo) will follow suit.

FYI D250 BIOS 1.22 as released in November does not fix the issue.

---

### Post by vajorie on 2009-12-05
> **00b00nt00 said:**
> Let's keep this thread alive until Acer get around to releasing a BIOS update for the D250 as well. MSI's move may be a good sign that Acer (and Lenovo) will follow suit.

FYI D250 BIOS 1.22 as released in November does not fix the issue.

I rmmod'ed acpi-cpufreq and modprobed p4-clockmod and it went up to 1.66. cpufreq-info: 

```
analyzing CPU 0:
  driver: p4-clockmod
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 0 1
  maximum transition latency: 10.00 ms.
  hardware limits: 208 MHz - 1.67 GHz
  available frequency steps: 208 MHz, 417 MHz, 625 MHz, 833 MHz, 1.04 GHz, 1.25 GHz, 1.46 GHz, 1.67 GHz
  available cpufreq governors: userspace, performance
  current policy: frequency should be within 208 MHz and 1.67 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1.67 GHz.
analyzing CPU 1:
  driver: p4-clockmod
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 0 1
  maximum transition latency: 10.00 ms.
  hardware limits: 208 MHz - 1.67 GHz
  available frequency steps: 208 MHz, 417 MHz, 625 MHz, 833 MHz, 1.04 GHz, 1.25 GHz, 1.46 GHz, 1.67 GHz
  available cpufreq governors: userspace, performance
  current policy: frequency should be within 208 MHz and 1.67 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1.67 GHz.
```
is there a specific reason we weren't supposed to us that one instead of acpi-cpufreq?

---

### Post by SnappyU on 2009-12-07
> **00b00nt00 said:**
> Let's keep this thread alive until Acer get around to releasing a BIOS update for the D250 as well. MSI's move may be a good sign that Acer (and Lenovo) will follow suit.

FYI D250 BIOS 1.22 as released in November does not fix the issue.

I'll update this thread title to reflect that. :)

---

### Post by SnappyU on 2009-12-07
Wow ... this could well be a better solution.  So do you have the whole range of clock speed from 208MHz to 1.67GHz?  If so, I would like to try your method as it can increase my batt life with the 208MHz clockdown.  Or at least 417MHz. :p

> **vajorie said:**
> I rmmod'ed acpi-cpufreq and modprobed p4-clockmod and it went up to 1.66. cpufreq-info: 

```
analyzing CPU 0:
  driver: p4-clockmod
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 0 1
  maximum transition latency: 10.00 ms.
  hardware limits: 208 MHz - 1.67 GHz
  available frequency steps: 208 MHz, 417 MHz, 625 MHz, 833 MHz, 1.04 GHz, 1.25 GHz, 1.46 GHz, 1.67 GHz
  available cpufreq governors: userspace, performance
  current policy: frequency should be within 208 MHz and 1.67 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1.67 GHz.
analyzing CPU 1:
  driver: p4-clockmod
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 0 1
  maximum transition latency: 10.00 ms.
  hardware limits: 208 MHz - 1.67 GHz
  available frequency steps: 208 MHz, 417 MHz, 625 MHz, 833 MHz, 1.04 GHz, 1.25 GHz, 1.46 GHz, 1.67 GHz
  available cpufreq governors: userspace, performance
  current policy: frequency should be within 208 MHz and 1.67 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1.67 GHz.
```
is there a specific reason we weren't supposed to us that one instead of acpi-cpufreq?

---

### Post by vajorie on 2009-12-07
> **SnappyU said:**
> Wow ... this could well be a better solution.  So do you have the whole range of clock speed from 208MHz to 1.67GHz?  If so, I would like to try your method as it can increase my batt life with the 208MHz clockdown.  Or at least 417MHz. :p

Yep, I have the whole range. But configuring powernowd just became a whole lot complicated :)

Edit: I also have a feeling that p4-clockmod might not be giving any power savings in contrast to acpi-cpufreq. I don't have any prrof for that: someone with more time than I do will have to check up on that.

---

### Post by 00b00nt00 on 2009-12-08
Acer have released BIOS 1.25 for the D250.

I'll try updating the BIOS after work and report back in the next 24 hours or so if the latest BIOS addresses the CPU scaling issue.

Why oh why don't Acer release change notes with their software?

---

### Post by vajorie on 2009-12-08
> **00b00nt00 said:**
> Acer have released BIOS 1.25 for the D250.

I'll try updating the BIOS after work and report back in the next 24 hours or so if the latest BIOS addresses the CPU scaling issue.

Why oh why don't Acer release change notes with their software?

Thanks :)

Yet I hate BIOS updates, they truly scare the **** out of me!.. 

I am not sure if it would work for our d250 but here's a link to bios recovery, in case anyone needs it: [http://macles.blogspot.com/2008/08/acer-aspire-one-bios-recovery.html](http://macles.blogspot.com/2008/08/acer-aspire-one-bios-recovery.html) (the number of people in there commenting is simply amazing and very scary).

Edit1: Acer seems to suggest that the above link is *not* applicable to D250:
[http://netbooks-us.custhelp.com/app/answers/detail/a_id/66/kw/bios%20recovery/r_id/166](http://netbooks-us.custhelp.com/app/answers/detail/a_id/66/kw/bios%20recovery/r_id/166)

Edit2: I don't see 1.25 in their list of available BIOS updates: [http://us.acer.com/acer/service.do?LanguageISOCtxParam=en&miu10einu24.current.attN2B2F2EEF=3750&sp=page15e&ctx2.c2att1=25&miu10ekcond13.attN2B2F2EEF=3750&CountryISOCtxParam=US&ctx1g.c2att92=453&ctx1.att21k=1&CRC=2054404012](http://us.acer.com/acer/service.do?LanguageISOCtxParam=en&miu10einu24.current.attN2B2F2EEF=3750&sp=page15e&ctx2.c2att1=25&miu10ekcond13.attN2B2F2EEF=3750&CountryISOCtxParam=US&ctx1g.c2att92=453&ctx1.att21k=1&CRC=2054404012)

---

### Post by 00b00nt00 on 2009-12-08
I bought mine in Japan, but the December AOD250 BIOS is also listed on the U.K. support page.

Don't worry about flashing; it only really fails if you: a)flash a BIOS for a different model of computer, b) interrupt the flashing process e.g. removing the power, c) you're a chump who shouldn't be let near electronic machines of any sort!

AOD250 - that'll be the KAV60 BIOS you need. Asus do include a rubric to advise you which files to use (depending on Windows or DOS). My approach is to boot within Freedos and then flash.

For the record, I have flashed several machines while following the appropriate instructions and I've never had any fail on me.

---

### Post by 00b00nt00 on 2009-12-09
KAV60 BIOS 1.25 installed, but whatever issues it fixes, it doesn't fix CPU scaling. Additionally, Ubuntu now only boots intermittently, so I've had to put on Windows 7 to get the machine to start every time. Ubuntu has always been a bit fussy on this laptop - maybe GRUB 2 has something to do with it.

Don't expect this BIOS to fix your problems.

---

### Post by caiacoa on 2009-12-10
> **00b00nt00 said:**
> Let's keep this thread alive until Acer get around to releasing a BIOS update for the D250 as well. MSI's move may be a good sign that Acer (and Lenovo) will follow suit.

FYI D250 BIOS 1.22 as released in November does not fix the issue.
BIOS Update for Acer Aspire One D150 is required too since there are the same CPU frequency problems ...

[https://bugs.launchpad.net/ubuntu/+source/cpufreqd/+bug/422858](https://bugs.launchpad.net/ubuntu/+source/cpufreqd/+bug/422858)

BR
caiacoa

---

### Post by 00b00nt00 on 2010-02-03
New KAV60 (D250) BIOS out: v1.26.

Said to address this issue. Downloading FreeDOS now in preparation for flashing.

---

### Post by qorron on 2010-05-10
did the upgrade to 1.27, got this:


```
cpufrequtils 006: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 1000 MHz - 1.67 GHz
  available frequency steps: 1.67 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1000 MHz and 1.67 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.
  cpufreq stats: 1.67 GHz:11.31%, 1.33 GHz:0.26%, 1000 MHz:88.43%  (1050)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 10.0 us.
  hardware limits: 1000 MHz - 1.67 GHz
  available frequency steps: 1.67 GHz, 1.33 GHz, 1000 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 1000 MHz and 1.67 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1000 MHz.
  cpufreq stats: 1.67 GHz:11.53%, 1.33 GHz:0.29%, 1000 MHz:88.17%  (1088)

```

acer aspire one d250

with windows XP, I get runtimes up to 8 hours.
ubuntu: 5:30

---

### Post by SnappyU on 2010-10-28
> **qorron said:**
> did the upgrade to 1.27, got this:

acer aspire one d250

with windows XP, I get runtimes up to 8 hours.
ubuntu: 5:30
wow ... that is drastic!  Any idea what the cause is?  I'm on Ubuntu on two machines.  The notebook is basically my desktop, so no worries abt batt time.

The netbook I have has a 9 cell and a 6 cell, giving 7+hrs and 4+ hours respectively.  Would be nice to have 8~10 hrs for the 9cell. :D

---

### Post by alexv75 on 2011-02-16
Any hope for people with N280 from other brands, like gigabyte? I have the T1028X stuck at 1.33G. I even tried talking to gigabyte but they basically told me that they don't care about linux support :(. I have tried changing the scaling driver with no result. The only way to get full speed was to disable acpi, but that kills my batt. awfully fast.

---

### Post by goodbyewindows2008 on 2011-03-04
> **alexv75 said:**
> Any hope for people with N280 from other brands, like gigabyte? I have the T1028X stuck at 1.33G. I even tried talking to gigabyte but they basically told me that they don't care about linux support :(. I have tried changing the scaling driver with no result. The only way to get full speed was to disable acpi, but that kills my batt. awfully fast.

I got this netbook around a year ago and found the same problem. With acpi=off i would loose my graphics driver for some reason.

Gigabyte support were no help to me either, they wanted me to send them my netbook which is not an option in my part of the world.

I just looked into this again just now and found that acpi_no_auto_ssdt as a boot option gives me the full range from 208MHz to 1.67GHz. 

This is good but choosing ondemand in the cpufreq applet just enables performance(Edit: this seems to be a restriction in p4_clockmod module which is loaded instead of acpi-cpufreq), but I can choose any of the speeds and it runs at that fine.

I haven't done any tests on battery life yet, hopefully it's as good as it is with the 1.33GHz problem.

---

### Post by SnappyU on 2011-04-26
> 208MHz 

Wow ... will that give superlong batt life?

---

