---
title: "Screen Resolution"
date: 2008-04-25
forum: Hardware
---

### Post by tckrockz on 2008-04-25
Finally i managed to install ubuntu 8.04 lts. but i cant use the screen resolution 1024x768 when i used ubuntu 6 and 7 it automaticly detected and used it. but i cant use it in ubunutu 8..i downloaded the driver and then it became worse it switched to 640x480..
i m using a nvidia geforce 6200...
any help?
what i meant by downloading is from here
[IMG]http://img170.imageshack.us/img170/1908/screenshothardwaredrivepf6.png[/IMG]

---

### Post by bbmak on 2008-04-25
i got the same problem. I am trying to adjust the xorg.conf now

---

### Post by DukeNuke2 on 2008-04-25
have you installed the nvidia-settings manager?

---

### Post by tckrockz on 2008-04-25
> **DukeNuke2 said:**
> have you installed the nvidia-settings manager?

nope i dint install anything from nvidia.any link?

---

### Post by DukeNuke2 on 2008-04-25
just install it with apt or aptitude or syaptic... which ever you use. i did it with commandline:

sudo apt-get install nvidia-settings

---

### Post by tckrockz on 2008-04-25
> **DukeNuke2 said:**
> just install it with apt or aptitude or syaptic... which ever you use. i did it with commandline:

sudo apt-get install nvidia-settings

i tired it but it switched to 600x480 now...
cant use the 1024 :S

---

### Post by jimhu on 2008-04-25
I've got the same problem.
Then I tried to install drivers from nvidia.cn(I'm a Chinese user), and the resolution became too high.

I'm using BenQ monitor 17' and Nvidia Geforce 7300GT

---

### Post by tckrockz on 2008-04-25
> **jimhu said:**
> I've got the same problem.
Then I tried to install drivers from nvidia.cn(I'm a Chinese user), and the resolution became too high.

I'm using BenQ monitor 17' and Nvidia Geforce 7300GT

i tired was envy...:(:(:(

---

### Post by samzhu168 on 2008-04-25
the "nvidia settings" just do not work as before, i checked the xorg.conf to find out that there is not "Monitor" subsection too, maybe this is the problem

---

### Post by tckrockz on 2008-04-25
> **samzhu168 said:**
> the "nvidia settings" just do not work as before, i checked the xorg.conf to find out that there is not "Monitor" subsection too, maybe this is the problem

whats the version of drivers ur using? i dont have that option :S

---

### Post by samzhu168 on 2008-04-25
> **tckrockz said:**
> whats the version of drivers ur using? i dont have that option :S

nvidia-glx-new
NVIDIA binary XFree86 4.x/X.Org 'new' driver 169.12

BTW, where are these function of 7.10 located in 8.04??

---

### Post by tckrockz on 2008-04-25
> **samzhu168 said:**
> nvidia-glx-new
NVIDIA binary XFree86 4.x/X.Org 'new' driver 169.12

BTW, where are these function of 7.10 located in 8.04??

i m using the same version but nothing helps :( i tired to use a older version lets see if it helps

---

### Post by derekaug on 2008-04-25
I'm having the same problems, which sucks... only I have two identical monitors, one it detects correctly at 1024x768 and the other it doesn't and set it to 640x480.

Thought maybe it was dependent on which connector it was connected to (the vga, or the vga through vga to dvi converter). Tried that, and still same issue. Meaning I tried the monitor that doesn't work in both connectors, restarted x, and each time detected as a crt monitor with a max res of 640x480.

Then tried the other one through each connector, restarted x, and each time it was correctly detected as 1024x768. It's making me think it's my other monitor that's the problem... but then again... in feisty, gutsy, windows, etc. it detected it fine.

I've submitted a bug report, [https://bugs.launchpad.net/ubuntu/+bug/221648](https://bugs.launchpad.net/ubuntu/+bug/221648), although so for it's pretty specific to my issues, maybe others can add there experiences.

---

### Post by frjcmaximilian on 2008-04-25
I am also having problems with screen resolution.  I installed Ubuntu 7.10 on my MacBook Pro via VMWare Fusion.  I had somehow set my screen resolution to 1280x960 (I think) and it was working fine.  Yesterday I upgraded to Ubuntu 8.04 (very slow, like 14 hours), and at first it kept my screen resolution as I had it.  Then suddenly it switched to 640x480 which is very small.  When I go to System>Preferences>Screen Resolution I cannot see the bottom of the new box to click "Save".  I have tried everything I know of to try to resize the box.  Admittedly, I am not all that tech savy, so I would really appreciate some help.  640x480 is too small of a screen.  Thanks

---

### Post by Curtisc on 2008-04-25
I had this same problem, with the "Hardware Drivers" box saying "not in use".  It turned out that when I enabled the driver, it actually gave up on downloading it because the servers are so overloaded right now.  The only thing I did was "sudo apt-get install nvidia-glx-new", but I had to do it over and over again before I could luck out and get into the queue (and that's with the Canadian servers, the US ones didn't respond at all).  Once the driver actually downloaded and installed, I just rebooted and I automatically had 1680x1050 (no nvidia-settings or anything required).

It's entirely possible that you guys have more serious problems, but maybe check and see if the nvidia driver is actually installed - it may not have finished downloading due to the server overload.

---

### Post by Malfet on 2008-04-25
> **Curtisc said:**
> 
It's entirely possible that you guys have more serious problems, 

Looks like it's a general problem with NVidia and 8.04
[http://ubuntuforums.org/showthread.php?t=766515](http://ubuntuforums.org/showthread.php?t=766515)

---

### Post by Kaploink on 2008-04-25
I had the same resolution problem with the Nvidia drivers.  I could only go to 640-480 max. I finally fixed it by running "sudo displayconfig-gtk" from a terminal and selecting the correct monitor. Apparently in my case, Ubuntu did not detect the monitor.

---

### Post by samzhu168 on 2008-04-25
maybe i find out a solution:
1, switch to recovery mode from the grub menu
2, use the command: dpkg-reconfigure xserver-xorg, it will let u select many options, i just enter the default but the screen resolution i select 1024x768.
3,reboot to normal
4,enable nvidia driver(reboot)
5,I got 800x600, do not worry, go system-preference-screen resolution, turn to 1027x768, then log out, got 1027x768.
6, go system-administration-nvidia X-server-settings, u can use, for me,1440*900, 1280*800. BUT, when i log out,it will back to 1024*768, every time i need do the 6th step to use 1280*800 since i get a widescreen. if anybody can help with this??

PS. yesterday i even got the 1400*900 in nvidia X-server-settings, but now it's gone, so bad.

---

### Post by masticate on 2008-04-25
See my solution in the following thread.

[http://ubuntuforums.org/showthread.php?t=765581](http://ubuntuforums.org/showthread.php?t=765581)

---

### Post by tckrockz on 2008-04-26
I reinstalled ubuntu few mins ago and everything seems to be working fine yayy....

---

### Post by 79spitfire on 2008-04-28
I got mine fixed. I had to run nvidia-xconfig as root, then edit the resulting xorg.conf and add:

```
Modes  "1280x1024"
```

To set my monitor resolution correctly. Nvidia-xconfig wrote a more "Normal" looking xorg.conf than the one that came with Ubuntu.

---

### Post by anc2020 on 2008-08-10
> **Kaploink said:**
> I had the same resolution problem with the Nvidia drivers.  I could only go to 640-480 max. I finally fixed it by running "sudo displayconfig-gtk" from a terminal and selecting the correct monitor. Apparently in my case, Ubuntu did not detect the monitor.

This worked, thanks a lot!

---

### Post by pietjanjaap on 2008-08-11
With ubuntu 8.04, dpkg-reconfigure xserver-xorg is not the same anymore, now you can install your keybord and more with this.
But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the "Try to fix X-server",
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.
Then reboot and install your videcard driver.(i use envy for this).

---

