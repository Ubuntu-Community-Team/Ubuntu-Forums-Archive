---
title: "CPU fan, ready for take-off!"
date: 2008-04-25
forum: Hardware
---

### Post by TjiffTjoff on 2008-04-25
Hi!

I've just installed the new Ubuntu 8.04LTS on my laptop(Asus F3F)
and I love it! It's only one small problem which tend to grow and
become a major frustration.

My CPU-fan doesn't seem to respond correctly. When I boot into
Ubuntu the fan starts to go berserk and I can't find out why!
Earlier I have tried Gutsy Gibbon with the same behavior.
The temperature is about the same as in XP when the fan is
inactive. Any ideas?

My specs are:

Asus F3F
intel Centrino Duo t5200
Intel 945gm
1024 mb RAM
100 gb HDD

---

### Post by ajmorris on 2008-04-25
hi there,
have you opened up your lappy to make sure the fan doesnt need re-seating? Also, lm_sensors can tell you if your fan is functioning properly.

AJ

---

### Post by Yoeri on 2008-04-25
Are you sure it is the CPU-Fan and not the video card fan?

Had the same issues with my ATI Mobility in an Asus A4K this link:
[http://natonelbronx.wordpress.com/my-linux-pcs/asusa4k-mtrr-solution/](http://natonelbronx.wordpress.com/my-linux-pcs/asusa4k-mtrr-solution/)
solved my problems.

What video card is installed in your laptop?

---

### Post by Jimmy9pints on 2008-04-25
I think I have this problem too!

Recently my computer goes for some pretty hardcore fan related whirring just after logging in. 

Also, my CD drive has been running like mad after logging in (I swear that's getting noisier by the day).

J

---

### Post by Ebuntor on 2008-04-26
I've got the same problem since I installed Hardy, the fan keeps running nonstop. As soon as the CPU temperature reaches 50°C it starts running, while in Gutsy it would start around 65°C. I can manually change the CPU frequency and make it stay below 50° but that's hardly a solution.

Have the fan settings changed since Hardy or could this be a bug?

---

### Post by y2kprawn on 2008-04-26
I have the same problem on my HP nx9420, sounds like a small aircraft all the time and I have no idea what is going on. Any input at all would be greatly appreciated.

---

### Post by Ebuntor on 2008-04-26
> **Jimmy9pints said:**
> 
Also, my CD drive has been running like mad after logging in (I swear that's getting noisier by the day).

Same problem here, although my drive isn't getting noisier it just doesn't stop running when I insert a disk, even when I'm not accessing the disk. This problem and the fan problem are getting really annoying.

---

### Post by Jingo on 2008-04-26
Does it scale the frequency ?

I have a Celeron M 540 here, which is running at 1,86GHz all the time.

Modprobing p4-clockmod gives FATAL: no supported device....

Did find a patch out there, but then I have to compile a new kernel! :(

---

### Post by sojusnik on 2008-04-27
> **Ebuntor said:**
> I've got the same problem since I installed Hardy, the fan keeps running nonstop. As soon as the CPU temperature reaches 50°C it starts running, while in Gutsy it would start around 65°C. I can manually change the CPU frequency and make it stay below 50° but that's hardly a solution.

Have the fan settings changed since Hardy or could this be a bug?

How can you change in hardy that your cpu fan shall start at 65° and not at 50° ?

---

### Post by Ebuntor on 2008-04-27
> **sojusnik said:**
> How can you change in hardy that your cpu fan shall start at 65° and not at 50° ?

Follow [this link.]("http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html") :)

---

### Post by acron1 on 2008-04-27
You should also check and make sure the CPU/GPU heatsink is clean and if not clean it.

---

### Post by Ebuntor on 2008-04-27
> **acron1 said:**
> You should also check and make sure the CPU/GPU heatsink is clean and if not clean it.

That sure isn't the case with my laptop, I got it three weeks ago. :)

---

### Post by sojusnik on 2008-04-27
> **Ebuntor said:**
> Follow [this link.]("http://www.ubuntugeek.com/howto-change-cpu-frequency-scaling-in-ubuntu.html") :)
In this link it's written about cpu scalling, not about cpu fan regulation. I don't want to change my cpu rate, but to adjust my fan so that it shall start at 65° to cool down, not at 50° as it is now.

---

### Post by Ebuntor on 2008-04-27
> **sojusnik said:**
> In this link it's written about cpu scalling, not about cpu fan regulation. I don't want to change my cpu rate, but to adjust my fan so that it shall start at 65° to cool down, not at 50° as it is now.

Oh sorry didn't read your post carefully enough. I know it's about CPU scaling, if you read my original post I said: " I can manually change the CPU frequency and make it stay below 50° but that's hardly a solution." 

I have no idea how you can control when the fan starts running otherwise this thread would have been solved. :)

---

### Post by mimetist on 2008-04-28
Hi, same problem here.

I've been reading about this in several forums and it seems to be something about the new kernel, could it be a temporary solution to go back to an old kernel?

Any idea about how to solve this issue?

---

### Post by mimetist on 2008-04-28
I think I've found the solution!! :)

Firs of all you have to read this thread:
[http://ubuntuforums.org/showthread.php?t=729406&highlight=hardy+heat](http://ubuntuforums.org/showthread.php?t=729406&highlight=hardy+heat)

Maybe your problem is related to the misconfiguration that is solved up on that thread. (remove powernowd and install cpufreq instead)

I tried that, but it didn't work for me... so I did enable CPU Scaling just like it is showed here:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features)

Using "ondemand" module has decrease the heat, but sometimes the fan begins to make a loud noise again... so here it's our temporary solution

Any other idea?

---

### Post by mimetist on 2008-04-28
Sorry, but it doesn't Work...

Right now I'm having the same problem even with the CPU Frequency Scaling... so it has to be something else...

---

### Post by TjiffTjoff on 2008-04-30
I seriously doubt that going back to the previous kernel would do the trick.
I tried Ubuntu 6.06, 7.10 and 8.04 on my laptop and the same problem occurs
in any version I've tested.

Would be intresting to know about your temperatures and what kind of CPU you
guys have. I'm also a bit confused since I monitor my temperature in two different ways; one of them is ACPI which gives a higher number and the 
other is through lm-sensors wich gives a lower temperature. Which one of 
these should I rely on?

Some of you might be rid of the fan-noise by configure your BIOS. My BIOS
is a very simple one with no option for temperatures or fans.

---

