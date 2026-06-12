---
title: "Acer Ferrari One Netbook"
date: 2009-12-16
forum: Hardware
---

### Post by moddie666 on 2009-12-16
Hi everyone,

since there appears to be no info at all about this Netbook's compatibility with Ubuntu, I am starting this thread.

So far I am very pleased with compatibility, after installing via USB and installing all the updates everything seems to work.

Most importantly:
Wired Network: works (of course)
Wireless: seems to work (it detects the Networks in my area, but I have none to test myself)
3D Acceleration: Works with the driver provided by Ubuntu + latest kernel (as of this date at least)

The only thing I did notice in these few hours of trying:
CPU-Frequency-scaling does not work: Why, I do not know (maybe not supported by the hardware at all?)

And the Webcam(integrated) and Mic.(headset) I did not test yet.
-------------------------------------------------------------------

What I did notice comparing Win 7 and Ubuntu (9.10) is that (flash)video has very poor performance in Ubuntu compared to Win, and hardware acceleration for video(in general) appears to be unavalable. (mplayer -vo vdpau .... produces audio but no video)

-------------------------------------------------------------------

Have fun playing around and please let me know of any errors on my part.

--EDIT--
I have now tried the Webcam and Mic with skype, works like a charm, except you have to use "microphone 2" in sound preferences > input.

If there's something else you wish me to test, let me know.

In Conclusion:
Two thumbs up for this one, unless you wanna watch HD video or FS Flash Video.

greetings
/moddie

---

### Post by ltsampros on 2009-12-19
Hehe! thanks about the report! I just bought this netbook! I'll give some testing results too in a few hours! (seems and feels awesome btw)

---

### Post by ltsampros on 2009-12-19
> **moddie666 said:**
> Hi everyone,
What I did notice comparing Win 7 and Ubuntu (9.10) is that (flash)video has very poor performance in Ubuntu compared to Win, and hardware acceleration for video(in general) appears to be unavalable. (mplayer -vo vdpau .... produces audio but no video)


I think that vdpau is an nvidia specific API :)

---

### Post by shababhsiddique on 2010-02-11
> **moddie666 said:**
> Hi everyone,

since there appears to be no info at all about this Netbook's compatibility with Ubuntu, I am starting this thread.

So far I am very pleased with compatibility, after installing via USB and installing all the updates everything seems to work.

Most importantly:
Wired Network: works (of course)
Wireless: seems to work (it detects the Networks in my area, but I have none to test myself)
3D Acceleration: Works with the driver provided by Ubuntu + latest kernel (as of this date at least)

The only thing I did notice in these few hours of trying:
CPU-Frequency-scaling does not work: Why, I do not know (maybe not supported by the hardware at all?)

And the Webcam(integrated) and Mic.(headset) I did not test yet.
-------------------------------------------------------------------

What I did notice comparing Win 7 and Ubuntu (9.10) is that (flash)video has very poor performance in Ubuntu compared to Win, and hardware acceleration for video(in general) appears to be unavalable. (mplayer -vo vdpau .... produces audio but no video)

-------------------------------------------------------------------

Have fun playing around and please let me know of any errors on my part.

--EDIT--
I have now tried the Webcam and Mic with skype, works like a charm, except you have to use "microphone 2" in sound preferences > input.

If there's something else you wish me to test, let me know.

In Conclusion:
Two thumbs up for this one, unless you wanna watch HD video or FS Flash Video.

greetings
/moddie

can anyone confirm about wireless networking?

---

### Post by moddie666 on 2010-02-14
Hi.

Since then i've been able to test wireless, works without a hitch.
As it seems it also has an integrated mic. that i could not get to work.

greetings
/moddie

---

### Post by xellink on 2010-02-28
I used Linux Mint 8 Helena x64 from usb and everything worked out of the box, including mic, except for multitouch which worked eventually. I created the usb in windows, note that the netbook has no optical drive but it is easily done. Refer to [http://www.pendrivelinux.com/install-linux-mint-8-to-a-flash-drive-in-windows/](http://www.pendrivelinux.com/install-linux-mint-8-to-a-flash-drive-in-windows/)

I suggest resizing using windows instead of gparted or it may cause windows to fail. Remember than Ubuntu/mint can access the NTFS folders

(It is odd that oem is used instead of a generic user, just create a new user and add him to sudo. It can be tweaked when you use Visudo. Its funny when helena does it by default i suppose but should work fine in ubuntu. Or alternatively, you can choose to not install in OEM mode by pressing any key when the first reboot screen appears. [http://forums.linuxmint.com/viewtopic.php?f=46&t=42128&p=242368&hilit=oem#p242368](http://forums.linuxmint.com/viewtopic.php?f=46&t=42128&p=242368&hilit=oem#p242368) )
Before you install your graphics driver, i recommend to update the linux headers and wireless as described below.

I noticed that the wireless does disconnect when too many pcs are online at the same time to my router. Installing a newer driver, the backports-modules-wireless-karmic-generic package using the package manager fixed this. You may need to remove unnecessary headers from your grub menu by just remove the unnecessary outdated headers in the package manager.

Restricted drivers can easily be installed after loading gnome in low graphics mode which should automatically prompt you. You will need to install the restricted drivers again under hardware drivers settings should you update your wireless drivers with the backports drivers. Graphics work fine, but have problems with cairo dock. ATI dislike Cairo i suppose. 2d acceleration works and glxgears work. Gnome-Do works fine as an alternative. Shouldn't need to touch the command line at all.

Tested the mic. It is necessary to increase the volume of the mic under volume settings before getting reasonable input. There are two mics. It tells the output so you know it when one is actually working.

Multitouch works with emulation. Doesn't work otherwise. synclient -m 100 doesn't detect 2 fingers. I had to do some tweaking in the commandline and some restarts before the touchpad worked. Mouse jumps around when two fingers are on the touchpad, but this can be fixed. I tweaked using gpointing-device-settings package and set it to chiral scrolling as well as enabled the mouse in xorg and allowed it direct memory and enabled SHMconfig. Restarting the netbook caused the mouse to not jump. This was before emulation. Finally, with emulation set, width of 5-6 and pressure of 0-30(10 works for me), two finger can be used easily by activating it under preferences->mouse. Sensitivity of the touchpad should be increased to increase performance, but that is up to you. Remember to disable everything under gpointing-device-settings Doesn't work out of the box like windows though. =( However, it works better than windows. Windows have problems in horizontal scrolling, which is quite a pain. Windows also has problems with two finger scrolling if the fingers are not parallel to each other.

The results from mint should be almost exactly the same as Ubuntu. Good luck and have fun.

---

### Post by moddie666 on 2010-04-29
Hi.

So as promised more 10.04 info.
Firstly I am by no means an Ubuntu pro but I'd like to think I know my way around.

So, after first upgrading about a month ago my netbook didn't work (hangs at the login, before i can log in) using an older kernel it behaved normally.
A few Upgrades/Updates later some weeks ago the same problem presented itself again, only this time no Kernel would work. So, no graphical Interface. Everything else seemed to work fine.
Then, being frustrated, I started playing around: gdm obviously did not work, xdm (could not find out how to tell it what to use) hung right after the login, kdm however yielded some results using the Gnome Failsafe Session (only combo that works for me) which works at least partially. I cannot update from the GUI however because whenever I click "check" or "install updates"(what does it do exactly?) in "sudo update-manager" the system freezes. This is especially annoying because "sudo apt-get update/upgrade" and checking for updates with synaptic does not cause a hangup.

By the way, booting from CD/USB yields the same result (hangs before the GUI starts with "try ubuntu without installing") even though the normal installer will work fine to the finish, with graphical niceties and all.

So anyone willing to "play" or help try it now, anyone else stay with 9.10 for now.
Stay tuned because I will update this as my netbook system becomes more or (hopefully) less broken.

still loving ubuntu
/moddie

---

### Post by jgfoot on 2010-05-01
I had some trouble installing 10.04 on my brand new Ferrari One, until I realized that this thing has an AMD64 processor.  Now, it is running without a problem.  So, two lessons learned: (1) the i386 installer will not stop you from being an idiot and installing the wrong distro on your AMD64 computer, and (2) an AMD64 is now cheap enough that you can expect to encounter it in a $600 notebook.

The computer itself?  Very good value.  The Ferrari branding is a little much.  The BIOS displays a full screen photo of some race car on boot.  Then, if you let it boot into Windows, you are treated to the sound of a Ferrari engine, and a function key that will take you to the Ferrari web site.  Yeah, that will get a lot of use...

---

### Post by KrisDouglas on 2010-05-02
Hello, no point starting a new thread while this one is so young. I have been having problems, big ones, getting Ubuntu 10.04 to boot on my AF1. I saw above you used a 64 bit installer and it worked. I'm going to try that, but I'm getting a really annoying freeze when I boot Ubuntu, it just hangs, can't do anything to the computer, not even drop to a command line TTY.

Any info on getting x32 to work would be cool, but I may try 64bit for the hell of it.

Thanks, Kris.

---

### Post by moddie666 on 2010-05-02
Hi.

Mine works again, after installing the fglrx drivers.
Even 3D accelleration.

@KrisDouglas
You might also try the alternate install CD which doesn't have "nice" graphics:
[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

If ubuntu is already installed you can also select recovery mode before boot. There you do get a command line.

greetings
/moddie

---

### Post by KrisDouglas on 2010-05-02
Ahh, so it's the fglrx drivers. Cause I'm seeing a UI, and I can move the mouse around, and then the ubuntu startup sound is played over and over, and then crashes. 

I'll try using the alternate install and loading fglrx that way. Let's see, thanks for that nugget of info :)

---

### Post by jgfoot on 2010-05-02
> **KrisDouglas said:**
>  I'm getting a really annoying freeze when I boot Ubuntu, it just hangs, can't do anything to the computer, not even drop to a command line TTY.

Yes -- those were the exact problems I was getting. I had that problem when using both the i386 "alternate" and live CDs. (Actually, I don't think the 10.04 i386 live CD booted. The 9.10 i386 live CD did). The problems stopped when I used the AMD64 version.

---

### Post by isterios on 2010-05-03
> **KrisDouglas said:**
> Ahh, so it's the fglrx drivers. Cause I'm seeing a UI, and I can move the mouse around, and then the ubuntu startup sound is played over and over, and then crashes. 

I'll try using the alternate install and loading fglrx that way. Let's see, thanks for that nugget of info :)

I've exactly the same issue Kris:
the system hangs during boot, before logging, with sound looping just before crash. I tried many reboots, and a complete reinstall: same issue.

But I'm afraid the AMD64 version doesn't solve our problem, as it is this version I actually run.


I just found this on google:
[https://bugs.launchpad.net/ubuntu/lucid/+source/fglrx-installer/+bug/552782](https://bugs.launchpad.net/ubuntu/lucid/+source/fglrx-installer/+bug/552782)

Could try this:
Had the same problem, and solved by executing this command manually, thus removing the xorg-drivers-fglrx instead of fglrx:
"sudo dpkg-divert --remove --rename --package xorg-driver-fglrx --divert /usr/lib/fglrx/libdri.so.xlibmesa /usr/lib/xorg/modules/extensions/libdri.so > /dev/null"
Afterwards, fglrx installs normally. However I still had a problem with the graphics card not being recognized, but this was solved after executing
"sudo aticonfig --initial"
After a reboot everything worked fine.

---

### Post by KrisDouglas on 2010-05-03
I solved this problem by plugging a network cable into the machine, booting into recovery mode with networking, wgetting the ati drivers, like so:

(recovery mode can be selected from GRUB, it's the second option usually, and then you need to select **root console with networking**, or something similar.)

```
wget http://www2.ati.com/drivers/linux/ati-driver-installer-10-4-x86.x86_64.run
```

Then, just in case I needed it, I then ran:

```
sudo apt-get install build-essential
```

Finally I loaded the really friendly ATI installer:

```
chmod a+x ati-driver-installer-10-4-x86.x86_64.run
```

```
./ati-driver-installer-10-4-x86.x86_64.run
```

I then followed the instructions, rebooted, and it was fixed, and worked perfectly. You can use either the 64bit or the 32bit, install from the boot menu of the CD and this works. Because for some reason the installer link on the CD worked, the try Ubuntu one didn't.

---

### Post by isterios on 2010-05-03
Thanks Kris.

I hopped not to install the ATI driver, to avoid problems after ubuntu updates.

I will try to boot also in safe mode and to work around the fglrx component, which seems to be the guilty one.

---

### Post by KrisDouglas on 2010-05-03
I don't think installing the ATI driver should cause any problems, I've had many updates come through and I've not had any problems, and when another kernel is scheduled for release you can just download the new ati driver ready to be installed when the kernel is updated, I used to do that back in the day with my Inspiron 6400.

---

### Post by isterios on 2010-05-04
Thanks Kris.

ok so I did this:
- F6 during boot to enter in shell mode.
- Installation of fglrx package
- Installation of fglrx-amdcccle package
- sudo aticonfig --initial

After reboot, it works perfectly.

---

### Post by isterios on 2010-05-06
Kris, do you meet issues with the wifi AR928x chipset?

Personnaly, I have regular disconnections after x minutes or when there are big packets used over the net.

I tried to install backports packages, but it's not better.

---

### Post by CoreyB. on 2010-05-07
Has anyone tried installing a 64-bit Ubuntu Netbook Edition using the directions here, [https://help.ubuntu.com/community/UbuntuNetbookEdition/amd64]("https://help.ubuntu.com/community/UbuntuNetbookEdition/amd64")?

This guide assumes you are on a fresh install of regular ubuntu 10.04 amd64 and installs all of the packages that you can on your amd64 version that are on the normal i386 version and removes packages that are not on the normal Netbook Edition.

Post back if this works or doesn't work for you, would really like to know.

---

### Post by ltsampros on 2010-05-11
> **xellink said:**
> I used Linux Mint 8 Helena x64 from usb and everything worked out of the box, including mic, except for multitouch which worked eventually. I created the usb in windows, note that the netbook has no optical drive but it is easily done. Refer to [http://www.pendrivelinux.com/install-linux-mint-8-to-a-flash-drive-in-windows/](http://www.pendrivelinux.com/install-linux-mint-8-to-a-flash-drive-in-windows/)

I suggest resizing using windows instead of gparted or it may cause windows to fail. Remember than Ubuntu/mint can access the NTFS folders

(It is odd that oem is used instead of a generic user, just create a new user and add him to sudo. It can be tweaked when you use Visudo. Its funny when helena does it by default i suppose but should work fine in ubuntu. Or alternatively, you can choose to not install in OEM mode by pressing any key when the first reboot screen appears. [http://forums.linuxmint.com/viewtopic.php?f=46&t=42128&p=242368&hilit=oem#p242368](http://forums.linuxmint.com/viewtopic.php?f=46&t=42128&p=242368&hilit=oem#p242368) )
Before you install your graphics driver, i recommend to update the linux headers and wireless as described below.

I noticed that the wireless does disconnect when too many pcs are online at the same time to my router. Installing a newer driver, the backports-modules-wireless-karmic-generic package using the package manager fixed this. You may need to remove unnecessary headers from your grub menu by just remove the unnecessary outdated headers in the package manager.

Restricted drivers can easily be installed after loading gnome in low graphics mode which should automatically prompt you. You will need to install the restricted drivers again under hardware drivers settings should you update your wireless drivers with the backports drivers. Graphics work fine, but have problems with cairo dock. ATI dislike Cairo i suppose. 2d acceleration works and glxgears work. Gnome-Do works fine as an alternative. Shouldn't need to touch the command line at all.

Tested the mic. It is necessary to increase the volume of the mic under volume settings before getting reasonable input. There are two mics. It tells the output so you know it when one is actually working.

Multitouch works with emulation. Doesn't work otherwise. synclient -m 100 doesn't detect 2 fingers. I had to do some tweaking in the commandline and some restarts before the touchpad worked. Mouse jumps around when two fingers are on the touchpad, but this can be fixed. I tweaked using gpointing-device-settings package and set it to chiral scrolling as well as enabled the mouse in xorg and allowed it direct memory and enabled SHMconfig. Restarting the netbook caused the mouse to not jump. This was before emulation. Finally, with emulation set, width of 5-6 and pressure of 0-30(10 works for me), two finger can be used easily by activating it under preferences->mouse. Sensitivity of the touchpad should be increased to increase performance, but that is up to you. Remember to disable everything under gpointing-device-settings Doesn't work out of the box like windows though. =( However, it works better than windows. Windows have problems in horizontal scrolling, which is quite a pain. Windows also has problems with two finger scrolling if the fingers are not parallel to each other.

The results from mint should be almost exactly the same as Ubuntu. Good luck and have fun.

Hi, 

could you please provide the xorg input device configuration you created for the touchpad? I'm facing similar problems. Thanks.

---

### Post by kryon on 2010-05-21
Help me please! I don't have wired connection with Lucyd. My router is a D-Link DI-524. I don't get download of  ati drivers.

Excuse for my english. Thanks.

---

### Post by kryon on 2010-05-21
> **KrisDouglas said:**
> I solved this problem by plugging a network cable into the machine, booting into recovery mode with networking, wgetting the ati drivers, like so:

(recovery mode can be selected from GRUB, it's the second option usually, and then you need to select **root console with networking**, or something similar.)

```
wget http://www2.ati.com/drivers/linux/ati-driver-installer-10-4-x86.x86_64.run
```Then, just in case I needed it, I then ran:

```
sudo apt-get install build-essential
```Finally I loaded the really friendly ATI installer:

```
chmod a+x ati-driver-installer-10-4-x86.x86_64.run
``````
./ati-driver-installer-10-4-x86.x86_64.run
```I then followed the instructions, rebooted, and it was fixed, and worked perfectly. You can use either the 64bit or the 32bit, install from the boot menu of the CD and this works. Because for some reason the installer link on the CD worked, the try Ubuntu one didn't.


I don't have network active:

ping 64.233.163.104
-> Destination Host Unreachable

In Asus eee wired is ok!

---

### Post by KrisDouglas on 2010-06-12
Hello there, if you are having problems with the wired network, try putting the driver on a USB stick. The mounting process of a usb stick through terminal is as follows:

Make the directory to mount the drive to:
```
sudo mkdir /media/usb
```

Find out what the drive device is called
```
sudo fdisk -l
```

Usually a usb stick is formatted to FAT, if that is the case:
```
sudo mount -t vfat /dev/sdb1 /media/usb
```

If it is an NTFS drive, it works the same way, just replace vfat with ntfs-3g

You will find the driver you downloaded within the /media/usb folder then, so you can ```
cd /media/usb
```

Hope that helps, Kris

---

### Post by leofishman on 2010-08-31
What is your experience with battery autonomy?

In ubuntu mine is a little bit more than 2 hours, while in windows it last for much more than 3 hours.

---

### Post by moddie666 on 2010-08-31
@leofishman
What are you doing in those 2 hours? Full brightness or not?
That battery life sounds about right (with full brightness),
but in Windows more components are simply off or in powersave.

@KrisDouglas
How exactly does putting a driver on a usb disk help
with the networking issue. I suppose you mean the ati
driver. which wont help with the network
Still I find it weird that wired networking wouldn't
work. I don't believe ubuntu is at fault here, in linux
normally just about any wired network works out of the box.

greetings
/moddie

---

### Post by leofishman on 2010-08-31
[QUOTE=moddie666;9788895]@leofishman
What are you doing in those 2 hours? Full brightness or not?
That battery life sounds about right (with full brightness),
but in Windows more components are simply off or in powersave.

I didn't have full brightness, but I had firefox and chrome open, and in firefox there was a site with many flashes, after closing firefox, I gained an extra hour autnomy.

thanks,
leo

---

### Post by moddie666 on 2010-08-31
A website with a lot of flash likely means that one core is fully occupied.
also reducing the backlight brightness to its lowest gives quite a boost
normally. The "shiny" display unfortunately makes it pretty useless
outside in the sun.

Also there should an option to automatically turn down the display brightness
when you're idle, this can however be quite annoying at times. Just try and
see how you like it.

greetings
/moddie

---

### Post by habiwan on 2010-09-22
Hi,

I just bought one as well, I am using 10.10 devel version 64-bit. Works like a charm execpt the CPU scaling. I tried 10.4 first and saw it was not working... I will try to get that to work else battery is down quick.

---

### Post by habiwan on 2010-09-23
> **habiwan said:**
> Hi,

I just bought one as well, I am using 10.10 devel version 64-bit. Works like a charm execpt the CPU scaling. I tried 10.4 first and saw it was not working... I will try to get that to work else battery is down quick.

OK, so the initial installation is done. 
Webcam works very well, I used cheese. But video recording freezes...
Everything else is working fine, no need to install GPU ATI drivers, compiz is running very well.

Things I am currently investigating, please help me on this if you can:

Touchpad drives that supports multitouch?
CPU modules that allow frequency change?

Maybe a nice graphical grub... but I can do that.

cheers

---

### Post by moddie666 on 2010-09-23
The Processor does not support CPU frequency scaling because it lacks PowerNow.
[http://en.wikipedia.org/wiki/Athlon_64#Athlon_X2_Dual_Core_Processor_L310](http://en.wikipedia.org/wiki/Athlon_64#Athlon_X2_Dual_Core_Processor_L310)


How did you get compiz effects without hardware accelerated graphics?
Are you sure 3D is working? you can check with "glxgears"

About multitouch as someone else in this thread already mentioned seems to be a lot of work.
---############---
Multitouch works with emulation. Doesn't work otherwise. synclient -m 100 doesn't detect 2 fingers. I had to do some tweaking in the commandline and some restarts before the touchpad worked. Mouse jumps around when two fingers are on the touchpad, but this can be fixed. I tweaked using gpointing-device-settings package and set it to chiral scrolling as well as enabled the mouse in xorg and allowed it direct memory and enabled SHMconfig. Restarting the netbook caused the mouse to not jump. This was before emulation. Finally, with emulation set, width of 5-6 and pressure of 0-30(10 works for me), two finger can be used easily by activating it under preferences->mouse. Sensitivity of the touchpad should be increased to increase performance, but that is up to you. Remember to disable everything under gpointing-device-settings Doesn't work out of the box like windows though. =( However, it works better than windows. Windows have problems in horizontal scrolling, which is quite a pain. Windows also has problems with two finger scrolling if the fingers are not parallel to each other.
---############---
Personally I think the touchpad on this machine is quite useless.
On mine at least the sensitivity is way too low, Windows or Linux
makes no difference at all. Has anyone else had this experience
or is it possible mine is faulty?

greetings
/moddie

---

### Post by habiwan on 2010-10-01
> **moddie666 said:**
> The Processor does not support CPU frequency scaling because it lacks PowerNow.
[http://en.wikipedia.org/wiki/Athlon_64#Athlon_X2_Dual_Core_Processor_L310](http://en.wikipedia.org/wiki/Athlon_64#Athlon_X2_Dual_Core_Processor_L310)


How did you get compiz effects without hardware accelerated graphics?
Are you sure 3D is working? you can check with "glxgears"

About multitouch as someone else in this thread already mentioned seems to be a lot of work.
---############---
Multitouch works with emulation. Doesn't work otherwise. synclient -m 100 doesn't detect 2 fingers. I had to do some tweaking in the commandline and some restarts before the touchpad worked. Mouse jumps around when two fingers are on the touchpad, but this can be fixed. I tweaked using gpointing-device-settings package and set it to chiral scrolling as well as enabled the mouse in xorg and allowed it direct memory and enabled SHMconfig. Restarting the netbook caused the mouse to not jump. This was before emulation. Finally, with emulation set, width of 5-6 and pressure of 0-30(10 works for me), two finger can be used easily by activating it under preferences->mouse. Sensitivity of the touchpad should be increased to increase performance, but that is up to you. Remember to disable everything under gpointing-device-settings Doesn't work out of the box like windows though. =( However, it works better than windows. Windows have problems in horizontal scrolling, which is quite a pain. Windows also has problems with two finger scrolling if the fingers are not parallel to each other.
---############---
Personally I think the touchpad on this machine is quite useless.
On mine at least the sensitivity is way too low, Windows or Linux
makes no difference at all. Has anyone else had this experience
or is it possible mine is faulty?

greetings
/moddie

Hi moddie666,

Thanks for your reply, good to know about the AMD CPU...

Compiz is still working like a charm, I even did daily upgrades with 10.10, all fine with the hardware.

Results of glxgears:
habiwan@habiwan-laptop:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
273 frames in 5.0 seconds = 54.518 FPS
300 frames in 5.0 seconds = 59.888 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 1378 requests (1377 known processed) with 0 events remaining.



habiwan@habiwan-laptop:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
273 frames in 5.0 seconds = 54.518 FPS
300 frames in 5.0 seconds = 59.888 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 1378 requests (1377 known processed) with 0 events remaining.

Thanks for your help about multitouch, I read the original post already, but got stuck with enabling chiral scrolling as well as  xorg (direct memory and enabled SHMconfig). First, installing in 10.10 the gpointing-device-settings does not have any chiral options in the GUI. I am not too keen on creating a /etc/X11/xorg.conf without knowing exactly what goes in there. 

I don't have multitouch, but scrolling works now thanks to your help. I can live with that...

All in all am happy with the touchpad, even in Windows (allright in Windows the multitouch is pretty shitty, both fingers have to be EXACTLY horizontally, like you said... but no sensitivity issues).

As for the 3D, I don't know, it worked straight away from 10.10. I never tried 10.04

Thanks again!!

---

### Post by ltsampros on 2010-10-01
> **habiwan said:**
> Hi moddie666,

Thanks for your reply, good to know about the AMD CPU...

Compiz is still working like a charm, I even did daily upgrades with 10.10, all fine with the hardware.

Results of glxgears:
habiwan@habiwan-laptop:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
273 frames in 5.0 seconds = 54.518 FPS
300 frames in 5.0 seconds = 59.888 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 1378 requests (1377 known processed) with 0 events remaining.



habiwan@habiwan-laptop:~$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
273 frames in 5.0 seconds = 54.518 FPS
300 frames in 5.0 seconds = 59.888 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 1378 requests (1377 known processed) with 0 events remaining.

Thanks for your help about multitouch, I read the original post already, but got stuck with enabling chiral scrolling as well as  xorg (direct memory and enabled SHMconfig). First, installing in 10.10 the gpointing-device-settings does not have any chiral options in the GUI. I am not too keen on creating a /etc/X11/xorg.conf without knowing exactly what goes in there. 

I don't have multitouch, but scrolling works now thanks to your help. I can live with that...

All in all am happy with the touchpad, even in Windows (allright in Windows the multitouch is pretty shitty, both fingers have to be EXACTLY horizontally, like you said... but no sensitivity issues).

As for the 3D, I don't know, it worked straight away from 10.10. I never tried 10.04

Thanks again!!


Guys I have this laptop for almost 9 months and I haven't been able to get the correct sensitivity of the touchpad. I mean it's so s***y on my setup  that I always use a mouse cause I can't even move the pointer from point A to point B.  Did you do sth in specific ?

Nevertheless I use the laptop cause I pretty much like the specs and it is a viable portable. Regarding use and battery life at first I was around 04:30 but now it is sth like 03:40/04:00 (brightness set a couple of bars before 0 and with wifi always on).

Regards

---

### Post by moddie666 on 2010-10-01
Hello.

I suspect that on some of these netbooks the touchpad is just plain broken. I did not have any issues in the beginning, but over time it took more and more force to get the touchpad to register my finger. That's a bit disappointing for a €600 machine, but doesn't matter to me anyway since I almost always use a mouse.

greetings
/moddie

---

### Post by chiossif on 2010-10-22
Hi to all.

I just got my Acer F1 and I've installed 10.10 AMD64 at once :-)

With glrx driver I'm at:
```

2641 frames in 5.0 seconds = 528.157 FPS
3035 frames in 5.0 seconds = 606.890 FPS
2978 frames in 5.0 seconds = 594.810 FPS
2909 frames in 5.0 seconds = 581.705 FPS
1209 frames in 5.0 seconds = 241.422 FPS
650 frames in 5.0 seconds = 129.960 FPS
2640 frames in 5.0 seconds = 527.926 FPS
2966 frames in 5.0 seconds = 593.048 FPS
3013 frames in 5.0 seconds = 602.514 FPS
2982 frames in 5.0 seconds = 596.388 FPS

```
with compiz enabled and rotating the cube on low values.

I've also changed the System->Preferences->Startup Application preferences->Gnome Login sound->Edit->Command: /usr/bin/canberra-gtk-play --id="ferrari" --description="GNOME Login"
(ferrari is the ogg version of the ferrari.wav login sound)

The ONLY problem that annoys me is the mic:
While I've followed [this](http://ubuntuforums.org/showpost.php?p=9238540&postcount=31) the solution is not permanent.
Is there any other way to fix the microphone?

Thanks.

---

### Post by isterios on 2011-02-25
> **chiossif said:**
> Hi to all.

I just got my Acer F1 and I've installed 10.10 AMD64 at once :-)

With glrx driver I'm at:
```

2641 frames in 5.0 seconds = 528.157 FPS
3035 frames in 5.0 seconds = 606.890 FPS
2978 frames in 5.0 seconds = 594.810 FPS
2909 frames in 5.0 seconds = 581.705 FPS
1209 frames in 5.0 seconds = 241.422 FPS
650 frames in 5.0 seconds = 129.960 FPS
2640 frames in 5.0 seconds = 527.926 FPS
2966 frames in 5.0 seconds = 593.048 FPS
3013 frames in 5.0 seconds = 602.514 FPS
2982 frames in 5.0 seconds = 596.388 FPS

```
with compiz enabled and rotating the cube on low values.


Debian with ati drivers:

5465 frames in 5.0 seconds = 1092.910 FPS
5460 frames in 5.0 seconds = 1091.984 FPS
5489 frames in 5.0 seconds = 1097.714 FPS
5319 frames in 5.0 seconds = 1063.698 FPS
5659 frames in 5.0 seconds = 1131.771 FPS
4477 frames in 5.0 seconds = 895.267 FPS
5626 frames in 5.0 seconds = 1124.908 FPS
5899 frames in 5.0 seconds = 1179.724 FPS
5991 frames in 5.0 seconds = 1197.999 FPS
5698 frames in 5.0 seconds = 1139.540 FPS

If someone knows how to make the multitouch work, I have absolutely no idea.

---

### Post by xellink on 2011-05-04
> **isterios said:**
> If someone knows how to make the multitouch work, I have absolutely no idea.

There is a MUCH easier way to get multitouch working. I know my previous post was a little complicated but it is no longer relevant due to HAL. I knew this over a year now but i forgot to update this page. IF you are installing Maverick or Lucid, your touchpad woes are just a click away. I cannot remember what I did but I will get back to this post tonight, but the easiest method is to install the new synaptics driver.

There is a not as efficient other way which i used originally since 10.04 and up. You can run this at startup every boot.
Method
Copy this and run in a script:

#!/bin/bash
xinput set-int-prop 'SynPS/2 Synaptics TouchPad' "Synaptics Two-Finger Pressure" 32 4
xinput set-int-prop 'SynPS/2 Synaptics TouchPad' "Synaptics Two-Finger Width" 32 7
xinput set-int-prop 'SynPS/2 Synaptics TouchPad' "Synaptics Two-Finger Scrolling" 8 1 1
xinput set-int-prop 'SynPS/2 Synaptics TouchPad' "Synaptics Jumpy Cursor Threshold" 32 250


Of course, if you have the patience to wait till tonight, i will provide a better solution.

Update: oops, i remembered replying you isterios last year, but i have lost my 'sent messages'. If you could post my solution here that will be great

---

### Post by xellink on 2011-05-06
> **xellink said:**
> 
Of course, if you have the patience to wait till tonight, i will provide a better solution.

Update: oops, i remembered replying you isterios last year, but i have lost my 'sent messages'. If you could post my solution here that will be great

Ahh, i remember the solution. Just install synaptics-dkms driver. U can find it in .deb form. Remove all useless mouse scripts. when u restart comp, it should work when u enable under mouse preferences. Good luck.

---

### Post by andreasnj on 2011-05-06
@xellink:

Hi, I'm an ubuntu newb, just installed 11.04 x64 on my Acer Ferrari One. How do I install/where can I download the synaptics-dkms driver?

11.04 x64 works like a charm except poor performance in compiz, but I lack the skills to find out why :-P

---

