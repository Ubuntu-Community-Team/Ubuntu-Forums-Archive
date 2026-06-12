---
title: "Rebooting Problem"
date: 2005-12-06
forum: Hardware &amp; Laptops
---

### Post by winstonma on 2005-12-06
I got Ubuntu Linux 5.10 on Dell GX280. After installation I can't do the normal reboot and shutdown. I always said 'Restarting System and the system helt'. Does anyone have the same problem?

---

### Post by amohanty on 2005-12-06
> 'Restarting System and the system helt'

When do you get this? When you reboot, or shutdown or all the time?
Have you been able to login and use the system?

AM

---

### Post by winstonma on 2005-12-06
It always states 'Restarting System'

During reboot and restarting system
And mostly (90%)

---

### Post by amohanty on 2005-12-06
So you have been able to login and use the system, but whenever you boot or shutdown or restart you get this message, am I correct?

Try the following from the terminal and post the result:

```
sudo shutdown -h now
```

---

### Post by winstonma on 2005-12-06
Thanks it works... but how can i do that in GUI mode?

---

### Post by amohanty on 2005-12-07
So basically a clean shutdown does work. Now when you do a shutdown using the logout confirmation dialog, does it give the message that you reported, every time?

I am sorry if I sound repetitive, but I want to be sure of the steps you take to shutdown the system.

---

### Post by winstonma on 2005-12-07
Yes

---

### Post by amohanty on 2005-12-07
And once it gets to the "Restarting system" message does it hang or do you get a list of messages, indicating that a shutdown is in progress?

Does it hang at any point of time during shutdown? If so what is last message on the screen before it hangs?

Finally, do you have to press the power button to turn it off?

AM

---

