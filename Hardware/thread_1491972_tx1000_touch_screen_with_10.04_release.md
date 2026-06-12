---
title: "tx1000 touch screen with 10.04 release"
date: 2010-05-24
forum: Hardware
---

### Post by blakstar61 on 2010-05-24
All

I'm an absolute noob, so please excuse me if this has already been posted before.

I have an HP tx1000 tablet that I've just finished installing the newest version to.  Everything works so far, except for my touch screen.  I've found numerous posts regarding earlier releases and getting this to work with the sudo-apt command and the ev something-or-other driver.  However, I do not see the configuration tool in any of my menus.

Looking at the synaptics package manager, it says the drivers are there and installed. Reboots have not helped, either.

Any help would be appreciated! :)

---

### Post by Favux on 2010-05-24
Hi blakstar61,

Welcome to Ubuntu forums!

It looks like you have a couple ways to go.  Get it working with evtouch.  You say it's installed but not working.  That probably means either the configuration file for evtouch wasn't installed or the match line in it isn't picking up the TX1000.  If present it is probably called something like xx-evtouch.conf and located in /usr/lib/X11/xorg.conf.d/.

The alternative appears to be the eGalax beta driver.  This post describes using that:  [http://ubuntuforums.org/showpost.php?p=9247538&postcount=33](http://ubuntuforums.org/showpost.php?p=9247538&postcount=33)  And it links you to the eGalax driver site:  [http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm)

Hope this helps.  Good luck!

---

### Post by blakstar61 on 2010-05-24
Thanks for the quick answer!

The file is there, and here are the contents:

Section "InputClass"
    Identifier "touchscreen catchall"
    MatchIsTouchscreen "on"
    Driver "evtouch"
EndSection

Not sure what this all means (did I mention that I'm a noob?).

I may have to try the alternative you suggested if this looks correct.

---

### Post by Favux on 2010-05-24
That looks right.  In a terminal try:
```
xinput --list
```
and lets see if the output has your touch screen.

---

### Post by Favux on 2010-05-24
Oops, forums double posted.

---

### Post by blakstar61 on 2010-05-24
Sure thing

Here's the output:

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; eGalax INC. USB TouchController             id=11    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; USB 2.0 Camera                              id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

Also, I took a look at some other posts, and I don't seem to have a driver loaded in /etc/X11/xorg.conf.

Following are the contents:

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

I would expect there to be an entry here, but there isn't.  Question is, how do I open it for edit?  It seems it's marked for read-only.

Thanks for the help and patience!

---

### Post by blakstar61 on 2010-05-29
Well, I managed to get the touchscreen semi-working with the eGalaxTouch driver.  I configured the screen and such, but the issue I see is that every time I touch the screen, the application menu opens, making it rather annoying to try and use.

Has anybody ever seen this behavior?  Or is it a setting I'm missing?

---

### Post by billund on 2010-06-21
I'm "suffering" same problem!

I want to use touchscreen... I tried many ways... Nothing works.

Everything what is said in this thread, I tried...

I have same behavior... When I touch, only in top-left is "felt"...

I send SOS!

---

### Post by Favux on 2010-06-21
Hi billund,

Welcome to Ubuntu forums!

When the arrow goes to the upper left that usually means the driver isn't working.  What does your:
```
xinput --list
```
show?

---

### Post by billund on 2010-06-21
At least... I think I found the solution... (!)

Here: [http://ubuntuforums.org/showthread.php?t=831041](http://ubuntuforums.org/showthread.php?t=831041)

It goes almost perfect...

Now the problem is: when I touch the screen, the mouse pointer always begins at top-left, then in less a second goes to where the touch point is...

It makes a hold windows to work "crazy"...

Any cheat?

---

### Post by Favux on 2010-06-21
Hi billund,

It would help if you told us what you did from that thread.

---

### Post by billund on 2010-06-21
Sorry...

Let me tell how I did it: :roll:

I did almost everything what is explained by first post on the linked thread... :arrow:

But after restarting X, (logout and login again... ), I went directly to terminal and digited the command "eGalaxTouch"... The party began. \\:D/

But my beer has been watered by the little, but annoying, problem described by me a two post ago... ](*,)

Hope that it may help you, and you help me. :wink:

---

### Post by Favux on 2010-06-21
So you downloaded the 4-13-10 Beta version from here?:  [http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm](http://home.eeti.com.tw/web20/eGalaxTouchDriver/linuxDriver.htm)  Did you look at the read me?

---

### Post by billund on 2010-06-22
Yes... This...

With this "Kernel 2.6.x   3.01.4001", with 32-bit

(because 64-bit hasn't full support yet for major programs...)

Answering your post, here:

Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; egalax                                      id=6    [slave  pointer  (2)]
&#9116;   &#8627; eGalax INC. USB TouchController             id=12    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=14    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; USB 2.0 Camera                              id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]


It almost worked perfectly... 

Only solving about what I said, it will be 100% perfect! :-({|=

---

### Post by Favux on 2010-06-22
Well the driver is in Beta.  So they probably want feedback.  Describe:
> Now the problem is: when I touch the screen, the mouse pointer always begins at top-left, then in less a second goes to where the touch point is...
on their form:  [http://home.eeti.com.tw/web20/fae.htm](http://home.eeti.com.tw/web20/fae.htm)  (touch_fae@eeti.com).

Did you change your xorg.conf in /etc/X11?  Did the driver install a xx-eGalax.conf in /usr/lib/X11/xorg.conf.d/?

---

### Post by pithdillinja on 2010-07-26
I am having the same problem as billund - I'll try to be more literate about what happens though.

If you don't feel like reading all that, here's a quick summary:
- I believe that installing the eGalaxTouch drivers (which work CORRECTLY) causes interference with the drivers that come out-of-the-box with Lynx.
- I believe the solution is to remove the original drivers. Problem is, I'm not experienced enough to know which drivers these are.

Details:

I am running ubuntu 10.04 on the tx1000 on a 64-bit architecture.
I installed the egalax BETA driver that was recently release. (july 20th)
I configured the tablet using eGalaxTouch and the stylus input is properly recognized.

Whenever I press the stylus against the screen, 2 things happen:
1. The mouse moves to position 0,0 (top left) and occasionally clicks.
2. The mouse immediately pops over to the correct position as given by my stylus's input. Also occasionally clicks.

I believe that one of two things are happening here: (just a guess though)
1. There are two scripts that manage the touchscreen input. One of them isn't configured, and that one is the script that is causing the top-left positioning. The other script is the properly configured one that is working fine, but is being interfered with by the original script.
2. There is only one script that manages the touch screen, and the way it works is it detects a click, moves the mouse to a generic position, THEN moves the mouse to a proper position and clicks.

It wouldn't make much sense to have option #2 to be the correct problem here, seeing as that seems to be pretty bad programming.

I've read other threads and some of them mention Lucid Lynx coming with some touchscreen drivers already. Lynx DID successfully detect input BEFORE I installed the correct eGalaxTouch drivers - so maybe the only solution is to remove whatever generic scripts/drivers were previously installed with Lynx.

Thanks guys. I am inspired by the geniuses on these forums that seem to know exactly what to do. I call for you geniuses.

---

### Post by Favux on 2010-07-26
Hi pithdillinja,

Welcome to Ubuntu forums!

What we want to see is what the eGalax.conf looks like.  It'll be named something like 50-egalax.conf and be located, most likely, in /usr/lib/X11/xorg.conf.d/.  It'll be installed by the beta driver.

I don't think evtouch is installed by default.  Evdev is though, and it's touchscreen or touchpad catchall might be interfering.  We want to see what's happening in Xorg.0.log in /var/log.

---

### Post by Ocxic on 2010-07-26
I HAVE THE SOLUTION!!!! I installed a eGalax touchscreen in my eeepc and YES the ubuntu touchscreen drivers interfere with the eGalax drivers(Same stuffs happening as you describe [pithdillinja]("http://ubuntuforums.org/member.php?u=1118660")).

I had to do this to my "/usr/lib/X11/xorg.conf.d/05-evdev.conf" then all was well!!(you'll still need the eGalax drivers.)  ( i didn't comment out the keyboard section because that actually disabled my keyboard)

```

# Catchall classes for input devices
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

#Section "InputClass"
#    Identifier "evdev pointer catchall"
#    MatchIsPointer "on"
#    MatchDevicePath "/dev/input/event*"
#    Driver "evdev"
#EndSection

Section "InputClass"
    Identifier "evdev keyboard catchall"
    MatchIsKeyboard "on"
    MatchDevicePath "/dev/input/event*"
    Driver "evdev"
EndSection

#Section "InputClass"
#    Identifier "evdev touchpad catchall"
#    MatchIsTouchpad "on"
#    MatchDevicePath "/dev/input/event*"
#    Driver "evdev"
#EndSection

#Section "InputClass"
#    Identifier "evdev tablet catchall"
#    MatchIsTablet "on"
#    MatchDevicePath "/dev/input/event*"
#    Driver "evdev"
#EndSection

#Section "InputClass"
#    Identifier "evdev touchscreen catchall"
#    MatchIsTouchscreen "on"
#    MatchDevicePath "/dev/input/event*"
#    Driver "evdev"
#EndSection

```

---

### Post by pithdillinja on 2010-07-26
That worked great Ocxic! I looked at this configuration file initially and decided I didn't want to mess with it - I guess I should have! And thank you, favux, for the welcome! You guys are great. Looks like I just found a new home for forum-ing!

---

### Post by Alejandro Nova on 2010-08-23
Read carefully this Ubuntu bug report. The solution has been with us since ever, and is around the corner; however nobody sees it.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/549447](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/549447)

Basically, that's about using **evdev** (not evtouch, but the generic evdev driver that powers everything input-related on a fully working Lucid system) to manage the eGalax touchscreen. When you press on the screen and watch the cursor going to a corner it's because the screen is working fine. It only needs this, in your kernel line (/etc/default/grub, GRUB_CMDLINE_LINUX)

```
usbhid.quirks=0xeef:0x1:0x40
```

After that, reboot. The touchscreen should work. To calibrate, add this PPA, install this and run this ;).

```
$ sudo add-apt-repository ppa:tias/xinput-calibrator-ppa
$ sudo apt-get install xinput-calibrator
$ xinput_calibrator_x11
```

Later, pick the right calibration values (they will be written down for you if you run xinput_calibrator on the console, don't worry) and send them to /usr/lib/X11/xorg.conf.d/05-evdev.conf . Add this section:

```
Section "InputClass"
        Identifier "eGalax"
        MatchProduct "eGalax"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "SwapAxes" "on" #<- This is optional!
        Option "Calibration" "415 3906 406 3862" # MODIFY THIS WITH YOUR VALUES
EndSection
```

This should make work your eGalax touchscreen under Lucid. No binary blob required. Also, it's highly recommended you watch my tx1000 howto for Fedora 12/13 there: [http://fedoraforum.org/forum/showpost.php?p=1357742&postcount=3](http://fedoraforum.org/forum/showpost.php?p=1357742&postcount=3) . All Ubuntu-specific bits are here.

---

### Post by synplague on 2010-09-06
Hi guys, I have a tx1000 (ubuntu 10.04 i386) and still with the same problem as pithdillinja[]("http://ubuntuforums.org/member.php?u=1118660") had. I did the solution proposed by Ocxic and this last one by Alejandro Nova, but none of them worked for me.

With the first one nothing happened. With the second one, after installing xinput-calibrator as proposed, I couldn't run xinput_calibrator_x11, said that was not installed. So I ran xinput_calibrator, a red cross appeared on the screen, I touched it and the cursor went to the 0,0 position. Wen the second red cross appeared I the click was to the same position (0,0) and the program didn`t recognized as click on a different position... So I had to quit the program. 

What else can I do???

Thanks everybody.

---

### Post by synplague on 2010-09-07
Ok, working!!! After 5 years of tablet pc I have the touchscreen working on linux!!!! No need of Rwindows anymore!!! :p:D:p

I followed what proposed in [http://samiux.blogspot.com/2010/07/howto-ubuntu-1004-on-gigabyte-touchnote.html](http://samiux.blogspot.com/2010/07/howto-ubuntu-1004-on-gigabyte-touchnote.html)

It's similar of what Alejandro Nova did, I'll show the differences too. 

First, it appends usbhid.quirks=0xeef:0x1:0x40 to the line GRUB_CMDLINE_LINUX_DEFAULT instead of the line GUB_CMDLINE_LINUX in the Alejandro's post. The line stays like: 
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.noloop=1 usbhid.quirks=0xeef:0x1:0x40"
```And then updated the grub:
```
sudo update-grub
```Second, append the line
```
blacklist usbtouchscreen
```To the file
```
/etc/modprobe.d/blacklist.conf
```The third step is like Alejandro's, open the file
```
/usr/lib/X11/xorg.conf.d/05-evdev.conf
```And append the code 
```
Section "InputClass"
   Identifier "eGalax"
   MatchProduct "eGalax"
   MatchDevicePath "/dev/input/event*"
   Driver "evdev"
   Option "SwapAxes" "off" 
   Option "Calibration" "44 4007 108 3988" #my calibration
EndSection
```You can use my calibration and after calibrate your screen  change to yours.

Fourth you have to install the xinput_calibrator. I did the solution of the site I mentioned, but is easier to install via apt-get, like Alejandro. Remember to update after add a repository. 
```
$ sudo add-apt-repository ppa:tias/xinput-calibrator-ppa
$ sudo apt-get update
$ sudo apt-get install xinput-calibrator
``` When I installed the xinput_calibrator there was no option to run xinput_calibration_x11, like in the Alejandro's post. So I used xinput_calibrator and didn't find any problem. 

To finish, reboot your system and calibrate your screen running
```
xinput_calibrator
```And reedit the file in the third step with your own calibration settings.

Good luck, and enjoy your touchscreen on ubuntu 10.04!!!

---

### Post by synplague on 2010-10-13
By the way, I'm with some troubles with the screen rotation. When I rotate the screen the touch configuration gets crazy. When I return to the normal position the calibration looks ok.

Any ideas??

---

### Post by Dhruv94 on 2010-11-06
hey guys, 

im a ABSOLUTE noob at this stuff ( im sorry)

my problem that bothers me the most is the touchscreen... 

im running 10.10 64bit

i have no clue what egalax is or touchkit and things..

so can anyone help me out and guide me to help me get my touch screen working.

thanls guys :)

oh and sorry i forgot, i have a HP tx1000 series notebook, to be specific its the hp tx-1218ca

thank u

---

### Post by Alejandro Nova on 2011-02-07
Guys, if you are still there and alive, I can report that the AutoMagic&#8482; Rotation featured in the tx2000, tx2500, and TouchSmart tm2 and tx2 WORKS HERE FLAWLESSLY.

@Dhruv94: Follow the updated instructions by **synplague**. Don't worry about the blob, egalax or touchkit. The relevant line is this one.

```
GRUB_CMDLINE_LINUX_DEFAULT="usbhid.quirks=0xeef:0x1:0x40"
```

This line enables your evdev driver, the thing that drives your keyboard and your mouse, to drive also your touchscreen. These instructions also work with Maverick. Also, add the PPA I suggested: the new xinput-calibrator 0.7.5 even has a menu entry! 

Here's my autorotate script. Remember: the device numbers are tx1000 specific, and this won't work if you are using the blob; you need to kill the blob and rely on free drivers as synplague and I suggested.

```
#!/bin/sh
OLDMODE=$(cat /sys/devices/platform/hp-wmi/tablet)
while true; do
    MODE=$(cat /sys/devices/platform/hp-wmi/tablet)
    if [ "$MODE" != "$OLDMODE" ]
    then
        #echo "$MODE - $OLDMODE"
        case "$MODE" in
            "0")
                # Do something
                echo "Normal mode"
                xrandr -o normal
                xinput set-prop 12 "Evdev Axis Inversion" 0 0
                xinput set-prop 12 "Evdev Axes Swap" 0
                xinput set-prop 13 "Evdev Axis Inversion" 0 0
                xinput set-prop 13 "Evdev Axes Swap" 0
                ;;
            "1")
                # Do something else
                echo "Tablet mode"
                xrandr -o left
                xinput set-prop 12 "Evdev Axis Inversion" 1 0
                xinput set-prop 12 "Evdev Axes Swap" 1
                xinput set-prop 13 "Evdev Axis Inversion" 1 0
                xinput set-prop 13 "Evdev Axes Swap" 1
                ;;
        esac
        OLDMODE=$MODE
    fi
    sleep 3s
done
```

---

### Post by WillLik on 2011-05-17
Good advice here, sometimes a bit hard to follow, but it's nice to be getting all these little bits working on this tx1000.

---

### Post by WillLik on 2011-05-17
I am still not getting what do do with the above script though.

---

### Post by tbongiovani on 2011-06-03
Hello,
Dont work, for 11.04.
The pointer only move to up left!!!

I execute steps for [Alejandro Nova]("http://ubuntuforums.org/member.php?u=728980").
My hardware is not a pc table, is monitor touchscreen. 

My 05-dev.conf
Section "InputClass"
        Identifier "eGalax"
        MatchProduct "eGalax"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "SwapAxes" "on" #<- This is optional!
        Option "Calibration" "415 3906 406 3862"
EndSection

pdv@jundiaiOrlando:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:00e1 Microsoft Corp. Wireless Laser Mouse 6000 Reciever
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0eef:7229 D-WAV Scientific Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1e3d:2093  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


pdv@jundiaiOrlando:~$ xinput --list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; eGalax Inc. USB TouchController             id=8    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft Wireless Optical Mouse® 1.00    id=9    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]

---

