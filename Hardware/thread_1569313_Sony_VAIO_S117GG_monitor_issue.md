---
title: "Sony VAIO S117GG monitor issue"
date: 2010-09-06
forum: Hardware
---

### Post by dannykopping on 2010-09-06
Hi all!

I've got a really annoying problem - I recently bought a Sony VAIO S117GG and the first thing I tried to do was install Ubuntu 10.04 on it. To my horror, it seems as though Ubuntu doesn't know how to output to my laptop monitor once it's finished with the grub loader, and will only output to an external display.
I've tried all the combinations - with external display, without, installing NVidia drivers, slaughtering goats... nothing works!!

Can anyone help?
Thanks

Danny

PS: it's an NVidia 310M 512Mb graphics card if that helps?

---

### Post by dannykopping on 2010-09-24
Hi everyone

I'm at the end of my tether :(
I recently bought a Sony VAIO VPCS117GG laptop and - to my absolute dismay - not a single Linux distribution correctly manages to handle my laptop screen and an external monitor.

The graphics card is a NVidia GeForce 310M. I've installed the drivers several times and have tried looking at every link I could find about configuring X to work with my monitors. I've been at this for 2 days now and I'm getting very disheartened! If there's an article on UbuntuForums about this, I've tried it and I've failed.

PLEASE can someone help me? I'm very close to just giving up and buying support from Canonical but the smallest support package I can find from them is for a year and is $140. Might that be the only way?

Thanks!!

---

### Post by Iowan on 2010-09-27
Threads merged.

---

### Post by gordintoronto on 2010-09-27
It might be helpful if you stuck to facts and skipped the emotion.

I *think* it works OK with an external monitor. Did you run Preferences/Hardware Drivers? Did it offer an nVidia driver, and did you "activate" it?

What is the key-combination to cycle through "built-in," "external," "both"? Most laptops have such a combination.

---

### Post by dannykopping on 2010-10-03
Hi

Yes, I've installed all the correct drivers and i've edited the xorg.conf file with numerous different combinations of values picked from around the web, but no success as yet.

---

### Post by realzippy on 2010-10-03
...tested to feed an edid.bin file?:

[http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9323377&postcount=1](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9323377&postcount=1)

---

### Post by dannykopping on 2010-10-03
Indeed I did... I actually found a similar post [here]("http://ubuntuforums.org/showthread.php?t=1392766&highlight=vaio+monitor")

That fixes the laptop's monitor issue, but I can't get Ubuntu to recognize any attached monitors (VGA or HDMI). I've run "xrandr" and it only brings up my laptop's monitor and nothing else.

---

### Post by realzippy on 2010-10-03
...any clue in the Log.files?
Plug in the external monitor and run
```
sudo nvidia-bug-report.sh
```
and post the file (it is created in your user's directory)...

---

### Post by dannykopping on 2010-10-03
Here you go! Thanks

---

### Post by realzippy on 2010-10-03
...it is maverick you use.Did not know,no idea if problem might be related to new xserver etc.
Your current xorg.conf is pretty vanilla except the edid lines:
```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier "Device0"
    Driver "nvidia"
    VendorName "NVIDIA Corporation"
    Option "ConnectedMonitor" "DFP-0"
    Option "CustomEDID" "DFP-0:/etc/X11/sonycw.bin"
EndSection

Section "ServerFlags"
    Option    "IgnoreABI"    "True"
EndSection


```
Would like to see the xorg.conf 
made by nvidia -xconfig,with external monitor connected and powered on.
Run
```
sudo nvidia-xconfig
```
Your old file is automatically back-upped to /etc/X11/xorg.conf.backup
When done this,open the new created xorg.conf file 
```
gedit /etc/X11/xorg.conf
```
and post it please.hope there will be a monitor section (or 2)..then restore your old xorg.conf:
```
sudo mv /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

### Post by dannykopping on 2010-10-03
I've already tried that - it still does not pick up the additional monitors. It's not a problem isolated to Maverick - i've tried to get it working on Linux Mint 9, Fedora 13, Ubuntu 10.04 and now 10.10. I think it's got less to do with X server and more to do with Sony making weird laptops.

Can you think of anything else that it might be?

---

### Post by realzippy on 2010-10-03
The cable...but you might have tried this,also HDMI does not work  ....
Any laptop specific shortcut to switch monitor-out on? (sorry,not kidding..)
You run the 256.xx,could try the 260.xx nvidia-driver...

Does a liveCD run (without nvidia)?Does xrandr also see no external output in this case?

---

### Post by dannykopping on 2010-10-03
> **realzippy said:**
> The cable...but you might have tried this,also HDMI does not work  ....
Correct... i've tried with both VGA and HDMI which are functional with Windows
> **realzippy said:**
> Any laptop specific shortcut to switch monitor-out on? (sorry,not kidding..)
Not sure what you mean by this... Are you asking whether I'm using a shortcut to try show the extra monitor or whether there is such a key?
> **realzippy said:**
> You run the 256.xx,could try the 260.xx nvidia-driver...
I've tried all the NVidia drivers going back about 5 versions, none work...

> **realzippy said:**
> Does a liveCD run (without nvidia)?Does xrandr also see no external output in this case?
Unfortunately not...

---

### Post by skew on 2010-10-05
I'm having the same issues. Since upgrading to the most recent Nvidia drivers, only my external monitor works. Nothing on the laptop screen.
If I disconnect the external monitor and reboot the last thing I see on my laptop screen is the purple Ubuntu splash page then a corrupted screen
 display.  If i remove the 3d Nvidia driver everything returns to normal with the exception of my mood as I would like to maintain the 3d capability
the card it designed for. :-(

  I will be very interested to see if anyone can come up with a solution.
Not being able to use a portable computer w/o a working display is a big problem, to say the least.

Sony VAIO VPCF121FD
GeForce 310m
Nvidia driver 195.36.24
Lucid

---

### Post by Abdurahim Zuvaydov on 2011-09-07
> **realzippy said:**
> ...any clue in the Log.files?
Plug in the external monitor and run
```
sudo nvidia-bug-report.sh
```and post the file (it is created in your user's directory)...



Hey there, I have the same problem, and I can't fix it....I typed the code which you wrote.............and it write nvidia-bug-report.sh will now collect information about your
system and create the file 'nvidia-bug-report.log.gz' in the current
directory.  It may take several seconds to run.  In some
cases, it may hang trying to capture data generated dynamically
by the Linux kernel and/or the NVIDIA kernel module.  While
the bug report log file will be incomplete if this happens, it
may still contain enough data to diagnose your problem.

Please include the 'nvidia-bug-report.log.gz' log file when reporting
your bug via the nV News NVIDIA Linux forum (see [www.nvnews.net](www.nvnews.net))
or by sending email to 'linux-bugs@nvidia.com'.

Running nvidia-bug-report.sh... complete.






BUT IT DOESN'T WORK..............i CAN'T ADJUST THE BRIGHTNESS

---

