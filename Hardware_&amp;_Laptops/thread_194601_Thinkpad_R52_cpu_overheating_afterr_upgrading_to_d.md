---
title: "Thinkpad R52 cpu overheating afterr upgrading to dapper"
date: 2006-06-11
forum: Hardware &amp; Laptops
---

### Post by punda on 2006-06-11
Hi all,

I was an happy "old breezy" driver... with 2.6.12 kernels my thinkpad cpu temperature stays between 40 and 50 degres and reaches 60° on  high cpu usage...

after upgrading from kubuntu breezy + kde 3.5 by apt-get I've this problem:

cpu temperature stays high (near 60°) and lauching every program causes cpu temperature raising by 10/15°

with linux-image-686-2.6.15 cpu temperature stays near 60° and cpuscaling doesn't work;

with linux-image-386-2.6.15 cpu temperature stays near 55°, cpuscaling works but on high cpu usage reaches 70/80 degrees

with a vanilla kernel 2.6.16 home compiled: same  behavior...

I've tried both ubuntu and kubuntu dapper from live cd: same behavior...

No help from googling...

machine tipe: Thinkpad R52 1GB ram / ati X300 / centrino 1.8GHz

Any tip? or it's just a  "feature" of kernels >2.6.15 ??

thanks,

---
punda

---

### Post by pubwho on 2006-06-14
I don't want to sound daft, but seeing as nobody else has chipped in. Are you sure this hasn't got anything to do with the recent heat spell across Europe?

If the temperate outside your case rises, then the temperature inside, including the CPU will rise too.

---

### Post by zahidism on 2006-06-14
there are a bunch of threads concerning laptops and over heating, check them out if you want.  i do not believe there is a solution at this time.  my dell 600m idles at 52 degrees in linux whereas it idles at 40 degrees in Windows....:(

---

### Post by punda on 2006-06-15
[QUOTE=pubwho]
If the temperate outside your case rises, then the temperature inside, including the CPU will rise too.[/QUOTE]

Sorry for don't mentioning this before but test were done in temperature controlled ambient and the differences between 2.6.12 and 2.6.16 were the ones reported on my previus post.

---
punda

---

### Post by punda on 2006-06-15
[QUOTE=zahidism]there are a bunch of threads concerning laptops and over heating, check them out if you want.  i do not believe there is a solution at this time.  my dell 600m idles at 52 degrees in linux whereas it idles at 40 degrees in Windows....:([/QUOTE]

I know, but my problem started with the 2.6.15 kernels shipped with dapper, previus 2.6.12.x kernel stays in linea with window$ temperatures.
With 2.6.12 my thinkpad was running at 40/45 degrees and was reaching 60/62 max when compiling a new kernel...
Now I'm running a 2.6.15-386 (ubuntu dapper standard) and  compiling my new 2.6.16-beyond4.1 has reached 80/86 degrees... too much considering that test are done in a room at 21° ;-(((
...if I use the 2.6.15-686 temperature of 70° are reached "only" in opening kmail ;-[


cy,

punda

---

### Post by EpicCrusadr on 2006-06-28
I've noticed that the temperature of my Toshiba m55, while running linux, is also noticeably high. I have also noticed that my fan doesn't come on as often as it does in windows. How can I check the actual temperature of the CPU?

---

### Post by fast1 on 2006-06-28
cat /proc/acpi/thermal_zone/THM/temperature

---

### Post by EpicCrusadr on 2006-06-28
I'm gessing that my comuter doesn't have a thermal sensor, because there is nothing in the "thermal_zone" directory. Maybe it only has a thermistor to cut out when it gets too hot. Is that the case?

---

### Post by Hellkeepa on 2006-06-28
HELLo!

For a temporary workaround to this problem, I suggest reading my thread over here:
[http://ubuntuforums.org/showthread.php?t=204100](http://ubuntuforums.org/showthread.php?t=204100)

I've read quite a few threads about this, and it seems that everyone is afflicted with the bug mentioned in the thread I linked to. Thus the workaround is very likely to help.

Happy codin'!

---

