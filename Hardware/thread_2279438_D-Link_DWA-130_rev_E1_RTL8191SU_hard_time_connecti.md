---
title: "D-Link DWA-130 rev E1 RTL8191SU hard time connecting"
date: 2015-05-23
forum: Hardware
---

### Post by N'ko on 2015-05-23
I have a D-Link DWA-130 rev E1 with a RTL8191SU chip set.  Under Ubuntu 14.04 it will connect to the router occasionally, most of the time it tries and fails over and over.  It seems to connect with out issue on one of my machines that is running 12.04.  Any help would be appreciated.

---

### Post by Pilot6 on 2015-05-23
Good that you are here too. Try to test my solution at AskUbuntu, but I think it won't work.
I made a patch, then you can test it and we will fix this for everyone.

---

### Post by N'ko on 2015-05-23
I tested the driver that you suggested.  It connects consistently now, so that is great news.  It seems a little slow to connect but that is just a perception, I think it is working correctly.

The issue I know have is that after suspending and waking the computer, I need to remove the dongle and reinsert to get the wifi back up and running.  I do not know if that is a function of the driver?

---

### Post by Pilot6 on 2015-05-23
OK. Accept my answer then. I will remove my patch, because it is not needed. Suspend / resume with dongles is another issye and works differently with different kernels. I am thinking how to fix that too. But it won't be fast.

---

### Post by N'ko on 2015-05-23
Thank you for your help, I will accept your answer and do you want me to mark this thread solved?

---

### Post by Pilot6 on 2015-05-23
The solution is

```
sudo apt-get install git
git clone https://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo make install
```

Yep. It is solved. You are welcome.

---

### Post by Pilot6 on 2015-05-23
And which one did you test? First or second?

---

### Post by N'ko on 2015-05-23
I download the driver from link below and compiled the driver, I do not know if it was before or after you added a patch.
git clone [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)

---

### Post by Pilot6 on 2015-05-23
I did not add a patch there. OK it works with Larry's driver. Just accept my answer by clicking the "bird" at the left of it.

---

