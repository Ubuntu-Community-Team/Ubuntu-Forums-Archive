---
title: "Pentium-M and cpufreqd"
date: 2007-09-02
forum: Hardware &amp; Laptops
---

### Post by MorphiusFaydal on 2007-09-02
I have an HP dv4150us with a Pentium-M 725 (1.6 GHz, 400 MHz FSB, "Dothan"), and I've set up cpufreqd (I uninstalled powernowd), and the detected frequencies are off from what I understood them to be on this chip.

I used to run Gentoo on this laptop, and when I had cpufreqd on there, it would scale from 600 MHz to 1.6 GHz at 200 MHz increments.  Now that I'm running "Feisty Fawn", it detects it at 798 MHz, 1.06 GHz, 1.33 GHz and 1.6 GHz.  I'm using the "speedstep-centrino" driver and the "conservative" governor.

Is this by design, or have I got something configured wrong somewhere?

Thanks in advance, Chris.

---

### Post by -::Bas::- on 2007-09-05
Don't know if it's wrong, but I, having the same processor, have the same increments.
How is the performance of your laptop? 

Mine is quite poor, (MSI s260, 1GB mem, Intel 915GM). For instance, opening a terminal causes the cpu frequency to go up to 1,6GHz en the system monitor tells me it's on a hundred percent for several seconds (between 5 and 8 ), before actually showing me the terminal.

In windows it's all much faster, though there are no such things as terminals unfortunately...

Is it just a slow processor, or is there some misconfiguration going on?

---

### Post by MorphiusFaydal on 2007-09-05
I find performance to be quite good... You may want to check what governor you're using... That behavior sounds like 'ondemand'... I'm using 'conservative', and it stays at 798MHz most of the time.  When I open Firefox, or right after I log in, it jumps to 1.06 or 1.33.  I rarely see it at 1.6

1.25 GB RAM, 915GM, whatever mobo HP put in there.

And my whole point in posting this thread is that at 798MHz, my lap is still getting hot.  When it scales down to 600 MHz (which it's only done in Gentoo), it stays cold.  There's also a noticeable battery life difference.

---

### Post by MorphiusFaydal on 2007-09-05
I just noticed that I have no /etc/cpufreqd.conf

Is that normal, or do I need to make one?

---

### Post by Djembe on 2007-09-05
> **MorphiusFaydal said:**
> I just noticed that I have no /etc/cpufreqd.conf

Is that normal, or do I need to make one?

I don't have one either, but I'm using powernowd so maybe I don't need it.  

To answer the original poster, I've got a 1.86 Ghz Pentium M CPU, and using the ondemand governor, I have 5 steps, as opposed to the 8 I have in Windows.  I'm not really sure why, but like MorphiusFaydal, I haven't had any performance issues.

---

### Post by MorphiusFaydal on 2007-09-05
> **Djembe said:**
> I don't have one either, but I'm using powernowd so maybe I don't need it.  

To answer the original poster, I've got a 1.86 Ghz Pentium M CPU, and using the ondemand governor, I have 5 steps, as opposed to the 8 I have in Windows.  I'm not really sure why, but like MorphiusFaydal, I haven't had any performance issues.

Powernowd uses different configs from cpufreqd.. But I've had more experience with cpufreqd.. Just enough to tell that I don't think it's working right..

---

### Post by -::Bas::- on 2007-09-05
> **Djembe said:**
> I haven't had any performance issues.
Sorry to hijack your thread, but my performance isses have vanished. Just freshly installed ubuntu on this lappie. Probalbly needed another reboot. Reminds me of windows. LOL

Anyway, sorry Morph but I haven't got any anwers to your questions. Just hijacking the thread.

---

### Post by MorphiusFaydal on 2007-09-06
must have been a temporary thing. :)

---

