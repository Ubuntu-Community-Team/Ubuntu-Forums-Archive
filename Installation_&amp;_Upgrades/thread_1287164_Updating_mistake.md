---
title: "Updating mistake"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by jlnortell on 2009-10-09
I have Ubuntu 9.04 kernel 2.6.28-15-generic installed on my laptop. I was trying to get my webcam to work and in another forum I read to make sure that the linux image was checked in Synaptic but I accidently checked the 2.6.28-15-server and now I can not boot into the GUI. Is there any way to reverse this?

---

### Post by wojox on 2009-10-09
Try:

```
sudo /etc/init.d/gdm start
```

See if that does anything

---

### Post by jlnortell on 2009-10-09
> **wojox said:**
> Try:

```
sudo /etc/init.d/gdm start
```See if that does anything

It says:

* Starting GNOME Display Manager                                          [ OK ]

The goes back to $

---

### Post by wojox on 2009-10-09
Okay how about:

```
sudo startx
```

---

### Post by jlnortell on 2009-10-09
> **wojox said:**
> Okay how about:

```
sudo startx
```


Ahh that gives me a new message

Fatal server error:
no screens found

---

### Post by slakkie on 2009-10-09
Looks like you are not the only one: [http://ubuntuforums.org/showthread.php?t=1286114](http://ubuntuforums.org/showthread.php?t=1286114)

---

