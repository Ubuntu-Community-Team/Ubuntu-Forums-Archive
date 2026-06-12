---
title: "Where does PowerManagement save battery experience?"
date: 2009-02-10
forum: Hardware
---

### Post by zxmon21 on 2009-02-10
I am using Ubuntu 8.10 on a Fujitsu Siemens Lifebook S7020. My battery was good when I installed Ubuntu first. Since then it's gotten MUCH worse. Not because of Ubuntu, it just got worse over time.

When I look at the Power Management "Power History", the graphs there make very little sense. I assume that Power History is based on experience from previous charge / discharge cycles while Ubuntu was running.

I would like to reset the Power History "experience", so that it can learn to predict my "crappy" battery.

I have tried to google for "ubuntu power management experience", but obviously that's not the right keyword :)

Do you know where Power Manager saves its discharge data? How should I search to find this on the net?

Thank you for your help!

---

### Post by EricDB on 2010-04-06
I'd love to know, too.

---

### Post by pedro.nariyoshi on 2011-03-12
I found them at /var/lib/upower/

To reset ALL the histories, try

```
sudo rm /var/lib/upower/*
```

---

### Post by zxmon21 on 2011-03-14
Cool, thanks for that!

Even though I asked the question quite a long time ago, I was still looking for this bit of info. This helped me a lot!

---

### Post by StuartZ on 2011-10-18
Thank you. Same here.  Just installed a new battery, and it was going to hibernate in 4 minutes after charging it.

---

