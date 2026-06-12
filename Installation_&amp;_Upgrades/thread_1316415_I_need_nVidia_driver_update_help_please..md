---
title: "I need nVidia driver update help please."
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by Visible Spirit on 2009-11-05
**Hi all,**


I have some questions about updating my nVidia driver.

**1)** Do I need to uninstall the current video driver and related files *before* installing a new one?

_Files currently installed from the Ubuntu repository_:

nvidia-glx-new | version: 169.12+2.6.24.18-25.2
nvidia-kernel-common | version: 200511028+ubuntu8
nvidia-new-kernel-source | version: 169.12+2.6.24.18-25.2
nvidia-settings | version: 1.0+20080304-0ubuntu.1

**2)** Should I install only from an Ubuntu repository, or is the nVidia download site driver just as safe/compatible for Ubuntu distro's?

_Current video card and driver_:

GRAPHIC CARD
	VGA controller
		nVidia Corporation NV34 [GeForce FX 5200] (rev a1) (prog-if 00 [VGA controller])
		Subsystem: Chaintech Computer Co. Ltd Unknown device 1942

NVIDIA GRAPHIC CARD INFORMATION
	Model name: GeForce FX 5200
	Card Type: AGP 8x
	Video RAM: 256 MB
	GPU Frequency: 250 MHz
	Driver version: NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008 (from Ubuntu restricted repository)

---------
lspci -v Output relative to my video card.

01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1) (prog-if 00 [VGA controller])
	Subsystem: Chaintech Computer Co. Ltd Unknown device 1942
	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 21
	Memory at f0000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (32-bit, prefetchable) [size=256M]
	[virtual] Expansion ROM at f1000000 [disabled] [size=128K]
	Capabilities: <access denied>

**3)** Should I use the recommended driver from nVidia?

_[Recommended driver from nVidia's site]("http://www.nvidia.com/object/linux_display_ia32_173.14.20.html")_:

Version: 173.14.20
Release Date: 2009.07.01
Operating System: Linux
Language: English (U.S.)
File Size: 19.20 MB

**4)** Or should I add *this* repository to my sources list in Synaptic and use the driver from there?

_[Ubuntu nVidia driver repository]("http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-173/")_:

[http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-173/](http://archive.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers-173/)

**5)** What if any difference is there between the nVidia download site driver(s) and the driver(s) in the Ubuntu repositories?

**6)** If I use the driver from nVidia's download site will it break after a new kernel update?

**7)** Will the driver from the repository be automatically updated via Synaptic as new higher version recommended drivers are added to the repository?

If someone can answer my questions and offer any advice about this I'd be very grateful.


[B]Thank you,
Visible Spirit[/B]

---

### Post by AmbientOcclusion on 2009-11-06
I always use the NVIDIA driver from the site. Sometimes with certain kernel updates you have to reinstall it, but it is fairly easy.

It seems like the drivers in Synaptic are a few releases behind.

It is always better to use the latest drivers, unless they are beta or pre-release.

To install new NVIDIA drivers:

CTRL+ALT+F1

login and password

```
sudo /etc/init.d/gdm stop
```

cd Desktop  (or wherever you downloaded the driver package to)

```
sudo sh NVIDIA-Linux-x86_64-190.42-pkg2.run
```
...of course you would put the name of the driver after the sudo sh command...

Select yes on the install questions, also installing the 32 bit set. After you click thru and have the nvidia installer update x, at command line type:

```
sudo /etc/init.d/gdm start
```

You should return to the login screen.

---

### Post by Visible Spirit on 2009-11-06
**Hi AmbientOcclusion,**


Thanks very much for your reply. Short and to the point. But I'm still left with a couple questions not answered that concern me. Redundancy is a MS-Windows trait I want to avoid here if possible, although on a MS-Windows system it is *required* to remove old video-card hardware drivers prior to installing new ones. Unlearning MS-Windows brainwashing doesn't happen over night, and so I ask these questions to better understand Linux systems in general. Some things Linux I understand very well, others I'm still learning. I suppose there isn't one person alone that has *all* the answers, but together we learn and that's what makes the Linux community unique to others IMO. Anyway, here we go....

I'm assuming there's no difference between nVidia's website dwnldd driver file(s) vs the driver file(s) on the repository, other than the repository versions are generally behind a version or more-(which I've noticed quite often on many counts, not just video drivers)? In other words, do the maintainers of Ubuntu's video-card drivers tweak them in any way specific to Ubuntu's various flavors?

Another question not clear for me is whether or not the old/previous driver(s) should be removed first, or is this accomplished when the new driver(s) are installed?

Should I keep the old driver as backup in case the new one doesn't perform properly, and if so, how would I go about switching from one to the other if necessary?

If the old driver(s) need to be removed first, then I'll need some guidance in the procedure(s) to do so please. I'm learning to use the terminal more and more little by little, but I'm no whiz when it comes to command-line operations, or more specifically, the bash code/syntax used to do so. All things come with practice... and help from good knowledgeable folks in doing so.

Again, any help is much appreciated. ;)


[B]Thanks,
Visible Spirit[/B]

---

### Post by AmbientOcclusion on 2009-11-06
Hi.

I have not had an issue with simply installing the new drivers. 

If you would like to switch, you can go to System >> Administration >> Hardware Drivers and if you want pick an older one. Which generally lists the recommended one from the repositories.

If you would like to remove the installed driver here are the steps:


Before removing, reset original and backup Xorg:
```

$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
$ sudo dpkg-reconfigure -phigh xserver-xorg

```

Install package dependencies:
```

$ sudo apt-get install build-essential linux-headers-`uname -r`

```

Remove old driver:
```

$ sudo apt-get --purge remove $(dpkg -l | grep nvidia | awk '{print $2}')

```

Getting Driver from command line (of course insert correct url to driver version you need the one I have is just an example and intentionally wrong.)
```

wget ftp://download.nvidia.com/XFree86/NVIDIA-Linux-x86/123-45/NVIDIA-Linux-x86_64-190.42-pkg2.run -O NVIDIA-Linux-x86_64-190.42-pkg2.run
```

To install follow the directions from my previous post.


To be on the safe side, you can reboot:
```
sudo reboot
```

If for some reason during the driver install NVIDIA didn't configure X you could do this:
```
sudo nvidia-xconfig
```
But I have yet to encounter this.

---

### Post by AmbientOcclusion on 2009-11-06
You may reference it as well:
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

I think the mention of mandatory removal is just a means to ensure no problems occur. But good advice.

---

### Post by Visible Spirit on 2009-11-06
> **AmbientOcclusion said:**
> You may reference it as well:
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

I think the mention of mandatory removal is just a means to ensure no problems occur. But good advice.


Thank you so much for your help. I looked at the thread you linked and will tackle this later this evening or sometime over this coming weekend. I'm very busy with other things at the moment, but wanted you to know I *greatly* appreciate all your help here.

I'll post my results when completed. ;)

Again, thanks!


[B]Regards,
Visible Spirit[/B]

---

### Post by AmbientOcclusion on 2009-11-08
Okay good luck!

---

### Post by Visible Spirit on 2009-11-11
Well... I'm in the process of doing this now and ran into a problem. I hope I didn't screw things up. Please look at the terminal sessions posted below. Things don't look right to me and my big concerns are in session #2 where it says;

"E: Couldn't find package linux-headers-uname -r"

*and.....*

"The following packages will be REMOVED:
  linux-restricted-modules-2.6.24-24-rt*
  linux-restricted-modules-2.6.24-25-rt* linux-restricted-modules-rt*
  linux-rt* nvidia-kernel-common* nvidia-new-kernel-source* nvidia-settings*
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
After this operation, 104MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort."

The two kernels listed are the only two I have installed. This doesn't make sense to remove them on top of the fact that it didn't install the "build-essential linux-headers-'uname -r'" as well. Something just doesn't look/feel right here.

```
Terminal Session 1:
-------------------

XXXXXXXXXX@ubuntu:~$ sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
[sudo] password for XXXXXXXXXX: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting nvidia-glx-legacy-envy for regex 'nvidia-glx*'
Note, selecting nvidia-glx-dev-envy for regex 'nvidia-glx*'
Note, selecting nvidia-glx-dev for regex 'nvidia-glx*'
Note, selecting nvidia-glx-new for regex 'nvidia-glx*'
Note, selecting nvidia-glx-new-envy for regex 'nvidia-glx*'
Note, selecting nvidia-glx-src for regex 'nvidia-glx*'
Note, selecting nvidia-glx-new-dev-envy for regex 'nvidia-glx*'
Note, selecting nvidia-glx-legacy-dev for regex 'nvidia-glx*'
Note, selecting nvidia-glx-new-dev for regex 'nvidia-glx*'
Note, selecting nvidia-glx-envy for regex 'nvidia-glx*'
Note, selecting nvidia-glx-legacy-dev-envy for regex 'nvidia-glx*'
Note, selecting nvidia-glx-legacy for regex 'nvidia-glx*'
Note, selecting nvidia-glx for regex 'nvidia-glx*'
E: Couldn't find package nvidia-glx*
XXXXXXXXXX@ubuntu:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gcjwebplugin-4.2
The following packages will be REMOVED:
  gcjwebplugin-4.2
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 65.5kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 264230 files and directories currently installed.)
Removing gcjwebplugin-4.2 ...
XXXXXXXXXX@ubuntu:~$ exit

*Note: autoremoved file via synaptic while purging repository version of nvidia video driver <sudu apt-get autoremove>: gcjwebplugin-4.2


Terminal Session 2:
------------------

XXXXXXXXXX@ubuntu:~$ sudo cp /etc/X11/xorg.config etc/X11/xorg.config.original
cp: cannot stat `/etc/X11/xorg.config': No such file or directory
XXXXXXXXXX@ubuntu:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20091111135547
XXXXXXXXXX@ubuntu:~$ sudo apt-get install build-essential linux-headers-'uname -r'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-uname -r
XXXXXXXXXX@ubuntu:~$ sudo apt-get --purge remove $(dpkg -l | grep nvidia | awk '{print $2}')
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-new is not installed, so not removed
The following packages were automatically installed and are no longer required:
  dpatch
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-restricted-modules-2.6.24-24-rt*
  linux-restricted-modules-2.6.24-25-rt* linux-restricted-modules-rt*
  linux-rt* nvidia-kernel-common* nvidia-new-kernel-source* nvidia-settings*
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
After this operation, 104MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
XXXXXXXXXX@ubuntu:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
XXXXXXXXXX@ubuntu:~$ exit
```

Initially I disabled the old nvidia video driver via '>System >Administration >Hardware Drivers', which removed it at that time. Session #1 was to make sure it was removed completely. At this time I'm running in the default mode of things relative to video. All's good relatively speaking, just no effects (i.e... no Avant Window Navigator, Compiz, etc.) which is to be expected at this point. Do I need to fix or reverse anything and/or start over? Any help/suggestions will be appreciated. Thanks.


[B]Regards,
Visible Spirit[/B]

---

### Post by Visible Spirit on 2009-11-12
[B]*Bump*


Any help/suggestions/advice would be greatly appreciated.


Thanks,
Visible Spirit[/B]

---

### Post by Visible Spirit on 2009-12-20
**[COLOR="Blue"]Okay, I need this answered asap tonight please.[/COLOR]**

I re-enabled my original video drvr right after the last "BUMP" posting above and all is/was well. Tonight I'm at this again, have followed AmbientOcclusion's instructions to-the-letter in his second posting illustrating how to remove the v169 nvidia driver, and have reached the same impasse/dilemma as before and need an answer asap from someone please.

Here's where I'm at;
```
The following packages will be REMOVED:
  linux-restricted-modules-2.6.24-24-rt*
  linux-restricted-modules-2.6.24-25-rt*
  linux-restricted-modules-2.6.24-26-rt* linux-restricted-modules-rt*
  linux-rt* nvidia-glx-new* nvidia-kernel-common* nvidia-new-kernel-
  source* nvidia-settings*
0 upgraded, 0 newly installed, 9 to remove and 0 not upgraded. After this operation, 169MB disk space will be freed. Do you want to continue [Y/n]?
```
...and am confused about what to answer here. Y/n? I realize it says remove "restricted-modules", but I'm concerned whether or not this can/will harm my installed system-kernel(s)? This is my main box and I can't afford any screw ups or inability to re-boot after-the-fact.

Someone knowledgeable about this process/stage of things please help with a quick response so I can resolve this dilemma. I'm writing this post on my laptop and have my desktop idling hoping for a quick response here asap.


Thanks,
Visible Spirit

---

### Post by Visible Spirit on 2009-12-20
BUMP


Anyone got an answer?

---

### Post by grackleman on 2009-12-21
Hi
I'm using Hardy 8.04 and a NX8400GS. I needed separate screens on the 2 monitors (not extended or big desktop). All I did was install ENVYNG (synaptic package manager). It automatically finds the correct nVidia or ATI drivers and installs them.
After synaptic installs it you will find envyng under applications>system tools. Run it and it will do the driver install.
After that is finished under system>administration there will be nvidia x server settings.

Don't use this because it will not be able to save changes to xorg.conf. Open a terminal and use 'sudo nvidia-settings' the you can save the changes.

---

### Post by Visible Spirit on 2009-12-21
Hi grackleman,


Thanks for your response. I've read conflicting comments about envyng and suppose I'm a bit confused about which way is the best way to maintain the correct up-to-date nVidia drivers without breaking things when the system gets updated, in particularly kernel updates. My intent was to follow AmbientOcclusion's instructions, then go to [this posting]("http://ubuntuforums.org/showthread.php?t=835573") to further the process with a script that would do in essence the same thing you claim envyng does.

But I reached a point where I wasn't sure of the results during AmbientOcclusion's posted process, and it seems AmbientOcclusion isn't anywhere to be found after his/her last posting, or maybe just doesn't have the answer I need?, or possibly assumed it was a dumb question?, I don't know. But the question remains for me, and that is to know (since I've gone so far with his/her instructions) whether or not by answering Y to the proposed terminal question, if the kernel(s) will be corrupted and un-bootable because it's stating removal of restricted modules in all three kernels I currently have and this concerns me regarding other restricted modules I may have installed via the repositories? Since it says "restricted modules will be removed", it came to mind to question whether or not this refers to 'all' restricted modules in the kernel, or simply the modules related to the nVidia drivers?

I know it may seem obvious by the terminal output, but since this isn't an area I have a lot of experience with, I'm asking for help to clarify the result of answering Y to the posed question. To those that are familiar with this procedure as stated, it may seem obvious, but I wanted to know for sure since this is my main box and I can't afford any losses or corruption. As it was, I chose n at the terminal last night and aborted the procedure because of no response here then.

So again, thanks for your response grackleman. You may have the answer I need here, but I'd like some confirmation/answers to my question(s) before I go any further. As noted, I've already gone part way, it seems kind of a mute point to change in mid-stream from one process to another toward the same goal. If you have the answer(s) then I'll thank you up front for them. If not, I at least thank you for your reply and will keep your advice under consideration. I look forward to your reply, thanks.


Regards,
Visible Spirit

---

