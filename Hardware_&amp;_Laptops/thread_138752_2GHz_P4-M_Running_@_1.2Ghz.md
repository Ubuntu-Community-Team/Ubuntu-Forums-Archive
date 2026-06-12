---
title: "2GHz P4-M Running @ 1.2Ghz"
date: 2006-03-02
forum: Hardware &amp; Laptops
---

### Post by OPaul on 2006-03-02
My 2.00 GHz Pentium 4-M is only running at 1.20GHz, even though it is running on AC power, and not the battery. How do I make it run at its full speed?

---

### Post by OPaul on 2006-03-03
After a closer examination it does go to 2.0GHz when I open an application. So I'm assuming this is the "stepping" function... does anyone have any information on this feature in Linux? For example, how to configure it.

---

### Post by dbott67 on 2006-03-03
[QUOTE=OPaul]After a closer examination it does go to 2.0GHz when I open an application. So I'm assuming this is the "stepping" function... does anyone have any information on this feature in Linux? For example, how to configure it.[/QUOTE]

I don't know for sure (seeing that I'm running Ubuntu on a P2-300 :green_with_envy: ), but you could check the system BIOS for power saving options.  Generally, there's a setting in there that you can change.

-Dave

---

### Post by OPaul on 2006-03-05
The only option in the BIOS is for Battery Save mode, which is set to Full. There is nothing for AC Power.

When I had Windows installed the only time the CPU would down clock was when it was running off the battery. When the AC power was plugged in the CPU would always run at full speed.

---

### Post by towsonu2003 on 2006-03-05
search for powernowd in the forums. that should be the one that's doing the trick. 

oh, and, *don't fix it if it ain't broke* ;)

---

### Post by patrickfromspain on 2006-03-06
why shouldn't it down clock when running on AC Power??? I mean.. why should the CPU be running at 100% if you only have firefox opened? 

If it clocks down, the  temperature also falls and the fan will also turn on less times... Only good things, and temperature is very important in a laptop.

Anyway... when you need the full power (because Amule is hashing files or you're compiling a kernel or whatever) the CPU will go up tu 2Ghz automatically.

I'd say just let it just as it is, as it is working perfectly fine.

---

### Post by Jason_25 on 2006-03-06
There are various problems with the underclocking crap.  Anyway, to remove it, uninstall powernowd.

---

### Post by OPaul on 2006-03-06
[QUOTE=patrickfromspain]why shouldn't it down clock when running on AC Power??? I mean.. why should the CPU be running at 100% if you only have firefox opened? 

If it clocks down, the  temperature also falls and the fan will also turn on less times... Only good things, and temperature is very important in a laptop.

Anyway... when you need the full power (because Amule is hashing files or you're compiling a kernel or whatever) the CPU will go up tu 2Ghz automatically.

I'd say just let it just as it is, as it is working perfectly fine.[/QUOTE]

I've noticed several occasions where my laptop seemed to be straining when opening an application, and the CPU would remain down clocked.

Can powernowd be set to only run when the laptop is operating off the battery?

---

### Post by Miguel on 2006-03-06
Hi OPaul,

I suppose you could easily edit the powernowd init script so that, if you are running on AC during bootup,  powernowd always uses maximum clock. 

It should go on the line of looking at /proc/acpi/ac_adapter/AC/state. If it reports it is on-line, use all the cpu clock, while if it is discharging, switch to the usual stepping policy. 

Anyway... won't your laptop run a bit too hot if it is always at 2GHz?

---

### Post by Jason_25 on 2006-03-06
[QUOTE=Miguel]
Anyway... won't your laptop run a bit too hot if it is always at 2GHz?[/QUOTE]
This would imply that the laptop could not run at 100% cpu all of the time, which would be ridiculous.  Stability testing programs and distributed computing use 100% of the CPU.

---

### Post by Miguel on 2006-03-07
No offense intended on the following post, but I'm spanish and English is my second/third language.

Sorry Jason, but I don't understand what you said. Could you explain it again, please?

From the thread's title and first post, OPaul's CPU is a 2.0GHz P4-M that can downclock to 1.2GHz. I said that it can be made that the CPU is always at 2.0GHz. You suggested that, on this settings, he could not use all 100% of his CPU. Well, if the stepping is disabled and the CPU is running at his max speed, I fail to see why he couldn't fully use his proccessor.

And, again, I will be grateful if you explain to me what do stability testing programs and distributed computing (what is this? multiprocessor calculations?) have to do with clock speed stepping on a CPU.

---

### Post by patrickfromspain on 2006-03-07
in my celeron M underclocking works fine, after having installed emifreq-applet and loaded the p4-clockmod module... if it needs power, it instantly raises de cpu speed. Maybe you should try that.

---

