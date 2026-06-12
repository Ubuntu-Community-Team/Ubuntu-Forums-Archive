---
title: "Is this the right video driver?"
date: 2007-08-07
forum: Hardware &amp; Laptops
---

### Post by iAndrew on 2007-08-07
Hi, I got ubuntu working. Yes, finally.

And I have a Nvidia GeForce 8600 GT.

I was looking at the Nvidia Site, and in the driver downloads, I've stumbled upon 2 choices.

Choice A:
[http://www.nvidia.com/object/linux_display_ia32_100.14.11.html](http://www.nvidia.com/object/linux_display_ia32_100.14.11.html)

Choice B:
[http://www.nvidia.com/object/linux_display_amd64_100.14.11.html](http://www.nvidia.com/object/linux_display_amd64_100.14.11.html)

I was thinking Choice A, seeing how this is an **Intel Dual Core Processor**

And if so, is there another way to install it? Because the code to install it:

```
sh NVIDIA-Linux-x86-100.14.11-pkg1.run
```

This doesn't seem to work in the terminal.

---

### Post by merlinus on 2007-08-07
Try putting sudo in front of the command.

-merlin

---

### Post by koshari on 2007-08-07
is there any reason you dont want to use the compiled closed source drivers in the ubuntu repositorys?

---

### Post by iAndrew on 2007-08-07
I'm new to the whole Linux scene, but what?

@merlinus: Also it asks for my password, yet I can't type it into terminal.

---

### Post by Ub1476 on 2007-08-07
Administration>Restricted Driver Manager

Enable the video driver if there is one there..

To install manually (from the file you downloaded)

Put it at desktop

```
cd /home/yourusername/Desktop
sudo sh NVIDIA-Linux-x86-100.14.11-pkg1.run

```


For the password thing:

When it shows:
Password: 

Just type your password and click enter (the letters are hidden).

---

### Post by iAndrew on 2007-08-07
Hey ub1476, Thanks for the help.

But, I still cannot type in the password.

And there is not video driver there.

---

### Post by Ub1476 on 2007-08-07
Alright, if there's no video driver in the RDM, then I guess your good with open source. But are you sure you can't type in your password? Cause look here:

```
kasper@FeistyFawn:~$ sudo apt-get update
Password:
Hent:1 http://no.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://no.archive.ubuntu.com feisty/main Translation-nb                    
Ign http://no.archive.ubuntu.com feisty/restricted Translation-nb
Ign http://no.archive.ubuntu.com feisty/universe Translation-nb
Ign http://no.archive.ubuntu.com feisty/multiverse Translation-nb

```

As you see, no letters or **** are shown when I type/typed it.

---

### Post by iAndrew on 2007-08-07
There we go. But now an installation error. I'm so used to Windows, but I'll try my best to get used to Ubuntu.

Error log:
```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue Aug  7 02:51:38 2007

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
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '5382'
   of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing. 
       For further details, please see the section INSTALLING THE NVIDIA DRIVER
       in the README available on the Linux driver download page at
       www.nvidia.com.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

---

### Post by Ozdemon on 2007-08-07
If you are a noob like me, it's easier to use the fantastic work of gui makers.  I installed 2 x 8500GT cards today, no problems.

The automated software (Nvidia or ATI) is at:

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")
=D>

---

### Post by iAndrew on 2007-08-07
This doesn't seem to be working for me.

---

### Post by Ub1476 on 2007-08-07
Alright, looks like you need to install when not running the X server. Now I just forgot what the short-cut to that was:lolflag:

Try to type Super (windows button) + f2 or ctrl+alt+f2

When you do (if it's the correct key) you will end in a black terminal filling your hole screen. Just do the same as repeated (write it down if you don't remember) and hopefully you'll do fine.


Oh and man, don't give up upon Ubuntu. I had lots of problems too, but I got rewarded for my patience:D

---

### Post by iAndrew on 2007-08-07
Whoever said I was giving up? Linux is awesome. (So far.)

---

### Post by iAndrew on 2007-08-07
Okay, I did Ctrl + Alt + F2. It went to the terminal. I typed everything:

sudo sh NVIDIA-Linux-...etc.

I still get the X server error. On top of that, I didn't know how to return, so I had to restart my computer.

---

### Post by Ub1476 on 2007-08-07
Alright, I suggest you maker a thread in the general forum, where you ask how you can exit the X server because you need to install a Nvidia driver.

To get back I think you just have to type ctrl alt f2 again..

---

### Post by iAndrew on 2007-08-07
Okay, I exited X-server. Yet again, another error. Geez.

```
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue Aug  7 03:37:43 2007

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
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
ERROR: You do not appear to have libc header files installed on your system. 
       Please install your distribution's libc development package.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```

---

### Post by Ub1476 on 2007-08-07
Well, just follow the errors.

Go to administration>Synaptic>Search>libc6-dev (I believe that's what you need)

Click on it and install.. Then err, retry](*,)

---

### Post by iAndrew on 2007-08-07
I don't know if that helped, instead of posting the whole log, I'm just gonna post the error.

```
ERROR: Unable to find the kernel source tree for the currently running kernel. 
```

---

### Post by 3rdalbum on 2007-08-07
Why not install the linux-restricted-modules-<kernel version> [1] package from the Synaptic Package Manager program, and then go to the terminal and paste each command in:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
sudo dpkg-reconfigure xserver-xorg
```

Accept the defaults until you get to the part where it asks "Autodetect video card?". At this point, go to No. Select the "nvidia" driver from the list. Everything else can be the defaults.

Once the program has finished, restart the system and you should be running with 3D acceleration. If you just get a command-line and no graphical display (usually Xorg gives you an error message), then type:

```

sudo rm /etc/X11/xorg.conf
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf
sudo reboot

```

And you'll be back to where you started.

[1] You can find out your kernel version by typing uname -r into a terminal.

---

### Post by iAndrew on 2007-08-07
NVIDIA Graphics Card Driver? Through SPM? Really?

---

### Post by 3rdalbum on 2007-08-07
Yep! The Restricted Drivers Manager *should* do it for you, but it's a fairly new program so maybe it didn't recognise your card.

---

### Post by iAndrew on 2007-08-07
Yes. It didn't.

I'm trying to follow this guide:

[http://compiz.org/NVidia](http://compiz.org/NVidia)

But I don't seem to be doing this right.

Also, I can't select NVIDIA, unless (NV Is NVIDIA).

---

