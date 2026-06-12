---
title: "Gutsy on Thinkpad T60p"
date: 2007-10-25
forum: Hardware &amp; Laptops
---

### Post by softtower on 2007-10-25
============ UPDATE ==========================
Thanks to p2im0, he wrote a nice tutorial on how to solve it:
[http://ubuntuforums.org/showpost.php?p=3683760&postcount=24](http://ubuntuforums.org/showpost.php?p=3683760&postcount=24)
============================================

I noticed quite a few people installed Gutsy 7.10 on their ThinkPad T60p laptops. How did I notice? Because a lot of them are complaining about suspend/hibernate feature not working due to the bug in ATI video driver.

My question is not about that. I am asking how did you manage to put Gutsy on T60p **AT ALL**? Mine has ATI FireGL v5250 video card, and regardless of installation option (I tried regular CD, alternate CD, safe graphics mode) I always end up with X errors shown to me in a super-super-super low resolution screen, something like 320x200.

I never get a chance to work the command line. The resolution is so low that nothing fits on the screen except maybe for one sentence. I cannot even see what I type.

I reported the bug here:
[https://bugs.launchpad.net/ubuntu/+bug/155918](https://bugs.launchpad.net/ubuntu/+bug/155918)

Does anyone have this issue?

---

### Post by cow_racer on 2007-10-25
Did u try to install fglrx and fglrx-control?  Once that's installed, 

After that..

sudo aticonfig --initial

Reboot.  You should get the right solution..

---

### Post by softtower on 2007-10-25
As I said - I don't even get to use the command line. There is nothing I can do but stare at messed up screen and turn the power off.

Switching to "parallel consoles" does not work either - video mode is messed up everywhere. 

I will repeat: there is no "text mode" when installing Gutsy on my T60p. I cannot use command line.

---

### Post by kleeman on 2007-10-25
Does alt-f2 work?
Or is there an option to boot into (recovery mode) when you first switch on?

---

### Post by shomati_sen on 2007-10-26
Look at [http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_Feisty_Fawn_on_a_ThinkPad_T60p](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_Feisty_Fawn_on_a_ThinkPad_T60p)

You need to download the fglrx driver, it seems to me.

The key instructions are:
    *  Be sure to have a *wired* network connection ready (wifi will not work yet)
    * Download a ubuntu 7.04 feisty fawn image from ubuntu.com
    * Boot from the CD, and wait ... the installation will break down when attempting to start the graphical part of the installation (X). 
    * apt-get update
       apt-get install xorg-driver-fglrx fglrx-control
       depmod -a 
    * restart X with /etc/init.d/gdm restart
    * If X doesn't launch, try changing the Driver in /etc/X11/xorg.conf from "vesa" to "fglrx", then restart X.

Hope this helps,

Shomati

---

### Post by softtower on 2007-10-26
shomati_sen, please read what I was saying. I repeated myself 3 times already: I do not have command line to type commands in and follow tutorials with. I have installed ATI driver many times in the past, I am not asking *how* to install it. I am asking how do I get to command line when installing Gutsy on T60p and video fails.

kleeman, yes Alt+F2 works - it switches me to another console, but the video mode is still screwed: I can see about 40 characters on the screen in 4 lines, with cursor and command line way way way down, invisible. So i can do "clear" and then type something, but I cannot reconfigure X this way - there isn't enough real estate in this weird video mode to acocmodate standard 80x25 text console.

Recovery mode? Is there a hotkey I can press during booting process? By itself it does not offer me to boot into recovery mode. 

Still looking for a solution and help is appreciated. I do not mind living without Standby/Hibernate, but my friend put Gutsy on his T61 and I *love* improved font rendering, something most people did not even notice.

---

### Post by wsduvall on 2007-10-26
It might be possible to install Ubuntu 7.04, and then immediately do an update. My roommate has the same problems you do, but he has given up on Ubuntu, and is now using OpenSUSE :(. Hope you get it working, Thinkpads are nice machines.

---

### Post by sum][one on 2007-10-26
so i'm not the only one here...

I''m on t60p ... and I have ubuntu since breezy ... upgraded to 7.04 with no problems at all ...

upgraded last night to 7.10 ... problems.

BLACK screen at boot (I hate splash.. hence I always used vga=794 in my menu.lst) .. now it just DONT work except with splash...

ALT+Fx (consoles) just gives me black screen .. 
Xorg wont start at any higher resolution other than 640x480 ... and after "configuring" it i'm on 1600x1200 until next reboot (with a sort of dunno driver though) 

the usual "build packages from binary, compile, install" apparently works.. but then no fglrx module loaded.

I installed ATI driver (the manual way) since EVER .. cause they are the only truly working with serious 3D apps, which is my job though.... 

I simply cant manage to install ATI drivers now ... 

I realized that the problem relies on the new kernel... old 2.16.20 still works at boot time (vga=794)... I just cant install drivers right now cause I'm at work .. and my laptop doesnt have internet connection here.. and I'm missing the headers.. (crap me) ... I'm pretty sure the problem is within the kernel.. I'll give a try with 2.16.20 tonight when on internet .. If it'll works.. i'll let you know for sure.. (and I'm positive about this)

but.. I guess I'm having the same problem as -softtower- have... 

any help is really appreciated.

cheers

---

### Post by tristan@Ubuntu on 2007-10-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/122328](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/122328) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi,

I'm experiencing similar problems after the upgrade (sorry I don't have a solution for the install problem) on a T60p:
 - kernel 2.6.22-14 does not boot, I have to use 2.6.20-16. 
 - My BigDesktop setting make X to crash. I have to use a simple setup (one screen)
 - Graphic performances are really bad. No 3D, very slow... I can't watch a DVD anymore
 - Only the flgrx driver works. ati & radeonhd crashes. 
 - If I use glx-server, I obtain the slowest computer of the world...

I think that our problem is a combination of graphic card driver (fireGL V5250) and kernel incompatibilities...

So far, the gutsy upgrade was not a good idea.

-Tristan

---

### Post by sum][one on 2007-10-26
> **tristan@Ubuntu said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/122328](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/122328) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
[...]
So far, the gutsy upgrade was not a good idea.

-Tristan

so far, so true.. 

I'll check tonight with 2.16.20 and hopefully I'll get my laptop working again .. but yet again .. damn me and my "always last release" attitude...  I was so positive after the Brezzy Feisty upgrade... it went slick and easy...

---

### Post by nandaiyo on 2007-10-26
This is how I got Gutsy to install on my T60p

1. Boot off liveCD
2. Select Install with Safe Graphics option, then press F6
3. In the command line at the end, remove quiet and change splash to nosplash
4. Press enter and start the install.
5. The screen will start flashing - let it flash until the error message appears that it will try again in 2 minutes. **At this time you have a 2-minute window to enter in everything**. If you don't get it all done in time, don't worry, you'll just need to go through the screen flashing+ error message again. 

6. Hit enter a few times (about 10-14) until you can see the prompt on the screen. The prompt is there, but because the screen res is so screwed up, you won't see it since the bottom of the "screen" is about 10-14 lines below your visible view.
7. Enter the following:
> $sudo apt-get update
$sudo apt-get install -y xorg-driver-fglrx

If at any time you can't see the prompt and are wondering what's going on, just hit Enter a few times to scroll the screen up.

> $sudo depmod -a
$sudo aticonfig --initial
$sudo aticonfig --overlay-type=Xv

That's it. You may have to hit enter a bunch of times to make sure you can see that what you typed is correct because it'll be offscreen. Then you wait until the 2 minute timer is up and it starts flashing your screen again. This time, however, it should work.

The annoying thing is the 2-minute timer. And the fact that Ubuntu hates ATI. You will have to repeat this process after you install Gutsy and reboot for the first time.

---

### Post by nandaiyo on 2007-10-26
When you run Gutsy for the first time it will repeat the flashing and error. Just hit CTRL + ALT + F2 and login to get to a prompt, then repeat the process above. Keep in mind that you may be prompted to enter your password more than once so keep hitting Enter to see what's going on offscreen.

---

### Post by softtower on 2007-10-27
Wow! :-) Thank you! I will definitely try this out once I have time to play around (since my laptop is my workhorse)

BTW: does anyone know why is this happening? Why wouldn't it switch back to text mode if X isn't working?

---

### Post by sum][one on 2007-10-27
well I seriously hope I dont have to reinstall everything actually ... I upgraded from Feisty and I've got a complete setup laptop that I wont loose cause of a graphics problem ... 
my main problem about text mode is ... with new kernel I've got no text mode at all ... ALT+CTRL+Fx just gives me black screen .. only way to have text mode is booting the 2.16.20 kernel ... 
btw last night I didnt managed to go on with tries (too many beers) but I've managed to get Xorg less pissed and now at least I got rid of the segfault when launching "fglrxinfo" ... now I've got MESA .. which sound promising at least :) ... 

anyone solved the blank textmode issue?



just out of curiosity .. why Live CD lets me run text mode resolution up to 1600x1200 and with grub I cant have that resolution?.. max I have so far after MANY tries is 1280x1024 .. any idea what's the setting liveCD uses to go to 1600?

---

### Post by InfinityCircuit on 2007-10-27
> **nandaiyo said:**
> This is how I got Gutsy to install on my T60p

1. Boot off liveCD
2. Select Install with Safe Graphics option, then press F6
3. In the command line at the end, remove quiet and change splash to nosplash
4. Press enter and start the install.
5. The screen will start flashing - let it flash until the error message appears that it will try again in 2 minutes. **At this time you have a 2-minute window to enter in everything**. If you don't get it all done in time, don't worry, you'll just need to go through the screen flashing+ error message again. 

6. Hit enter a few times (about 10-14) until you can see the prompt on the screen. The prompt is there, but because the screen res is so screwed up, you won't see it since the bottom of the "screen" is about 10-14 lines below your visible view.
7. Enter the following:


You'll have to hit Y + enter a few times blindly, because the Y/N prompt is off the screen. Just hit Y+Enter a few times.



That's it. You may have to hit enter a bunch of times to make sure you can see that what you typed is correct because it'll be offscreen. Then you wait until the 2 minute timer is up and it starts flashing your screen again. This time, however, it should work.

The annoying thing is the 2-minute timer. And the fact that Ubuntu hates ATI. You will have to repeat this process after you install Gutsy and reboot for the first time.

To make this easier, you should probably apt-get install -y xorg-driver-fglrx.  This way you won't have to worry about hitting "Y" many times.

---

### Post by derjusti on 2007-10-27
THANX! helped a lot after the alternate install!

---

### Post by sum][one on 2007-10-27
problem solved.... 
fought for two days against ATI drivers... installed version 40 .. worked straight away.
obviously 41 or 42 doesnt support FireGL ... 

:D

gutsy up and running!

---

### Post by fishtoprecords on 2007-10-28
> **tristan@Ubuntu said:**
> 
 - kernel 2.6.22-14 does not boot, I have to use 2.6.20-16. 
 - Graphic performances are really bad. No 3D, very slow... I can't watch a DVD anymore
 - Only the flgrx driver works. ati & radeonhd crashes. 
 - If I use glx-server, I obtain the slowest computer of the world...


I agree. I had a happy T60P with Fiesty, did the upgrade, and it wouldn't boot. You have to kill the 22-14 kernel. I have acceptable performance with flgrx, only after I uninstalled gl-x-server

Plus my system won't read either CF cards or my Nikon camera.

I was an early adpoter, that was a really bad idea.

---

### Post by nandaiyo on 2007-10-29
> **InfinityCircuit said:**
> To make this easier, you should probably apt-get install -y xorg-driver-fglrx.  This way you won't have to worry about hitting "Y" many times.

Thanks InfinityCircuit... I'll update the commands. :)

---

### Post by tristan@Ubuntu on 2007-10-30
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Regarding the kernel problem, it is now well documented:

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653)

Though, that might not concern every ATI graphic card. For sure, I can't boot 2.6.22 with an Mobility fireGL V5250.

---

### Post by blackrim on 2007-10-30
> **softtower said:**
> shomati_sen, please read what I was saying. I repeated myself 3 times already: I do not have command line to type commands in and follow tutorials with. I have installed ATI driver many times in the past, I am not asking *how* to install it. I am asking how do I get to command line when installing Gutsy on T60p and video fails.

kleeman, yes Alt+F2 works - it switches me to another console, but the video mode is still screwed: I can see about 40 characters on the screen in 4 lines, with cursor and command line way way way down, invisible. So i can do "clear" and then type something, but I cannot reconfigure X this way - there isn't enough real estate in this weird video mode to acocmodate standard 80x25 text console.

Recovery mode? Is there a hotkey I can press during booting process? By itself it does not offer me to boot into recovery mode. 

Still looking for a solution and help is appreciated. I do not mind living without Standby/Hibernate, but my friend put Gutsy on his T61 and I *love* improved font rendering, something most people did not even notice.

Finally! I too have been having this problem with the T60p and am very interested in any solutions. Keep the thread alive.

---

### Post by allent on 2007-10-30
I also have a ThinkPad T60P, and cannot get beyond the graphics problem.  Everything goes OK until it tries to autodectect the graphics, and it then, depending on the version of Ubuntu either gets stuck in a loop, where the screen goes black at intervals, or it ends up in an ultralow resolution mode with a handfull of characters taking up the entire screen.  I tried 6.10, 7.04 and 7.10, as well as the alternate CD with no luck.  I am getting pretty exasperated - 6.10 worked well enough on my old Thinkpad I was going to make it my primary OS on the new.  Has anyone come up with a solution yet?

---

### Post by nandaiyo on 2007-10-31
allent, have you tried the suggestion on post #11  on page 2? Let us know how it goes... it's frustrating I know, but it can be done :)

---

### Post by p2im0 on 2007-11-01
> **cow_racer said:**
> Did u try to install fglrx and fglrx-control?  Once that's installed, 

After that..

sudo aticonfig --initial

Reboot.  You should get the right solution..

This is exactly what you have to do to get past the initial graphical problem.  The only tough part about it is that you can't see whats going on and when the ati-driver has finished installing.

I used a combination of two terminals (ALT+ F2 & ALT+ F3) used the the **CLEAR** command to completely clear the screen so I could see as much as possible.

First of all make sure you're hard-wired and have the internet working check by using: ```
ifconfig
```

In console #1 run: ```
sudo apt-get install xorg-driver-fglrx
```

Now, you're not going to see everything you want to see, so wait a few seconds and it will prompt you to install the package.  Type "**Y**" and hit "**enter**."  You won't see anything happening here, but to check and be sure apt-get is actually running go to console #2 and type:
```
sudo apt-get update
```
You should get an error saying it can't get a lock on the PID file.  That's good, it means the driver is installing.  I gave it about 10 minutes, tried running "apt-get update" again and didn't receive the error.

Now clear the screen and run in either console:
```
clear
sudo depmod -a
```

Now configure xorg.conf to use the FGLRX driver:
```
sudo aticonfig --initial
```

Now set the overlay for ATi Cards:
```
sudo aticonfig --overlay-type=Xv
```

Now restart GDM.  I had to do this a couple times as it failed instantly the first time:
```
sudo /etc/init.d/gdm restart
```

Now you should be in.

Let me know if this works!  This is my first "helpful tutorial-ish" post on these forums.  I've used them so much I feel I needed to contribute with something I got working.


-P2iM-0

---

### Post by blackrim on 2007-11-01
worked for me, in order to see i just booted in safe mode. doesn't try to boot the graphics so i get a normal terminal

---

### Post by beetlejelly on 2007-11-01
thanks, I've got my t60p up and running now.:)
I have the wide screen model and was wondering if anyone has gotten the correct resolution for the screen to work? My resolution tops out at 1280 x 1024.

---

### Post by p2im0 on 2007-11-01
I have the Widescreen version as well.  Did you follow my steps from the post above?  My resolution is set to 1680x1050 by default.  I've yet to have to change it.
-P2iM-0

---

### Post by boxrec on 2007-11-01
Instructions above worked for me as well, widescreen and resolution is fine. Noticed a couple of things :
although  4GB installed only 3GB are detected
system monitor reports about 30% cpu usage when machine is idle

---

### Post by softtower on 2007-11-05
I suspect that "3GB detected" is normal for 32 bit OS. The upper 1GB is probably used by the kernel. On Windows, any process can only access 2GB max by default.

---

### Post by boxrec on 2007-11-12
after following the previous instructions I brought up a terminal and 

sudo apt-get install xserver-xgl

logged out and back in, idle load is down and compiz is working great :-)

---

### Post by tristan@Ubuntu on 2007-11-14
boxrec, what is your graphic card?
Can you paste your lspci?

Thanks

---

### Post by boxrec on 2007-11-14
sure :-

VGA compatible controller: ATI Technologies Inc M56GL [Mobility FireGL V5250]

---

### Post by tristan@Ubuntu on 2007-11-15
Thank you boxrec. We probably have the same laptop, but mine does not work. The main difference is probably that I did an dist upgrade from fiesty, not a fresh install, which would mean that I probably have some old fiesty configuration that does not work under gutsy. My problems are:
- kernel 2.6.22-14 does not boot
- server-xgl does not work properly (very very slow and buggy)

Otherwise the laptop runs with 2.6.20-16 and flgrx alone.

aaaa.....

---

### Post by Fire_Chief on 2007-11-15
> **boxrec said:**
> Instructions above worked for me as well, widescreen and resolution is fine. Noticed a couple of things :
although  4GB installed only 3GB are detected
system monitor reports about 30% cpu usage when machine is idle

This is due to the kernel you are running...just as in 32-bit Windows, 32-bit Linux will only reference 3GB of RAM by default. To see more than 3GB, you have to enable PAE (Physical Address Extension) in the kernel. The easiest way to do this in Ubuntu is to install the version of your running kernel that is labelled BIGSMP. It's okay to install an SMP kernel on a non-SMP machine. The BIG part of that name is the indicator that the kernel has PAE support enabled.

---

### Post by xlillo on 2007-11-18
Hello,
think u have some screwed bios settings. I junst fired 7.10 CD into the laptop, and only that useless fingerprint stuff is not working.

---

### Post by semaj3000 on 2008-03-21
Just a side note. I installed ubuntu today on my IBM T60p with the v5200 card 256mb and ubuntu seems to operating flawlessly so far.  I am just working on how to get the opensuse rpms from lenovo to work on ubuntu, as well as the fingerprint reader and dual screens. If anyone needs my config info tell me how to get it and I will post it. Just make sure you message goes to my email since i don't frequent here yet much.

---

