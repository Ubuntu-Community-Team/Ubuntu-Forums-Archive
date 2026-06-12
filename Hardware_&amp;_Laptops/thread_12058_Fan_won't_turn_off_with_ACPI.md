---
title: "Fan won't turn off with ACPI"
date: 2005-01-21
forum: Hardware &amp; Laptops
---

### Post by malmjako on 2005-01-21
When I wake my HP Omnibook 6000 up from ACPI suspend mode, the fan comes on and then won't come off. I've tried writing 0 and off to /proc/acpi/fan/FAN/state but it won't shut off. I can write on to this file and the fan will come on, but then I can't turn it off. Waking the computer from APM suspend mode does work, however. The fan comes on and is then turned off immediately.

How do I turn the fan off? The fan module is loaded and I use the latest Ubuntu kernel.

---

### Post by burriko on 2005-01-21
I have the same problem on my omnibook 6100.  What seems to work is to first send a command to turn the fan on and then the command to turn it off.  I've added the following to the end of /etc/acpi/sleep.sh and it seems to do the job.

```
echo "on" > /proc/acpi/fan/FAN/state
echo 3 > /proc/acpi/fan/FAN/state
```

---

### Post by malmjako on 2005-01-22
Thanks burriko! The fan now comes off. However, after a suspend, networking won't work. I get my IP address with DHCP, but after suspend, I can't seem to get the connection back again. Have you had this problem? If so, how did you solve it?

Another strange thing: When I press the sleep button, there is no action until I press the increase or decrease LCD brightness function buttons. Does acpid not listen all the time, or what is wrong?

---

### Post by malmjako on 2005-01-23
I solved the network issue by adding the following to suspend.sh:

```
ifdown eth0
rmmod 3c59x
...
modprobe 3c59x
ifup eth0 &
```
Is there some easy way to check whether eth0 was up before suspend? Then I shouldn't do the ifup eth0.

---

