---
title: "Laptop Linux"
date: 2008-07-02
forum: Hardware
---

### Post by faromount on 2008-07-02
Hi all. I am looking for info on Ubuntu power usage. Upon purchasing my laptop it was pre-loaded with "That that shall not be spoken of," but it did last longer on one full battery that Ubuntu-Gnome, not sure which version.

Does anyone know if a particular window manager would prove better for laptop battery time?

Perhaps there is a guide to turning off non-essential services to save CPU cycles and saving Battery time?

I have all desktop effects compiz etc. turned off and I don't want to loose any functionality to wireless network detection/connection, web browsing or multimedia.

Thanks for any replies.

Laptop - HP nc6320
Dual core @2.00GHz
Memory - 1GB
Wireless - ipw3945

---

### Post by kevmitch on 2008-07-02
Install cpufreq utils if it isn't already

```
sudo aptitude install cpufrequtils
```

Then run

```
cpufreq-info
```

and post the output

You can also try using powertop for diagnosing what is using all that battery power. It gives mostly info relating to processor power usage, but it also gives more general tips at the bottom for reducing power. 

```
sudo aptitude install powertop
sudo powertop
```

If you post the tips it gives, I can help you make them permanent.

---

### Post by sdennie on 2008-07-02
You should also have a look at [www.lesswatts.org](www.lesswatts.org).  It contains a lot of information on improving battery life.

---

### Post by faromount on 2008-07-02
cpufreq-info gives

```
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU
```

any suggestions?

powertop suggests usb wakeups, wifi radar and other stuff. That is a wicked tool. I am gonna go through them 1 by 1. It gives excellent info on cpu wake ups and remedies.

LessWatts.org is a good site as well. To be honest I was hopin one of you might say xfce or something simple but this will keep me busy for a while.

Thanks for your responses.

---

### Post by faromount on 2008-07-02
FYI, found this site whilst looking at usbcore.autosuspend=1

[http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption](http://www.thinkwiki.org/wiki/How_to_reduce_power_consumption)

Some good tips.

Cheers

---

### Post by kevmitch on 2008-07-02
It looks like you don't have a module loaded to do cpu frequency scaling. Since it looks like you have a newer processor (is it core or core2?) you could try acpi-cpufreq

```
sudo modprobe acpi-cpufreq
```

You'll also want to load a governor module. "ondemand" is probably what you want. 

```
sudo modprobe ondemand
```

Otherwise, you could just try

```
sudo /etc/init.d/loadcpufreq start
sudo /etc/init.d/cpufrequtils start

```

This is what should get run on boot, so you'll see if things will load up correctly this way.

Someone else may know more about wifi radar, but for the usb wakeups,
 
```

echo options usbcore autosuspend=1 > /etc/modprobe.d/usbcore.modprobe

```

will make USB auto-suspend permanent starting the next time you load this module. Depending on your powertop version, it may not stop complaining because it really wants autosuspend=0, which is probably not necessary. The number is the number of seconds before an inactive usb port suspends.

Are you running i386 or amd64? Especially for the latter, you want to use a kernel newer than 2.6.24 which is the first one that allows dynamic ticks (NO_HZ) for 64-bit. There is also quite a lot of other powersaving improvment in that kernel. I literally decreased my wakeups by an order of magnitude by upgrading to it on amd64.

---

