---
title: "Limiting CPU c-state Level"
date: 2008-06-20
forum: Hardware
---

### Post by pveurshout on 2008-06-20
Since I've been using Ubuntu (version 8.04; using it about two weeks now), I've been terrorized by an annoying high-pitch noise coming from the inside of my laptop. Recently I found out this most likely has to do with my CPU entering a higher c-state (whenever I'm playing music, for example, the annoying sound disappears, which may point to the CPU entering a cstate which doesn't produce the annoying noise). After spending many hours searching for a way to fix this, I only ended up highly confused because everyone seems to have their own solution to fix this (there are numerous system files which refer to c-state in one or another way).

Since I'd rather not start trying stuff which may result in damaging my hardware, I am hoping someone knows which files I need to edit to limit the maximum c-state to -lets say- C3, using Ubuntu 8.04. Basically I know *what* to do, but I have absolutely no clue *how* to do it (safely). :(

Thanks so much in advance, this noise is driving me absolutely crazy!

*If someone knows of a tool that can show in which power state the CPU is actually in at a given moment, I'd be thankful to hear about it so I can check what state is causing the noise and, after fixing, to see if the fix actually worked.*

---

### Post by Sef on 2008-06-20
<snip>

---

### Post by ukripper on 2008-06-20
> **pveurshout said:**
> Since I've been using Ubuntu (version 8.04; using it about two weeks now), I've been terrorized by an annoying high-pitch noise coming from the inside of my laptop. Recently I found out this most likely has to do with my CPU entering a higher c-state (whenever I'm playing music, for example, the annoying sound disappears, which may point to the CPU entering a cstate which doesn't produce the annoying noise). After spending many hours searching for a way to fix this, I only ended up highly confused because everyone seems to have their own solution to fix this (there are numerous system files which refer to c-state in one or another way).

Since I'd rather not start trying stuff which may result in damaging my hardware, I am hoping someone knows which files I need to edit to limit the maximum c-state to -lets say- C3, using Ubuntu 8.04. Basically I know *what* to do, but I have absolutely no clue *how* to do it (safely). :(

Thanks so much in advance, this noise is driving me absolutely crazy!

*If someone knows of a tool that can show in which power state the CPU is actually in at a given moment, I'd be thankful to hear about it so I can check what state is causing the noise and, after fixing, to see if the fix actually worked.*

How are you so sure it is related to cpu not the alsa drivers/pulseaudio.
i had this high pitch noise coming out of speakers and culprit was alsa drivers long back
and then i went on alsa website and installed the latest drivers which fixed my high pitch noise.

---

### Post by pveurshout on 2008-06-20
> **ukripper said:**
> How are you so sure it is related to cpu not the alsa drivers/pulseaudio.
i had this high pitch noise coming out of speakers and culprit was alsa drivers long back
and then i went on alsa website and installed the latest drivers which fixed my high pitch noise.

The noise is not coming out of my speakers. I also considered the HDD and memory to be the problem, but since CPU activity is the thing that tends to silence the noise, I figured it could very well be CPU-related.

**Edit:** I have also tried removing the battery and disabling my proprietary graphics driver, so I doubt it's any of those. If it's related (I can't think of much else than that it is, though): while booting, my system hangs for about 30 seconds and I get the same high pitch noise - but a lot louder.

---

### Post by ukripper on 2008-06-20
> **pveurshout said:**
> The noise is not coming out of my speakers. I also considered the HDD and memory to be the problem, but since CPU activity is the thing that tends to silence the noise, I figured it could very well be CPU-related.

**Edit:** I have also tried removing the battery and disabling my proprietary graphics driver, so I doubt it's any of those. If it's related (I can't think of much else than that it is, though): while booting, my system hangs for about 30 seconds and I get the same high pitch noise - but a lot louder.

Can you check ```
cat /var/log/messages 
```for any errors or warnings?

---

### Post by pveurshout on 2008-06-20
I found the following errors/warnings:

```
ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
```

Several of the these: ```
system 00:04: ioport range 0x***-0x*** has been reserved
``` (where the asterisks are different numbers each time)

..and several of these:```
 system 00:04: iomem range 0x********-0x******** could not be reserved
```

```
Cannot allocate resource for EISA slot 1
```
..and slots 4 through 7

```
EISA: Detected 0 cards.
```

```
EDD information not available.
```

This one seems interesting?:
```
ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
```

```
alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
``` (if it's related to this message: I'm having some sound trouble as well; bass sounds are crackling when the PCM volume is too high, whereas Master volume doens't affect the sound quality at all.)

That seems to be it. Is there anything specific you were looking for?

Although I don't really know anything about this stuff, after reading something about CPU-noises on the internet I think it's just something my CPU (and others, too) does when running at lower capacity. Therefore it may not appear as an error or warning message (like an old TV that works just fine, but emits a high pitching sound). That may also be why I didn't read about actually *fixing* the problem anywhere, but only about how to avoid the situations in which it occurs (presumably the C3 or C4 CPU power state).

---

### Post by ukripper on 2008-06-20
i found this bug on launchpad relating to your cpu error:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/218188](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/218188)

This has been fixed in latest kernel 2.6.25

Rest of the messages i am still probing.

your problem could be related to this as current kernel is not recognising your current CPU cores and thereofre, it could be the reason it is not scaling

can you post outoput of the follwoing command:
> dmesg | less

and 

> cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies

---

### Post by ukripper on 2008-06-20
Can you also install package called powertop to see your cpu scaling in operation.

Just do ```
sudo apt-get install powertop
```

---

### Post by pveurshout on 2008-06-20
> i found this bug on launchpad relating to your cpu error:
[https://bugs.launchpad.net/ubuntu/+s...ux/+bug/218188](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/218188)

For some reason I was unable to copy everything in dmesg. The terminal window (I used dmesg | less like you said, btw) won't let me select more text than what's visible at the time. However, I did find the *exact* same error as described in your link above:
```
[   19.445323] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
```
On every boot, my system hangs for about 30 seconds (the bug description also mentions a long booting time) and the noise comes up really badly. Hopefully the new kernel will fix it! How does that work, does it come with one of the regular updates some time in the future, or do I manually have to implement version 2.6.25?

./scaling_available_frequencies:
```
798000 1064000 1330000 1596000 1862000 
```

**Powertop** tells me the CPU resides in C4 most of the time and the P-state is the lowest of the four states (798 Mhz) nearly all the time (while having some applications open but not doing anything but watching Powertop).

---

### Post by ukripper on 2008-06-20
> **pveurshout said:**
> For some reason I was unable to copy everything in dmesg. The terminal window (I used dmesg | less like you said, btw) won't let me select more text than what's visible at the time. However, I did find the *exact* same error as described in your link above:
```
[   19.445323] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
```
On every boot, my system hangs for about 30 seconds (the bug description also mentions a long booting time) and the noise comes up really badly. Hopefully the new kernel will fix it! How does that work, does it come with one of the regular updates some time in the future, or do I manually have to implement version 2.6.25?

./scaling_available_frequencies:
```
798000 1064000 1330000 1596000 1862000 
```

**Powertop** tells me the CPU resides in C4 most of the time and the P-state is the lowest of the four states (798 Mhz) nearly all the time (while having some applications open but not doing anything but watching Powertop).

i am not sure when or if new kernel .25 will be avilable from hardy's repos but surely will be included in ibex in October release.

but for the time being if you want you can compile and install to the latest kernel very easily using kernelcheck app [http://ubuntuforums.org/showthread.php?t=618563](http://ubuntuforums.org/showthread.php?t=618563).

just follow the steps you are done.

it may take 2 to 3 hours depending on machine. on my machine i compiled to latest kernel .25 was within 2 hours 15 mins. May take less for you.

before you do that can we check what kernel version r u using?
> uname -a

---

### Post by pveurshout on 2008-06-20
> **ukripper said:**
> i am not sure when or if new kernel .25 will be avilable from hardy's repos but surely will be included in ibex in October release.

but for the time being if you want you can compile and install to the latest kernel very easily using kernelcheck app [http://ubuntuforums.org/showthread.php?t=618563](http://ubuntuforums.org/showthread.php?t=618563).

just follow the steps you are done.

it may take 2 to 3 hours depending on machine. on my machine i compiled to latest kernel .25 was within 2 hours 15 mins. May take less for you.

before you do that can we check what kernel version r u using?

First of all: thanks for your help! I'll post a reply in this thread to let you know if I succeeded. Currently I'm using kernel version 2.6.24-19.

---

### Post by likuidkewl on 2008-06-20
This is a known issue with Core2 Duos(assuming you have one) and has been going on for ages!!!!

I am still waiting for Lenovo to go further than "We are looking into it..."

It happens in Windows too btw just not so bad.


[http://forums.lenovo.com/lnv/board/message?board.id=R_Series_Thinkpads&thread.id=159](http://forums.lenovo.com/lnv/board/message?board.id=R_Series_Thinkpads&thread.id=159)

Argh!

---

### Post by sdennie on 2008-06-20
> **likuidkewl said:**
> This is a known issue with Core2 Duos(assuming you have one) and has been going on for ages!!!!

I am still waiting for Lenovo to go further than "We are looking into it..."

It happens in Windows too btw just not so bad.


[http://forums.lenovo.com/lnv/board/message?board.id=R_Series_Thinkpads&thread.id=159](http://forums.lenovo.com/lnv/board/message?board.id=R_Series_Thinkpads&thread.id=159)

Argh!

This isn't a Core 2 Duo problem but, a vendor problem.  I run a Core 2 Duo (T9300) on a Dell XPS m1330 and never have any odd noises.  It's probably a problem with the BIOS doing something incorrectly with the power savings and causing the whine.

---

### Post by pveurshout on 2008-06-21
> **vor said:**
> This isn't a Core 2 Duo problem but, a vendor problem.  I run a Core 2 Duo (T9300) on a Dell XPS m1330 and never have any odd noises.  It's probably a problem with the BIOS doing something incorrectly with the power savings and causing the whine.

Yeah, I tried to find something in my BIOS about that, but for some reason the BIOS-options I have are extremely limited. I don't look into my BIOS-settings that often, but I can still remember there was a whole lot more to change in all my previous PC's BIOSes.

(I'm using a Pentium M processor, by the way.)

---

### Post by likuidkewl on 2008-06-21
> **vor said:**
> This isn't a Core 2 Duo problem but, a vendor problem.  I run a Core 2 Duo (T9300) on a Dell XPS m1330 and never have any odd noises.  It's probably a problem with the BIOS doing something incorrectly with the power savings and causing the whine.

I have heard it both ways and folks with Dells like yourself have complained.  But this is all moot since it is a Pentium M.  This is the first I have heard of these cpus.

---

### Post by ukripper on 2008-06-22
This problem relates more to BIOS and kernel rather than core2duo as i run 4 core2duo without any problems. I would sugegst anyone who is having this problem first try latest kernel .25 then see if this problem still persists.

---

