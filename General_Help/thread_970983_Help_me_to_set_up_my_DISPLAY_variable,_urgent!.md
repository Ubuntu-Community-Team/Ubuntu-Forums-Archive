---
title: "Help me to set up my DISPLAY variable, urgent!"
date: 2008-11-04
forum: General Help
---

### Post by agasamapetilon on 2008-11-04
Hi mates, I would like to know how to set up my display variable. I've tried more than once and got nothing. Actually I echo $DISPLAY and shows nothing. 

I have installed xdebconfigurator and this is what shows:
```

Detected Xorg server
VIDEO CARD: Xdebconfigurator Card
VIDEO CARD DEVICE: 
VIDEO CARD VENDOR: 
VIDEO DRIVER: i810
VIDEO DRIVER SRC: discover
VIDEO MEMORY: 
POSSIBLE XSERVER: xorg
XSERVER 3: 
XSERVER 4: xfree86
DEBIAN PACKAGE: xserver-xorg
MOUSE DEVICE SRC: hwinfo
MOUSE DEVICE: /dev/input/mice
MOUSE PROTOCOL: ImPS/2
MOUSE WHEEL: 1
KEYBOARD RULES: xorg
MONITOR: Xdebconfigurator Monitor
MONITOR ID: 
SUGGESTED METHOD: Simple
MONITOR SIZE: 15 inches (380 mm)
MONITOR MODES: 1280x800, 1024x768, 1024x600, 800x600, 640x480
MONITOR MODES SRC: hwinfo
MONITOR MODE: 1024x768 @ 70Hz
MONITOR MODE SRC: default
MONITOR DEFAULT DEPTH: 16

```

This is my main configuration using geekbench:
[http://browse.geekbench.ca/geekbench2/view?id=86096]("http://browse.geekbench.ca/geekbench2/view?id=86096")

I'm a bit desperate, please help me guys!
EDIT: I forgot, my laptop model is VGN-N250E (VAIO)

---

### Post by Coreigh on 2008-11-04
Is the a special setting you are trying to achieve? Or is it not working at all? If it is working but not the right resolution/size you can adjust that via System >> Preferences >> Screen Resolution.

If you have no X (no graphical display) you can try the install script from the command line.

This is the automated script that runs during install
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

In older versions (before 8.x) I was able to copy the default setting (xorg.conf) from a LiveCD session, but I think the current setup does configuration on the fly at start-up.

---

### Post by bodhi.zazen on 2008-11-04
Your display is normally set when you start an X session.

If you need to set it to something else :

```
DISPLAY=0:0
```

Or what have you.

If you are connecting over ssh, use the -X flag (and make sure the server is forwarding X)

ssh -X user@server

---

### Post by agasamapetilon on 2008-11-04
Thanks for your quick responses guys! Actually I want to install a program that needs the X server to be running or the display variable set properly but I really got no idea on how to do that. I tried DISPLAY=0:0 and nothing happens actually.

This is the error I got:
```
root@laptop:~# wineprefixcreate --prefix .wine_Esword
Note: wineprefixcreate is deprecated and shouldn't be needed anymore.
      WINEPREFIX creation and updates now happen automatically when needed.

Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:ole:apartment_createwindowifneeded CreateWindow failed with error 1114
err:ole:apartment_createwindowifneeded CreateWindow failed with error 1114
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:ole:apartment_createwindowifneeded CreateWindow failed with error 1114
err:ole:apartment_createwindowifneeded CreateWindow failed with error -536870654
err:ole:apartment_createwindowifneeded CreateWindow failed with error -536870654
err:ole:apartment_createwindowifneeded CreateWindow failed with error -536870654
err:ole:apartment_createwindowifneeded CreateWindow failed with error 0
fixme:iphlpapi:NotifyAddrChange (Handle 0x7dc889f8, overlapped 0x7dc889dc): stub
fixme:shell:DllCanUnloadNow stub
err:wgl:process_attach X11DRV or GDI32 not loaded. Cannot create default context.
wine: configuration in '/root/.wine_Esword' has been updated.

```

I tried also to run xclock & and the same:
```
root@laptop:~# xclock &
[1] 10081
root@laptop:~# Error: Can't open display: 

[1]+  Exit 1                  xclock

```

Therefore I cannot install the program I want and its becoming frustrating, the program I wish to have via WINE is e-Sword, here are the steps I am following:
[http://ubuntuforums.org/showthread.php?t=404042]("http://ubuntuforums.org/showthread.php?t=404042")

I appreciate your help mates!

---

### Post by bodhi.zazen on 2008-11-04
I do not understand what you are doing.

First, are you running X ?

Second, why are you running as root ? Try xeyes as you user or gksu xeyes.

then use sudo , or become root with sudo -s

---

### Post by agasamapetilon on 2008-11-04
Thanks!

I got the problem. Yes I am running X. I could run the xclock command as my personal user but couldn't do the same when becoming root. I was searching the web and find that the environment changes from one user to another.

Indeed, when typing sudo -s I could run the same command (xclock) without any trouble. I take a look to the man pages for sudo and got this:

```

-s  The -s (shell) option runs the shell specified by the SHELL envi&#8208;
           ronment variable if it is set or the shell as specified in
           passwd(5).

```

The command I was trying to execute needs root permissions. Reason I was running it that way.

Now i got no more trouble, I appreciate your comments for this post! I will thank you, surely!

---

