---
title: "Overclocking my E7200 Intel."
date: 2008-05-29
forum: Hardware
---

### Post by chris062689 on 2008-05-29
I plan on overclocking my E7200 Intel chip to 4Ghz.
It's possible, through the BIOS.
But I also want to be able to smack it around on-the-fly inside of Ubuntu.  :lolflag:
The only time I think I'll need the 4Ghz is when using pcsx2 (a playstation 2 emulator)

I realize there is a CPU Mhz Monitor for GNOME-panel, that allows you to change clock speeds, is there a way I can configure this to pump my Intel Chip to the following settings? (Stock Speed 2.55 (I think), 3Ghz, 3.5Ghz, 3.8Ghz, 4Ghz)


Also, intel-overclocking.net suggested:
> You need to download CPU-Z to check settings from within windows. The main CPU tab and memory tab are the important ones. Also use RealTemp to monitor your CPU's temp at idle and load. To put a load and stress test your OC, run Prime 95. All of these programs can be found in the downloads section.
([http://www.overclock.net/intel-cpus/337667-overclocking-e7200.html](http://www.overclock.net/intel-cpus/337667-overclocking-e7200.html))

Of course these programs are not for Ubuntu, so are they any alternatives that I can use that will give me the same thing?

Has anyone else overclocked a E7200 to 4Ghz?  Can someone help me do it?  :(
Thank you!

---

### Post by Joeb454 on 2008-05-29
Check [http://appdb.winehq.org](http://appdb.winehq.org) and see if CPU-Z is in there :)

And I don't think overclocking is a beginner issue ;) Don't worry, somebody will move it

---

### Post by chris062689 on 2008-05-29
I can't imagine it working properly in a WINE environment.
Is there a Linux alternative I can use?

---

### Post by Joeb454 on 2008-05-29
Not sure off the top of my head, I'll pass it on to some others that may know :)

---

### Post by syko21 on 2008-05-30
```
sudo apt-get install cpufreq-utils
```

Then at the terminal type in cpufreq-info. You'll get a fair amount of CPU related information

---

### Post by hotweiss on 2008-05-30
I'm overclocking an E6850 to 3.8 GHz with out any problems. It has now ran without any crashes for 5 months. Intel CPU's are actually rock solid, so don't worry about lowering frequencies - have it maxed out always. Overclocking these days is a little tricky, here are my tips:

-don't overclock memory
-set memory ratio to 2.0
-set PCI-E frequency to 100
-you will need to overclock your Northbridge & FSB
-disable all of the CPU's energy scaling options, etc...
-disable the turbo modes that some motherboards have
-don't go past 1.5 Volts on the CPU

Follow those steps, increase the speed to maximum incrementally. I got a Thermal right heat sink, just to keep the sound levels down. I also overclocked my Nvidia 8800 GT GPU to 700 MHz using Nibitor.

---

### Post by Brian96 on 2008-05-30
Not trying to hi-jack this thread, but I am running a Dell Inspiron 530 (desktop) with the Core 2 Quad Q6600 with the infamous "tape mod." When I boot into Vista and run CPU-Z, the FSB is indeed up and it runs at 2900 MHz when maxed out (though it scales down to 1900 the rest of the time). 

However, the emifreq applet in Ubuntu shows only 2.4 GHz max (and CPU-Z in my virtual machine's XP also shows on 2.4 GHz).

Am I really not getting the extra juice in Ubuntu? Why might I not be?

---

### Post by Brian96 on 2008-06-07
> **Joeb454 said:**
> Check [http://appdb.winehq.org](http://appdb.winehq.org) and see if CPU-Z is in there :)

And I don't think overclocking is a beginner issue ;) Don't worry, somebody will move it

For the record, CPU-Z installs and loads in WINE, but it doesn't detect anything. You just get empty fields for everything.

---

### Post by mael on 2009-05-24
> **Brian96 said:**
> Not trying to hi-jack this thread, but I am running a Dell Inspiron 530 (desktop) with the Core 2 Quad Q6600 with the infamous "tape mod." When I boot into Vista and run CPU-Z, the FSB is indeed up and it runs at 2900 MHz when maxed out (though it scales down to 1900 the rest of the time). 

However, the emifreq applet in Ubuntu shows only 2.4 GHz max (and CPU-Z in my virtual machine's XP also shows on 2.4 GHz).

Am I really not getting the extra juice in Ubuntu? Why might I not be?

i have the same problem. does anybody have a solution?

---

### Post by mael on 2009-05-30
> **mael said:**
> i have the same problem. does anybody have a solution?

disabling speedstep "solved" the problem

---

### Post by DanglingPointer on 2009-06-01
I have CPU-Z running under the latest WINE in windowsME compatibility mode.  It loads most fields.  However:
voltage
Multiplier
Bus Speed
Rated FSB
Package
Brand ID
Do not show.

See attached jpg...

---

