---
title: "how to diagnose hardware issues in kubuntu?"
date: 2023-11-19
forum: Hardware
---

### Post by alvere on 2023-11-19
Years ago my computer was working just fine but lately it freezes completely more often everyday, specially when i run demanding software like videogames. Don't know which part of my hardware is causing this freezes, i made a full memtest run and think that can discard memory but don't know if it is my motherboard, my graphic card or my CPU what is failing. What can i do in linux to know which  part of my hardware is failing?

---

### Post by Yellow Pasque on 2023-11-19
When was the last time you cleaned out the inside of the system?
It's a bit difficult to diagnose these things without spare parts.

---

### Post by ian-weisser on 2023-11-19
It's possible to have memory that works fine...but not enough of it

Start with the output of "free -h".
Once then the system is idle, preferably after a fresh boot is complete.
Then again when the system is sluggish or under stress.
This simple test will confirm whether you have enough RAM+Swap for your use.

---

### Post by alvere on 2023-11-20
> **ian-weisser said:**
> It's possible to have memory that works fine...but not enough of it I'm pretty sure it's not the ram, don't have spare parts to test but i could put my ram modules on a friend's computer and works just fine even stressing the system. 
Is there any software tool to diagnose which part is failing amongst CPU, motherboard and graphic card?

---

### Post by ian-weisser on 2023-11-20
A faulty motherboard or CPU, by definition, means that no software tool will return reliable results. Might not run at all.

Like riding your bicycle to town to replace the missing wheels.

---

### Post by SeijiSensei on 2023-11-20
How much memory do you have?

---

### Post by Yellow Pasque on 2023-11-20
Again, make sure your CPU heatsink (and all your other components) are free of dust and the fan(s) is working properly. While you have the case open, inspect the motherboard for swollen capacitors. Those are the first things I would do and look for if the problem was getting worse.

> **alvere said:**
> Is there any software tool to diagnose which part is failing amongst CPU, motherboard and graphic card?

There is no magic command to do that, and don't forget that your PSU may be failing too. Maybe looking at the journal will provide clues after a freeze and reboot.
```
sudo journalctl --boot=-1
```

Monitoring temps (and hopefully, voltages if your system supports that) is a good idea too.
```
sensors
```

And please respond to the people who ask you questions or ask for output of commands. You seem to be ignoring everyone.

---

