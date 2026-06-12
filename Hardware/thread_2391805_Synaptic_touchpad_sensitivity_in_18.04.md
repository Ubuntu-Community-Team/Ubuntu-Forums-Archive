---
title: "Synaptic touchpad sensitivity in 18.04"
date: 2018-05-13
forum: Hardware
---

### Post by johnrobert2 on 2018-05-13
Have been having trouble with my touchpad since upgrading to 18.04 from 14.04: the cursor freezes in mid-move or fails to move when I start moving my finger. I'm guessing this has to do with finger sensitivity settings.

In this forum I've found instructions for adjusting the touchpad finger sensitivity but they're not working for me. Looking at xinput -list-props doesn't reveal any sensitivity settings I can change. I also tried just running xinput --set-prop 12 "Synaptics Finger" and the system responded that this property doesn't exist.

Back in 14.04 I was able to use synclient to smooth out the touchpad operation but now synclient isn't available from the repositories anymore.

So, the question: Is there a way to adjust the sensitivity using libinput driver, or failing that, can I reinstall the synaptic driver so that I can regain access to synclient?

---

### Post by johnrobert2 on 2018-05-13
Okay, solved it. I just had to install the synaptic touchpad driver using

sudo apt install xserver-xorg-input-synaptics.

I was worried that things would break but everything is fine and the problem's solved.

---

### Post by chantroikhatvong on 2018-05-17
I have same problem but after i install xserver-xorg-input-synaptics that all ok but Ctrl+F3 can not dibable touchpad. How fix???

---

### Post by wildmanne39 on 2018-05-17
Hello and welcome to the forum chantroikhatvong, please start your own thread to receive support and you can link back to this one if you believe it will help someone solve your issue. The OP of this thread is also a new member so it is very unlikely they can help you if they return here.

Thanks

---

### Post by aruninterval on 2018-11-09
I was facing the same problem.

I just had to install the synaptic touch pad driver using:
```
sudo apt install xserver-xorg-input-synaptics
```

And then restart the Computer. The touch pad works perfectly now. The sensitivity is as it should be.

---

