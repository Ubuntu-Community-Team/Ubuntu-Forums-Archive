---
title: "Stuck at Refresh Rate 60 Hz"
date: 2009-11-22
forum: Hardware
---

### Post by bit mad on 2009-11-22
The Display settings only has 60 in the list, nothing else. It's way too flickery for me, it's usually 75 in Windows.

I'm using a Dell, and in Windows there's an Intel control app for the "Intel(R) G33/G31 Express Chipset Family" as it appears in Device Manager... Display adapters.

My Ubuntu is booted up via a persistent USB stick (2GB) installation of 9.04, set up using LiLi.

It appears (from the date/time stamp) that the etc/x11/xorg.conf is re-written from the bootup Hardware Detection phase each time, so any changes made there get lost.

Is there any solution, or do I give up? I can't even figure out how to get drivers onto Linux - the dialog says it's searching but none exist on my system ... and it doesn't provide a way to lookup on the net, at least not that I can see. :?

If this is "Linux is ready for the desktop" I have to say at the moment it doesn't feel like it :D   ](*,)  but I accept that I'm not running this in a normal way and I'm hoping that The Community will have an answer for me! Thanks

---

### Post by m3741 on 2009-11-22
Are you running a CRT or LCD monitor? If you're running an LCD, 60Hz is the default refresh rate and I don't think you can/should change it.

---

### Post by bit mad on 2009-11-23
Thanks, but it's a good ol'  MultiSync CRT ... I'm happy with the pic and haven't felt the need to upgrade yet :D

---

### Post by bit mad on 2009-11-23
... but at least the Ubuntu (and Linux Mint) setting of 1152x864 is better than Fedora 12 on the USB key via LiLi - that only gave me 800x600 and 640x480 to choose from, with 56 or 60 Hz :)

I would be trying OpenSUSE and Mandriva next, just for shots and goggles, but LiLi doesn't work with those distros :(

---

### Post by bit mad on 2009-11-24
**OpenSuse**
I tried openSUSE-11.2-GNOME-LiveCD-i686.iso, and the md5 was ok. I used the recommended Win32DiskImager, and it all looked promising with a nice bootup... but it got stuck. At the login screen it all totally froze. I tried following some hairy instructions
[I][http://lizards.opensuse.org/2008/05/31/making-opensuse-110-liveusb-the-easiest-and-fastest-way/](http://lizards.opensuse.org/2008/05/31/making-opensuse-110-liveusb-the-easiest-and-fastest-way/)
and vavai.net/2009/01/02/how-to-make-opensuse-111-liveusb/[/I]
using SysLinux, an "initrdud" version of InitRd designed to work with USB, and even using the shortcut method of *UnetBootin-windows-377* but I couldn't get it to work.

I don't the how the heck a *mount -o loop openSUSE-11.0-RC1-KDE4-LiveCD-i386.iso liveiso/* command is supposed to work in MS-DOS, and the config files they said to rename? Couldn't find them anywhere! Still, at least I've learnt a thing or two, and now I know that an ISO can be opened like a ZIP file :)

Overnight I've downloaded Debian-live-502, Ubuntu 9.10, and Mandriva One, along with Fedora's *Liveusb-creator.exe, *so my quest continues. *(update : debian-live-502-i386-gnome-desktop.img doesn't work with LiLi or anything else I've tried, and I ended up with a 700MB USB key which meant that I had to track down and run an HP Reformat utility to get it back to 2GB again)*

**All I want is a USB key persistent Linux that will give me 1024x768 75Hz** on a Dell with Intel Graphics... to play with Kdenlive and OpenShot... **who'd have thought it would be so hard?** :rolleyes:

---

### Post by bit mad on 2009-11-24
**Ubuntu 9.10** (ubuntu-9.10-desktop-i386.iso)

via "LiLi" : worse than 9.04, now stuck on 800x600 60Hz

via "LiveUSB Creator" (seems to put Wubi on the USB key) : despite setting a persistence, I got a different boot experience that looked like a CD boot, no evident persistence option, just "Try Ubuntu without any changes". I changed keyboard and wallpaper, but it was forgotten by the next time in.

Unless there's another way to try 9.10 on USB with persistence, I shall move on to another distro for my next thrilling installment.

Edit : tried with u910/USB-Installer-U910.exe from
[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)  and got a persistent install working, but still on 800x600-60

---

### Post by HavocXphere on 2009-11-24
There are two ways to fix that (which I know of). 1. Force refresh rate via xorg 2. Install correct driver.

In our case, it sounds like you are missing a video driver so it defaults to something safe (800.600 @60). Once you've got the correct driver more options should be available.

Not sure how the video driver setup works on a persistent USB though.

"G33/G31 Express Chipset Family" is not the video card. You'll have to do some more research to identify the video card and then search for threads on how to install it. I've got zero experience with intel video so I can't provide more detailed guidance.

---

### Post by bit mad on 2009-11-24
Thanks. The PC is a Dell Vostro 200, but I don't know how to find out anything more than that. Windows device manager doesn't really help.

I tried fiddling about with xrandr in the terminal, but it just ignored everything I tried, or said the resolution I was trying wasn't in its list.

I've no idea how to get the right drivers for Linux, or how to install them :(

Cheers anyway!

---

### Post by bit mad on 2009-11-24
**Mandriva One**  (mandriva-linux-one-2010.0-GNOME-europe-americas-cdrom-i586.iso)

via : liveusb-creator.exe - I got to choose 1024x768 via F3 at the first splash screen, but with that or the default 800x600 it just got stuck at the main splash screen with a circle of dashes whizzing around... no USB key activity... keyboard frozen (Num Lock or Caps Lock not working)... so after a minute or two I gave up.

via : UnetBootin - straight to the whizzing around and freeze

via : Win32DiskImager.exe - got in OK .. and **managed 1024x768 at 70.1Hz!** - thanks to the "Configure your system" options... hardware... Intel 810 I think it was.  Why can't Ubuntu have that?
I don't like the logout/shutdown being on the system menu though :)

I just need a persistent version of the Mandriva  USB key then.... but doesn't seem to be possible, because they want to sell such a thing instead. Not exactly the kind of freedom I thought Linux stood for!

---

### Post by bit mad on 2009-11-24
Is there anything I can do in Mandriva *(where 1024x768-70 works)* that I can use to replicate that mode in Ubuntu? Can I run something in the Mandriva terminal and use what it reports  to achieve the same mode in 9.10? Or the LTS ver?
thanks...

---

### Post by bit mad on 2009-11-25
Fixed!
Although there wasn't an etc/x11/xorg.conf file, I created one as follows (in entirety).

Open a terminal, run this to bring up an editor with privileges to save in the restricted folder :
```

gksudo gedit /etc/X11/xorg.conf

```... then paste this in and save :

```
Section "Monitor" 
        Identifier      "Configured Monitor" 
        HorizSync       31-65 
        VertRefresh     50-120 
EndSection 
 
Section "Screen" 
        Identifier      "Default Screen" 
        Monitor         "Configured Monitor" 
        Device          "Configured Video Device" 
        DefaultDepth    24 
             SubSection      "Display" 
                Viewport        0 0 
                Depth           24 
        Modes      "1152x864" "1024x768" 
             EndSubSection 
EndSection

```I can now choose 1152x864 @70  or  1024x768 at 75, and it remembers it for next time.

Yay :D

---

### Post by m3741 on 2009-12-02
Sorry I dropped out there after the first post, but I'm glad you got your problem fixed! If you don't mind, would you mark this thread as solved? Thanks!

---

### Post by utux_utux on 2010-03-05
> **bit mad said:**
> Fixed!
Although there wasn't an etc/x11/xorg.conf file, I created one as follows (in entirety).

Open a terminal, run this to bring up an editor with privileges to save in the restricted folder :
```

gksudo gedit /etc/X11/xorg.conf

```... then paste this in and save :

```
Section "Monitor" 
        Identifier      "Configured Monitor" 
        HorizSync       31-65 
        VertRefresh     50-120 
EndSection 
 
Section "Screen" 
        Identifier      "Default Screen" 
        Monitor         "Configured Monitor" 
        Device          "Configured Video Device" 
        DefaultDepth    24 
             SubSection      "Display" 
                Viewport        0 0 
                Depth           24 
        Modes      "1152x864" "1024x768" 
             EndSubSection 
EndSection

```I can now choose 1152x864 @70  or  1024x768 at 75, and it remembers it for next time.

Yay :D


[SIZE=4][COLOR=Blue]dear bit mad....

you're my savior..... yay [/COLOR][/SIZE]:KS:KS:KS:KS:KS

---

