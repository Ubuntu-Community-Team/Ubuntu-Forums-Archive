---
title: "Nvidia + Compiz + Unity very slow and choppy performance."
date: 2012-04-01
forum: Hardware
---

### Post by shivamkalra on 2012-04-01
Hello,
I started using Linux last year and left windows since then. I've university issued laptop which chnages every year, this we have got Lenovo T-520, with i7 and Nvidia NVS 4200 m graphic car. I installed the ubuntu recently and felt that it was way too laggy and choppy in terms of switching or draging windows and even sometimes watching videos.

Everything was fine, until I installed Nvidia drivers from x-swat/xupdates ppa and changed the bios settings to discrete graphic only. I need Nvidia support for some Matlab related work I have to do, even with choppy performance Matlab seems to run faster.

I the performance gets much much better when I switch to ubuntu 2D but unfortunately there is no window positioning and docking support in 2D. I tried all the hack and tricks posted online but nothing seems to work? Any ideas or help would be appreciated.

Thanks,
Regards
Shivam kalra

---

### Post by Curious00 on 2012-05-11
Yes, I have serious concerns about the build quality of the Unity plugin overall. One thing that is glaringly obvious, is that Compiz crashes when unloading and loading plugins, and this happens only when the Unity plugin is enabled. 

I have also noticed what you have, here.. Over time, with more and more programs running, Unity will slow the framewrate of Compiz effects like the "wobbly windows" to where the experience is quite choppy. Unload Unity, and all of a sudden, everything is as smooth as butter again.

You know, you can run compiz alongside of "Ubuntu 2D", right? Just type at a terminal window:

```
compiz --replace &
```

You can probably place this command line as a startup program, too.

Then you'll probably want to disable the "unity" plugin using CCSM (otherwise you'll have the translucent Unity taskbar overshadowing the ordinary Ubuntu 2d taskbar).

---

### Post by pquinnet on 2012-05-17
I have 10.10 running with Compiz full blown with nVidia 8300 and it works great.  New hard drive and new install of 11.10 and Compiz is very problematic. Compiz-check shows "GNOME as my Composite Manager and COMPIZ won't run."  I installed the [RECOMMENDED] nVidia drivers. If I do "compiz --replace ccp &", the terminal window just shows running log lines, warnings and won't return to prompt. Windows decorations go away and windows stick in upper left corner. I have to reboot to get control back but without Compiz.  CCSM is installed and setup.  I have tried everything GOOGLING this problem has suggested. Using a DELL VOSTRO 200. But again a 10.10 install works like a charm.

---

### Post by Cavsfan on 2012-05-17
If you are up to it, here is a manual way of updating the nVidea driver. Version 295.53 just came out yesterday.

There is a link to download the driver, a link with instructions on how to remove the old driver and install the new one 
and a 3rd link which you will need to do. It is a How to in this forum that creates a script to install the driver into any 
new kernel that gets installed in the future.

I suggest using this manner to get your updates so you can see what is going on and whether the driver gets installed into a new kernel:
A very knowledgeable friend in this forum **ranch hand** calls Update Manager Update Mangler.
He told me to always use these commands to get my updates:

```
sudo apt-get update
sudo apt-get upgrade
```If there is anything held back like a new kernel install this will get that:
```
sudo apt-get dist-upgrade
```Here is the link to install the new driver:

[[COLOR=blue]_http://ubuntuforums.org/showthread.php?t=1948062_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1948062")

---

### Post by Cavsfan on 2012-05-17
shivamkalra, I am not sure if your card is supported but, you can check here:

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

