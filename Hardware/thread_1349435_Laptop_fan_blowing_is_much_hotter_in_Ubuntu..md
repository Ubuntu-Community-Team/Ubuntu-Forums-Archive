---
title: "Laptop fan blowing is much hotter in Ubuntu."
date: 2009-12-08
forum: Hardware
---

### Post by mahela007 on 2009-12-08
The air coming out of my laptops cooling grill seems to be much hotter when I use linux compared to when I use windows. I have no way of proving this because I don't have a CPU temperature monitoring utility in windows. In linux, the monitor says it's at 69 degrees C.
The air coming out feels much hotter when I keep my hand in front the the vents. Is that normal? My CPU is a Celeron M running at 1.5 GHz. I use windows XP and Ubuntu 9.10.

---

### Post by michael18 on 2009-12-08
ow...izit?

but mine is totally diff from u..

when i'm using win vista...the fan is so damn hot!!

then i change to win 7...its much better...

and i juz change to Ubuntu last sunday...the 1st time using LINUX...xD

much more better!!!

love it...love Ubuntu...haha

---

### Post by Johansen on 2009-12-08
Chances are linux isn't scaling the processor frequency down, that and Ubuntu idle processor usage on a non optimized install is at least 2-3 times higher than the same fresh install of WinXP.

---

### Post by mahela007 on 2009-12-08
Is that bad? What would it do to battery life?

---

### Post by Johansen on 2009-12-08
"In linux, the monitor says it's at 69 degrees C"

That sounds like the sensor is not configured properly, unless you have a thermocouple or a thermometer to measure it I don't believe it is that high.

Battery life is the ultimately the measuring rod to be used, how does it compare?

---

### Post by mahela007 on 2009-12-08
I should have a thermometer lying around somewhere. I'll post back. Meanwhile, is the lm-sensors library / program installed by default in ubuntu? I posted another thread about this, but since it's probably relevant here, I posted the question again.

---

### Post by mahela007 on 2009-12-08
Yes.. you were right. The temperature of the air comming out of the vents was 41 degrees C. But I still feel it's a bit on the hot side. Is there a way to check if the hard drive is continuously running? When I press my ear to the laptop, I hear  a small humming noise. I don't know if this is the fan or the hardrive (I feel stupid saying that. ;-) )

---

### Post by ProgramErgoSum on 2009-12-08
Type the top command and see what/how much is the highest.

In my case, whenever the air blowing from the vents heated up, I would see ntop running at almost 100 % CPU (in the output of top). When I kill the process for ntop, the CPU %age utilisation plummets and air blowing out is cooler.

---

### Post by mahela007 on 2009-12-08
What is ntop?

---

### Post by yossell on 2009-12-08
The programme powertop worked very well for me in making my computer running cooler and lengthening battery life. Without it, battery life was much less than under Vista. With it, a little longer.

[http://www.lesswatts.org/projects/powertop/](http://www.lesswatts.org/projects/powertop/)

---

### Post by mahela007 on 2009-12-08
> **Johansen said:**
> Chances are linux isn't scaling the processor frequency down, that and Ubuntu idle processor usage on a non optimized install is at least 2-3 times higher than the same fresh install of WinXP.
My laptop is a thinkpad R51e with a celeron CPU. I went and checked out the thinkpad wiki and it said linux doesn't support CPU scaling for my processor. (or more specifically, I wasn't listed with the processors that DO support scaling)
Is this a hardware issue or can I fix it?

---

### Post by zami on 2009-12-08
I apologize if this is overly simple or already thought of.

On my laptop,

Ubuntu 9.10 + Desktop Effects = burn your fingers hot
Ubutnu 9.10 + No desktop Effects = just fine
Vista = just fine
Vista + Hefty 3D Game = burn your fingers hot

I don't know about CPU scaling, but I know graphics cards run HOT.

Whatever the cause, I hope you get it figured out.  Good luck!

-zami

---

### Post by ProgramErgoSum on 2009-12-09
[ntop]("http://sourceforge.net/projects/ntop/")

---

### Post by mahela007 on 2009-12-09
thanks for the the help. I'll try turning the effects settings down.

---

