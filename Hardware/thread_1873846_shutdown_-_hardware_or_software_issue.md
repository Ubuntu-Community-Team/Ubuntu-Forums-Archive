---
title: "shutdown - hardware or software issue?"
date: 2011-11-02
forum: Hardware
---

### Post by rebeltaz on 2011-11-02
I have an eMachines e520 laptop runing Ubuntu 10.04 that I have had for several years. I've never had any real problems with this until recently. Twice, while working with video files, my laptop has stopped mid-job and shutdown. Not a graceful shutdown, but a somebody-removed-the-power type shutdown. 

One time was while using the program k9copy to extract the video from a DVD. The second time was while using Avidemux to convert a video file from one format to another. I have used both programs in the past with no trouble.

I thought it was a heat issue, so I installed the Computer Temperature Monitor app and my system runs at a consistent 79 degrees Celsius. I don;t know if that is too hot not, but I do know that it doesn't raise above that when it shuts down. 

I also ran memtest86 for a complete day with the system ever finding any errors. 

Normal usage of the computer has never resulted in a shutdown. It's only when I attempt to use those programs - and not always then, either. Are there any issues with either Ubuntu or these programs that could cause this or does it sound like a hardware issue? I'm afraid it sounds hardware related and, as it is extremely intermittent, difficult to diagnose.

---

### Post by Redblade20XX on 2011-11-02
Hmm... seems like a heat problem. 80 degrees for a desktop? :confused: 

Can you install this package for sensors?
```
sudo apt-get install acpi
sudo apt-get install lm-sensors
```

And then run and post the outputs?
```
acpi -V
sensors
```

Also check if the vents to the computer are clogged and if you can open it, see if you cpu fan isn't clogged also?

- Red

---

### Post by rebeltaz on 2011-11-02
Actually, this is a laptop...

I already have those packages installed. Here are the results:

```

acpitz-virtual-0
Adapter: Virtual device
temp1:       +79.0°C  (crit = +110.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +77.0°C  (high = +100.0°C, crit = +100.0°C)  

```

You know... in all my years of computer repair, I have never really paid attention to what temperature the CPUs actually run at. I guess 75 degrees Celsius sitting at an idle is too hot. 

I took the laptop apart and did indeed find that the cooling fins were totally blocked by dust. After blowing that out, I went ahead and replaced the heatsink compound on the CPU with Arctic Silver since I was already in there and had some on hand. 

After I put it back together, I was amazed to see that the temperature never goes above 35 or 40 degrees just sitting there and when I stressed it by re-encoding a video file (which would have shut it down before), it never went above 50 degrees! 

Needless to say, I am one happy camper now!

---

