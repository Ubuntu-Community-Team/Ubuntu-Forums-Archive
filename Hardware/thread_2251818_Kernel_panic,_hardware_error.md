---
title: "Kernel panic, hardware error"
date: 2014-11-06
forum: Hardware
---

### Post by Alexander2301 on 2014-11-06
Sorry for crappy shots from phone.
Adding irqpoll option in grub and updating microcode didn't help


[ATTACH=CONFIG]257795[/ATTACH][ATTACH=CONFIG]257797[/ATTACH][ATTACH=CONFIG]257796[/ATTACH]

---

### Post by Alexander2301 on 2014-11-06
RAM tested with extended tests and its ok, HDD scanned with MHDD - no bad sectors found
I guess that problem with CPU or with the south bridge. How can i check my assumption?

---

### Post by MIJ-VI on 2014-11-07
Have you tried clearing the CMOS?

BTW. Just think of the kind of help you could get if you supplied your hardware's specs--in detail.

---

### Post by Alexander2301 on 2014-11-07
Tried clearing CMOS - nothing changed. Tried updating BIOS with original 1.11 ROM which provided by Acer - nothing. After updating BIOS to modified 1.11 - { [http://forum.notebookreview.com/acer/480992-acer-laptop-phoenix-bios-bios-mod-request-210.html#post7500930](http://forum.notebookreview.com/acer/480992-acer-laptop-phoenix-bios-bios-mod-request-210.html#post7500930) } and turning off internal graphics (this option is not available in original BIOS) - system worked longer, but then same problem.
Laptop Acer Aspire 5530g 
CPU: AMD Turion x2 rm-70 
Graphics: ATI HD3470 and internal HD3400
South bridge: ATI SB700
North bridge: ATI RS780M

---

### Post by MIJ-VI on 2014-11-07
How hot is that notebook running? If it needs to be cleaned out this might help:

Aspire 5530_5530G Series Service Guide.pdf
[http://tim.id.au/laptops/acer/aspire%205530%205530g.pdf](http://tim.id.au/laptops/acer/aspire%205530%205530g.pdf)

--

My eyes aren't good enough to see more than this portion of the photo you posted:

CPU 1: Machine Check Exception: 4 Bank 1: b600000000000181

Machine-check exception - Wikipedia, the free encyclopedia
[https://en.wikipedia.org/wiki/Machine-check_exception](https://en.wikipedia.org/wiki/Machine-check_exception)

You might want to type out the rest of those error messages and do a search.

---

### Post by Alexander2301 on 2014-11-07
I cleaned it from dust and changed thermal paste about week ago, max temp of CPU is 80c at 100% load of both cores and 100% load of GPU with FurMark.
Searching error message didn't help(

This type of message is most frequent, and ends on line: "drm_kms_helper: panic occured, switching back to text console", nothing else

CPU 1: Machine Check Exception: 4 Bank 1: b600000000000181
TSC 14db941a5f ADDR 5c47c2c0                                                           ***- This parameter is not constant in errors***
PROCESSOR 2:200f31 TIME 1415308563 SOCKET 0 APIC 1 microcode 2000032
Run the above through 'mcelog --ascii'                                                   
Machine check: invalid
Kernel panic - not syncing: fatal machine check on current CPU
drm_kms_helper: panic occured, switching back to text console

---

### Post by MIJ-VI on 2014-11-07
How was its operation and how were the temps. before you cleaned and re-pasted it?

---

### Post by Alexander2301 on 2014-11-07
Overheating up to 95 and then shutting down.
It had win7 x32 installed, had BSODs of overheating. Than i received it from friend, re-pasted and installed x64 - again BSOD but with other code.

---

### Post by MIJ-VI on 2014-11-07
"Maximum operating temperature 100°C"
AMD Turion 64 X2 Mobile technology RM-70 - TMRM70DAM22GG
[http://www.cpu-world.com/CPUs/K8/AMD-Turion%2064%20X2%20Mobile%20technology%20RM-70%20-%20TMRM70DAM22GG.html](http://www.cpu-world.com/CPUs/K8/AMD-Turion%2064%20X2%20Mobile%20technology%20RM-70%20-%20TMRM70DAM22GG.html)

How long does it run before the errors start?

Is the fan running as it should?

[ubuntu] Acer Aspire 5515 shuts down from overheating, fan not working
[http://ubuntuforums.org/showthread.php?t=1696532](http://ubuntuforums.org/showthread.php?t=1696532)

Have you tried a different OS?

---

### Post by Alexander2301 on 2014-11-07
Fan works fine and RPM is changing when loaded. When 3d games are played, it can run about 1-1.5 hour without problem. But if it not fully used (browsing or watching video etc) it can shut down in minute. It has no certain time borders, but works better when more loaded.

---

### Post by Alexander2301 on 2014-11-07
And when crossfire mode is on FPS is less then if crossfire is off

---

### Post by MIJ-VI on 2014-11-07
> **Alexander2301 said:**
> Fan works fine and RPM is changing when loaded. When 3d games are played, it can run about 1-1.5 hour without problem. **But if it not fully used (browsing or watching video etc) it can shut down in minute.** It has no certain time borders, but works better when more loaded.

Do you mean that if you don't continuously touch the keys and/or the trackpad it will shut itself down?

Exactly which OS are you using and have you tried a different one?

---

### Post by MIJ-VI on 2014-11-07
It's nearly 4 AM here. I need sleep. Good nite.

---

### Post by Alexander2301 on 2014-11-07
Win7 x64 and Ubuntu 11.04 are installed, using them both. Also tried Ubuntu 10.10, same thing. It shuts down even if i using keyboard or/and trackpad/mouse, and error messages are same to messages after running 3d apps

---

### Post by Alexander2301 on 2014-11-07
We have 11am, but i need sleep too, good night

---

### Post by matt_symes on 2014-11-07
Hi

You've not supplied your kernel version. Post the output of this command from the terminal.

```
uname -a
```

You seem to be getting a kernel panic in drm_kms_helper. This may suggest graphics issues.

Have run run the error text through "mcelog --ascii" as suggested in the screenshots you posted ?

You will need to install it first.

```
sudo apt-get install mcelog
```

That may provide better information as to what is causing the machine check exception.

Kind regards

---

### Post by Alexander2301 on 2014-11-07
Hi
Linux kd-Aspire-5530 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
Unable to locate package mcelog error, tried different servers

---

### Post by Alexander2301 on 2014-11-07
Runned S&M under widows - it show errors in CPU L2 cache, then shot down. Is it possible that it's the only problem and discrete graphics card is fine?
Ubuntu on my laptop uses internal graphics card

---

### Post by matt_symes on 2014-11-07
Hi

> **Alexander2301 said:**
> Hi
Linux kd-Aspire-5530 3.13.0-39-generic #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
Unable to locate package mcelog error, tried different servers

Do you have the universe repository enabled ?

apt-cache search mcelog shows it's in the universe repo on my 14.04 installation

Kind regards

---

### Post by Alexander2301 on 2014-11-07
Bug reported: package mcelog 100-1fakesync1 failed to install/upgrade: subprocess installed post-installation script returned error exit status 1
And message from terminal: 
Do you want to continue? [Y/n] y
Setting up mcelog (100-1fakesync1) ...
Starting Machine Check Exceptions decoder: CPU is unsupported
invoke-rc.d: initscript mcelog, action "start" failed.
dpkg: error processing package mcelog (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mcelog
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Alexander2301 on 2014-11-07
> **Alexander2301 said:**
> Runned S&M under widows - it show errors in CPU2 L1 cache, then shot down. Is it possible that it's the only problem and discrete graphics card is fine?
Ubuntu on my laptop uses internal graphics card

Is it possible to disable/turn off CPU2 for checking source of problem?

---

### Post by MIJ-VI on 2014-11-07
> **Alexander2301 said:**
> Win7 x64 and **Ubuntu 11.04** are installed, using them both. Also tried Ubuntu 10.10, same thing. It shuts down even if i using keyboard or/and trackpad/mouse, and error messages are same to messages after running 3d apps

Son-of-a-comely-canine! You're struggling with Ubuntu 11.04?! It hasn't been supported in *years!*

Here's the current Long Term Support release (which will be supported until April 2019): 
 
Ubuntu 14.04.1 LTS (Trusty Tahr)
[http://ubuntu-cd.mirror.iweb.ca/14.04/](http://ubuntu-cd.mirror.iweb.ca/14.04/)

Download this ^, check its sha256sum, burn it to a DVD-R / DVD+R, boot with said DVD, verify the DVD's integrity and then re-boot into the DVD's desktop to see how well your machine runs it. If all goes well then do a clean install (not an upgrade) and we'll take it from there.

---

