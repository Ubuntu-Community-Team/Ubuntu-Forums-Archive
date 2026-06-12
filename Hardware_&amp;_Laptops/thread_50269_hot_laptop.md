---
title: "hot laptop"
date: 2005-07-19
forum: Hardware &amp; Laptops
---

### Post by MikehBar on 2005-07-19
Hi,

I have a dell inspiron 5150 with a 3.20 Ghz p4-m (ht) processor. Problem is that the laptop is hot most of the time while in ubuntu. Fan is constantly running. powernowd is enabled and p4-clockmod module is loaded. Before p4-clockmod loaded, cpu scaling was not working. Did

mike@Abaddon:~$ cat /proc/acpi/thermal_zone/THM/temperature
temperature:             73 C

Very hot! 

I'm no expert and kind of new in linux, but I don't think this cpu is fully supported. I don know if Hyper threading is working under ubuntu. Can anyone point me to some answers? I would really love to get my cpu to run at a lower temperature, it's the only thing keeping me from using linux full-time. THX.

---

### Post by missileboat on 2005-07-19
You could throw it in the freezer for a couple of hours!  :smile: I had that problem with a custom made tower I had. The only solution that I found was to take the side of the case off and use my room fan to cool it. As far as laptops are concerned, the best that I can suggest is to buy a laptop heat distrobution stand like  [this.](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=984047&CatId=607) Otherwise, I don't know what to tell you. Good Luck,

missileboat

---

### Post by matthew on 2005-07-19
Those processors tend to be a bit hot, but this does seem excessive. 

If you have a can of compressed air, or maybe a gentle vacuum you could try to clean out the ventilation (carefully and with the power off!) and see if that helps. Even a little bit of dust can cause the temperature to rise and it makes cooling systems significantly less efficient.

---

### Post by MikehBar on 2005-07-19
[QUOTE=matthew]Those processors tend to be a bit hot, but this does seem excessive. 

If you have a can of compressed air, or maybe a gentle vacuum you could try to clean out the ventilation (carefully and with the power off!) and see if that helps. Even a little bit of dust can cause the temperature to rise and it makes cooling systems significantly less efficient.[/QUOTE]
 
These Processors do tend to get really hot, I was aware of that problem and I've cleaned it with compressed air before. But I don't think that's the problem here, since it runs very cool in windows as it should run in ubuntu.

---

### Post by MikehBar on 2005-07-24
Anyone out there?

---

### Post by müller on 2005-07-25
[QUOTE=MikehBar]Anyone out there?[/QUOTE]
 if i was you i would return the laptop where you bought it. Hope it is still in warenty.

---

### Post by ph00dz on 2005-07-26
Out of curiosity, is there a practical problem with it running this hot? In other words, does the laptop feel uncomfortable on your lap or does the machine shut down from overheating?

---

### Post by MikeyXX on 2005-07-26
So it's only overheating with Linux? Did you have Windows installed? If so, what was the temperature characteristics with that?

---

### Post by netsyd on 2005-07-26
Not necessarily in reference to your exact problem, but somewhat similar...

I'm running a P4 1.4 (NC4000) and it was running pretty hot as well. But I found it not to be so much my processor but the power unit for battery charging and whatnot that was getting really hot. I'm not sure why or how, but by installing laptop-mode-tools and laptop-tools (this is a harddrive control application and the scripts for it) it brought the temperatures way down. 

Basically by throttling the hard drive it brought down the amount of pre-reading/caching. In turn this brought down the utilization of the processor and served to lower the overall temperature and actually significantly improved my battery life as well.  ;-)

---

### Post by dgrant on 2005-07-26
It is most likely a Ubuntu linux problem. Did you experience the problem in any other OS? I only experience it with Ubuntu, I had straight Debian on my laptop before with no problems. Now I tried Ubuntu, and the laptop is extremely hot. So much so that I don't want to run it.

---

### Post by netsyd on 2005-07-26
By the way ... is powernowd running? 

```
pgrep powernowd
``` If it returns a value then it is running....

---

### Post by kiddo on 2005-07-27
I have a speedstep pentium 3 (500/600mhz). I've stopped monitoring it with gkrellm, it was getting me friggin' paranoid. 50 degrees minimum, easily up to 60. And if it's struggling, or even just watching anime, it can reach that 73 degrees. Then the fan starts. Cools down, starts again, etc. Otherwise, until 72 degrees no problem.

First I've been using door-blocks (you know the thingies that are used to block the door by kickin' these in the space below), bought 50¢ at a dollar store near me, to make a cheap but efficient stand for the laptop. Because this laptop doesn't have that keyboard standup (bad thing). I haven't noticed a change, but it can't hurt (especially on fluffy surfaces).

I've bought a cheap usb fan (it's cool looking... lit by a green LED) in Hong Kong. Easy to find and that allows my keyboard to stay fresh, but I don't think I have seen any heat difference from the sensors.

So that sums it. Seems like there's nothing to do. I thought, however, that newer laptops did not produce so much heat. Seems like I'm partially wrong.

---

### Post by N8MAN1068 on 2005-07-27
If you are using it on your desk with the AC plugged in, take out the battery. You'd be surprised how much that helps. on my HP ZD8000, my right wrist cooks and make me uncomfortable.

The usb powered laptop cooler is a good idea. I have the Antec one for mine and I can notice a difference, even though my laptop is too large to fit the base properly. That is another thing....there are several aftermarket laptop coolers. Look at them all, and notice where the fans are. Then look under your laptop, and get a cooler that matches your laptop fan pattern.

I believe in the ACPI settings there's options for configuring the laptop to run differently between AC/Battery.

---

### Post by MikehBar on 2005-08-02
[QUOTE=dgrant]It is most likely a Ubuntu linux problem. Did you experience the problem in any other OS? I only experience it with Ubuntu, I had straight Debian on my laptop before with no problems. Now I tried Ubuntu, and the laptop is extremely hot. So much so that I don't want to run it.[/QUOTE]
I'm sure its an ubuntu problem. This has been the only OS I've had besides windows and in windows it runs very cool. The fan only starts when the computer is under heavy workload.

> By the way ... is powernowd running?

Code:

pgrep powernowd

If it returns a value then it is running....


did that, and i got a value. Actually powernowd doesn't start when Ubuntu starts, I have to manually start it right after loading the p4-clockmod module. I have now the latest version of powernowd. Using the old one cpu scaling showed 3.2 Ghz as the highest freq, but now with the latest version it shows 1.6 Ghz. I think HT has problems with powernowd. When I start it i get:

mike@Abaddon:/etc/init.d$ sudo powernowd start
powernowd: PowerNow Daemon v0.96, (c) 2003-2005 John Clemens
WARN: ncpus(1) is not a multiple of threads_per_core(2)!
WARN: Assuming 1.
powernowd: Found 1 cpu:  -- 1 thread (or core) per physical cpu
powernowd:   cpu0: 199Mhz - 1599Mhz (8 steps)

If anyone has any idea of whats going on...

---

### Post by daniel@dpr on 2005-09-24
Can someone tell me how to run or start powernowd?
When i pgrep powernowd in a terminal screen, it returns no value.
I am having same problems with my zd7000.
I will buy a laptop cooler fan gadget on monday as this seems consistent advice to this issue.

---

