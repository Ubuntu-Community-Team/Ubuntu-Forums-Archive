---
title: "Latest Nvidia Drivers (8756) Not Working on Ubuntu"
date: 2006-04-08
forum: Hardware &amp; Laptops
---

### Post by RiffX on 2006-04-08
Hello,

I have a bit of a problem with the latest NVidia drivers (8756, released yesterday) running on Ubuntu Breezy. I need these drivers because they are the first to work with my GPU (GeForce Go 7400).

Following NVidia's instructions, I hit CTRL+ALT+F1 to switch to terminal, then kill GDM with:

```
sudo /etc/init.d/gdm stop
```

For some reason, I get a message saying 'gcc-version-check failed', but a little Googling found this was solved with:

```
export CC=gcc-3.4
```

It then seems to install perfectly, it auto-configures xorg.conf and I can restart GDM with:

```
sudo /etc/init.d/gdm start
```

And lo! The chip works! BUT...

The moment I reboot, I can a message telling me that xorg.conf is not configured properly, and the X Server can't start. I've had to restore the backup to get GDM working again.

If anybody has any ideas, I've posted the old (working) and the new (faulty) xorg.conf files with this post. Any help much appreciated.

---

### Post by tseliot on 2006-04-08
1) Type:
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common

2) Uninstall the driver from the nvidia installer:

CTRL+ALT+F1

sudo /etc/init.d/gdm stop

cd &#8220;directory where you have the nvidia installer&#8221;

sudo sh name_of_the_nvidia_installer --uninstall

3) Install the driver again (as described in my guide)

4) It is likely that the new driver is ignoring the Modline you have set in your xorg.conf

sudo nano /etc/X11/xorg.conf

Add the following option to the Section "Device" in your xorg.conf: 

```
Option "UseEDID" "False"
```

---

### Post by jalm111 on 2006-04-08
Have you tried simply using the old xorg.conf?

---

### Post by RiffX on 2006-04-08
Thanks for your help, tseliot, but I'm afraid it didn't work.

I followed your instructions exactly, but I wasn't sure what you meant by:

> Install the driver again (as described in my guide)

I found [this]("http://doc.gwos.org/index.php/Install_Nvidia_driver") page through the link at the end of your post, so I tried that installation method. I added the option to the xorg.conf using nano, but when I attempted to restart GDM or reboot, I got the same blue-screen "Cannot Start the X Server" message", and I had to restore my backup.

I also tried re-installing the proprietary drivers using simply:

```
sudo sh NVIDIA-Linux-x86-1.0-8756-pkg1.run
```

...followed by your amendment to xorg.conf, but that failed too.

Do you have any further ideas?

jalm111, I can use the old xorg.conf file, but it loads the generic 'nv' driver, which doesn't have 3D acceleration or OpenGL support. That's the reason I'm trying to get the proprietary drivers to work.

It just seems odd that the NVIDIA driver should work when I install it and run GDM straight away, but then fail when I reboot. Could this lead anywhere...?

---

### Post by Ensnared on 2006-04-08
Can you post your /var/log/Xorg.0.log?

There's obviously a problem with the new driver, as the difference between your working and faulty config-file is the driver they use for the display adapter.

One thing you could try is just using your old config-file, but edit it manually changing "nv" to "nvidia" in the Device-section for the card.

---

### Post by tseliot on 2006-04-08
Ok, let's try to diagnose the error:

Boot with the "nv" driver in your xorg.conf

Then (after Ubuntu has booted) Set the driver to "nvidia" in your /etc/X11/xorg.conf
Log out and Press CTRL+ALT+F1

You will get to the command line (no GUI)
Type:

```
sudo /etc/init.d/gdm stop (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm stop (if you use KDM)
```

Then:
```
startx -- -verbose 5 -logverbose 5
```

You will see several lines with the same error.

Then if you can't get to the command line press CTRL+ALT+F1 or CTRL+C (select NO if it asks you if you want to see the output of the error or something like that)

Then type this in order to copy the output of the error to your home folder:
```
sudo cp /var/log/Xorg.0.log /home/your_username/Xorg.0.log
```
(Of course you have to replace "your_username" with your username)

Access the GNOME or KDE again in the following way:
```
sudo nano /etc/X11/xorg.conf
```
Set the driver back to "nv" instead of "nvidia"
CTRL+O to save
CTRL+X to exit

```
sudo /etc/init.d/gdm stop (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm stop (if you use KDM)
```

Then
```
sudo /etc/init.d/gdm start (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm start (if you use KDM)
```


Post the content of that file (which you can find under /home/your_username/Xorg.0.log )

---

### Post by DoktorSeven on 2006-04-08
I've found that Debian-based distros like to randomly change my Xorg / XF86Config files back to a nonworking state if I do anything manually (like install new NVidia drivers or such).  I really wish I knew what exactly does this so I can disable it...

(I think I temporarily fixed it once by chmod'ing the config file to 444 (read-only, even for owner) :) )

---

### Post by RiffX on 2006-04-08
Hi guys, thanks for all your help.

Ensnared - I've posted the /var/log/Xorg.0.log (see below) as 'Log01'.
DoktorSeven - I'm afraid I don't know what you mean by "chmod'ing the config file to 444". Perhaps you could explain to a newb! ;-)

tseliot - Thank you for your comprehensive instructions. I've followed them exactly, and posted the version of /var/log/Xorg.0.log you asked for as "Log01". I've also tried re-installing the NVIDIA drivers, letting the installer configure the xorg.conf again, and then logging how the X Server starts with that. You'll remember that the NVIDIA driver actually loads immediately after installing, but then fails to load after a reboot.

I've posted three versions of the /var/log/Xorg.0.log file as follows:

[LIST]
[*]Log01: Original (generic) xorg.conf with driver='nv' changed to driver='nvidia' [as requested] (does NOT work!).
[*]Log02: Xorg.conf as auto-configured by NVIDIA Driver 8756 but WITHOUT reboot (this DOES work!)
[*]Log03: As Log02, but AFTER a reboot (this does NOT work!)
[/LIST]

I hope this is clear!

Thanks again.

---

### Post by tseliot on 2006-04-09
> **RiffX]Hi guys, thanks for all your help.

Ensnared - I've posted the /var/log/Xorg.0.log (see below) as 'Log01'.
DoktorSeven - I'm afraid I don't know what you mean by "chmod'ing the config file to 444". Perhaps you could explain to a newb!  said:**
> 
[*]Log01: Original (generic) xorg.conf with driver='nv' changed to driver='nvidia' [as requested] (does NOT work!).
[*]Log02: Xorg.conf as auto-configured by NVIDIA Driver 8756 but WITHOUT reboot (this DOES work!)
[*]Log03: As Log02, but AFTER a reboot (this does NOT work!)
[/LIST]

I hope this is clear!

Thanks again.
1) Do you use a LCD monitor (DVI?)?

2) Can you try to add this option in the Section Device of your xorg.conf:
```
Option   "UseDisplayDevice" "DFP"
```

Tell me if it works, please

---

### Post by RiffX on 2006-04-09
Hi again,

> 1) Do you use a LCD monitor (DVI?)?

I use the laptop's own built-in monitor. There are no other monitors connected.

> 2) Can you try to add this option in the Section Device of your xorg.conf:
Option   "UseDisplayDevice" "DFP"

I've added this option, but sadly it doesn't work. I've tried it with both the original xorg.conf (modified to Driver='nvidia') and the xorg.conf as auto-configured by the NVIDIA installer.

I've posted the logs, in addition to the previous ones, as follows:

[LIST]
[*]Log04: Original (generic) xorg.conf with driver='nv' changed to driver='nvidia', and Option "UseDisplayDevice" "DFP" added to Device section (does NOT work!).
[*]Log05: Xorg.conf as auto-configured by NVIDIA Driver 8756, after a reboot and with Option "UseDisplayDevice" "DFP" added to Device section (does NOT work!).
[/LIST]

---

### Post by morpheus_clio on 2006-04-09
Why doesn't we can't update the drivers with synaptic?? I'm using the old repository version because I can't configure correctly the new drivers! If exists an repository version why isn't updated?

---

### Post by RiffX on 2006-04-09
These drivers were only released two days ago, on a Friday evening. I guess it takes a little time for someone to update Synaptic. I don't know the ins and outs of this, perhaps someone could correct me?

---

### Post by trent dillman on 2006-04-10
Solved it here on Dapper:

Drop to tty, then:

```
sudo -s
apt-get --purge remove nvidia-*
apt-get install build-essential linux-source
sh NVIDIA-Linux-x86-1.0-8756-pkg1.run -e -a
```

Uninstall the previous driver using the prompts. Kernel module installation path should be default. Do not get a precompiled kernel module. The kernel source path should be ok as it is. X installation prefix should be /usr/lib/xorg, not /usr/X116. X module installation path should be /usr/lib/xorg/modules. OpenGL installation prefix should be /usr. Installer installation prefix should be /usr/. Say yes to NVIDIA's OpenGL header files.

Then, it will compile!

It may ask to back up old files, just say yes to that...

And don't bother letting it touch your xorg.conf, just say no and then ok to the last screen.

---

### Post by `Dale Snider on 2006-04-17
[QUOTE=trent dillman]Solved it here on Dapper:

Drop to tty, then:

```
sudo -s
apt-get --purge remove nvidia-*
apt-get install build-essential linux-source
sh NVIDIA-Linux-x86-1.0-8756-pkg1.run -e -a
```


Uninstall the previous driver using the prompts. Kernel module installation path should be default. Do not get a precompiled kernel module. The kernel source path should be ok as it is. X installation prefix should be /usr/lib/xorg, not /usr/X116. X module installation path should be /usr/lib/xorg/modules. OpenGL installation prefix should be /usr. Installer installation prefix should be /usr/. Say yes to NVIDIA's OpenGL header files.

Then, it will compile!

It may ask to back up old files, just say yes to that...

And don't bother letting it touch your xorg.conf, just say no and then ok to the last screen.[/QUOTE]

If you have upgraded gcc it may not match with gcc used to compile kernel. Nvidia install-script tells you the gcc version. List gcc versions and make sure you have it "ls -l /usr/bin/gcc*". If not there, use synpatic-manager to load it. Then before starting the Nvidia install "export CC=gcc-3.4"

---

### Post by oddisej on 2006-04-21
Hallo everybody,

I had the same problem with new NVIDIA driver istallation.
Following instructions from 'dale snider, I tried following:

sudo -s
apt-get --purge remove nvidia-*
apt-get install build-essential linux-source
sh NVIDIA-Linux-x86-1.0-8756-pkg1.run // without -e -a

and now everything seems to work.

Thanks.

---

### Post by LocoMan on 2006-04-22
Greetings (first post here)... :)

I'm trying Ubuntu for the first time and since thursday I've been trying to install the nvidia drivers, basically with the same effect described here. It installs aparently with no problems, but once I reboot it enters into GDM, seems to work nicely except that doesn't run anything 3D (glxgears gives me a segment fault or something like that, translating from spanish). If I reboot, it looks like it's going to enter, but then it shows a screen with the top half black and the bottom half white, and hangs there. I have to use ctrl+alt+F1 to get to the command line and then even if I do a /etc/init.d/gdm stop, if I try to run the installer it tells me that it seems that X is still running.

I've uninstalled it and installed it several times already, both from synaptic (that kill X instantly, gives me the blue screen that says that it can't enter) and from nvidia (that does as I described up here)

Any ideas what could be happening?.. it works perfectly with the "nv" driver, but of course, I don't get 3D then... but it just doesn't want to work with any of the nvidia drivers...

EDIT: I think I got it to work... basically by formatting the HD and installing ubunto from scratch, and then followed the instructions here before installing anything else. It seems to work, I rebooted 3 times and I didn't get the blue screen.

---

### Post by boosted_sled on 2006-04-23
I have a nvidia 7600 and a Shuttle mb with a geforce 6300 on board.  I have the video buffer on the 6300 set to 'disabled' in setup.  After an hour of pain fighting conflicts with the legacy driver, I followed tselliot's excellent howto and installed the 8756 driver again.  It worked, but on reboot it failed.  I installed the driver again from scratch.  It worked.  I rebooted - it worked.  I went for full shutdown and rebooted again - it worked.  No modifications were made by the system to the Xorg.conf file.

I have no explanation for this and hate it when random keystrokes fix problems.  My buddy with a shuttle is still battling this one.

Any further intelligence much appreciated.

---

### Post by LocoMan on 2006-04-24
Again I got the blue screen when rebooting. However, I started reading the report to see if I could make sense of something on it and I found this:

"Error: API mismatch: the NVIDIA kernel module has the version 1.0.7667, but this X module has the version 1.0.8756. Please make sure that the kernel module and all NVIDIA driver components have the same version"

Maybe that's what it's causing problems?... any way to fix it?...

EDIT: I think this was the first reboot since I let ubuntu update itself (I kept ignoring updates until I had the nvidia driver working). Maybe it updated X and that's why is giving problems now?

---

### Post by boosted_sled on 2006-04-24
After I got X working I discovered my 3D accel wasn't.  Doing some research on the Nvidia site, I discovered that my /usr/lib/libGL.so was pointed at the original OpenGL driver.  After mv'ing that one out of the way and running ldconfig I could finally start burning some rubber.

---

### Post by carlao2005 on 2007-01-28
Hello Riffix,

Have you solved the problem?
Thanks in advance
Kind Regards

---

