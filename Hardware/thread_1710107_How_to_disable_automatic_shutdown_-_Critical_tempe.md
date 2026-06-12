---
title: "How to disable automatic shutdown - Critical temperature reached (97 C)"
date: 2011-03-19
forum: Hardware
---

### Post by restofactor on 2011-03-19
Hi there,

I have a Dell Inspiron 15R laptop with a i7 processor and 8GB of RAM. I am running Ubuntu 10.10 and I have seen various trouble shooting guides for acpi, however I cant find clear information on how to disable the automatic shutdown when the critical temperature has been reached or how to increase it.

I am trying to convert a movie with Handbrake and it utilises processing power that takes the temperature up to the maximum acpi value of 97 degrees then the system shuts down without warning.

This is HIGHLY annoying and it caused me to lose work. I would at least expect a warning and some kind of human intervention option to prevent this from happening.

Any help/suggestions?

Thanks

---

### Post by PatrickVogeli on 2011-03-19
I don't think there's a way to disable this.. it's the bios taking care. Maybe you could get the acpi dsdt, decompile it, disable that, then recompile the dsdt and, last thing, compile a custom kernel with the dsdt in it.. but, honestly, I don't think anyone would like to do that.

Something is wrong with your computer. No matter what you do, it shouldn't reach critical temparutes as yours. If it does, I think there are basically four options: 
1.- because the software (os, drivers) is not managing the fans as it should
2.- because the laptop's cooling system is poorly designed and can't cool that processor
3.- because you upgraded the processor to something too hot.. which the cooling system wasn't designed to take care of
4.- because it's broken (bad fan, fan temperature sensors, etc)

Since your machine is quite new, I'd say yours is case 1. Disabling the acpi stuff isn't a good idea: what will happen if, after disabling it, you leave and forget about it?

---

### Post by sammiev on 2011-03-19
Never disable automatic shut down. It shutting down because your running too hot. Best to repair your problem than burn out your computer. GL :)

---

### Post by restofactor on 2011-03-20
I appreciate the feedback, however you guys are not answering my question. If I go back to my original question I asked how do I disable this feature.

After a lot of reading I did this and then I rebooted. I ran the temperature up again and it shut down so I am not sure whether this is working;

```
Edit => /etc/default/grub

Edit => GRUB_CMDLINE_LINUX_DEFAULT=

Add => GRUB_CMDLINE_LINUX_DEFAULT="quiet splash thermal.nocrt=1"

Update GRUB => sudo update-grub

View settings, should be disabled => cat /proc/acpi/thermal_zone/THM/trip_points

View temperature => acpi -V or sensors
```I then found and did as per the following write up on the issue and it seem to have worked => [http://burnz.wordpress.com/2009/02/23/ubuntu-auto-shutdown-due-to-high-cpu-temperature/](http://burnz.wordpress.com/2009/02/23/ubuntu-auto-shutdown-due-to-high-cpu-temperature/)

---

### Post by grandsatrap on 2011-03-23
> I appreciate the feedback, however you guys are not answering my question. If I go back to my original question I asked how do I disable this feature.

I think that what people are saying is that you have another much more serious problem with your computer that you are ignoring. My laptop [Dell Inspiron 1501] NEVER gets hotter than 62 degrees. If yours is doing this then (i) check the fans - are they working? are they clogged with cat hair and dust? (ii) get an external laptop cooler - the fan thingy that goes under your laptop to cool it more.
Run Powertop (and maybe htop) and see if there is some process that is using 100% CPU all the time, or doing something to raise the temperature. 
If you can't find a solution to these high temperatures, then take it in to get a technician to look at it. 
Disabling the autoshutdown feature is just plain dumb -- you might as well just stick the laptop in an oven.  Of course, if you are living in the desert, than maybe there is another reason why it is getting so hot. I don't think laptops would work in desert heat.

---

### Post by tgm4883 on 2011-03-23
> **restofactor said:**
> I appreciate the feedback, however you guys are not answering my question. If I go back to my original question I asked how do I disable this feature.

On the contrary, you aren't reading the answers.

Lets clarify a few things. Most people consider 70C hot for a CPU. Getting to 97C is likely above the maximum recommended operating temperature. The machine is shutting itself down to protect the CPU from melting/burning. This would be far more annoying/expensive than just having the computer shut down.

So in conclusion, it's the BIOS, not Ubuntu that is shutting the system down. You may be able to disable the safety measures in the BIOS, but no, I won't help you ruin your computer.

---

### Post by sammiev on 2011-03-23
To give an answer that may kill your computer is just NOT right. Read the post and get your fan running is the answer. GL :)

---

### Post by restofactor on 2011-03-24
> **tgm4883 said:**
> On the contrary, you aren't reading the answers.

Lets clarify a few things. Most people consider 70C hot for a CPU. Getting to 97C is likely above the maximum recommended operating temperature. The machine is shutting itself down to protect the CPU from melting/burning. This would be far more annoying/expensive than just having the computer shut down.

So in conclusion, it's the BIOS, not Ubuntu that is shutting the system down. You may be able to disable the safety measures in the BIOS, but no, I won't help you ruin your computer.

Dude, Cheryl Cole is hot, anything else is pale in contrast!

What annoyed the fQ@#%$@# out of me was watching my laptop shut down 10mins every time into an AcidRIP session without any warning - causing me to lose all my work open at the time. I'd much rather lose a processor than go through this kind of pain again. It is only when I use AcidRIP that the temp goes up.

This is my current temp;

```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +66.5°C  (crit = +97.0°C)
```       

On my laptop it is not controlled via the BIOS, as noted in my previous post the changes in Ubuntu fixed the automatic shut down.

---

### Post by tgm4883 on 2011-03-24
> **restofactor said:**
> Dude, Cheryl Cole is hot, anything else is pale in contrast!

What annoyed the fQ@#%$@# out of me was watching my laptop shut down 10mins every time into an AcidRIP session without any warning - causing me to lose all my work open at the time. I'd much rather lose a processor than go through this kind of pain again. It is only when I use AcidRIP that the temp goes up.

This is my current temp;

```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +66.5°C  (crit = +97.0°C)
```       

On my laptop it is not controlled via the BIOS, as noted in my previous post the changes in Ubuntu fixed the automatic shut down.

If you lose your processor, you lose your unsaved work (and potentially your saved work too). It doesn't magically save stuff just because you disable the safety measures.

Again, I'm not going to help you disable safetly measures, sorry. Laptops don't generally get that hot doing normal activity, heck even when encoding they don't get that hot. I'd check your airflow.

---

### Post by restofactor on 2011-03-25
> **tgm4883 said:**
> If you lose your processor, you lose your unsaved work (and potentially your saved work too). It doesn't magically save stuff just because you disable the safety measures.

Again, I'm not going to help you disable safetly measures, sorry. Laptops don't generally get that hot doing normal activity, heck even when encoding they don't get that hot. I'd check your airflow.

It is okay, I successfully disabled it and posted my solution for everyone else annoyed by this.

It is fine to warn people, but give people the freedom to do what they want. 

My laptop is under warranty, if it gets fried I will take it in and get a new one :) I ran it for more than an hour at 97 without any issues. Still strong as mother Russia! :guitar:

---

### Post by mobius357 on 2011-03-25
Except you've certainly voided your warranty.

---

### Post by restofactor on 2011-03-25
I am confused. In what way did I possibly void my warranty ? I made no changes to the BIOS or altered the hardware.

How would they possible know that a piece of software fried their processor?

---

### Post by mhakali on 2011-08-06
> **restofactor said:**
> It is okay, I successfully disabled it and posted my solution for everyone else annoyed by this.

It is fine to warn people, but give people the freedom to do what they want. 

My laptop is under warranty, if it gets fried I will take it in and get a new one :) I ran it for more than an hour at 97 without any issues. Still strong as mother Russia! :guitar:

Thank you for the fix!

As for the others in this thread, it may be noted that I run in to this problem and it is due to a BUG in the thermal sensor readings. A bug which causes my work to disappear randomly.

I hate it.

It would be awesome if it was working. And disabling it on hardware that it was not working on..

---

### Post by yamagami on 2011-10-26
I had the same problem for a very long time now. In my case I also had a motherboard replaced on my Thinkpad T61p which was not exactly the one I had before, resulting in no way to get into the Bios and a "Thermal Sensor" warning on startup. I was ready to take the risk and follow your fix here, 

BUT,

Before I did, I applied some thermal paste on my processor last night. 
Previously ```
acpi -t
``` showed me at around 70 degrees going quickly up to 100 after minutes of use. Now I'm around the 50 degrees going up to 70 occasionally. Its only been a day, but after having random shutdowns many times a day, I call this a success so far.

I suggest you try thermal paste. You'll need to open it up, remove the heatsync etc., and you WILL void your warranty. 
Or, if you are under warranty still, get it to the manufacturer and ask them to apply it.

---

### Post by diasf on 2011-10-26
Just 2 cents of info there...

ok, 70C won't burn your processor right away. But it will damage it a little, in a cumulative fashion.
(I searched that a lot, my laptop - HP touchsmart tx2 1050- has an inerent, by design, stupid heating problem and can reach 100C idle/booting).

---

### Post by mifritscher on 2012-11-04
Is there any news? This tweak doesn't work anymore it seems :-(

I've a Thinkpad with a defect sensor I think - I don't believe that the temperature can suddenly raise from 50 to 127 C in notime. The other sensors continue to deliver normal values as well ( the Thinkpads have many sensors in nearly every edge)

Edit:
On [http://www.mjmwired.net/kernel/Documentation/thermal/sysfs-api.txt](http://www.mjmwired.net/kernel/Documentation/thermal/sysfs-api.txt) are more infos - but on a Ubuntu 12.04 a echo disabled>/sys/class/thermal/thermal_zone0/mode fails with "write error: argument is invalid" ...

Edit2:
echo -n "disabled" >/sys/class/thermal/thermal_zone0/mode works :-)

---

