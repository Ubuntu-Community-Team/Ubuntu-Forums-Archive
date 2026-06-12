---
title: "Reached critical tempreture"
date: 2006-05-17
forum: Hardware &amp; Laptops
---

### Post by Michiba on 2006-05-17
Hi all,

Here goes......

I have a machine which occasionally does not boot up. It gets to the loading Kernel bit, reports it has reached critical tempreture displays some numbers and a temp usually 167 degrees, says the system is shutting down, which it does. 

If it does boot up all the way it runs all day no problems. If it decides it's a critical tempreture kind of day I can turn it off and on all I like and it still won't go past loading the kernel. I can however boot into CMOS.

Now I figured "Reached Critical Tempreture" must be the CPU. So I swapped CPU's with a stable machine. The stable machine remained stable and the "Critical Tempreture" mahine remained critical. So not the CPU.

Now heres an observation, If I shut the machine down and leave it plugged in and switched on at the wall it won't start next morning. If I turn it off at the wall it will boot normally. This may be coincedence and I will test it over the next couple of days.

Is the machine possesed by evil spirits ?

Does any one have any ideas?

Thanks
Michiba

---

### Post by blip on 2006-05-18
That's definitely a strange one.  Only thought I had is when you do get it to boot up, does the CPU temp remain high?  In other words, if you check the temp after boot-up (using lm-sensors say) does it consistently show a high temperature or does it decline after boot up?  Does the temperature vary?  Furthermore, what temperature shows up in your bios?

It sounds to me like there is something screwed up in your sensor settings which is producing a fake temp...  If so you could always just disable temperature sensing. (I assume it is being logged by lm-sensors?  But I'm a bit of newbie myself so I may be missing something.)

Either that or you need to replace your heatsink big time! lol :)

---

### Post by Michiba on 2006-05-19
Hey blip,

When it's boot up time everything is normal. You know how I said if i shut down and leave it swithed on at the wall it wont start and if i switch it off at the wall it will. Well its proving very consistant.

The gods of electricity are simply teaching me good habits. 

I think this is just one of those Ripleys believe or not things. 

I'll shut down now (and switch off at the wall).

Michiba

---

### Post by tkjacobsen on 2006-05-19
I also had a problem like this. When the computer went back from standby, it just shut down. The syslog's last output was "reached critical temp 112C, shutting down). As of my knowlage, my cpu max temp is 75C, so it must be a kernel or sensor problem.. Though when i updated my kernel, the problem disappered.. 

Are you running the kernel for the corretc arct (386 or 686 etc,)

---

