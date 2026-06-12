---
title: "overclocking broken natty  11.04"
date: 2011-09-21
forum: Hardware
---

### Post by gracchus on 2011-09-21
My comp is an intel 920 i7 on an asus p6t v2 mobo.  I was working fine on 10.04 or 10.10 I don't remember which. During the install of 11.04 the OS would crash on boot with an error that said "No *human* readable *MCE* decoding support on this *CPU* type".  The error went away if I turned my overclock off.

Now I have 11.04 installed and running with the overclock off perfectly.  When I turn the overclock back on it gives me a different error during boot up saying "general error mounting filesystem"

I'm only a linux novice so I could use some help.  I saw another thread where people were talking about fixing underclocking on laptops and they said to either use an older 2.6.35 kernel or a newer one from one of these links possibly [https://launchpad.net/~guido-iodice/...el-and-drivers]("https://launchpad.net/%7Eguido-iodice/+archive/kernel-and-drivers") or [http://kernel.ubuntu.com/~kernel-ppa...3.0.3-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.0.3-oneiric/")

What should I do to fix this?  Thanks

---

### Post by gracchus on 2011-09-22
bump

---

### Post by .... on 2011-09-22
How much is your OC? Have you tried lower OC's?

---

### Post by gracchus on 2011-09-23
My mobo is crossflashed to a special p6t v1 bios that lets me lock my multi at 21x without thermal throttling pushing it automatically down to 20x.  My overclock which was causing crashes was 4.2ghz, 21x multi, 200 base clock.  I tried 4.0ghz, 20x multi, and 200 base clock and it solved the crashing.  I wonder what changed in the new version of ubuntu since it worked fine in 10.04.  This should be fixed as I believe my overclock is very stable it must be a software problem.

---

### Post by maul9999 on 2011-09-23
> **gracchus said:**
> My mobo is crossflashed to a special p6t v1 bios that lets me lock my multi at 21x without thermal throttling pushing it automatically down to 20x.  My overclock which was causing crashes was 4.2ghz, 21x multi, 200 base clock.  I tried 4.0ghz, 20x multi, and 200 base clock and it solved the crashing.  I wonder what changed in the new version of ubuntu since it worked fine in 10.04.  This should be fixed as I believe my overclock is very stable it must be a software problem.

You're overclocked too much.  Ubuntu can't handle too much overclock.  try to keep it lower.   Oh and you don't need to overclock.

---

### Post by gracchus on 2011-09-26
Your reply makes absolutely no sense.  I've pointed out a clear regression in this version of ubuntu.  My overclock was 100% stable in version 10.04 and in windows so it is not too high.  There are many purposes for overclocking but that is completely irrelevant to resolving a problem with the operating system.

---

### Post by maul9999 on 2011-09-26
> **gracchus said:**
> Your reply makes absolutely no sense.  I've pointed out a clear regression in this version of ubuntu.  My overclock was 100% stable in version 10.04 and in windows so it is not too high.  There are many purposes for overclocking but that is completely irrelevant to resolving a problem with the operating system.

I'm not talk about 10.10.  I'm talk about that 11.04 can't handle overclock because it was not stable-ready.  Sometime Natty give me a trouble.

---

### Post by .... on 2011-09-26
> **gracchus said:**
> My mobo is crossflashed to a special p6t v1 bios that lets me lock my multi at 21x without thermal throttling pushing it automatically down to 20x.  My overclock which was causing crashes was 4.2ghz, 21x multi, 200 base clock.  I tried 4.0ghz, 20x multi, and 200 base clock and it solved the crashing.  I wonder what changed in the new version of ubuntu since it worked fine in 10.04.  This should be fixed as I believe my overclock is very stable it must be a software problem.
You need to get dmesg logs from when it crashes. Don't expect a lot of help from kernel devs.. :P

---

