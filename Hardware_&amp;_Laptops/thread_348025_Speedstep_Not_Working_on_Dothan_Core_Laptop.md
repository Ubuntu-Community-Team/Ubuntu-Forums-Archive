---
title: "Speedstep Not Working on Dothan Core Laptop"
date: 2007-01-28
forum: Hardware &amp; Laptops
---

### Post by zizdodrian on 2007-01-28
Hello all.

I deliberated at length as to whether to post this message - after all, I had seen that there were a number of threads about issues with speedstep/clock speed scaling. However, none of the threads solved my problem, and I wasn't too sure about resurrecting one of them.

I run a Toshiba Tecra A3 (unsure of exact hardware details, but it runs the 915GM chipset, with what appears to be a Dothan Core M processor with a maximum clock speed of 1.5Ghz) with Dapper Drake (6.06 LTS.)

The main issue is that the speedscaling/stepping doesn't work, even though my processor should allow 8 stepping increments, and I have no idea where to start.

While I am a competent programmer and web developer on a number of other platforms, and I am not new to linux, I have only just recently begun to use it outside of the GUI, and I wouldn't call myself very profficient with the commandline. For the purpose of the excercise, please consider me a very basic user. :)

Any help would be greatly appreciated.

Thanks in advance,
Christopher

---

### Post by dstockin on 2007-01-30
Hi,

I have the same problem with my HP TC4400 laptop (Dual core T2500 processor). A basic problem seems to be that the directory
/sys/devices/system/cpu/cpu0/cpufreq/
does not exist. Executing modprobe on all modules that are relevant as far as I know (speedstep-lib, cpufreq_userspace, cpufreq_stats, cpufreq_powersave,...) generates no error messages, however
e.g. powernowd doesn't run because the above directory is missing, and similarly the GNOME CPU frequency scaling monitor displays the error message "Frequency Scaling Unsupported".

One hint that I found by googling is that the latest HP BIOS (F.05) might not support the frequency scaling, while an older BIOS version (F.03) did. I did not dare to try this yet but possibly in your case it is also the BIOS's fault?

I would also be very grateful for any help or information.

Thanks in advance,

Dominik

---

### Post by zizdodrian on 2007-01-30
Thanks very much for the reply.

Yes, I had allready looked for  /sys/devices/system/cpu/cpu0/cpufreq/, which doesn't exist on my system, and, like on your laptop, the GNOME scaling widget claims my processor 'doesn't support scaling'.

Something I've noticed is that the ubuntu device manager has no idea what the processor is - it just appears as 'Processor' with no additional information about the make, model, etc.

Unfortunately, I have no idea how to check the version of, or update my BIOS on linux. If possible, could you give me some basic instruction in this respect? Thanks.

Also, (I'm a little ignorant in this respect) is it possible to create the directory  /sys/devices/system/cpu/cpu0/cpufreq/ and then use modprobe to alert the kernel to the presence of scaling functionality?

Incidentally, I installed Ubuntu on my (meromised) Mac Mini to see how XGL would perform with a 950GMA. The processor isn't detected at all by the device manager, and scaling isn't possible either.

Again, thankyou for the swift reply.

---

### Post by dstockin on 2007-01-30
Hi,

it seems we are stuck here. In Device Manager my processor is also simply recognised as "Processor", but I don't know whether this is a problem. Try "dmesg|less" -> I obtain a line 
[17179573.868000] CPU0: Intel(R) Core(TM) Duo CPU      T2500  @ 2.00GHz stepping 0c
and a similar one for the second core.
So the processor is correctly identified in my case - maybe also in yours.

I tried simply creating the cpufreq directory, but this fails. I am also no linux expert so I don't know why. The /sys/... path seems to be different and it seems not possible to create files there.  

One other thing I noticed is that I would expect   "modprobe speedstep-centrino" to work but it doesn't. Only "modprobe speedstep-lib" works in the sense of not generating error messages but the cpufreq directory is not created and cpu frequency scaling doesn't work.

I didn't yet change my BIOS.

I would probably change it via Windows ( I have dual boot). In my case I could download a Windows executable from the HP web site which would install the BIOS. I would not know how to do it from Linux.

But checking which BIOS version you have should be possible by typing a particular key (in my case F10) immediately after switching on. On most computers the key that needs to be typed is printed on screen for a few seconds during booting.

I would still hope that someone with more experience would comment on these issues.

At the moment there is also an active thread on "switching off frequency scaling" on the ubuntu forum but that doesn't help us...

Best regards and thanks!

Dominik

---

### Post by dstockin on 2007-01-30
Hi again,

my problem is solved now :-) It was indeed the BIOS. I downloaded the latest BIOS F.07 for the TC4400 from HP, installed it from Windows, and now speedstep works under ubuntu. I didn't even have to modify the linux installation at all.

I hope you will also solve your problem soon!

Best wishes,

Dominik

---

