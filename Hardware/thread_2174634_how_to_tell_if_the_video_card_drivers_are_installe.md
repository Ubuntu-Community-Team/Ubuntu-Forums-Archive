---
title: "how to tell if the video card drivers are installed?"
date: 2013-09-15
forum: Hardware
---

### Post by iacoposk8 on 2013-09-15
Hello to all! I logged into my computer video card [Asus GT 620 (nvidia)]("http://www.asus.com/Graphics_Cards/GT6201GD3L/")
there are no drivers to install linux, but it often happens that things on linux and enter the range :)
how to tell if the drivers are installed or not?
I used these commands but do not know them decipher:
[B]
lspci | grep VGA[/B]
```
1:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 620] (rev a1) 
```

**sudo lshw -c display | grep driver**
```
configuration: driver=nouveau latency=0
```

---

### Post by VMC on 2013-09-15
What does 'lsmod' show

---

### Post by Yellow Pasque on 2013-09-15
```
driver=nouveau
```
You're using the open-source nouveau driver, which is okay for older cards, but is sorely lacking for newer ones (like gt620).
You probably want to install nvidia proprietary driver, but it depends on what version of Ubuntu you're running...

---

### Post by iacoposk8 on 2013-09-16
I'm using version 13.04 :)

---

### Post by iacoposk8 on 2013-09-18
you can install the driver for this card?
and how? thanks :)

---

### Post by Yellow Pasque on 2013-09-18
```
sudo apt-get install nvidia-313-updates
```

---

### Post by iacoposk8 on 2013-09-21
after installing the driver, if the launch commands in the first post I have this result:
```
lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 620] (rev a1)
sudo lshw -c display | grep driver
       configuration: driver=nouveau latency=0
```

---

### Post by Yellow Pasque on 2013-09-21
Consider blacklisting the nouveau driver: [http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html](http://www.dedoimedo.com/computers/ubuntu-ringtail-nvidia.html)

---

### Post by iacoposk8 on 2013-09-21
after installing the driver, if the launch commands in the first post I have this result:
```
lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 620] (rev a1)
sudo lshw -c display | grep driver
       configuration: driver=nouveau latency=0
```

---

### Post by deadflowr on 2013-09-21
Did you reboot the computer after installing the drivers?

If not, then reboot the system.

---

### Post by iacoposk8 on 2013-09-21
right! has now changed indeed!
now I read this:
configuration: driver=nvidia latency=0
it means that I'm using the latest drivers?

---

### Post by deadflowr on 2013-09-21
Did you end up blacklisting the nouveau driver or was it a simple reboot that did it?

And also, if the driver line says nvidia, then your using nvidia.
But that doesn't necessarily mean the latest nvidia driver.
There are a lot of nvidia drivers, I think they release a new one every month or so.
Take solace though, that even if the driver isn't the latest, it is still fully supported.

---

