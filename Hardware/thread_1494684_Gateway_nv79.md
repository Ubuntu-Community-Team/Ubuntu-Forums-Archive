---
title: "Gateway nv79"
date: 2010-05-27
forum: Hardware
---

### Post by combatwombat_nz on 2010-05-27
Report on a new Gateway nv79 laptop: i5-430, 4GB Ram, 500 GB hdd, i915 VGA, 17" 1600x900 LCD.

Very nice machine, at a great price. Hardware compatibility not so great. I first tried loading the latest Archlinux on it...no go due to the i915 driver being absolutely crappy with Xorg 1.8 and any kernel...it would just black screen at the start of module load.

So I tried the 10.4 Ubuntu i386; the live cd mostly worked, so it got installed. All's good bar the sound...you will need a kernel 2.6.34.999  from here :[https://wiki.ubuntu.com/KernelMainlineBuilds](https://wiki.ubuntu.com/KernelMainlineBuilds)

Another note: DON'T use Compiz and attempt to do a screenshot using the gnome default key press PRTSC or ALT+PRTSC... the machine flips out , dumping cryptic kernel messages, dropping out of gnome.

With Compiz on, PRTSC will work ONCE, then subsequently result in general weirdness. Compiz OFF= working PRTSC. Being that this is the wifey's laptop, she couldn't care less for graphical bling...

---

### Post by combatwombat_nz on 2010-07-06
Ok, since then the screenshot has again stopped. :-s I guess one of the regular updates loaded another new component...and blamo. Kernel still same as above.

This machine will also lock up fairly often, doesn't matter where.

Doing diagnostics tonight I found Skype eating 200% (2 cores) at idle, and kded4 another 95%. Yikes. Killed both, restarted skype, and it's behaving. Am not sure how/why kded even loaded. She has complained that the machine is sometimes slow (and it's a bloody rocketship for hardware!), so I need to jump on it when she complains again to see what is eating it up.

Another gripe: cannot get the numpad on the keyboard to work properly for Home/End...must have some weird mapping going on. It is set as US 105.

Am going to boot back into Arch, and see if they have fixed the KMS intel issues yet ;)

---

### Post by combatwombat_nz on 2010-07-06
I love talking to myself...;)

Just booted back to 2.6.32 kernel Ubuntu for giggles. Ok the sound no worky, but the screenshot does, and so does the keyboard :S

So I guess the 2.6.34.999 kernel is problematic...

downloading new 2.6.35 now

---

### Post by combatwombat_nz on 2010-07-06
This kernel seems to be the winner; from
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.34-lucid/")

I installed the i386 kernel...download
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-source-2.6.34_2.6.34-020634_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-source-2.6.34_2.6.34-020634_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb)

to a new folder. Open terminal,
cd /path/to/newfolder
sudo dpkg -i *deb
You will see it run through the installation of the new packages, and update grub.
Now make sure it uses the right entry for Grub booting:
sudo nano /etc/default/grub
change the default=0 to whatever numeric entry the new kernel 2.6.34-020634 is set at (look at but don't change /boot/grub/grub.cfg)
then sudo update-grub.

Screeenshot and keyboard works, as does Audio. Graphics seem to be okay, but only time will tell in regards to stability.

---

### Post by Jpatrick408 on 2010-11-01
I have a gateway nv79 and never had the sound problems in Ubuntu that you had.  I did have the same problems with Arch Linux.  My screen went black every time I installed it.  The problem seems to be with the back lights not turning on.  If you hold a flashlight up to the screen, then you can see the picture on the screen.  I have found two work arounds (both not ideal, but they work).  

First, after waiting for Arch Linux to finish boot, simply close the lid, wait a few seconds, then open it up.  This will cue Linux to "wake up" the laptop and turn on the back lights.  Everything seems to work fine after that.

Second, use the previous work around to get the system up and running, then install a GUI (I use KDE, but this should work with Gnome as well).  Have the GUI automatically load after booting.  When I did this, the GUI automatically turned on the back lights whenever I booted the laptop.

I know this is an old thread, but I've looked around and no one seems to have this solved so I thought I would post just so others can know.

---

### Post by dsaronin on 2011-01-17
Got this same issue upon upgrade from 10.04 to 10.10 with kernel 2.6.35-24; boot process reports error with intel i915 0000:00:1f.6 failed and turns off backlight. workaround to close lid, wait, reopen does not turn on backlight when linux is restored. graphics atill being displayed but barely visible with a bright flashlight.

** UPDATE .. WORK-AROUND FOUND! **
Do this (below) in a working displayable kernel (for me: 2.6.32-27):
system > preferences > power management
"On AC Power" tab; "DISPLAY" section: "set display brightness to:" change from 100% to 85%.
then reboot to kernel 2.6.35-24 .. and the backlight is on and everything displays great!

---

