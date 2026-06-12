---
title: "Process Eating up Computing power"
date: 2008-12-24
forum: Hardware
---

### Post by 89gtt on 2008-12-24
I am runing hardy heron on a compaq Presario desktop that has a single core Intel Celeron processor clocked at 2.5ghz and it has 385mb worth of ram.
the problem is that when ever the computer goes into to standby or sits idle for a while it comes back on with the processor beinng overworked. I ran top to find out what was eating the processing and found
*PID USER PR NI VIRT RES SHR S %CPU %MEM TIME- COMMAND*
*45  root 15 -5 0    0   0   R 40+  0.0 110:06 kacpi_notify*
That process is the only one that looks abnormally high for a computer that is just idleing. I tried to find a fix for it but it seemed no one had a problem with the same process/command. Any attempt to use the computer causes the processor to work at 100% for to long of a period to open anything. I don't know what the command is to kill the process through top and don't know IF it should be killed.

---

### Post by squee on 2008-12-24
mech, people will know more than me but I've been in your situation a couple of times. Killing whatever the process is has never caused a problem for me.

Processes like that usually happen (for me anyway) when a program terminates badly (i.e it crashes).

If somethign goes wrong, restart your machine.

---

