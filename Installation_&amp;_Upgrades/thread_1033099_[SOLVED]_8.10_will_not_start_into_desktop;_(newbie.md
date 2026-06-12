---
title: "[SOLVED] 8.10 will not start into desktop; (newbie)"
date: 2009-01-07
forum: Installation &amp; Upgrades
---

### Post by bmarshall on 2009-01-07
I have a good Compaq EVO computer that has had Debian and Ubuntu 7.10 loaded on it for the past year. Today I have tried desperately to load Ubuntu 8.10. Both the 'Live' CD as well as the install fail to enter the desktop after I log in. I saw the desktop during install and I let the partition manager do a clean 'whole disk' partitioning. The 'UBUNTU" logo is normal before LOGON and LOGON works. I have tried the kernel 'restore' mode and everything. The resolution it tries is 1024x768. What have I done wrong? When I try to repair a bad distro it tries to upgrade and load a lot of files from the web.

Can anyone direct me to someone who can help? I really want to learn Linux.

---

### Post by halovivek on 2009-01-07
Welcome to Ubuntu fourms.
While boot up can you see the older kernal versions list?
try to select previous version of kernal while boot up.
can you post full configuration of your system?

---

### Post by bmarshall on 2009-01-07
Thank You Halovivek

No, there is only the one kernel number.(2.6.27-7-Generic). The three entries are there (+MemTest). The 7.10 was working fine yesterday morning; I could try 8.04 and see if that works. It does not seem as if other people have install problems. Could my hard disk have gotten corrupted during partitioning? It just seems to stop with either a black or the orange-yellow background with a white mouse arrow.

---

### Post by jimv on 2009-01-07
It's having issues with your video card.  What kind of video card do you have?

You can boot into rescue mode and type "lspci | grep VGA" to check.

---

### Post by bmarshall on 2009-01-07
Thank You Very Much for Your Help, Jim; I am really trying.

Please explain to me a little clearer as I am a newbie. I went to the Recovery menu and found the BASH prompt.  entered the command you gave me.
[email]root@xxxxx.deskto[/email]p:~# Ispci | Grep VGA
bash: Grep: Command  Not Found
bash: Ispci: Command Not Found

---

### Post by dadozgb on 2009-01-07
> **bmarshall said:**
> Thank You Very Much for Your Help, Jim; I am really trying.

Please explain to me a little clearer as I am a newbie. I went to the Recovery menu and found the BASH prompt.  entered the command you gave me.
[email]root@xxxxx.deskto[/email]p:~# Ispci | Grep VGA
bash: Grep: Command  Not Found
bash: Ispci: Command Not Found

It mean that a) you don't have l(it's letter L)spci installed and b) you wrong typed "Grep". Linux "understands" big and small leters so if you writte Grep it is not the same as grep 'cause it "thinks" that you need a command named Grep not grep.

---

### Post by DeMus on 2009-01-07
> **bmarshall said:**
> Thank You Very Much for Your Help, Jim; I am really trying.

Please explain to me a little clearer as I am a newbie. I went to the Recovery menu and found the BASH prompt.  entered the command you gave me.
[email]root@xxxxx.deskto[/email]p:~# Ispci | Grep VGA
bash: Grep: Command  Not Found
bash: Ispci: Command Not Found

It's not Ispci, but lspci (small letter l, like in like)
It's not Grep but grep. Linux is case sensitive so when you need to type small characters you really have to type small characters.

Try it.
DeMus

---

### Post by bmarshall on 2009-01-07
Good News! I found in the Recovery Menu page an "F4 - Safe Graphics Mode" and I was able to boot the live CD into a Desktop.

I think that now all I need to do is reprogram the start-up for 800x600. When I had 7.10 on this computer I used a higher resolution with no problem and I didn't use any special drivers. But things change. I will try to get specs on the graphics chip, I believe it is run-of-the-mill Intel.

---

### Post by dadozgb on 2009-01-07
> **bmarshall said:**
> Good News! I found in the Recovery Menu page an "F4 - Safe Graphics Mode" and I was able to boot the live CD into a Desktop.

I think that now all I need to do is reprogram the start-up for 800x600. When I had 7.10 on this computer I used a higher resolution with no problem and I didn't use any special drivers. But things change. I will try to get specs on the graphics chip, I believe it is run-of-the-mill Intel.

Hmm. Maybe you used framebuffer device and wasn't aware of? Never mind. If your gui worked on 7.10 it should be working on 8.10. Just sit tight and relax.  :-)

---

### Post by bmarshall on 2009-01-07
Thank You again, you have helped a lot.

Sorry about the errors. I entered the command and got this reply:
Graphics: Intel 82845G/GL (Brookdale-G)

---

### Post by dadozgb on 2009-01-07
> **bmarshall said:**
> Thank You again, you have helped a lot.

Sorry about the errors. I entered the command and got this reply:
Graphics: Intel 82845G/GL (Brookdale-G)

Can you google it to find out is there some/any problem with this graphics and ubuntu 8.10?

---

### Post by bmarshall on 2009-01-07
At root prompt in Recovery I tried to open 'gedit /etc/X11/xorg.conf'. It replied 'Gtk-Warning** Cannot open display:'.

---

### Post by dadozgb on 2009-01-07
> **bmarshall said:**
> At root prompt in Recovery I tried to open 'gedit /etc/X11/xorg.conf'. It replied 'Gtk-Warning** Cannot open display:'.

You can't use gui programs from console. And gedit is program that needs gui. You can use midnight commander as mc if you have it or simply use vim. And why do you edit xorg file ? You can also do dpkg-reconfigure xserver-xorg. It's I belive easyer.

---

### Post by bmarshall on 2009-01-07
Found this bug notice in launchpad.net

Bug: 257807
USPLASH RESOLUTION
(reported by: mansur)

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/257807](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/257807)

COULD this be the problem with mine? (I noted that it says the resolution didn't work for them.)

The LOGON screens are normal though!

I also have a CRT monitor and 1 Gig of memory. (?)

---

### Post by dadozgb on 2009-01-07
> **bmarshall said:**
> Found this bug notice in launchpad.net

Bug: 257807
USPLASH RESOLUTION
(reported by: mansur)

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/257807](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/257807)

COULD this be the problem with mine? (I noted that it says the resolution didn't work for them.)

The LOGON screens are normal though!

I also have a CRT monitor and 1 Gig of memory. (?)
You got me really confused.. This thread is about usplash.. and in your case.. what is not working? Splash image or x server?Splash image has nothing to do with X server. You can deinstall a splash package but you X server (gui) will work..

---

### Post by bmarshall on 2009-01-07
Thank You 'dadozgb' for the suggestion, but, that was a lot of education about keybords, but not Graphics.

---

### Post by dadozgb on 2009-01-07
> **bmarshall said:**
> Thank You 'dadozgb' for the suggestion, but, that was a lot of education about keybords, but not Graphics.
I will really like to help you but I just don't understand you. Is there a problem with a X server or with a splash image? I first belived it was with X server and now I'm not really shure.

---

### Post by bmarshall on 2009-01-07
I am sorry! I am just trying to get a Desktop image to appear after the LOGON. I found that when I entered Safe Graphics Mode in 800x600 resolution that the live CD would boot into a Desktop. I do not know what a 'splash' is or an 'x-server' either; but I want to learn. It is difficult to practice what I learn with a Linux computer that does not boot.

No one here is more confused as to what is happening here then me. I just cannot understand why 7.10 and Debian worked on this machine and not 8.10.

---

### Post by dadozgb on 2009-01-07
> **bmarshall said:**
> I am sorry! I am just trying to get a Desktop image to appear after the LOGON. I found that when I entered Safe Graphics Mode in 800x600 resolution that the live CD would boot into a Desktop. I do not know what a 'splash' is or an 'x-server' either; but I want to learn. It is difficult to practice what I learn with a Linux computer that does not boot.

No one here is more confused as to what is happening here then me. I just cannot understand why 7.10 and Debian worked on this machine and not 8.10.

Ok. X server is gui (graphical user interface) on linux. This is a program in which you configure your graphics card, mouse, keyboard and monitor. It has nothing to to with you icons etc. It just use your display hardware as you told him so by loading your display driver, keyboard driver etc. To display your icons linux use a window manager like icewm or desktop environment like gnome or kde. The major differnece is that desktop enviroments can have independent environment than a system by default ie. you use in system english but in your d.e. turkish by default and they are much hardware consuming than a window manager.I don't know why your comp won't boot, I have no clue, but if you wont to learn something about linux a best start point is a bunch of various howtos to strart with along with manual pages accessd with man ls ie typed in terminal. There is no fast learning in linux. It will probably be hard for you if you go this way but if you will be persistant you will eventually understand how things are working in linux. It may seem very confused and hard to understand but it is not. for me understanding windows is much much harder task.
Internet is full of information on a various aspects of linux and here is a good link for x server. Much better explaind than I can do.
[http://en.wikipedia.org/wiki/X-server](http://en.wikipedia.org/wiki/X-server)

---

### Post by bmarshall on 2009-01-07
OK. Thank You again for the explanation.

When I searched with google, I found out a few things:
There is no driver for the Intel graphics, it should work with the install, (which it does not). There are also many people with graphics problems using the same Intel Graphics chip, when they loaded 8.10.

I have been told I need to get the /var/log/xorg.o.log file and have someone look at it it for error. I do not yet know how to do that. I have also been told that I will need to edit the /etc/X11/xorg.conf file to remove video resolutions that may be causing my problem. I have already backed up the xorg.conf file. Can you recommend a file editor that I can use?

Now you are telling me I need to edit the x-server file(s). This I will do first.

When I have a working Linux machine I will start to learn. I may have to return to 7.10 in order to have a working machine. This is something I do not want to do.

---

### Post by dadozgb on 2009-01-07
> **bmarshall said:**
> OK. Thank You again for the explanation.

When I searched with google, I found out a few things:
There is no driver for the Intel graphics, it should work with the install, (which it does not). There are also many people with graphics problems using the same Intel Graphics chip, when they loaded 8.10.

I have been told I need to get the /var/log/xorg.o.log file and have someone look at it it for error. I do not yet know how to do that. I have also been told that I will need to edit the /etc/X11/xorg.conf file to remove video resolutions that may be causing my problem. I have already backed up the xorg.conf file. Can you recommend a file editor that I can use?

Now you are telling me I need to edit the x-server file(s). This I will do first.

When I have a working Linux machine I will start to learn. I may have to return to 7.10 in order to have a working machine. This is something I do not want to do.
 As I saw this graphics chip should use i810 driver which is shiped with x server I belive. So in your /etc/X11/xorg.conf should be written Driver "i810"
Before you edit it try sudo dpkg-reconfigure xserver-xorg and choose this driver if it doesn't do it for yoz. Maybe it isn't installed so maybe you will have to install it from console. You have to have working net connection and than sudo apt-cache search xserver and sudo apt-get install the one with i810 in it.Install midnight commander. You will probably find it most usefull. The command for it is mc

---

### Post by bmarshall on 2009-01-08
I have found the problem, it was not an ubuntu problem.

First, I thank you dadozgb, you have really imparted good knowledge and several excellent ideas to me. I also have a deep respect for all the people who have spent hours writing working code so that we can enjoy Linux, they are heroes!

When I examined the xorg.conf file, it was basically empty. The info that was there had no clear definition as to what it was. The xorg.0.log file also had no default resolutions listed. I surmised that the CD installer was not able to sense the graphics card/monitor during the installations. Sure enough, my son had placed a High Definition Video Interface on my monitor cable to watch Hi-Res video and the installer could not properly sense the monitor. After removing the adapter & replacing a suddenly failed DVD/RW drive (?) I have been able to install and run 8.10. I will report this thread as solved.

---

### Post by sonnysk76 on 2009-01-08
I have the same problem, but maybe different cause, I install 8.10, 

when I turn on the PC, grub  ok,  
then the screen go black ( no slash screen, and no text wile loding )  After  a time the logon screen appears, no problem in this,

After logging in the screen turn brown with the mouse pointer on it, and noting else, no wallpaper.  and also the kaybord dont work.

Tomorrow I will install a grafic card to see if this is the problem. I have installed and reinstalled like 3 times, hope this work.

---

### Post by dadozgb on 2009-01-09
> **sonnysk76 said:**
> I have the same problem, but maybe different cause, I install 8.10, 

when I turn on the PC, grub  ok,  
then the screen go black ( no slash screen, and no text wile loding )  After  a time the logon screen appears, no problem in this,

After logging in the screen turn brown with the mouse pointer on it, and noting else, no wallpaper.  and also the kaybord dont work.

Tomorrow I will install a grafic card to see if this is the problem. I have installed and reinstalled like 3 times, hope this work.

When you boot linux press ctrl-alt-F1 to see boot messages. Your X server doesn't working for some reason. Switch to console with ctrl-alt-F1 and try to reconfigure your server.

---

