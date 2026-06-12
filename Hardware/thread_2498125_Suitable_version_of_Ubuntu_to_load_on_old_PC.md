---
title: "Suitable version of Ubuntu to load on old PC"
date: 2024-05-31
forum: Hardware
---

### Post by garvind25 on 2024-05-31
Hi,
   
    I have an old desktop (assembled) and wanted to try out Ubuntu on it. My hardware config is as below:
   
  Intel Q6600 processor (Core 2 Quad series)
  Gigabyte G41 mobo
  4 GB DDR 3 1333MHz RAM
  1TB HDD (600 GB free)
   
   Pls suggest an appropriate version of Ubuntu to load on this PC.  
   
  Thanks,
  Arvind Gupta

---

### Post by deadflowr on 2024-05-31
Any Ubuntu will be fine, depending on how much more you would want to get out of it, probably Xubuntu or Ubuntu mate will give a little more pop.

Any sluggishness will be because of low RAM (4GB is on the lower side these days),
and whether or not the HDD is a spinning drive or solid state drive.

---

### Post by garvind25 on 2024-05-31
Thanks for your reply. 

I have not heard of Xubuntu or Ubuntu mate. Can you pls give me a few details about them. And how to select the UBuntu version pls?  

My aim of using UBuntu is to reduce heating of my CPU. Someone told me that using UBuntu will reduce the thermal load on my CPU. Is that true? Presently my CPU is getting very heated (its hitting 80 degree celcius!)

I plan to run open source EDA tools towards electronic designing on Ubuntu install.

> **deadflowr said:**
> Any Ubuntu will be fine, depending on how much more you would want to get out of it, probably Xubuntu or Ubuntu mate will give a little more pop.

Any sluggishness will be because of low RAM (4GB is on the lower side these days),
and whether or not the HDD is a spinning drive or solid state drive.

---

### Post by deadflowr on 2024-05-31
> I have not heard of Xubuntu or Ubuntu mate. Can you pls give me a few details about them. And how to select the UBuntu version pls?
You can check them out yourself.
On this very page go up top to the section Ubuntu Community.
It's a dropdown with links to all the Ubuntu flavors.

---

### Post by ajgreeny on 2024-05-31
Also have a read through [https://ubuntuforums.org/showthread.php?t=2415676](https://ubuntuforums.org/showthread.php?t=2415676) which gives lots of details about all the different versions.

---

### Post by Yellow Pasque on 2024-05-31
> **garvind25 said:**
> My aim of using Ubuntu is to reduce heating of my CPU. Someone told me that using Ubuntu will reduce the thermal load on my CPU. Is that true? Presently my CPU is getting very heated (its hitting 80 degree celcius!)

The first thing I would look at is CPU usage in Windows. Unless something has all your CPU "pegged" at 100% use, it shouldn't be hitting 80C (and even then..)
When was the last time you cleaned out the heatsink? Have you considered removing it and redoing the thermal material?

---

### Post by garvind25 on 2024-06-01
Thanks for your reply.
 
 Yes, yesterday itself I cleaned my CPU fan and heatsink before redoing the thermal paste. Prior to it, the CPU was hitting 90 degree celscius.
None of the software installed in my Windows PC is taking the whole CPU. However when I run my browser Mozilla FireFox ESR, it takes 60% of the memory. CPU is engaged to 30%.
I have a core 2 Quad Q6600 with 4GB DDR3 RAM and 1 TB SATA HDD. My heatsink and fan are properly connected. Due to old hardware, I am presently using Win 7 32 bit. This restricts my RAM choice to 4GB and use of Mozilla FireFox ESR edition.
 
Also, can you pls suggest any Winn 7 based web browser which will take less RAM?
 
Regards,
Arvind Gupta

---

### Post by garvind25 on 2024-06-01
> **ajgreeny said:**
> Also have a read through [https://ubuntuforums.org/showthread.php?t=2415676](https://ubuntuforums.org/showthread.php?t=2415676) which gives lots of details about all the different versions.

Its nice of you to point me towards the thread. I came to know a lot more about other Ubuntu distributions. I suppose Lubuntu would be a decent choice for old hardware as in my case. Can you/ someone confirm if it will reduce my processor heating issue. Presently, during max usage, my processor is hitting 80 degree celscius. I plan to use open source EDA tools on the Ubuntu install.

Regards,
Arvind Gupta.

---

### Post by Yellow Pasque on 2024-06-01
> **garvind25 said:**
> Can you/ someone confirm if it will reduce my processor heating issue?

Your processor shouldn't be getting to 80C, even if all the cores are running at full use, no matter what OS you are using. To me, it sounds like a hardware problem (insufficient cooling) if you're still hitting 80C after cleaning/reapplying the heat sink. 
But if you want to see how Lubuntu runs, download it, put it on a USB stick and try it out. Even if it doesn't solve your CPU temp, you should probably still use it. Windows 7 has been EOL (End of Life) over 4 years now and is insecure.

---

### Post by guiverc on 2024-06-01
All [Ubuntu *flavors* are really just Ubuntu systems]("https://ubuntu.com/desktop/flavours"), with the primary difference being different packages included on a default install, which largely change the GUI (desktop/WM/DM) and apps. As such I'd expect rather similar experience between them all, esp. in dealing with the hardware (*though I do note differences with graphics hardware I'm ignoring for now*). 

The oldest device I currently use in QA (*Quality Assurance testing*) is a 2005 HP Compaq, though I've increased its CPU so its now a c2d-e6320  (core 2 duo) making it somewhat similar. The only c2q's I have are a little higher spec'd (q9400) but most of those are pretty equivalent in most regards, esp. in relation to the OS being used in my experience.

Lubuntu is the *lightest* flavor of Ubuntu *out of the box* (ie. if used as provided, without any changes), with Xubuntu the second *lightest*... but personally I think that's a near-pointless stat, as almost no-one uses their system without making changes... esp. adding apps.

If picking a *flavor*, I'd consider what apps you'll use, esp if RAM is limited (5GB or less), as Lubuntu uses the LXQt desktop thus will run well if using Qt5 apps, Xubuntu uses the Xfce desktop which is GTK3/4 and will run well if using GTK3/4 apps (*gtk3 for most; Xfce is only just moving to GTK4 but you didn't provide release details*)... but this really only impacts RAM.

To ensure good performance, you want apps & desktop to share resources, otherwise you can cause extra work on the machine, as RAM needs to be swapped out to disk etc.. but this will generally be noticed by lagging, and not temperature.

The temp. issues you're alluding to I'd blame on hardware... Sure some CPUs have variations in they can't handle some instructions as well as others, but again that's usually evidenced in lag and not excessive heat.

Something I do consider in what I'd run is the GPU or video hardware...  as the release being used has great influence on the kernel options you have (LTS have two main choices; GA + HWE), and I have found some older GPUs or video hardware perform best when older kernel stacks are used; as older kernels mean older kernel modules (kernel modules being commonly called *drivers*).  I have noted some Desktops have fewer issues than others on older hardware in regards graphic glitches, with Xfce/Xubuntu usually the last to cause me to swap out video card in my QA test hardware (*where the hardware is mostly used for install testing.. thus I don't want to be bothered by graphic glitches.. Lubuntu being second last impacted incidentally*).

---

