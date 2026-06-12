---
title: "Install Ubuntu 10.10 onto MSI CX420 and having black screen after fresh installation"
date: 2010-10-17
forum: Hardware
---

### Post by topgun889 on 2010-10-17
[COLOR=#000000][FONT=Times New Roman][FONT=arial]Hello, everyone,  

I am sharing with all of you about this issue and seeking a solution.

[/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][FONT=arial]on Oct 15, 2010,  [/FONT][/FONT][/COLOR][COLOR=#000000][FONT=Times New Roman][FONT=arial]I installed Ubuntu10.10 into a notebook which is MSI-CX420. (with Switchable Graphic, it means there are two display cards, one is integrated intel graphic card, another is (ATI 5471)ATI independent graphic card with 1GB., CPU: I3-330M, RAM: 4GB, HD: 320GB)

Firstly, I installed Windows7 and leave 70GB for the last logical partition.  Then I installed Ubuntu10.10 after installing Windows7.  

I met a problem then.  First, I installed Ubuntu10.10 with no problem using LiveCD, but when I tried to reboot right after finishing installation, I waited for over 5 minutes and system doing nothing.  So I forced shutting down notebook by just push the power-off button.  Then I could log in the Ubuntu10.10 again.  This was first problem. [/FONT][/FONT][/COLOR][FONT=Arial][SIZE=2]Why can't I decently reboot the Ubuntu on MSI-cx420 notebook?[/SIZE][/FONT]
[COLOR=#000000][FONT=Times New Roman][FONT=arial] 
Second problem, everything seemed going smoothly when I downloaded language pack, compiz application and display card driver, running Ubuntu10.10 . [/FONT][/FONT][/COLOR][SIZE=3][FONT=Arial][SIZE=2]But when I activated the display driver that Ubuntu suggests,[/SIZE][/FONT][SIZE=2][FONT=Arial]I can only get text mode when boot up the notebook[/FONT]. And moreover, [/SIZE][/SIZE][COLOR=#000000][FONT=Times New Roman][FONT=arial]when I tried to reboot the machine, it again couldn't automatically reboot.   I had to push the power-off button to force shutting down again.  Then I was able to turn on the notebook, however, I could only be able to log in in text mode instead of Graphic mode (I mean GUI mode).  This was the second problem.  [/FONT][/FONT][/COLOR][COLOR=#000000]How do I fix the problem of not get into the GUI mode?[/COLOR]
[COLOR=#000000][FONT=Times New Roman][FONT=arial] 
Does anyone of you have any clue of these problems that I met with?  What should possibly do with this?  Do you think that MSI-CX420 itself has hardware compatibility issue with Ubuntu10.10 system, which leads to not rebooting automatically after I clicked reboot button?
  

Please help.  I really appreciate it.
[/FONT][/FONT][/COLOR]

---

### Post by topgun889 on 2010-10-17
Hi,  It's topgun889 again.

Does anyone have any solutions for the issue?  

Two problems that I had on MSI CX420 while installing Ubuntu10.10.  

1.  [B]10.10 won't shut down on notebook.

2.  having black screen after activating the display driver in Ubuntu10.10, which means I could only get into text mode(tty) of Ubuntu.

Please help!!   
[/B]

---

### Post by topgun889 on 2010-10-24
Hi, everyone,  I figured out why this happened.  I did installation of Ubuntu10.10 the second time yesterday.  It worked well then.  So the first time when I screwed up was that I installed the additional drive of ATI/AMD FGLRX graphic driver.  After I installed that, I had this problem.  However, Ubuntu10.10 won't shut down on MSI-CX420 notebook.  I have to push the power-off button every time when I shutdown.(both using GUI way or typing 'sudo shutdown -h now' in the terminal.)  Does anyone know how to solve this problem?  I really need your help!!

---

### Post by Vermilion Sparrow on 2010-10-28
I have an MSI L1300, and with 10.04 I had random X crashes all the time. 10.10 isn't doing that, but it won't shut down, nor will it resume after suspend/hibernate.

There's a possible solution in [http://ubuntuforums.org/showthread.php?t=1594326](http://ubuntuforums.org/showthread.php?t=1594326) but I can't get the PPA (which I used with success in Karmic and Lucid) to install under Maverick, and I haven't had the time to try compiling the driver myself.

---

### Post by arghyaghosh on 2010-11-13
Hi,

I am new to ubuntu. I am using it for the first time. And I really need your help. I have a laptop having configuration : intel pentium processor p6100., 500GB HDD, 14 inch screen, 2GB ddr3 ram. 

The problem I am facing is ; I have chosen all of my disk space when I was installing Ubuntu. I followed everything I could : like having the dsl connection on thus the installation would include all updates and plugins. The installtion completed successfully.  But when I restarted my Laptop then it started in full screen terminal promt with the user I created.  I tried several times to get to the GUI screen by  command "startx", but the screen goes black / blank .  And after waiting 10/15 min I had to restart by pressing the power button.

Please help me to get to the GUI screen/mode.  Waiting for your valuable help. Thanks.

---

### Post by yclian on 2011-01-05
If you are on SG or IGD (duh?), the proprietary driver won't work - not until Linux supports graphical switching.

You do not need to do an uninstallation, do either:

 - Disable fglrx in your xorg.conf; or
 - Use IGD.

---

