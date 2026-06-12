---
title: "HDD condition?"
date: 2010-11-06
forum: Hardware
---

### Post by Yezinki on 2010-11-06
Since am replacing  my desktop HDD coz has approx 199 bad sectors might as well show you the state of my Dell XPS laptop's drive condition?

Do I need to replace this too?

Hoping to hear your expert opinion,

Regards!

---

### Post by zealibib slaughter on 2010-11-06
no, as long as the smart values return a healthy disk then its ok.

---

### Post by Yezinki on 2010-11-06
Thanks for your expert opinion.

Is 199 Bad/Reallocated sector count an indication to replace a HDD?

---

### Post by dino99 on 2010-11-06
powered on: 275 days !!!

so maybe its time to run a fsck on next boot:

sudo shutdown now -R

and clean the system too with bleachbit for example

---

### Post by Yezinki on 2010-11-06
I just got the new 350 GB HDD on the desktop. You mean to run this command on the laptop?

Thanks.

---

### Post by Yezinki on 2010-11-06
The command wont run in the Terminal??

---

### Post by Yezinki on 2010-11-06
xps@xps-laptop:~$ sudo shutdown now -R
shutdown: invalid option: -R
Try `shutdown --help' for more information.
xps@xps-laptop:~$ 
xps@xps-laptop:~$ 
xps@xps-laptop:~$ 
xps@xps-laptop:~$ sudo shutdown now -R

---

### Post by P4man on 2010-11-06
So whats this thread about? You had a failing drive that you replaced and you have another one that is perfectly healthy. Whats the question :confused:

---

### Post by P4man on 2010-11-06
> **dino99 said:**
> powered on: 275 days !!!

Thats the total time the drive has been powered on, its not uptime!

---

### Post by Yezinki on 2010-11-06
dino99 posted command doesn't run?

---

### Post by P4man on 2010-11-06
that command if typed correctly (with a lower case r), would just reboot your system. There is no point doing that. He thought your machine had been running for nearly a year non stop.

---

