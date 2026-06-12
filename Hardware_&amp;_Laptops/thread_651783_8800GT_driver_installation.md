---
title: "8800GT driver installation"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by wripley on 2007-12-27
hey, i'm using Ubuntu Studios, and i was wondering how the bloody hell i should go about installing the new driver 169.07 on my ubuntu?  currently, i can't even get a screen, it just goes black and does nothing, (PS i am an old fedora user that lost interest in the "bleeding edge" nonesense and am looking for a more stable product) anybody able to help?

---

### Post by wripley on 2007-12-28
i just tried dropping my 7600 GT back in , it worked with US 7.1 a few months ago, but i couldn't get a mobo splash screen or anything with that, so i'm back to square -1.  is there a way to download it and then install it from the command line?

---

### Post by tommcd on 2007-12-28
Are you able to boot to a terminal? I have never used ubuntu studio, just ubuntu. For such a new nvidia card you will likely need the latest driver from nvidia. If you can boot to a terminal, here is how to install the latest nvidia driver on ubuntu. If you have the nvidia driver from the ubuntu repos installed you will need to remove that first, then install the driver from nvidia this way
[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)

---

### Post by wripley on 2007-12-28
i finally got it to boot up with my 7600 GT dropped back in out of my brothers box, and i was wondering if i could download and install the driver for the 8800GT with the 7600 in it, power down, replace the 8800, and then reboot?

---

### Post by wripley on 2007-12-28
i get a "screw yourself' message from the driver installer and then sent to this readout

nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Fri Dec 28 12:57:36 2007

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
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  compat32 install chroot : (not specified)
  compat32 install prefix : (not specified)
  compat32 install libdir : (not specified)
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
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '5574'
   of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       [www.nvidia.com](www.nvidia.com).
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

what should i do, besides shoot myself and my PC?

---

### Post by kaytaro on 2007-12-28
have you tried Envy? It worked really well for me and installing the new drivers, for a Ubuntu nub. Here is the link. 

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

I couldn't get them to install manually myself either >.< , But this worked like a charm!

---

### Post by jespdj on 2007-12-28
> **wripley said:**
> i get a "screw yourself' message from the driver installer and then sent to this readout

...

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '5574'
   of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       [www.nvidia.com](www.nvidia.com).
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).

what should i do, besides shoot myself and my PC?
It's not a 'screw yourself' message. Instead of trying to shoot yourself and your PC, you should stay calm and read the message, because it tells you exactly what the problem is: you are running X windows, and to install this, X windows must not be running. It even suggests looking in the README file for a solution.

Go to a terminal window by pressing Ctrl + Alt + F1 and login. Then type
```
ps -ef | grep gdm
```
The output will look something like this:
```
root      6282     1  0 23:32 ?        00:00:00 /usr/sbin/gdm
root      6285  6282  0 23:32 ?        00:00:00 /usr/sbin/gdm
root      6289  6285  8 23:32 tty7     00:00:18 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth vt7
jesper    6938  6918  0 23:36 pts/0    00:00:00 grep gdm
```
Look at the first line. The number 6282 is the process number of the GDM (graphical login) that's running. You need to stop GDM, by doing
```
sudo kill <number>
```
In this case, the number is 6282; you'll have to see on your system what the process number is.

When GDM is killed, run the nVidia installer again from the text screen.

---

### Post by jespdj on 2007-12-28
Also carefully read the [installation instructions]("http://us.download.nvidia.com/XFree86/Linux-x86/169.07/README/chapter-04.html").

---

### Post by wripley on 2007-12-29
i read the installation instructions, thats how i knew i needed the x server off.  however it was definately telling me to go screw myself, i got that message long before it closed out the last time, which i couldn't figure out.

---

### Post by wripley on 2007-12-29
it told me it didn't have  a compiled kernal and that it would make one, and then it said "your kernal source tree is effed in the a, download the RPM'' how do i do this?

---

### Post by jespdj on 2007-12-29
Ok, I just spent time installing the nVidia driver version 169.07 myself, and also had some trouble with it.

I didn't get an error message about the kernel sources or headers, the kernel module was built just fine on my system. Maybe this will help with that problem: make sure you have a C compiler and the kernel header files installed:
```
sudo apt-get install build-essential linux-headers-generic
```
I hope that will solve your problem.

I had a problem that after installing the driver it would fail to start properly. In /var/log/Xorg.0.log.old I found an error message saying something like "failed to initialize kernel module". With some searching I found the solution: the "nv" module needs to be disabled. You do this by editing the file **/etc/default/linux-restricted-modules-common**. Add "nv" to the line with DISABLED_MODULES. On my system it now looks like:
```
DISABLED_MODULES="nv"
```
After rebooting, it works! :)

I hope this is useful to you.

---

### Post by mellowd on 2007-12-29
I agree with kaytaro. Download envy and it will do everything automatically for you

---

### Post by kaytaro on 2007-12-30
woot a leet forum poster agreed with me must be my lucky day! But really Envy makes it super easy, even my wife could install it that way. gl mate!

---

### Post by pwc on 2008-01-01
I used Envy also, had to use the manual install. Seems to be working ok now, I installed 2-3 days ago. One thing I don't like is the fan runs all the time, in XP(duel boot) it does not run at all( haven't played anything heavy yet). I saw reference to this in post a couple of weeks ago but no solution. Anybody else notice this? or know of a solution.

pwc

---

### Post by GeoPirate on 2008-01-03
I have also noticed the fan issue.  It's noticable because the rest of my system is almost silent.  Would be nice to get a fix for this.

---

### Post by Fred_E _krugar on 2008-01-03
Sorry for the hi-jack but I cant even install Ubuntu with my 8800gt how are you guys doing it?? The only linux I can install is Fedora 8. What can I do to get  my Ubuntu back??

---

### Post by tommcd on 2008-01-03
> **Fred_E _krugar said:**
> Sorry for the hi-jack but I cant even install Ubuntu with my 8800gt how are you guys doing it?? The only linux I can install is Fedora 8. What can I do to get  my Ubuntu back??

Try the alternate install CD. If the live CD has a problem with your graphics card the alternate CD may allow you to install ubuntu since it is text based. If then you are unable to startx, you could use the vga or vesa driver until you can get the nvidia driver installed according to this thread.

---

