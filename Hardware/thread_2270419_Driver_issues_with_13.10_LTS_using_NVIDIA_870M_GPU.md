---
title: "Driver issues with 13.10 LTS using NVIDIA 870M GPU"
date: 2015-03-22
forum: Hardware
---

### Post by brent19 on 2015-03-22
My machine has a 870m GPU and an Intel integrated GPU.  I was hoping to run Ubuntu 13.10 for compatibility reasons for Salome-meca and OpenFOAM.

I have gone through a few different processes of cleaning out Nvidia drivers with apt-get --purge nvidia*. I have tried to simply sudo apt-get install nvidia-current.  I have downloaded the current .run file from Nvidia's website for linux 64 bit distributions.

All of the above methods get me to the point where the computer boots to a black screen where I can see a cursor and I can ctrl+alt+t to get the terminal up but there isn't a taskbar displayed or any window for the terminal(only text).

I can run nvidia-settings and it always displays the error "you do not appear to be using the nvidia x driver"(I have run nvidia-xconfig)

I believe I have an issue because I need more current drivers then the 331 nvidia drivers(which I have tried to install also) but the 331 drivers don't support 800 series GPUs.

To clarify what I have done so far.


I have 

(Before all of these processes I always log out of the x server(ctrl+alt+F1) and use the command  [FONT=Ubuntu Mono]sudo service lightdm stop)[/FONT]

[FONT=Ubuntu Mono]sudo apt-get remove --purge nvidia-*

[/FONT][FONT=Ubuntu Mono]sudo apt-get install nvidia-current

[/FONT]Then I restart the lightdm service and reboot

I have also installed using the Nvidia .run files found on Nvidia's driver website (I have tried the most current driver and also the 331 driver).

I have also blacklisted the following

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
I have also tried other combinations of purging and installing using apt-get (after updating the repositories suggested on other posts here) with no luck.

I am probably missing something obvious here.  Please let me know if further information is required. Thank you!

---

### Post by Keith_Helms on 2015-03-22
I'm on 14.04 not 13.10 and the nvidia-331 drivers (version 331.113)  support my geforce 860M GPU.  According to Nvidia's doc, the 331.113  driver should also support your 870M GPU - [http://www.nvidia.com/Download/driverResults.aspx/80533/en-us](http://www.nvidia.com/Download/driverResults.aspx/80533/en-us)   If the nvidia-331 driver for 13.10 is not up to the 113 level, then you may have to obtain a driver from another source, such as the xorg-edgers PPA.

When  I was trying to get Nvidia Optimus working a couple of weeks ago, I  also tried downloading drivers directly from Nvidia and that didn't work  for me either.  I also got myself into a fix a couple of times where I just got a black screen.

Make sure you have all the Nvidia drivers  removed whether from the repository (sudo apt-get purge nvidia*)
or from the .run file (I think you  invoke the .run file with the option --uninstall to get rid of them).  You can also remove all the blacklist entries you made.  Once you have Nvidia removed, run
```
sudo dpkg-reconfigure xserver-xorg
```
Then reboot and see if your system comes up using the Intel GPU.

If you get your GUI back using the Intel GPU, install nvidia-331 (if it's the 331.113 version) and nvidia-prime from the repository and reboot.  If that works, you should be able to open Nvidia X Server Settings and see an option for PRIME Profiles.  That should show you're running on Intel (Power Saving Mode) and give you the option to switch to Nvidia (Performance Mode).  The instructions say to log out and back in, but I found just logging out gave me a black screen and I actually had to reboot.  I sometimes got some error messages about something in X crashing after the first reboot, but I didn't get them on 2nd and subsequent reboots.

For me, this seemed to boil down to installing and uninstalling drivers until the planets somehow aligned and Nvidia Optimus decided to work.

---

### Post by brent19 on 2015-03-23
Well, I am now at a wider, less "zoomed in" black screen but still no gui.  I have installed and uninstalled drivers and still haven't gotten the planets to align unfortunately.

Excuse my ignorance, but when you say try installing from repositories, do you mean use the apt-get command?

---

### Post by Keith_Helms on 2015-03-23
Yuck.  It may be time to start poking through logfiles.  Start by looking at /var/log/Xorg.0.log and see what kind of errors are in there.  Do you have an /etc/X11/xorg.conf file?  I remember not getting a gui when that thing had "modesetting" listed as the driver for the Intel GPU.  I think I changed that to "Intel" and was able to get back to my desktop.

---

### Post by Bucky Ball on 2015-03-23
13.10 is no longer supported. Hasn't had updates, including security updates, for quite awhile. What works in 14.04 will possibly not apply to an EOL release. If you are required to install anything, you probably can't. 

Please upgrade to a supported release. 14.04 LTS might be the best bet. We can not give you much help with an EOL release. Please see [here]("http://ubuntuforums.org/showthread.php?t=2229730"). Good luck.

---

### Post by brent19 on 2015-03-23
I am just concerned about combatibility issues with Salome([http://www.salome-platform.org/downloads/current-version](http://www.salome-platform.org/downloads/current-version)).  I don't mind upgrading, however, the binaries for Salome are for 13.10

---

### Post by brent19 on 2015-03-23
I guess I'll update and give it a shot. Thanks for the help

---

### Post by Bucky Ball on 2015-03-23
Up to you, but as mentioned, as you're install is no longer getting updates it becomes more vulnerable over time and when/if something breaks we are not going be a lot of help with an EOL release. 

Salome is in the repositories in 14.04 LTS, incidentally, but not the 7.5 version. It's 6. something. It may be in the 13.10 repos, too, but you won't be able to install it probably as the 13.10 repositories are no longer up (and that may be a thorn in your side if installing Salome in 13.10 requires you to download dependencies from the 13.10 repos).

---

### Post by tokyobadger on 2015-03-23
[quote="Salome-platform"]
[h=3][IMG]http://www.salome-platform.org/downloads/current-version/bullet3.png/image_preview[/IMG] Universal binaries for Linux:[/h] 
[LIST]
[*]Download a version for *_64bits Linux_* (798 MB, *_md5sum_*)
[/LIST]
 *Note: 32bits platforms are not supported.* [INDENT]You have to login(register) to use download links[/INDENT] Universal binary package is a self-extracting archive. Just download  the file and execute it to install SALOME. The installer supports  options, run it with "-h" to see full list of available options.
 This packaging includes Debian Squeeze layer, all the pre-requisites  and SALOME 7.5.1 binaries. It is known to work on Linux distributions  like **Mandriva**, **Debian**, **Ubuntu**, **SUSE**, **RHEL**, etc ...
 *Please note that this packaging is not officially supported but feel free to report all related issues to the forum. *[/quote]
Seems like you should be able to get 7.5.1 running on 14.04

---

