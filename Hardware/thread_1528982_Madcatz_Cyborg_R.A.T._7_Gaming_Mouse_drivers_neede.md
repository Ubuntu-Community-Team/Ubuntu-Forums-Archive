---
title: "Madcatz Cyborg R.A.T. 7 Gaming Mouse drivers needed."
date: 2010-07-11
forum: Hardware
---

### Post by nikitis on 2010-07-11
Madcatz Cyborg R.A.T. 7 Gaming mouse. (Kernel recognizes it as a Saitek Cyborg R.A.T. 7 mouse.)

I already posted this in the Desktop hardware incompatibility list, but I'm doing it here to just so it gets noticed.  

This mouse works when you first start into Gnome or KDE.  I've done this on my Desktop running Gnome 10.04, and KDE 10.04 on my Laptop, and I get the same results. 

When using it after a few seconds, things no longer become clickable left or right.  I'm not entirely sure if it's the mouse, or if it's the Display Managers (Maybe Xorg?), but if I push the buttons to change the "DPI" Settings on the mouse, things work again for a few more seconds, then it starts to happen all over again.  

The only thing that makes me think it's on the software side of things and not just the hardware is 1.) It works in Windows without drivers and doesn't crashes, and 2.) in KDE, I can still click on the big "K" start menu like item while it's wigging out.  This mouse has an usually high Dot Per Inch laser and maybe the linux kernel can't handle it? 5400 DPI.  Most mice only go up to like 800 or 1500.

Anyway, I tried asking in #ubuntu IRC, but they don't know what's going on.  They had me try a: $ tail -f /var/log/syslog and tail -f /var/log/messages to see if there was anything going nuts while using it, and I got nothing except for the plug in and plug out messages.

This mouse needs to work if Linux is ever going to be taken seriously on the gaming front ;)  please, please PLEASE i beg someone to help me diagnose and fix this error!  I will do/try anything, including reinstalls.  Just help me out here!

---

### Post by mohaine on 2010-07-27
I can verify this issue.   

It seems that with this mouse hooked up, the window manager gets confused. The application with focus will still accept mouse clicks, but you can not click on anything outside the focused window.

Pressing the mode button will fix things for a bit, but the issue will come back very quickly(< 30 seconds)

---

### Post by pag747 on 2010-08-08
Same issue!!

---

### Post by pag747 on 2010-08-08
Firefox and Gedit


(firefox-bin:11366): Gdk-CRITICAL **: gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

(gedit:13609): Gdk-CRITICAL **: gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

---

### Post by mohaine on 2010-08-09
This seems to be an Xorg issue.  

I've compiled Xorg from GIT and it seems to be fixed upstream.

Still broken in 10.10 alpha 3.

---

### Post by jawvvd on 2010-08-27
Please log in and vote (mark yourself as affected) here: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/615892](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/615892)

Hopefully it's possible to patch this for 10.04, after all it's a LTS release...

---

### Post by Ancanus on 2010-10-11
Does the workaround posted on the bug report work for you guys?

---

### Post by TheMadEngineer on 2010-10-21
I managed to get the Xmodmap fix to work in 10.10 with a R.A.T. 3 Mouse, though with a slight modification:

In ~/.Xmodmap,
```
pointer = 1 2 3 4 5 6 7 8 9 0 0 0
```

Apparently, the mode button is specified by 10, 11, and 12 for this mouse.  To get it to work, though, I had to actually restart the X server from a virtual terminal after rebooting.

---

### Post by bl4z on 2010-10-28
that worked for me // thanks

> **TheMadEngineer said:**
> I managed to get the Xmodmap fix to work in 10.10 with a R.A.T. 3 Mouse, though with a slight modification:

In ~/.Xmodmap,
```
pointer = 1 2 3 4 5 6 7 8 9 0 0 0
```

Apparently, the mode button is specified by 10, 11, and 12 for this mouse.  To get it to work, though, I had to actually restart the X server from a virtual terminal after rebooting.

---

### Post by mpampis636 on 2010-10-31
Hello  Im using the RAT 5, and not 7, on Debian.  I've run into the same problem many times. Everytime this happens, i log out and log back in, and the mouse works. However the solution of changing .Xmodmap or even the global Xmodmap didn't help.  I run xev, and noted down all buttons, which run from 1,2,3,4,5,8,9,10,11,12,[13,14,15],16,17  The buttons 13,14,15 are found on the same button (the emblem that switches profiles).  I tried using /dev/input/event instead of /paux/mouse, with options buttons 15 enabled in xorg.conf but still nothing changed.  Im assuming the problem lies with the fact that the profile button is mapped as 3 different buttons, cuz If i log in (the second time) and never click it, the mouse keeps running fine.  I don't know how to go on, to solve this issue, but I'm assuming someone with more experience might have a solution...

---

### Post by oohbuntoo on 2010-11-18
> **TheMadEngineer said:**
> I managed to get the Xmodmap fix to work in 10.10 with a R.A.T. 3 Mouse, though with a slight modification:

In ~/.Xmodmap,
```
pointer = 1 2 3 4 5 6 7 8 9 0 0 0
```

Apparently, the mode button is specified by 10, 11, and 12 for this mouse.  To get it to work, though, I had to actually restart the X server from a virtual terminal after rebooting.
This unfortunately is all greek to me.  I don't have a Xmodmap file.  I had a Xmodmap.swp file that couldn't be read.  Could you add a little more detail to what you did here.

---

### Post by elglas on 2010-11-18
how to create a .Xmodmap file:

1. Open up your text editor of choice, gedit (or Accessories > Text editor) is my perfered choice.

2. in the first line of a new file, paste in:
```

pointer = 1 2 3 4 5 6 7 8 9 0 0 0

```

3. Save that file as .Xmodmap (case sensitive) in your home directory, and restart your gnome session (or restart your computer)

4. On boot, Ubuntu 10.10 will prompt you for which Xmodmap file to load. Select the one you just created, and hit load.


Issue: I still have the same error after rebooting, help anyone?

---

### Post by japser on 2010-12-15
> **elglas said:**
> how to create a .Xmodmap file:

1. Open up your text editor of choice, gedit (or Accessories > Text editor) is my perfered choice.

2. in the first line of a new file, paste in:
```

pointer = 1 2 3 4 5 6 7 8 9 0 0 0

```

3. Save that file as .Xmodmap (case sensitive) in your home directory, and restart your gnome session (or restart your computer)

4. On boot, Ubuntu 10.10 will prompt you for which Xmodmap file to load. Select the one you just created, and hit load.


Issue: I still have the same error after rebooting, help anyone?

It doesn't solve the problem. Program's are still not clickable.
(Should point out that the mousemovement is very nice ;))

What is the status of this bug being solved?

---

### Post by awc_ on 2011-01-22
> **TheMadEngineer said:**
> I managed to get the Xmodmap fix to work in 10.10 with a R.A.T. 3 Mouse, though with a slight modification:

In ~/.Xmodmap,
```
pointer = 1 2 3 4 5 6 7 8 9 0 0 0
```Apparently, the mode button is specified by 10, 11, and 12 for this mouse.  To get it to work, though, I had to actually restart the X server from a virtual terminal after rebooting.

For my R.A.T.9 Mouse, the mode button is mapped as 13 14 and 15 so 

pointer = 1 2 3 4 5 6 7 8 9 10 11 12 0 0 0 16 17 18 19 20 21

does the trick.

---

### Post by elglas on 2011-02-03
A slightly more permanent solution appears to append to (or create on a stock installation) your /etc/X11/xorg.conf file.

complete instructions can be found here in post #23.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/615892](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/615892)

---

### Post by Chris_28 on 2011-03-17
How can I fix this on Kubuntu. I can't find it anywhere and I'm new with Linux. Please help :confused:
I can't find xorg.conf file in /etc/X11/

OK
I've managed to generate xorg.conf in case some noob like myself is trying to do the same:

1. Ctrl+Alt+F1, login
2. sudo service kdm stop (gdm for ubuntu, kdm for kubuntu)
3. sudo Xorg -configure
4. sudo mv /home/"username"/xorg.conf.new /etc/X11/xorg.conf
5. sudo service kdm start

6. open terminal
7. sudo kate /etc/X11/xorg.conf (kate for kubuntu, gedit for ubuntu)
8. add (for R.A.T. 5):

Section "InputClass"
        Identifier "Mouse Remap"
        MatchProduct "Saitek Cyborg R.A.T.5 Mouse"
        MatchDevicePath "/dev/input/event*"
        Option "ButtonMapping" "1 2 3 4 5 6 7 2 9 10 11 12 0 0 0"
EndSection

save it and restart, then see if it works

---

### Post by Idyll on 2011-11-11
This worked for me with Ubuntu 11.10 from:
[http://fcns.eu/2011/04/cyborg-rat-7-mouse-under-linux/](http://fcns.eu/2011/04/cyborg-rat-7-mouse-under-linux/)


Add this section to you xorg.conf file. 

You can do it by typing this in a terminal: 
sudo gedit /etc/X11/xorg.conf
and then pasting the following block of text at the bottom of the file:

Section "InputClass"
        Identifier "Mouse Remap"
        MatchProduct "Saitek Cyborg R.A.T.7 Mouse"
        MatchDevicePath "/dev/input/event*"
        Option "ButtonMapping" "1 2 3 4 5 6 7 2 9 10 11 12 0 0 0"
EndSection

---

### Post by MiLeon on 2011-12-16
Thx, this thread help with debian squeeze (xfce 4) and R.A.T. 7

My system have no xorg.conf (same "problem" from [Chris_28]("http://ubuntuforums.org/member.php?u=1263031")), but just create a .Xmodmap in home directory and insert:
pointer = 1 2 3 4 5 6 7 8 9 10 11 12 0 0 0
and restart xserver/login manager

Ciao!

---

### Post by De4dSpace on 2012-01-31
1 2 3 4 5 6 7 8 9 5 4 12 0 0 0 :popcorn:

Replace the 10 and 11 with 5 and 4 to enable the thumb scroll-wheel for that side to side action.

---

### Post by vralfy on 2012-08-12
Hi everyone ... I dont know if i could help you, but i have also a Rat 7 on my Ubuntu 12.04.
But post my Solution here. Perhaps someone could use it:

Paste the following to your /etc/X11/xorg.conf:

```

    Section                       "InputClass"
    Identifier                    "Mouse Remap"
    MatchDevicePath    "/dev/input/event*"
    MatchProduct          "Saitek Cyborg R.A.T.7 Mouse"
    Option                        "AutoReleaseButtons"     "13 14 15"
    Option                        "Buttons"            "17"
    Option                        "YAxisMapping"          "10 11"
    Option                        "ZAxisMapping"        "4 5 6 7"
    Option                        "Emulate3Buttons"    "no"
    Option                        "Resolution"        "3200"
    Option                        "ButtonMapping"     "1 2 3 4 5 0 0 8 9 7 6 12 0 0 0 16 17"
EndSection

```Restart and have fun!

---

### Post by endorlow on 2012-08-16
> **Chris_28 said:**
> How can I fix this on Kubuntu. I can't find it anywhere and I'm new with Linux. Please help :confused:
I can't find xorg.conf file in /etc/X11/

OK
I've managed to generate xorg.conf in case some noob like myself is trying to do the same:

1. Ctrl+Alt+F1, login
2. sudo service kdm stop (gdm for ubuntu, kdm for kubuntu)
3. sudo Xorg -configure
4. sudo mv /home/"username"/xorg.conf.new /etc/X11/xorg.conf
5. sudo service kdm start

6. open terminal
7. sudo kate /etc/X11/xorg.conf (kate for kubuntu, gedit for ubuntu)
8. add (for R.A.T. 5):

Section "InputClass"
        Identifier "Mouse Remap"
        MatchProduct "Saitek Cyborg R.A.T.5 Mouse"
        MatchDevicePath "/dev/input/event*"
        Option "ButtonMapping" "1 2 3 4 5 6 7 2 9 10 11 12 0 0 0"
EndSection

save it and restart, then see if it works

realy thx

---

### Post by unoo on 2013-01-25
sorry to be a noob but I have having issues with this mouse in ubuntu 12.10.  When I plug it in the roll overs don't work and the clicks don't work.  My computer basically freezes up with the mouse plugged in.  Does this xorg.conf file work with ubuntu 12.10?

I have a 2009 Macbook Pro with the nvidia geforce 9400m video card.  core 2 duo running at 2.53Ghz and 8gb of ram.  I cannot get the file to save at all after I open it in the console so that's why I am asking.  If it does work then what am I doing wrong?  I have been searching for about 2 days now but I can only find information on previous versions of ubuntu.  Thanks for any help provided!

p.s. I know this is an old thread.  I wasn't sure if I should create a new one for ubuntu 12.10.

---

### Post by sasukeskapa on 2013-02-07
Cyborg RAT 7 mouse Linux Setup:
Hi everyone ... I dont know if i could help you, but i have also a Rat 7 on my Kubuntu 12.04.
But post my Solution here. Perhaps someone could use it:

First run this code:
```

xinput -list

```
Search for your mouse's name:
(My is "Mad Catz Mad Catz R.A.T.7 Mouse" ,but can be other like: "Saitek Cyborg R.A.T.7 Mouse")

Paste the following to your /etc/X11/xorg.conf:
(sudo nano /etc/X11/xorg.conf) for example
BUT!!! Change the 
MatchProduct     "Mad Catz Mad Catz R.A.T.7 Mouse"
line to match your mouse's name :)

```

Section "InputClass"
    Identifier       "Mouse Remap"
    MatchDevicePath  "/dev/input/event*"
    MatchProduct     "Mad Catz Mad Catz R.A.T.7 Mouse"
    Option           "AutoReleaseButtons"    "13 14 15"
    Option           "Buttons"     "17"
    Option           "YAxisMapping"      "10 11"
    Option           "ZAxisMapping"     "4 5 6 7"
    Option           "Emulate3Buttons"  "no"
    Option           "Resolution"   "3200"
    Option           "ButtonMapping"   "1 2 3 4 5 0 0 8 9 7 6 12 0 0 0 16 17"
EndSection

```

Restart and it works :)

---

### Post by sasukeskapa on 2013-02-07
Did you use the sudo magic word???
With that it HAS to save :)
(Earlier post has a working solution for me, try it :D)

---

### Post by Narcas on 2013-02-26
Anybody know how to do this with the M.M.O.7 Mouse? It's basically a Rat 7 with more buttons.. Thanks!

---

