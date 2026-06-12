---
title: "No Sound after accident restart!!"
date: 2009-03-04
forum: Hardware
---

### Post by KaMii on 2009-03-04
I recently installed ubuntu 8.10 interpid...and it detected all my hardwares automatically including sound card... i have been hearing sound perfectly...

but then yesterday, ubuntu locked due to some reason and i had to hit the power button to restart...

upon restart, there was no sound...

it has my sound card detected still...i also do not see volume control at the panel..

what should be the cause??

---

### Post by linux_tech on 2009-03-04
First check all settings, make sure nothing is muted
Gnome-alsamixer is easier to use than alsamixer. Try installing and running it it first
```
sudo apt-get install gnome-alsamixer

``` 
To open gnome-alsamixer type


```
gnome-alsamixer

```

---

### Post by KaMii on 2009-03-04
ah... stupid me!!

it was actually master muted!!!


thanks alot man...

---

