---
title: "How to properly power off a RPi4 with Ubuntu"
date: 2019-12-25
forum: Hardware
---

### Post by multibuild on 2019-12-25
Hey guys. I'm new to the Raspberry Pi and Ubuntu. When I power off using the GUI, the operating system turns off, but the Raspberry Pi stays running. 

I have tried using:
sudo shutdown -h now 
and a few other things with the same result. 

Is this what is supposed to happen?  Can I now unplug it from the wall; as I need it off and not running all the time. 

Thanks everyone!

---

### Post by yetimon_64 on 2019-12-25
> **multibuild said:**
> Hey guys. I'm new to the Raspberry Pi and Ubuntu. When I power off using the GUI, **the operating system turns off**, but the Raspberry **Pi stays running**. ...

That sounds exactly the same with the raspberry pi 3B, pi 3B+ and pi 4 using raspbian here. When I shut down the OS the OS powers down and the monitor goes blank but the power light on the pi-s all stay on.

After shutting down the OS I simply unplug the pi unit from the power source otherwise it will still appear to be on but is not running.

That seems to be a design/functional shortcoming with the pi hardware, not so much an OS problem.

---

### Post by multibuild on 2019-12-26
Thanks for the reply.  I have marked the thread as solved for now.  

I appreciate it!

---

