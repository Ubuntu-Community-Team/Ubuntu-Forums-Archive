---
title: "Trouble with 18.04 LTS and nVidia 340.107 driver"
date: 2019-09-26
forum: Hardware
---

### Post by Gourmand on 2019-09-26
I worked with 14.04 LTS for years. Now I need 18.04 for some serious reasons. I upgraded 14.04 to 16.04 LTS without problems. In 16.04 all worked well. Then I upgraded 16.04 to 18.04 LTS with the same way. I have lost high-resolution GUI. From this step I can only use 640x380 screen. The 14.04 used driver nvidia-304 which 18.04 did not load. I removed this driver. After commands *apt-get update* and then *upgrade* and reboot it proposed install needed driver. In selection list there were only two options available - currently used *nouveau* and *nvidia-340*. I selected nvidia-340 and installed it. This driver is latest for used video adapter GeForce 8500 GT 512. After reboot I get error message - Plasma cannot use OpenGL. In GUI mode I can use only console. Graphics screen is black. All glx utilities fail with same message:

> :~$ glxgears
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Value in failed request:  0x0
  Serial number of failed request:  23
  Current serial number in output stream:  24


Please help!

---

### Post by SeijiSensei on 2019-09-26
Try running the command
```
sudo nvidia-xconfig
```
then rebooting.  Any better?

---

### Post by Gourmand on 2019-09-27
> **SeijiSensei said:**
> Try running the command
```
sudo nvidia-xconfig
```
then rebooting.  Any better?

Nope.

> WARNING: Unable to locate/open X configuration file.

Package xorg-server was not found in the pkg-config search path.
Perhaps you should add the directory containing `xorg-server.pc'
to the PKG_CONFIG_PATH environment variable
No package 'xorg-server' found
New X configuration file written to '/etc/X11/xorg.conf'

> :~$ sudo find / -name "xorg-server.pc"
:~$

Who made this distribution?... :-(

---

### Post by Autodave on 2019-09-27
Upgrading from one release to another often causes problems like this.  And you updated 2 releases.  I would download 18.04 and make a bootable DVD or thumb drive.  Boot your machine from that and see if the graphics work.  You just may find that the nouveau driver is your best choice.

---

### Post by Yellow Pasque on 2019-09-28
Are you sure you're not booting into a kernel from 16.04?

> You just may find that the nouveau driver is your best choice. 
Yeah, nouveau ran really well on an 8400GS I had.

---

### Post by SeijiSensei on 2019-09-28
Last time I checked the nouveau driver does not support hardware acceleration of H.264-encoded content. With contemporary fast CPUs that's less of an issue than it once was.

---

### Post by Gourmand on 2019-09-28
> **SeijiSensei said:**
> Last time I checked the nouveau driver does not support hardware acceleration of H.264-encoded content. With contemporary fast CPUs that's less of an issue than it once was.

I do not need h.264 acceleration. This is software development workstation. I need only Qt 5.12/13 working on it. But when nouveau used I cannot select any other resolution except 640x380.

---

### Post by Gourmand on 2019-09-28
> **Autodave said:**
> Upgrading from one release to another often causes problems like this.  And you updated 2 releases.  I would download 18.04 and make a bootable DVD or thumb drive.  Boot your machine from that and see if the graphics work.  You just may find that the nouveau driver is your best choice.

This could be an idea if there is no any other choice. I have got free USB stick for it.

---

### Post by CatKiller on 2019-09-28
> **Gourmand said:**
> The 14.04 used driver nvidia-304 which 18.04 did not load. I removed this driver... In selection list there were only two options available - currently used *nouveau* and *nvidia-340*. I selected nvidia-340 and installed it. This driver is latest for used video adapter GeForce 8500 GT 512. After reboot I get error message 

> **Gourmand said:**
> I do not need h.264 acceleration. This is software development workstation. I need only Qt 5.12/13 working on it. But when nouveau used I cannot select any other resolution except 640x380.

You need to decide which driver you want to use.

If you want to use nouveau, you'll need to help it out with the details of your monitor. Nouveau is not as good as the proprietary driver at gleaning that information from the monitor's EDID, so you'll need to put your monitor information in xorg.conf.

The proprietary nvidia driver is unable to upgrade cleanly from one branch to another. You need to completely purge the old branch before the installation of another branch will work. In this case it seems that you have cruft from 304 breaking the install scripts for 340.

For other issues, dmesg and the X log at /var/log/Xorg.0.log will help you identify the source of the problem.

---

### Post by Gourmand on 2019-09-28
> **CatKiller said:**
> You need to decide which driver you want to use.

If you want to use nouveau, you'll need to help it out with the details of your monitor. Nouveau is not as good as the proprietary driver at gleaning that information from the monitor's EDID, so you'll need to put your monitor information in xorg.conf.

I need 1920x1080 resolution. For me there is no difference which one driver use for this. I used 304 driver before cause nouveau did not work with integrated GPU. 

> **CatKiller said:**
> The proprietary nvidia driver is unable to upgrade cleanly from one branch to another. You need to completely purge the old branch before the installation of another branch will work. In this case it seems that you have cruft from 304 breaking the install scripts for 340.

Before install 340 driver I removed all packages with "nvidia" in their names.

---

### Post by Yellow Pasque on 2019-09-28
Once again, did you check in GRUB that you are booting into the correct kernel?

> **SeijiSensei said:**
> Last time I checked the nouveau driver does not support hardware acceleration of H.264-encoded content. 

You have to use the firmware from the proprietary driver. Luckily, it's fairly easy and a one-time job: [https://nouveau.freedesktop.org/wiki/VideoAcceleration/](https://nouveau.freedesktop.org/wiki/VideoAcceleration/)
After that, any video player that can use VDPAU will use the GPU to decode.

> Before install 340 driver I removed all packages with "nvidia" in their names. 
But did you purge them? Removing the packages will keep files in /etc and could cause issues. Specifically, it could keep nouveau blacklisted.

---

### Post by Gourmand on 2019-09-29
> **Yellow Pasque said:**
> Once again, did you check in GRUB that you are booting into the correct kernel?

Loaded kernel version is 4.4.0-164-generic. It is 18.04 LTS definitely. What do you mean by "correct kernel"?

> **Yellow Pasque said:**
> You have to use the firmware from the proprietary driver. Luckily, it's fairly easy and a one-time job: [https://nouveau.freedesktop.org/wiki/VideoAcceleration/](https://nouveau.freedesktop.org/wiki/VideoAcceleration/)
After that, any video player that can use VDPAU will use the GPU to decode.

I do not need play video on this machine.

> **Yellow Pasque said:**
> But did you purge them? Removing the packages will keep files in /etc and could cause issues. Specifically, it could keep nouveau blacklisted.

Yes of course. sudo apt-get remove --purge nvidia-<package1>... so on

Today is Sunday - therefore I did not yet try load Linux from USB-stick. But what I remembered from 2014 when I first installed 14.04 LTS - it was unable run nouveau in 1920x1080 on integrated GPU GeForce 6150. It started with screen completely in color garbage. Therefore I installed nVidia driver and used it. But now this machine has another one discrete GPU adapter GeForce 8500 GT. What should I do to allow nouveau work in 1920x1080 if USB-stick will load correctly? First I must purge nVidia driver of course. What to do next to allow 1920x1080 appear in screen settings? I never had deal with nouveau settings.

---

### Post by CatKiller on 2019-09-29
> **Gourmand said:**
> Yes of course. sudo apt-get remove --purge nvidia-<package1>... so on

Not all of the nvidia packages start with the string 'nvidia'.

You still don't appear to have checked your logs.

> What should I do to allow nouveau work in 1920x1080 if USB-stick will load correctly?

Add details about your monitor to xorg.conf.

---

### Post by Yellow Pasque on 2019-09-29
> **Gourmand said:**
> Loaded kernel version is 4.4.0-164-generic. It is 18.04 LTS definitely. What do you mean by "correct kernel"?

That's the kernel from 16.04. You're booting into the wrong one. Ubuntu 18.04 should have kernel version >= 4.15.x
[https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes/18.04.1#Linux_kernel_4.15](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes/18.04.1#Linux_kernel_4.15)

---

### Post by Gourmand on 2019-09-29
> **Yellow Pasque said:**
> That's the kernel from 16.04. You're booting into the wrong one. Ubuntu 18.04 should have kernel version >= 4.15.x
[https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes/18.04.1#Linux_kernel_4.15](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes/18.04.1#Linux_kernel_4.15)

What's the hell!
> :~$ cat /proc/version
Linux version 4.4.0-164-generic (buildd@lgw01-amd64-021) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.10) ) #192-Ubuntu SMP Fri Sep 13 12:02:50 UTC 2019
:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.3 LTS"


:shock: This was made by 18.04 installer, not me...

---

### Post by deadflowr on 2019-09-29
If installing on top of existing install and you do not overwrite it by reformatting, old kernels will still be there.

Edit:
Forgot to ask to check the /boot folder to quickly see what kernels are installed.
If installed from the 18.04.3 ISO then the kernel versions should be 5.0.X-X, as that's what 18.04.3 comes with.
Might be a simple re-running of the grub update command
```
sudo update-grub
```

---

### Post by Gourmand on 2019-09-29
> **deadflowr said:**
> If installing on top of existing install and you do not overwrite it by reformatting, old kernels will still be there.

Edit:
Forgot to ask to check the /boot folder to quickly see what kernels are installed.
If installed from the 18.04.3 ISO then the kernel versions should be 5.0.X-X, as that's what 18.04.3 comes with.
Might be a simple re-running of the grub update command
```
sudo update-grub
```

I upgraded online with command ```
sudo do-release-upgrade
```

---

### Post by deadflowr on 2019-09-29
Either method keeps old kernels.

---

### Post by Gourmand on 2019-09-29
```
sudo update-grub
```
not helped. It found only kernel 4.4 and previous 3.x from 14.04. No more kernel 5.&#1093; or 4.15. After reboot cat /proc/version tells the same as before.

Is there any way to fix this instead of install 18.04 from distribution ISO? I am not sure it will install properly. I already had read a lot of bad things about 18.04 LTS therefore I am not sure in this release.

But I need at least 18.04 to continue working with Qt5.12/13. It does not work in older versions.

---

### Post by deadflowr on 2019-09-29
Run
```
sudo apt install linux-generic
```
My guess is you don't have the linux-meta packages for 18.04 installed.
Possible if you originally installed from release point ISOs.
Point releases come with hwe kernels meta-packages which have a different specific name.
fwiw

---

### Post by Gourmand on 2019-09-29
```
sudo apt install linux-generic
```
Done. It installed 4.14 kernel and updated grub. SHAITAN!!!! It rebooted to 1920x1080! PLASMA WORKS!!! :guitar: :-({|= :-({|= :-({|=

But VNC server refuses connection to client. :-( May be just client and server update required. But in 640x480 mode it worked minutes ago.

---

### Post by deadflowr on 2019-09-29
> It installed 4.14 kernel and updated grub
?
Weird.
No version of Ubuntu has ever supported that kernel.
(except briefly during 18.04's development cycle.)

---

### Post by Gourmand on 2019-09-29
4.15... I was very surprised when got hi res mode. But I mandatory need VNC connection. After reboot it briefly worked. I saw large client window on other workstation. I saw settings GUI in it. But seconds later it closed. Next time I got only error message "connection refused".

---

### Post by Gourmand on 2019-09-30
VNC connection works some time after boot but very glitchy and slow. Then disconnects suddenly. Then it fails to reconnect. Both machines have same 1G network cards. In 14.04 it flew like a fly. What can be reason for present behavior?

---

### Post by Gourmand on 2019-09-30
Almost done.

Looks like I solved x11vnc crash by adding options -noxfixes -noxrecord -noxdamage to x11vnc autostart script. 
Froze akonadi and nepomuk - and have got about 1 GB memory more and free one processor core.

But sometimes interface freezes for just seconds. What can cause this?

---

### Post by Gourmand on 2019-09-30
Probably problem was inspired by baloo_file_extractor. It occupied more than 500 MB RAM and ate about 55% processor time. Hope it's disabling won't cause any problem more. Now system is almost reactive as 14.04 was. Even through VNC connection. But once x11vnc suddenly crached... :-k If anybody can tell why this can happen - I will look with great interest.

Now I can mark question as SOLVED.

---

### Post by Yellow Pasque on 2019-09-30
Maybe there are incompatibilities between versions of baloo. If you still want to use it, you might have to reset the databse:  [https://en.opensuse.org/SDB:Reset_Baloo_database](https://en.opensuse.org/SDB:Reset_Baloo_database)

---

### Post by Gourmand on 2019-09-30
> **Yellow Pasque said:**
> Maybe there are incompatibilities between versions of baloo. If you still want to use it, you might have to reset the databse:  [https://en.opensuse.org/SDB:Reset_Baloo_database](https://en.opensuse.org/SDB:Reset_Baloo_database)

I did not use it in 14.04. It appeared with 18.04 together. 

There are only 2 unknown small problems: 
1. Why the x11vnc sometimes crashes? Not often, between long time period - but sometimes...
2. Why after hibernation, after RAM image was saved and power was turned off - the motherboard suddenly awakes and restores? This was not happen in 14.04 - hibernation worked well instead. 

But this all does not forbid me work.

---

### Post by Yellow Pasque on 2019-09-30
> 2. Why after hibernation, after RAM image was saved and power was turned off - the motherboard suddenly awakes and restores? This was not happen in 14.04 - hibernation worked well instead.

It could be Wake on LAN (WoL)

---

### Post by Gourmand on 2019-10-01
> **Yellow Pasque said:**
> It could be Wake on LAN (WoL)

It is turned off in BIOS. The *ethtool* is not installed. And machine does not awake after turned off or suspended. It awakes only after hibernated.

---

