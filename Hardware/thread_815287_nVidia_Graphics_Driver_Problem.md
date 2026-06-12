---
title: "nVidia Graphics Driver Problem"
date: 2008-06-01
forum: Hardware
---

### Post by Gannon8 on 2008-06-01
I have a nVidia GeForce 440 Go on my Dell Inspiron 8200 laptop. After I install the driver from the restricted hardware menu, I reboot my computer. After the loading bar, when the login menu is suppose to appear, my monitor turns off, and I have to press the power button on my computer, which displays the unloading bar and shuts down. I have to go into recovery mode and uninstall the driver with apt-get to get my desktop back.

I have downloaded the .run package from the nVidia website. How do I stop x-server while in run layer 2?

EDIT: The .run package does the same thing and it has my graphics card on it #-o
I had to go to recovery mode and fix the x server conf file

Edit once again: This is what nVidia says is a legacy device BTW

---

### Post by JimiHendrix[BR] on 2008-06-03
I have the same problem! Can somebody help us?

---

### Post by nick_h on 2008-06-04
Change to a virtual terminal with Ctrl-Alt-F1.

Stop the X server by stopping gdm with:
```
sudo /etc/init.d/gdm stop
```

Then install the driver.

Start the X server again with:
```
sudo /etc/init.d/gdm start
```

---

### Post by Gannon8 on 2008-06-04
New problem:

After installing the driver and rebooting, my screen turns off after the loading bar. :(

---

### Post by nick_h on 2008-06-04
You could try reconfiguring the X server to get it back:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Make a backup of your /etc/X11/xorg.conf first:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

### Post by Unix_Slayer on 2008-06-05
See this thread. ===>[http://ubuntuforums.org/showthread.php?t=819043]("http://ubuntuforums.org/showthread.php?t=819043")

---

### Post by Gannon8 on 2008-06-05
> **nick_h said:**
> You could try reconfiguring the X server to get it back:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Make a backup of your /etc/X11/xorg.conf first:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
I went into recovery mode and fixed x-server.
> **Unix_Slayer said:**
> See this thread. ===>[http://ubuntuforums.org/showthread.php?t=819043]("http://ubuntuforums.org/showthread.php?t=819043")
Same thing happens. BTW I'm using the legacy driver.

The Envy driver works sort of. There is color bars on the right of the screen and the top part gets repeated on the bottom.
That also happened when I tried installing Windows with a disk that didn't come with my computer.

---

### Post by Gannon8 on 2008-06-06
So theres no hope for me?

(AKA bump)

---

### Post by nick_h on 2008-06-06
What driver versions have you tried so far?

I think you need nvidia-glx rather than nvidia-glx-legacy or nvidia-glx-new.

Have a look at [this](http://www.nvidia.com/object/IO_32667.html) page on the nvidia site.

---

### Post by Archmage on 2008-06-06
Did you try envy? This does a nice job on many PCs.

---

### Post by Unix_Slayer on 2008-06-06
Don't use Envyng. It's just a quick fix. Use this thread. ==> [http://http://ubuntuforums.org/showthread.php?t=819043]("http://http://ubuntuforums.org/showthread.php?t=819043")

Works perfectly everytime for me. Legacy, and non-legacy drivers. No matter.

---

### Post by Gannon8 on 2008-06-06
> **nick_h said:**
> What driver versions have you tried so far?

I think you need nvidia-glx rather than nvidia-glx-legacy or nvidia-glx-new.

Have a look at [this](http://www.nvidia.com/object/IO_32667.html) page on the nvidia site.
Yes, the nvidia Geforce 4 440 Go Is on that list.
----------------------------------------------------
> **Archmage said:**
> Did you try envy? This does a nice job on many PCs.
> **Gannon8 said:**
> The Envy driver works sort of. There is color bars on the right of the screen and the top part gets repeated on the bottom.
That also happened when I tried installing Windows with a disk that didn't come with my computer.
----------------------------------------------------
> Don't use Envyng. It's just a quick fix. Use this thread. ==> [http://http://ubuntuforums.org/showthread.php?t=819043](http://http://ubuntuforums.org/showthread.php?t=819043)

Works perfectly everytime for me. Legacy, and non-legacy drivers. No matter.
Except now, and pressing ctrl alt Backspace just lets init start GDM again

---

### Post by Unix_Slayer on 2008-06-06
> **Gannon8 said:**
> Yes, the nvidia Geforce 4 440 Go Is on that list.
----------------------------------------------------


----------------------------------------------------

Except now, and pressing ctrl alt Backspace just lets init start GDM again


While in X11.... if you control+alt+backspace, it takes you out of X11 and into the main terminal login before X11. There must be something wrong with your shortcuts.

---

### Post by nick_h on 2008-06-06
> Except now, and pressing ctrl alt Backspace just lets init start GDM again
Yes, if gdm is running it will try to restart X.  Use the command I posted earlier to stop gdm.

> Yes, the nvidia Geforce 4 440 Go Is on that list.
What versions of the driver have you tried?

I don't think it really matters if you install the driver manually or use Envy.  All I can suggest is that you try different versions.

---

### Post by Unix_Slayer on 2008-06-06
> **nick_h said:**
> I don't think it really matters if you install the driver manually or use Envy.  All I can suggest is that you try different versions.


Doens't Envyng allow you to install the 169 driver and below?

---

### Post by nick_h on 2008-06-06
> Doens't Envyng allow you to install the 169 driver and below?
I haven't tried it myself but I understand that it is a GUI front-end to install a selection of driver versions.

The OP could also download them manually from the nvidia [Linux Display Driver Archive](http://www.nvidia.com/object/linux_display_archive.html).

I would suggest 1.0-9639 as a starting point.

---

### Post by Unix_Slayer on 2008-06-06
> **nick_h said:**
> I haven't tried it myself but I understand that it is a GUI front-end to install a selection of driver versions.

The OP could also download them manually from the nvidia [Linux Display Driver Archive](http://www.nvidia.com/object/linux_display_archive.html).

I would suggest 1.0-9639 as a starting point.


I've installed the latest driver from scratch using my method. Works everytime. I've even done it for a bunch of people. Not a bad apple in the bunch running the latest.

---

### Post by jocko on 2008-06-07
> **Unix_Slayer said:**
> While in X11.... if you control+alt+backspace, it takes you out of X11 and into the main terminal login before X11. There must be something wrong with your shortcuts.

There must be something wrong with *your* shortcuts.
Ctrl+Alt+Backspace causes a RESTART of xorg. It always has and always will cause xorg to immediately restart, unless you have found some magic setting somewhere that makes it behave differently.
To stop xorg without restarting it, you need to run this:
```
sudo killall gdm
```Or:```
sudo /etc/init.d/gdm stop
```

---

### Post by AnonCat on 2008-06-07
EnvyNG installed the Nvidia drivers flawlessly on my machine, so don't be afraid to try it.

---

### Post by dnairb on 2008-06-07
> **jocko said:**
> There must be something wrong with *your* shortcuts.
Ctrl+Alt+Backspace causes a RESTART of xorg. It always has and always will cause xorg to immediately restart, unless you have found some magic setting somewhere that makes it behave differently.
To stop xorg without restarting it, you need to run this:
```
sudo killall gdm
```Or:```
sudo /etc/init.d/gdm stop
```

You are both right, depending on whether you are using KDE (as I believe Unix_Slayer is) or Gnome.

---

### Post by Unix_Slayer on 2008-06-07
> **AnonCat said:**
> EnvyNG installed the Nvidia drivers flawlessly on my machine, so don't be afraid to try it.


 	[B]Linux Display Driver - x86

Version: 173.14.05
Operating System: Linux x86
Release Date: May 28, 2008 [/B]  [B][SIZE="6"]?????
[/SIZE][/B] I don't think so, since the gentleman who created it doesn't work on it any more.

---

### Post by Unix_Slayer on 2008-06-07
> **jocko said:**
> There must be something wrong with *your* shortcuts.
Ctrl+Alt+Backspace causes a RESTART of xorg. It always has and always will cause xorg to immediately restart, unless you have found some magic setting somewhere that makes it behave differently.
To stop xorg without restarting it, you need to run this:
```
sudo killall gdm
```Or:```
sudo /etc/init.d/gdm stop
```


Sorry I am using KDE4. You need to stop Gnome, and install the driver in term. The above code is correct to stop Gnome. Instead of control+alt+backspace. Use the above.

---

### Post by Unix_Slayer on 2008-06-07
So lets hear the good word! Has this worked for anyone? I know it works, because I've installed this way about 20 times already. Also.... When there is a kernel update, the driver has to be re-installed same way. Kernel change means no X11 start, until you re-install the driver. Or in grub loader you can start with the other kernel. Either way it works.

---

### Post by nick_h on 2008-06-07
> Has this worked for anyone? I know it works, because I've installed this way about 20 times already.

Yes, I have manually installed nvidia drivers successfully using only a minor modification to your instructions for Gnome.  I have never used Envy myself but have heard good reports about it.

As far as the OP is concerned I think the problem is the driver version not how it is installed.  I suggest the following:

1. Try the driver version 1.0-9639
2. Look in /var/log/Xorg.0.log for any errors
3. Check the dmesg output for any errors

Try:
```
dmesg | grep -i nv
```
This will also confirm your driver version.

---

### Post by PmDematagoda on 2008-06-07
> **Unix_Slayer said:**
> [B]Linux Display Driver - x86

Version: 173.14.05
Operating System: Linux x86
Release Date: May 28, 2008 [/B]  [B][SIZE="6"]?????
[/SIZE][/B] I don't think so, since the gentleman who created it doesn't work on it any more.

Your information is a bit off. The gentleman who created the program is none other than tseliot of these very forums, who still lives and breathes FYI. And he is also still very active on his program, so Nvidia driver version 173 will come soon.

---

### Post by Unix_Slayer on 2008-06-07
> **PmDematagoda said:**
> Your information is a bit off. The gentleman who created the program is none other than tseliot of these very forums, who still lives and breathes FYI. And he is also still very active on his program, so Nvidia driver version 173 will come soon.

I went to his webpage, and he said something about being too busy to update the program. I've found an easier way to install the newest NVidia driver. And it works without installing an added program. I was only sharing that information.

---

### Post by xmastree on 2008-06-07
I think there ws a recent update, after which my nvidia driver no longer works.
I just get a blank screen after the status bar.

Changing my xorg.conf like this:
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection


# Section "Device"
# 	Identifier	"Configured Video Device"
# 	Driver		"nvidia"
# 	Option		"NoLogo"	"True"
# EndSection

```gets me running, but without the fancy stuff.

Any ideas?

---

### Post by Unix_Slayer on 2008-06-07
> **xmastree said:**
> I think there ws a recent update, after which my nvidia driver no longer works.
I just get a blank screen after the status bar.

Changing my xorg.conf like this:
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection


# Section "Device"
# 	Identifier	"Configured Video Device"
# 	Driver		"nvidia"
# 	Option		"NoLogo"	"True"
# EndSection

```gets me running, but without the fancy stuff.

Any ideas?

There was a kernel update. You have to re-install the NVidia driver each time the kernel updates. Works like a charm.

---

### Post by xmastree on 2008-06-07
> **Unix_Slayer said:**
> There was a kernel update. You have to re-install the NVidia driver each time the kernel updates. Works like a charm.
So it does, thanks. I guess I've been spoiled by earlier versions which didn't require anything more than a reboot after a new kernel.

---

### Post by Lacrimstein on 2008-06-07
Yes, custom-installed drivers (not the ones from linux-restricted-modules) require a reinstall after a kernel update.

I installed the 173.14 driver on my laptop with the 8600MGT just now, works like a charm. Compiz works very smoothly with the PerfLevel hack. The only thing is that the nvidia-settings displays my GPU RAM as 512, when it is only 256. Hopefully that won't cause problems, but if it does i'll just revert to beta.

---

### Post by PmDematagoda on 2008-06-07
> **Unix_Slayer said:**
> I went to his webpage, and he said something about being too busy to update the program. I've found an easier way to install the newest NVidia driver. And it works without installing an added program. I was only sharing that information.

That maybe because he is working on an xorg.conf editor for Intrepid, but this doesn't mean that he wouldn't update the program.

---

### Post by Unix_Slayer on 2008-06-07
> **Lacrimstein said:**
> Yes, custom-installed drivers (not the ones from linux-restricted-modules) require a reinstall after a kernel update.

I installed the 173.14 driver on my laptop with the 8600MGT just now, works like a charm. Compiz works very smoothly with the PerfLevel hack. The only thing is that the nvidia-settings displays my GPU RAM as 512, when it is only 256. Hopefully that won't cause problems, but if it does i'll just revert to beta.


There are switches that people neglect to run. Like nvidia-xconfig --multigpu=on or nvidia-xconfig --sli=on, and so forth. You can run your video card any way you want.

**This is my setup running in multiGPU SLI. All done without Envyng using my guide lines ==>**[IMG]http://mysite.verizon.net/mgm_mgm/nv1.jpg[/IMG][IMG]http://mysite.verizon.net/mgm_mgm/nv3.jpg[/IMG]

---

### Post by Unix_Slayer on 2008-06-07
> **PmDematagoda said:**
> That maybe because he is working on an xorg.conf editor for Intrepid, but this doesn't mean that he wouldn't update the program.

I'm not putting the guy down. He has other projects he's working on. And that's cool. I am just showing other users it can be done another easier way. I've worked with Unix/Linux/xenix/FreeBSD/Suse, and Sun for 28 years. I'm now just starting to play with X11. Because the servers I administrated through out the years were always running in term only. I can do many fixes in Linux through binaries, and scripts. Including networks, hardware devices, and so forth.... But them again I am the Blizzard Of Ozz. [IMG]http://www.tech-faq.com/emoticons/free-animated-emoticons/smiley_67.gif[/IMG]

---

### Post by Gannon8 on 2008-06-07
Lol, 3 pages of post in 1 day? thats spectacular for me, although it gives me too much info to handle.

Stopping GDM does NOT give me a terminal. I've tried it.

I have tried all but the "new" drivers in the respiratory, as well as the legacy .run package, and it doesn't tell me how to delete all the files. I installed the .run package in run level 1, so if that has anything to do with it.

The driver with the most success is the envy driver. SO STOP TELLING ME TO TRY IT I'VE ALREADY DONE SO!!!

---

### Post by nick_h on 2008-06-07
```
Stopping GDM does NOT give me a terminal. I've tried it.
```
No, but it will stop your X session.

Type Ctrl+Alt+F1 to get to another virtual terminal (VT 1).  Now login and stop gdm.  If you try to switch back to the GUI (Ctrl+Alt+F7) you should see that it has stopped.

Now you can can install the driver in VT 1.   Unix_Slayer's instructions work for the installation.  Note:  You will need the build-essential package installed.

When you have finished the installation start gdm again.  Switch back to VT 7 again for the GUI (I think it might change back for you).

I suggest you have a look in the log files for any errors.  Try to make note of the driver versions you have tried.  (and try version 1.0-9639)

---

### Post by Unix_Slayer on 2008-06-07
If you have ANY other NVidia drivers installed, it will not work. Stop getting frustrated, and think about it my friend. Notice the driver version I am using.

[IMG]http://mysite.verizon.net/mgm_mgm/realnv.jpg[/IMG]

---

### Post by Gannon8 on 2008-06-07
How do I get rid of the driver then? It doesn't look like it has an uninstall.

---

### Post by nick_h on 2008-06-07
Uninstalling a driver depends on how you installed it.

Ubuntu packages can be uninstalled from the Synaptic package manager or from the command line:
```
sudo apt-get remove nvidia-glx-new
```

For the drivers downloaded from the nvidia site the same executable that you run to install them can be run with an uninstall option.  I can't remember exactly how.  Try running it with the option --help and it will list the options. (I think it may be --uninstall).

I haven't used Envy so I can't comment about uninstalling Envy drivers.

One other point that is worth mentioning - when using drivers downloaded from the nvidia site you need to disable the ubuntu restricted drivers by adding an entry in the /etc/default/linux-restricted-modules-common file.

---

### Post by Gannon8 on 2008-06-07
Ok, I uninstalled the -96xx driver. I'm going to install the 1.0-71xx driver now.

---

### Post by Unix_Slayer on 2008-06-07
> **nick_h said:**
> Uninstalling a driver depends on how you installed it.

Ubuntu packages can be uninstalled from the Synaptic package manager or from the command line:
```
sudo apt-get remove nvidia-glx-new
```

For the drivers downloaded from the nvidia site the same executable that you run to install them can be run with an uninstall option.  I can't remember exactly how.  Try running it with the option --help and it will list the options. (I think it may be --uninstall).

I haven't used Envy so I can't comment about uninstalling Envy drivers.

One other point that is worth mentioning - when using drivers downloaded from the nvidia site you need to disable the ubuntu restricted drivers by adding an entry in the /etc/default/linux-restricted-modules-common file.

Don't worry about the ENVYNG driver/program. Just follow my directions. Are you running Gnome? I don't know the shortcut key for stopping Gnome. Only KDE. sudo apt-get remove nvidia* will get rid of any, and all useless NVidia drivers. It also take care of the restricted modules as well. One command comes in for the swoop, and does the job.

---

### Post by Unix_Slayer on 2008-06-07
> **nick_h said:**
> One other point that is worth mentioning - when using drivers downloaded from the nvidia site you need to disable the ubuntu restricted drivers by adding an entry in the /etc/default/linux-restricted-modules-common file.

Actually I think it's /lib/linux-restricted-modules/2.6.24-18-generic

---

### Post by Gannon8 on 2008-06-07
The restricted drivers menu doesn't show anything anyway after installing the first package, not even my integrated wireless adapter.

The 76 driver installed, but the xorg.conf is not configured. Can someone tell me what to type?

---

### Post by Gannon8 on 2008-06-08
Bump

---

### Post by PmDematagoda on 2008-06-08
Try:-
```
sudo nvidia-xconfig
```
that should configure the xorg.conf in some proper way.

---

### Post by nick_h on 2008-06-08
> I don't know the shortcut key for stopping Gnome. Only KDE.
In Gnome, Ctrl+Alt+Backspace will stop X but it will restart if you don't stop gdm first.  Stopping gdm is simple though:
```
sudo /etc/init.d/gdm stop
```

> sudo apt-get remove nvidia* will get rid of any, and all useless NVidia drivers.
Well apt-get will certainly remove packages, but if you have installed drivers without using the package management system then it won't find a package to remove.

If the drivers were installed using the nvidia installer, then the same installer can be run with the --uninstall option.

---

### Post by nick_h on 2008-06-08
> Actually I think it's /lib/linux-restricted-modules/2.6.24-18-generic
No the file is /etc/default/linux-restricted-modules-common and the line should read:
```
DISABLED_MODULES="nv"
```
to disable the restricted nvidia drivers.

Note: You obviously don't need to do this if you have previously removed the drivers with *sudo apt-get remove nvidia**

---

### Post by Unix_Slayer on 2008-06-08
> **nick_h said:**
> No the file is /etc/default/linux-restricted-modules-common and the line should read:
```
DISABLED_MODULES="nv"
```
to disable the restricted nvidia drivers.

Note: You obviously don't need to do this if you have previously removed the drivers with *sudo apt-get remove nvidia**

Mine are in the /lib directory.

---

### Post by Unix_Slayer on 2008-06-08
> **nick_h said:**
> In Gnome, Ctrl+Alt+Backspace will stop X but it will restart if you don't stop gdm first.  Stopping gdm is simple though:
```
sudo /etc/init.d/gdm stop
```


Well apt-get will certainly remove packages, but if you have installed drivers without using the package management system then it won't find a package to remove.

If the drivers were installed using the nvidia installer, then the same installer can be run with the --uninstall option.


You are correct. This is the easiest way to remove all unwanted NVidia drivers, and make a fresh install of the newest, and latest drivers.

---

### Post by Unix_Slayer on 2008-06-08
> **nick_h said:**
> In Gnome, Ctrl+Alt+Backspace will stop X but it will restart if you don't stop gdm first.  Stopping gdm is simple though:
```
sudo /etc/init.d/gdm stop
```


Well apt-get will certainly remove packages, but if you have installed drivers without using the package management system then it won't find a package to remove.

If the drivers were installed using the nvidia installer, then the same installer can be run with the --uninstall option.

Double post for me that is.

---

### Post by Gannon8 on 2008-06-09
Back to the current situation:
> **PmDematagoda said:**
> Try:-
```
sudo nvidia-xconfig
```
that should configure the xorg.conf in some proper way.
It says the command is not found.

---

### Post by Gannon8 on 2008-06-09
I also checked the documentation included with the .run file, and there is nothing that configures X-Server.

---

### Post by Unix_Slayer on 2008-06-09
> **Gannon8 said:**
> Back to the current situation:

It says the command is not found.

Do you have nvidia-xserver installed? Open adept manager, and search for nvidia. Only install nvidia xserver, and nothing else.

---

### Post by Gannon8 on 2008-06-09
I hate it when I'm in windows and I have to reboot to do something with Ubuntu. I'll go try it now.

---

### Post by Gannon8 on 2008-06-09
I installed it and did the same thing. Still said the command was not found.

---

### Post by Unix_Slayer on 2008-06-09
> **Gannon8 said:**
> I installed it and did the same thing. Still said the command was not found.

It doesn't seem to be installed. You might have to go over it, and find out why.

---

### Post by Dizzle7677 on 2008-06-09
> **Gannon8 said:**
> I installed it and did the same thing. Still said the command was not found.

[http://download.nvidia.com/XFree86/nvidia-xconfig/nvidia-xconfig-1.0.tar.gz]("http://download.nvidia.com/XFree86/nvidia-xconfig/nvidia-xconfig-1.0.tar.gz")

Make
Install

---

### Post by Unix_Slayer on 2008-06-10
> **Dizzle7677 said:**
> [http://download.nvidia.com/XFree86/nvidia-xconfig/nvidia-xconfig-1.0.tar.gz]("http://download.nvidia.com/XFree86/nvidia-xconfig/nvidia-xconfig-1.0.tar.gz")

Make
Install

Thank you Dizzle. Doesn't it show up in Adept?

---

### Post by Gannon8 on 2008-06-10
```
gannon8@g8-laptop:~/Downloads/nvidia-xconfig-1.0$ make
cc -c -g -O -Wall -O -I XF86Config-parser util.c -o util.o
cc -c -g -O -Wall -O -I XF86Config-parser nvidia-xconfig.c -o nvidia-xconfig.o
cc -c -g -O -Wall -O -I XF86Config-parser make_usable.c -o make_usable.o
cc -c -g -O -Wall -O -I XF86Config-parser multiple_screens.c -o multiple_screens.o
cc -c -g -O -Wall -O -I XF86Config-parser tree.c -o tree.o
cc -c -g -O -Wall -O -I XF86Config-parser nvgetopt.c -o nvgetopt.o
cc -c -g -O -Wall -O -I XF86Config-parser options.c -o options.o
cc -c -g -O -Wall -O -I XF86Config-parser lscf.c -o lscf.o
cc -c -g -O -Wall -O -I XF86Config-parser query_gpu_info.c -o query_gpu_info.o
cc -c -g -O -Wall -O -I XF86Config-parser extract_edids.c -o extract_edids.o
cc -c -g -O -Wall -O -I XF86Config-parser g_stamp.c -o g_stamp.o
make NV_CFLAGS='' -C XF86Config-parser
make[1]: Entering directory `/home/gannon8/Downloads/nvidia-xconfig-1.0/XF86Config-parser'
make[1]: Leaving directory `/home/gannon8/Downloads/nvidia-xconfig-1.0/XF86Config-parser'
make[1]: Entering directory `/home/gannon8/Downloads/nvidia-xconfig-1.0/XF86Config-parser'
cc -c -Wall -g DRI.c -o DRI.o
cc -c -Wall -g Device.c -o Device.o
cc -c -Wall -g Files.c -o Files.o
cc -c -Wall -g Flags.c -o Flags.o
cc -c -Wall -g Input.c -o Input.o
cc -c -Wall -g Keyboard.c -o Keyboard.o
cc -c -Wall -g Layout.c -o Layout.o
cc -c -Wall -g Module.c -o Module.o
cc -c -Wall -g Monitor.c -o Monitor.o
cc -c -Wall -g Pointer.c -o Pointer.o
cc -c -Wall -g Screen.c -o Screen.o
cc -c -Wall -g Vendor.c -o Vendor.o
cc -c -Wall -g Video.c -o Video.o
cc -c -Wall -g Read.c -o Read.o
cc -c -Wall -g Scan.c -o Scan.o
cc -c -Wall -g Write.c -o Write.o
cc -c -Wall -g Util.c -o Util.o
cc -c -Wall -g Extensions.c -o Extensions.o
cc -c -Wall -g Generate.c -o Generate.o
cc -c -Wall -g Merge.c -o Merge.o
ld -r -o libXF86Config-parser.o DRI.o Device.o Files.o Flags.o Input.o Keyboard.o Layout.o Module.o Monitor.o Pointer.o Screen.o Vendor.o Video.o Read.o Scan.o Write.o Util.o Extensions.o Generate.o Merge.o
ar ruv libXF86Config-parser.a libXF86Config-parser.o
ar: creating libXF86Config-parser.a
a - libXF86Config-parser.o
ranlib libXF86Config-parser.a
make[1]: Leaving directory `/home/gannon8/Downloads/nvidia-xconfig-1.0/XF86Config-parser'
cc -g -O -Wall -O -I XF86Config-parser util.o nvidia-xconfig.o make_usable.o multiple_screens.o tree.o nvgetopt.o options.o lscf.o query_gpu_info.o extract_edids.o g_stamp.o -lm  -ldl -o nvidia-xconfig XF86Config-parser/libXF86Config-parser.a
cc -g -O -Wall -O -I XF86Config-parser -c gen-manpage-opts.c
cc -g -O -Wall -O -I XF86Config-parser gen-manpage-opts.o -lm  -ldl -o gen-manpage-opts
./gen-manpage-opts > options.1.inc
m4 -D__HEADER__=".\\\" WARNING: THIS FILE IS AUTO-GENERATED!  Edit nvidia-xconfig.1.m4 instead." nvidia-xconfig.1.m4 > nvidia-xconfig.1
/bin/sh: m4: not found
make: *** [nvidia-xconfig.1] Error 127

```
At the bottom, says a command or file isn't found.
What should I do?

---

### Post by Gannon8 on 2008-06-11
bump

---

### Post by Unix_Slayer on 2008-06-11
> **Gannon8 said:**
> ```
gannon8@g8-laptop:~/Downloads/nvidia-xconfig-1.0$ make
cc -c -g -O -Wall -O -I XF86Config-parser util.c -o util.o
cc -c -g -O -Wall -O -I XF86Config-parser nvidia-xconfig.c -o nvidia-xconfig.o
cc -c -g -O -Wall -O -I XF86Config-parser make_usable.c -o make_usable.o
cc -c -g -O -Wall -O -I XF86Config-parser multiple_screens.c -o multiple_screens.o
cc -c -g -O -Wall -O -I XF86Config-parser tree.c -o tree.o
cc -c -g -O -Wall -O -I XF86Config-parser nvgetopt.c -o nvgetopt.o
cc -c -g -O -Wall -O -I XF86Config-parser options.c -o options.o
cc -c -g -O -Wall -O -I XF86Config-parser lscf.c -o lscf.o
cc -c -g -O -Wall -O -I XF86Config-parser query_gpu_info.c -o query_gpu_info.o
cc -c -g -O -Wall -O -I XF86Config-parser extract_edids.c -o extract_edids.o
cc -c -g -O -Wall -O -I XF86Config-parser g_stamp.c -o g_stamp.o
make NV_CFLAGS='' -C XF86Config-parser
make[1]: Entering directory `/home/gannon8/Downloads/nvidia-xconfig-1.0/XF86Config-parser'
make[1]: Leaving directory `/home/gannon8/Downloads/nvidia-xconfig-1.0/XF86Config-parser'
make[1]: Entering directory `/home/gannon8/Downloads/nvidia-xconfig-1.0/XF86Config-parser'
cc -c -Wall -g DRI.c -o DRI.o
cc -c -Wall -g Device.c -o Device.o
cc -c -Wall -g Files.c -o Files.o
cc -c -Wall -g Flags.c -o Flags.o
cc -c -Wall -g Input.c -o Input.o
cc -c -Wall -g Keyboard.c -o Keyboard.o
cc -c -Wall -g Layout.c -o Layout.o
cc -c -Wall -g Module.c -o Module.o
cc -c -Wall -g Monitor.c -o Monitor.o
cc -c -Wall -g Pointer.c -o Pointer.o
cc -c -Wall -g Screen.c -o Screen.o
cc -c -Wall -g Vendor.c -o Vendor.o
cc -c -Wall -g Video.c -o Video.o
cc -c -Wall -g Read.c -o Read.o
cc -c -Wall -g Scan.c -o Scan.o
cc -c -Wall -g Write.c -o Write.o
cc -c -Wall -g Util.c -o Util.o
cc -c -Wall -g Extensions.c -o Extensions.o
cc -c -Wall -g Generate.c -o Generate.o
cc -c -Wall -g Merge.c -o Merge.o
ld -r -o libXF86Config-parser.o DRI.o Device.o Files.o Flags.o Input.o Keyboard.o Layout.o Module.o Monitor.o Pointer.o Screen.o Vendor.o Video.o Read.o Scan.o Write.o Util.o Extensions.o Generate.o Merge.o
ar ruv libXF86Config-parser.a libXF86Config-parser.o
ar: creating libXF86Config-parser.a
a - libXF86Config-parser.o
ranlib libXF86Config-parser.a
make[1]: Leaving directory `/home/gannon8/Downloads/nvidia-xconfig-1.0/XF86Config-parser'
cc -g -O -Wall -O -I XF86Config-parser util.o nvidia-xconfig.o make_usable.o multiple_screens.o tree.o nvgetopt.o options.o lscf.o query_gpu_info.o extract_edids.o g_stamp.o -lm  -ldl -o nvidia-xconfig XF86Config-parser/libXF86Config-parser.a
cc -g -O -Wall -O -I XF86Config-parser -c gen-manpage-opts.c
cc -g -O -Wall -O -I XF86Config-parser gen-manpage-opts.o -lm  -ldl -o gen-manpage-opts
./gen-manpage-opts > options.1.inc
m4 -D__HEADER__=".\\\" WARNING: THIS FILE IS AUTO-GENERATED!  Edit nvidia-xconfig.1.m4 instead." nvidia-xconfig.1.m4 > nvidia-xconfig.1
/bin/sh: m4: not found
make: *** [nvidia-xconfig.1] Error 127

```
At the bottom, says a command or file isn't found.
What should I do?

Can you paste up the config.log? Your missing M4 I think. Sorry for the delay. I was away on business. Did you do this before your install:

```
sudo apt-get install build-essential
```

---

### Post by Gannon8 on 2008-06-11
Where would I find that file? It's not in the directory that the source is in. I don't know much about make, only that it is a compiler.

And I do have the build-essential package

---

### Post by Unix_Slayer on 2008-06-12
> **Gannon8 said:**
> Where would I find that file? It's not in the directory that the source is in. I don't know much about make, only that it is a compiler.

And I do have the build-essential package


Go to this page. ==> [http://packages.debian.org/stable/libs/]("http://packages.debian.org/stable/libs/")

Search out M4.

---

### Post by Gannon8 on 2008-06-12
No, I did edit > find and didn't see an M4 library that wasn't apart of an abbreviation. And I meant the config.log.

Would apt-get source nvidia-xconfig --compile give me the same error?

---

### Post by Gannon8 on 2008-06-13
Bump

---

### Post by Unix_Slayer on 2008-06-13
> **Gannon8 said:**
> No, I did edit > find and didn't see an M4 library that wasn't apart of an abbreviation. And I meant the config.log.

Would apt-get source nvidia-xconfig --compile give me the same error?

See, I didn't use that method. I would hate to give you the wrong instructions. I would save a copy of my xorg.conf before I attempted it. Also, if it doesn't work, you would need to sudo apt-get remove nvidia* again. And you would have to re-install the driver once again.

---

### Post by Gannon8 on 2008-06-14
I didn't run apt-get source. I was just wondering.

---

### Post by Unix_Slayer on 2008-06-14
> **Gannon8 said:**
> I didn't run apt-get source. I was just wondering.

If someone is willing to give it a roll, but I'm super content with the way my NVidia SLI are working. I don't want to fix something that's already fixed.

---

### Post by Gannon8 on 2008-06-17
I reinstalled the 96 Nvidia driver, and using some docs from the nvidia site, hand configured xorg.conf. It doesn't give me a blank screen when I load ubuntu, but it will not let me enable desktop effects.

JimiHendrix[BR], I will post my xorg.conf file shortly.

---

### Post by Gannon8 on 2008-06-17
Heres the xorg.conf file, in a .tar.gz file. Experts, if you can point out changes I should make, then please do so =)

---

### Post by oldweasel on 2008-06-17
Sigh, having issues here also. I have tried Envy, the restricted drivers, and the methods indicated in earlier pages here, no luck. figured I needed to start "clean", so here's what I did:

1) run Envy driver uninstall, reboot
2) run sudo apt-get uninstall -nvidia*, reboot
3) shutdown the xserver and run sh NVIDIA* -- uninstall [uninstall the NVIDIA kernel-level drivers], reboot

Then following the earlier thread instructions, I ran sudo sh NVIDIA-Linux-x86-173.14.05-pkg1.run and let the NVIDIA driver install and configure itself.

Here';s the xorg.conf after the NVIDIA driver got done with it:

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Mon May 19 00:33:37 PDT 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Noticed the horiz and vert refresh rates were off, so changed them to match my Syncmaster 930b:

Horiz refresh: 30 - 81 kHz
Vert Refresh: 56 - 75 Hz

Rebooted and same issue, splash screen works correctly, then when xserver starts up screen goes black and goes into standby mode.

Rebooted in safe mode and ran the xserver config, now xorg.conf looks like the below:

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

I am at a loss as to what to do now, my Nvidia 7900 worked great without these issues, and my ATI X1950 pro worked well.

Only issues with the 8800 GT.

Frustrated and at a loss what to try next, any ideas?

EDIT: I get my desktop using the latter settings, but no 3-D acceleration, so compiz, etc are out. Would really like to get my wavy windows again ;).

---

### Post by Gannon8 on 2008-06-18
[Clicky to fix]("http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/chapter-06-section-02.html")

---

### Post by oldweasel on 2008-06-18
> **Gannon8 said:**
> [Clicky to fix]("http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/chapter-06-section-02.html")

Not trying to be rude here, but I have the settings advocated by the link in my Nvidia xorg.conf, but still get the blank screen after startup.

Or am I missing what you were trying to convey?

---

### Post by SDREnate on 2008-06-18
I've been having the same problem as oldweasel, and I've tried pretty much the same things. I also have an 8800 gt. I haven't taken a look at my xorg.conf yet though. This is frustrating because I would really like to get my 3d desktop effects working. I guess I'll try a fresh install then a system update when I get home from work.

---

### Post by Gannon8 on 2008-06-18
I figured out why I can't turn on effects now. It wasn't using the driver. I configured it to use it, but now xorg will not start. :(

---

### Post by Gannon8 on 2008-06-18
Okay, I hadn't installed it :confused:
Installing it gives me a blank screen, so now finally, I am going to try the latest driver.

---

### Post by Gannon8 on 2008-06-18
New driver will not build nvidia.ko...

Well, I guess I could e-mail nvidia.

---

### Post by jarocooke on 2008-06-18
Hi Gannon8,

I have an old laptop with a 440 Go Nvidia graphic card.

You need to add a specific option to xorg.conf and then the problem goes away without any issues what so ever (assuming you have the same problem that I had.

The laptop isn't on at the moment, but as you've been having troubles with this for a little while now I see I'll go get the info.

Just get your system back to the default Nvidia driver that it would normally use (Nvidia legacy one in repos I guess).

Back in a minute.

James Cooke
[www.massoss.com](www.massoss.com)
Powered by Penguins

---

### Post by jarocooke on 2008-06-18
Right here is the crutial info.

In your xorg.conf add the following line to the "Device" section.

```

Option		"UseDisplayDevice"	"DFP-0"

```

I'm pretty sure that is it, let me know if it works.

Cheers,

James
[www.massoss.com](www.massoss.com)
Powered by Penguins

---

### Post by Unix_Slayer on 2008-06-18
> **oldweasel said:**
> 
2) run sudo apt-get uninstall 
-nvidia*, reboot
.

This was your mistake. The command should have been:
```
sudo apt-get **remove** nvidia*
```

---

### Post by hotweiss on 2008-06-19
You are in luck, Envy has the new Nvidia drivers as of June 11th.

1. sudo apt-get remove nvidia*
2. sudo apt-get install envyng-gtk
2. enable the proposed repositories
3. sudo apt-get update
4. sudo envyng -g
5. Select Nvidia on the left side, now click on Install the Nvidia driver (Manual Selection of the Driver), select 173, and finally click Apply.
6. Once the installation is completed, reboot and you will once again have a crisp screen.

---

### Post by tenmoi on 2008-06-19
Hi there,

I recommend installing the .run driver provided by NVidia. You can go to nvidia linux forum or this forum to find the proper instructions.

If you still have problems, you should look at your /var/log/Xorg.0.log and if you find this line
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
Then try to remove or traces of nvidia* and install sysv-rc-conf and you can try blanking out all X's behind nvidia-kernel/ker$ and see if it helps.

---

### Post by Gannon8 on 2008-06-20
> **tenmoi said:**
> I recommend installing the .run driver provided by NVidia. You can go to nvidia linux forum or this forum to find the proper instructions.Not trying to be rude, but that is what I have been doing.:)

I have deleted the Ubuntu partition last night, because of broken dependencies that I cannot solve and repartitioning the disks for windows and up to 5 other Linux OS's, as well as a /home partition shared between OS's (that will work right?), a FAT32 partition for sharing with windows users via wireless, an ext3 partition for general storage and wireless sharing, and finally a small encrypted partition. (and some swap, most of this is in an extended partition)

I plan to install Ubuntu last, so it should configure GRUB with all my other OS's. Right now I have windows and PCLinuxOS.

---

### Post by oldweasel on 2008-06-20
> **Unix_Slayer said:**
> This was your mistake. The command should have been:
```
sudo apt-get **remove** nvidia*
```

My apologies, I mistyped the statement, I did use the remove statement. 

Anyone had the new Envy drivers work?

---

### Post by oldweasel on 2008-06-20
> **Gannon8 said:**
> Not trying to be rude, but that is what I have been doing.:)

I have deleted the Ubuntu partition last night, because of broken dependencies that I cannot solve and repartitioning the disks for windows and up to 5 other Linux OS's, as well as a /home partition shared between OS's (that will work right?), a FAT32 partition for sharing with windows users via wireless, an ext3 partition for general storage and wireless sharing, and finally a small encrypted partition. (and some swap, most of this is in an extended partition)

I plan to install Ubuntu last, so it should configure GRUB with all my other OS's. Right now I have windows and PCLinuxOS.

Does your Nvidia card work with PCLinuxOS? If so you might be able to see what parameters they have in their xorg.conf file.

---

### Post by Unix_Slayer on 2008-06-20
> **oldweasel said:**
> My apologies, I mistyped the statement, I did use the remove statement. 

Anyone had the new Envy drivers work?

No problem. Let me how the new Envy works. I haven't heard any feedback on it as yet.

---

### Post by Unix_Slayer on 2008-06-23
From what I hear, the new kernel supposedly fixes the video and network problems. At least the problems of not working that is after a new kernel update. Anyone have anything to add?

---

### Post by Gannon8 on 2008-06-23
I posted on the nvnews.net forum, which is where the nvidia unix portal took me. A user replied that had a similar problem on a similar graphics card (Geforce 4 420 Go), and said X-Org was trying to use the port on the back of my computer.
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	        "True"
	Option		"UseDisplayDevice"	"DFP-0"
	Option		"DynamicTwinView"	"false"
EndSection
```He said that disabling Dynamic TwinView would make compliz smoother.

This worked, and my monitor comes on, but with the same color bars and effects as the 71 driver. So I believe that it is a monitor problem and not a graphics card problem. I am going to plug my computer in the CRT monitor in my bedroom and see if it gets the same problem.

If it does not then I will post a new thread, and mark this one as solved. If it does, I will leave this one open. Thank you all for the help!:)

---

### Post by Gannon8 on 2008-06-24
> **oldweasel said:**
> Does your Nvidia card work with PCLinuxOS? If so you might be able to see what parameters they have in their xorg.conf file.It works using the nv driver I believe, I notice that there is no desktop effects. Also, I burned a Mandriva LiveCD, and the screen went blank like it did without that line. On my home computer, it gets desktop effects (ooo neat wobbly effect:popcorn:).

Plugging in the other monitor and enabling TwinView works without color bars, so I guess this is now a monitor problem. Thank you all so much for the help you have given me!:KS

---

### Post by ronaldp423 on 2008-07-02
Hi everyone,

I'm bran-spankin new to Linux and installed Ubuntu 8.04 a month ago; when I got tired of XP. I absolutely love it!!

My only serious problem has been this whole Nvidia driver issue.

I would be deeply grateful if someone could tell me exactly step-by-step how they would go about installing the proper Nvidia driver.

I have been studying Ubuntu and everything I could find about Nvidia drivers for a month now. I am familiar with Envy and Envyng and the archives at Nvidia. I know my card needs driver 7184. I believe; according to the Envy site; that I will actually need to install the driver manually from the archives.

Could someone please walk me through this blow-by-blow.

My laptop is a Dell Inspiron 2650 with a13 bios; 16mb Geforce2 Go card.

Thanks in advance!

---

### Post by xmastree on 2008-07-06
<sigh> It was working fine, but overnight it's broken again.
I've tried reinstalling the nvidia drivers but to no avail.

I'll stick with using nv in my config file for now. Who needs fancy effects anyway?

---

### Post by Gannon8 on 2008-07-10
I believe the problem is how the driver configures the display. I am going to try xrandr and see if I can at least get my 1600x1200 back.
Edit: topic now unsolvified.

---

### Post by Kileli on 2008-07-12
Can anyone help me out. i cannot seam to get my grafics card to work right i have installed the latest nvidia driver but i cannot gain a resolution more than 600x800 i have a geforce 8400 gs i have been denied permission to make changes to the confx.org file so even when i am able to obtain hier reslutions i cant save the configuration WTH Please help

---

### Post by Gannon8 on 2008-07-12
> **Kileli said:**
> Can anyone help me out. i cannot seam to get my grafics card to work right i have installed the latest nvidia driver but i cannot gain a resolution more than 600x800 i have a geforce 8400 gs i have been denied permission to make changes to the confx.org file so even when i am able to obtain hier reslutions i cant save the configuration WTH Please helpPlease either search the threads or post your own thread.

Maybe the one on my computer I am building in my summer technology class will work. I get to build, set up, and keep a free computer :D

But it does not come with a:
Monitor, but I got an extra CRT monitor in my room.
Keyboard and mouse, but my dad has some.
OS, but that's what linux is for :)

---

### Post by Kileli on 2008-07-12
> **Gannon8 said:**
> Please either search the threads or post your own thread.

Maybe the one on my computer I am building in my summer technology class will work. I get to build, set up, and keep a free computer :D

But it does not come with a:
Monitor, but I got an extra CRT monitor in my room.
Keyboard and mouse, but my dad has some.
OS, but that's what linux is for :)

yeah thanks bud i have been searching the threads for three days now nothing suggested works

---

### Post by Gannon8 on 2008-07-13
Then post a new one.

Gannon8 casts Topic Change!
The thread became on-topic!

---

