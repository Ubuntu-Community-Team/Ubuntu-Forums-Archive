---
title: "Asus A2D and Ubuntu: fan problem"
date: 2007-08-08
forum: Hardware &amp; Laptops
---

### Post by Olio on 2007-08-08
Hi,

I have an Asus laptop with Ubuntu 7.04 installed. It has been installed from a 7.04 final CD, and is up-to-date.
The problem I have is that sometimes the laptop fan will start, and never stop. So my CPU temp goes down to about 37 C, as now.

I used to have PCLinuxOS 0.93 on this laptop, and installing a few modules (such as cpufreq or similar, but I can't exactly remember which) sorted this issue.

What do you advise to solve this issue?

Thanks in advance for your help.

---

### Post by bwtranch on 2007-08-08
Don't you want the fan to keep your computer as cool as possible? I don't see theproblem:confused:

---

### Post by Olio on 2007-08-08
Quite a quick answer...

A never stopping fan is a problem to me. Particularly since it is not the most silent one. That's on top of the issue that the fan will need replacing earlier than it should, and I am not keen on opening the laptop.

---

### Post by Olio on 2007-08-09
Alternatively, is there a way to reset the status of the fan via a command line ? So when the CPU temp is low but the fan is still spinning, I could somehow reset the fan status, which would get an update of the temp from the probe, and, realising it does not need to spin, would stop...

---

### Post by Olio on 2007-08-14
Still no suggestion?

---

### Post by shad0w_walker on 2007-08-14
Have you tried powersaved? Its in the repos and I have seen a couple of sources that say this works nicely.
If that doesn't work try:

```
sudo modprobe asus_acpi
```

If that works then add asus_acpi to the end of your /etc/modules file and you should be set.

---

### Post by Olio on 2007-08-18
Thanks for the tip. I'll try that. I just hope if things go wrong I can go back to my current install...

---

### Post by Olio on 2007-08-18
OK, so after trying powersaved, I removed it immediately.

It could not change my CPU speed , and the laptop fan was on permanently. Back to using powernowd.

I do not get any output (or apparent chage in fan behaviour)  while trying you modprobe code :/

---

