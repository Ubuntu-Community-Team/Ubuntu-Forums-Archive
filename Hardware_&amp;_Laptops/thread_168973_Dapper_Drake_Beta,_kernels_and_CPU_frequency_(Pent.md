---
title: "Dapper Drake Beta, kernels and CPU frequency (Pentium M laptop)"
date: 2006-05-01
forum: Hardware &amp; Laptops
---

### Post by jcraveiro on 2006-05-01
**Please move this to the appropriate forum. My apologies for the mistake.**

Hi there!

I'm not new to using Ubuntu, and less even to Linux, but I am a total newbie as what regards laptops -- it is the first I own, and the first I put Linux on.

I now own a HP Pavilion dv1597ea (Pentium M Sonoma 750, @1,86GHz), and I installed Ubuntu Dapper Beta on it. On a side note, I must say: it was s.m.o.o.t.h. --- the only thing not working is the Texas Instruments card reader, but word is that there's a driver already in development.

Anyway: out of the box, Dapper, obviously, brings the 2.6.15-20-386 kernel.

Since I have the perception that 'specialized' kernels have advantage over 386 (at least I have better peformance with linux-k7 on my AMD desktop), I also installed the 686 kernel (2.6.15-21-686).

What I noticed (rather than any performance difference *per se*), was that CPU frequency scaling worked very differently --- it isn't as dynamic as the one performed by the 386 kernel, it seems to 'stick' longer at higher frequencies. Furthermore, despite the GNOME applet reports the frequency changes, the gDesklet (FTB-cpu-plot) doesn't (it always says the CPU is at 1,86GHz).

Any thoughts on this? This is a field that is so strange to me that I don't even know the right question to make! ;) What I am really curious about is:
1) is there any known problem/disadvantage with linux-686's speedstep implementation?
2) what are other advantages of using linux-686 rather than linux-386?

Thanks in advance.

---

### Post by rado_london on 2006-05-01
Hi. I dont have the exact answer for the question but my experience could be helpful. I have dv4145ea laptop which is similar to yours. 386 kernel works just fine, supports frequent scalling, also keeping my system cool for days. With 686 the batery life is shorter and my system is going fu**ing hot. So I would sugest you to use the 386 kernel. For the card reader mine is texas instruments as well and it works for SD cards but not for MS which i mostly use.

---

### Post by jcraveiro on 2006-05-01
[QUOTE=rado_london]Hi. I dont have the exact answer for the question but my experience could be helpful. I have dv4145ea laptop which is similar to yours. 386 kernel works just fine, supports frequent scalling, also keeping my system cool for days. With 686 the batery life is shorter and my system is going fu**ing hot. So I would sugest you to use the 386 kernel. For the card reader mine is texas instruments as well and it works for SD cards but not for MS which i mostly use.[/QUOTE]

Thank you very much for your testemonial --- for this specific purpose, experience is already very helpful. :)

(As for the card reader, in fact, I only had the opportunity to test it for xD cards.)

---

### Post by thasheep on 2006-05-01
1) I don't know that there's any difference in how the two kernels implement speedstep but the 686 kernel probably tries to get the processor to work harder in general (because it knows it can) so it's more likely to sit on a higher workload. However, you can set the frequency or governor manually if you configure gnome-applets to do so (sudo dpkg-reconfigure -p low gnome-applets)
2) The only real advantage of linux-386 is that it will work on older (pre pent II) computers whereas 686 won't.

A couple of other notes, my TI multi-card reader works out of the box on dapper (on a toshiba tecra a3), with the mmc and sd cards i have but the driver is a bit sensitive with non-ubuntu kernels (but can be beaten into shape with the 2.6.17-rc ones). Also, I think this (Hoary) is the wrong forum.

---

### Post by jcraveiro on 2006-05-01
[QUOTE=thasheep]1) I don't know that there's any difference in how the two kernels implement speedstep but the 686 kernel probably tries to get the processor to work harder in general (because it knows it can) so it's more likely to sit on a higher workload. However, you can set the frequency or governor manually if you configure gnome-applets to do so (sudo dpkg-reconfigure -p low gnome-applets)
[/QUOTE]

Yes, I used:
```
sudo chmod +s /usr/bin/cpufreq-selector
```
and that allows me to choose freq/governor in the applet, be, even so, the governors seem to be more prone to higher loads on 686 than on 386.

[QUOTE=thasheep]Also, I think this (Hoary) is the wrong forum.[/QUOTE]

Noticed it afterwards, already added that to the original post. Sorry.

---

