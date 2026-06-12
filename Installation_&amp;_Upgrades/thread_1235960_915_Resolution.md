---
title: "915 Resolution"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by gos1 on 2009-08-09
Hi ; 
 
  When I 
 
     ```
sudo apt-get install 915resolution
```

    In Ubuntu Jaunty Jackalope 
 
     I am getting this error message. 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 915resolution is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package 915resolution has no installation candidate
```



     How Can I install 915Resolution package ?  :???:

---

### Post by Mark Phelps on 2009-08-10
> **gos1 said:**
> How Can I install 915Resolution package ?  :???:

According to the page, the package was made for Hoary Hedgehog.  Unless you can find a newer package (one for Jaunty), you're most probably going to have to install from the source.

---

### Post by gos1 on 2009-08-10
I am taking a look at package from Google and really confused is there a Guide for me to be able to install it from source. And does the 915Resolution have an official home page ?

---

### Post by kerry_s on 2009-08-10
if you have a intel card the driver is intel and it should already be using it. look at the /var/log/Xorg.0.log
or
lsmod can tell you if its loaded.

---

### Post by gos1 on 2009-08-11
Nope it is not installed. I am using a MSI vr330 lap top with Nvidia graphics card and amd Sempron cpu .

---

### Post by kerry_s on 2009-08-11
> **gos1 said:**
> Nope it is not installed. I am using a MSI vr330 lap top with Nvidia graphics card and amd Sempron cpu .

so why are you trying to use a intel driver on a nvidia card?

---

### Post by 3rdalbum on 2009-08-11
Two things:

1. 915resolution is not needed anymore. Its functionality has been rolled into the Intel driver, and has been like that for some time now.

2. 915resolution never did anything useful unless you had an Intel graphics card.

Are you having a problem with the screen resolution on your Nvidia-based laptop?

---

### Post by gos1 on 2009-08-11
Yes I cannot use my graphic card in my Lap top And in ubuntuguide.org it says install the 915 resolution first . So What shall I do ?

---

### Post by kerry_s on 2009-08-11
> **gos1 said:**
> Yes I cannot use my graphic card in my Lap top And in ubuntuguide.org it says install the 915 resolution first . So What shall I do ?

did you activate the real nvidia drivers?

---

### Post by gos1 on 2009-08-12
How ? 
 
 Do I have to install NVIDIA drivers or just  have to activate them ? If just activation how ?

---

### Post by kerry_s on 2009-08-12
> **gos1 said:**
> How ? 
 
 Do I have to install NVIDIA drivers or just  have to activate them ? If just activation how ?

System->Administration->Hardware Drivers

the page hasn't been updated for 9.04, but should still be the same.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by robrist on 2009-10-31
> **gos1 said:**
> I am taking a look at package from Google and really confused is there a Guide for me to be able to install it from source. And does the 915Resolution have an official home page ?

I am in the same situation and I have an Intel 845G graphics card. So it seems I do need the 915resolution package to change the resolution.
How to get it, or work around it?
robrist

---

