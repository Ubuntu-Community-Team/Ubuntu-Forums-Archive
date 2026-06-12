---
title: "Grub not installing?"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by ojdon on 2009-11-10
Hey there, I'm currently on Windows 7 (home Premium 64-bit), which is on my main SATA Hard Disk. But I need to install ubuntu on my IDE Hard Drisk. So I downloaded the latest 64-bit version of Ubuntu (9.10) today and the installation process goes well up until 94% when I get a message saying that Grub cannot be installed, I've tryed installing with/without going through the process of testing it on the CD first as well. 

So I restarted my computer without the disc in to see what error message I get from GRUB and here is what I get: 

> 
GRUB loading.
error: no such disk
grub rescue>


Anyone know what the problem is here?

---

### Post by MichealH on 2009-11-10
Well you said Grub wouldn't install so obviously it is half-done could you please reinstall and see what happens.

---

### Post by ojdon on 2009-11-10
Already have, same issue. exactly at 94% again.

---

### Post by MichealH on 2009-11-10
Can you boot the live CD?

---

### Post by ojdon on 2009-11-10
Yeah, I've installed it through booting Ubuntu off the disc and just directly installing it. Still no luck.

---

### Post by MichealH on 2009-11-10
Ok then when you goto your live CD DO NOT INSTALL instead goto terminal and type in
```
sudo apt-get install grub-pc
```

---

### Post by MichealH on 2009-11-10
if that doesnt work try:

```
sudo apt-set upgrade grub2
```

---

### Post by ojdon on 2009-11-10
I've tried it but for both I get the result of:
> 
Reading package lists... Done
Building dependency tree
Reading state inforrmation... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by dhavalbbhatt on 2009-11-10
Try re-installing using the alternate installation CD. You can download that from Ubuntu website. I know there are a few issues with desktop installation CD. With the alternate installation CD, you will not have a GUI installater, but it will do the job of installing Ubuntu on your machine.

---

### Post by ojdon on 2009-11-10
I'll try that if the worst comes to the worst, or however the saying goes. I don't suppose GRUb is getting confused since I have Windows installed on a SATA hard drive while I have Ubuntu installed on a IDE hard drive?

---

### Post by ojdon on 2009-11-10
BUMP before this gets on the next page. Anyone else have another suggestion for a possible solution?

---

### Post by ojdon on 2009-11-10
Sorry for another post but is there a way of removing GRUB through ubuntu/terminal?  

I need to reburn the CD I think it says that there are two files missing just before installing/testing on the CD but I can't catch what files are missing.

---

