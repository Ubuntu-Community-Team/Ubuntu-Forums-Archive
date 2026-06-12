---
title: "How can I control cpu frequency?"
date: 2008-06-09
forum: Hardware
---

### Post by clapton on 2008-06-09
Hello people!

Is there a way to control cpu freq?
I wanna less performance when I'm working with battery and more performance with AC power.

I'm searching for utilities like "powerforgear" to windows.

Thanks :)

---

### Post by NikoC on 2008-06-09
On my intel mobile (quite and old system) I can type in a terminal:
for powersaving
sudo cpufreq-selector -g powersave
for best performance
sudo cpufreq-selector -g performance
on demand:
sudo cpufreq-selector -g ondemand

Cheers

---

### Post by ajgreeny on 2008-06-09
It depends entirely on your hardware; some cpus will not support frequency scaling at all, including mine, an AMD sempron 2400+.

---

### Post by clapton on 2008-06-09
> **NikoC said:**
> On my intel mobile (quite and old system) I can type in a terminal:
for powersaving
sudo cpufreq-selector -g powersave
for best performance
sudo cpufreq-selector -g performance
on demand:
sudo cpufreq-selector -g ondemand

Cheers

I don't know what kind of software shoud be installed.

---

### Post by clapton on 2008-06-09
I've got Asus F3Jc. with a intel Processor T5500.

I'm trying using lot of things, but I can't change frequency.

How can I do?

---

### Post by clapton on 2008-06-10
I dind't understand why it always warm me:
"Frequency scalling not supported"

---

### Post by Kantis on 2008-06-10
This is how I do it on my old ThinkPad T42:

Step 1:
Press Alt + F2

Step 2:
type: gconf-editor

Step 3:
Navigate to:
/apps/gnome-power-manager/cpufreq


The "conservative" setting seems to work best for me. I have set my performance_ac as 85 and performance_battery as 25.

I am a newbie at both Ubuntu and computers in general, and can assure you that every bit of software I use has been included in the Hardy Heron installation package or its automatic updates, i.e. I didn't have to manually install anything for this.

---

### Post by clapton on 2008-06-10
I've got NO scaling support.
My problem is similar this [http://ubuntuforums.org/showthread.php?t=380055](http://ubuntuforums.org/showthread.php?t=380055)

---

### Post by sdennie on 2008-06-10
I don't know how to help with your frequency scaling not working but, as has been pointed on a few times on this forum, setting the governor to "powersave" probably uses more power than leaving it at "ondemand" and, as far as performance, you won't see any difference between "ondemand" and "performance" on most machines.

---

### Post by Yellow Pasque on 2008-06-10
Hi clapton, boot into the BIOS/system setup and look for EIST or Speedstep controls.

---

