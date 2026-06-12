---
title: "Laptop overheating"
date: 2008-05-27
forum: Hardware
---

### Post by Sarah L on 2008-05-27
Hi guys,

In the last couple of days I've noticed that my laptop is reaching very high temperatures. I've felt around the case and found out that it's not the CPU that's heating up - it maintains a constant 60 degrees according to ACPI - but rather it's the memory chips and wireless card that are scalding hot.

There doesn't seem to be any built-in sensors for those components so I can't tell exactly how hot it is, but I've felt my CPU region when ACPI said it was 86 degrees, and that felt cool compared to how hot the memory and wireless card are now.

I've tried propping up my laptop for better air flow and cleaning out the case, but none of this has helped. The only thing that I can think of is that I burnt out a resistor somewhere and now excessive amounts of current is flowing through the computer - in fact, I can plug in a USB network adapter or a flash drive and it will begin to heat up to very high temperatures.

Does anyone have an explanation for this problem and a solution?

Thanks,
Sarah

---

### Post by powderhound99 on 2008-05-27
well you did better than me by cleaning it out first..... do you have lm-sensors installed  [http://ubuntuforums.org/showthread.php?t=2780]("http://ubuntuforums.org/showthread.php?t=2780")

---

### Post by jrusso2 on 2008-05-27
> **Sarah L said:**
> Hi guys,

In the last couple of days I've noticed that my laptop is reaching very high temperatures. I've felt around the case and found out that it's not the CPU that's heating up - it maintains a constant 60 degrees according to ACPI - but rather it's the memory chips and wireless card that are scalding hot.

There doesn't seem to be any built-in sensors for those components so I can't tell exactly how hot it is, but I've felt my CPU region when ACPI said it was 86 degrees, and that felt cool compared to how hot the memory and wireless card are now.

I've tried propping up my laptop for better air flow and cleaning out the case, but none of this has helped. The only thing that I can think of is that I burnt out a resistor somewhere and now excessive amounts of current is flowing through the computer - in fact, I can plug in a USB network adapter or a flash drive and it will begin to heat up to very high temperatures.

Does anyone have an explanation for this problem and a solution?

Thanks,
Sarah

I think thats very unusual for those parts to be running so hot.

Usually the CPU, GPU and the Hard Drives run hot in Laptops.

---

### Post by Sarah L on 2008-05-27
Yes, I've already installed and configured lm-sensors. Unfortunately it only seems to give me a CPU temperature reading - I don't think my laptop has temperature probes in any of the other parts.

Any suggestions in how to fix this issue? I'm already trying to cool the laptop down externally, but if there's an internal cause to be found it'd be great if I could fix the root of the problem.

Thanks for the support,
Sarah

---

### Post by powderhound99 on 2008-05-28
What types of changes have been made? New install? Upgrade? what version are you using? Any new software or hacks? Are you running Compiz? Don't really have much advice, it just might help if there was something specific you could trace back to. If you have done and update recently try jumping back a kernel. This is all pretty basic I know but have you missed something in your frustration? (Thats usually my problem)

Sorry not much else to say maybe try the Gentoo forums. Or you could try running another live CD and finding out if it's an Ubuntu specific issue.

---

### Post by krlhc8 on 2008-05-29
I was having similar issues with my laptop until I used an undervolting technique found in this thread: [http://ubuntuforums.org/showthread.php?t=786402](http://ubuntuforums.org/showthread.php?t=786402)

---

### Post by cdtech on 2008-05-29
Do you see anything using excessive amounts of cup usage in top?

If not, try going to “system > preferences > sessions” and uncheck “Tracker”, see if it stops.

Hope this helps...:popcorn:

---

### Post by paloberjot101 on 2008-12-08
i'm goin through the exact same thing. the area where my wireless card and memory are is scalding hot. i have been searching around everywhere online tryin to find out how to solve the problems. no one really has a solution. i tried checking the temp on my laptop and i have no sensors, it seems, for the system to give me feedback. my fan doesn't come on as often as it should as does windows. it's a toshiba laptop. the infamous satellite series m35x-s149

i don't know where to start and what to do. i'm a new linux user and just wiped out my windows for this os. so any posts on where i should start would be useful.

---

### Post by Gausian on 2008-12-08
My lappy ran a little warm using 8.04, but is much cooler now using 8.10.  Which version are you running?

Also have you upgraded your mobo bios?

---

