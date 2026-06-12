---
title: "Scrolling question"
date: 2005-03-31
forum: Hardware &amp; Laptops
---

### Post by radioact1ve on 2005-03-31
Hey all!

Yeah, sorry another Synaptics touchpad scrolling question. Vertical (dont care for horizontal) scrolling just wont work!

I have used VertScrollDelta, updownscrolling, and what not. I have followed all the HowTos on ubuntu wiki and the search the fourms like crazy. I do what work for other people but I just wont work here.  ](*,) 

Any other suggestions? Everything else on the toucpad works fine!

Thxs for your time!!

- Miguel

---

### Post by lerrup on 2005-03-31
Mine worked out the box.  Here is the part of my config file that refers to it:

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option  "HorizScrollDelta" "0"
EndSection

Have you tried these settings?

---

### Post by tmowerman on 2005-03-31
I needed to change the size options on my touchpad to enable vertical scrolling.

  ```

  Option        "LeftEdge"      "1700"
  Option        "RightEdge"     "5650"
  Option        "TopEdge"       "1700"
  Option        "BottomEdge"    "5000"
  
```

in the synaptics section of xorg.conf

I suggest try fiddling with these a until you get the desired result

Tim

---

### Post by radioact1ve on 2005-03-31
I tried those number you gave me Tim but my config was almost set-up like that. I tried it anyway and still nothing. Should I make then numbers bigger or smaller?

lerrup, yea I have those settings (and others) exactly like that. Thats how it always has been. 

Im thinking of compiling my own driver ( do I have to compile the kernel!?!) to see if that would work if there are not anymore ideas...

Thanks you two, Im so close and I know we can do it!! 8)

---

### Post by lerrup on 2005-04-01
There is a technique to using the touchpad, you need to have the window you wish to scroll focused and then put your finger as far right as you can and then apply pressure.  Then you should be able to scroll the window by moving it up and down.

I'm not taking the mick, but just checking.  

If anyone knows how to make the scroll wheel work, please tell me.

---

### Post by tmowerman on 2005-04-01
Im just a newbie too, but thought id let you know because it worked for me

The numbers seem to refer to the size of the actual touchpad, where the computer registers the mouse movements.  My touchpad actually has a seperate area for scrolling up and down, so maybe that is why.

I would recommend making the right edge number smaller, but im just guessing

Tim

---

### Post by tmowerman on 2005-04-01
Ive just thought of something else i had to change in my xorg.conf that may make it work, if your laptop has a mouse port as well

These are the relevant sections of xorg.conf

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
#       Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
  Driver        "synaptics"
  Identifier    "Synaptics Touchpad"
  Option        "Device"        "/dev/psaux"
  Option        "Protocol"      "auto-dev"
# Option        "CorePointer"
# Option        "SendCoreEvents" "true"
  Option        "LeftEdge"      "1700"
  Option        "RightEdge"     "5650"
  Option        "TopEdge"       "1700"
  Option        "BottomEdge"    "5000"
  Option        "FingerLow"     "25"
  Option        "FingerHigh"    "30"
  Option        "MaxTapTime"    "0"
  Option        "MaxTapMove"    "220"
  Option        "VertScrollDelta" "100"
  Option        "HorizScrollDelta" "0"
  Option        "MinSpeed"      "0.2"
  Option        "MaxSpeed"      "0.2"
  Option        "AccelFactor" "0.0000"
  Option        "SHMConfig"     "on"
#  Option       "Repeater"      "/dev/ps2mouse"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad" "CorePointer"
EndSection
```

Notice the core pointer and send core events in the server layout section.  If you are just using the touchpad, i think you can also remove the configured mouse section, and the line referencing it in serverlayout, but i have not tested this, so if you try this make sure to comment it out first!

Hope this helps.  It annoyed me too.

Tim

---

### Post by radioact1ve on 2005-04-01
Dam, it just crashed my X. My laptop just has usb for a mouse. No extra port. And I tired shrinking RightEdge to no use. This sucks... it works for everyone but me.  ](*,)

Thanks everyone for the help though!!!! Anything else :-k

---

### Post by radioact1ve on 2005-04-01
Anything? [-o<

---

### Post by radioact1ve on 2005-04-03
ok ok last one I promise  :cry:

---

### Post by ubuntu_demon on 2005-04-03
always backup your xorg.conf if X crashes than you can always copy it back.

did you try :
sudo dpkg-reconfigure xserver-xorg

---

### Post by radioact1ve on 2005-04-04
Oh yeah, always back up everything b4 I do something. I have learned that the hard way. 

Is that command to fix X or the scrolling problem? X is working so thats all good here. Just that dam scroll!! 

Thanks though!!!! :-)

---

### Post by ubuntu_demon on 2005-04-04
[QUOTE=radioact1ve]Oh yeah, always back up everything b4 I do something. I have learned that the hard way. 

Is that command to fix X or the scrolling problem? X is working so thats all good here. Just that dam scroll!! 

Thanks though!!!! :-)[/QUOTE]
 xserver-xorg also handles your mouse. xorg.conf is the configuration file of xserver-xorg that you can edit by hand or with the command sudo dpkg-reconfigure xserver-xorg. I prefer the command and edit the file manually only if I can't configure something using the command.

You have to restart xserver-xorg after I have editted your xorg.conf (by command or hand). I always go to init 1 and after this back to init 2.  like this :
sudo init 1

wait a little bit untill everything is closed and the system reports you have entered init 1

sudo init 2

---

### Post by radioact1ve on 2005-04-04
I have always edited xorg.conf like that as well. I like to read what Im doing. 

I didnt know about that init 1 and 2 thing though. Very helpful. thanks.

OK so I ran dpkg stuff and as I go through the process, one part dealt with buttons 4 and 5, or "scrolling" I got excited to soon as the end result was nothing. It still didn't wrok. Dam I feel so close. 

Its the same way I felt when I was about to get my wifi card working (which it is, finally).

---

### Post by grendelkhan on 2005-04-04
I must be the lone guy here, but my Synaptics pad, along with the verticle and hortizontal scroll button, all auto-detected right out of the box.  First distro that has ever happened with!

---

### Post by ubuntu_demon on 2005-04-04
[QUOTE=radioact1ve]I have always edited xorg.conf like that as well. I like to read what Im doing. 

I didnt know about that init 1 and 2 thing though. Very helpful. thanks.

OK so I ran dpkg stuff and as I go through the process, one part dealt with buttons 4 and 5, or "scrolling" I got excited to soon as the end result was nothing. It still didn't wrok. Dam I feel so close. 

Its the same way I felt when I was about to get my wifi card working (which it is, finally).[/QUOTE]
 In my experiences sudo dpkg-reconfigure xserver-xorg and after this editting xorg.conf manually if necessary is the best way to go

---

### Post by radioact1ve on 2005-04-04
[QUOTE=grendelkhan]I must be the lone guy here, but my Synaptics pad, along with the verticle and hortizontal scroll button, all auto-detected right out of the box.  First distro that has ever happened with![/QUOTE]
 Can I take a look at your xorg.conf? Maybe that could help.

thxs!

---

### Post by zabilcm on 2005-04-05
[QUOTE=radioact1ve]Hey all!

Yeah, sorry another Synaptics touchpad scrolling question. Vertical (dont care for horizontal) scrolling just wont work!

I have used VertScrollDelta, updownscrolling, and what not. I have followed all the HowTos on ubuntu wiki and the search the fourms like crazy. I do what work for other people but I just wont work here.  ](*,) 

Any other suggestions? Everything else on the toucpad works fine!

Thxs for your time!!

- Miguel[/QUOTE]

If you in  wary you need to install the "xfree86-synaptics" package. If you are in hoary "xorg-synaptics" packages

```
$ sudo apt-get install xorg-synaptics
```

Things worked for me after that.

---

