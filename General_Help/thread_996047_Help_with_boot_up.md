---
title: "Help with boot up"
date: 2008-11-28
forum: General Help
---

### Post by ozweego5 on 2008-11-28
Ok so i installed ubuntu 8.10 on my girlfriends computer on my monitor and when i started ubuntu on her computer her monitor right before the gdm screen would load her monitor would say i need to change the resolution back to 1280 x 1024. I was wondering if i boot into the repair mode and drop to the command line, was there any line of code i could add to change it or defualt it to this monitor??? 
any help would be great!!!!:)

---

### Post by taurus on 2008-11-28
Try running this command from the prompt to see if it fixes the problem.

```
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by ozweego5 on 2008-11-28
ok thank you very much, I am actually not going to be able to fix this for like 2 weeks since it is at my GF's house and she is gone but i figured I would research it and get some help from the best support on the internet!!! you guys rock and I cant wait to continue spreading the word of ubuntu into the world as I am finishing up my college education in Computer science!  You guys rock and keep up the good work!!

Ozweego5

---

### Post by ozweego5 on 2008-12-14
ok that did not work it still says to change 1280x1024 @60Hz


any one else have any suggestions????   please and thank you!!

---

### Post by ozweego5 on 2008-12-14
i dont know were to start? I have never had this problem before, how do i change the resolution on the command line??

---

### Post by ozweego5 on 2008-12-15
bump, help me please or else I am just going to have to re-install it using her monitor to  try and avoid this problem

---

