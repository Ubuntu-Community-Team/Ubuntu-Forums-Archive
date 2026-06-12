---
title: "Blank Screen after NVidia driver install"
date: 2007-06-22
forum: Hardware &amp; Laptops
---

### Post by Collywobbles on 2007-06-22
Hi,

I have a Dell Inspiron 2560 Laptop which uses the NVidia GO 100 graphics card. Ubuntu 7.04 works fine after installation, however, it always prompts me to install the 2D/3D Nvidia drivers. Unfortunately, when I do, the laptop boots as normal until it tries to run the X interface. Then, the screen is just blank. I hear the drum notes play and I can type in my username/password so the thing is running okay - I just can't see anything!

I can boot into recovery mode okay but I don't know how to uninstall the driver. I've seen some posts on modifying the xorg.conf file but the suggestions didn't help. The main one I've tried is adding:

"UseDisplayDevice" "DFP"

to the Device Section. This didn't work though.  I ended up reinstalling Ubuntu to everything working again. Also, after running Ubuntu without choosing to install the NVidia drivers by clicking on the icon, the icon disappears after a while. Is there any way to get it back? 

Can anyone help, please!

Thanks,
Collywobbles

---

### Post by Collywobbles on 2007-06-22
bump

---

### Post by Collywobbles on 2007-06-22
Okay,

I ran the following after installing the nVidia drivers:

[B]sudo dpkg-reconfigure xserver-xorg -phigh
sudo nvidia-xconfig[/B]

I then added the line **Option "UseDisplayDevice" "DFP"**

I've had a look in the /var/log/Xorg.0.log file and it seems my flat panel is not detected correctly and it is trying to use a CRT monitor which obviously isn't connected. The messages are:

[B]No connected display devices detected; assuming 1 CRT
Unable to read EDID for display device CRT-0
Option "UseDisplayDevice" requested "DFP", but no unused DFPs are available
Option "UseDisplayDevice" "DFP" converted to ""
Unable to find any of the requested display device "" in the list of available display devices "CRT-0"
Asssigned display device: CRT-0[/B]

Does anyone have any idea how to fix this? 

Thanks for any help!
Collywobbles

---

### Post by Collywobbles on 2007-06-22
Update:

I tried changing

"UseDisplayDevice" "DFP" to "ConnectedMonitor" "DFP"

and this gives me a completely white screen on the login screen at the drum beat!

I quick look at the log shows it is forced to use the DFP but the only mode it recognises as valid is 640x480 which I think is the only mode my laptop is incapable of displaying!

These nVidia drivers really seem to be completely confused - I might try the legacy driver to see what happens with that...

---

### Post by Collywobbles on 2007-06-25
No luck yet...

I've tried nvidia-glx-legacy & nvidia-glx-new as well as the nvidia-glx drivers. None of them seem to want to work. Help!

---

### Post by Collywobbles on 2007-06-29
Okay, I give up. I also get the feeling I'm talking to myself!

Anyway, can't get it to work so I'm off to try Fedora instead...

---

### Post by foxmuldr on 2007-07-07
I'm having a similar problem.  You're not talking to yourself.  I just don't think there are too many people here in the Install forum interested in helping with display issues, at least not for Nvidia cards.

---

### Post by fredj on 2007-07-07
Usually installing the nvidia display drivers through the system - restricted drivers manager is trouble free.
Maybe the ubuntu nvidia driver doesn't cover your particular video chipset. 
The video configuration is in /etc/X11/xorg.conf and you should always back up this file before making any
changes to the video.

If you boot into recovery mode you should be able to access this file and try to undo changes or at least
you could if you had a backup of the original. Look for a file called xorg.conf~ and try using the cp command
to copy this to xorg.conf. Beyond that I can't offer any real help. In recovery mode you can look at these 
files using the vi editor.

---

### Post by fnandocc on 2007-07-21
Try this How To

[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)

Check the problems Section, and try different settings.

I'm using a Geforce Go 440. (Dell C840)
with the nvidia-glx driver from the repositories. (restricted)
This is my xorg.conf 

[http://pastey.net/71135](http://pastey.net/71135)

Good Luck

---

### Post by Man@Arms on 2007-11-26
Ubuntu was running awesome until I hit this same issue with same machine specs. I need the machine running so back to XP it is. It's a real, real  shame. Everything was running and installing perfect until I ran the update for my nvidia Geforce2Go drivers... As a last ditch effort, does anyone have anything? I am experiencing the same symptoms as mentioned previously..

---

### Post by tiaguim on 2008-01-28
After you hear the drum sound on the login screen, press "Ctrl + Alt + Backspace"
It should restart X and you'll get the display working with the nvidia drivers.
This is how I am currently booting everytime.

GL

---

