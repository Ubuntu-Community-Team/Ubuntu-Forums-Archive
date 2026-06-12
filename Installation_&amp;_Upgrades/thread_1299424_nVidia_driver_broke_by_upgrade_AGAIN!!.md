---
title: "nVidia driver broke by upgrade AGAIN!!"
date: 2009-10-23
forum: Installation &amp; Upgrades
---

### Post by fryser_d on 2009-10-23
[COLOR="Red"]Cool! Nice new upgrades! *Click*
Woke up tomorrow, BANG! system at "Low graphic" blablabla

Error:"Please waste your @%%2#?$ day with us, trying fixing that #$?@"
Why in the WORLD would they touch my beeeeautiful VGA Card with their sticky sticky drivers AND with no rollback possible? God Ubuntu exist for more than 10 years now... grow up damit! :mad: Why would you ask Windows to try that to see how much lawsuits it would bring...

/*take sip of Jack Daniel's*/ 

Ouff! Ok now that I took that out of my system... Lets begin.[/COLOR]

[COLOR="Blue"][SIZE="3"]
-e9400_1333, nVidia_8800GT512MB, 4GDDR3_1333, Sata500G
-Ubuntu 9.04 - the Jaunty Jackalope
-Kernel 2.6.28-15-generic
-Nvidia Driver installed: (173 and 180)[/SIZE][/COLOR]

[COLOR="Red"][SIZE="4"]_Problem:_[/SIZE][/COLOR]
After the upgrade of the 22 Oct
When I boot it says an error occurred your sys will start up with low graph > I checked the logs BOOM! "Could not open: /libmodeles/2.6.28-16-generic/kernel/drivers/video/nvidia/nvidia.Ko"

[COLOR="Red"][SIZE="4"]_What I tried:_[/SIZE][/COLOR]
[LIST=1]
[*]-System>Admin>HardwareDrivers
[*]-Nvidia (180) driver: NOT activated.
[*]-Activate.
[*]-wait........
[*]-back to window with driver not activated.
[*]-Loop 3X same results.
[/LIST]

[LIST=1]
[*]-Check the net for answers.. blablabla: Need to reinstall drivers.
[*]-Download new drivers (185) and the (190) Beta
[*]-Install (190)Beta: Error: Need to shutdown all Xservers; -Damn!
[*]-Shutdown Xservers
[*]-Install (190)Beta: Error: Need Kernel 2.6.28 source; -WTF!? AH! The hell with that.
[*]-Install (185):Error: Need to shutdown all Xservers; -Damn!
[*]-Shutdown Xservers
[*]-Install (185): Message:"We will download kernel source, install and config for you!"; -Cool! /*click Yes*/
[*]-Install (185): Error: "Unknow host"; -Wut?
[*]-ping google.com: "Unknow host" -WUUUUUT!?
(when I quit gnome my Internet connection shutdown.) :confused:
[/LIST]

[LIST=1]
[*]-Reboot
[*]-Choose Ubuntu kernel 2.6.25: Same thing
[/LIST]


[COLOR="Red"][SIZE="4"]_What I need:_[/SIZE][/COLOR]

- The command to activate my Internet connection in terminal with gnome shutdown or the nVidia installation

- A (How to) install my CURRENT kernel source for the nVidia installation :/

- Any suggestions... :popcorn:


Thx for your time guys :)

fryser.

---

### Post by creiz on 2009-10-23
Calm down, buddy. Nobody's going to help if you bitch about everything. Take a sip of Jack Daniels, yeah, and gimme some. 

First of all, close all Xservers by yourself, if it's not already done.

Sudo to a terminal, I think it's still CTRL-ALT-F2 or F3. 

Try to manually activate you ETH0 connection by typing (in root)

ifup eth0 (where the 0 is a zero, not a O"

Wait. Restart your steps :)

Oh! and btw, make sure you have downloaded your kernel sources. (By downloading them BEFORE attempting to install your drivers.) 

apt-cache search kernel-sources(and look for your version.)

Oh! maybe you need to CHMOD 777 your nvidia.ko maybe the permissions are wrong. unlikely, but it happenned to me once. 

And again, buddy, calm down. You look too good to be angry. smile, and I'll take you to a strip club :D

---

### Post by fryser_d on 2009-10-24
Thx for your quick answer creiz

**1-**
> sudo ifup eth0
Didn't startup my internet connection... I also tried
```
sudo ifconfig eth0 up
```
didn't work either :(


**2-**
> Oh! maybe you need to CHMOD 777 your nvidia.ko
Tried AND I rename/copy nvidiafb.ko to nvidia.ko.... didn't work. :/


**3-**
I search on the web a How to install the Kernel Source and I found: [[source]]("https://help.ubuntu.com/community/Kernel/Compile#Get the kernel source")
> 
sudo apt-get build-dep linux-source
apt-get source linux-source

Starting from Hardy (8.04) this has changed to: 
sudo apt-get build-dep linux-image-$(uname -r)
apt-get source linux-image-$(uname -r)

Took about 10 mins, tried Again... didn't work...


May be I'm just over thinking something... :confused:
m I on the right tracks?

Y my Internet connection shutdown when I close gnome and how I get that kernel source working :/

Thx for your time.
Fryser

---

### Post by ghettofreeryder on 2009-10-24
```
sudo apt-get install linux-headers-server build-essential
```
then
```
wget ftp://download.nvidia.com/XFree86/Linux-x86/185.18.36/NVIDIA-Linux-x86-185.18.36-pkg1.run
```
or
```
wget ftp://download.nvidia.com/XFree86/Linux-x86_64/185.18.36/NVIDIA-Linux-x86_64-185.18.36-pkg2.run
```
then you need to kill gdm so you
CTRL+ALT+F1
then
```
sudo /etc/init.d/gdm stop
```
then
```
sudo chmod +x NVIDIA...run
```
then
```
sudo ./NVIDIA...run
```

There are newer drivers available, but I figured Id link you to the latest stable version.  Keep a copy of the drivers on your computer, as any time you do a kernel upgrade, you will need to reinstall the drivers

---

### Post by fryser_d on 2009-10-24
thx ghettofreeryder.
I tried what you said, butI still have the same issue :frown:

**/var/log/nvidia-installer.log**:popcorn:
> nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sat Oct 24 12:44:50 2009
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : [ftp://download.nvidia.com](ftp://download.nvidia.com)
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 185.18.36.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
ERROR: Unable to connect to download.nvidia.com (unknown host)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.28-16-generic/build'
-> Kernel output path: '/lib/modules/2.6.28-16-generic/build'
ERROR: If you are using a Linux 2.4 kernel, please make sure
       you either have configured kernel sources matching your
       kernel or the correct set of kernel headers installed
       on your system.
       
       If you are using a Linux 2.6 kernel, please make sure
       you have configured kernel sources matching your kernel
       installed on your system. If you specified a separate
       output directory using either the "KBUILD_OUTPUT" or
       the "O" KBUILD parameter, make sure to specify this
       directory with the SYSOUT environment variable or with
       the equivalent nvidia-installer command line option.
       
       Depending on where and how the kernel sources (or the
       kernel headers) were installed, you may need to specify
       their location with the SYSSRC environment variable or
       the equivalent nvidia-installer command line option.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).


```
fryser@fryser-pc:/lib/modules$ ls
2.6.28-11-generic  2.6.28-14-generic  2.6.28-15-server   2.6.28-16-server
2.6.28-13-generic  2.6.28-15-generic  2.6.28-16-generic  2.6.28-6-386

```

Why the installer cries like that? I have everything installed! I don't get it. :(

---

### Post by cossist on 2009-10-24
I'm in the same boat. I've tried installing the latest as well as previous drivers 180.44 - 190.42. Each time I get the installer complaining about the kernel source. I was hoping to wait for the new release but I might be headed for a fresh install

---

### Post by fryser_d on 2009-10-24
^ If you find solution please share! 

Good luck :KS

---

### Post by scoopit on 2009-10-24
Actualy, [creiz]("http://ubuntuforums.org/member.php?u=189622"), I think he's right about the bitching.
While you may be right about not getting help etc. he's having a point about this video crap not working right.

Testing changes is what's it all about. 
Ubunty is not ready for the desktop while these things are still around.
You and me will find a way out, but what about the average user ?
There are lots of excuses, but if you want to conquer the desktop you have to be right every time ;-)

...says a 9.04 64-bit user who just lost data after a kernel hang after upgrading to 2.6.28-16...
seems to be related to resume issues, I'm annoyed, it worked before...
and a few days ago it cost me  alot of time to install the nvidia drivers on a 8.04 LTS system...

---

### Post by Shazaam on 2009-10-24
Try this...
```
sudo apt-get install linux-headers-$(uname -r)
```
Then do the gdm shutdown dance posted earlier. Run the Nvidia installer next. Reboot and you should be golden.

---

### Post by fryser_d on 2009-10-25
Thx for your reply Shazaam

> 
sudo apt-get install linux-headers-$(uname -r)
...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



It's all already there. But Why it doesn't register?

In the log it says:
> If you are using a Linux 2.6 kernel, please make sure
you have configured kernel sources matching your kernel
installed on your system. If you specified a separate
output directory using either the "KBUILD_OUTPUT" or
the "O" KBUILD parameter, make sure to specify this
directory with the SYSOUT environment variable or with
the equivalent nvidia-installer command line option.

Maybe I should use one of these commands.
But when they say "environment variable" are they taking about "options" like: ```
sudo ./NVIDIA...run --KBUILD=/lib/modules/2.6.28-16-generic/kernel
``` 

I'm sure it's something really stupid like that. :P

---

### Post by frisket on 2009-10-25
> **cossist said:**
> I'm in the same boat.

Same here. 8.10 and 9.04 docs claim to spot the fact that I have a crappy old nVidia Geforce 4 and will install the old nv driver, but they don't. They go right ahead and install some broken driver, so now the only way into my system is via single-user mode, and I can't get a network connection in that (if it's possible, would some kind soul please explain how? using ifconfig eth0 up and /etc/init.d/networking start both fail to do anything). All the suggestions I can find all assume you can log in and that you have a net connection. 

Maybe it's time to try Fedora...

---

### Post by fryser_d on 2009-10-26
Up! :popcorn:

---

### Post by ozzyprv on 2009-10-26
Same here.
I was able to fix the nVidia drivers issue with every kernel upgrade until this last one.
See what at did before [_here_]("http://ubuntuforums.org/showthread.php?p=8167032#post8167032") 

I tried that and did not work. I have to spend some more time goign from the begining of that post and see if that works.

In the mean time, if you find a solution please let us know (I will do the same).

---

### Post by Saghaulor on 2009-10-26
> **scoopit said:**
> Actualy, [creiz]("http://ubuntuforums.org/member.php?u=189622"), I think he's right about the bitching.
While you may be right about not getting help etc. he's having a point about this video crap not working right.

Testing changes is what's it all about. 
Ubunty is not ready for the desktop while these things are still around.
You and me will find a way out, but what about the average user ?
There are lots of excuses, but if you want to conquer the desktop you have to be right every time ;-)

...says a 9.04 64-bit user who just lost data after a kernel hang after upgrading to 2.6.28-16...
seems to be related to resume issues, I'm annoyed, it worked before...
and a few days ago it cost me  alot of time to install the nvidia drivers on a 8.04 LTS system...

+1

Although you win more with honey than you do with vinegar.

At the very least if you're going to release shoddy updates have the decency to code a warning about the risks involved before installing.

---

### Post by ozzyprv on 2009-10-27
> **ozzyprv said:**
> Same here.
I was able to fix the nVidia drivers issue with every kernel upgrade until this last one.
See what at did before [_here_]("http://ubuntuforums.org/showthread.php?p=8167032#post8167032") 

I tried that and did not work. I have to spend some more time goign from the begining of that post and see if that works.

In the mean time, if you find a solution please let us know (I will do the same).

Got nVidia driver working again with kernel 2.6.28-16-server

See [_this post_]("http://ubuntuforums.org/showthread.php?p=8172873#post8172873") for details.

---

### Post by to3000 on 2009-10-27
i had the same problem when upgrading to ubuntu 9.04 when i tryed ext4, i reinstaled ubuntu with ext3 and the drivers worked!!!

---

