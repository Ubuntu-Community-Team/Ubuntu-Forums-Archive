---
title: "Upgrade kernel to 2.6.19.1 with Macbook"
date: 2006-12-16
forum: Hardware &amp; Laptops
---

### Post by xoai on 2006-12-16
Does anyone succeed in upgrading kernel to 2.6.19.1 on Macbook? I have complied for 2 times, one with 2.6.19 and one with 2.6.19.1 but both of them does not work anyway. When I start my Macbook, it freezes at Ubuntu loading screen. I heard a small beep sound from inside. I think there is something problem with hardware?

---

### Post by pay on 2006-12-16
Does it still load the kernel that you had before?

---

### Post by lezig2laisilles on 2006-12-18
*sorry for my english but i'm french" So, I've finaly boot under 2.6.19.1 kernel with ubuntu on my macbook.
The support is really better (power management, smc, etc):D 
I used the .config which i found on the Gentoo How to.
The only problem is that the direct rendering is disabled ( however it's okay under 2.6.18&17 kernel) and without it I can't use Beryl.](*,) 
the .config for macbook (not pro) [http://gentoo-wiki.com/HARDWARE_Apple_MacBook/config]("http://gentoo-wiki.com/HARDWARE_Apple_MacBook/config")

If somebody can help me...

(one more time sorry for my very very VERY bad english":-# 

Goodbye,
Clément

---

### Post by xoai on 2006-12-19
Yes, it still loads other kernels.
Oh. it is really sad that we can't use Beryl with 2.6.19.1 >_<

---

### Post by gavin8or on 2006-12-23
Yeah I've found the same thing, it freezes at "waiting for root filesystems"

---

### Post by lezig2laisilles on 2006-12-30
YEAh:D  So i've got the 2.6.19.1 kernel with all mactel patches (sensor, rackpad etc) and beryl, the .config comes from the GENTOO how too. And I have added some modules and after many test => Beryl + a better kernel ( Boot in  25sec) + 2H30 of autonomy 
Wao ubuntu : I love you.

---

### Post by xoai on 2007-01-07
I have just installed 2.6.19.1 kernel on my Macbook but Beryl doesnt work. Hix. It loads but logout to console mode right after. And it always happens each time I login >< how did you make Beryl work with 2.6.19.1 kernel?

---

### Post by lezig2laisilles on 2007-01-24
Hello. to get beryl , I've compiled the kernel (many time lol). Finnaly I've had somme line at the gentoo's config. I can't remember the exact lines, and I think it's not the best but it working.
that is my .config (macbook core 1 Duo  1, 83ghz), but my printer can't work (however all my  other usb devices run perfectly (ipod, mouse....) :confused: )

---

