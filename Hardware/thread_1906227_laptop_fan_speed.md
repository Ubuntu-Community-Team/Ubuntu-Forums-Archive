---
title: "laptop fan speed"
date: 2012-01-08
forum: Hardware
---

### Post by mistafeesh on 2012-01-08
Right, I've been meaning to post about this for ages but I suggested a friend move over to ubuntu after windoze problems and he's got the same issue...

My laptop fan is constantly going at full blast when it's in Ubuntu - it sounds like it's going to take off sometimes! I have a fairly old HP Compaq 6720s. I'm not sure which laptop my mate has but it's not the same one.

Anyone got any idea what could be causing this?


Thanks,
Dan

---

### Post by Bucky Ball on 2012-01-08
Perhaps look here: [http://ubuntuforums.org/showthread.php?p=5031046](http://ubuntuforums.org/showthread.php?p=5031046)

The fix is in post #2. I had an older HP laptop which I needed to apply this fix to.

---

### Post by Mark Phelps on 2012-01-08
> **mistafeesh said:**
> Anyone got any idea what could be causing this?

Yes -- HEAT!  Recent Linux kernels don't allow the CPU to idle, thus, since it's running all the time, it's getting HOT -- and that causes the fan to run louder as well.

See below for more info:

[https://bugs.launchpad.net/ubuntu/+bug/901232]("https://bugs.launchpad.net/ubuntu/+bug/901232")

---

### Post by KdotJ on 2012-01-08
What is the temperature like? Does it feel hotter than usual?

You can check the temperature by installing the sensors...

```
sudo apt-get install lm-sensors
```

Then detect the sensors in your machine...

```
sudo sensors-detect
```

And follow the instructions it provides you (tey are yes/no questions). You can then view the temperatures of your hardware with..

```
sensors
```

Paste the output here if you like.

---

### Post by KdotJ on 2012-01-08
> **Mark Phelps said:**
> Yes -- HEAT!  Recent Linux kernels don't allow the CPU to idle, thus, since it's running all the time, it's getting HOT -- and that causes the fan to run louder as well.

See below for more info:

[https://bugs.launchpad.net/ubuntu/+bug/901232]("https://bugs.launchpad.net/ubuntu/+bug/901232")

Urgh.. I had this issue with Arch, managed to solve it with cpufreq but obviously that's what the bug is about. It took me a lot of messing around.

---

### Post by mistafeesh on 2012-01-11
Okay... I think I'm totally in over my head here! I get the general gist of what you're saying and it sounds like it's not too bad an issue. Running smartctl on my hdd seems to say it's healthy. I have loads of other stuff to sort out at the moment so I'll come back to this one when I've got some headspace! Sorry

---

