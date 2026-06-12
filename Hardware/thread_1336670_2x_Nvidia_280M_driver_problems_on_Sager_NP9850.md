---
title: "2x Nvidia 280M driver problems on Sager NP9850"
date: 2009-11-24
forum: Hardware
---

### Post by Troop116rules on 2009-11-24
This laptop's bios is officially messed up. They have the 1.00.00 version of the Phoenix bios, with no virtualization, OC, or Nvidia card settings support.

When I first tried to install drivers for my two 280Ms, it worked perfectly on Ubuntu 9.04. Had Sli running and everything. But, then I started trying out different boot loaders (a lot) Eventually, I had to wipe both hard drives, because I was messing with stuff I shouldn't have, plus, along the way I changed some Bios settings (I believe only the Boot device order.)

Now, all I get is a black screen on boot of 9.10, and a bunch of X errors saying it can't find the monitor in versions of Ubuntu below and equal to 9.04. I've tried multiple versions of the drivers, too. 173, 183, 185, 190. None prevailed.I also tried out Kubuntu 9.10.

Man, I'm always the one to get errors that Google doesn't have the answer to. lol.

---

### Post by Troop116rules on 2009-12-21
bump?

---

### Post by Indymaynard on 2009-12-22
I'm glad that I'm not the only one. I'll tell you that I am interested in the answer to this one. Ubuntu finds the make of the video cards, but it doesn't recognize the monitor. I'll try to figure it out as well. Hopefully, we can find out the answer. This computer is so amazing, I can only imagine how wonderful it would be with Ubuntu running on it.

---

### Post by Troop116rules on 2010-01-11
I'm glad I'm not the only one wanting Linux on this beast as well!

I'm getting closer. I believe it has to do with the Xorg configuration, most likely has to do with Sli.

Someone at another IRC channel (FlightGear, user Brannon or something like that) new a bit about Nvidia cards and Linux. He told me to look up the device location.

Nvidia device Properties in Device Manager (Windows) showed "Location Information" as:
PCI bus 2, device 0, function 0 (Card a)
PCI bus 3, device 0, function 0 (Card b)

The guy continued, and said that I needed to add one of the card location numbers to the Xorg conf, to state the primary card, which is required for Sli to work.

Lines to add under line, *Section "Device"*, for Nvidia.
```
BusID "PCI:2:0:0"
```

Only do this for one card, he said, as the other should be detected automatically.


The reason I am saying "should" is because I haven't tried it myself, yet. Honestly, after 3 months of trying to get this to work, I'm kind of hesitant that it will work.

On a side-note, I thought this would be a good idea to add to the Xorg.conf under "Screen" section, at the end:
```
Option         "SLI" "on"
```


Good Luck!!

---

### Post by Indymaynard on 2010-01-15
[SIZE=2]I did this already, but I can't seem to get the native driver to work. I would use nouveau if 3d acceleration worked for it, but I can't justify wasting the power of this machine. It's so impressive with (looks over shoulder)[/SIZE] [FONT=Arial][SIZE=1]Seven[FONT=Verdana][SIZE=2] that I can't wait to see how compiz and some OpenGL 64-bit games run on it. It gives me the shivers to think about it. Any geniuses out there to help?[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by Troop116rules on 2010-01-16
Well, I tried it myself, and I had no success.

Another friend, knowing the in's and out's of the back-end of Fedora, said that he has never seen a compute be able to run both Ubuntu successfully and Fedora successfully. He recommended me to out Fedora 9 or 10, since they are very stable, and there are no real changes in 11 and 12 that you can't update yourself.

With Fedora 9, the wireless drivers would not work at all. (same as Ubuntu's older versions)

But, Fedora 10 surprised me, a lot. It's boot process was as quick as Ubuntu 9.04 and 9.10, even possibly quicker. And, wireless worked right after the initial install.

I also found that Nvidia driver support and tutorials are much easier to find, plus they are organized better.

RPMFusion, a repository for xorg-X11 Nvidia drivers, is a very easy choice to follow. It installs through the package manager, allowing me to retry it over and over again (with some fixes through live Ubuntu CD) without reinstalling. I also found that, through the Livna repository, everything is available that I could find in Ubuntu.

I am still preferring Ubuntu, however, because I've used it so long.

Is there anyone that can help us? I have tried to find help for this for almost 4 months now.

---

### Post by Indymaynard on 2010-02-08
Partial success. GLX working.

Evidently, this is based on a fairly old problem. The problem is that the kernel module doesn't get put in the proper place. This is frustrating, but it's not the end of the world. It's a lot more simple than I made it.

After you do a vanilla install, reboot and we'll start from there. You will be presented with the option to install restricted drivers. Do this and activate the 185 version. You should probably update all of the other software, too.

After you reboot from the updates, X11 will inform you that you are running in low graphics mode. Drop to the shell using the option presented for the next step. 

Login to the command prompt. Then type in:

```

sudo dpkg-reconfigure nvidia-settings
startx

```I was greeted with the Ubuntu 9.10 default background. I had gotten this before, though, so I didn't want to start the celebration early. I clicked System->Preferences->Display. I was then informed:

It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?

Yes gave me the nVidia control panel. I was elated and wasted no time in getting here to inform you of my success. Let me know how this works for you.

---

### Post by Indymaynard on 2010-02-08
Okay, more interesting stuff. On a whim, I just decided to install the binary drivers and start from there. I had already tried this before, but it hadn't worked the first time. So I downloaded the 190.53 version. From there, I used the Terminal to kill the Xserver and install the binary driver:

```

sudo /etc/init.d/gdm stop
sudo sh /home/indymaynard/NVIDIA-Linux-x86_64-190.53-pkg2.run

```

I went ahead and had it write an xorg.conf for me, though I knew that it would be one I had already worked with that didn't work. After this, I added a line under the SLI option designating the monitor on PCI:3:0:0 as the primary. It was either PCI:3:0:0 or PCI:2:0:0, and I had worked 2 to death. I had already installed vim, so I used it to edit /etc/X11/xorg.conf in this way:

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Wed Dec  9 16:34:26 PST 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option       "SLI"    "on"
    BusID       "PCI:3:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

At first glance, this didn't seem like it was going to work. I typed startx and waited. The screen stayed black for a little while. Then, I saw the spinning disc start. Eventually, my desktop popped up and it was good looking. I had to verify that everything had worked, so I opened the NVIDIA X Server Settings from System->Preferences. Sure enough, I saw that X Screen 0 was using both cards. I've already rebooted once with success (minus a small color hiccup). Everything seems fine. I'll let you know if this continues to work.

---

### Post by Indymaynard on 2010-02-08
Well, I'll keep trying here. It's going to be a fun journey.

I now have this intermittent problem with the screen getting all psychedelic. It happens when I first boot up. I then have to switch screens (Ctrl + Alt + F1, for example), login, and type:

```
sudo /etc/init.d/gdm stop
startx

```

Sometimes the desktop will appear normal, and sometimes it won't. It's really baffling. I'm glad I've gotten this far, though.

Very few warnings show up in the most recent Xorg.0.log. One about Cyrillic not being in the path and another unimportant one. No errors.

Also, some of the screens (Ctrl + Alt + F2, - Ctrl + Alt + F7) show up funky. It is a bunch of gray, vertical lines. You can tell where the cursor is at, but it is all unintelligible. I'm not sure how that one works. Maybe that's why I get the psychedelic colors. I'm going to keep trying for it, but it might not be tonight.

---

### Post by Indymaynard on 2010-02-17
Okay, I'm not sure why this is the way it is, but this is what I've found to be my solution. Something is not letting gdm start properly the first time. When I use the above solution, things freeze up on the screen when OpenGL stuff happens. It is crappy that I have to have a solution like this, but maybe someone else can see it and help out.

After I log into my computer (usually in a psychedelic gdm), I press Ctrl + Alt + F1 to go to a login prompt (hidden among some of my startup messages.) Then, I type in the following:

```

sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start

```

Then, everything seems to work fine. No freezing! But I can't find error messages to save my life. It's very weird. Is it possible that someone has an idea?

---

### Post by Vinnare on 2010-02-18
I've installed Ubuntu only yesterday in my new laptop everything worked out fine till I installed the nVidia display driver suggested by its search. When I rebooted, the display went blank after displaying the normal ubuntu startup circles. Actually the display gets switched off and NOT BLACK (you can mke that difference easily) but the system keeps on. You can infact even log in if you type the password (as if blindfolded, of course ), you know this by the welcome music. Then you can do the work too if you know how to use the keyboard.

When I tried starting in the recovery mode then I did as suggested in most of the other forums i.e. type the command:
sudo dpkg-reconfigure xserver-xorg
but unlike as suggested the rest of the process does not follow and the command line reappears.

Please suggest some solution. **My GPU is NVIDIA GT330M**.
I'm new to linux.

Thnx anyhow

---

### Post by Indymaynard on 2010-02-18
Page 1 of this thread contains a whole lot of stuff that I've done to get mine working.
 
You mentioned that you did:
 
```
 
dpkg-reconfigure xserver-xorg

```
 
But you should actually try:
 
```
 
dpkg-reconfigure nvidia-settings

```
 
See if this works for you, but don't forget to sudo this command.

---

### Post by Troop116rules on 2010-02-18
I apologize for not keeping in contact. I had a little accident with my laptop. (Actually big, I drove over it :S lol)

Amazingly, nothing is damaged except the screen and a couple cracks in the top half of the case. (below the screen) This is because, of course, me driving over it bent the top half of the case.

Thankfully, nothing else is damaged. They said it boots fine.

Sadly, though, the screen is the most expensive part of the laptop. :S The total repair cost is $881 (includes shipping)

I was sure my Western Digital external hard drive, above the laptop at the time, was shot. But, low and behold, it was only the case that was shot. USB wouldn't work.

So, I plugged it in via SATA in my desktop at home, and it didn't load. But, unmounting and remounting it in Linux fixed it. My friend said that Linux resets the hard disk error codes on the hard drive.

So, now I have it running beautifully in my Windows server under FTPES. Yay.

I'll definitely try out what you suggested when I get my laptop back. I'm not entirely experienced with Linux, but at least I can follow directions without being n00bish. :)

---

### Post by Indymaynard on 2010-03-16
I've been doing this all wrong. The easiest fix once I get the psychedelic colors is to press Ctrl + Alt + F1 to switch screens. Then I just switch back to the login screen by pressing Ctrl + Alt + F7. This actually takes care of everything. How weird.

---

### Post by Troop116rules on 2010-07-25
I finally got around to facing my fears, and tried my hand at installing the Nvidia drivers.

It turns out that I tried installing the 256.35 official driver from Nvidia.

(NVIDIA-Linux-x86-256.35.run - I'm running 32-bit, :-) )

It installed nicely. I backed up the generated xorg.conf and copied your xorg.conf over. I rebooted, and I had no problems starting up Ubuntu. It wasn't even slow.

With Extra Settings and SLI, I'm ready to get compizconfig-settings-manager installed. :-D

Thanks for the help. Topic closed.

---

