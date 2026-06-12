---
title: "Changing resolution after install"
date: 2008-12-11
forum: Installation &amp; Upgrades
---

### Post by scoobydoo518 on 2008-12-11
Is it possible to change from 1024 x 768 to 1400x900 after installing 8.04? I cannot get install to use greater than 1024x768. If I install nVidia drivers(nVida 6800 card) can I then change to higher resolution?
Or am I outta luck?

Thanks

---

### Post by howefield on 2008-12-11
The nvidia drivers should give you access the range of resolutions that your card supports.

You might want to install nvidia-settings after enabling the nvidia driver.

In terminal type

```
sudo apt-get install nvidia-settings
```

And run with gksu, in terminal type

```
gksu nvidia-settings
```

---

### Post by scoobydoo518 on 2008-12-11
> **howefield said:**
> The nvidia drivers should give you access the range of resolutions that your card supports.

You might want to install nvidia-settings after enabling the nvidia driver.

In terminal type

```
sudo apt-get install nvidia-settings
```

And run with gksu, in terminal type

```
gksu nvidia-settings
```

Thanks. I'm gonna give it a try now!

---

### Post by scoobydoo518 on 2008-12-11
> **scoobydoo518 said:**
> Thanks. I'm gonna give it a try now!

It worked! Thanks

---

### Post by howefield on 2008-12-11
No probs, glad you are sorted :)

---

### Post by icanfly0307 on 2008-12-11
Could you mark this thread as Solved? That would help others. :)

---

