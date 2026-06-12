---
title: "Laptop graphics problem"
date: 2012-08-11
forum: Hardware
---

### Post by Doj on 2012-08-11
Hi,

I'm not sure if here's the place to post this. I have an old (2006ish) Packard Bell laptop with Windows XP and Lubuntu on it. The graphics card is an ATI Radeon XPRESS200M 5955 with 128mb graphics ram.(other specs: 1GB ddr ram, AMD turion64 1.8GHz single core cpu) I have 2 queries:

1: A while ago I tried playing GTA San Andreas on it using Wine, but couldn't get it to do anything because the graphics were completely messed (menu had black background and blocks where each letter should've been. Also, the loading logos were just black.) I also had a similar problem with a native game (Bloboats, which now works fine) and NFS UG2 on wine. GTA SA works fine on Windows on this machine, and on another AMD desktop with a Nvidia GPU.

2: Another thing about the laptop is I now have to run Lubuntu on it as the newer Unity desktop runs quite slowly (probs about 5 fps to open the unity dash) when Gnome2 ran perfectly fluid even with some hectic animations on it. Overall the performance has dropped substantially. Lubuntu runs fine, but it has small irritations about it.

So my question: Do you think it has to do with the graphics drivers and would the continued work with the open source AMD graphics drivers eventually sort either of the problems?

The laptop has other issues like soft sound, but I won't go into that here.

Thanks a lot
Jodie

---

### Post by Doj on 2012-08-12
Bump.

---

### Post by Doj on 2012-08-14
Bump

---

### Post by Doj on 2012-08-16
Ok, nudda bump. Maybe this'll break soon.

---

### Post by Doj on 2012-08-18
2 more bumps and I'll give up.

---

### Post by TenPlus1 on 2012-08-18
You could try installing the actual Ati binary and see if that helps with your graphics, but it could just be that your card is too slow to run the game properly...

To install binary open a terminal window and type these commands:

sudo apt-get install fglrx fglrx-amdcccle

sudo aticonfig --initial

now reboot and see if your gfx are any better, if not then go to terminal and type this to remove drivers:

sudo apt-get remove --purge fglrx fglrx-amcccle

...and reboot to return to open-source drivers...

---

### Post by Doj on 2012-08-20
Thanks, I will try these when I get home. What's funny is when I installed GTA SA and Need for speed U2 on windows, they worked fine...

---

### Post by typhoon_tip on 2012-08-20
When playing 3D games, open the ATI/AMD Panel, go to 3D advanced settings, and force "Wait for vertical refresh" in 3D always off. Make sure also "Tear free" is off when playing 3D games. Then enjoy your games at insane FPS... :guitar:

---

### Post by mastablasta on 2012-08-20
> **Doj said:**
> Thanks, I will try these when I get home. What's funny is when I installed GTA SA and Need for speed U2 on windows, they worked fine...
 
i hope you didn't do that before chekcing if ATI drivers can actually work on your card. i doubt they can: 
 
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
 
and you will make a mess in your system using them 
 
what windows? XP? they are from 2001. ATI drivers worked fine on old Ubuntu as well. 12.04 is form 2012 (so 11 years later...)
 
if (and i think it did in this case) ATI/AMD dropped support for your card you are stuck with opesource drivers and would have to work with what you've got or move back to windows where ATI/AMD might still be supporting this chip. with some chips they work great, others not so much. you can try the xorg edgers PPA to update them to latest version.

---

### Post by Doj on 2012-08-20
Thanks for the help guys, but after reading up on the subject for quite a while, looks like support for my chipset has been dropped even in the open source drivers for quite a while, which explains why the laptop was so good at running Ubuntu up till 8.10, but sucks now...

Looks like I'll just have to get a job and buy a replacement sometime... :)

Now do I mark this as solved or what? (and how? Also, how do I see my posts when I log in as opposed to browsing down the pages for them?)

Thanks again...

---

### Post by mastablasta on 2012-08-21
> **Doj said:**
> Thanks for the help guys, but after reading up on the subject for quite a while, looks like support for my chipset has been dropped even in the open source drivers for quite a while, which explains why the laptop was so good at running Ubuntu up till 8.10, but sucks now...

 
no, as you can see in my link the card is still supported by opensource drivers. in fact i have ati rage 16MB that is still supported (no 3D hw accelleration though).
 
> 
Now do I mark this as solved or what? 

Thread tools in the upper right corner of the thread and then chooose mark thread a ssolved (not that it is really solved....)
> 
(and how? Also, how do I see my posts when I log in as opposed to browsing down the pages for them?)
 
 
top right corner of forums and click search. then you can select to find your threads (the topics you started) or all your posts (even to other peoples topics).
Thanks again...[/QUOTE]

---

