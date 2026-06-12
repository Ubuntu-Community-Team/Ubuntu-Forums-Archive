---
title: "Thermal Sensor issue in Asus Eee PC X101CH"
date: 2018-05-06
forum: Hardware
---

### Post by stlu on 2018-05-06
Hi

I have an Asus Eee PC X101CH.  I have used it for about 2-3 years now and the main application usage was Skype.  It was idle most of the time and I never experienced problems as I am experiencing now.

The difference is that Skype for Linux was sabotaged by a large shady corporation and since then I haven't had a use for this netbook.  This week, I re-purposed it to do another job, more CPU intensive, and now the netbook has started to shut off randomly.

Here is the error message from /var/log/syslog that the kernel provides before shutting down:

```
kernel: [ 1340.226327] thermal thermal_zone0: critical temperature reached(255 C),shutting down

```

And from running the [FONT=courier new]sensors[/FONT] command, I see there is a virtual device called "temp1" that has 255 C as a supposed critical temperature:

```
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +83.0°C  (crit = +255.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +80.0°C  (crit = +100.0°C)
Core 1:       +81.0°C  (crit = +100.0°C)

asus-isa-0000
Adapter: ISA adapter
cpu_fan:        0 RPM


```

I'm not sure what to believe, because the values seem awfully high.  One thing is correct though - the CPU fan is 0 rpm because this netbook does not have a fan.  The palm rest has a sticker that says "0dB - Quiet fanless design".

I have applied the direction given in [https://ubuntuforums.org/showthread.php?t=1543868](https://ubuntuforums.org/showthread.php?t=1543868)  and it works.  (NOTE; anyone reading this who is trying to solve their own issue, **disabling thermal shutdown can destroy your computer!**  You've been warned.)  But it worries me, for with the warning I have given users and the lack of fans, I have stopped the kernel from reacting to this strange "temp1" device, but that means if the CPU temperatures go into a dangerous range, they won't be protected with a shutdown :(


I have a suspicion that heat is related to my netbook's weird temp1 value of 255.  Obviously 255 is not a temperature, but maybe it is supposed to be a message?  Like, at a certain point, the real temperature value gets too high, so this "temp1" thing is trying to signal to the OS "Hey, just FYI we're going to slow down a bit, it's getting too hot in here"  but the kernel interprets it as a critical thermal event and shuts down when it doesn't have to.  I also have been monitoring the output of the [FONT=courier new]sensors[/FONT] command every 4 seconds, and the range doesn't ever go above 80-85, and it never shows as 255, so it looks like it jumps quickly to 255 then back down to the lower range.  This makes me believe even more strongly that it is indeed a message/flag/signal of some sort.

So I have 2 choices.  I continue to run the system with the thermal safety feature disabled, with the risk of an actual thermal event killing it, or I hope the Linux or lm_sensors developers can figure out what this thing is and release a patch against this model netbook.

Should I feel safe that this is just an erroneous interpretation of sensor information, or should I avoid the high-load work and pick a lighter job for my netbook?  I mean, the netbook is 32-bit only and has 1GB of RAM, so it won't ruin my day if it does get burnt.  If I do get confirmation that this thermal event is actually a heat problem, then I'd rather re-purpose it again to some job that uses little CPU, such as a network file storage device.

---

### Post by him610 on 2018-05-06
stlu,

Your temps do seem to be a little high. In fact, they are way too high. I have a similar, but older (bios 2008) Acer netbook - mine has a fan in it though. The CPU in your netbook depends on a free flow of air through the vents in the casing to keep it from overheating. When it does overheat, it will shut down. Sometimes the air vents get clogged with lint, hair, crud, and other foreign material. You can try to vacuum it out, or if you have some mechanical aptitude, you could disassemble your netbook to give it a through cleaning.
This is the result my running sensors after operating about 30 minutes...
```
 sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +27.0°C  (crit = +90.0°C)

acerhdf-virtual-0
Adapter: Virtual device
temp1:        +46.0°C  (crit = +89.0°C)

```

You can find out more about *sensors* from the command line, ```
man sensors
```

---

