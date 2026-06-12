---
title: "Radeon 9800 and hardware acceleration?"
date: 2008-05-17
forum: Hardware
---

### Post by coalquay404 on 2008-05-17
I've just installed Hardy on a Dell Dimension 8300. My video card is a Radeon 9800 Pro and I'd really like to get hardware acceleration to work.

I assumed that Administration->Hardware Drivers, which offered to install a driver for my card, would give me hardware acceleration. Silly me! When I installed the drivers and rebooted, GDM comes up but once I attempt to log in to a Gnome session the screen goes white and remains that way. The only way out of this is to Ctrl-Alt-Backspace to reset the window manager.

So my questions are as follows:

    * Is it really so unreasonable to expect that the hardware drivers that the system offers to install for you when you first boot up the system will actually work?
    * Is there any way besides the (obviously broken) Administration->Hardware Drivers method to get hardware acceleration to work for my card?
    * Assuming that I do manage to get my card to work, does Hardy still have that stupid bug where Shift-Backspace will reset the window manager?


Thanks in advance.

PS: For what it's worth, I've also tried installing the driver using EnvyNG (didn't work) as well as the official ATI drivers (didn't work). One of the main problems I seem to be encountering is that even when the driver has been installed properly, fglrxinfo keeps giving telling me that the Mesa drivers are installed, *not* fglrx:

```
coalquay404@bluechip:~$ fglrxinfo 

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)
```

This happens even after following the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Removing_Mesa_drivers](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Removing_Mesa_drivers).

---

### Post by coalquay404 on 2008-05-18
Anyone?

---

### Post by coalquay404 on 2008-05-18
Anyone at all?

---

### Post by coalquay404 on 2008-05-18
Hello?

---

### Post by coalquay404 on 2008-05-19
bump

---

### Post by pietjanjaap on 2008-05-19
Hi
I got the ati 9600, have the same problem.
Tried a lot of things but nothing works.

---

### Post by mr_smitty on 2008-05-19
I have exactly the same problem...I have deactivated Desktop Effects (Compiz) but have extreeeeeemly low performance on all OpenGL programs.

---

### Post by HawleySmoot on 2008-05-19
Same problem, can't remove the mesa drivers even after following that, and the guide it links to.

---

### Post by coalquay404 on 2008-05-20
> **pietjanjaap said:**
> Hi
I got the ati 9600, have the same problem.
Tried a lot of things but nothing works.

> **mr_smitty said:**
> I have exactly the same problem...I have deactivated Desktop Effects (Compiz) but have extreeeeeemly low performance on all OpenGL programs.

> **HawleySmoot said:**
> Same problem, can't remove the mesa drivers even after following that, and the guide it links to.

Precisely. This is apparently an extremely common problem for people who have ATI cards, and in spite of the fact that Ubuntu offers to install drivers for you, few people seem able actually to get hardware acceleration enabled. This is bizarre, particularly given that 3D acceleration worked fine for me on earlier versions of Ubuntu.

I'm going to keep bumping the thread until I find a solution.

---

### Post by pointfivezero on 2008-05-20
bump!

---

### Post by coalquay404 on 2008-05-20
*bump*

C'mon. Somebody must know something about this problem.

---

### Post by coalquay404 on 2008-05-20
Bump!

---

### Post by Zimmer on 2008-05-20
Instructions for Ubuntu 8.04 (Hardy)

To be determined. 

This is the message at 
 [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
I am a Radeon 9600 owner, and still on Dapper, but that is the page I go to for info when upgrading (last time was from Breezy). So, there may be an ATI thread around with some latest info , but I haven't found it yet. If I do, I will post here.
The fact that you have tried various methods already may have led to conflicts with your install, as in the past it has often been necessary to remove certain drivers before installing others...
Also see post #8
[http://ubuntuforums.org/showthread.php?t=800123&highlight=ati+hardy](http://ubuntuforums.org/showthread.php?t=800123&highlight=ati+hardy)
and the latest posts here
[http://ubuntuforums.org/showthread.php?t=221320](http://ubuntuforums.org/showthread.php?t=221320)

---

### Post by mr_smitty on 2008-05-21
Thanks Zimmer...

By following your links I finally made it to [https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684).

At the very end of this page it describes how

> adding lines to /etc/modprobe.d/blacklist:

blacklist i82875p_edac
blacklist edac_mc

fixes the problem. And it sure did for me :)

Best regards
Martin

---

### Post by coalquay404 on 2008-05-21
> **Zimmer said:**
> Instructions for Ubuntu 8.04 (Hardy)

To be determined. 

This is the message at 
 [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
I am a Radeon 9600 owner, and still on Dapper, but that is the page I go to for info when upgrading (last time was from Breezy). So, there may be an ATI thread around with some latest info , but I haven't found it yet. If I do, I will post here.
The fact that you have tried various methods already may have led to conflicts with your install, as in the past it has often been necessary to remove certain drivers before installing others...
Also see post #8
[http://ubuntuforums.org/showthread.php?t=800123&highlight=ati+hardy](http://ubuntuforums.org/showthread.php?t=800123&highlight=ati+hardy)
and the latest posts here
[http://ubuntuforums.org/showthread.php?t=221320](http://ubuntuforums.org/showthread.php?t=221320)

> **mr_smitty said:**
> Thanks Zimmer...

By following your links I finally made it to [https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684).

At the very end of this page it describes how



fixes the problem. And it sure did for me :)

Best regards
Martin

Yup! Thanks a million for the pointer. I would never have figured it out on my own.

---

### Post by wootah on 2008-05-22
Let me know if you have further problems. I have the same card and managed to get everything work (short of composition) including dual nonmirrored monitors.

Cheers!

---

### Post by andlinux on 2008-06-18
Not working here :(

---

### Post by pietjanjaap on 2008-06-19
I got my 9600 ati working, but did so many thing, but search with blacklist, you have to disable something.
After doing several thing i now install like this.

dpkg-reconfigure xserver-xorg is not the same anymore, now you can install your keybord and more with this.
But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the x,
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.
Then reboot and install your videcard driver.(i use envy for this).


i also do this:

Stop Compiz-Fusion From Loading Automatically

This guide will show you how to stop Compiz-Fusion from loading automatically on startup in Hardy Heron and how to setup a shortcut for launching Compiz when you want.

Step 1: Run gconf-edit
Start Run Application by pressing Alt+F2

Screenshot-Run Application

Enter gconf-editor into the box, hit enter


Step 2: Set Metacity as your default start up window manager
Once in gconf-editor navigate to desktop>gnome>applications>window_manager

Screenshot-Configuration Editor - window_manager

under current and default replace each instance of:
/usr/bin/compiz with /usr/bin/metacity
it should like this when you're done:

Screenshot-Configuration Editor - window_manager-1



Step 3: Create a shortcut for starting Compiz-Fusion
right click the Applications Places System Menu
select the Edit Menu option

Screenshot-Main Menu

pick a location for your shortcut and select New Item box

Screenshot-Launcher Properties
Type: Application
Name: Compiz
Command: compiz --replace
COmment compiz window manager

---

### Post by andlinux on 2008-06-20
> **pietjanjaap said:**
> I got my 9600 ati working, but did so many thing, but search with blacklist, you have to disable something.
After doing several thing i now install like this.

dpkg-reconfigure xserver-xorg is not the same anymore, now you can install your keybord and more with this.
But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the x,
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.
Then reboot and install your videcard driver.(i use envy for this).


i also do this:

Stop Compiz-Fusion From Loading Automatically

This guide will show you how to stop Compiz-Fusion from loading automatically on startup in Hardy Heron and how to setup a shortcut for launching Compiz when you want.

Step 1: Run gconf-edit
Start Run Application by pressing Alt+F2

Screenshot-Run Application

Enter gconf-editor into the box, hit enter


Step 2: Set Metacity as your default start up window manager
Once in gconf-editor navigate to desktop>gnome>applications>window_manager

Screenshot-Configuration Editor - window_manager

under current and default replace each instance of:
/usr/bin/compiz with /usr/bin/metacity
it should like this when you're done:

Screenshot-Configuration Editor - window_manager-1



Step 3: Create a shortcut for starting Compiz-Fusion
right click the Applications Places System Menu
select the Edit Menu option

Screenshot-Main Menu

pick a location for your shortcut and select New Item box

Screenshot-Launcher Properties
Type: Application
Name: Compiz
Command: compiz --replace
COmment compiz window manager
I don't use Compiz.

---

### Post by nofear187 on 2008-06-20
this is the type of video card i have and I have the same issue 
as well as I can't enable the video card in the hareware drivers menu
since these drivers that ATI hare are just not cutting it they need to 
break down and pay their people to write new one's! 
oddly enought I was dealing with this same issue in vista 
just with the sound cards and not the video card o figure!
if any one's has got a resolution let me now 

thanks 
adam

---

### Post by andlinux on 2008-06-21
I was trying yesterday to make it work and I had 3D acceleration at one moment but then my external usb mouse didn't work. I used the drivers from ati's website and not those from synaptic. 

This is what I did:

Download the drivers from [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html) -- ati-driver-installer-8-6-x86.x86_64.run --

Be sure that the fglrx packages are removed in synaptic... 

Then, do a sudo apt-get update in a console. 

Next thing, sudo apt-get install build-essential fakeroot dh-make debhelper debconf libstdc++5 dkms linux-headers-$(uname -r) in a console.

And install the downloaded driver with the next command
sudo sh ati-driver-installer-8-6-x86.x86_64.run

in console: sudo aticonfig --initial -f

After that I restarted and I did a fglrxinfo in a console and I had 3D acceleration + glxgears was showing good things ;)

Maybe I can help someone else with this.

---

### Post by ThomThom on 2008-06-21
I had problems getting hardware accelecration working after I updated to Ubuntu 8.04. I also got an Dell Dimmention 8300 with an ATI Radeon 9800.

Problem is that I don't remember what I did to make it work. I spent about a week trying a number of various potential fixes.

Though, your solution sounds familiar to what I was messing about with at the end as well.

If it hadn't been for the fact that it worked before the update and I saw people posting on the forum that they got Hardware Acceleration with the 9800 under 8.04 I would have given up.

---

### Post by pietjanjaap on 2008-06-22
1 do this then compiz does not start with ubuntu, and you don't get the white screen.

Stop Compiz-Fusion From Loading Automatically

This guide will show you how to stop Compiz-Fusion from loading automatically on startup in Hardy Heron and how to setup a shortcut for launching Compiz when you want.

Step 1: Run gconf-edit
Start Run Application by pressing Alt+F2

Screenshot-Run Application

Enter gconf-editor into the box, hit enter


Step 2: Set Metacity as your default start up window manager
Once in gconf-editor navigate to desktop>gnome>applications>window_manager

Screenshot-Configuration Editor - window_manager

under current and default replace each instance of:
/usr/bin/compiz with /usr/bin/metacity
it should like this when you're done:

Screenshot-Configuration Editor - window_manager-1



Step 3: Create a shortcut for starting Compiz-Fusion
right click the Applications Places System Menu
select the Edit Menu option

Screenshot-Main Menu

pick a location for your shortcut and select New Item box

Screenshot-Launcher Properties
Type: Application
Name: Compiz
Command: compiz --replace
COmment compiz window manager


2 try this:
dpkg-reconfigure xserver-xorg is not the same anymore, now you can install your keybord and more with this.
But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the x,
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.
Then reboot and install your videcard driver.(i use envy for this).

3

/etc/modprobe.d/blacklist

hier in kopieren

blacklist i82875p_edac
blacklist edac_mc

4

Setup Compiz Fusion with open source ati radeon drivers

Older ATI cards have been blacklisted for Compiz Fusion because of a bug in the driver, but there is an easy workaround for many cards that use the open source ati drivers. Radeon 9500 are the oldest cards to support the restricted "fglrx" drivers, so everything older requires the open source drivers to function properly.



First edit the launcher for Compiz Fusion:

gksudo gedit /usr/bin/compiz

Near the top, add the line

SKIP_CHECKS="yes"

I added it under VERBOSE="yes"

You may also need to install the Compiz settings manager program that you can access from System->Preferences->Advanced Desktop Effect Settings | 1-click install or:

sudo apt-get install compizconfig-settings-manager

You can now load Compiz Fusion with

compiz --replace

and revert to Metacity (the basic window manager) with

metacity --replace

I suggest making launchers in a panel for this.

Remember that this is a workaround and may not work for everybody. If you have further problems, you should consider running a forum search and then posting on one of the main support forums if you still need help.
For the record, my card is an ATI Mobility Radeon 9000.

---

