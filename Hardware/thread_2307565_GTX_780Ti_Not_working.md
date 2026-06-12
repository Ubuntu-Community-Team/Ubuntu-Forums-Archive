---
title: "GTX 780Ti Not working"
date: 2015-12-26
forum: Hardware
---

### Post by Elias_Jrgensen on 2015-12-26
Hi all,

I have a problem with the driver support for my GTX 780Ti, the default drivers to be specific.
I just tried installing Ubuntu GNOME, but when i login i just get a black screen.

This happens not just with Ubuntu Gnome, but with every other distribution i try using.
I managed to get it to work with the proprietary Nvidia drivers on Arch, but then i got some color issues on one of my monitors. (I do don have ANY problems on windows)

I don't know if it's a problem with the Nouveau drivers, or if i need to do some specific configuration for my card.
This is a really annoying problem, so i would appreciate any help i can get.

I have an I7 3770K and a GTX 780Ti.

Many thanks
- Elias

---

### Post by Bashing-om on 2015-12-26
Elias_Jrgensen; Hi ! Welcome to the forum .

What release are you running ? 
Nvidia recommends the 352 version driver :
[http://www.nvidia.com/download/driverResults.aspx/95159/en-us](http://www.nvidia.com/download/driverResults.aspx/95159/en-us)
This driver is only available in later releases of linux.

What does the system advise of hardware and available drivers ?
Post back - Between Code Tags - the outputs of terminal commands:
```

lsb_release -a
sudo ubuntu-drivers devices
sudo ubuntu-drivers list

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Then we look at what is, and where we are going.

[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by Elias_Jrgensen on 2015-12-27
Thanks for the quick reply!

I will do that, but how will i post the output when i can't login to ubuntu?
I am dual booting with Windows 10m, if that's any help.

I'm running the 15.10 release, but this is not just the case with 15.10 Ubuntu, it's the same with Fedora etc. where the standard driver is Nourveau.

---

### Post by Bashing-om on 2015-12-27
Elias_Jrgensen; Hey ...

There are a few ways we can activate a terminal.
Try:
At the login screen key combo ctl+alt+F1.
This should activate a console interface, login here with username and pass word - there is no response to the screen when the pass word is entered .

Release 15.10 has the proprietary Nvidia driver available. I bet if we clean up old drivers, and install (maybe the 346 version as it seems the more stable ) anew a driver, all will be well .

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by Elias_Jrgensen on 2015-12-28
Bashing-om; 
I'm sorry, i must have explained my problem in a weird way, making it hard for you to understand.
I have no problem getting into a virtual console and executing the commands you specified.

However, when i can't login to the GUI and open a web browser, how am i supposed to paste the results from the commands?

---

### Post by Bashing-om on 2015-12-28
Elias_Jrgensen; Hey;

a few ways:
> 
However, when i can't login to the GUI and open a web browser, how am i supposed to paste the results from the commands?

one can manage to relay outputs. I consider our paste site an easier method.
Install the tool:
```

sudo apt install pastebinit

```
Now run:
```

lsb_release -a | pastebinit
sudo ubuntu-drivers devices | pastebinit
sudo ubuntu-drivers list | pastebinit

```
the results are URLs back to your terminal, pass these links back to the thread.
These outputs are more or less for your info, but will not hurt for us to see them too ! Once we know what the platform and hardware are, and we have a few options, we can then decide on what to do.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Elias_Jrgensen on 2015-12-28
Bashing-om; 

Great, thanks!
Here are the outputs of the commands:
```
[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"]1
2
3
4
[/TD]
[TD="class: code"][COLOR=#000000]Distributor ID:	Ubuntu
Description:	Ubuntu 15.10
Release:	15.10
Codename:	wily[/COLOR]
[/TD]
[/TR]
[/TABLE]

```
```
[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"] 1
 2
 3
 4
 5
 6
 7
 8
 9
10
11
12
13
14
15
16
17
18
[/TD]
[TD="class: code"][COLOR=#000000]== cpu-microcode.py ==
driver   : intel-microcode - distro non-free

== /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0 ==
vendor   : NVIDIA Corporation
modalias : pci:v000010DEd0000100Asv00001458sd00003628bc03sc00i00
model    : GK110B [GeForce GTX 780 Ti]
driver   : nvidia-352-updates - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin
driver   : nvidia-352 - distro non-free recommended
driver   : nvidia-340-updates - distro non-free
driver   : nvidia-340 - distro non-free

== /sys/devices/pci0000:00/0000:00:1c.6/0000:04:00.0/0000:05:08.0/0000:0b:00.0 ==
vendor   : Broadcom Corporation
modalias : pci:v000014E4d00004359sv00001043sd0000850Cbc02sc80i00
model    : BCM43228 802.11a/b/g/n
driver   : bcmwl-kernel-source - distro non-free[/COLOR]
[/TD]
[/TR]
[/TABLE]

```

```
[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"]1
2
3
4
5
6
[/TD]
[TD="class: code"][COLOR=#000000]nvidia-340
nvidia-352
nvidia-352-updates
bcmwl-kernel-source
nvidia-340-updates
intel-microcode[/COLOR]
[/TD]
[/TR]
[/TABLE]

```

---

### Post by Bashing-om on 2015-12-28
Elias_Jrgensen; Welp; shucks -

The 352 version is available and suites for the GeForce GTX 780 Ti graphic's card. But I do wonder why the 346 version is not offered.

Let's now look at what is installed and what the system reports:
```

dpkg -l | grep -i nvidia
sudo lshw -C display | pastebinit
cat /var/log/Xorg.0.log | pastebinit

```
With the idea to make sure the driver is installed, that the config app 'nvidia-settings' is also installed. One can control the monitors from the 'nvidia-settings' tool .

[INDENT][INDENT]it should just work
[INDENT][INDENT][INDENT]why not ?
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Elias_Jrgensen on 2015-12-28
Sure, here is the output

```

[COLOR=#000000][FONT=Verdana]  *-display
       description: VGA compatible controller
       product: GK110B [GeForce GTX 780 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:43 memory:f6000000-f6ffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
[/FONT][/COLOR]

```

Since the last one is so long, i will just provide you with the link: [http://pastebin.ubuntu.com/14243909/](http://pastebin.ubuntu.com/14243909/)

---

### Post by Bashing-om on 2015-12-28
Elias_Jrgensen; Well ...

You presently have the open source driver nouveau loaded.
As to the Nvidia driver.. the system say uh uh - no will do:
> 
3.969] (EE) Failed to load module "nvidia" (module does not exist, 0)


Monitors :
> 
4.217] (II) NOUVEAU(0): EDID for output DVI-I-1
[     4.217] (II) NOUVEAU(0): Manufacturer: PHL  Model: 8a8  Serial#: 3706

bk

4.217] (II) NOUVEAU(0): Serial No: AU51148003706
[     4.217] (II) NOUVEAU(0): Monitor name: 273PLPH

bk

4.217] (II) NOUVEAU(0): Printing probed modes for output DVI-I-14.217] (II) NOUVEAU(0): Printing probed modes for output DVI-I-1
4.217] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     4.276] (II) NOUVEAU(0): EDID for output DVI-D-1
[     4.276] (II) NOUVEAU(0): Manufacturer: SAM  Model: 8b2  Serial#: 808595762
 4.277] (II) NOUVEAU(0): Printing probed modes for output DVI-D-1
4.335] (II) NOUVEAU(0): EDID for output HDMI-1
[     4.335] (II) NOUVEAU(0): Manufacturer: SAM  Model: 8ce  Serial#: 808595764
4.335] (II) NOUVEAU(0): Monitor name: S24B300
4.336] (II) NOUVEAU(0): Printing probed modes for output HDMI-1

4.400] (II) NOUVEAU(0): EDID for output DP-1
4.400] (II) NOUVEAU(0): Output DVI-I-1 connected
[     4.400] (II) NOUVEAU(0): Output DVI-D-1 connected
[     4.400] (II) NOUVEAU(0): Output HDMI-1 connected
[     4.400] (II) NOUVEAU(0): Output DP-1 disconnected


Seems nouveau is happy happy to drive 3 monitors . But but I only see one card on the system :
> 
3.965] (--) PCI:*(0:1:0:0) 10de:100a:1458:3628 rev 161, Mem @ 0xf6000000/16777216, 0xe8000000/134217728, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[
is this showing that there are the 3 outputs on this one card ?

Is there no Nvida driver on the system ?
No return for:
```

dpkg -l | grep -i nvidia

``` ??

And does this file exist on your system:
```

cat /etc/X11/Xorg.conf

``` ??
------------------

You are presently getting a black screen on all monitors when the GUI is activated ? Strange as there are no errors reported in the log file.
What results if you power the system down - disconnect the auxiliary monitors and come back up on only the main monitor ?

Does X report anything for the desktop ? show:
```

cat .xsession-errors

```


This may be a real pain to find the reason why not as all reports with
[INDENT][INDENT]no problems seen[/INDENT][/INDENT]

---

### Post by Elias_Jrgensen on 2015-12-28
Bashing-on; This is weird...

You are correct, i have one graphics card with 3 monitors attached.

```

dpkg -l | grep -i nvidia
```
Does not return anything.
Also, Xorg.conf and .xsession-errors are not existing.
I tried only having 1 monitor plugged in, but the issue is the same. When i log in, i just get the gnome login background (i have Ubuntu GNOME installed, but the issue is the same on vanilla Ubuntu) and then i can't do anything.

This is probably very tiresome for you, but i just wanted to let you know that i appreciate your help! This is really bothering me! :)

---

### Post by Bashing-om on 2015-12-28
Elias_Jrgensen; Nawww ...

Not at all tiresome, just frustrating at the stonewall of my ignorance that we work'n presently to alleviate.

No output " dpkg -l | grep -i nvidia " -> Nvidia is not installed onto the system, not a bad thing yet
No " Xorg.conf " -> the use of said file is depreciated with the advent of Dynamic Kerenl Mode Setting, but with 3 monitors I had the thought it might be a factor
no " .xsession-errors " now that gives me cause to paause, I would think at the least that it would exist with an advisory that "Xsession: X session started for ......" ...

OK, let's get one possibility out of the way to cloud our think'n. Let's make sure that "you" are authorized to access your /home.
What permissions are set :
```

ls -al /home
ls -al /home/elias/

```
where 'elias' is your normal username on this system.

Then we next see what results when booting with the boot parameter "nomodeset" to disable DKMS, booting with the fall back graphic's driver. See what that tells us. 

There is a bunch I do not know, never having used multiple monitors. Maybe 'nouveau' just can not cope ? Though the log file says nouveau is all happy driving 3 monitors. See what results if we install the Nvidia proprietary driver ??

[INDENT][INDENT]there must be a reason
[/INDENT][/INDENT]

---

### Post by Elias_Jrgensen on 2015-12-28
Here is the output of "ls -al /home/"
```

[COLOR=#000000][FONT=Verdana]total 12
drwxr-xr-x  3 root  root  4096 Dec 26 12:52 .
drwxr-xr-x 23 root  root  4096 Dec 26 12:52 ..
drwxr-xr-x 12 elias elias 4096 Dec 28 18:56 elias
[/FONT][/COLOR]

```

And the output of "ls -al /home/elias": (yes, that was my username)
```

total 64
drwxr-xr-x 12 elias elias 4096 Dec 28 18:56 .
drwxr-xr-x  3 root  root  4096 Dec 26 12:52 ..
-rw-------  1 elias elias  280 Dec 28 21:22 .bash_history
-rw-r--r--  1 elias elias  220 Dec 26 12:52 .bash_logout
-rw-r--r--  1 elias elias 3771 Dec 26 12:52 .bashrc
drwx------  3 elias elias 4096 Dec 28 17:52 .cache
drwx------  2 elias elias 4096 Dec 26 12:55 .config
drwxr-xr-x  2 elias elias 4096 Dec 26 12:55 Desktop
drwxr-xr-x  2 elias elias 4096 Dec 26 12:55 Documents
drwxr-xr-x  2 elias elias 4096 Dec 26 12:55 Downloads
drwxr-xr-x  2 elias elias 4096 Dec 26 12:55 Music
drwxr-xr-x  2 elias elias 4096 Dec 26 12:55 Pictures
-rw-r--r--  1 elias elias  675 Dec 26 12:52 .profile
drwxr-xr-x  2 elias elias 4096 Dec 26 12:55 Public
-rw-r--r--  1 elias elias    0 Dec 28 18:53 .sudo_as_admin_successful
drwxr-xr-x  2 elias elias 4096 Dec 26 12:55 Templates
drwxr-xr-x  2 elias elias 4096 Dec 26 12:55 Videos
```

I know for a fact that the proprietary drivers should work. I got them to work on Arch Linux, however i got some color problems (i couldn't see shadows on webpages, perhaps too high contrast, i dont know).
Due to those problems, i would like to see if i couldn't get the Nouveau drivers to work. But if that doesn't work out, i will just have to find a way to fix those color problems with the Nvidia drivers.

The weird part is, that when i boot the live installer, all 3 monitors work fine and i can move the windows between the monitors and everything.

---

### Post by Bashing-om on 2015-12-28
Elias_Jrgensen; Welp !

Authorization is not an issue .

So we look at it as a driver issue, Try and prove this with booting up with the boot parameter 'nomodeset'.

Reboot and as soon as the bios screen clears depress and hold a shift key -> grub boot menu;
With the latest kernel selected, press the 'e' key for edit mode -> boot parameters screen .
In this screen arrow down to the line starting with linux, and across to "quiet splash'. add the term "nomodeset" - with out the quotes - and then key combo ctl+x to continue the boot process.

What now results ? all 3 monitors available ?  At this point I can accept there to be degraded graphics. that is not the issue.
If we have displays at this point, I am all in favor of installing the proprietary driver and see then what results .

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by Elias_Jrgensen on 2015-12-28
Bashing-on;

I added nomodeset right behind "quiet splash", so it said "quiet splash nomodeset".
This resulted in that i was able to login, but only one of my monitors were recognized by Ubuntu.

I also checked in Settings -> Displays but there was only one monitor, also.

---

### Post by Bashing-om on 2015-12-28
Elias_Jrgensen; Well, At least that is promising.

OK, how bout we install the proprietary driver. That should also install the GUI config tool " nvidia-settings". See what we can do from "nvidia-settings" .
```

sudo ubuntu-drivers autoinstall

```

Now reboot, do we have the tool installed ?
on the new boot what returns:
```

dpkg -l | grep -i nvidia

```

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by Elias_Jrgensen on 2015-12-28
Bashing-om;

I can now login with all 3 monitors connected, as i expected.
But i also now have the color issue on my HDMI monitor, that i spoke of before. (I have one HDMI monitor and two DVI monitors)
I can correct this in the nvidia-settings, but it is reset on boot
_______________________________
[ATTACH=CONFIG]266424[/ATTACH]
I am also getting this error message.

This is what "dpkg -l | grep -i nvidia" returns:
```

ii  bbswitch-dkms                               0.7-2ubuntu1                             amd64        Interface for toggling the power on nVidia Optimus video cards
ii  libcuda1-352                                352.63-0ubuntu0.15.10.1                  amd64        NVIDIA CUDA runtime library
ii  nvidia-352                                  352.63-0ubuntu0.15.10.1                  amd64        NVIDIA binary driver - version 352.63
ii  nvidia-opencl-icd-352                       352.63-0ubuntu0.15.10.1                  amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                0.8.1                                    amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                             352.21-0ubuntu1                          amd64        Tool for configuring the NVIDIA graphics driver

```

---

### Post by Bashing-om on 2015-12-28
Elias_Jrgensenl Hummm ...

The good thing is now we have something we can bite on .
> 
I can correct this in the nvidia-settings, but it is reset on boot

so we are looking at a config not sticking .
Have you looked into nvidia-prime, see if there is any tweaking leading to something positive that can be done ?


That error indicates would behoove us to see what xorg has to say:
```

cat /var/log/Xorg.0.log | pastebinit

```
Did the Nvidia installer make up a config file ( maybe yes, maybe not so yes ) .
```

ls -al /etc/X11/xorg.conf

```
If not maybe see what results when we have Nvidia try and make up a default config file .

[INDENT][INDENT]take care of the little things
[INDENT][INDENT][INDENT]big things will take care of themselves
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Elias_Jrgensen on 2015-12-28
Bashing-om;

I have not looked into Nvidia Prime, but i might do so, if you think that will be a help?

This is the output of "[COLOR=#000000][FONT=Ubuntu Mono]cat /var/log/Xorg.0.log": [http://pastebin.ubuntu.com/14248979/](http://pastebin.ubuntu.com/14248979/)[/FONT][/COLOR]

I looked, and xorg.conf is not existing.

EDIT: I just rebooted, and the settings i configured in nvidia-settings to fix my color issue has not been reset. It was resetting when i was using Arch Linux, but it doesn't seem to be the case right now. (YES!!)

---

### Post by Bashing-om on 2015-12-28
Elias_Jrgensen; Well ..

I see nothing in the xorg log file to be concerned about .. all looks rosy !

I am in favor of generating the Nvidia config file, If worse comes to worse, we can remove the file.
As advised the use of this file is depreciated, but with multi-monitors, might be the thing to do .

Reboot, and at the login screen ctl+alt+F1 to gain a console, and so X is not started.
I think in this instance that the 15.10 systemd will honor the upstart process calls.
Insure that X is not running:
upstart way :
```

sudo service gdm stop

```
where you are running gnome as the DE.
generate the file:
```

sudo nvidia-xconfig
sudo mv xorg.conf.new /etc/X11/xorg.conf

```
now start the desk top:
```

sudo service gdm start

```

Do you switch to the GUI ? 
I see in the log file that the Virtual terminal is VT2 ( standard is VT 7 - not sure what is going on here !)
maybe key combo alt+F2 to gain the GUI ???

What now for the displays ? Still good after another reboot ?

[INDENT][INDENT]hey it could happen
[/INDENT][/INDENT]

---

### Post by Elias_Jrgensen on 2015-12-29
Bashing-om; Success!!

Everything is working nicely now - i haven't gotten any errors so far.

If i get a problem with a setup in the future, should i just reply to this thread or make a new one?

Thanks for the help! I appreciate it! :D

---

### Post by Bashing-om on 2015-12-29
Elias_Jrgensen; Hey hey !

Wadda ya know !

Please advise on the resolution, did the generation of the xorg.conf file do the trick ?

If you are satisfied that resolution on this one issue is reached,
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Open a new thread on any new issue.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]together we do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Elias_Jrgensen on 2015-12-29
Bashing-om;

Indeed, i haven't gotten any error messages since i generated the xorg.conf file!
I will mark the thread as solved! :D

---

