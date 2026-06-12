---
title: "Cooling problems under Ubuntu"
date: 2011-02-27
forum: Hardware
---

### Post by CST10 on 2011-02-27
Ubuntu no long controls the fan to help deal with heat on my Toshiba Satellite L505, and won't bump fan speed when the computer heats up. It just runs at the same low speed, until eventually the computer shuts itself off to save itself. 

Part of the problem is now it's also running nearly 100% cpu all the time, recently. There's nothing in the system monitor that can show me what's causing it... 

On top of that, my battery has suddenly died (Won't hold a full charge) during all of this too, but it wouldn't shock me if the heat had something to do with it (computer idling while I'm away, over heating itself for one reason or another). Lithium doesn't like heat...

---

### Post by CST10 on 2011-02-28
Bump

---

### Post by CST10 on 2011-03-01
Any help on this...?

I need the OS to know when to cool down the computer...

---

### Post by sammiev on 2011-03-02
Type in Toshiba+heat in the search bar and there maybe a few things you can try. Running with Toshiba-650 here and the fan works alright, a little hotter than windows but working. GL :)

---

### Post by CST10 on 2011-03-03
> **sammiev said:**
> Type in Toshiba+heat in the search bar and there maybe a few things you can try. Running with Toshiba-650 here and the fan works alright, a little hotter than windows but working. GL :)
Nothing works, the ACPI... codes do nothing. Main problem is the CPU running at 100% (Or one core will run 100% while the other runs a 50%, then they switch and the other one jumps to 100% and then the other drops to 50%). 

No problems in windows, it's all Ubuntu. I can't figure out why,
A) The CPU is working so hard, when the task manager shows nothing consuming that much CPU
B) Why the fan doesn't react to temperature any more.

---

### Post by sammiev on 2011-03-03
You will need to go into system monitor and find out what's taking up all your resources. GL :)

---

### Post by skeilman on 2011-03-03
Hello everyone. I have the same problem. My laptop (acer Aspire5715Z) work very good under Windows7. But when i work with Ubuntu (Powerpack 2010.2), i can surf the web for around 30 min and comp just shutdown. i know why this happening (overheating), but what can i do?:confused:
P.S. i have the both system instaled. Win7 work fine - Ubuntu shutdown

---

### Post by CST10 on 2011-03-03
> **sammiev said:**
> You will need to go into system monitor and find out what's taking up all your resources. GL :)

> The CPU is working so hard, when the task manager shows nothing consuming that much CPU

Replace task manager (windows, lol) with system monitor. 

[[IMG]http://img268.imageshack.us/img268/6210/screenshot4rl.png[/IMG]](http://img268.imageshack.us/i/screenshot4rl.png/)

This is the weird CPU action it has in Ubuntu. Ignore the low battery, it does this regardless of charge.

---

### Post by peculiar penguin on 2011-03-03
Install and run powertop (sudo powertop on the command line), look at the "Avg residency" and "P-states (frequencies)" columns. When the system is idle, the CPU should spend almost all of its time at the lowest frequency and in some sort of power saving mode (Cx where x != 0).

The number of "Wakeups-from-idle per second" can also be a hint - if it's a ridiculously large number something is very wrong (usually something ACPI-related).

```
sudo powertop -d > $HOME/Desktop/powertop.txt
```will dump the powertop output into a text file on your desktop in case you see anything weird and want to post it here.

---

### Post by CST10 on 2011-03-03
> **peculiar penguin said:**
> Install and run powertop (sudo powertop on the command line), look at the "Avg residency" and "P-states (frequencies)" columns. When the system is idle, the CPU should spend almost all of its time at the lowest frequency and in some sort of power saving mode (Cx where x != 0).

The number of "Wakeups-from-idle per second" can also be a hint - if it's a ridiculously large number something is very wrong (usually something ACPI-related).

```
sudo powertop -d > $HOME/Desktop/powertop.txt
```will dump the powertop output into a text file on your desktop in case you see anything weird and want to post it here.

Here you guy. In windows it'll idle at the lower CPU speed just fine, and at a normal CPU usage. It's only doing this wierd stuff under Ubuntu. The fan problem wouldn't be such an issue if the CPU wasn't always running hot.

[[IMG]http://img141.imageshack.us/img141/5307/screenshotmqo.png[/IMG]](http://img141.imageshack.us/i/screenshotmqo.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by Blasphemist on 2011-04-11
I have the same laptop and had the same problem. Never did figure it out for sure.

I can tell you that a couple weeks ago I made an effort to shrink windows partition and do a clean install of natty over my upgrade of natty. In doing this I chose to not save my existing natty but rather overwrite it. I had a backup of home.

The only thing I can think of that could have been affecting me in maverick and natty that I didn't re-enable was BOINC. [http://en.wikipedia.org/wiki/Berkeley_Open_Infrastructure_for_Network_Computing](http://en.wikipedia.org/wiki/Berkeley_Open_Infrastructure_for_Network_Computing)

It's manager came installed on my clean natty but I didn't join my project again after the install. I don't remember what all settings I'd used for BOINC and I may have been too aggressive with how much CPU to use.

---

