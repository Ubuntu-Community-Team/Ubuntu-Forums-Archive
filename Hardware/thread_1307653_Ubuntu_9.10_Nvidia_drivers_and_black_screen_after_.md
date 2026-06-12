---
title: "Ubuntu 9.10 Nvidia drivers and black screen after reboot"
date: 2009-10-31
forum: Hardware
---

### Post by mokojin on 2009-10-31
Hi

So i just instaled Ubuntu 9.10 and activated the restricted driver that the ubuntu notification system just recommended for my Nvidia card, rebooted and nothind happenend, got a black screen.

Any thought how i may be able to recover my desktop?

Graphic card: Nvidia Geforce 9800gtx


Thanks

---

### Post by Alfons81 on 2009-11-01
Hi,

I had the same problem as you using an Nvidia GeForce 8400M GT and running Ubuntu Karmic 9.10 beta. The problem appear when I tried to run the most recent Nvidia driver 185. Then apeared the black screen on boot, I solved it reinstalling and choosing the driver 173. 
Actually I'm yet using the recent driver 185 and it's working ok.

I hope it help to you.

---

### Post by spedoinkle on 2009-11-04
same problem here. using nvidia 8800gts sli. this also happened when i was using 9.04 and 8.10 ubuntu. this restricted driver bug has followed me through 3 generations of ubuntu. i really would like to get this fixed so i can once more use compiz fusion.

this is exactly what i did every time over and over. install ubuntu, activated the nvidia restricted driver. (newest one required me to close x server, which i did) restarted the system, and poof x server wont open. before i would get crash errors, now it just gives me a big blank screen of blackness.

here is the same problem, tried all the fixes, none of them worked:

[https://answers.launchpad.net/ubuntu/+source/xorg/+question/68054](https://answers.launchpad.net/ubuntu/+source/xorg/+question/68054)

[http://www.linuxforums.org/forum/ubuntu-help/96770-solved-ubuntu-loads-blank-screen.html](http://www.linuxforums.org/forum/ubuntu-help/96770-solved-ubuntu-loads-blank-screen.html)

[https://answers.launchpad.net/ubuntu/+question/7901](https://answers.launchpad.net/ubuntu/+question/7901)

[http://www.techenclave.com/open-source-and-linux/ubuntu-black-screen-after-installing-nvidia-142804.html](http://www.techenclave.com/open-source-and-linux/ubuntu-black-screen-after-installing-nvidia-142804.html)

[http://ubuntuforums.org/showthread.php?t=410708](http://ubuntuforums.org/showthread.php?t=410708)

if there is a fix out there please help, otherwise here's a bunch of links to try and find the solution.

---

### Post by spedoinkle on 2009-11-04
ooooooooooooooook. so this just blew my mind. this is exactly what i did. i installed the 64 bit of ubuntu this time. i heard that driver 173 was working so i applied it. well, it worked, kind of. it worked terribly and there was no way to change the resolution. so i removed it using the hardware drivers application. i decided it was time to give driver 190 another shot. i did the usual thing. stopped xserver using:

sudo /etc/init.d/gdm stop

i went to the area where the driver was located and ran:

sudo sh NVIDIA-Linux-x86_64-190.42-pkg2.run

i rebooted expecting to see the evil black screen of doom. it never happened, i am writing on a system now using driver 190 successfully. i think it must have something to do with an error within jockey, the driver device and when i installed 170 successfully it left something that i was missing before from when i tried installing driver 190 previously. i have a feeling jockey has been screwing up alot and that's why i haven't been successfully installing the nvidia drivers. i don't know, i hope all of this helps...

---

### Post by nedflenders on 2009-11-08
I had similar issue when upgrading from 9.04 to Ubuntu 9.10.
I have a GeForce 9800 GT video card.

A quick fix to get video to work properly is to change your nvidia video driver in your xorg.conf to "vesa" then "startx" (I use KDE)

Section "Device"
    Identifier     "Device0"
#    Driver         "nvidia"
    Driver         "vesa"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GT"
EndSection

I then uninstalled the new nvidia drivers(185) and installed the older version 173.

sudo rmmod nvidia
sudo aptitude remove --purge nvidia-glx-185 nvidia-185-libvdpau nvidia-185-kernel-source
sudo aptitude install nvidia-glx-173 nvidia-173-kernel-source nvidia-173-modaliases

Make sure to edit your xorg.conf file and replace your driver back to nvidia.
reboot your computer.

Unfortunately, the removal of the nvidia 185 drivers will have some dependency issues, so I had to uninstall mythtv and a few other software.

I will probably try and install the 185 drivers when there is a new revision, until then, I think this will do just fine.

FYI

# uname -a
Linux myserver 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

---

### Post by kc5hwb on 2009-11-14
I upgraded to 9.10 this week and when I did, my screen resolution was HUGE.  I ran the Hardware Drivers utility from System->Administration and it showed it was running version  185.  So I downgraded to 173 just now, rebooted and it is worked great, my resolution is back where I like it, at 1680x1050.  Maybe I will try to jack with the new 190 later, but for now 173 works fine.

---

### Post by komodo-tux on 2009-11-15
@nedflenders Thanks for the clear insructions.  Worked for me.

---

### Post by GolemdX on 2009-11-15
This happened when I installed ATI Catalyst on an unsupported card. I didn't realize the problem at first, but booting into recovery mode on an install CD and removing it from there also works great.

---

### Post by Enginator on 2009-11-15
I had the same problem, but am only half way there and could use some suggestions.  I have a nVidia 7600GS, which gave me the black screen of death.  Using CTRL +/- gave me some faded odd looking screens that were unusable.  I had an old ATI 9600XT laying around so I popped that in there and it works just fine.  Of course I want to use my 7600GS.  Normally the way to install a graphics card is to install the card, then the drivers.  Of course if I do that, I'll have black screen and won't be able to install the drivers.  I'm a Ubuntu n00b and have a rudimentary understanding of Linux commands.  I assume I have to install the card, then boot up and do an ALT+F2 to get a non GUI?  Then enter some commands to get the new and working drivers loaded, whatever those are.  Can someone help me get the rest of the way?

---

### Post by nedflenders on 2009-11-17
@ Enginator:

In synaptic(package manager), Make sure you have nvidia-glx-new (this is the driver that is recommended for your card [nVidia 7600GS]). installed and see the nvidia driver listed and ticked in System, Administration, Hardware Drivers. also get the Nvidia X Server Settings package so you can change your resolution/etc.

Make sure to change your Device driver to nvidia in the X11 config file [/etc/X11/xorg.conf]

Section "Device"
    Identifier     "Device0"
Driver         "nvidia"
    EndSection

reboot.
If all goes well, you should get a GUI.

use Nvidia X Server Settings in System, Administration to make your resolution changes.

Hope this helps.

---

### Post by jcxaver on 2009-11-17
nothing from your suggestions above helps me on Sony Vaio vgn z31xn with nVidia GeForce 9300 GS :(

---

### Post by luxotek on 2009-11-26
Since this is the first thread i checked (first in google) when i got this problem i'm gonna post my solution here and hopefully save someone some hair pulling.

I installed ubuntu 9.10 and was getting the dreaded black screen of death with every single nvidia driver release (97.x, 176.x 180.x 185.x 190.x 195.x) searched all over the place and even tried some old tricks (rolling back libc6 and its friends to ubuntu9 which worked on a lot of the other deb distros like sabayon). I even tried the nouveau driver (same problem)

but since there's nail-biting suspense here for all the people with this problem i'll keep a 16 hour story as short as above.

my relevant specs:
amd 5000+
MSI 9370-v2(?) (k9n v2)
nvidia 9500gt X2 (sli with bridge)

here's how i FINALLY got a working nvidia driver installed

this time i started with a clean OS (just to be sure)
i updated everything in synaptics (did not reboot)
followed the directions [here]("http://www.ubuntugeek.com/install-nvidia-graphics-drivers-190-42-in-ubuntu-karmicjauntyintrepidhardy.html") to install the 190.42 nvidia drivers (did not reboot)
ran ```
sudo nvidia-xconfig
``` (did not reboot)
ran ```
sudo gedit /etc/X11/xorg.conf
``` (got tired of using nano)

added to the device section:
   ```
Option       "ConnectedMonitor" "DFP-0"
   BusID       "PCI:5:0:0"
```added to the screen section:
  ```
 Option       "UseDisplayDevice" "DFP-0"
```and since i didn't want to run any chances i dropped in the display section just to be sure
 ```
Modes "1920x1200"
```and saved xorg.conf

NOW I REBOOTED (and crossed my fingers)

yahtzee... 

i've attached my xorg.conf just incase any one needs it.
the tricky part for me was figuring out which video card was used as primary since i have PCI:4:0:0 and PCI:5:0:0 - but a little spelunking thru xorg.0.log and the NV drivers told me everything i needed.

i sincerely hopes this works for you guys... and helps at least someone from enduring the 16 hour frustrate-a-thon i went thru.

now - to get SLI working again... sigh

---

### Post by jcxaver on 2009-11-26
looks nice, so I tried your solution

**worked not** on my vaio :(

---

### Post by luxotek on 2009-11-26
> **jcxaver said:**
> looks nice, so I tried your solution

**worked not** on my vaio :(


ah man that sucks

have you taken a look at xorg.0.log because it was that log file that told me what my problem was.

---

### Post by ebharv on 2009-11-27
Thanks, luxotex!! I had a black screen coming up when I booted my machine but this fixed the problem.
I'm also using 9800GT cards. After two days of searching forums everywhere this is the only one that helped.

Thanks again, I thought I was going to have to go back to windows for a while

---

### Post by ks0ft on 2009-11-27
> **nedflenders said:**
> I had similar issue when upgrading from 9.04 to Ubuntu 9.10


nedflenders - thanks for this, I'm up and running on 173

---

### Post by jusce on 2009-12-04
I'm having the same problem with my Vaio, nothing worked for me...

---

### Post by jcxaver on 2009-12-05
> **jusce said:**
> I'm having the same problem with my Vaio, nothing worked for me...

tried todays new updates of kernel, tried nvidia proprietary drivers(190), worked not.

I can start my vaio without any xorg.conf, vaio switch always in speed (means nvidia) position, and I can see that I have both drivers (using hwinfo -gfxcards, modprobe), i915 and nvidia active, but I can not use hdmi output. That is my main trouble, unable to use hdmi output. Normal VGA output works.

I tried to uninstall intel video drivers, and I had to install it quickly again, I had black screen only ;). 
I think that no nvidia driver never worked on my vaio, why?
How to fix this vaio problems? 

I have followed, succesfully, but without understanding :( , all  [http://global-social.net/tiki-view_blog.php?blogId=3#intel_xorg.conf](http://global-social.net/tiki-view_blog.php?blogId=3#intel_xorg.conf)     instructions.
Now I have led stamina, speed o.k. but when I switch to speed mode, I am like a blind, Nvidia show some strange unreadeable effects and that's all.
In stamina mode it worked.

I runned sudo nvidia-xconfig,
I checked that I have two xorg.conf.INTEL , xorg.conf.NVIDIA

And I am a happy man!!!!!
I am running on my Dell 2209WA LCD using hdmi and nvidia card.

:) :) :)

---

### Post by 11g on 2010-01-08
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/267241](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/267241)

1. list the device:
myname@pc1:/etc/X11$ lspci | grep -i vga
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)
2. edit xorg.conf under /etc/X11 and append BUSID with the displayed value

myname@pc1:/etc/X11$ cat xorg.conf

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Busid    "PCI:2:0:0"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

for me it helped

---

### Post by patryk77 on 2010-01-20
I also had the same problem on my Sony VAIO

The solution posted at [http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22](http://www.nvnews.net/vbulletin/showpost.php?p=2118873&postcount=22) worked for me :D

I just have to get HDMI working again now, but at least I have the screen.

---

### Post by Kbipinkumar on 2010-01-21
i too have problem with my nvidia geforce gt 130m card in laptop. i installed the latest 190.x drivers nvidia website and i got six desktop clones on my monitor, i had same problem with driver i got from ubuntu repos as well ca someone tell what has gone wrong

---

### Post by henriquegontijo on 2010-01-23
After a lot of tries, following other tips from internet, it worked for me.

The steps that I used:

-Open console and type:
sudo rmmod nvidia
sudo aptitude remove --purge nvidia-glx-185 nvidia-185-libvdpau nvidia-185-kernel-source
sudo aptitude install nvidia-glx-173 nvidia-173-kernel-source nvidia-173-modaliases

-Go System > Administration > Hardware Drivers, select driver 173 and then click Enable. Reboot!

Plus: After rebooting I enabled the display Visual Effects (System > Preferences > Appearance > Visual Effects > Extra. It's so nice, the display looks a lot better, the windows are 'softer' and more pleasant.

My dist and hardware:
VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)

Linux henrique-pc 2.6.31-16-server #53-Ubuntu SMP Tue Dec 8 05:08:02 UTC 2009 x86_64 GNU/Linux

---

### Post by ebischoff on 2010-01-30
Same symptoms : black screen with GeForce 9800 GT from TwinTech (1 GB RAM, "Green edition"), with Karmic on a 64 bit machine.

I tried all versions of the proprietary nvidia driver (96, 128, 173, 185, 190), as well as "nouveau" driver, with no results.

I also tried many changes in xorg.conf file, with no success. For example, declaring the BusID does not help.

It does not seem to be a problem related to missing EDID info either (my monitors' names are recognized correctly).

I ended up using the old "nv" driver. The result is fine, excepted that I can't do real Xinerama, only RandR 12. As a result, the KDE desktop does not span over both screens, but at least I can drag a window between both screens.

Also, that workaround leaves me without 3D (OpenGL).

I hope that helps.

---

### Post by jimflood on 2010-02-05
[FONT=Verdana]A simple way on 9.10 karmic koala to undo the black screen after activation of the restricted nvidia driver: while sitting at the black screen, hit Ctrl-Alt-1 to switch to a text login. Then use the command
[/FONT][INDENT][FONT=Verdana]$ sudo jockey-text -l[/FONT]
[/INDENT][FONT=Verdana]to list the drivers, and then, for example
[/FONT][INDENT][FONT=Verdana]$ sudo jockey-text -d xorg:nvidia-96[/FONT]
[/INDENT][FONT=Verdana]to deactivate the driver, and then reboot
[/FONT][INDENT][FONT=Verdana]$ sudo shutdown -r 0[/FONT]
[/INDENT][FONT=Verdana]jockey-text is the text version of the dialog box which activated the driver in the first place, so you should be exactly restoring your system to just before the, uh, mistake.[/FONT] (I just learned this the hard way on a fresh install of 9.10.)

---

### Post by karukera7 on 2010-02-08
Hello,
 
**@nedflenders**, i'm having having the same problem, after i installed the nvidia driver and rebooted my computer, i get a dark screen, the ubuntu logo shows up at startup then i get a dark screen, cannot see the logon window.

---

