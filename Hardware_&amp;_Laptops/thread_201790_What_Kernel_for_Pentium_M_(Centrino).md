---
title: "What Kernel for Pentium M (Centrino)?"
date: 2006-06-22
forum: Hardware &amp; Laptops
---

### Post by elwood_j_blues on 2006-06-22
Hi there,

I run Dapper on a Toshiba M30X Centrino laptop. 

I recently realized that the default kernel installed by Ubuntu is a regular 386 kernel.

Now I was wondering which kernel would be a better idea to install on a Pentium M system? It is obviously a 686 system. Is it a good idea to replace the kernel by the version optimized for 686, then?

Thanks!

---

### Post by tribaal on 2006-06-22
Well I own a Dell Inspiron 9300 (Centrino too), and I haven't really figured out which one works best either. A few words on my experiences tough:

The i686 seems faster somehow, like in "more snappy", but seems to make xorg user about 10% of my CPU all the time (even when idle). This of course sucks on power, so the batteries won't last as long.

On the other side, the 386 feels a little less optimised, but really helps me save on battery and heat output. 

I've used the 686 for a while, but I'm back with the 386 now. I might be wrong, but this really feels like it's the best deal for me.

- trib'

---

### Post by yopnono on 2006-06-22
As stated above the 686 uses more CPU on my M 1.6 Dell D610, but I added this to the rc.local and it use not more than 386

echo 2 > /sys/module/processor/parameters/max_cstate

You have 4 levels. Some need to use level 1 others 3 etc,etc.
This prevent the cpu to use all the levels of power state.
[http://www.thinkwiki.org/wiki/Talk:Problem_with_high_pitch_noises](http://www.thinkwiki.org/wiki/Talk:Problem_with_high_pitch_noises)

---

### Post by elwood_j_blues on 2006-06-22
Restricting the CPU states is a very good idea.

I wonder if we can put that into an ACPI script so that it only applies when the computer is on battery? Obviously, I want it to be fast again when I connect the power supply.

P.S.: Thanks for your answers, the battery question was in fact the reason why I asked this here.

---

### Post by yopnono on 2006-06-22
You will not lose any speed on this. It's only stops the CPU to use all powerstate levels.
IE: If you set it to L2 it will only use L1-L2. It's a (bug? or something) that make the CPU use a lot more on idle on some machines. And if the CPU is in a like "work" state it will, i guess use more power.

---

### Post by elwood_j_blues on 2006-06-22
Then I don't seem to get what these power levels do?

I thought, this is a percentage level of the CPU speed it runs on. Obviously, if you restrict it to the lower two levels, it will never run on full speed, hence be slower. Right?

This is an intended behavior while running on battery, because it probably uses less power when running on, say, 800 MHz than at twice the speed.

Am I getting it right?

---

### Post by yopnono on 2006-06-22
On my machine the CPU uses full speed when needed (CPU Scaling)
This powerstate is as far as i know only for idle. Quote from the link I provided.

[http://www.thinkwiki.org/wiki/Talk:Problem_with_high_pitch_noises](http://www.thinkwiki.org/wiki/Talk:Problem_with_high_pitch_noises)
> #  Thinker: These options affect power consumption when the CPU is idle. Here are the figures on one ThinkPad T43:

    * processor.max_cstate=4: 15160mW (default, noisy)
    * processor.max_cstate=3: 15770mW (660mW higher, silent)
    * processor.max_cstate=2: 16100mW (2940mW higher, silent)

---

### Post by elwood_j_blues on 2006-06-22
Ah, okay. Yes I read your link but I could not quite make sense of it. Now I can, thanks.

When I look at this though, the smaller cstates seem to consume *more*, not *less* power, is that right? (Not considering the sound factor on your laptop, currently).

Does anyone know if there is a flag to affect the speedstepping behavior? I think it would positively affect the battery life if we cut it down to like 60% cpu maximum while on battery.

Anyone having experience with that?

---

### Post by tribaal on 2006-06-23
No unfortunately, but I'll be sure to subscribe to this thread as I would love to have that possibility :

- trib'

---

### Post by yopnono on 2006-06-23
The CPU scaling should make the cpu stepdown on idle or on battery. Add it to you panel and see. Also read this thread, specially the 3rd post down on how to activate manual control of the cpu.

[http://ubuntuforums.org/showthread.php?t=183416&highlight=governor](http://ubuntuforums.org/showthread.php?t=183416&highlight=governor)

---

### Post by yopnono on 2006-06-23
The CPU scaling should make the cpu stepdown on idle or on battery. Add it to you panel and see. Also read this thread, specially the 3rd post down on how to activate manual control of the cpu.

[http://ubuntuforums.org/showthread.php?t=183416&highlight=governor](http://ubuntuforums.org/showthread.php?t=183416&highlight=governor)

---

