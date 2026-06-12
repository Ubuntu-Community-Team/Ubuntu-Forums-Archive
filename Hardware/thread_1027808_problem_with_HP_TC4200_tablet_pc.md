---
title: "problem with HP TC4200 tablet pc"
date: 2009-01-01
forum: Hardware
---

### Post by saplatok on 2009-01-01
Hello,
I'm a newbie and I want to install ubuntu (or another variant) on a TC4200. The touchscreen doesn't work with Hardy and partially work with Gutsy (the right-clic on the stylus doesn't work and i can't rotate the desktop).
How I can make all fully fonctionnal ?

Thank You

---

### Post by Favux on 2009-01-01
Hi saplatok,

Are you planning on installing Intrepid?  HAL (hardware abstraction layer) new to Intrepid should support your stylus "out of the box".  I don't know about the side button though.

Anything else will require you reverting to xorg.conf.  It is located in /etc/X11/.  It is not that difficult to configure.  There are a couple tutorials available for installing the linuxwacom drivers and wacom tablets.

So aside from stylus and side button, do you have eraser?  And are you sure the TC 4200 has touch?

It really isn't all that difficult.  So if you install, the next time you post mention what version of Ubuntu you're on and include your xorg.conf as an attachment.

---

### Post by peterlustig on 2009-01-02
Hi saplatok,

The TC4200 is working pretty well in Ubuntu 8.04, so you should install that. (I've tested 8.10 on a TC4200 when it appeared and turned back to 8.04 after a day of no success with the pen and no reason to run 8.10). 

[COLOR="Red"][EDIT: it seems to be quite easy to get everything up and running in 8.10 as Favux pointed out later in this thread (post 8 in this thread) - Thanks a lot!] [/COLOR] 

I found Ubuntu to be the most suitable distribution among the ones I've tested recently on the TC4200 (Suse, Mepis, Fedora, Ubuntu). The out-of-the-box hardware-functionality (pen/screen/buttons) is very similar. But after using Suse for 3 years, the "Synaptic Package-Manager" and the variety of software-packages let me switch to ubuntu. [edit: ... ubuntu 8.10 seems to work well with the tc4200check this out: [wacom-guide]("https://help.ubuntu.com/community/Wacom#Ubuntu%208.04%20(Hardy%20Heron)"), [wacom-troubleshooting]("https://help.ubuntu.com/community/WacomTroubleshooting")]

**Screen and pen/eraser/pen-button**
Screen and pen/eraser/pen-button do work in 8.04 but need some settings changed in the xorg.conf (see above post). All the wacom-driver sections need to be modified or added. The following section is adapted from a couple of tutorials (links below). This is all I do after a new Ubuntu 8.04 installation to make the TC4200 work decently.

[COLOR="Red"]Works with ubuntu 8.04 [/COLOR]

After a successful installation of ubuntu 8.04 (e.g. from a usb-stick or from an attached cd/dvd-drive)
enter in terminal (to get to terminal: Alt+F2 --> gnome-terminal --> return):

before we start a quick installation and a short check. copy and paste this into your terminal window:

Install procinfo:
```

sudo apt-get install procinfo

```
enter password and confirm if necessary.

check for wacom-module:
```

lsmod | grep wacom

```

You should get something like this in return:

$ lsmod | grep wacom
wacom                  18048  0 
usbcore               146412  4 wacom,ehci_hcd,uhci_hcd

If the output was similar, start editing the xorg.conf:
```

sudo gedit /etc/X11/xorg.conf

```

Now search for these sections and modify / add them:

/etc/X11/xorg.conf:
```

Section "InputDevice"
        Driver "wacom"
        Identifier "stylus"
        Option "Device" "/dev/input/wacom"    #seems to be the correct device for TC4200
#        Option "Device" "/dev/ttyS0"  #is for serial tablets only (uncommented for TC4200, whic is serial tablet)
        Option "Type" "stylus"
        Option "ForceDevice" "ISDV4"
        Option "button2" "3"
EndSection

Section "InputDevice"
        Driver "wacom"
        Identifier "eraser"
        Option "Device" "/dev/input/wacom"    #seems to be the correct device for TC4200
#        Option "Device" "/dev/ttyS0"         #is for serial tablets only (uncommented for TC4200, which is serial tablet)
        Option "Type" "eraser"
        Option "ForceDevice" "ISDV4"
EndSection

```

Add this to the section "ServerLayout" of xorg.conf:
/etc/X11/xorg.conf:
```

InputDevice "stylus" "SendCoreEvents"
InputDevice "eraser" "SendCoreEvents"

```

Save+quit
(You can find my xorg.conf as an attachment to this post. Yours should look something in between identical and similar.)

The screen + pen is working as pointing device and as pen in GIMP and xournal&co after restart of xserver (ctrl+alt+backspace).


[COLOR="Red"]That's it. All the rest is optional and deals mainly with rotating the screen by clicking a shortcut-icon[/COLOR]

**Rotate**
Rotation works with a script (xrandr / xsetwacom), but neither with any of the soft-buttons nor automatically by flipping the screen, since I didn't yet find a way to detect the specific specific signals for that.

Solution: 
a) clickable icon for rotation-command on desktop (easy and included)
b) assign a rotation-command to any mechanically operable key on the TC4200 (like the wireless-key) (use link [1])

This is a script that I adapted from somewhere.[edit: Favux has a better version without all the potentially unnecessary stuff like onboard and compiz, using an if clause instead of two files.]
Leave out the lines containing metacity and compiz in case you are not using those (for desktop-effects). onboard is an on-screen keyboard that you might find useful. To install onboard run this in a terminal:

```

sudo apt-get install onboard

```

**rotate**

To edit script in /usr/local/bin enter in terminal:

```

sudo gedit /usr/local/bin/rotate

```

/usr/local/bin/rotate:
```

#!/bin/bash
#metacity-workaround (remove if not in use)
metacity --replace &

#OnScreen Keyboard start
onboard &

#rotate screen
xrandr -o right

#rotate pen
xsetwacom set "stylus" Rotate CW
xsetwacom set "eraser" Rotate CW

exit 0

```

Save + quit

**unrotate**
In a terminal enter:

```

sudo gedit /usr/local/bin/unrotate

```


/usr/local/bin/unrotate:
```

#!/bin/bash

#unrotate screen (to landscape)
xrandr -o normal

#unrotate pen
xsetwacom set "stylus" Rotate none
xsetwacom set "eraser" Rotate none

#restart compiz (remove if not in use)
compiz --replace &

#wait for compiz

sleep 5
exit 0

```
Save + quit

Now modify rights and make it executable. Enter in terminal:

```

cd /usr/local/bin/ && sudo chmod 777 rotate && sudo chmod 777 unrotate

```

Create a "launcher"-icon on your desktop for each of these scripts

_rotate-launcher:_

right-click on desktop 
select "Create Launcher"

Type: Application
Name: rotate
Command: /usr/local/bin/rotate
Comment:

click OK to close

_unrotate-launcher:_

right-click on desktop
select "Create Launcher"

Type: Application
Name: rotate
Command: /usr/local/bin/unrotate
Comment:

click OK to close

Double-clicking the respective icon on the desktop should lead to the desired action.

**Wine**
MS Office 2007 works pretty well in wine, but you won't be able to use the pen in OneNote or use the formula-editor in word.
The are a couple of great tutorials for Office 2007 in wine. Otherwise I could post one.
Instead of OneNote you could you use xournal (sudo apt-get install xournal).
It is fairly easy to install Artrage (WindowsXP-Graphics software) in wine >1.0 (I could post a tutorial).

**PowerManagement**
Works. I haven't really tried getting "Suspend to Ram" and "Suspend to Disk" to work - they might even work out of the box.

**IR-Sensor**
The IR-sensor should work somehow, but not out of the box.

**Tutorials**
There are some great tutorials in this forum and elsewhere (specific for TC4200 + Linux). If you need any help, let me know.

**Links**
[1] [http://yergler.net/Ubuntu_on_tc4200](http://yergler.net/Ubuntu_on_tc4200) (deals with rotation as well)
[2] [http://www.ser1.net/Files/Reviews/HP4200/index.html](http://www.ser1.net/Files/Reviews/HP4200/index.html) (older, most of it is done automatically in ubuntu 8.04 - still worth reading)

This is the _full_ extend of modifications I do. I don't really miss the soft-buttons (the ones you can only press with the pen).


Good luck! 

Peter

PS: I'm pretty new to this as well. This is officially my first forum-post... shiver... that's why I kept editing this article for the last 5h.

---

### Post by Favux on 2009-01-04
Hi peterlustig,

Really nice job!  This is turning into quite the TC 4200 HOW TO.

I do have some questions about your xorg.conf.  The TC 4200 has a serial tablet doesn't it?  Or does it have a USB tablet?  It has stylus, side button and eraser, correct?  Does it have touch?

---

### Post by peterlustig on 2009-01-05
Hi Favux,
guilty as charged.
Thanks for looking at it in detail. You are right in both cases. What I wrote in the xorg.conf section is far from optimal.

a) The TC4200 does not have touch. 

I suppose you wonder why I added the pad section. I assume it's an I-don't -know-what-I'm-doing copy+paste artifact that occurred when I copy+pasted my xorg.conf from several sources some time ago. It's useless in this case and I'll delete it.

b) It seems to be a serial tablet... The USB-option is not necessary. I'll delete that as well. According to the wacom troubleshooting [guide]("https://help.ubuntu.com/community/WacomTroubleshooting") the xorg.conf should contain a device-option "ttyS0" for each of the wacom input devices. It seems to work without though.

Wow there is a lot of great documentation about how to configure wacom nowadays as I found out just now. When I first got the tablet a couple of years ago it was such a pain to find anything specific. After reading the wacom-guides [[1]("https://help.ubuntu.com/community/Wacom")], [[2]("https://help.ubuntu.com/community/WacomTroubleshooting")] I am beginning to understand what I was doing.

Thanks a lot for your help!

Peter

---

### Post by Favux on 2009-01-05
Hi peterlustig,

Again nice job!  Almost there.  Like "pad" the "cursor" is for an attachable graphics tablet and a tablet pc doesn't use it.  I gather it is for a seperate mouse the graphics tablets have.

Also serial tablets usually have:
```
	Option		"Device"	"/dev/ttyS0"	# SERIAL only
```
Now I know with some of the graphics tablets "wacom" works, so maybe on your tablet pc "ttyS0" is unnecessary.  Since you're getting "stylus" in 8.04 (without HAL) I guess it is.  Also it isn't always 0, it can be 1,2 or 3 also (I think).

In addition to a xorg.conf, I'm going to attach a rotation script for your perusal.

---

### Post by peterlustig on 2009-01-05
Hi Favux!
Thanks again. I have added the serial device option and removed the "cursor" from xorg.conf and the rotate scripts. Yours is pretty neat. Are you using compiz?

...I'm thinking about upgrading to ubuntu8.10, since (having read the wacom tutorials) it really doesn't seem to be a problem to get the tablet working. You seem to have 8.10 and a tc4200. May I ask whether you regret upgrading or notice any difference practically?

Thanks  :-)
Peter

---

### Post by Favux on 2009-01-05
Hi peterlustig,

Yes I'm using Compiz.  I have nVidia graphics.

I'm on a TX2000 in 8.10.  Fortunately I upgraded from Hardy otherwise my xorg.conf would have been empty, making things harder.  I got the tablet working easy enough.  Since I use gali98's tutorial:
[http://ubuntuforums.org/showthread.php?p=5469447#post5469447]("http://ubuntuforums.org/showthread.php?p=5469447#post5469447")
the module breaks every time the kernel is updated.  So you have to run through the tutorial again.  I'm on 0.8.2 (the latest).  Unfortunately gali98 hasn't posted in about 2 months, so I've adapted his tutorial (you can use his just sticking in 0.8.2 for 0.8.1-6) and simplified it.

The main problem for me in upgrading to Intrepid was loss of wireless.  Details here:
[http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")
Also Intrepid broke single key key binding.  So I lost my screen rotation button until I figure out how to fix it.  Actually its a screen bezel button I re-purposed into a rotation button.  But all in all I think Intrepid works better for me, the kernel seems more compatible with my machine.

At my rotation HOW TO I have some more scripts and stuff.  Also in the thread we talk about setting up some programs for eraser, etc.

[http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")


Have fun.

---

### Post by saplatok on 2009-01-05
Hi Favux, Hi Peterlustig,

Thank you both ! I have now intrepid with peterlustig's xorg.conf. First it did not work so I have installed new packages : [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)
I also use the script for the rotation.

Ihave two questions : how can I modified the script in order to have a rotation to the left and a rotation upside-down too ? How to use the eraser in Gimp ?


Thank you again for your help !

---

### Post by Favux on 2009-01-05
Hi saplatok,

Good deal!  Glad you now have a working tablet.

On the rotation scripts.  Do you want a separate one for each?  Or do you want a script that will rotate 360 degrees?  Clockwise or counterclockwise?  To help me with the script could you type in a terminal:
```
xrandr -q --verbose

```
and upload the output as an attachment.

To get info on how to use the eraser in Gimp follow the thread link I posted above to the Rotation HOW TO a few posts in.

---

### Post by saplatok on 2009-01-05
Ok thank you. I join the output.
I'd like two scripts : one just to rotate to the left (90 degrees counterclockwise) and the other that will rotate 360 degrees counterclockwise.

---

### Post by Favux on 2009-01-06
Hi again saplatok,

Ok, the xrandr output was very helpful.  Based on it you should be able to use method 1 at my Rotation HOW TO to get what you want.  The first script in method 1 should give you the 360 degrees counterclockwise and the third script (left handed) in method 1 should give the other script you need.  Please find them at:

[http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")

Let me know if they work for you.

---

### Post by peterlustig on 2009-01-07
Hi Favux,
thanks a lot for the detailed information on upgrading the tablet to 8.10. That was really helpful.

I've looked at the rotation tutorial. - Brilliant work, great detail! Thanks.
That should do it for saplatok.

---

### Post by peterlustig on 2009-01-07
Hi saplatok
I think Favux has extensively covered the rotation-part with his tutorial.
No idea about the eraser in gimp, sorry. - I'm using the stylus instead.

Good luck!
Peter

---

### Post by Favux on 2009-01-07
Hi peterlustig,

Your HOW TO keeps getting better and better as you polish it!  I think you should keep it up.  Maybe start a new thread with the HOW TO the first post and appropriate title.  If you have the time and inclination you could then steer TC4200 (and maybe TC4400) users to it.  You could also go to the laptop testers wiki and put your results up on it if you wanted.

One final question.  In you xorg.conf you have:
```
        Option "Device" "/dev/input/wacom"
        Option "Device"	"/dev/ttyS0"  

```
It seems to me it should be one or the other.  Like:
```
#        Option "Device" "/dev/input/wacom"
        Option "Device"	"/dev/ttyS0"  

```
or
```
        Option "Device" "/dev/input/wacom"
#        Option "Device"	"/dev/ttyS0"  

```
You'll know when you have the right one when you get eraser working in Gimp or Inkscape.  Check post #8 in my Rotation HOW TO.

Hi saplatok,

Did the method 1 rotation scripts work for you?  I'd love to know because then I could add to the HOW TO that the method works for TC4200 serial tablet also.

---

### Post by dkeats on 2009-01-08
What do you do if the output of lsmod | grep wacom is blank?
I have installed Intrepid on a tc4400 and have neither tablet nor wireless, both of which were working in Hardy. When I do lsmod | grep wacom I just get a blank result. Any suggestions? thanks, derek

---

### Post by Favux on 2009-01-08
Hi dkeats,

It sounds like you do not have the linuxwacom drivers installed.  Use the links on peterlustig's HOW TO (post #3) or saplatok's post #9.  They should take you to Loic2's Wacom wiki.  Try the various ways the wiki instructs you to install them.  In the meantime why don't you upload your xorg.conf  as an attachment.

---

### Post by peterlustig on 2009-01-09
Hi Favux,
thanks again for the corrections. I should have test-run the script or at least have taken care when copy&pasting. The how to is updated.

I won't have the time to move the thread or the wiki or the like. It's a good idea though.

All the best!
Peter

---

### Post by saplatok on 2009-01-09
Hello everybody,
Thank for your posts. I'm sorry, I can't try the scripts now but I will post when it's done.

dkeats if you have installed the drivers and still have nothing after : lsmod | grep wacom

Try : sudo su modprobe wacom 
close you session, open your session again then enter: lsmod | grep wacom
It should work now.

---

### Post by Mig Daddy on 2009-03-20
It is my understanding that Ubuntu Studio has built in tablet support.  Has anyone tried this?

---

### Post by saplatok on 2009-04-30
Hello everebody,

Thank you and sorry for answering so late. The scripts work well for the TC4200 when no applications are running. Sometimes when some applications run in the same times it crashes. 
I have installed Jaunty to see if it's better. The stylus works out of the box, but the button on the stylus is no more a right-clic but a middle-clic, and the rotation scripts don't work anymore.

---

### Post by Favux on 2009-04-30
Hi saplatok,

Jaunty has a problem with the callout from the wacom.fdi.  It returns HAL names that linuxwacom doesn't recognize, that's why xsetwacom (rotation) and wacomcpl doesn't work.  You should be able to map your stylus button once you get wacomcpl to work.

While we are waiting for a fix there are three work arounds.  One is a script by rec that translates the HAL names.  Another reverts to xorg.conf instead of Jaunty's HAL/.fdi method.  Both are discussed in Jaunty Users near the top here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  Since you have a serial tablet all you need is rec's script (called wacomtoHAL) and then use section 3 below to calibrate with wacomcpl.  You can ignore the other stuff.

The other way is to use:
```
xinput --list
```
to return the names HAL is using and then rename the wacom stuff appropriately.

---

### Post by saplatok on 2009-04-30
Hi Favux,
Thanks a lot, I used the script and it works now. Just a problem : if I rotate the screen and after put my computer in hibernate mode, when I restart there is a problem with the cursor which not follow exactly the stylus anymore. To solve that I have to quit the session and after that it's OK.
Another question: there are three buttons on the side of the screen that are made to be activated by the stylus and another button (which look like a thumb wheel), I don't know how to use it. Can you tell me if it's possible to get it work ?


Thank you

---

### Post by Favux on 2009-04-30
Hi saplatok,

We are working on the suspend/hibernate thing right now.  I'll let you know if we come up with anything.

We've got the same problem.  We got 2/4 of our bezel buttons to work.  In a terminal you type xev.  A gui pops up and then you press a button.  You are looking for something like "keycode=154"  in the output it spews out.  Repeat for each button.  Hopefully it will return at least a few keycodes.  Otherwise MisteR thinks the other buttons and swivel hinge are controlled by a kernel module called HP-WMI and he posted a launchpad bug on it.

---

### Post by saplatok on 2009-05-01
Hi Favux,

I tried xev but it doesn't work for these buttons. I will wait for that. The most important was the rotation so thank you again.

---

### Post by Favux on 2009-05-01
Hi saplatok,

Breaking news!  MisteR2 got in touch with Matthew Garrett who maintains HP-WMI.  It turns out the swivel hinge signal was part of the docking station signal and Matthew Garrett has now seperated them out.  MisteR2 is going to put up a makefile for 2.6.30 and then for 2.6.28.  I haven't yet had a chance to ask if this will do anything for the non-functioning bezel buttons.  It will be great if this works.  I hope the "fixed" module will work for you too.  I'll have to ask.

---

### Post by saplatok on 2009-05-01
Great, I hope it will work !

---

### Post by Favux on 2009-05-02
Hi saplatok,

It's up.  MisteR2 doesn't know if it will work for you but he thinks it's worth a try.  Post #106 here:  [http://ubuntuforums.org/showthread.php?t=996830&page=11](http://ubuntuforums.org/showthread.php?t=996830&page=11)  It's probably still a no go on the buttons.  But now that we know where the signal is who knows.

---

### Post by saplatok on 2009-05-12
Hello Favux,
Thank you for your help but it's a little bit complicated for me. MisterR2 said "**REMEMBER!!** Apply the attached patch to 2.6.30-rc sourced hp-wmi. I used 2.6.30-rc2." 
I don't know exactcly what to do, so if i understand well I have to modify the kernel first ?

I think I will wait for something easier.

---

### Post by jepense on 2009-06-25
Hi,

I've just installed ubuntu 9.04 on my tc4200, and tried the rotate scripts above.  They do rotate the screen successfully, but then the pen calibration is off.  I have to move the pen one direction physically in order to get it to move in a direction 90 degrees rotated from that on the screen.  Very confusing.  I'm new to all this, so I'm looking for a fix that's not too in-depth.  Can anyone shed some light on this?

Thanks

---

### Post by Favux on 2009-06-25
Hi jepense,

Welcome to Ubuntu!

The 90 degree calibration thing is what saplatok and I were talking about in post #22 above.

To see what we were discussing in a terminal enter (copy and paste):
```
xsetwacom list
```
That should return your wacom input devices names like stylus and eraser.  If it is blank then the xsetwacom commands (rotation) and wacomcpl won't work.

To see the names HAL (hardware abstraction layer) returns enter in a terminal:
```
xinput --list
```
To open a terminal you can go Applications>Accesories>Terminal.

So probably the easiest thing for you to do is follow the link to Jaunty Users and read that.  And then maybe install rec's script (now called wacom-names) like saplatok did.  Rotation should then work as should wacomcpl.

Good luck!

---

