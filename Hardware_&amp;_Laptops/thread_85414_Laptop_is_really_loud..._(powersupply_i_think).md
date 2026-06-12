---
title: "Laptop is really loud... (powersupply i think?)"
date: 2005-11-02
forum: Hardware &amp; Laptops
---

### Post by pear-i on 2005-11-02
hey there, i upgraded to breezy a month ago and its working quite beautifully except for this loud humming -- powersupply i presume thats really getting on my nerves (especially in lectures / library haha makes ppl look at me funny :p) 

but yah was wondering if there's a way to moderate or control the power supply fan? It used to be ok in Hoary... it'd be loud when CPU went to 100% (2.0ghz) and quiet down at 60% (1.2 ghz) so now its sorta really annoying :p

Oh yah -- specs for my laptop:
Dell C640 2.0/1.2Ghz Pentium M 512 mb 
scaling govenor is userspace
and cat /proc/cpuinfo is as follows:
```
 
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Mobile Intel(R) Pentium(R) 4 - M CPU 2.00GHz
stepping        : 7
cpu MHz         : 1196.208
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid
bogomips        : 2324.88

```

any help / ideas would be greatly appreciated!
Thanks!

---

### Post by Chuckaluphagus on 2005-11-03
The noise is coming from the fan for your notebook's processor, and while you have some options on reducing the fan noise, you have to be careful or you may end up cooking your processor.

The main cause of the problem here is that you have a Pentium 4-M, not a Pentium M; the difference in the name is small, the difference in the processors is more substantial.  The Pentium M processor line was designed for a reasonable balance of processor performance and power consumption, while the Pentium 4 line was designed for processor performance only at the cost of very high power consumption.  For processors, power consumption directly relates to heat, and your Pentium 4-M processor is putting out a lot of heat.  This is why the fan runs very fast at the full 2.0 GHz processor speed and makes an awful racket.  

The other side of this is that, in my experience at least, Dell notebooks have very loud, obnoxious fans that drive me up a wall.  They sound more like leafblowers than notebooks.  You appear to be in this sort of situation.

There is this Howto ([http://ubuntuforums.org/showthread.php?t=42737&highlight=fan+speed+control](http://ubuntuforums.org/showthread.php?t=42737&highlight=fan+speed+control)) on controlling fan speeds, although I've never tried it and it may not work with your notebook.  If it does work, it would allow you to lower the speed of your processor fan so that it would make less noise when the processor is running at full speed.  Even a fan speed reduction of 10% could make a significant difference in the noise it generates.

The very real danger here is that, if your processor overheats because the slower fan isn't dissipating heat fast enough, you could end up frying your notebook.  Pentium 4 processors run _very_ hot, so you'll want to be careful.  Your processor does contain a temperature sensor that will attempt to shutdown the processor (therefore crashing your notebook) before it gets cooked in the event of overheating, but this is obviously not an optimal solution.  In short, if you do try and change the fan speeds, be careful.

One last thing: I did a quick search on Google for "Dell c640 fan noise" and found this page ([http://comcap.free.fr/c640.html](http://comcap.free.fr/c640.html)) discussing running Debian 3.0 on your model of notebook.  In the section titled "Power management", it mentions that 

[INDENT] Suspend from the keyboard (Fn-Esc) works fine (including in X) but on resume, the BIOS thinks that the cpu temperature is 85 C and the fan spins out at maximum speed. Whatever you do, the noise will soon drive you crazy and you will have to reboot (which makes suspend not a very attractive option). This is a problem encountered by other users on other Dell (recent) models which is well described here (the same source also mention the keyboard repeat rate problem which I also encountered but this is a minor issue fixable with kbdrate or xset, also you may need to re-run the pcmcia scripts if you have pcmcia cards).

The Dell support site has a version A07 of the BIOS which makes the problem less frequent but does not completely solve it (still happens after very long suspends). The A08 which is the latest available BIOS upgrade from Dell does not improve on this [Minh Ha Duong, March 17 2003].

However, the problem IS SOLVED SIMPLY BY TYPING Fn-Z on resume (which makes the BIOS re-read the temperature). [/INDENT]

In light of this, if the fan starts to go nuts, try hitting Fn-Z in order to reset the sensor.  If the sensor is mistakenly reading a very high temperature, then the noise should return to normal.  If it really is running hot enough to justify the high fan speed, then it'll return to that high speed and your processor won't be in any danger.

Hope some of this helps.

---

### Post by pear-i on 2005-11-03
thanks for the quick reply
I'll look into the fan control thing in a bit,

As for the bios / sensor thing -- Ubuntu's own sensors are reporting that the CPU is about 40 C, which isn't too hot i suppose, yet like you said i'm flooded with that obnoxious blowing noise :p sounds like an acute vacuum cleaner ugh!
+i read about that problem with the bios sensor, and i don't think it really applies to me cause i'm using acpi right now -- and the fn to bios etc.. only work if i'm in apmd -- course if i use apmd it, ubuntu sensors go kind of kinky... 

kinda blargh :p

Just thought it was odd cause on the lowe CPU freq back on hoary it'd be silent... and nwo it sorta just goes nonstop :p

**edit:** i tried the how to didn't detect my sensors... :\ suppose they're not supported.. any other ideas?

---

