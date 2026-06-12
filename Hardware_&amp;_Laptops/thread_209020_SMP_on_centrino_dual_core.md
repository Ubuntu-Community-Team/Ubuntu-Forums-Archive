---
title: "SMP on centrino dual core"
date: 2006-07-04
forum: Hardware &amp; Laptops
---

### Post by ganja_guru on 2006-07-04
Hi everyone,
I'm trying to get both processors working in my friend's HP pavillion dv5200 (1.73 Dual core with a geforce Go 7400).

cat /proc/cpuinfo lists only one processor, so I installed the linux-686 -smp kernel (and the deps that came along with it)

now cat /proc/cpuinfo lists both processors, but the system is highly unstable:

1) crashes within 10 mins with a dark screen and only a hard poweroff works
2) keyboard stops responding early after logging into the desktop

I read somewhere that adding noapic and nolapic to boot options makes a difference, but this didnt seem to help. Please help. I'm using the 386 kernel for now and everything is stable, but only a single processor is being used.

Thanks in advance.

ganja_guru

---

### Post by m94mni on 2006-07-04
I'd just like to say that there are many people that are using core duo processors without issues, so might I suggest either:

* a hardware issue either with the processor or other component. have you run windows successfully? What about temperature, is it overheating?
* An issue with another driver, such as video etc.

---

### Post by ganja_guru on 2006-07-04
I'm having better luck now. I changed KLaptop to 'userspace', disabled 'suspend' 'hibernate' and 'standby', and removed noapic nolapic. The system seems to be fairly stable now. Whats the best way to handle frequency scaling?

---

### Post by insanedc on 2006-07-04
I use the default powernow daemon with the Centrino Duo without problem. I have experimented with the klaptop configuration in the past with disma results. Hope this helps.

Also I don't pass any ACPI boot parameters to the kernel.

---

### Post by samir85 on 2006-07-05
is there a way to see if cpu frequency scaling is working ?

---

### Post by ganja_guru on 2006-07-05
Hear the fans speed up/slow down? :) :)

---

### Post by m94mni on 2006-07-05
[QUOTE=samir85]is there a way to see if cpu frequency scaling is working ?[/QUOTE]

Add the cpu frequency scaling applet (included in gnome-applets) and you'll be able to see the frequency of one processor. Add two of them, and configure one to watch the other CPU...

Or just:

while true; do cat /sys/devices/system/cpu/cpu?/cpufreq/scaling_cur_freq; sleep 1; done

---

