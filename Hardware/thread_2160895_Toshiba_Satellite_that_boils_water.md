---
title: "Toshiba Satellite that boils water"
date: 2013-07-08
forum: Hardware
---

### Post by gizzardgulpe on 2013-07-08
I have a 4 year old Toshiba Satellite with a dual core Pentium T3400 @2.16 GHz, two gigs of RAM, running Ubuntu Gnome 13.04 (though the distro seems irrelevant--every flavor of ubuntu I've tried has had this problem.)

Also, Jupiter helps, but does not solve the problem.

In short, the single cooling fan can't seem to be bothered to keep my hands from bursting into flames while I use this laptop. It has three speeds--off, low, and slightly less low. Only when the cpu reaches a critical temp of 110 C will it go into hyper-turtle mode, bringing the CPU down to a sweet, Arctic cool of 80 C. 

This was not a problem at all running Windows Vista.

So, I've spent a good 10 or 12 hours tinkering with thinkfan, fancontrol, Jupiter, and whatever else that might do the trick, but honestly, there isn't much to work with. So I thought I'd manually edit the LNXTHERM files to be more discerning about what temps are acceptable or not, but I'm not quite savvy enough to figure out the permissions and editing powers that be. "Sudo gedit" and its derivatives are about the extent of my tinkering knowledge, I'm afraid.

Anyone willing to tackle this? I'm about fed up with the blisters on my thighs.

Edit: This is all to say, I just want the fan to spin up faster. I don't care how much noise it makes, I want it to move some air.

---

### Post by ohnonot on 2013-07-10
before we go into sudo savviness, 2 things:

- my laptop sucks air from its underside, so if i actually have it on my lap (or mattress), it can't suck air. there should be a law against calling that a laptop.

- maybe your fan is clogged?

please forgive me if that's not the case. i might be able to help with the software side of things, but at least you get a free bump.

---

### Post by slickymaster on 2013-07-10
> **ohnonot said:**
> before we go into sudo savviness, 2 things:

- my laptop sucks air from its underside, so if i actually have it on my lap (or mattress), it can't suck air. there should be a law against calling that a laptop.

- maybe your fan is clogged?...

The most important part of your laptop that needs to be clean is… the heatsink. Heat is the “cause of death” for most laptops. The heat not only causes all components to expand and contract a little (as you turn it on and off), but will also reach dangerously high levels and make your laptop crash or shut down if the fan(s) and the heatsink(s) are clogged with dust.
All computers work a little bit like vacuum cleaners – sucking air form one side and blowing it out from the other. Unfortunately they don’t come with filter bags to catch all the dust and debris. After just a few months the fans and heatsinks are well coated with dust. If not cleaned, their effectiveness quickly drops and eventually goes down to zero when the heatsinks get fully clogged.
Before you start fiddling with any file in your system I would advise you to get yourself a can of compressed air and blow away the dust off the fan and heatsink. However if the heatsink has already been clogged, this won’t help. The compressed air will not be enough to unclog it. If you have never cleaned the heatsink and you had used your laptop for over a year, chances are that both the fan and the heatsink are clogged with dust and debris. The solution in this case is to remove the heatsink, clean it and install it back.
Some newer laptops have a special removable cover on the back for easy access to the heatsink. But most laptops have to be disassembled to reach it. Another problem is that the thermal paste between the heatsink and the CPU hardens with higher temperature, so if the laptop has been overheating, chances are that the heatsink is stuck solid to the CPU, making it very hard to remove. The process also includes removal of the old thermal paste from both the CPU and the heatsink and applying a small dab of fresh thermal paste, preferably silver filled for better heat transfer.
And lastly – don’t use your laptop while it’s on a soft surface, like bed cover or sofa. That will block the fan and the laptop will overheat. Try using something with a hard surface under the laptop, like a large hardcover book or a tray.

---

### Post by gizzardgulpe on 2013-07-10
Thank you both for your replies. Having just taken the laptop apart and replacing the dvd drive with an extra fan and modding the case to give it a bit more airflow for said fan, I can assure you that the old fan is not bound in any way and the heatsink is not clogged. I am aware that blocking the air intake is a bad idea.

However, I can block the holes all I want, the fan simply doesn't spin up until it hits 70C. Then it might hit a higher rpm around 100C. If the fan spun at the 100C rpm from the start, I'd be happy.

---

### Post by ohnonot on 2013-07-10
ok, but ithink it's good we ruled that one out...

so you put in the extra fan just now, or was it there from before your problem started?
that might explain why linux is having a hard time setting that up.
have you made extensive websearches on that kind of stuff?

you might also search if this is a toshiba related thing, not so much ubuntu.

are there some hardware/software/powermanagement analyzing tools that might shed more light on this?
there's really not much hard information here, so far.
generally i would say, yes, there's files in the system somewhere that say what temperature is critical. i've seen them. racking my brain to remember where, but even if, istill wouldn't know what to do with them. but it just might be enough for a dirty hack, to prevent your laptop from burning itself.

fwiw, my laptop's fan is practically always moving. conky shows a temperature of ~55 degrees celsius whith normal use (internet, movies...) and it hardly goes beyond 70.

---

### Post by 1clue on 2013-07-10
My wife's satellite had the same problem, almost the same model laptop.  I eventually put the windows drive back in it.

This is NOT a blocked airflow problem, nor is it a hardware problem.  You can boot Windows, it's absolutely fine.  Boot *buntu, and it overheats.  You can actually use it as a laptop when it's running Windows, you have to put it on a table with spacers under it to run Linux, and then you can feel the heat blisters forming on your fingers.  It was actually painful to touch.

I think there are kernel options for Toshiba laptops which are not compiled into *buntu.  I didn't have time to mess with it for my wife's laptop, and she doesn't understand why I have to spend so much time tinkering with it.

If I had time and inclination, I would experiment with compiling the kernel, then try to install a kernel option to pin the fan wide open.  It's gotta be something with sensors or something like that.

---

### Post by ohnonot on 2013-07-11
i did a web search "linux toshiba satellite overheat solved"
and this came up:
[http://www.linlap.com/toshiba_satellite_u500](http://www.linlap.com/toshiba_satellite_u500)
> I could solve the overheating problem with Toshiba Satellite U500-11J under Ubuntu 12.04 LTS. There are 6 binary registers located at

/sys/devices/virtual/thermal/cooling_device0/cur_state
…
/sus/devices/virtual/thermal/cooling_device5/cur_state

– they are responsible for the cooling fan,
but I have not yet figured out how.

For me, writing 1 and then 0 to cooling_device0 solved the problem.
Namely, one needs to execute the two lines (as a root):

echo -n “1” > /sys/devices/virtual/thermal/cooling_device0/cur_state
echo -n “0” > /sys/devices/virtual/thermal/cooling_device0/cur_state

I wrote a simple script that does it and call it in /etc/rc.local
(so that it is executed at the boot). With this solution, the processor
temperature is stabilized at 60-65 C.
...and this:
[http://tuxtweaks.com/2008/08/how-to-control-fan-speeds-in-ubuntu/](http://tuxtweaks.com/2008/08/how-to-control-fan-speeds-in-ubuntu/)
(though i would recommend conky instead of gkrellm, but that's purely aesthetic)
...and this:
[https://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/toshiba-satellite-pro-laptop-overheating-911956/](https://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/toshiba-satellite-pro-laptop-overheating-911956/)
(mainly links to other potential solutions)
...and this:
[https://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=54452](https://forums.computers.toshiba-europe.com/forums/thread.jspa?threadID=54452)
(probably more linux related stuff on the toshiba forums)

i hope this helps. good luck.

---

