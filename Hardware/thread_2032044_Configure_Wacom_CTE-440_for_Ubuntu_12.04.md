---
title: "Configure Wacom CTE-440 for Ubuntu 12.04"
date: 2012-07-23
forum: Hardware
---

### Post by koosfoto.hu on 2012-07-23
Greetings!

I am running on Ubuntu 12.04 and have a Wacom CTE-440.
The system has recognised the Wacom and I made some configutaions in Gimp.

However, there are some further things I would like to use:

The eraser - when the other end of the stylus is used
How can I make it work as an eraser? (Now it is the same for both ends)

On the tablet itself there are two buttons and a wheel. 
How can they be configured to be used?

Thanks,

Tamas

---

### Post by Favux on 2012-07-23
Hi koosfoto.hu,

In Gimp point the eraser end of the pen to the little pink eraser icon on the tool palette to the left.  When the eraser tool is assigned to the eraser test it by erasing something in the drawing window.  If it works hit Save at the bottom of the tool palette.

For the two buttons and wheel see:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#Graphire4](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration#Graphire4)

---

### Post by koosfoto.hu on 2012-07-23
Thanks, Favux!

It was quick... and useful. 
The eraser works now find. :)

However, I tried to enter the lines in the terminal for the buttons and for the wheel... nothing happened. 

In the Ubuntu settings, there is a Wacom Graphics Tablet... and there is a button saying: +Map Buttons..." When I go there I see an empty field 
Would it be possible, that I should put THERE the assignements?

Thanks,

Tamas

---

### Post by Favux on 2012-07-23
The reason the Wacom tablet applet is blank is a data file for your tablet hasn't been added to libwacom/data yet.

I'd need some questions answered to write one.

First we should try to get the buttons working.

I would expect something like:
```
xsetwacom set "Wacom BambooFun 4x5 pad" Button 1 "key esc"
xsetwacom set "Wacom BambooFun 4x5 pad" AbsWheelDown "key minus"  # zoom out
xsetwacom set "Wacom BambooFun 4x5 pad" AbsWheelUp "key plus"  # zoom in
xsetwacom set "Wacom BambooFun 4x5 pad" Button 2 "key F12 "

```
But your device name will be different.  In a terminal run the command:
```
xinput list
```
and post the output.

---

### Post by koosfoto.hu on 2012-07-23
Thanks.

Here it is the list:

```
 xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 4x5 stylus              	id=14	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 4x5 eraser              	id=15	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 4x5 cursor              	id=16	[slave  pointer  (2)]
&#9116;   &#8627; Wacom Graphire4 4x5 pad                 	id=17	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB2.0 UVC VGA WebCam                   	id=10	[slave  keyboard (3)]
    &#8627; Eee PC WMI hotkeys                      	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]
```


Greetings,

T.

---

### Post by Favux on 2012-07-23
Hi Tamas,

OK, this should work then:
```
xsetwacom set "Wacom Graphire4 4x5 pad" Button 1 "key esc"
xsetwacom set "Wacom Graphire4 4x5 pad" RelWheelDown "key minus"  # zoom out
xsetwacom set "Wacom Graphire4 4x5 pad" RelWheelDown "key plus"  # zoom in
xsetwacom set "Wacom Graphire4 4x5 pad" Button 2 "key ctrl z"  # Undo
```
I don't know of any reason why Button 1 and 2 should have different assignments.  It is possible RelWheel is now suppose to be AbsWheel so if RelWheel doesn't work change it and let me know.

You can check for assignment with the **get** command, for example:
```
xsetwacom get "Wacom Graphire4 4x5 pad" Button 1
```
For the data file I need the output of the **lsusb** command in a terminal.  The line with Wacom in it especially.

I was wrong and the data file for your model appears to be in libwacom.  So you should be able to make button assignments in the Wacom Tablet app.  But the xsetwacom commands should work also.  This is the graphire4-4x5.tablet data file:
```
# Wacom
# Graphire4 4x5
# CTE-440
#
# Button Map:
# (A=1, B=2, C=3, ...)
#
#               AA  BB
#      *----------------------*
#      |                      |
#      |                      |
#      |                      |
#      |        TABLET        |
#      |                      |
#      |                      |
#      |                      |
#      *----------------------*
#
[Device]
Name=Wacom Graphire4 4x5
DeviceMatch=usb:056a:0015
Class=Graphire
Width=5
Height=4

[Features]
Stylus=true
Buttons=2

[Buttons]
Top=A;B
```
Does the wheel do anything by default?  Scroll?

---

### Post by koosfoto.hu on 2012-07-24
So, here it is the lsusb:

```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 13d3:5111 IMC Networks Integrated Webcam
Bus 003 Device 002: ID 056a:0015 Wacom Co., Ltd Graphire 4 4x5
```

The answer to 
```
xsetwacom get "Wacom Graphire4 4x5 pad" Button 1
1
```

So, where exactly should I put the assignment data? In a file? If yes, where, in which folder and with what filename?

For the time being the 2 buttons and the wheel do just nothing at all.

Thanks a lot for all...

T.

---

### Post by Favux on 2012-07-24
You should be able to do it using the Wacom Tablet app. in System Settings.  Or the xsetwacom commands, which you can set up in a xsetwacom.sh script file if you wanted to.

Right now you have the default version of xf86-input-wacom that comes with Precise, which is version 0.14.0.  To determine your version run the following command in a terminal:
```
xsetwacom -V
```
Version 0.14.0 has at least one bug with the Graphire pad, the scroll wheel, that was fixed:  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=bef544bef0be59f9fdff9231ce85cd41e4149975](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=commit;h=bef544bef0be59f9fdff9231ce85cd41e4149975)  This means you will want to update to at least the xf86-input-wacom-0.16.0 tar or else clone the xf86-input-wacom git repository.  Which of course means RelWheel is correct for the xsetwacom commands.

Instructions are available on [http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)  or  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949).  Please ask if you have questions.

---

### Post by koosfoto.hu on 2012-07-28
(I was away for some days... Here I am now again)

Thanks... I am lost a bit.

Where is, or where should I put the xsetwacom.sh script file?
(I did not find it in my system...)

Yes, xsetwacom -V gives 0.14.0!


So, what and how to???? 


Greetings,

Tamas

---

### Post by Favux on 2012-07-28
Hi Tamas,

First you need to update your Wacom X driver, xf86-input-wacom, to at least version 0.16.0.  I gave you links to two HOW TOs that give you instructions on how to compile it.  For example on the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") it is in "II. Install Xorg's xf86-input-wacom tar or clone the git repository for Lucid, Maverick, Natty, & Oneiric (the X driver)" part "a) Now compile the xf86-input-wacom tar".  Just change the 0.15.0 to 0.16.0.

Then you create a xsetwacom.sh script if you want/need to.  The BambooPT HOW TO shows you that also.  I suggest creating a /bin directory in /home/username, if you don't have one, and placing the script there.

---

### Post by albertnet on 2012-09-05
Hi Favux, I own a Wacom Bamboo CTH-470 (just bought it :)) and after playing around and trying to configure it, I found myself with this same scenario, in which it's a blank space when I hit the "Map Buttons" under the Systems Settings/"Wacom Graphics Tablet". Even though it's nice to have a GUI for such matter, I don't mind using my old reliable command line, in fact I have been quite succesful at it.
After reading lots and lots of threads, guides and such, I've come to realize that you are impresively active in helping others and have become some sort of wacom tablets linux configuring Guru! :lolflag:
So, my question is that I'd like to map the 4 buttons in my tablet but I don't know what is the meaning of the numbers, this is, if I input: 

```
xsetwacom --get "Wacom Bamboo 16FG 4x5 Finger pad" Button 2
```

I get the number 2 as an answer, then I remapped it to:

```
xsetwacom --set "Wacom Bamboo 16FG 4x5 Finger pad" Button 2 5
```
and the answer is : button +5.
This made the second button to click a "forward page" in firefox.

So, do you might be able to know what does each number means or where can I find such info? Also, if I'd like to emulate with a click the scroll as in my Logitech Trackman Marble, How can it be done or what command should it be?

Thank you!

Albertnet

---

### Post by Favux on 2012-09-05
Hi albertnet,

The information you are looking for is in part V. of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").
> Also, if I'd like to emulate with a click the scroll as in my Logitech Trackman Marble, How can it be done or what command should it be?
Do you mean with a pad or a stylus button?  Either way you can't get true scroll because both give a button press and release.  But part V. also gives you the scroll integers 4-7.  You could assign a pad button to Prior (page up) and another to Next (page down) but that isn't true scroll.  Your best bet is probably to use EasyStroke.  I'm pretty sure its website wiki showed how to set up a scroll gesture as one of the examples.  Or why not use the Capture's scroll touch gesture?

---

