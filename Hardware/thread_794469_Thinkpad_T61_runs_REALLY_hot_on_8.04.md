---
title: "Thinkpad T61 runs REALLY hot on 8.04"
date: 2008-05-14
forum: Hardware
---

### Post by grifter13 on 2008-05-14
Does anyone have this issue?  Fresh install of Hardy on T61, laptop becomes VERY hot with minimal activity.  The fan does not seem to be coming on or is very slow.  I also have a XP partition, which does not have this problem.

Also, my cpu speed monitor shows that I'm only at 800mhz so I should not be running this hot.  Which I am also wondering if I can set a profile to not CPU throttle when on power supply and throttle when on battery.

Any advice is greatly appreciated.

Grift

---

### Post by cmnorton on 2008-05-15
Suggest you look at these and beyond:

[http://ubuntuforums.org/showthread.p...hlight=cpu+fan]("http://ubuntuforums.org/showthread.php?t=794456&highlight=cpu+fan")
[http://ubuntuforums.org/showthread.p...cpu+fan&page=2]("http://ubuntuforums.org/showthread.php?t=765688&highlight=cpu+fan&page=2")
[http://ubuntuforums.org/showthread.p...78#post4895378]("http://ubuntuforums.org/showthread.php?p=4895378#post4895378")
 		                   		  		  		 		 			 				__

---

### Post by Jordanwb on 2008-05-15
I am having the exact same problem (identical) but with a T21 instead of a T61.

---

### Post by cmnorton on 2008-05-16
> **Jordanwb said:**
> I am having the exact same problem (identical) but with a T21 instead of a T61.

You might be able to find more information at ThinkWiki.org, and if you find something useful, it is always helpful to add your information there as well.

---

### Post by djs_uk on 2008-05-24
Which part of your T61 gets hot?  On mine, the front right palm rest tends to heat up often. It does get a little uncomfortable at times, but not so hot that you can't keep your hand there. I think it is due to the hard disk being located underneath that palm rest. Maybe your heat problem happens at the same time as disk access is high?

---

### Post by Steve413z on 2008-05-24
try disabling the Compiz effects

---

### Post by Steve413z on 2008-05-24
Step 1:
Press Alt + F2

Step 2:
type: gconf-editor

Step 3:
Navigate to:
/apps/gnome-power-manager/cpufreq/policy_ac

Step 4:
change that from "performance" to either "ondemand" or "conservative"

---

### Post by grifter13 on 2008-06-03
> **djs_uk said:**
> Which part of your T61 gets hot?  On mine, the front right palm rest tends to heat up often. It does get a little uncomfortable at times, but not so hot that you can't keep your hand there. I think it is due to the hard disk being located underneath that palm rest. Maybe your heat problem happens at the same time as disk access is high?

For me its the upper left corner and center of the laptop, or the area where the CPU is located.  Center might be where the GPU is located.

Grif

---

### Post by grifter13 on 2008-06-04
> **Steve413z said:**
> try disabling the Compiz effects

Yup I did that and it did help a bit.  I mean it is still very warm to the touch, but then again I don't expect it to be ice cold either :)

Grif

---

### Post by grifter13 on 2008-06-04
> **Steve413z said:**
> Step 1:
Press Alt + F2

Step 2:
type: gconf-editor

Step 3:
Navigate to:
/apps/gnome-power-manager/cpufreq/policy_ac

Step 4:
change that from "performance" to either "ondemand" or "conservative"

Awsome this exactly what I was looking for.  I didn't know how to change the setting.  Thanks for the tip.

Grif

---

### Post by grifter13 on 2008-06-04
By the way thanks for all the advise and tips guys.  I have been away for some time and couldn't check the thread.  Thx again everyone.

Grif

---

### Post by XProgrammer on 2008-07-21
Hi Grif,

I'm getting same problem of which you reported in this thread. 

[http://ubuntuforums.org/showthread.php?p=5432503&posted=1#post5432503](http://ubuntuforums.org/showthread.php?p=5432503&posted=1#post5432503)

I've raised a bug also for that. 

Did you able to solve this problem or some workaround. Please let me know. I'm desperate to get rid of it.

---

### Post by samskpun on 2008-07-28
> **Steve413z said:**
> Step 1:
Press Alt + F2

Step 2:
type: gconf-editor

Step 3:
Navigate to:
/apps/gnome-power-manager/cpufreq/policy_ac

Step 4:
change that from "performance" to either "ondemand" or "conservative"

i did that and avg temp drop from 60 to 43 (with flash one 70 to 55)

but the fan is on all the time now

---

### Post by cprofitt on 2008-07-28
I have not had any issues with my T61.

---

### Post by iamsobored0056 on 2008-07-28
> **samskpun said:**
> i did that and avg temp drop from 60 to 43 (with flash one 70 to 55)

but the fan is on all the time now

My T61's fan never turns off either.  The noise isn't too noticeable during the day, but it's keeping me awake at night. :(

---

### Post by ryansinn on 2008-08-09
the gconf-editor suggestion was already set to ondemand...

I let my machine idle for a day and I came back with it being too hot to touch.

---

### Post by maphilli14 on 2008-09-06
My T61 is hot.  I use kpowersave to set cpu from ondemand to powersave.  It's definatly hotter in performance/ondemand than in powersave.  Still hot in powersave.  Yes I use compiz and do notice that compiz eats quite a bit of CPU, even when idle.

I found a couple of items on thinkwiki which when added to the xorg.conf helped boost fps graphics performance, but still hot with high cpu.  Xorg and compiz.real processes eat 30-40% cpu at idle state, no user input, no working processes.

Mike

---

### Post by MaindotC on 2009-02-09
My T60 is hot as well - especially with more graphics-intensive applications being run.  Usually about 70 degrees C just by itself - which I think is a little high.

---

### Post by maphilli14 on 2009-02-09
Good thing I subscribed to this thread.  I solved a few things on my T61 still running Hardy.  I manually upgraded the video drivers to the latest I could find (nVidia X Server Settings says 177.80, but it wasn't avail via EnvyNG, it d/l and ran the setup script).
I also setup the latest compiz via synaptic 3rd party sources.
Best thing I did was to add the tpfan utils linked off the thinkwiki.  The fan is noisy, but the temperature is not as much an issue now!
It is still cool in my house now during late winter, so we'll see how this holds up in the hot summer.

Mike

---

### Post by MaindotC on 2009-02-14
I installed the [Fan Control Program](http://www.gambitchess.org/mediawiki/index.php/ThinkPad_Fan_Control) and not only does it work but it enabled some sort of permission so I can echo level numbers into /proc/acpi/ibm/fan now.

---

