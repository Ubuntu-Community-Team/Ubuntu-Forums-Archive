---
title: "System running hot at &gt;70deg C. How worried should I be?"
date: 2014-06-13
forum: Hardware
---

### Post by welshmike on 2014-06-13
My msi cr620 that I'm using to post this message runs hot. Please see Psensor image below. How worried should I be?

I've only noticed the hot temperature since replacing the HDD with a SSD but it may have been running hot with the HDD.
[IMG]http://www.hantsnwa.org.uk/Psensor.jpg[/IMG]

---

### Post by tgalati4 on 2014-06-14
Install *htop* and see if your CPU's are stuck.

Open a terminal:

```
sudo apt-get install htop
htop
```

---

### Post by welshmike on 2014-06-14
Thanks for your help.
Below is what htop shows.
I've only booted my laptop in the last hour or so and re-booted in the last 20minutes.
So maximum temperature is "only" about 53 deg C
Pulseaudio and Skype look suspect.
What do you think please?

[ATTACH=CONFIG]253946[/ATTACH]

---

### Post by tgalati4 on 2014-06-14
```
sudo killall skype
pulseaudio -k
```

Your screenshot is not showing.

---

### Post by welshmike on 2014-06-14
Thanks,
Screenshot was thumbnailed by (moderator?) QIII

---

