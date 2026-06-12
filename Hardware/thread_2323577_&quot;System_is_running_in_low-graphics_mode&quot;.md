---
title: "&quot;System is running in low-graphics mode&quot;"
date: 2016-05-06
forum: Hardware
---

### Post by jorge39 on 2016-05-06
Hey! 

I was installing gnome for ubuntu 14.04 LTS but it didn't work well so I decided so unninstall the graphical environment (unity) and then reinstall gnome. But I have a problem which I didn't solve yet. This is ehat I did:

```
 Sudo apt-get update

Sudo apt-get install ubuntu-gnome-desktop

Sudo apt-get remove ubuntu-desktop unity && sudo apt-get autoremove (ubuntu-desktop and unity not installed) 

Sudo apt-get purge ubuntu-desktop unity unity-greeter && sudo apt-get autoremove  (unity-greeter removed)

Sudo apt-get remove gnome-shell 

Sudo apt-get install gnome-shell -> lightdm

Sudo apt-get install ubuntu-gnome-desktop

Sudo reboot now

"System is running in low-graphics mode" 

Sudo apt-get remove ubuntu-gnome-desktop

Sudo apt-get install ubuntu-gnome-desktop 

Sudo shutdown -r now

Still 
"System is running in low-graphics mode" 

Sudo apt-get install gdm (it did nothing)
Sudo service gdm restart -> got stuck -> forced shutdown

It shows gnome loadin screen but then it still shows "System is running in low-graphics mode" 
```

Can anyone give me a hint?

I have a hp pavillion with nvidia drivers if it matters.

---

### Post by T.J. on 2016-05-06
Do things work in other desktops already?  if they do, it may be a problem with Gnome Shell.  Some drivers do not support EGL.  I don't think that would be the problem with Nvidia though.  I'd reinstall ubuntu-desktop for testing purposes.  Two desktops can happy co-exist.

  If video doesn't work in any environment, you may need to configure the driver.  The command: *sudo nvidia-xconfig* should help.  It should create a new settings file for X11.  After you save it, and reboot, you should be "right as rain".  If that does not work, we will need to check to see if your drivers are installed properly.  If you are using the nouveau driver, I need to know what generation your card is before I can help you.

---

### Post by jorge39 on 2016-05-06
Thank you for the reply.

It doesn't work on other desktops. I tried to configure the driver but it did not work. I have a noveau driver (as I'll show further) and tried to install the latest nvidia driver but got again the low-graphics mode issue. 

Here's what I did:

```

To configure the nvidia driver I did: 

Sudo nvidia-xconfig (It created new settings file for X11).

Sudo shutdown -r now

Back to low-graphics mode.

To see what kind of drivers I have I did:

Sudo ubuntu-drivers devices

The output can be seen in this image: [http://postimg.org/image/cr9x8k45d/](http://postimg.org/image/cr9x8k45d/)

Then I did:

Sudo apt-get install nvidia-352 (already installed)

Sudo apt-get install nvidia-340 (it removed nvidia 352) 

Sudo apt-get install nvidia-352 (it removed nvidia-340)

Sudo shutdown -r now 

Back to low-graphics mode 
```

What should I do next?

---

### Post by him610 on 2016-05-07
To get a better idea of your system specs, run this from a terminal...
```
inxi -b
```
Post the results.

---

### Post by T.J. on 2016-05-07
I would suggest that perhaps the video driver is not correctly installed - your OpenGL installation is probably corrupted.  I have had this happen before with previous versions of Ubuntu, so it is definitely not outside of the realm of possibility. I'm afraid that Ubuntu's driver installation is somewhat broken on rare occasions, compared to Debian - its parent distribution. 

Ubuntu used to use a tool called Jockey and I suspect that (or its replacement) is your problem.  


First, I would try to revert to the opensource nouveau driver temporarily, in order to get the OpenGL libraries back to a working state.  Don't be surprised if one or two come back with errors.  Ubuntu might have changed the Debian default names or one might be missing or not installed. I'm sorry about the huge list. We are just being as thorough as possible.   Please report any errors as they may be important.  It is quite likely that uninstalling one package may cascade others, so do not be surprised if more than one uninstalls at a time or some are already removed when you reach a step. 

Now, these commands are from Debian (mostly), but they should work for Ubuntu as well.  Ubuntu is basically a copy of Debian Linux with a few things added to make it more friendly.

Try the cleanup package (if it exists) first. It may save you a lot of work. Then again you may need to perform them all anyway. 

```
sudo apt-get install nvidia-installer-cleanup
sudo apt-get purge nvidia-installer-cleanup
```

Try a reboot.  If that doesn't work proceed with a manual cleanup.

Manual removal
--------------------------------------------------

1. Purge the Nvidia OpenGL driver install:
 ```
sudo apt-get purge nvidia-352

```

2. Purge the Nvidia EGL library:
```
sudo apt-get purge libegl1-nvidia

```


3. Remove the Nvidia diversions:
```
sudo apt-get purge glx-alternative-nvidia

```


4.Reinstall the open Nvidia driver:
```
sudo apt-get install --reinstall xserver-xorg-video-nouveau
```

5. Reinstall the Mesa GLX library:
```
sudo apt-get install --reinstall libgl1-mesa-glx
```

6.Reinstall the Direct Render library:
```
sudo apt-get install --reinstall libgl1-mesa-dri
```

7.Reinstall the EGL library:```

sudo apt-get install --reinstall libegl1-mesa
```

8.Force Ubuntu back to Mesa OpenGL as the default rendering library:```
sudo apt-get install  --reinstall glx-alternative-mesa
```

9. Make sure to delete the /etc/X11/xorg.conf file - it is important to get all traces of the bad driver install out of there.
```
sudo rm /etc/X11/xorg.conf*
```

10. Force Ubuntu to reconfigure the GUI login so that we make sure that it will start.
```

sudo dpkg-reconfigure lightdm
```

11. Check the /etc/modules.d for blacklist files for Nouveau.  If so, their contents need to be commented out with a #.

12. Reinstall the required firmware.
```
sudo apt-get install --reinstall firmware-linux firmware-linux-nonfree

```

13. Remove any remaining Nvidia kernel or utilities
```
sudo apt-get purge nvidia*

```

14. Try to purge anything else.
```
sudo apt-get install nvidia-installer-cleanup
sudo apt-get purge nvidia-installer-cleanup
```


-----------------------------------------------------------------------
End of manual remove


After that, I would reboot and see if you get a decent GUI. If you have a 900 series card, you may not - but that is not unheard of. If we are successful, I'll walk you through building your own Nvidia driver from the latest Nvidia download - but I will need the model number to get the right driver.

---

### Post by jorge39 on 2016-05-07
I still have the same problem :(

This is what I did:

```

sudo apt-get purge nvidia-352

sudo apt-get purge libegl1-nvidia (unable to locate) 

sudo apt-get purge glx-alternative-nvidia (unable to locate) 

sudo apt-get install --reinstall xserver-xorg-video-nouveau

[http://imgur.com/FEe5WxE](http://imgur.com/FEe5WxE)

Tried to reinstall dependencies without success:

[http://imgur.com/P3nEf56](http://imgur.com/P3nEf56)

sudo apt-get install --reinstall libgl1-mesa-glx (same problem - error pkgProbemResolver:: ...) 

Libgl1-mesa-dri -> same problem

Libgl1-mesa -> unable to locate

Glx-alternative-mesa -> unable to locate

 ----

Recovery menu:
1) dpkg - repair broken packages

[http://m.imgur.com/YeUPyH2](http://m.imgur.com/YeUPyH2)

Network -> wrote crtl C and after wrote 'exit' (sent me to a new terminal) -> forced shutdown

``` 

Any suggestions?

---

### Post by T.J. on 2016-05-07
As long as you have a connection, a prompt, or in worst case - a startup disc - nothing has been done here that can't be undone. =)  Don't worry.  Have to work.  Will consider things and get back to you soon.

---

### Post by T.J. on 2016-05-07
In the meantime, please verify your connection (if you can download packages) and then try 

```
sudo apt-get install --reinstall xorg
```
 
Please tell me what it says please.  Ubuntu may have changed the dependency chains.

---

### Post by T.J. on 2016-05-07
As soon as I have some free time, I will create a new 14.04 machine, and run through the entire process manually.  We WILL fix your problem, "by hook or by crook."  (Sorry old English expression - dates me doesn't it?  It means "by any means necessary".)

---

### Post by T.J. on 2016-05-07
Please post the results of```
lspci -vnn 
``` as soon as can be accomplished.

Thank you! =)

---

### Post by jorge39 on 2016-05-07
Once I get home I'll see your suggestions and post the output.

Thank you for your help! See you later!

---

### Post by jorge39 on 2016-05-09
When I did 

```
 sudo apt-get install --reinstall xorg 
```

I got:
[http://m.imgur.com/gallery/Q1oGVu8](http://m.imgur.com/gallery/Q1oGVu8)

[http://m.imgur.com/FDOwiEr](http://m.imgur.com/FDOwiEr) 

Tried sudo apt-get update and --fix-missing but still shows the same error.

The output of lspci -vnn is the following:

[http://m.imgur.com/qqp0iYe](http://m.imgur.com/qqp0iYe) 

[http://m.imgur.com/FFJB24C](http://m.imgur.com/FFJB24C) 

[http://m.imgur.com/TjMV0He](http://m.imgur.com/TjMV0He) 

Sorry for posting photos as I can't copy paste the output and put it here. If you have any problem reading just say something and I'll try to make it clearer.

Thank you for your help.

---

### Post by T.J. on 2016-05-09
I think I got most of what I needed.  I'm up to my ears with work the next day or so but I will get back to you soon

---

### Post by jorge39 on 2016-05-09
Ok, thank you in advance.

---

### Post by jorge39 on 2016-05-16
I am still trying to fix it. Does anyone have any further suggestions?

---

### Post by T.J. on 2016-05-20
Jorge, 

I apologise for being absent so long.  Work, life and other things have kept me distracted.  Do you still need help?

---

### Post by jorge39 on 2016-05-23
No problem.

Now I have installed gnome shell but it only works if you run in low-graphics mode. Thus, the problem is not yet fully solved. 

Thank you, 
Jorge

---

### Post by T.J. on 2016-05-23
It sounds like a firmware issue to me.   Are firmware-linux and firmware-linux-nonfree installed?

---

### Post by jorge39 on 2016-05-23
> **T.J. said:**
> It sounds like a firmware issue to me.   Are firmware-linux and firmware-linux-nonfree installed?

Both are not installed.. And doing sudo apt-get won't work. Maybe there is another way of installing them?

---

### Post by jorge39 on 2016-05-25
I already installed them, but the problem isn't solved. I will search more about this

---

### Post by T.J. on 2016-05-25
You have an 840m card, which is not a "regular" Nvidia card, but a hybrid.  Have you tried the nvidia-prime package? I'm not an expert with it, but I have seen it recommended in posts regarding M series cards before. All of my cards are fully discrete cards rather than M versions. 

The other logical alternative is to install the Nvidia driver manually.

You've been more than patient and I am sure you would rather be doing something else - so if the prime package does not help, I'll walk you through the manual install process and we will get this fixed, once and for all.

---

### Post by jorge39 on 2016-05-25
Hey, thank you for the help so far.
Unfortunately, it didn't work. Purged nvidia content and tried to install prime-nvidia but it doesn't appear in "Additional Drivers". Here are two nvidia drivers (version 340.96 and 352.63) which can be made proprietary. I tried to install the latest version and then switching from using X.org X server to the proprietary driver nvidia 352, but it didn't work either.

(Actually whenever I have some problem with working in GUI I do:
```
 
$ sudo apt-get purge "nvidia *" 
$ sudo apt-get install nvidia-current
$ sudo reboot 
``` 

and it always runs with GUI in low-graphics mode.)

Also the graphics driver is being reported as Gallium something..

---

### Post by T.J. on 2016-05-25
All right.  =)

My Nvidia card is dedicated to my right monitor and KVMs, so I will setup a KVM with 14.04 as we previously discussed.  I'll manually install the Nvidia driver on my 960, and then write the process down and post it for you.  I have to work tonight so I will take a stab at it tomorrow or Friday at the latest, and then post it all here for you, in detail.

---

### Post by RobGoss on 2016-05-25
Hello and welcome to the forum, You might find this article useful with this type of problem [http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error) according to this post it's a drives problem that may need updating. I also had this issue a few weeks back but I was in the process of upgrading from** 14.04 to 16.04**, so I did not find this article at the time I just did a clean install of **16.04** and it took care of my issue. Hope this help

---

### Post by T.J. on 2016-05-28
Just an update on a first attempt, Jorge.

X went into low mode with a segfault.  I'm guessing at the moment, but it appears the built in driver does not support a significant segment of hardware.  I'll have to find a way to perform an install with X and then manually install the driver.  I'm thinking about the alternative install disc if Ubuntu still makes one.  I'll run another pass tomorrow after work.

---

### Post by jorge39 on 2016-05-28
OK, thank you T.J.

Meanwhile I'll also try to read more about this. 

Appreciate your effort!

---

### Post by jorge39 on 2016-05-28
> **RobGoss said:**
> Hello and welcome to the forum, You might find this article useful with this type of problem [http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error) according to this post it's a drives problem that may need updating. I also had this issue a few weeks back but I was in the process of upgrading from** 14.04 to 16.04**, so I did not find this article at the time I just did a clean install of **16.04** and it took care of my issue. Hope this help

I have tried, unsuccessfully, the suggestions presented in that post. 

Thank you for the feedback.

---

### Post by Bashing-om on 2016-05-28
jorge39; T.J.

Mind if I poke my nose in this ?

Nvidia recommends the 361 version driver for this card . In release 14.04 we do not have that driver in the repo.
[http://www.nvidia.com/download/driverResults.aspx/103306/en-us](http://www.nvidia.com/download/driverResults.aspx/103306/en-us)

However, it is available in our trusted PPA .
Hybrid graphics, so we want to insure we have a means of controlling the graphics sets - the more recommended controller is nvidia-prime.

How about we purge all nvidia stuff, remove the present config file and add the PPA to the system; then install the 361 version driver and controller  ?

Worth a shot .

```

sudo apt purge nvidia*
sudo rm /etc/X11/xorg.conf
sudo apt update
sudo apt upgrade
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get install nvidia-361 nvidia-prime
sudo reboot

```

Now upon the reboot, what is the situation ?

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by T.J. on 2016-05-28
Well, this was interesting.  I hope these instructions are clear.  If they make no sense, then please let me know. Before you try this, you should read everything first. I believe you should also try the nvidia-prime repository first, if you have not already done so.

**Step 1. **
When Ubuntu starts press ESC or use the bootmenu edit to  add &#8220;nomodeset blacklist=nouveau vga=0x318&#8221; to start kernel parameters to force Ubuntu into a stable lower resolution mode.


**Step 2:**
Login and update Ubuntu in a terminal

[I]sudo apt-get update
sudo apt-get upgrade[/I]


You want to disable Ubuntu&#8217;s broken startup on modern Nvidia cards.  The easy way is to add:

&#8220;nomodeset blacklist=nouveau vga=0x318&#8221;  

to the GRUB_CMD_LINE_DEFAULT in your /etc/default/grub file.

Be sure to run: *sudo update-grub *so the bootloader gets updated.

Reboot and login

**Step 3:**
Download the Nvidia driver from Nvidia.

**Step 4:**
install the module assistant to compile a new driver.

[I]
sudo apt-get install module-assistant
sudo m-a prepare[/I]

**Step 5: **
Get out of X.  You can&#8217;t install the Nvidia driver manually inside of X11. 

In a terminal: *sudo /etc/init.d/lightdm stop*

This will put you at a black screen, press alt+F1 to get a standard terminal prompt. Login


**Step 6:**
install the driver. Assuming you saved the driver to Downloads cd to that directory. The current driver is 361.45.11.


To install the driver manually, you must do so with root permission:
[I]
sudo sh ./NVIDIA-Linux-x86_64-361.45.11.run[/I]

It will proceed with a bunch of prompts, including a warning about distribution scripts.Take the defaults and proceed. At the end, it will ask you if you want to reconfigure X11, say yes. After that, reboot and enjoy a decently working 14.04!

**Step 7:**
Only after you are satisfied &#8211; as a safety measure, you will need to mark the glxdrivers as &#8220;Held&#8221; so that if Canonical updates Mesa it does not break your driver install.

[I]sudo apt-mark hold libgl1-mesa-glx
sudo apt-mark hold libgl1-mesa-dri[/I]




A couple of caveats:

**Uninstalling the driver**
Installing the driver manually means that you can&#8217;t use the Ubuntu installer for video drivers, unless you uninstall the manual one first.  You can do that by adding &#8211;uninstall to the *NVIDIA-Linux-x86_64-361.45.11.run* command.


Before you reboot,you will need to repair Mesa after you uninstall  the driver.  
[I]

sudo apt-mark unhold libgl1-mesa-glx
sudo apt-mark unhold libgl1-mesa-dri

sudo apt-get install &#8211;reinstall libgl1-mesa-glx
sudo apt-get install&#8211;reinstall libgl1-mesa-dri[/I]


Be sure to delete the /etc/X11/xorg.conf file, then reboot.




**32-bit such as Steam**
If you want to use Steam or 32 bit OpenGL apps, you may find yourself in a position where you have to reinstall the driver after you install them.  This is ok, but you will have to shutdown X to do it.  Just install the apps, then exit X, reinstall the driver over itself and reboot.

---

### Post by T.J. on 2016-05-28
> **Bashing-om said:**
> jorge39; T.J.

Mind if I poke my nose in this ?[INDENT][INDENT]
[/INDENT]
[/INDENT]


Not at all.  In fact, I am glad for it if it is supported. It's better than a hack from someone like myself, from the old days of X11 and XFree. My methods are less polished and more direct.  (Some might even consider them similar to going after a housefly with a bazooka.)   If the nvidia prime package works for Jorge, and it is easier then by all means!  I believe I did suggest it at one point.  

I think the only thing that left me at a loss during this experience is why Ubuntu fails to fallback on standard VESA/VGA modes when booting after the primary tests fail (as they did in this case).  I had to manually force the system out of a loop where the repair option failed to function correctly at all.  This has been a problem for a long time in my experience. IMHO the "low-graphics mode" repair is a severely broken idea and should have been replaced long ago. 

Maybe you know somewhere I can suggest a fix?

---

### Post by jorge39 on 2016-05-29
Thank you both for your replies. Very interesting suggestions indeed. To try them I will have to have a wired internet connection, since I am not able to connect via wifi. Thus tomorrow I will try first the prime repository (already tried but without nvidia-361) and if it doesn't work I will try to configure manually.

Once I get this working I will post here the steps I made in case someone has the same problem.

Thank you for your help!

---

### Post by jorge39 on 2016-05-30
> **Bashing-om said:**
> jorge39; T.J.

Mind if I poke my nose in this ?

Nvidia recommends the 361 version driver for this card . In release 14.04 we do not have that driver in the repo.
[http://www.nvidia.com/download/driverResults.aspx/103306/en-us](http://www.nvidia.com/download/driverResults.aspx/103306/en-us)

However, it is available in our trusted PPA .
Hybrid graphics, so we want to insure we have a means of controlling the graphics sets - the more recommended controller is nvidia-prime.

How about we purge all nvidia stuff, remove the present config file and add the PPA to the system; then install the 361 version driver and controller  ?

Worth a shot .

```

sudo apt purge nvidia*
sudo rm /etc/X11/xorg.conf
sudo apt update
sudo apt upgrade
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get install nvidia-361 nvidia-prime
sudo reboot

```

Now upon the reboot, what is the situation ?

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

Unfortunatelly it wasn't capable of locating nvidia-361. I did all the steps but it still gives me the low-graphics mode. Thank you anyway! 

I will try to manually install it later when I get back home.

---

### Post by Bashing-om on 2016-05-30
jorge39; Ouch !


Not to be stepping on T.J. 's toes; He does excellent work.

My thought process:
There must be an underlie-ing reason why the driver install does not succeed. We do need to discover this cause.
Make sure the system is fully updated:
```

sudo apt update
sudo apt upgrade

```
If any errors are reported we do need to see them . Post the command and the complete output for our examination.

Next in order to build a driver, the kernel header files must be available, are they ?
show:
```

dpkg -l | grep linux-

```

AND do we have the operating head room on the system ?
Show:
```

df -h
df -i

```

Then once the ground work is completed .. we go looking at the log files on our mission of discovery.

[INDENT][INDENT]it's cause and effect
[/INDENT][/INDENT]

---

### Post by jorge39 on 2016-05-30
> **Bashing-om said:**
> jorge39; Ouch !


Not to be stepping on T.J. 's toes; He does excellent work.

My thought process:
There must be an underlie-ing reason why the driver install does not succeed. We do need to discover this cause.
Make sure the system is fully updated:
```

sudo apt update
sudo apt upgrade

```
If any errors are reported we do need to see them . Post the command and the complete output for our examination.

Next in order to build a driver, the kernel header files must be available, are they ?
show:
```

dpkg -l | grep linux-

```

AND do we have the operating head room on the system ?
Show:
```

df -h
df -i

```

Then once the ground work is completed .. we go looking at the log files on our mission of discovery.

[INDENT][INDENT]it's cause and effect
[/INDENT][/INDENT]

After doing sudo apt update it does give me 3 warnings and one error:
[ http://imgur.com/BGjs8rs ]( http://imgur.com/BGjs8rs )

It doesn't find "/trusty/main/source/Sources", "/trusty/main/binary-i386/Pacjages" and "/trusty/main/binary-amd64/Packages". Consequently, the error is that some index files failed to download...

---

### Post by Bashing-om on 2016-05-30
jorge39; K ..Making progress.

The PPA " http://ppa.launchpad.net/artfwo/ppa/ubuntu/dists/" does not support trusty. Disable this source and try again:
Load the URL as given in your browser, see for yourself .. Will have to ask the author(s) why the LTS 14.04 is not supported !
```

sudo apt update
sudo apt upgrade

```

If that now runs clean and all up dates are done we want to see:
```

dpkg -l | grep linux-
df -h
df -i

```

and see where these lead us .

[INDENT][INDENT]get a firm foundation
[INDENT][INDENT]and push
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jorge39 on 2016-05-30
> **Bashing-om said:**
> jorge39; K ..Making progress.

The PPA " http://ppa.launchpad.net/artfwo/ppa/ubuntu/dists/" does not support trusty. Disable this source and try again:
Load the URL as given in your browser, see for yourself .. Will have to ask the author(s) why the LTS 14.04 is not supported !
```

sudo apt update
sudo apt upgrade

```

If that now runs clean and all up dates are done we want to see:
```

dpkg -l | grep linux-
df -h
df -i

```

and see where these lead us .

[INDENT][INDENT]get a firm foundation
[INDENT][INDENT]and push
[/INDENT][/INDENT][/INDENT][/INDENT]

Hmm nice! 

The output of the commands above is:
[imgur.com/ZIfdf1m](imgur.com/ZIfdf1m)
And 
[imgur.com/EldBNPS](imgur.com/EldBNPS)

---

### Post by Bashing-om on 2016-05-30
jorge39; Ouch !!

What have you been doing ? The old header files are installed .. but there are no matching kernel images ?
And you are still at 97% capacity  in the /root directory. 

What kernel are you booting up with ?.. what ever we do we must not mess the the kernel that you are booted up with.
```

uname -r

```

I am going to have to consider ways and means to climb out of this hole . Background info will help .
We are going to have to get the header and kernel images straight so the system can build the driver modules .

Oh Boy;

[INDENT][INDENT]I hate when this happens
[/INDENT][/INDENT]

---

### Post by jorge39 on 2016-05-30
The kernel I'm running is 4.2.0-37-generic. Sorry if I am being ignorant but isn't there a matching kernel image for 4.2.0-37-generic kernel? In the output I posted there were both headers and images of this kernel..

I will try to read more about this though :)

---

### Post by Bashing-om on 2016-05-30
jorge39; Yeah .

We are good as to the booted matching kernel and headers.

Let's see what results:
```

sudo apt autoclean
sudo apt clean
sudo apt-get autoremove
sudo apt update
sudo apt upgrade

```
Paying real close attention to what is being removed .. we do not want to disturb the 4.2.0-37 kernel.

I can accept that the package manager is going to balk. In that case we drop down to a lower level and remove those old headers manually. What is going on I think is that the system is attempting to build the driver module on these old headers. Let's take this out of the equation and also get the disk space usage down below " fragmentation" level.
Once we have reduced to 2 kernels only and we have the operating headroom .. we try and build the graphic's modules once more.

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

### Post by jorge39 on 2016-05-31
I started by doing 

```
sudo apt-get autoclean
sudo apt-get clean
```

But it was going to clean:
```
linux-headers-4.2.0-27 linux-headers-4.2.0-27-generic
  linux-image-4.2.0-27-generic linux-image-extra-4.2.0-27-generic
  linux-signed-image-4.2.0-27-generic
```


So I only did:
```
sudo apt-get remove bbswitch-dkms linux-headers-3.13.0-85 linux-headers-3.13.0-85-generic primus-libs primus-libs:i386 primus-libs-ia32:i386 socat
```

(What about primus-libs stuff? Should I clean them too?)

After the "sudo apt-get remove bbswitch-dkms (...)" I notice it said:

```
bbswitch.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.2.0-36-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
```

So I did:
```
sudo apt-get install bbswitch-dkms
```

When I did this I noticed in the output the following: 
```
"Building only for 4.2.0-37-generic
Building initial module for 4.2.0-37-generic"
```

Then I did:
```
sudo apt update
sudo apt upgrade
```

The output of "sudo apt upgrade" had this:

```
The following packages were automatically installed and are no longer required:
  linux-headers-4.2.0-27 linux-headers-4.2.0-27-generic
  linux-image-4.2.0-27-generic linux-image-extra-4.2.0-27-generic
  linux-signed-image-4.2.0-27-generic
Use 'apt-get autoremove' to remove them.
```

The output of "dpkg -l | grep linux-" was:
```
jorge@jorge-HP-ENVY-15-Notebook-PC:~$ dpkg -l | grep linux-
ii  linux-firmware                                        1.144+ar3012                                        all          Firmware for Linux kernel drivers
ii  linux-firmware-nonfree                                1.14ubuntu3                                         all          Non-free firmware for Linux kernel drivers
ii  linux-generic-lts-wily                                4.2.0.37.30                                         amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-86                               3.13.0-86.131                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-86-generic                       3.13.0-86.131                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-87                               3.13.0-87.133                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-87-generic                       3.13.0-87.133                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-27                                4.2.0-27.32~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-27-generic                        4.2.0-27.32~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-34                                4.2.0-34.39~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-34-generic                        4.2.0-34.39~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-36                                4.2.0-36.42~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-36-generic                        4.2.0-36.42~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-37                                4.2.0-37.43~14.04.1                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-37-generic                        4.2.0-37.43~14.04.1                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.87.93                                        amd64        Generic Linux kernel headers
ii  linux-headers-generic-lts-wily                        4.2.0.37.30                                         amd64        Generic Linux kernel headers
ii  linux-image-4.2.0-27-generic                          4.2.0-27.32~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-34-generic                          4.2.0-34.39~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-36-generic                          4.2.0-36.42~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-37-generic                          4.2.0-37.43~14.04.1                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-27-generic                    4.2.0-27.32~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-34-generic                    4.2.0-34.39~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-36-generic                    4.2.0-36.42~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-37-generic                    4.2.0-37.43~14.04.1                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-wily                          4.2.0.37.30                                         amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                  3.13.0-87.133                                       amd64        Linux Kernel Headers for development
ii  linux-signed-generic-lts-wily                         4.2.0.37.30                                         amd64        Complete Signed Generic Linux kernel and headers
ii  linux-signed-image-4.2.0-27-generic                   4.2.0-27.32~14.04.1                                 amd64        Signed kernel image generic
ii  linux-signed-image-4.2.0-34-generic                   4.2.0-34.39~14.04.1                                 amd64        Signed kernel image generic
ii  linux-signed-image-4.2.0-36-generic                   4.2.0-36.42~14.04.1                                 amd64        Signed kernel image generic
ii  linux-signed-image-4.2.0-37-generic                   4.2.0-37.43~14.04.1                                 amd64        Signed kernel image generic
ii  linux-signed-image-generic-lts-wily                   4.2.0.37.30                                         amd64        Signed Generic Linux kernel image
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

Btw, T.J. I didn't forget your suggestion about installing manually the drivers, but I am going to do that as last resource. Thanks for the effort!

---

### Post by T.J. on 2016-05-31
> **jorge39 said:**
> Btw, T.J. I didn't forget your suggestion about installing manually the drivers, but I am going to do that as last resource. Thanks for the effort!

You're very welcome! =)  Not to worry. I am in no way offended. 


This is a learning process for all of us, and our approaches to the same problem vary.  That doesn't make them any less valid.  You do what you think is best for you and I'll be content.  Both you and Bashing-om have my support in any case.  We are here to help you, not win an argument with you caught in the middle.  

I respect Bashing-om's methodical approach. I approach the problem with "the nuclear option" because - and I say this with honesty, I have a very jaded view of Ubuntu's handling of video drivers over the years.  I've viewed the driver installer with a measure of disdain, thinking it an incompetent software.  When I say that, I am not trying to be nasty. If something causes as many problems as it solves, it is not a good solution.  I've have had it fail more often then it worked.  However, in passing that judgement, at no time have I stopped to help fix it either. I did not believe in the Canonical copyright agreements, that allowed them to reassign a license as they saw fit. I do not know if that has changed significantly since.

I usually say nothing.  I mention it now so that you can understand why I took that approach, not as a criticism of Ubuntu.

---

### Post by Bashing-om on 2016-05-31
jorge39; Look'n promise 'n 

Sorta confirms the system was not happy with the state of the headers.

How bout this for a thought . Let's get the old 3.13.0- series kernels off the system ..IF and only IF you are up on the 4.2.0-37 kernel and there are absolutely no issues with it .. such that you have no need to boot an old 3.13 kernel . We will keep a backup for the 4.2.0-37 kernel .

Confirm what kernel is booted once more:
```

uname -r

```

and we work to getting only 2 kernels on the system.

BK

 primus-libs stuff: 
```

apt-cache depends primus

```
Hey that is under BumbleBee, is it not ? .. did you have then a conflict with nvidai-prime ?
When we get the kernel issue where it is consistent, we address this possible conflict .


That is what I think
[INDENT][INDENT]anywho, else
[/INDENT][/INDENT]

---

### Post by T.J. on 2016-05-31
As a point of advice, you should use only the kernel header files that glibc and gcc were compiled with, regardless of the kernel you have installed.  Using other versions of the headers can - theoretically at least - cause unforeseen bugs when linking.  The kernel package itself will be fine as long as its version is equal or newer than the headers used for glibc when it was built.  The kernel's ABI is pretty stable, and won't care if older headers are used.

---

### Post by jorge39 on 2016-06-01
I have cleaned the 3.(...) versions of the kernel and when I do "apt-cache depends primus" it says that it is under BumbleBee. 

Update: some of the first steps I did here didn't work because I didn't have internet connection, so I will try to look for what I wasn't capable of doing due to the internet connectio. What a silly billy I am..

---

### Post by Bashing-om on 2016-06-01
jorge39; K -

When we know the system is stable on 4.2.0-37 kernel ; then we can remove the old 3.13 kernels, and future installs for this series.


[INDENT][INDENT]reduce to simplest terms
[/INDENT][/INDENT]

---

### Post by jorge39 on 2016-06-01
Sorry, I meant I removed the 3.13 kernels.. (And not just cleaned)

---

### Post by Bashing-om on 2016-06-01
jorge39; K;

Let's look and see where we stand:
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-
ls -al /vmlinuz*
ls -al /initrd.img*

```
I do want to insure that the 3.13 series kernels do not get re-installed .

If all looks good .. we try once more to install the driver .

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jorge39 on 2016-06-02
When I do 

```
 ls -al /lib/modules/
```

I get the following output: 
```
jorge@jorge-HP-ENVY-15-Notebook-PC:~$ ls -al /lib/modules/total 32drwxr-xr-x  8 root root 4096 Jun  1 21:16 .
drwxr-xr-x 25 root root 4096 Mai 30 17:46 ..
drwxr-xr-x  3 root root 4096 Mai 31 21:29 3.13.0-85-generic
drwxr-xr-x  3 root root 4096 Jun  1 21:13 3.13.0-86-generic
drwxr-xr-x  3 root root 4096 Jun  1 21:14 3.13.0-87-generic
drwxr-xr-x  6 root root 4096 Mai 31 21:28 4.2.0-34-generic
drwxr-xr-x  6 root root 4096 Mai 31 21:28 4.2.0-36-generic
drwxr-xr-x  6 root root 4096 Mai 31 21:31 4.2.0-37-generic

```

But I am struggling a bit removing the lib modules of the kernel versions 3.13.*

When I do 
```
[COLOR=#000000][FONT=&quot]dpkg -l | grep linux-
```
[/FONT][/COLOR]
It doesn't show the 3.13.* kernel versions.

The other output I find interesting is from 

```
[COLOR=#000000][FONT=&quot]ls -al /vmlinuz*
ls -al /initrd.img*
```

Because the old kernel is different and I don't know if it is useful to change it. The output is the following:
```
 [/FONT][/COLOR]~$ ls -al /vmlinuz*lrwxrwxrwx 1 root root 29 Mai 30 17:28 /vmlinuz -> boot/vmlinuz-4.2.0-37-generic
lrwxrwxrwx 1 root root 29 Mai 25 09:28 /vmlinuz.old -> boot/vmlinuz-4.2.0-36-generic

~$ ls -al /initrd.img*
lrwxrwxrwx 1 root root 32 Mai 30 17:28 /initrd.img -> boot/initrd.img-4.2.0-37-generic
lrwxrwxrwx 1 root root 32 Mai 25 09:28 /initrd.img.old -> boot/initrd.img-4.2.0-36-generic

```

---

### Post by Bashing-om on 2016-06-02
jorge39; Welp ...

We know we still have inconsistencies .
Let see what we can do to make things right.
Show us now what is the present condition. Post what we are working with:
```

dpkg -l | grep linux-
ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/

```
As to:
> 
Because the old kernel is different and I don't know if it is useful to change it. 

Is proper as is .. what you have set here is to boot 4.2.0-37- ; and IF there is a problem booting it ..there is the fall back " /vmlinuz.old  " kernel.

One can straighten things up kernel wise. but at this point is very dirty .. as we have arrived here at this means of last resort; that is what we do . We get dirty .
Handle things manually breaking the package management system. When we have all in a consistent state we have the system fix the package manager .

[INDENT][INDENT]got to have a firm foundation
[INDENT][INDENT][INDENT]to push from
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jorge39 on 2016-06-03
Roger that!

The output of 

```
 [COLOR=#000000][FONT=&amp]dpkg -l | grep linux-
[/FONT][/COLOR]ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/

```

Is presented in these 3 images:
[http://imgur.com/a/ADq6R ]("http://imgur.com/a/ADq6R")

---

### Post by Bashing-om on 2016-06-03
jorge39; Yeah ..

Not much that you have not done.
All I see to do is :
```

sudo rm -rf /lib/modules/3.13.0-{85,86,87}*
sudo apt -f install

```
should fix the package manager.

Now check:
```

sudo apt update
sudo apt upgrade

```
that all runs clean.


And then we are back to getting the proprietary driver to install. A conflict with BumbleBee?
Show what is presently installed:
```

dpkg -l | grep -i nvidia

```

also a log file :
```

cat /var/log/gpu-manager.log

```
to see if the system is in a state to build the driver .

[INDENT][INDENT]cause and effect
[/INDENT][/INDENT]

---

### Post by jorge39 on 2016-06-04
I am with weak wifi connection right now. Tomorrow I'll go to a spot near the router and will do that. Thank you

---

### Post by jorge39 on 2016-06-05
As expected nvidia is not enabled but it is available. Prime isn't though...

The ouput of 
```

dpkg -l | grep -i nvidia 
cat /var/log/gpu-manager.log

```

Is the following:
[http://imgur.com/a/VhkZI](http://imgur.com/a/VhkZI)

---

### Post by Bashing-om on 2016-06-05
jorge39; Ouch ....

I am so confused .. Conflicts in the information .
What hardware does the system see ?
```

lspci -k | grep -EA2 'VGA|3D'

```
Please use code tags for this forum ... I find it very difficult - in my work flow and thought process - to work with images ,
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Try try again to clean things up and get a driver to install.

[INDENT][INDENT]should not be
[INDENT][INDENT][INDENT]such a big deal
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jorge39 on 2016-06-07
Sorry about the images. Here is the ouput of lscpi -k | grep -EA2 'VGA|3D':

```
jorge@jorge-HP-ENVY-15-Notebook-PC:~$ lspci -k | grep -EA2 'VGA|3D'00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
	Subsystem: Hewlett-Packard Company Device 1967
	Kernel driver in use: i915
--
07:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 840M] (rev a2)
	Subsystem: Hewlett-Packard Company Device 21a0
08:00.0 Network controller: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter (rev 03)

```

The system sees nvidia, but it is not enabled... :confused:

---

### Post by Bashing-om on 2016-06-07
jorge39; K;


Code tags are good, that I can work the easier with, thanks !

Back to square one . We have hybrid graphics, and Nvidia recommends the 361 version driver for this system.
So, did the driver build ?
We look at the log file:
```

cat /var/log/Xorg.0.log

```

Is the system able to build the driver ?
We look at log file:
```

/var/log/gpu-manager.log

```

And, what is the source for any proprietary driver that we might be building ?
```

lsb_release -a
uname -r
cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

Depending on what is, 
[INDENT][INDENT]is what we do
[/INDENT][/INDENT]

---

### Post by jorge39 on 2016-06-07
I don't have nvidia 361 installed. Should I purge all nvidia content and install the nvidia 361? Currently I have the nvidia version 352...

With this in mind the output of the Xorg.0.log file is the following: 
```
X.Org X Server 1.17.2Release Date: 2015-06-16
[    98.537] X Protocol Version 11, Revision 0
[    98.537] Build Operating System: Linux 3.19.0-43-generic x86_64 Ubuntu
[    98.537] Current Operating System: Linux jorge-HP-ENVY-15-Notebook-PC 4.2.0-34-generic #39~14.04.1-Ubuntu SMP Fri Mar 11 11:38:02 UTC 2016 x86_64
[    98.537] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-34-generic.efi.signed root=UUID=5c039739-bd2b-4ff7-89d9-51fc0a0105d8 ro recovery nomodeset
[    98.537] Build Date: 15 January 2016  10:17:33PM
[    98.537] xorg-server 2:1.17.2-1ubuntu9.1~trusty1 (For technical support please see http://www.ubuntu.com/support) 
[    98.537] Current version of pixman: 0.30.2
[    98.537] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    98.537] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    98.537] (==) Log file: "/var/log/Xorg.0.log", Time: Sat May  7 02:38:46 2016
[    98.637] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    98.671] (==) No Layout section.  Using the first Screen section.
[    98.671] (==) No screen section available. Using defaults.
[    98.671] (**) |-->Screen "Default Screen Section" (0)
[    98.671] (**) |   |-->Monitor "<default monitor>"
[    98.671] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    98.671] (==) Automatically adding devices
[    98.671] (==) Automatically enabling devices
[    98.671] (==) Automatically adding GPU devices
[    98.721] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    98.721] 	Entry deleted from font path.
[    98.721] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    98.721] 	Entry deleted from font path.
[    98.721] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    98.721] 	Entry deleted from font path.
[    98.721] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    98.721] 	Entry deleted from font path.
[    98.721] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    98.721] 	Entry deleted from font path.
[    98.721] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    98.721] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    98.721] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    98.748] (II) Loader magic: 0x558b1ca23c80
[    98.748] (II) Module ABI versions:
[    98.748] 	X.Org ANSI C Emulation: 0.4
[    98.748] 	X.Org Video Driver: 19.0
[    98.748] 	X.Org XInput driver : 21.0
[    98.748] 	X.Org Server Extension : 9.0
[    98.748] (II) xfree86: Adding drm device (/dev/dri/card0)
[    98.749] (--) PCI:*(0:0:2:0) 8086:0416:103c:1967 rev 6, Mem @ 0xb7000000/4194304, 0xc0000000/268435456, I/O @ 0x00007000/64
[    98.749] (--) PCI: (0:7:0:0) 10de:1341:103c:21a0 rev 162, Mem @ 0xb5000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00005000/128
[    98.760] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    98.760] (II) "glx" will be loaded by default.
[    98.760] (II) LoadModule: "glx"
[    98.806] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    99.683] (II) Module glx: vendor="NVIDIA Corporation"
[    99.683] 	compiled for 4.0.2, module version = 1.0.0
[    99.683] 	Module class: X.Org Server Extension
[    99.691] (II) NVIDIA GLX Module  352.63  Sat Nov  7 20:52:00 PST 2015
[    99.699] (==) Matched nvidia as autoconfigured driver 0
[    99.699] (==) Matched nouveau as autoconfigured driver 1
[    99.699] (==) Matched intel as autoconfigured driver 2
[    99.699] (==) Matched modesetting as autoconfigured driver 3
[    99.699] (==) Matched fbdev as autoconfigured driver 4
[    99.699] (==) Matched vesa as autoconfigured driver 5
[    99.699] (==) Assigned the driver to the xf86ConfigLayout
[    99.699] (II) LoadModule: "nvidia"
[    99.700] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    99.787] (II) Module nvidia: vendor="NVIDIA Corporation"
[    99.787] 	compiled for 4.0.2, module version = 1.0.0
[    99.787] 	Module class: X.Org Video Driver
[    99.798] (II) LoadModule: "nouveau"
[    99.804] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    99.822] (II) Module nouveau: vendor="X.Org Foundation"
[    99.822] 	compiled for 1.17.2, module version = 1.0.11
[    99.822] 	Module class: X.Org Video Driver
[    99.822] 	ABI class: X.Org Video Driver, version 19.0
[    99.822] (II) LoadModule: "intel"
[    99.822] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    99.863] (II) Module intel: vendor="X.Org Foundation"
[    99.863] 	compiled for 1.17.2, module version = 2.99.917
[    99.863] 	Module class: X.Org Video Driver
[    99.863] 	ABI class: X.Org Video Driver, version 19.0
[    99.863] (II) LoadModule: "modesetting"
[    99.863] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    99.866] (II) Module modesetting: vendor="X.Org Foundation"
[    99.866] 	compiled for 1.17.2, module version = 1.17.2
[    99.866] 	Module class: X.Org Video Driver
[    99.866] 	ABI class: X.Org Video Driver, version 19.0
[    99.866] (II) LoadModule: "fbdev"
[    99.866] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    99.877] (II) Module fbdev: vendor="X.Org Foundation"
[    99.877] 	compiled for 1.17.2, module version = 0.4.4
[    99.877] 	Module class: X.Org Video Driver
[    99.877] 	ABI class: X.Org Video Driver, version 19.0
[    99.877] (II) LoadModule: "vesa"
[    99.877] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    99.877] (II) Module vesa: vendor="X.Org Foundation"
[    99.877] 	compiled for 1.17.2, module version = 2.3.4
[    99.877] 	Module class: X.Org Video Driver
[    99.877] 	ABI class: X.Org Video Driver, version 19.0
[    99.877] (II) NVIDIA dlloader X Driver  352.63  Sat Nov  7 20:29:25 PST 2015
[    99.877] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    99.888] (II) NOUVEAU driver Date:   Thu Aug 28 03:57:48 2014 +0200
[    99.888] (II) NOUVEAU driver for NVIDIA chipset families :
[    99.888] 	RIVA TNT        (NV04)
[    99.888] 	RIVA TNT2       (NV05)
[    99.888] 	GeForce 256     (NV10)
[    99.888] 	GeForce 2       (NV11, NV15)
[    99.888] 	GeForce 4MX     (NV17, NV18)
[    99.888] 	GeForce 3       (NV20)
[    99.888] 	GeForce 4Ti     (NV25, NV28)
[    99.888] 	GeForce FX      (NV3x)
[    99.888] 	GeForce 6       (NV4x)
[    99.888] 	GeForce 7       (G7x)
[    99.888] 	GeForce 8       (G8x)
[    99.888] 	GeForce GTX 200 (NVA0)
[    99.888] 	GeForce GTX 400 (NVC0)
[    99.888] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
	i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
	915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
	Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
	GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    99.888] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    99.888] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    99.888] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    99.888] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    99.888] (II) FBDEV: driver for framebuffer: fbdev
[    99.888] (II) VESA: driver for VESA chipsets: vesa
[    99.888] (++) using VT number 7


[    99.889] (EE) [drm] KMS not enabled
[    99.892] (WW) Falling back to old probe method for modesetting
[    99.892] (II) Loading sub module "fbdevhw"
[    99.892] (II) LoadModule: "fbdevhw"
[    99.892] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    99.897] (II) Module fbdevhw: vendor="X.Org Foundation"
[    99.897] 	compiled for 1.17.2, module version = 0.0.2
[    99.897] 	ABI class: X.Org Video Driver, version 19.0
[    99.897] (**) FBDEV(1): claimed PCI slot 0@0:2:0
[    99.897] (II) FBDEV(1): using default device
[    99.897] (WW) Falling back to old probe method for vesa
[    99.897] (EE) Screen 0 deleted because of no matching config section.
[    99.897] (II) UnloadModule: "modesetting"
[    99.897] (II) FBDEV(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    99.897] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    99.897] (==) FBDEV(0): RGB weight 888
[    99.897] (==) FBDEV(0): Default visual is TrueColor
[    99.897] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    99.897] (II) FBDEV(0): hardware: EFI VGA (video memory: 8100kB)
[    99.897] (II) FBDEV(0): checking modes against framebuffer device...
[    99.897] (II) FBDEV(0): checking modes against monitor...
[    99.897] (--) FBDEV(0): Virtual size is 1920x1080 (pitch 1920)
[    99.897] (**) FBDEV(0):  Built-in mode "current": 207.4 MHz, 85.3 kHz, 77.2 Hz
[    99.897] (II) FBDEV(0): Modeline "current"x0.0  207.38  1920 1952 2192 2432  1080 1084 1088 1104 -hsync -vsync -csync (85.3 kHz b)
[    99.897] (==) FBDEV(0): DPI set to (96, 96)
[    99.897] (II) Loading sub module "fb"
[    99.897] (II) LoadModule: "fb"
[    99.897] (II) Loading /usr/lib/xorg/modules/libfb.so
[    99.908] (II) Module fb: vendor="X.Org Foundation"
[    99.908] 	compiled for 1.17.2, module version = 1.0.0
[    99.908] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    99.908] (**) FBDEV(0): using shadow framebuffer
[    99.908] (II) Loading sub module "shadow"
[    99.908] (II) LoadModule: "shadow"
[    99.908] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    99.908] (II) Module shadow: vendor="X.Org Foundation"
[    99.908] 	compiled for 1.17.2, module version = 1.1.0
[    99.908] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    99.908] (II) UnloadModule: "nvidia"
[    99.908] (II) Unloading nvidia
[    99.909] (II) UnloadModule: "vesa"
[    99.909] (II) Unloading vesa
[    99.909] (==) Depth 24 pixmap format is 32 bpp
[    99.909] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    99.923] (==) FBDEV(0): Backing store enabled
[    99.923] (==) FBDEV(0): DPMS enabled
[    99.924] (==) RandR enabled
[    99.936] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[   100.040] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   100.049] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[   100.049] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   100.049] (II) LoadModule: "evdev"
[   100.050] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   100.078] (II) Module evdev: vendor="X.Org Foundation"
[   100.078] 	compiled for 1.17.2, module version = 2.9.2
[   100.078] 	Module class: X.Org XInput Driver
[   100.078] 	ABI class: X.Org XInput driver, version 21.0
[   100.078] (II) Using input driver 'evdev' for 'Power Button'
[   100.078] (**) Power Button: always reports core events
[   100.078] (**) evdev: Power Button: Device: "/dev/input/event2"
[   100.078] (--) evdev: Power Button: Vendor 0 Product 0x1
[   100.078] (--) evdev: Power Button: Found keys
[   100.078] (II) evdev: Power Button: Configuring as keyboard
[   100.078] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[   100.078] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   100.078] (**) Option "xkb_rules" "evdev"
[   100.078] (**) Option "xkb_model" "pc105"
[   100.078] (**) Option "xkb_layout" "pt"
[   100.079] (II) XKB: reuse xkmfile /var/lib/xkb/server-8F12297C8ADF2DCAF94655EF02F153CE34CF92F1.xkm
[   100.080] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   100.080] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   100.080] (II) Using input driver 'evdev' for 'Power Button'
[   100.080] (**) Power Button: always reports core events
[   100.080] (**) evdev: Power Button: Device: "/dev/input/event1"
[   100.080] (--) evdev: Power Button: Vendor 0 Product 0x1
[   100.080] (--) evdev: Power Button: Found keys
[   100.080] (II) evdev: Power Button: Configuring as keyboard
[   100.080] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[   100.080] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   100.080] (**) Option "xkb_rules" "evdev"
[   100.080] (**) Option "xkb_model" "pc105"
[   100.080] (**) Option "xkb_layout" "pt"
[   100.080] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   100.080] (II) No input driver specified, ignoring this device.
[   100.080] (II) This device may have been added with another device file.
[   100.080] (II) config/udev: Adding input device HP Truevision HD (/dev/input/event10)
[   100.080] (**) HP Truevision HD: Applying InputClass "evdev keyboard catchall"
[   100.080] (II) Using input driver 'evdev' for 'HP Truevision HD'
[   100.080] (**) HP Truevision HD: always reports core events
[   100.080] (**) evdev: HP Truevision HD: Device: "/dev/input/event10"
[   100.080] (--) evdev: HP Truevision HD: Vendor 0x4f2 Product 0xb40d
[   100.080] (--) evdev: HP Truevision HD: Found keys
[   100.080] (II) evdev: HP Truevision HD: Configuring as keyboard
[   100.080] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.0/input/input11/event10"
[   100.080] (II) XINPUT: Adding extended input device "HP Truevision HD" (type: KEYBOARD, id 8)
[   100.080] (**) Option "xkb_rules" "evdev"
[   100.080] (**) Option "xkb_model" "pc105"
[   100.080] (**) Option "xkb_layout" "pt"
[   100.081] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event9)
[   100.081] (II) No input driver specified, ignoring this device.
[   100.081] (II) This device may have been added with another device file.
[   100.081] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event8)
[   100.081] (II) No input driver specified, ignoring this device.
[   100.081] (II) This device may have been added with another device file.
[   100.081] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[   100.081] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   100.081] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   100.081] (**) AT Translated Set 2 keyboard: always reports core events
[   100.081] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[   100.081] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   100.081] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   100.081] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   100.081] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[   100.081] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[   100.081] (**) Option "xkb_rules" "evdev"
[   100.081] (**) Option "xkb_model" "pc105"
[   100.081] (**) Option "xkb_layout" "pt"
[   100.081] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event4)
[   100.081] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   100.081] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   100.081] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[   100.081] (II) LoadModule: "synaptics"
[   100.081] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   100.091] (II) Module synaptics: vendor="X.Org Foundation"
[   100.091] 	compiled for 1.17.2, module version = 1.8.2
[   100.091] 	Module class: X.Org XInput Driver
[   100.091] 	ABI class: X.Org XInput driver, version 21.0
[   100.091] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[   100.091] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   100.091] (**) Option "Device" "/dev/input/event4"
[   100.108] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[   100.108] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1282 - 5660 (res 41)
[   100.108] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1152 - 4702 (res 56)
[   100.108] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   100.108] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[   100.108] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[   100.108] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[   100.108] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[   100.108] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   100.108] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   100.124] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event4"
[   100.124] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 10)
[   100.124] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[   100.124] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[   100.124] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.035
[   100.124] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   100.124] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[   100.124] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   100.124] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   100.124] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   100.124] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[   100.124] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[   100.124] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event6)
[   100.124] (II) No input driver specified, ignoring this device.
[   100.124] (II) This device may have been added with another device file.
[   100.124] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[   100.125] (II) No input driver specified, ignoring this device.
[   100.125] (II) This device may have been added with another device file.
[   100.125] (II) config/udev: Adding input device HP Wireless hotkeys (/dev/input/event5)
[   100.125] (**) HP Wireless hotkeys: Applying InputClass "evdev keyboard catchall"
[   100.125] (II) Using input driver 'evdev' for 'HP Wireless hotkeys'
[   100.125] (**) HP Wireless hotkeys: always reports core events
[   100.125] (**) evdev: HP Wireless hotkeys: Device: "/dev/input/event5"
[   100.125] (--) evdev: HP Wireless hotkeys: Vendor 0 Product 0
[   100.125] (--) evdev: HP Wireless hotkeys: Found keys
[   100.125] (II) evdev: HP Wireless hotkeys: Configuring as keyboard
[   100.125] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event5"
[   100.125] (II) XINPUT: Adding extended input device "HP Wireless hotkeys" (type: KEYBOARD, id 11)
[   100.125] (**) Option "xkb_rules" "evdev"
[   100.125] (**) Option "xkb_model" "pc105"
[   100.125] (**) Option "xkb_layout" "pt"
[   100.126] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event7)
[   100.126] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[   100.126] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[   100.126] (**) HP WMI hotkeys: always reports core events
[   100.126] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event7"
[   100.126] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[   100.126] (--) evdev: HP WMI hotkeys: Found keys
[   100.126] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[   100.126] (**) Option "config_info" "udev:/sys/devices/virtual/input/input8/event7"
[   100.126] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 12)
[   100.126] (**) Option "xkb_rules" "evdev"
[   100.126] (**) Option "xkb_model" "pc105"
[   100.126] (**) Option "xkb_layout" "pt"
[   100.127] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[   100.405] (II) config/udev: removing GPU device /sys/devices/pci0000:00/0000:00:01.1/0000:07:00.0/drm/card0 /dev/dri/card0
[   100.405] xf86: remove device 0 /sys/devices/pci0000:00/0000:00:01.1/0000:07:00.0/drm/card0
[   558.237] (II) evdev: HP WMI hotkeys: Close
[   558.238] (II) UnloadModule: "evdev"
[   558.238] (II) evdev: HP Wireless hotkeys: Close
[   558.238] (II) UnloadModule: "evdev"
[   558.238] (II) UnloadModule: "synaptics"
[   558.238] (II) evdev: AT Translated Set 2 keyboard: Close
[   558.238] (II) UnloadModule: "evdev"
[   558.238] (II) evdev: HP Truevision HD: Close
[   558.238] (II) UnloadModule: "evdev"
[   558.238] (II) evdev: Power Button: Close
[   558.238] (II) UnloadModule: "evdev"
[   558.238] (II) evdev: Power Button: Close
[   558.238] (II) UnloadModule: "evdev"
[   558.239] (II) Server terminated successfully (0). Closing log file.


 
``` 

The nvidia kernel module is available as we can see in the output of /var/log/gpu-manager.log:
```
log_file: /var/log/gpu-manager.loglast_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
grep dmesg status 256
dmesg status 256 == 0? No
grep dmesg status 256
dmesg status 256 == 0? No
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is fglrx loaded? no
Was fglrx unloaded? no
Is fglrx blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is fglrx kernel module available? no
**Is nvidia kernel module available? yes**
Vendor/Device Id: 8086:416
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:1341
BusID "PCI:7@0:0:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:07:00.0/driver
The device is not bound to any driver. Skipping...
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Found "/dev/dri/card0", driven by "i915"
output 0:
	eDP connector
Number of connected outputs for /dev/dri/card0: 1
Does it require offloading? yes
last cards number = 1
Has amd? no
Has intel? yes
Has nvidia? no
How many cards? 1
Has the system changed? No
main_arch_path x86_64-linux-gnu, other_arch_path i386-linux-gnu
Current alternative: /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf
Current core alternative: (null)
Is nvidia enabled? no
Is fglrx enabled? no
Is mesa enabled? yes
Is pxpress enabled? no
Is prime enabled? no
Is nvidia available? yes
Is fglrx available? no
Is fglrx-core available? no
Is mesa available? yes
Is pxpress available? no
Is prime available? no
Single card detected
Nothing to do
No change - nothing to do


 
```

Finally, we have:
```
jorge@jorge-HP-ENVY-15-Notebook-PC:~$ lsb_release -aNo LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty

```
[I]
uname -r[/I]
```

jorge@jorge-HP-ENVY-15-Notebook-PC:~$ uname -r
4.2.0-37-generic

```
*/apt/sources.list*
```

jorge@jorge-HP-ENVY-15-Notebook-PC:~$ cat -n /etc/apt/sources.list
     1	# deb cdrom:[Ubuntu 14.04.4 LTS _Trusty Tahr_ - Release amd64 (20160217.1)]/ trusty main restricted
     2	deb-src http://archive.ubuntu.com/ubuntu trusty main restricted #Added by software-properties
     3	
     4	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     5	# newer versions of the distribution.
     6	deb http://archive.ubuntu.com/ubuntu trusty main restricted multiverse
     7	deb-src http://archive.ubuntu.com/ubuntu trusty multiverse universe #Added by software-properties
     8	
     9	## Major bug fix updates produced after the final release of the
    10	## distribution.
    11	deb http://archive.ubuntu.com/ubuntu trusty-updates main restricted multiverse
    12	deb-src http://archive.ubuntu.com/ubuntu trusty-updates multiverse restricted universe main #Added by software-properties
    13	
    14	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    15	## team. Also, please note that software in universe WILL NOT receive any
    16	## review or updates from the Ubuntu security team.
    17	deb http://archive.ubuntu.com/ubuntu trusty universe
    18	deb http://archive.ubuntu.com/ubuntu trusty-updates universe
    19	
    20	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    21	## team, and may not be under a free licence. Please satisfy yourself as to 
    22	## your rights to use the software. Also, please note that software in 
    23	## multiverse WILL NOT receive any review or updates from the Ubuntu
    24	## security team.
    25	
    26	## N.B. software from this repository may not have been tested as
    27	## extensively as that contained in the main release, although it includes
    28	## newer versions of some applications which may provide useful features.
    29	## Also, please note that software in backports WILL NOT receive any review
    30	## or updates from the Ubuntu security team.
    31	deb http://archive.ubuntu.com/ubuntu trusty-backports main restricted universe multiverse
    32	deb-src http://archive.ubuntu.com/ubuntu trusty-backports main restricted universe multiverse #Added by software-properties
    33	
    34	deb http://archive.ubuntu.com/ubuntu trusty-security main restricted multiverse
    35	deb-src http://archive.ubuntu.com/ubuntu trusty-security multiverse restricted universe main #Added by software-properties
    36	deb http://archive.ubuntu.com/ubuntu trusty-security universe
    37	
    38	## Uncomment the following two lines to add software from Canonical's
    39	## 'partner' repository.
    40	## This software is not part of Ubuntu, but is offered by Canonical and the
    41	## respective vendors as a service to Ubuntu users.
    42	deb http://archive.canonical.com/ubuntu trusty partner
    43	deb-src http://archive.canonical.com/ubuntu trusty partner
    44	
    45	## This software is not part of Ubuntu, but is offered by third-party
    46	## developers who want to ship their latest software.
    47	deb http://extras.ubuntu.com/ubuntu trusty main
    48	deb-src http://extras.ubuntu.com/ubuntu trusty main
    49	deb http://archive.canonical.com/ trusty partner
    50	deb-src http://archive.canonical.com/ trusty partner
    51	deb http://archive.ubuntu.com/ubuntu trusty-proposed universe multiverse main restricted

```
[I]
/apt/sources.list.d/*[/I]
```

jorge@jorge-HP-ENVY-15-Notebook-PC:~$ tail -v -n +1 /etc/apt/sources.list.d/* 

(...)



==> /etc/apt/sources.list.d/graphics-drivers-ppa-trusty.list <==
deb http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu trusty main


==> /etc/apt/sources.list.d/graphics-drivers-ppa-trusty.list.save <==
deb http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu trusty main

(...)


```

---

### Post by Bashing-om on 2016-06-07
jorge39; OK ..

You are booting with the boot parameter "nomodeset" . This defeats Kernel mode Setting such that the fall back graphic's driver is loaded. Can not and will not load the proprietary driver.
Are you presently booting from recovery mode ... or is this boot parameter set in /etc/default/grub ?

The 352 version driver appears to have built.
What results when booting normally ?
Maybe we also have  an authorization access issue to your /home ?
Maybe we have a config issue in your user profile for the Desktop Environment ?

And you do have our trusted Graphic's driver PPA available in your sources. 
If it proves that 352 is problematic in your install, then:
I am in favor once we have the "nomodeset" parameter out of the way .. to purge and install the 361 driver that is available from that PPA.

Has to be a reason.
[INDENT][INDENT][INDENT]we be looking
[/INDENT][/INDENT][/INDENT]

---

### Post by jorge39 on 2016-06-08
I am booting normally, not from recovery mode. It always shows the "low-graphics mode" option and I always choose "Run in low-graphics mode for just one session."

I am not sure about having an authorized access issue to my /home/. When I have some free time later I will see if I have a config issue in m user profile.

In the section "Additional drivers - Other software" it is only selected *[http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) trusty main* and _not_ the *[http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) trusty main[COLOR=#000000] _(_[/COLOR]_Source Code)_* option.

I also don't remember of having any problematic issue when I installed the latest available version (352).

---

### Post by Bashing-om on 2016-06-08
jorge39; Morning .

Let's see what we can do:
As you say:
> 
I am booting normally, not from recovery mode. It always shows the "low-graphics mode"

and the log file reflects "nomodeset" as a boot parameter... maybe that is set in the config file  /etc/default/grub ?
Show:
```

cat /etc/default/grub

```
> 
I am not sure about having an authorized access issue to my /home/.

verify that "you" own all the files in your /home less ". and ..":
```

ls -al /home/jorge

```
where "jorge" is the username you use on this system .

We can activate the "guest" session from the login screen as a verification that user config is not an issue .
What results when you activate the system as "guest " .. Do you boot to a functional GUI ?

> 
In the section "Additional drivers - Other software" it is only selected

It is fine not to have the "src" PPA enabled .. you do not need to mess with the driver source code. We get the binary already built with the normal non-source PPA active.

Brings to mind to verify that you are fully updated:
```

sudo apt update
sudo apt full-upgrade

```
and that the kernel header files are installed:
```

dpkg -l | grep linux-

```

The log file does reflect that the 352 version driver builds .. It should work ...

So, we are still looking for that
[INDENT][INDENT]why not
[/INDENT][/INDENT]

---

### Post by jorge39 on 2016-06-09
My grup log file is currently set this way:

```
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

```


Actually I don't own the file ".." in my home directory:


```
drwxrwxr-x 32 jorge jorge  4096 Jun  9 16:29 .
drwxr-xr-x  3 root  root   4096 Fev 29 10:24 ..

```

I also did the update and full upgrade but it still shows the "low-graphics mode" problem...

---

### Post by Bashing-om on 2016-06-09
jorge39; Sheesshhhhh ...

As the mystery deepens:
In your /home .. it is correct that '.' is owned by you ... my bad to say otherwise.

I see no fault with the /etc/default/grub file ...

So we are back to looking at the log file /var/log/Xorg.0.log ->
The line " Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-87-generic root=UUID=3a47f1f1-ed1f-4134-b6aa-be101a7d97b4 ro  XXXXXX " does it still reflect nomodeset as a boot option ?

If so .. and as it is not set in the config file nor are you setting nomodeset nor booting up in "recovery mode"  ; It is above my skill level to determine where else that "nomodeset" can originate from . So long as "nomodeset" is in effect .. one will boot in a degraded graphics state; as only a rudimentary graphic's driver is loaded .

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by jorge39 on 2016-06-13
Sorry for the late response but I had a busy weekend. 

Yes, the nomodeset is still set as a boot option in the /var/log/Xorg.0.log file... :confused:

---

### Post by Bashing-om on 2016-06-13
jorge39; Yuk !

I am aware of only 3 ways that "nomodeset" can be set :
1) Directly by user intervention my inserting that boot parameter as a kernel boot parameter from the grub boot menu, while booting ;
2) By booting the system in "recovery" mode ;
3) As an edit to the config file /etc/default/grub

Now if none of these apply to this situation, it is above my skill level to know .. I AM very interested to learn what is taking place here .

because;
[INDENT][INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT][/INDENT]

---

### Post by QLee on 2016-06-14
> **Bashing-om said:**
> I see no fault with the /etc/default/grub file ...
[INDENT][INDENT]...inquiring minds want to know
[/INDENT][/INDENT]

HI Bashing-om,

I had a quick read through of the 7 pages, I don't have much time today. It looks like at one time nomodeset was an option in /etc/default/grub and I don't think I saw any time that grub-mkconfig (update-grub) was run when it wasn't in there. I might have just missed it in the long thread. So maybe the initrd.img might be responsible.

You could check that if you think it is a possibility.

---

### Post by Bashing-om on 2016-06-14
@QLee; Appreciate that input .

That is a great thought . Glad to have confirmation that it must be one of the 3 options that set "nomodeset" .

A thought too .. that if worse comes to worse .. we can re-generate the initrd.img file. We can run update-initramfs manually in 'verbose' mode so it tells us what it is doing, making up a log file, and examine that to see if it gives clues.

[INDENT][INDENT]inquiring minds
[INDENT][INDENT][INDENT]still want to know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by QLee on 2016-06-14
If it is generated now, it should be correct as I agree things in default look OK now. Might be worthwhile to check the timestamp on the current image before you go to much effort, to get an idea of when it was created.

---

### Post by jorge39 on 2016-06-15
So, just to make sure I am not missleading you I will show the output of cat /var/log/Xorg.0.log

```
 jorge@jorge-HP-ENVY-15-Notebook-PC:~$ cat /var/log/Xorg.0.log [    98.537] 
X.Org X Server 1.17.2
Release Date: 2015-06-16
[    98.537] X Protocol Version 11, Revision 0
[    98.537] Build Operating System: Linux 3.19.0-43-generic x86_64 Ubuntu
[    98.537] Current Operating System: Linux jorge-HP-ENVY-15-Notebook-PC 4.2.0-34-generic #39~14.04.1-Ubuntu SMP Fri Mar 11 11:38:02 UTC 2016 x86_64
[    98.537] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-34-generic.efi.signed root=UUID=5c039739-bd2b-4ff7-89d9-51fc0a0105d8 ro recovery nomodeset
[    98.537] Build Date: 15 January 2016  10:17:33PM
[    98.537] xorg-server 2:1.17.2-1ubuntu9.1~trusty1 (For technical support please see http://www.ubuntu.com/support) 
[    98.537] Current version of pixman: 0.30.2
[    98.537] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    98.537] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    98.537] (==) Log file: "/var/log/Xorg.0.log", Time: Sat May  7 02:38:46 2016
[    98.637] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    98.671] (==) No Layout section.  Using the first Screen section.
[    98.671] (==) No screen section available. Using defaults.
[    98.671] (**) |-->Screen "Default Screen Section" (0)
[    98.671] (**) |   |-->Monitor "<default monitor>"
[    98.671] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    98.671] (==) Automatically adding devices
[    98.671] (==) Automatically enabling devices
[    98.671] (==) Automatically adding GPU devices
[    98.721] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    98.721] 	Entry deleted from font path.
[    98.721] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    98.721] 	Entry deleted from font path.
[    98.721] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    98.721] 	Entry deleted from font path.
[    98.721] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    98.721] 	Entry deleted from font path.
[    98.721] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    98.721] 	Entry deleted from font path.
[    98.721] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    98.721] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    98.721] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    98.748] (II) Loader magic: 0x558b1ca23c80
[    98.748] (II) Module ABI versions:
[    98.748] 	X.Org ANSI C Emulation: 0.4
[    98.748] 	X.Org Video Driver: 19.0
[    98.748] 	X.Org XInput driver : 21.0
[    98.748] 	X.Org Server Extension : 9.0
[    98.748] (II) xfree86: Adding drm device (/dev/dri/card0)
[    98.749] (--) PCI:*(0:0:2:0) 8086:0416:103c:1967 rev 6, Mem @ 0xb7000000/4194304, 0xc0000000/268435456, I/O @ 0x00007000/64
[    98.749] (--) PCI: (0:7:0:0) 10de:1341:103c:21a0 rev 162, Mem @ 0xb5000000/16777216, 0xa0000000/268435456, 0xb0000000/33554432, I/O @ 0x00005000/128
[    98.760] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    98.760] (II) "glx" will be loaded by default.
[    98.760] (II) LoadModule: "glx"
[    98.806] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    99.683] (II) Module glx: vendor="NVIDIA Corporation"
[    99.683] 	compiled for 4.0.2, module version = 1.0.0
[    99.683] 	Module class: X.Org Server Extension
[    99.691] (II) NVIDIA GLX Module  352.63  Sat Nov  7 20:52:00 PST 2015
[    99.699] (==) Matched nvidia as autoconfigured driver 0
[    99.699] (==) Matched nouveau as autoconfigured driver 1
[    99.699] (==) Matched intel as autoconfigured driver 2
[    99.699] (==) Matched modesetting as autoconfigured driver 3
[    99.699] (==) Matched fbdev as autoconfigured driver 4
[    99.699] (==) Matched vesa as autoconfigured driver 5
[    99.699] (==) Assigned the driver to the xf86ConfigLayout
[    99.699] (II) LoadModule: "nvidia"
[    99.700] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    99.787] (II) Module nvidia: vendor="NVIDIA Corporation"
[    99.787] 	compiled for 4.0.2, module version = 1.0.0
[    99.787] 	Module class: X.Org Video Driver
[    99.798] (II) LoadModule: "nouveau"
[    99.804] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    99.822] (II) Module nouveau: vendor="X.Org Foundation"
[    99.822] 	compiled for 1.17.2, module version = 1.0.11
[    99.822] 	Module class: X.Org Video Driver
[    99.822] 	ABI class: X.Org Video Driver, version 19.0
[    99.822] (II) LoadModule: "intel"
[    99.822] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    99.863] (II) Module intel: vendor="X.Org Foundation"
[    99.863] 	compiled for 1.17.2, module version = 2.99.917
[    99.863] 	Module class: X.Org Video Driver
[    99.863] 	ABI class: X.Org Video Driver, version 19.0
[    99.863] (II) LoadModule: "modesetting"
[    99.863] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    99.866] (II) Module modesetting: vendor="X.Org Foundation"
[    99.866] 	compiled for 1.17.2, module version = 1.17.2
[    99.866] 	Module class: X.Org Video Driver
[    99.866] 	ABI class: X.Org Video Driver, version 19.0
[    99.866] (II) LoadModule: "fbdev"
[    99.866] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    99.877] (II) Module fbdev: vendor="X.Org Foundation"
[    99.877] 	compiled for 1.17.2, module version = 0.4.4
[    99.877] 	Module class: X.Org Video Driver
[    99.877] 	ABI class: X.Org Video Driver, version 19.0
[    99.877] (II) LoadModule: "vesa"
[    99.877] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    99.877] (II) Module vesa: vendor="X.Org Foundation"
[    99.877] 	compiled for 1.17.2, module version = 2.3.4
[    99.877] 	Module class: X.Org Video Driver
[    99.877] 	ABI class: X.Org Video Driver, version 19.0
[    99.877] (II) NVIDIA dlloader X Driver  352.63  Sat Nov  7 20:29:25 PST 2015
[    99.877] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    99.888] (II) NOUVEAU driver Date:   Thu Aug 28 03:57:48 2014 +0200
[    99.888] (II) NOUVEAU driver for NVIDIA chipset families :
[    99.888] 	RIVA TNT        (NV04)
[    99.888] 	RIVA TNT2       (NV05)
[    99.888] 	GeForce 256     (NV10)
[    99.888] 	GeForce 2       (NV11, NV15)
[    99.888] 	GeForce 4MX     (NV17, NV18)
[    99.888] 	GeForce 3       (NV20)
[    99.888] 	GeForce 4Ti     (NV25, NV28)
[    99.888] 	GeForce FX      (NV3x)
[    99.888] 	GeForce 6       (NV4x)
[    99.888] 	GeForce 7       (G7x)
[    99.888] 	GeForce 8       (G8x)
[    99.888] 	GeForce GTX 200 (NVA0)
[    99.888] 	GeForce GTX 400 (NVC0)
[    99.888] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
	i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
	915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
	Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
	GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    99.888] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    99.888] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    99.888] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    99.888] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    99.888] (II) FBDEV: driver for framebuffer: fbdev
[    99.888] (II) VESA: driver for VESA chipsets: vesa
[    99.888] (++) using VT number 7


[    99.889] (EE) [drm] KMS not enabled
[    99.892] (WW) Falling back to old probe method for modesetting
[    99.892] (II) Loading sub module "fbdevhw"
[    99.892] (II) LoadModule: "fbdevhw"
[    99.892] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    99.897] (II) Module fbdevhw: vendor="X.Org Foundation"
[    99.897] 	compiled for 1.17.2, module version = 0.0.2
[    99.897] 	ABI class: X.Org Video Driver, version 19.0
[    99.897] (**) FBDEV(1): claimed PCI slot 0@0:2:0
[    99.897] (II) FBDEV(1): using default device
[    99.897] (WW) Falling back to old probe method for vesa
[    99.897] (EE) Screen 0 deleted because of no matching config section.
[    99.897] (II) UnloadModule: "modesetting"
[    99.897] (II) FBDEV(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    99.897] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    99.897] (==) FBDEV(0): RGB weight 888
[    99.897] (==) FBDEV(0): Default visual is TrueColor
[    99.897] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    99.897] (II) FBDEV(0): hardware: EFI VGA (video memory: 8100kB)
[    99.897] (II) FBDEV(0): checking modes against framebuffer device...
[    99.897] (II) FBDEV(0): checking modes against monitor...
[    99.897] (--) FBDEV(0): Virtual size is 1920x1080 (pitch 1920)
[    99.897] (**) FBDEV(0):  Built-in mode "current": 207.4 MHz, 85.3 kHz, 77.2 Hz
[    99.897] (II) FBDEV(0): Modeline "current"x0.0  207.38  1920 1952 2192 2432  1080 1084 1088 1104 -hsync -vsync -csync (85.3 kHz b)
[    99.897] (==) FBDEV(0): DPI set to (96, 96)
[    99.897] (II) Loading sub module "fb"
[    99.897] (II) LoadModule: "fb"
[    99.897] (II) Loading /usr/lib/xorg/modules/libfb.so
[    99.908] (II) Module fb: vendor="X.Org Foundation"
[    99.908] 	compiled for 1.17.2, module version = 1.0.0
[    99.908] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    99.908] (**) FBDEV(0): using shadow framebuffer
[    99.908] (II) Loading sub module "shadow"
[    99.908] (II) LoadModule: "shadow"
[    99.908] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    99.908] (II) Module shadow: vendor="X.Org Foundation"
[    99.908] 	compiled for 1.17.2, module version = 1.1.0
[    99.908] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    99.908] (II) UnloadModule: "nvidia"
[    99.908] (II) Unloading nvidia
[    99.909] (II) UnloadModule: "vesa"
[    99.909] (II) Unloading vesa
[    99.909] (==) Depth 24 pixmap format is 32 bpp
[    99.909] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    99.923] (==) FBDEV(0): Backing store enabled
[    99.923] (==) FBDEV(0): DPMS enabled
[    99.924] (==) RandR enabled
[    99.936] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[   100.040] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   100.049] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[   100.049] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   100.049] (II) LoadModule: "evdev"
[   100.050] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   100.078] (II) Module evdev: vendor="X.Org Foundation"
[   100.078] 	compiled for 1.17.2, module version = 2.9.2
[   100.078] 	Module class: X.Org XInput Driver
[   100.078] 	ABI class: X.Org XInput driver, version 21.0
[   100.078] (II) Using input driver 'evdev' for 'Power Button'
[   100.078] (**) Power Button: always reports core events
[   100.078] (**) evdev: Power Button: Device: "/dev/input/event2"
[   100.078] (--) evdev: Power Button: Vendor 0 Product 0x1
[   100.078] (--) evdev: Power Button: Found keys
[   100.078] (II) evdev: Power Button: Configuring as keyboard
[   100.078] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[   100.078] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   100.078] (**) Option "xkb_rules" "evdev"
[   100.078] (**) Option "xkb_model" "pc105"
[   100.078] (**) Option "xkb_layout" "pt"
[   100.079] (II) XKB: reuse xkmfile /var/lib/xkb/server-8F12297C8ADF2DCAF94655EF02F153CE34CF92F1.xkm
[   100.080] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   100.080] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   100.080] (II) Using input driver 'evdev' for 'Power Button'
[   100.080] (**) Power Button: always reports core events
[   100.080] (**) evdev: Power Button: Device: "/dev/input/event1"
[   100.080] (--) evdev: Power Button: Vendor 0 Product 0x1
[   100.080] (--) evdev: Power Button: Found keys
[   100.080] (II) evdev: Power Button: Configuring as keyboard
[   100.080] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[   100.080] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   100.080] (**) Option "xkb_rules" "evdev"
[   100.080] (**) Option "xkb_model" "pc105"
[   100.080] (**) Option "xkb_layout" "pt"
[   100.080] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   100.080] (II) No input driver specified, ignoring this device.
[   100.080] (II) This device may have been added with another device file.
[   100.080] (II) config/udev: Adding input device HP Truevision HD (/dev/input/event10)
[   100.080] (**) HP Truevision HD: Applying InputClass "evdev keyboard catchall"
[   100.080] (II) Using input driver 'evdev' for 'HP Truevision HD'
[   100.080] (**) HP Truevision HD: always reports core events
[   100.080] (**) evdev: HP Truevision HD: Device: "/dev/input/event10"
[   100.080] (--) evdev: HP Truevision HD: Vendor 0x4f2 Product 0xb40d
[   100.080] (--) evdev: HP Truevision HD: Found keys
[   100.080] (II) evdev: HP Truevision HD: Configuring as keyboard
[   100.080] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-7/1-7:1.0/input/input11/event10"
[   100.080] (II) XINPUT: Adding extended input device "HP Truevision HD" (type: KEYBOARD, id 8)
[   100.080] (**) Option "xkb_rules" "evdev"
[   100.080] (**) Option "xkb_model" "pc105"
[   100.080] (**) Option "xkb_layout" "pt"
[   100.081] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event9)
[   100.081] (II) No input driver specified, ignoring this device.
[   100.081] (II) This device may have been added with another device file.
[   100.081] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event8)
[   100.081] (II) No input driver specified, ignoring this device.
[   100.081] (II) This device may have been added with another device file.
[   100.081] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[   100.081] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   100.081] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   100.081] (**) AT Translated Set 2 keyboard: always reports core events
[   100.081] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[   100.081] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   100.081] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   100.081] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   100.081] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[   100.081] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[   100.081] (**) Option "xkb_rules" "evdev"
[   100.081] (**) Option "xkb_model" "pc105"
[   100.081] (**) Option "xkb_layout" "pt"
[   100.081] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event4)
[   100.081] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   100.081] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   100.081] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[   100.081] (II) LoadModule: "synaptics"
[   100.081] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   100.091] (II) Module synaptics: vendor="X.Org Foundation"
[   100.091] 	compiled for 1.17.2, module version = 1.8.2
[   100.091] 	Module class: X.Org XInput Driver
[   100.091] 	ABI class: X.Org XInput driver, version 21.0
[   100.091] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[   100.091] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   100.091] (**) Option "Device" "/dev/input/event4"
[   100.108] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[   100.108] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1282 - 5660 (res 41)
[   100.108] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1152 - 4702 (res 56)
[   100.108] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   100.108] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[   100.108] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[   100.108] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[   100.108] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[   100.108] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   100.108] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   100.124] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event4"
[   100.124] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 10)
[   100.124] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[   100.124] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[   100.124] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.035
[   100.124] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   100.124] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[   100.124] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   100.124] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   100.124] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   100.124] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[   100.124] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[   100.124] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event6)
[   100.124] (II) No input driver specified, ignoring this device.
[   100.124] (II) This device may have been added with another device file.
[   100.124] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[   100.125] (II) No input driver specified, ignoring this device.
[   100.125] (II) This device may have been added with another device file.
[   100.125] (II) config/udev: Adding input device HP Wireless hotkeys (/dev/input/event5)
[   100.125] (**) HP Wireless hotkeys: Applying InputClass "evdev keyboard catchall"
[   100.125] (II) Using input driver 'evdev' for 'HP Wireless hotkeys'
[   100.125] (**) HP Wireless hotkeys: always reports core events
[   100.125] (**) evdev: HP Wireless hotkeys: Device: "/dev/input/event5"
[   100.125] (--) evdev: HP Wireless hotkeys: Vendor 0 Product 0
[   100.125] (--) evdev: HP Wireless hotkeys: Found keys
[   100.125] (II) evdev: HP Wireless hotkeys: Configuring as keyboard
[   100.125] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event5"
[   100.125] (II) XINPUT: Adding extended input device "HP Wireless hotkeys" (type: KEYBOARD, id 11)
[   100.125] (**) Option "xkb_rules" "evdev"
[   100.125] (**) Option "xkb_model" "pc105"
[   100.125] (**) Option "xkb_layout" "pt"
[   100.126] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event7)
[   100.126] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[   100.126] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[   100.126] (**) HP WMI hotkeys: always reports core events
[   100.126] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event7"
[   100.126] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[   100.126] (--) evdev: HP WMI hotkeys: Found keys
[   100.126] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[   100.126] (**) Option "config_info" "udev:/sys/devices/virtual/input/input8/event7"
[   100.126] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 12)
[   100.126] (**) Option "xkb_rules" "evdev"
[   100.126] (**) Option "xkb_model" "pc105"
[   100.126] (**) Option "xkb_layout" "pt"
[   100.127] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[   100.405] (II) config/udev: removing GPU device /sys/devices/pci0000:00/0000:00:01.1/0000:07:00.0/drm/card0 /dev/dri/card0
[   100.405] xf86: remove device 0 /sys/devices/pci0000:00/0000:00:01.1/0000:07:00.0/drm/card0
[   558.237] (II) evdev: HP WMI hotkeys: Close
[   558.238] (II) UnloadModule: "evdev"
[   558.238] (II) evdev: HP Wireless hotkeys: Close
[   558.238] (II) UnloadModule: "evdev"
[   558.238] (II) UnloadModule: "synaptics"
[   558.238] (II) evdev: AT Translated Set 2 keyboard: Close
[   558.238] (II) UnloadModule: "evdev"
[   558.238] (II) evdev: HP Truevision HD: Close
[   558.238] (II) UnloadModule: "evdev"
[   558.238] (II) evdev: Power Button: Close
[   558.238] (II) UnloadModule: "evdev"
[   558.238] (II) evdev: Power Button: Close
[   558.238] (II) UnloadModule: "evdev"
[   558.239] (II) Server terminated successfully (0). Closing log file.

```

Should I search a bit about[COLOR=#000000]*initrd.img*?

Thank you[/COLOR]

---

### Post by Bashing-om on 2016-06-15
jorge39; Hey !

This :
> 
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-34-generic.efi.signed root=UUID=5c039739-bd2b-4ff7-89d9-51fc0a0105d8 ro recovery [color=red]nomodeset[/color]
 
is the whole rub of the affair . We do not know where "nomodeset" is set from. So long as this is set, no other driver than the fall back system driver will be able to load. The result is degraded graphics in the GUI .

So we must question how you are booting this system ..
Are you booting from recovery mode ? As this does set the "nomodeset" option .

If and only IF nomodeset  is NOT set in /etc/default/grub... then:
Let's see when the boot config file was created:
```

ls -al /boot/grub/grub.cfg

```

And now let us generate a new boot config file.
run terminal command:
```

sudo update-grub

```
to generate a new boot config file that "should" not contain the nomodeset parameter.
When was the init file generated ?
```

ls -al /initrd*

```
AND what kernel is booted presently ?
```

uname -r

```

Now reboot the system as a normal login and let us see that "nomodeset" is no longer present.

[INDENT][INDENT]just do not know
[INDENT][INDENT]want to find out
[/INDENT][/INDENT][/INDENT][/INDENT]

As we really have to get to the bottom of where the nomodeset is set from .. Until this is removed .. we can not move forward.

---

### Post by jorge39 on 2016-06-16
Nomodeset isn't set in [COLOR=#000000]*/etc/default/grub...*

The boot config file was created on 1st of June:
[/COLOR]```
-r--r--r-- 1 root root 10379 Jun  1 21:16 /boot/grub/grub.cfg

```[COLOR=#000000]

The s*udo update-grub *runs well:
[/COLOR]```
Generating grub configuration file ...Found linux image: /boot/vmlinuz-4.2.0-37-generic
Found initrd image: /boot/initrd.img-4.2.0-37-generic
Found linux image: /boot/vmlinuz-4.2.0-36-generic
Found initrd image: /boot/initrd.img-4.2.0-36-generic
Found linux image: /boot/vmlinuz-4.2.0-34-generic
Found initrd image: /boot/initrd.img-4.2.0-34-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done

```

The *initrd file* was generated on 25 and 30 of may

```
lrwxrwxrwx 1 root root 32 Mai 30 17:28 /initrd.img -> boot/initrd.img-4.2.0-37-generic
lrwxrwxrwx 1 root root 32 Mai 25 09:28 /initrd.img.old -> boot/initrd.img-4.2.0-36-generic
```

The booted kernel is the 4.2.0-37-generic version.

Hope this helps

---

### Post by Bashing-om on 2016-06-16
jorge39; Ho Kay ..

Let's now do a cold boot of the system .. all the way back up from a power down, booting to the login screen.
Here activate a console interface with key combo ctl+alt+F1.
Now let us look and see what the X log file relates:
terminal command:
```

cat /var/log/Xorg.0.log | nc termbin.com 9999

```

Where that file is transferred to the pastebin site, termbin . The result is a URL back in your terminal //Pass that link back here to the thread and we can access that file.

[INDENT][INDENT]now I do not know what to say
[INDENT][INDENT]pending what the log file relates
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jorge39 on 2016-06-17
> **Bashing-om said:**
> jorge39; Ho Kay ..

Let's now do a cold boot of the system .. all the way back up from a power down, booting to the login screen.
Here activate a console interface with key combo ctl+alt+F1.
Now let us look and see what the X log file relates:
terminal command:
```

cat /var/log/Xorg.0.log | nc termbin.com 9999

```

Where that file is transferred to the pastebin site, termbin . The result is a URL back in your terminal //Pass that link back here to the thread and we can access that file.

[INDENT][INDENT]now I do not know what to say
[INDENT][INDENT]pending what the log file relates
[/INDENT][/INDENT][/INDENT][/INDENT]

Okay, so the link is the following:

[ http://termbin.com/m744 ]( http://termbin.com/m744 )

---

### Post by Bashing-om on 2016-06-17
jorge39; Yukkie on me.

We still have that "nomodeset" boot parameter set !  It is now above my skill level to know or to determine what and where it is being set.
It is my hope others here can jump in and give us some direction,

So long as "nomodeset" is present we will not be able to load a higher level graphic's driver.

[INDENT][INDENT]Now I too am in that
[INDENT][INDENT][INDENT]learning mode
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jorge39 on 2016-06-17
> **Bashing-om said:**
> jorge39; Yukkie on me.

We still have that "nomodeset" boot parameter set !  It is now above my skill level to know or to determine what and where it is being set.
It is my hope others here can jump in and give us some direction,

So long as "nomodeset" is present we will not be able to load a higher level graphic's driver.

[INDENT][INDENT]Now I too am in that
[INDENT][INDENT][INDENT]learning mode
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

No problem, thank you for the help so far. I will also try to read a bit more about this.

---

