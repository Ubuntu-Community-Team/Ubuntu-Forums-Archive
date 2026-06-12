---
title: "Acer Aspire 5315 Ubuntu 11.10"
date: 2011-10-22
forum: Hardware
---

### Post by Belf on 2011-10-22
Hello everyone
I installed the newest version of Ubuntu 11.10 in my Acer Aspire 5315 laptop.
As usual with other versions, the fan doesnt work properly, BUUUUUT
when i start it, it wont work, but if I suspend it and make it go again, the fan will start and not stop again.
When I use the command 
```
sensors
```
it gives me this:
```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +40.0°C  (crit = +100.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +82.0°C  (high = +100.0°C, crit = +100.0°C)
```
temp 1 wont change, but Core 0 will go up and up, and if i dont suspend and start again, it will power off
with the typicall click.
I've been thinking about a way to trick ubuntu into thinking i come from suspension when i am coming from poweroff.
Anyone has any working solution or a good idea?
Hoping to get some answers ;)

---

### Post by Belf on 2011-10-24
Today I just noticed that when the fan turns on, the temperature changes from the stable 40ºC to 80ºC in just a sec, and the fan starts spinning and stays that way
Is there any way to change that temp manually to trick the fan into spinning?

---

### Post by dougalkerr on 2011-10-24
This might not help in your own case but, I have a Dell laptop which has terrible overheating problems which Dell have not admitted to. I now have three power supplies because this is the only thing apart from a motherboard replacement under warranty that Dell has been able to help with.

Anyways, searching the hinternet lead me to a post where people were saying that the heatsink compound between the processor chip and the cooling components was drying out and causing overheat problems. Now I am not saying this is the problem you might be having but, it wouldn't be a bad thing to refresh the heatsink compound if you think you can do that. It will help with the temperature sensing if nothing else.

Apparently when Dell carry out service work, the heatsink compound is always changed as a matter of course.
I would be surprized if other manufacturers didn't do the same, for good reason.

---

### Post by Belf on 2011-10-24
I will definetly have a look at that, thanks :D
Now that i have started I would like to know if there is a software remedy like tricking the system.
Thanks for your reply dougalkerr :)
I'll write again as soon as I try your advice.

---

### Post by mörgæs on 2012-07-30
In case someone googles the thread: Ubuntu 12.04 runs well without overheating.

Hereby closing.

---

