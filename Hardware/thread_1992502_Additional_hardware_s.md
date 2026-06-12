---
title: "Additional hardware :s"
date: 2012-05-31
forum: Hardware
---

### Post by G R E E N on 2012-05-31
update :
ok so after a long struggle i came across 2 main issues

first one: when i download the nvidia shell from their site and all goes well it boots into :

[IMG]http://img96.imageshack.us/img96/5179/screenshotfrom201206031.png[/IMG]

the resolution becomes so big and i am unable to navigate i have to delete my xorg config and remove nvidia !



Second : after blacklisting some stuff and whatnot i finally got there in my additional hardware 
but i am unable to use them because each time i try to activate it it gives me an eror
[IMG]http://img26.imageshack.us/img26/4259/screenshotfrom201206052.png[/IMG]






--------------------------------------
OLD ISSUE :
i am having issues using my nividia VGA as the main graphics card
when i try to launch additional hardware it gives me no hardware to identify 


here is my lspci
```
abdallah@abdallah-Inspiron-N5110:~$ lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev a1)

```

[IMG]http://img27.imageshack.us/img27/904/screenshotfrom201206010.png[/IMG]

---

### Post by G R E E N on 2012-05-31
hallbb me

---

### Post by G R E E N on 2012-05-31
added picture

---

### Post by G R E E N on 2012-06-01
anyone help me ???????????????

---

### Post by CatKiller on 2012-06-01
It's not polite to bump a thread more than once a day.

If your laptop is using Optimus (which Nvidia refuse to support on Linux) then you'll probably want to check out Bumblebee. Installing the proprietary driver will break your graphics completely, so it's probably good that you didn't.

---

### Post by G R E E N on 2012-06-02
how ?

---

### Post by Yellow Pasque on 2012-06-02
> **G R E E N said:**
> how ?
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by G R E E N on 2012-06-05
still nothing i tried many ways but no luck at all

---

