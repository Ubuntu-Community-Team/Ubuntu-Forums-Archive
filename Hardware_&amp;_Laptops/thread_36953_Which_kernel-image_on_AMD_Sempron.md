---
title: "Which kernel-image on AMD Sempron?"
date: 2005-05-25
forum: Hardware &amp; Laptops
---

### Post by saltydog on 2005-05-25
I am running Hoary on a server with AMD Sempron 2400 CPU, and I have always used the 386 kernel image. A couple of days ago I have received un update of kernel 2-6-10-5-386, and since then I have the second fan always running.... Maybe something wrong?
Which kernel-image should I install on AMD Sempron?

---

### Post by jasmuz on 2005-05-25
[QUOTE=saltydog]I am running Hoary on a server with AMD Sempron 2400 CPU, and I have always used the 386 kernel image. A couple of days ago I have received un update of kernel 2-6-10-5-386, and since then I have the second fan always running.... Maybe something wrong?
Which kernel-image should I install on AMD Sempron?[/QUOTE]
 Hello there..
My Processor is also a AMD Semprom 2400+, and i also have the 386 kernel.
But you should really have the latest kernel, and at the end it must say "K7". Those are optimized  for AMD.

Try to get it anyways, but i recomend you verify the status of your fans and the heatsink in the processor.

---

### Post by saltydog on 2005-05-25
[QUOTE=jasmuz]Hello there..
My Processor is also a AMD Semprom 2400+, and i also have the 386 kernel.
But you should really have the latest kernel, and at the end it must say "K7". Those are optimized  for AMD.

Try to get it anyways, but i recomend you verify the status of your fans and the heatsink in the processor.[/QUOTE]


There is something wrong in your reply. I don't understand... You say you have a 386 kernel, but it should have K7 at the end... Available kernels are:

linux-image-2-6-10-5-k7
linux-image-2-6-10-5-386
linux-image-2-6-10-5-686

..As you can see you cannot have the "386" with "k7" at the end. Are you meaning I should change kernel from 386 to K7?

---

### Post by Wombley on 2005-05-25
[QUOTE=saltydog]There is something wrong in your reply. I don't understand... You say you have a 386 kernel, but it should have K7 at the end... Available kernels are:

linux-image-2-6-10-5-k7
linux-image-2-6-10-5-386
linux-image-2-6-10-5-686

..As you can see you cannot have the "386" with "k7" at the end. Are you meaning I should change kernel from 386 to K7?[/QUOTE]

386 will work, it just won't use all of the features of the processor. K7 is probably what you want for best performance, as it is optimised for Athlon and Duron processors (and Semprons are essentially Athlons). You probably don't want to use the linux-image package directly though - it won't install modules - go for the linux-k7 package and it will install everything for you. Not sure if it'll do anything about the fan though - think that may be unrelated.

---

### Post by saltydog on 2005-05-26
Ok Kernel -k7 got installed. Maybe some enhancement for the CPU, but still this problemn of the fan... After few minutes of idle it starts and never stop.
And this happens since last kernel update...

---

### Post by saltydog on 2005-05-28
I am still struggling with the continuous fan problem.
When I give this command:

acpi -t

I always have a temperature reading between 45 and 49 degrees Celsius. Is it normal to have both fans running at this temp? Is there any Sempron user who can give me feedback on his temperature, please?

I am suspecting it could be an ACPI problem..Looking how to configure fan start in ACPI..

---

### Post by Spleenie on 2005-05-29
I am also running a Sepmtron 2400 and my CPU is generally between 36-42 degrees.

- Spleenie

---

### Post by saltydog on 2005-05-29
[QUOTE=Spleenie]I am also running a Sepmtron 2400 and my CPU is generally between 36-42 degrees.

- Spleenie[/QUOTE]

As my is ALWAYS over 46 degrees, there should be something not. working. Have you got powernowd working? On my Sempron it doesn't detect correctly CPU...

---

### Post by Spleenie on 2005-06-06
[QUOTE=saltydog]As my is ALWAYS over 46 degrees, there should be something not. working. Have you got powernowd working? On my Sempron it doesn't detect correctly CPU...[/QUOTE]
 I am not running the powernowd on my system

I am running the 2.6.10-5-k7 Kernel

Of late however I have been noticing the temp running a little high and always hear the fan going, so perhaps I wasn't exercising acute observation at the time, or it has started recently, although never higher than 40C when idling.

Maybe I will flick from one kernel to the other and see whether I notice a significant difference, and post back

As for correctly detecting CPU, if it reports the CPU as a 1500, I believe that is because thats what it is, but AMD claim that is equivilent to a 2400 Intel (orsomething)

- Spleenie

---

### Post by saltydog on 2005-06-06
No changes in temperature between the 2 kernels, so I suggest you to leave the k7 on.
Powernowd's author told me that desktop's AMD (Athlon or Sempron - K7) don't work with powernowd.

I have installed athcool, and the temperature has dropped from 45 to 40 degrees. It is a matter of un-latching the CPU from the bus when it is idling.

---

