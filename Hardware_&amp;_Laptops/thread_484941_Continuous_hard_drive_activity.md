---
title: "Continuous hard drive activity"
date: 2007-06-26
forum: Hardware &amp; Laptops
---

### Post by fmaste on 2007-06-26
Hi,
I'm running ubuntu Feisty on my Dell inspiron 9400.

Almost every two second the hard drive activity light blinks and I can also hear the hard drive doing something.
This happens no matter what I am doing, computer idle, just after login, after the computer was left alone for more than 10 hours. I even kill a lot of process and same thing happens.

The system monitor does not show disk activity, How can I know which process is? 
I believe this is not good for my hard drive lifetime. does anyone know something about or is having the same problem?

Thanks!

---

### Post by Nadstar on 2007-06-26
I think this is normal and just system tasks being run in the background (for instance; Beagle indexing), and is nothing to worry about.

---

### Post by fmaste on 2007-06-26
I leave my notebook all night on doing nothing and when I wake up beagle is still indexing? there must be a problem with something.
If I kill beagle processes it is the same story.
This means that my hard disk is always working, also when doing nothing. I don't think this is normal.

---

### Post by wally83 on 2007-07-04
I confirm this behavior/bug. 

You can still get rid of this using (and configuring) laptop-mode.

To install:
```
sudo apt-get install laptop-mode
```
Run:
```
sudo laptop-mode start
```

BUT, with default configuration file, laptop-mode does nothing, so you need to configure this file:
```
sudo gedit /etc/laptop-mode/laptop-mode.conf
```

Don't worry, configuration file is commented well.
#1 thing you have to do, is to enable laptop-mode:

```
# Enable laptop mode when on battery power.
ENABLE_LAPTOP_MODE_ON_BATTERY=1

# Enable laptop mode when on AC power.
ENABLE_LAPTOP_MODE_ON_AC=1
```

---

### Post by MindFlayer on 2007-07-04
I had this problem too on my Ubuntu laptop and it was *irritating*. Luckily laptop-mode seemed to fix the thing and now my laptop is fully silent.:p

---

### Post by socref on 2008-06-05
> **MindFlayer said:**
> I had this problem too on my Ubuntu laptop and it was *irritating*. Luckily laptop-mode seemed to fix the thing and now my laptop is fully silent.:p


I am having the same problem on a Dell Inspiron 530 desktop with 2GB of memory.

Any ideas how I can stop the constant hard drive activity on this desktop? Driving me crazy and it cannot be good for the HD.
Thx
socref

---

### Post by socref on 2008-06-10
Can anyone provide any guidance here? I am very concerned about my hard drive spinning constantly.

Thx
socref

---

### Post by socref on 2008-07-07
Interesting new information on non-stop H/D activity.

This morning I powered-up my computer. When the log-on screen came up, and before I entered my user name, I looked to see if the H/D light was blinking. It was. 

So before I had even logged-on and before I had my desktop on-screen the H/D light was flashing every one or two seconds.

Any ideas? Somebody must have some insight into this non-stop H/D spinning.
Thx
socref

---

