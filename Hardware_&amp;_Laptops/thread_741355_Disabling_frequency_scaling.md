---
title: "Disabling frequency scaling"
date: 2008-03-31
forum: Hardware &amp; Laptops
---

### Post by Vaftrudner on 2008-03-31
Hello!

I searched the forums, but couldn't find this specific problem. I'm using Gutsy on a Philips laptop with Intel Core2 Duos, 2x1.50 GHz. I've been using VMWare Workstation for a while, but yesterday, all of a sudden, it started complaining about my processor not reaching the minimum requirements, being at 1 MHz. I've asked around and I've been told that frequency scaling might cause this. As I understand it, powernowd does the scaling in Gutsy, but I don't feel comfortable using it without asking for advice first, since I'm new to Ubuntu.

Do you know how I can turn frequency scaling off to test if this causes problems with VMWare Workstation?

Thanks for your time!

---

### Post by sdennie on 2008-03-31
I've had and read about people having problems with frequency scaling (maybe just Core 2 Duo Penryn) after coming back from suspend/resume.  You can force the cpu to the maximum scaling mode using:

```

sudo sh -c "echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor"
sudo sh -c "echo performance > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor"

```

The default is "ondemand" and you can get back to it by using:

```

sudo sh -c "echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor"
sudo sh -c "echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor"

```

In fact, to avoid getting the cpu stuck at lowest frequency, I echo "userspace" to both CPU's and then go back to "ondemand" in a script that gets run when I resume from suspend.  That fixes the problem for me and, if that turns out to be your problem, you should be able to figure out how to do that automatically if you google a bit.

---

### Post by Vaftrudner on 2008-03-31
Thanks for the help vor, although this did not solve the problem, I managed to find out that this is indeed a bug in VMware, it seems to be a timing issue with the Core processors. It's not solved but I found a workaround in restarting VMware like so:

```
sudo /etc/init.d/vmware restart
```

I thought I'd change the title to [Solved] and edit it to make other users with this problem find it easier. How do I do that?

---

