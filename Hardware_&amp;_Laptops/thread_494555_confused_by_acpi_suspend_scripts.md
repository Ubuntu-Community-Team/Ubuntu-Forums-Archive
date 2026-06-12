---
title: "confused by acpi suspend scripts"
date: 2007-07-07
forum: Hardware &amp; Laptops
---

### Post by daschmidty on 2007-07-07
I am slightly puzzled. I am running feisty on a thinkpad X24. Suspend works, except for a few minor drawbacks. 1. sound doesn't resume unless i use 
```
sudo /etc/init.d/alsa-utils restart
```
is there a script i can add this to somewhere?

2. My backlight never turns off when the laptop goes into suspend. This really confuses me because in the /etc/acpi/suspend.d/90-frambuffer-stop.sh file there is a line for vbetool dpms off, which if i type into a console switches off the backlight. Is there some way to make this line not ignored by the system?

---

### Post by spacebetween on 2007-07-10
I have the same problem.

I'm looking how to incorporate the command that you posted into the suspend script. Also, randomly, my backlight does not go off during suspend, either.

---

### Post by daschmidty on 2007-07-19
i managed to fix the backlight problem using a workaround. I installed the uswsusp package and to suspend use
 ```
sudo s2ram -rf
```
which can be automated by following the instructions and using the scripts on this site
[http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/]("http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/")
and adding the "-rf" to the calls to s2ram
the sound is still a problem though.

---

