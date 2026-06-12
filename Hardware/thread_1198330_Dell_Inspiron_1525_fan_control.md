---
title: "Dell Inspiron 1525 fan control"
date: 2009-06-27
forum: Hardware
---

### Post by Unkraut on 2009-06-27
Hi!
I've searched the whole Internet page by page until its very end. But I haven't found anything that worked.
What I want is to control the fan speed of my Dell Inspiron 1525 because it is so loud most of the time. There are at least three fan speed steps. The highest I know kicks in at 60° C and above, the second highest at 50° C. Below 50° C the fan runs pleasently silent (but it still runs). I believe the fan turns off at 40° C and below, but I'm not quite sure.

Anyhow, most of the time CPU temperature is above 50°C. At this temperature fan speed is bearable - only a tiny bit annoying sometimes. But when temperature rises to 60° it becomes so annoying I would like to smash my laptop against the wall. The most annoying thing is: When temperature has risen above 60° and then goes down below 60° the fan speed does not go down anymore. It only goes down finally when temperature sinks below 50° - which virtually never happens.

What I tried:

1. I installed i8k and the i8k plugin for gkrellm, did
```
sudo modprobe i8k -force=1
```, started gkrellm, activated the i8k plugin and changed the temperature/fan speed settings there. But that had no effect. The fan still ran exactly the same way as before. Also tried running gkrellm as root. Didn't help either.

2. I installed and ran dellfand. Here's the output:
```
trollkotze@schrotthaufen-mobil:~/dellfand-0.9$ sudo ./dellfand 0 5 50 57 65
[sudo] password for trollkotze: 
Fan 0 Status 1->0 Speed 90000 CPU Temp 48C
dellfand: warning: set fan 0 status to 0 last cycle, it's now 1 (BIOS interference ?)
Fan 0 Status 1->0 Speed 90000 CPU Temp 48C
Fan 0 Status 1->0 Speed 90000 CPU Temp 48C
Fan 0 Status 1->0 Speed 90000 CPU Temp 49C
...

```
So, the fan speed should step down but it doesn't. I read somewhere that I should update the BIOS to the newest version. Did that. No effect.
I read somewhere I should try booting with acpi=off. The result was that speed-step did not work and the CPUs constantly ran at highest speed and had of course to be cooled down.

Does anyone know what to do?

---

### Post by Sealbhach on 2009-07-14
Hi, I've got a noisy whiny fan too so I found this here:  [http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)  .

---

