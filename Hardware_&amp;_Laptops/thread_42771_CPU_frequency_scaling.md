---
title: "CPU frequency scaling"
date: 2005-06-19
forum: Hardware &amp; Laptops
---

### Post by jeremytaylor on 2005-06-19
Hi,
I have a centrino based laptop.... How do I know if the cpu frequency scaling is working? The little applet to show it just displays a question mark and my battery life is pretty shocking so I have a feeling it's not doing what it should...

thanks
Jeremy

---

### Post by shof2k on 2005-06-20
Install powernow and that will link to the cpu frequency scaling applet.

---

### Post by jeremytaylor on 2005-06-20
hmm, I have powernow installed and when i try to reinstall it claims that cpu frequency scaling is not supported....

does powernow know about sonomas yet?

thanks for the help

Jeremy

---

### Post by kiddyfurby on 2005-06-20
Centrino? mine work out of the box (the scaling thing)

---

### Post by snop on 2005-06-20
Hi,

I own an Acer Travelmate 4001Wlmi and I had problems with frequency scaling (it uses a 1.5 Centrino but there was a message saying that "frequency scaling was not supported for this processor").

I had to load the module acpi_cpufreq. So try to issue this command and see if this works for you:

```
sudo modprobe acpi_cpufreq
```

If it does work you can make your change permanent in your /etc/init.d/local and append the line "modprobe acpi_cpufreq" (without quotes).

SnOp

PD: For more info check [the bug report](https://bugzilla.ubuntu.com/show_bug.cgi?id=5103) I filled.

---

### Post by shof2k on 2005-06-21
You may also need to do **sudo modprobe p4-clockmod**.  Let us know how you get on.

---

### Post by jeremytaylor on 2005-06-21
excellent it worked!
thanks for all the help
Jeremy

---

### Post by jeremytaylor on 2005-06-21
erm... how do i make the change permanent... I seem to have to do that modprobe p4 clockmod thing every time i start up.

Jeremy

---

### Post by stonecrest on 2005-06-21
Just add "p4-clockmod" to your /etc/modules file (pretty sure that's the file, I'm not at my linux box right now).

---

### Post by jeremytaylor on 2005-06-21
thanks again...

one other problem.... my processor is supposed to be 1.86GHz and when i look at /proc/cpuinfo it agrees with that but the little monitoring applet says that 100% is at 1.4GHz.

what's happening?

thanks

Jeremy

p.s. I've been playing about and the output from dmesg includes 

speedstep-centrino: obtaining ACPI data failed
speedstep-centrino: found unsupported CPU with Enhanced SpeedStep: send /proc/cpuinfo to Jeremy Fitzhardinge <jeremy@goop.org>
eth0: no IPv6 routers present
Access to /proc/cpufreq is deprecated and will be removed from (new) 2.6. kernels soon after 2005-01-01
p4-clockmod: Warning: Pentium M detected. The speedstep_centrino module offers voltage scaling in addition of frequency scaling. You should use that instead of p4-clockmod, if possible.
p4-clockmod: P4/Xeon(TM) CPU On-Demand Clock Modulation available

any ideas?

---

### Post by jeremytaylor on 2005-06-21
hi again.

sorted the problem... a BIOS update and then the centrino speedstep module could cope with it all... now running at the proper speed and the little applet is telling what that is and everything.

thank you everyone for your help

Jeremy

---

### Post by shof2k on 2005-06-21
Glad that it all worked for you.  Welcome to linux / Ubuntu :)

---

### Post by dezgot on 2005-06-21
jeremytaylor, I would like an applet that shows me what the powernow dameon is doing, could you tell me which you are using?

---

### Post by jeremytaylor on 2005-06-22
Hi there
I'm just using the frequency scaling applet that comes with gnome.... right click on the bar ==> add applet ==> cpu frequency monitor.

It's not very sophisticated but at least it lets you know that powernowd is actually working!

Does anyone know of anything better, i.e. more like the centrino hardware manager for windows?

Jeremy

---

### Post by dezgot on 2005-06-23
ah, of course i found it right before i checked for your response.  Thanks.  I still wonder if its working properly, the computer still seems to have alot of fan activity and such.   I guess in windows the max voltage it will use is .988v and in linux that would be the minimum, that could make it that much hotter i think (in RMClock or Centrino Hardware Tools i changed down the voltages at the multipliers, at 600mhz it can run perfectly stable at .7v!)

---

### Post by jeremytaylor on 2005-06-23
I'm still a little puzzled about the choice of scalings that is made. Of my 8 possible steps 5 of them seem to be at the maximum frequency and the lowest it goes is to about 40% of the maximum clock rate.

I'm not too bothered as it's already boosted my battery life consierably and reduced the operating temperature a fair amount; just seems a bit bizarre!

Jeremy

---

### Post by laue on 2005-10-28
AMD and intel both quit using the cpu clock frequency in their cpu names, as a higher frequency does not imply more speed. Now, a higher model number implies a better performing cpu, not only a higher clock frequency.

e.g. I have a amd Athlon xp 2000+ which runs at a clock frequency of 1660 MHz or something. An Intel with a version number of 2000 or something will typically have a higher clock frequency than an amd 2000, but they perform comparably.

---

