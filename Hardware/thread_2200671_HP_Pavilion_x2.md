---
title: "HP Pavilion x2"
date: 2014-01-20
forum: Hardware
---

### Post by andre-d-perkins on 2014-01-20
I'm posting this because I didn't see that anyone else has tried to install Ubuntu on this device.

As for my experience, this is the first tablet pc (not mobile device) that I've come across that has a 64-bit processor (that's efi compatible).

Ubuntu runs pretty well on this device, although there is need for some tweaking.  I tried 13.04 and 13.10 and the live OS ran great, except that wifi did not work.  I ended up trying (obviously before it's time) 14.04 and it runs pretty good.  Bluetooth doesn't work, and it runs pretty hot until you install cpu frequency indicator (to lower cpu speed) and laptop mode.  After that, the tablet runs much cooler, but the battery life is still not great (it's not so great for a tablet pc).

I haven't tried to tinker with the bluetooth drivers, but I can post the device name from lsmod perhaps in a few hours.  I did search the internet but did not find much help in that area.

Gnome Desktop (shell) seems to be the best environment for the tablet interface, though Unity works fine also.  Multitouch is not supported with the keyboard touchpad yet, and I don't believe it's supported at all on the touchscreen (I haven't checked the tablet-friendly browser that comes with installing Gnome Desktop - think metro-IE-like).

If anyone else has this device, give it a shot.  I'll have to post more details later regarding how I got Linux onto this puppy.  I will say this - Clonezilla and clone immediately!!!!  There a so many partitions on this thing that you want to be prepared to restore an image if you mess something up.  Do this preferably before you create any recovery media (so that if that get's messed up you can try that again as well - HP only gives you one shot to create the media and then you're out of luck).

---

### Post by andre-d-perkins on 2014-01-20
In order to install Ubuntu onto this device you will need to turn off secure boot.  I did not find an option for legacy boot, but as long as your live cd/dvd/usb-drive has efi boot you're golden.  After cloning the entire hard drive (I can't stress this enough, because that's the only way to restore Windows if you so desire - and you may, because 14.04 coupled with the newness of this device is still very "beta.")

When performing the installation you will want to choose "Something Else" (I think that's the wording).  Only mess with the actual Windows OS partition. Just delete it, then create two new partitions:  1) An ext4 partition as root, leaving a few GBs for swap, and then 2) a swap partition.

One thing that annoyed me about the Windows partition was that it ran out of space so quickly.  With the OS and all of the updates by themselves you probably had about 7-10 GBs of space left (if you're lucky).  At one point I had less than 4 GBs left (which is ridiculous) on a 64 GB hard drive - and I hadn't even installed any large programs.  The hard drive space with Ubuntu is more than adequate, unless you're planning on building an HD video library - you need to rethink your choice in hardware if you're looking to do that.

Once you get it installed do

```
sudo apt-get install laptop-mode-tools
```

then

```
sudo apt-get install indicator-cpufreq
```

These two programs helped to increase the battery life and made the system run much cooler.  Without them your Pavilion x2 will run extremely hot.

I have not figured out which partition install grub on yet.  I've tried sda and sda1, but in both cases the laptop/tablet will begin a repair process.  Not to worry.  It will take you to a point where you can choose to boot using a device, then you can choose "Ubuntu" to boot from.  This only happens when you shutdown or restart the system.  If you frequently close the lid to put it to sleep, it will simply open to the login screen when you reopen your x2 for use.

You can tell the OS itself is not yet geared toward touchscreens.  You can, however, tell that Canonical is moving in that direction with the inclusion of a few Ubuntu Touch-esque features you will find if you install Gnome Desktop Environment (not sure if it's Canonical or Gnome).  There is a very IE Metro-ish browser included in the Gnome Desktop installation that seems like it would be quite useful as more elements of the OS utilize the potential of the touchscreen.

If you like to detach your screen (I'm assuming you would if you purchased a device like this:p) you will have to make sure you start the OnBoard onscreen keyboard ahead of time.  The keyboard takes a little getting used to, but it is very functional.  One thing I did notice, however, is that if you run into a situation where you need to intervene to correct an issue with the current run of the OS, you may need to reconnect your keyboard.  That said, don't go too far from your keyboard if you go into tablet mode.

There may be some things I'm forgetting, but I'm overall pleased with 14.04 on this device (again, wifi doesn't work with any other version as far as I can tell).  Pleas chime in if you have the device, or ask any questions.  I'll at least attempt to answer them.

I must say, I've been waiting to get full-blown Ubuntu on a tablet PC!  As "beta" as it feels so far, I'm very pleased with the results and am excited about the potential!

---

### Post by freak2 on 2014-05-16
HP Pavilion 13-p110nr x2

One problems I'm having with 14.04 (haven't tried any earlier versions yet) is getting the Ralink rt3290 bluetooth adapter to work. The wifi and bt are on the same pcie card, and the wireless is working flawlessly, but bluetooth manager isn't recognizing any bluetooth adapters. rfkill list all only shows a wifi adapter, but lspci actually shows the bluetooth adapter.

we you able to get bluetooth to function on yours?

---

### Post by calanor on 2014-05-29
Hi,

I have got an HP h009tu x2 tablet laptop. I have installed ubuntu 14.04 on it and went back to using Windows 8. For the last 7 years I have been using Linux and I had to go back because the performance in windows was much better, battery life is around 10-11 hours in windows vs 5-6 (max) on linux. On top of that no touchscreen support (that's not a big deal though). I want to go back to using ubuntu so bad, but there is not much work done in linux for battery life savings.

Processor: Intel Pentium Bay trail n3510

I have tried all power saving techniques tlp, p_state(makes performance worse I think) etc. Everything works except the battery life and the light sensor, haven't checked the gyro-sensor.

---

