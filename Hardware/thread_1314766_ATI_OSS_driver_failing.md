---
title: "ATI OSS driver failing"
date: 2009-11-04
forum: Hardware
---

### Post by shocksafe on 2009-11-04
I've just installed an old ATI radeon 9600 and a fresh install of mythbuntu 9.10.
I'm trying to get the ati OSS drivers working but so far all attempts have failed.

I've followed this [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) to the letter but no matter if I just delete my xorg.conf or follow the instructions to create a new one when I reboot as x is starting it fails and the screen goes black.

I tried to look at /var/log/Xorg.0,log but its blank (after restarting in recovery mode)

I apt-get remove --purge fglrx* and even synaptic shows no installed fglrx packages when I search there.

glxinfo |grep vendor returns SGI.

Not sure what other info to post so I'll wait for a reply and keep trying in the mean time.

Cheers

---

### Post by shocksafe on 2009-11-04
_Update_

I tried again and this time have it working but every time I log in (gui login) the xserver restarts and takes me back to the login screen.

My xorg.conf is now exactly as provided in the link above except I commented out the keyboard and mouse lines in server layout as I was getting errors for those lines.

Cheers

---

### Post by edin9 on 2009-11-04
Hold on, did you try to install FLGRX on Karmic?

---

### Post by shocksafe on 2009-11-04
I did yes.
I didn't realise my card was no longer supported.
As I said though I did apt-get remove --purge fglrx* xorg-driver-fglrx.

is there more I need to do?

Cheers

---

### Post by edin9 on 2009-11-04
Did you install the driver manually with a driver from ATi's site?

---

### Post by shocksafe on 2009-11-04
I did try that but it failed.
ie I tried to install the legacy driver but it complained about version not compatable or something (presumeing xorg version from what I read about it)

Cheers

---

### Post by edin9 on 2009-11-04
Get to the CLi and enter the commands _**in this order**_! ```
sudo bash
``` ```
cd /usr/share/ati
``` ```
sh ./fglrx-uninstall.sh
```

---

### Post by shocksafe on 2009-11-04
/usr/share/ati does not exist

The ati driver from there site seemed to fail as it was unpacking. It then said "removing ........." can't remember the name but I guess it unpacked the files and then removed them all.


BTW thanks for helping me out here.

---

### Post by edin9 on 2009-11-04
> **shocksafe said:**
> /usr/share/ati does not exist

The ati driver from there site seemed to fail as it was unpacking. It then said &quot;removing .........&quot; can't remember the name but I guess it unpacked the files and then removed them all.


BTW thanks for helping me out here.

Ugh yeah I couldn't remember the exact command so I googled it. The path is different from what it used to be. Sorry, it's been a while since I used ATi.

---

### Post by edin9 on 2009-11-04
Try; ```
sudo bash
``` ```
cd /usr/share/fglrx
``` ```
sh ./fglrx-uninstall.sh
```

---

### Post by shocksafe on 2009-11-04
I just googled and found that after your last post but /usr/share/fglrx doesn't exist either.
/shrug

---

### Post by edin9 on 2009-11-04
> **shocksafe said:**
> I just googled and found that after your last post but /usr/share/fglrx doesn't exist either.
/shrug

Mhm. What was the driver version you installed?

---

### Post by shocksafe on 2009-11-04
9.3 which is the legacy driver.

---

### Post by edin9 on 2009-11-04
> **shocksafe said:**
> 9.3 which is the legacy driver.

Give me a minute.

---

### Post by edin9 on 2009-11-04
Ok it looks like your going to need to reinstall and BUY NVIDIA!! Sorry :(

---

### Post by shocksafe on 2009-11-04
googled and found a couple people with same issue.
[http://ubuntuforums.org/showthread.php?p=8228849](http://ubuntuforums.org/showthread.php?p=8228849)
and
[http://newyork.ubuntuforums.org/showthread.php?t=1309603](http://newyork.ubuntuforums.org/showthread.php?t=1309603)

Tried all of that (the displays.xml didn't exist, renaming ~/.config and ~/.cache didn't help either)
](*,)](*,)

---

### Post by shocksafe on 2009-11-04
LOL can't disagree with you atm.
I might try to reinstall (nothing to lose it's a fresh install anyway) and try again without the whole ati proprietry driver thing.

Cheers again for having a go and helping me out.

---

### Post by edin9 on 2009-11-04
> **shocksafe said:**
> LOL can't disagree with you atm.
I might try to reinstall (nothing to lose it's a fresh install anyway) and try again without the whole ati proprietry driver thing.

Cheers again for having a go and helping me out.

No problem man. Sorry it took so long but I had to install Adobe Reader to read the ATi driver PDF, but installing it crashed Firefox, and then the mouse froze. You've got to love the craptasticness of Vista.

---

### Post by shocksafe on 2009-11-05
:D:D:D
Ok got it working, Did a reinstall, plugged in a newer monitor (not sure if that helped) and followed the steps in the link I posted earlier and it's all good.

Next issue is I can't get tv out (S-Video) to work. I get a few squiggles and then it goes blue with the config the way it is below ie the force tv bits commented.
The TV is a crt Panasonic Quintrix. Been trying to find out the resolutions and vsync etc but no luck yet.

Any ideas how to get tv out working>?

Heres my xorg.conf

```

Section "Device"
        Identifier      "Radeon 9600"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
    Option          "BusType" "PCI"
        Option          "AGPMode" "1"
    Option         "TVStandard" "pal"
#    Option        "ForceTVOut" "true"
#    Option        "ForceMonitors" "tv"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-60
        VertRefresh     50-100
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 9600"
        Monitor         "Generic Monitor"
        DefaultDepth    24
    Virtual         1024 768
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600"
        EndSubSection
EndSection

```

---

### Post by shocksafe on 2009-11-05
Wow this has been a PITA. :p

Now have TV out working by doing the following

xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600
xvattr -a XV_CRTC -v 1

I added to my xrog.conf as detailed here
[http://wiki.x.org/wiki/radeonTV](http://wiki.x.org/wiki/radeonTV)

but it still didn't work until I installed xvattr and ran the command above.
I still have to run xrandr --output S-video --mode 800x600 each time I reboot/restart x. I guess I'll just put that in a script. 

Problem now is to resize the output to the tv. I only get about 3/4 of the screen in the viewable tv area. Anyone got any ideas how to fix this?

The thing is also, looking through the logs, without forceing tv output, it shows s-video not detecting a monitor and shows it disabled. Why is this when with the vesa driver or before X even starts in boot up the tv works perfectly. Display is nice and the right size. As X starts and the ati driver is loaded it shuts down the tv.

Then I run xrandr as above and it displays but the resolution is all wrong as I stated above. Is this an issue that's hard to solve with these drivers? or are some people (with specific cards) just unlucky? I read some people haveing no issues and others haveing issues for the last few years with these drivers.

Anyway my xorg.conf now looks like this

> 
Section "Device"
        Identifier      "Radeon 9600"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option          "BusType" "PCI"
        Option          "AGPMode" "1"
        Option          "TVDACLoadDetect" "TRUE"
        Option          "monitor-S-video" "TV-monitor"
        Option          "TVStandard" "pal"
        Option          "ForceTVOut" "true"
        Option          "ForceMonitors" "tv"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-60
        VertRefresh     50-100
        Option          "PreferredMode"  "800x600"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 9600"
        Monitor         "Generic Monitor"
        DefaultDepth    24
#       Virtual         1024 768
        SubSection "Display"
                Depth           24
                Modes           "800x600"
        EndSubSection
EndSection

Cheers

---

### Post by shocksafe on 2009-11-05
OK got the tv picture resized by adding a modeline. I used the calculator located here -
[http://www.arachnoid.com/modelines/index.html](http://www.arachnoid.com/modelines/index.html)

Only trouble left now is that the picture is about 15mm to far to the right (and I'm wasteing my life away sorting this out).
I tried adjusting the HSyncEnd and HSyncStart by 8's as described at the bottom of the above page but it only moves the picture on my monitor and not on the tv.

Anyone got any ideas on this?

And if anyone else reads this with the same problem (if I don't get some input in the mean time) I expect I'll have this running perfectly by 2017. message me then. :p

Edit: Forgot to mention I found some details on my tv and it mentions 640x480 @ 60hz interlaced (seems odd but) so I set my monitor to the 640x480 modeline I got above which is -

Modeline "640x480_60.00" 23.86 640 656 720 800 480 481 484 497 -HSync +Vsync

I still run xrandr the same though ie. xrandr --output S-video --mode 800x600

Man this stuffs confusing.


Cheers

---

### Post by shocksafe on 2009-11-06
Just a quick update.

Found out that if I unplug the vga I no longer have to manually (or I wrote a script to do it)

xrandr --output S-video --mode 800x600

at every boot. It just automagically outputs to the tv. Go figure.

Still can't manage to move the picture over though. I'm thinking I may be able to live a 15mm black gap down the left side but I'll keep trying for a bit longer until I get bored.

Cheers

---

