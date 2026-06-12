---
title: "Laptop fan is too noisy"
date: 2011-11-11
forum: Hardware
---

### Post by medoos on 2011-11-11
Hi , 

I have HP Pavilion Entertainment PC , and recently I installed Ubuntu .
I notice that the fan of the laptop is always noisy even I'm not doing any activity and no application is open.
is there a problem in the ubunto version ? is there any configuration needed to be done to get rid of this noise ?

---

### Post by medoos on 2011-11-11
any help please ?

---

### Post by antiartist on 2011-11-11
my first thought is that this has nothing to do with Ubuntu...or any OS version, for that matter.

How old is this box?  Fans are cheap and usually the first thing in terms of hardware to start failing.  Dirty/worn bears in the fan will create lots of noise all of the sudden.  Perhaps pulling the fan out of the case and cleaning it with some compressed canned air will help?  Do you have another case fan to swap with to eliminate hardware issues?

---

### Post by northd_tech on 2011-11-11
Fans aren't so easy to replace on laptops though (I've got an old, **briefly**-functional Compaq Laptop 'paperweight' in storage for this very reason, in fact).

Let's see how hot the thing really is with these 2 terminal commands:

```
sensors

sensors -f
```If the power management and CPU frequency are off-kilter for some reason could definitely cause **much** fan activity.

---

### Post by medoos on 2011-11-12
antiartist , northd_tech

Thanks for your replies .

I think the problem has nothing to do with the fan itself , as I have also Windows 7 installed on the same laptop and it behaves  smoothly with no noise .

I think it is something in the frequency of the CPU , I'm not sure

---

### Post by Lars Noodén on 2011-11-12
Try checking the temperature as in post [#4](http://ubuntuforums.org/showpost.php?p=11448856&postcount=4) above.  You may need to install the package [lm-sensors](http://packages.ubuntu.com/oneiric/lm-sensors) to get the utility [sensors](http://manpages.ubuntu.com/manpages/oneiric/en/man1/sensors.1.html).

---

