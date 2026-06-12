---
title: "Laptop shuts down unexpectedly"
date: 2009-05-04
forum: Hardware
---

### Post by Morgonte on 2009-05-04
I have a HP nx7400 Notebook that's been running a dual boot system Ubuntu/Win XP perfectly for 2½ years. Currently I run Hardy Heron and XP SP2. But since a month and a half Ubuntu shuts down unexpectedly, often when I leave the computer on to do something else. 
It will not boot in Windows Normal Environment (shuts down at the start screen) either, but will boot successfully into Windows Safe Mode environment.

The temp log for TZ0 (first core) doesn't exceed 50 C.

Any ideas on what to do?

---

### Post by mikedep333 on 2009-05-04
You should run memtest86 from the grub (black startup) menu. Leave that going for like 6 hours or so and see if it uncovers any errors.

---

### Post by Morgonte on 2009-05-04
Thanks, I've got memtest86 running now, and will let you know the outcome.:-\"

---

### Post by Morgonte on 2009-05-04
Ok, I've let memtest go for 5 hours 15 min with no errors. That is way beyond double the longest time the machine would last running Hardy.
Nevertheless, it was worth a try.

---

### Post by freonchill on 2009-05-04
does it just lock-up when you try to boot into windows?

it boots into ubuntu but shuts down or just dies when its idle?

we know its not a heat problem (perhaps) because of the memtest running for 5+ hours.

---

### Post by mikedep333 on 2009-05-04
You can also try running ubuntu off of a live CD or live USB key and see if it works reliably off of that. It it does, then it is likely a hard drive problem.

---

### Post by Morgonte on 2009-05-05
> **freonchill said:**
> does it just lock-up when you try to boot into windows?

It dies right after displaying the XP startup screen, before entering the login screen.

> 
it boots into ubuntu but shuts down or just dies when its idle?


It just dies when its idle, 30 min up to 2 hours after booting. If I then boot into ubuntu again it will only last a few minutes.

> 
we know its not a heat problem (perhaps) because of the memtest running for 5+ hours.

Yes, and I left memtest going for a total of 10 hours, with no errors.

---

### Post by Morgonte on 2009-05-05
I might have come up with a solution:). Since the shutdown often happen when I'm not at the computer I figured it could have something to do with the screensaver (maybe OpenGL), so I disabled it and lengthened the time before the system regards the computer inactive to 2 hours. Now Hardy have been up and running for 3 hours!=D>

---

### Post by mikedep333 on 2009-05-05
That would make sense because windows uses the graphics adapter in a larger way in regular mode than in safe mode.

Still, if your graphics adapter can't be used for regular 2D in windows, then that is not a good sign. I wouldn't count on it working with regular 2D in linux forever. In fact, I wouldn't be surprised if videos cause it to crash.

---

### Post by Morgonte on 2009-05-06
Yes, it seems definitely to have something to do with 3D graphics. Now Hardy runs all day without problems. Youtube videos are ok, wmv videos too, but when I run Billard-GL the computer dies within a minute. 

Of course the windows problems hasn't change, I'm gonna install the latest graphics drivers to see if that makes a difference (but this doesn't seem to be the proper forum for windows problems;)).

---

### Post by Morgonte on 2010-05-09
Just for the record, It's been a while since i solved the problem. It all had to do with a defective memory module. I removed the module, and the computer went completely normal in a blink.

---

