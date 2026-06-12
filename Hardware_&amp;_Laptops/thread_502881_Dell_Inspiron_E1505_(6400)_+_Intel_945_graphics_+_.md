---
title: "Dell Inspiron E1505 (6400) + Intel 945 graphics + Ubuntu  7.04"
date: 2007-07-17
forum: Hardware &amp; Laptops
---

### Post by nick.inspiron6400 on 2007-07-17
Hi,

I decided to give Ubuntu another try, and I am stuck with the graphics! I installed Ubuntu 7.04 via Wubi. I can't get my screen resolution any higher than something that is very low!

I checked and I do have the 915 resolution installed, but it does not seem to work. I removed it, and then I had to re-install.

Please help me!

Thank you.

Nick.

---

### Post by skirkpatrick on 2007-07-17
I have a 6400 that I setup for dual-boot using the normal installation method.  I installed 915resolution and it just seemed to work.  I can try to help out but since I never had a problem, it may take a little bit :)

---

### Post by kiv on 2007-07-17
I have installed Ubuntu on the same machine that blonged to a friend - didn't have any problems either.

I will look in to it for you and try and help!

---

### Post by nick.inspiron6400 on 2007-07-18
Hey guys!

Wow! Well I geuss I am a unlucky person, maybe the fact I am using Wubi might be the problem. I will download the ISO and install it.

I sure hope that it works! Thanks for your help anyway!

Nick.

---

### Post by walkerk on 2007-07-18
in a terminl do this to load the intel-driver..
```
sudo apt-get install xserver-xorg-video-intel
```

should do the trick!

---

### Post by nick.inspiron6400 on 2007-07-18
Thank you for all your help! 

I installed the 915resolution and it works!

---

### Post by jemfisher on 2007-09-25
Many Thanks as well, I was very dispondent I bought this Dell for my Mom and it looked  dire without the correct driver.

Jem..

---

