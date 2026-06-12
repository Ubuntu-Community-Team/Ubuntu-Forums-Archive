---
title: "Problem installing nVidia 6600GT driver on ubuntu 8.10"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by mpolizz on 2008-12-27
Hi Everyone,
Earlier this week, I installed **ubuntu 8.10** on my home computer. I then attempted to activate drivers for my **nVidia GeForce 6600GT** graphics card. Everything appeared normal until I was prompted to restart my computer. Once restarted, ubuntu's graphical user interface failed to load. Instead, I was greeted with a black screen with a command-line login prompt. Before writing this request for help, I searched the web and the ubuntu forums for a solution. I found similar situations but none that matched my exact problem or a solution that worked. Also, my lack of experience on a linux machine does not help the situation :). Any help is very appreciated. To install my driver, I took the following steps:

1. System > Administration > Hardware Drivers.
2. A "Hardware Drivers" window pops-up, which states that, "No proprietary drivers are in use on this system."
3. The "Hardware Drivers" window lists three possible options to select from:
a] NVIDIA accelerated graphics driver (version 173)
b] NVIDIA accelerated graphics driver (version 96)
c] NVIDIA accelerated graphics driver (version 177)[Recommended]
4. I have tested each option and clicked the activate button.
5. The selected driver installs and ubuntu tells me to restart.
6. Upon restart, the GUI fails to load and I am given a command-line login prompt.

Thanks again for any help.

---

### Post by damis648 on 2008-12-27
Well, to get back to the GUI, login then enter in:
```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm restart
```
and you should be able to login graphically. Try this: open up a terminal (Applications>Accessories>Terminal) and paste in
```
sudo apt-get install envyng envy-qt
```
and enter. Once finished, go to Applications>System Tools>Envy and choose to install the nVidia driver. See if that works.

---

### Post by mpolizz on 2008-12-27
> **damis648 said:**
> Well, to get back to the GUI, login then enter in:
```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm restart
```
and you should be able to login graphically. Try this: open up a terminal (Applications>Accessories>Terminal) and paste in
```
sudo apt-get install envyng envy-qt
```
and enter. Once finished, go to Applications>System Tools>Envy and choose to install the nVidia driver. See if that works.
Thank you for the quick response. When I ran *sudo apt-get install envyng envy-qt* in the command line I got the following response:

matthew@matthew-desktop:~$ sudo apt-get install envyng envy-qt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envyng
matthew@matthew-desktop:~$

---

### Post by damis648 on 2008-12-27
Sorry, that should be
```
sudo apt-get install envyng-core envy-qt
```

---

### Post by mpolizz on 2008-12-27
Maybe I am doing something wrong, but I got the same message:

matthew@matthew-desktop:~$ sudo apt-get install envyng-core envy-qt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envy-qt
matthew@matthew-desktop:~$

---

### Post by damis648 on 2008-12-27
Sorry, I'm really out of it today. :popcorn:
```
sudo apt-get install envyng-core envyng-qt
```

---

### Post by taurus on 2008-12-27
Maybe you don't have all the repos enable in /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by damis648 on 2008-12-27
> **taurus said:**
> Maybe you don't have all the repos enable in /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

No, he does, I'm just really out of it. :popcorn: I forgot the '-core' on the first package and then the 'ng' on the second.

---

### Post by mpolizz on 2008-12-27
EvnyNG installed, but nothing occurs when I select it. I performed the following steps:

1. I selected Applications > System Tools > EnvyNG
2. My system prompted me for my password.
3. I entered it and nothing happens.

---

### Post by mpolizz on 2008-12-27
> **damis648 said:**
> Sorry, I'm really out of it today. :popcorn:
```
sudo apt-get install envyng-core envyng-qt
```
Re: Problem installing nVidia 6600GT driver on ubuntu 8.10
EvnyNG installed, but nothing occurs when I select it. I performed the following steps:

1. I selected Applications > System Tools > EnvyNG
2. My system prompted me for my password.
3. I entered it and nothing happens.

---

### Post by RJARRRPCGP on 2008-12-27
It's best to reformat and start over then choose the hardware drivers manager. Sorry. :(

Especially when new to Linux.

---

### Post by mpolizz on 2008-12-27
So far all past advice has failed. Can anyone confirm that nVidia GeForce 6600GT graphics card will work with ubuntu 8.10? Can anyone point me toward a solution? Should I install a different version of ubuntu or use a different graphics card?

Thanks:confused:

---

### Post by RatherGood on 2009-01-03
> **mpolizz said:**
> So far all past advice has failed. Can anyone confirm that nVidia GeForce 6600GT graphics card will work with ubuntu 8.10? Can anyone point me toward a solution? Should I install a different version of ubuntu or use a different graphics card?

Thanks:confused:



Same problem here. System won't load GUI after loading restricted drivers. Envy won't work, etc.

I'm using a 6600GT and a FX 5200 to run three monitors. Had no previous problems under 8.04.

---

### Post by Strelz on 2009-01-08
If you haven't yet solved this problem, try going to the Nvidia driver site, select the driver for your card, download it, and follow the instructions in the readme.  You have to get out of Gnome and into a terminal session to do this.  I had a problem similar to yours, and installing the proper Nvidia driver rathern than using the one provided by Ubuntu fixed the problem.

-Al

---

### Post by Strelz on 2009-01-08
deleted

---

### Post by Strelz on 2009-01-08
deleted

---

### Post by Strelz on 2009-01-08
Web page said I got an error so I clicked again, sorry.  Now I'm the one who needs help on how to delete a post.

---

### Post by bucketheadshot on 2009-02-04
> **damis648 said:**
> Well, to get back to the GUI, login then enter in:
```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm restart
```
and you should be able to login graphically. Try this: open up a terminal (Applications>Accessories>Terminal) and paste in
```
sudo apt-get install envyng envy-qt
```
and enter. Once finished, go to Applications>System Tools>Envy and choose to install the nVidia driver. See if that works.

hi, i am having the same except problem only i have 2 nvidia 8800gt gfx cards. i tried the first code and it did something then i tried the one that restarts gnome? and i was still at the cli login.

---

### Post by Jesper-L on 2009-02-05
Just want to say that i had the exact same problem also with gf6600gt. There is still one small chance that its related to my other hardware, but i dont think so.

If you are still following the thread - what motherboard do you have?

---

### Post by bucketheadshot on 2009-02-05
> **Jesper-L said:**
> Just want to say that i had the exact same problem also with gf6600gt. There is still one small chance that its related to my other hardware, but i dont think so.

If you are still following the thread - what motherboard do you have?

me? i have nforce 680i

---

### Post by Glyfada13 on 2010-12-03
Hello , I am new user in Ubuntu and as result i make an account in the forum.I have a problem with my Nvidia 6600GT drivers.I search for similar problems but I did not found something usefull.

I monitor is located more in the right side and as result I can not see the full icons.Also when I try to change the resolution I get a message which says: 

"It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"


Anyone to help me?The font size is very small and I want to kick it... :?

---

