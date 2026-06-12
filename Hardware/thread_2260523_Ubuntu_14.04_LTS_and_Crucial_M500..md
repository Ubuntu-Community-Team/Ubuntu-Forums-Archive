---
title: "Ubuntu 14.04 LTS and Crucial M500."
date: 2015-01-12
forum: Hardware
---

### Post by warren3 on 2015-01-12
Hi.

Does the M500 Queued-Trim data corruption bug affect Ubuntu 14.04?  I have been running the Crucial mSata M500 and I get hard freezes and a lot of internel error messages.  The Crucial website states  
 **[FONT=Liberation Serif, serif][SIZE=3]Dangerous for use in kernels:[/SIZE][/FONT]**
 
[LIST]
[*]**[FONT=Liberation Serif, serif][SIZE=3]3.12 	(before 3.12.29);[/SIZE][/FONT]**

[*]**[FONT=Liberation Serif, serif][SIZE=3]3.13 	(before 3.13.7);[/SIZE][/FONT]**

[*]**[FONT=Liberation Serif, serif][SIZE=3]3.14 	(before 3.14.20);[/SIZE][/FONT]**

[*]**[COLOR=#ff0000][FONT=Liberation Serif, serif][SIZE=3]3.17 	(before 3.17.1) - regression in the blacklist, fixed in 3.17.1[/SIZE][/FONT][/COLOR]****[FONT=Liberation Serif, serif][SIZE=3].[/SIZE][/FONT]**
[/LIST]
  
 **[FONT=Liberation Serif, serif][SIZE=3]Safe kernels:[/SIZE][/FONT]**
 
[LIST]
[*]**[FONT=Liberation Serif, serif][SIZE=3]anything 	before 3.12;[/SIZE][/FONT]**

[*]**[FONT=Liberation Serif, serif][SIZE=3]3.12.29 	and later;[/SIZE][/FONT]**

[*]**[FONT=Liberation Serif, serif][SIZE=3]3.13.7 	and later;[/SIZE][/FONT]**

[*]**[FONT=Liberation Serif, serif][SIZE=3]3.14.20 	and later;[/SIZE][/FONT]**

[*]**[FONT=Liberation Serif, serif][SIZE=3]3.15 	(all);[/SIZE][/FONT]**

[*]**[FONT=Liberation Serif, serif][SIZE=3]3.16 	(all);[/SIZE][/FONT]**

[*]**[FONT=Liberation Serif, serif][SIZE=3]3.17.1 	and later.[/SIZE][/FONT]**

[*]
[/LIST]
 I am running kernel 3.13.0.43.  So does this affect me?

---

### Post by weatherman2 on 2015-01-12
Do you have any old kernels saved (automatically kept after updates) that you can try?

---

### Post by warren3 on 2015-01-12
I'm afriad not.  I built my Ubuntu system only recently and have only got kernels 3.13.0.43., 3.13.0.40. and 3.13.0.32.

---

### Post by weatherman2 on 2015-01-12
Is it easy to reproduce the problems?  Or are they just random freezes?

I'd probably find a way to install a different kernel known not to be one of the problem kernels just for testing.  I know you can do it, not sure what the easiest way is off the top of my head.  Freezes could be caused by something other than the SSD of course.

My M500 works great in my laptop, but I am using Ubuntu 12.04.2 so a much older kernel.

---

### Post by PhilGil on 2015-01-12
I'm not familiar with the bug, but based on your post you may be affected. Kernel 3.16.0 (which is safe based on Crucial's list) is available in the trusty-updates repository.

---

### Post by warren3 on 2015-01-12
Hi.

I have just looked in my Kernel log and find this entry:

ata4.00: disabling queued TRIM support
ata4.00: ATA-9: Crucial_CT120M500SSD3, MU05, max UDMA/133
ata4.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
ata4.00: supports DRM functions and may not be fully accessible
ata4.00: disabling queued TRIM support
ata4.00: configured for UDMA/133

So it looks like the queued TRIM is disabled.

---

