---
title: "HP tx2000 tablet won't function, 8.10 (Intrepid Bipex)"
date: 2008-12-08
forum: Hardware
---

### Post by murderslastcrow on 2008-12-08
Okay, first of all, I'm an intermediate linux user, only ever used Ubuntu, and I've looked for two weeks at every thread I could find on the internet and in these forums.

The basic issue is that I can't get the digitizer built into my screen (my serial tablet) to react. At all. Never done ANYthing, never detected any third party drivers, anything.

Now, what I have tried is all the linuxwacom drivers, different versions with different configurations. The huge thread that was tailored to 8.10 users didn't do a thing after two days of frustration, which is pretty depressing. Again, this laptop is fairly new- got it this summer.

I've also configured the xorg.conf, although it may not be necessary in 8.10, after all I mentioned above, and still absolutely no change. So really, I'm getting to the end of my rope. Is my tablet pc even compatible with linux? Is there any way I can diagnose my issue beyond reading FAQs and tutorials so I can figure out just what's missing?

Sorry for the vagueness of my request, but it's been very hectic. I'll be glad to give you any information or logs you want to see- I've had to reset and reconfigure my setup with each new method. I just feel like there must be a simpler way to install and configure these drivers, like I'm missing something really obvious.

---

### Post by jkorp on 2008-12-08
Same thing happened to me. Nothing happened when using the stylus. Two weeks ago I did get it to work though, with good help of the following thread:
[http://ubuntuforums.org/showthread.php?p=5469447#post5469447]("http://ubuntuforums.org/showthread.php?p=5469447#post5469447")

It didn't behave as the how-to said. After rebooting, it should be possible to move the pointer with the stylus, but nothing happened no matter how many times I rebooted. So I simply pasted in some code into my xorg.conf from the post - and voila! It worked!

But now, when I should reply on this post and tested the stylus again, it did not work... Any hints anyone? I have made the suggested updates (alot the last few days), so that might have broken something?

---

### Post by murderslastcrow on 2008-12-08
Pasted the code, both from scratch and as a copy of the xorg.txt file in the post. I had to reset the drivers and update again and still no reaction. Anyone else have an idea as to what the issue may be? I still have a current version of the driver source to work with.

---

### Post by Favux on 2008-12-11
Hi murderslastcrow and jkorp,

jkorp, everytime you update the linux kernel it breaks the linuxwacom driver and you have to run through the gali98 tutorial you reference again.  My advice is don't allow automatic install, so you can choose if you want the new kernel, and have to go through the tutorial again.

To begin with let's make sure we are all starting at the same place.  Intrepid 8.10?  AMD 64-bit Intrepid?  What are your TX2000's model numbers?  You have to follow gali98's tutorial exactly, installing linuxwacom development driver 0.8.1-6.  Also my advice is do not type in the tutorial's commands.  Copy and paste them in your terminal.  Please post your xorg.conf's.

I'm beginning to get an idea of what's been happening.  I followed the turorial, installing linuxwacom development driver 0.8.1-5 in 8.04 Hardy Heron.  This results in an xorg.conf filled with linux wacom project stuff.  But in Intrepid Ubuntu switched to HAL (hardware abstraction layer).  I'm beginning to think if you have an Intrepid install (and never installed on Hardy or earlier) none of the wacom stuff is added into xorg.conf.  There is suppose to be a fdo file that lets you use your stylus, but it did not work for me.  Additionally HAL can't support the eraser and touch.  So us tablet users have to revert back to xorg.conf.

If so no big deal, you can use my xorg.conf, and I have some sample TX2500 xorg.conf's also.  Or I suppose you could install Hardy, run through the tutorial and then update to Intrepid.  HAL will comment out all your wacom xorg.conf stuff, but you can remove the comments.

---

### Post by murderslastcrow on 2008-12-12
Thanks for the information! That definitely helps clear up some of what I was a tad confused with. I'm going to research a little bit more of the linuxwacom site over the next few days (just for the heck of it), and probably redo the tutorial, disabling the 'HAL' update on the kernel while I tinker with it.

I'll try that before I ask for your xorg.conf files. Thanks again for clearing things up a bit. I'm seeing this as an ongoing issue mostly for 8.10 users everywhere I've looked.

*will return*

---

### Post by M42 on 2008-12-12
Favux, 
I believe you are correct regarding a new install of Intrepid.  I had my TX2000 tablet working fine in 8.04 using gali98's tutorial but when I did a new install of Intrepid HAL did not include the xorg.conf information that is need to make the stylus and eraser work correctly.  I commented out the HAL stuff and inserted the old xorg.conf information and everything is working fine.  I just re-run the tutorial if I update the kernel.  I'm using the 32 bit Intrepid

---

### Post by Favux on 2008-12-12
Thanks M42,

I appreciate the confirmation.  This explains the rash of TX2500 posters with "naked" xorg.conf's.  At first I had wondered if if had something to do with the ATI video.  Instead it is the newer machine and so more likely to only have an Intrepid install.  And HAL is blocking any new xorg.conf configurations.

But this is the worst Ubuntu can do to us tablet users isn't it?  I mean xorg.conf says it in its name, it's the X org.'s configuration file.  In other words, since Ubuntu uses Xserver then we'll always be able to configure our tablet through xorg.conf, won't we?  Or maybe they'll have found a way around HAL's limitation of one input per usb and magically our tablets will be supported "out of the box".  You can tell I'm a dreamer.

It will be interesting to see if murderslastcrow can get a populated xorg.conf by disabling HAL in the kernel.  If so maybe gali98 will have to add it to the tutorial.

I hope he reports back.

---

### Post by yurtboy on 2008-12-12
subscribing to post...
Is there a wiki area where all the how to's to optimize this device are kept?
thanks

---

### Post by Favux on 2008-12-12
Hi yurtboy,

Sorry, as far a I know there is no consolidated area.  The wiki has wacom tablet stuff, a little outdated last time I checked.  A couple folk have wished gali98 would turn his tutorial into a wiki.  I think we are lucky he did the tutorial at all.  What I'll do for you is supply some links.  Hope these help.

gali 98's wacom tutorial:
   [http://ubuntuforums.org/showthread.php?p=5469447#post5469447]("http://ubuntuforums.org/showthread.php?p=5469447#post5469447")

mirosol's original TX2000 install tutorial:
   [http://mirosol.kapsi.fi/tx2020/tx2000howto.htm]("http://mirosol.kapsi.fi/tx2020/tx2000howto.htm")

siennalizard's HOW TO for TX2000:
   [http://ubuntuforums.org/showthread.php?t=837657&highlight=tx2000]("http://ubuntuforums.org/showthread.php?t=837657&highlight=tx2000")

G_man's TX2000 HOW TO:
   [http://georgia.ubuntuforums.org/showthread.php?t=792669]("http://georgia.ubuntuforums.org/showthread.php?t=792669")

I don't remember a consolidated HOW TO for the TX2500, but there are a couple big threads that have most of the info. if you're willing to go through them like:
   [http://ubuntuforums.org/showthread.php?t=845911&highlight=tx2000%2Bintrepid]("http://ubuntuforums.org/showthread.php?t=845911&highlight=tx2000%2Bintrepid")

and my Rotation HOW TO:
   [http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")

---

### Post by murderslastcrow on 2008-12-13
K,uninstalled all of the wacom stuff and made sure there was no xsetwacom or any wacom references in the xorg.conf file.

I then disabled HAL, but still not sure if I needed to do anything extra for fdi files.

So here's how it went:

After copying the src/2.26.7 version of wacom.ko to the input/tablet directory and restarting several times, got no response from the stylus/digitizer.

Upon following the tutorial thenafter,

"./configure --enable-wacom --prefix=/usr

make

sudo make install

sudo rmmod wacom

sudo modprobe wacom"

I received the following errors.

"checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
configure: error: source directory already configured; run "make distclean" there first"

Of course, at this point, xorg.conf still had no modifications from the default.

So I uninstalled, reinstalled again, and used the latest (linuxwacom-0.8.2), with the exact same results. No reactivity.

So I continued to edit the xorg.conf.
I didn't have anything that identified the "ServerLayout," so I pasted it in at the end like the example on the tutorial post. A lot of the options seemed to refer to a lot of synaptics in the xorg.txt from the post, but I didn't have anything but a monitor and graphics card in my xorg.conf. I pasted the pieces, anyway. Could this be related to HAL and Intrepid's new way of managing these drivers, or is there just nothing being detected at all?

The next code I put in got resulsts nothing like the tutorial.
"jack@jack-lappeh:~$ dmesg | grep Wacom
[  244.561430] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver"
Then the event results gave me the same as the tutorial, being on a 2000
(&#65279;pci-0000:00:0b.1-usb-0:2.3:1.1-eventmouse/event-).
So, I restarted the Xserver which caused me to go into low graphics mode. I didn't reconfigure the graphics so xorg.conf wouldn't revert to a previous state or be modified. There were no visible changes to the file.

I opened the wacom control panel, anyway, where I found nothing to choose from, so I exited.

So, I decided to replace my xorg.conf entirely with the one provided in the post, restarted the xserver again. Still nothing, with a low graphics mode again.

Thanks for getting this far and reading all the details. Looks like this is still a dead end for me.

---

### Post by Favux on 2008-12-13
Hi murderslastcrow,

Wow!  I can feel your frustration through the screen.

Too many variables.  Let's trim some.

First do you have a functioning tablet when you boot in Vista?  Everything works fine?

I have seen plenty of posts from folks with TX2500s saying they have full tablet functionality.  They followed gali98's tutorial and installed linuxwacom development driver 0.8.1-6 on kernel 2.6.27-7 or 2.6.27-9 or 2.6.27-10.  I have yet to see a post saying they have the tablet working on linuxwacom driver 0.8.2.  So let's forget it for now, better yet purge it off the system.  You still haven't posted your kernel:
```
uname -r
```
You're right, the empty xorg.conf may be, probably is, due to HAL.  This despite your disabling it.  I suppose it's even possible you have successfully installed the wacom kernel module and not even recognized it because your xorg.conf was not configured.  I am attaching the xorg.conf of a TX2500 that has functioning Wacom.  Back up your xorg.conf, keep a copy of the downloaded xorg.conf and replace your xorg.conf with it.  Let's get this working first.

This forces us to take a detour re video.  I don't know which video driver you are using.  ATI's "flgrx" does not support rotation.  I worked with a couple TX2500 users to confirm this.  You have to use Xorg's "radeon" driver which does support rotation.  This xorg.conf is configured for "radeon" (you can see flgrx commented out).  Some of the ATI guys say that when they go to System>Administration>Hardware Drivers to deactivate "flgrx" their system (X) crashes.  This shouldn't happen, but it does.  Be prepared.  When you restart hopefully "radeon" will be running.

In summary let's get you set up with a properly configured xorg.conf and video driver before running through the tutorial again.

I know you were desperate to try something new but let's forget linuxwacom 0.8.2 for now.  I know gali98 hasn't updated the tutorial since 11-3-08.  He's not posted for two or three weeks.

---

### Post by Favux on 2008-12-13
Oops!  Attachment didn't attach.  Try again.

---

### Post by murderslastcrow on 2008-12-14
Oh, forgot to mention, my kernel is 2.6.27-9-generic.

I replaced my xorg.conf with the tx2500 one provided, restarted, and I was in a high-graphic driver mode. I'd been using third-party nVidia 177 drivers, but they appear to be disabled now inside Administration\Hardware Drivers.

So, removing the linuxwacom stuff altogether- completed. Also, everything worked out of the box with my Vista installation. Calibration, flicks, screen rotation. My tablet doesn't make use of an eraser or extra buttons- just a stylus on the digitized screen.

I'm guessing this still qualifies it as a USB rather than serial since I've seen a lot of posts referring to this series of tablet PCs being that way. Also, within hardware drivers I didn't see anything like radeon, but I'm not sure if I should.

So here's where I am, still no reactivity from the stylus (seeing as how nothing's installed).

---

### Post by Favux on 2008-12-14
Hi murderslastcrow,

Good, now you have a configured xorg.conf.  The Xorg "radeon" driver is OSS and apparently default for Ubuntu.  Not being proprietary it would not be in Hardware Drivers.  Check there and make sure the ATI proprietary driver "flgrx" is deactivated.

Either the TX2000 or the TX2500 supports stylus, eraser, stylus side button, and touch in Vista or Ubuntu.  The wacom tablet built into the laptop is a Wacom Graphire USB (not serial) with active digitizer.

Now you say you have an nVidia 177 video driver?  But you have a TX2500?  TX2500's have the ATI 3200 HD video chip, not nVidia.  I'm assuming this is some sort of typo on your part.  Look at the little plate on the bottom of your laptop.  What exact model does it say you have?  If you are a TX2000 you have the wrong xorg.conf and we need to change it.

Assuming you have a TX2500 let's proceed.  You now have a properly configured xorg.conf on a "clean" machine.  This time do not remove the wacom stuff from the xorg.conf.

Go through the gali 98 (11-3-08) tutorial doing all the stuff for Intrepid (8.10) using the linuxwacom development driver 0.8.1-6 (we use the development branch because linuxwacom just introduced usb functionality into the driver).  Follow it exactly!  I mean exactly!  Read carefully, make sure you understand, go slowly (I'm afraid you're frustrated enough to be impatient and rush through).  Do not type in the commands.  Copy them from the tutorial and paste them in the terminal.

Check the xorg.conf and make sure the wacom configuration stuff is still in there.  Check xorg.conf again after reboot.

Let's see what happens when you go through the final reboot.

---

### Post by murderslastcrow on 2008-12-14
Ah, did I type tx2500? XD Oh bullocks. It's most certainly a tx2000. And despite my current predicament, my overjoyed satisfaction with the operating system itself far outgrows the small frustration of the tablet not working.

So yes, I'll be patient, but I think that means I'll need a slightly different xorg.conf? Good to have some well-versed guys out here. Thank you for your patience.

---

### Post by Favux on 2008-12-14
Hi murderslastcrow,

Well that's good to straighten out.  Attached find my TX2110us xorg.conf.  You want the nVidia driver activated.  After you get my xorg.conf in place go to System>Administration>Hardware Drivers and activate the nVidia 177 video driver.  Reboot and make sure everything is good to go.  Then follow the tutorial as above.

Edit:  I reread the thread and TX2500 thing was my mistake.  Like I mentioned I was helping some TX2500's I got myself confused.  I should have been reading the title of the thread, right?  Oh well, not much harm, minimal foul.  Sorry.

---

### Post by murderslastcrow on 2008-12-14
Alright. Followed the tutorial and got to the part where you restart (just before checking xinitrc and taking the wacom references out of xorg.conf, which I didn't do since I'm keeping the file as-is, and it hasn't been formatted by HAL or anything else). So I restarted four times, still no response from the digitizer on any place from the screen. So I ran the 'enable wacom' test suggested in the tutorial and to leave the results. I used the code on the linuxwacom directory unzipped to my desktop earlier.

My results are attached. I'm going to be patient like the tutorial said. I hope it's appropriate to stay in this thread with the results. ^^; Thanks again for your help.

---

### Post by Favux on 2008-12-14
Hi murderslastcrow,

No stylus, no eraser, no touch?  After restart if no stylus, try restarting X and see what happens.  To restart X <ctrl><alt><backspace>.  When you type "wacomcpl" in a terminal and the gui pops up do you see stylus, eraser, touch?  When you click on one of them do options appear like calibrate?

Post the output of:
```
reset

dmesg | grep Wacom
```
Post the output of:
```
ls -l /dev/input/by-path
```

Post your .xinitrc from /home/user name/ (be sure to check show hidden files in View so you can see it).

Post your xinitrc from /etc/X11/xinit/ (be sure to distinguish them so I can tell which is which).

You are now using the TX2000 xorg.conf right?

---

### Post by murderslastcrow on 2008-12-14
I've been using the tx2000 xorg.conf from the get-go, yes. Resetting the X Server gives no response, either (no touch, no stylus, no eraser, on any segment of the screen). The wacom control panel only brings up "Select Device" with a greyed out drop-box, so I'm unable to make any selection since there are none. So the only option I have is to click the exit button.

For the 'reset dmesg' code I got the following, "[   38.344594] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver". For the 'ls -l' I got this.

"total 0
lrwxrwxrwx 1 root root 10 2008-12-14 12:02 pci-0000:00:0b.1-usb-0:2.1:1.0-event- -> ../event10
lrwxrwxrwx 1 root root  9 2008-12-14 12:02 pci-0000:00:0b.1-usb-0:2.3:1.0-event-mouse -> ../event2
lrwxrwxrwx 1 root root  9 2008-12-14 12:02 pci-0000:00:0b.1-usb-0:2.3:1.0-mouse -> ../mouse1
lrwxrwxrwx 1 root root  9 2008-12-14 12:02 platform-i8042-serio-0-event-kbd -> ../event1
lrwxrwxrwx 1 root root 10 2008-12-14 12:02 platform-i8042-serio-1-event-mouse -> ../event11
lrwxrwxrwx 1 root root  9 2008-12-14 12:02 platform-i8042-serio-1-mouse -> ../mouse2
lrwxrwxrwx 1 root root  9 2008-12-14 12:02 platform-pcspkr-event-spkr -> ../event3"

When I unhid files in my home/jack (username) folder, I couldn't find any files or folders referring to xinitrc, only Xauthority and xsessionerrors. I am attaching the  xinitrc file from the X11/xinit folder, however.

---

### Post by Favux on 2008-12-14
Hi murderslastcrow,

I think I see a problem.  Change your /etc/X11/xinit/xinitrc from:
```
!/bin/bash
# $Xorg: xinitrc.cpp,v 1.3 2000/08/17 19:54:30 cpqbld Exp $

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
. /etc/X11/Xsession
```
to:
```
!/bin/bash
# $Xorg: xinitrc.cpp,v 1.3 2000/08/17 19:54:30 cpqbld Exp $

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
#. /etc/X11/Xsession
```
In other words comment out the last line like I just did.  You probably have to go into terminal and sudo gedit etc. to change it.  Do that and reboot and see if anything happens.

---

### Post by murderslastcrow on 2008-12-14
Alright. Commented out the final line, restarted computer and restarted X Server. Still no extra files in the home/username folder, no changes to xorg.conf or xinitrc after the change, etc. Still nothing in the wacom control panel. So no changes, still no reactivity. Hrm.. *puts on his thinking cap*

---

### Post by Favux on 2008-12-14
Hi murderslastcrow,

Thinking cap is right.  I may be stumped, but I'm not quite ready to admit it.  I've slowly been going through your enablewacomtest.txt and comparing it to my output.  So far the only difference is that you are on 32-bit x86 and I am on 64-bit AMD.  Plus you've got some other output to look at which on first glance doesn't look right.

Since we're getting desperate I am going to upload my .xinitrc file for you to load into your system.  Place it in /home/user name/ and be sure to put the period in front ".xinitrc".  Right click on it and chose properties and in permissions make sure allow executing file as program is checked.  It should end up as a hidden file that you will only be able to see with view hidden files checked.  What is your exact model number?  TX2??? and any trailing letters?

Ok, it would not let me add it as an attachment, so you'll have to create the file yourself.
```
xsetwacom set stylus Suppress "2"
xsetwacom set stylus RawSample "4"
xsetwacom set stylus ClickForce "6"
xsetwacom set stylus PressCurve "0 0 100 100"
xsetwacom set eraser bottomy "16630"
xsetwacom set eraser bottomx "26416"
xsetwacom set eraser topy "-101"
xsetwacom set eraser topx "66"
xsetwacom set stylus bottomy "16630"
xsetwacom set stylus bottomx "26416"
xsetwacom set stylus topy "-101"
xsetwacom set stylus topx "66"
xsetwacom set touch bottomy "3916"
xsetwacom set touch bottomx "4021"
xsetwacom set touch topy "81"
xsetwacom set touch topx "122"
xsetwacom set stylus TPCButton "off"
xsetwacom set stylus Button3 "Button 3"
xsetwacom set stylus Button2 "Button 3"
xsetwacom set stylus Button1 "Button 1"
# run the primary system script
. /etc/X11/xinit/xinitrc
```
Then reboot and let us see what happens.

---

### Post by Favux on 2008-12-14
By output I mean:
for dmesg | grep Wacom you got:
```
"[ 38.344594] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver"
```
while I get:
```
~$ dmesg | grep Wacom
[   30.563774] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:0b.1/usb2/2-2/2-2.3/2-2.3:1.0/input/input11
[   30.620392] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:0b.1/usb2/2-2/2-2.3/2-2.3:1.1/input/input12
[   30.661218] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver

```
While for ls -l /dev/input/by-path you get:
```
"total 0
lrwxrwxrwx 1 root root 10 2008-12-14 12:02 pci-0000:00:0b.1-usb-0:2.1:1.0-event- -> ../event10
lrwxrwxrwx 1 root root 9 2008-12-14 12:02 pci-0000:00:0b.1-usb-0:2.3:1.0-event-mouse -> ../event2
lrwxrwxrwx 1 root root 9 2008-12-14 12:02 pci-0000:00:0b.1-usb-0:2.3:1.0-mouse -> ../mouse1
lrwxrwxrwx 1 root root 9 2008-12-14 12:02 platform-i8042-serio-0-event-kbd -> ../event1
lrwxrwxrwx 1 root root 10 2008-12-14 12:02 platform-i8042-serio-1-event-mouse -> ../event11
lrwxrwxrwx 1 root root 9 2008-12-14 12:02 platform-i8042-serio-1-mouse -> ../mouse2
lrwxrwxrwx 1 root root 9 2008-12-14 12:02 platform-pcspkr-event-spkr -> ../event3"
```
I get:
```
~$ ls -l /dev/input/by-path
total 0
lrwxrwxrwx 1 root root  9 2008-12-14 15:05 pci-0000:00:0b.1-usb-0:2.1:1.0-event- -> ../event9
lrwxrwxrwx 1 root root 10 2008-12-14 15:05 pci-0000:00:0b.1-usb-0:2.3:1.0-event-mouse -> ../event11
lrwxrwxrwx 1 root root  9 2008-12-14 15:05 pci-0000:00:0b.1-usb-0:2.3:1.0-mouse -> ../mouse2
lrwxrwxrwx 1 root root  9 2008-12-14 15:05 pci-0000:00:0b.1-usb-0:2.3:1.1- -> ../mouse3
lrwxrwxrwx 1 root root 10 2008-12-14 15:05 pci-0000:00:0b.1-usb-0:2.3:1.1-event- -> ../event12
lrwxrwxrwx 1 root root  9 2008-12-14 15:05 platform-i8042-serio-0-event-kbd -> ../event1
lrwxrwxrwx 1 root root 10 2008-12-14 15:05 platform-i8042-serio-1-event-mouse -> ../event10
lrwxrwxrwx 1 root root  9 2008-12-14 15:05 platform-i8042-serio-1-mouse -> ../mouse1
lrwxrwxrwx 1 root root  9 2008-12-14 15:05 platform-pcspkr-event-spkr -> ../event8

```

There seems to be no wacom tablet input that your system is recognizing!  Which figures since you don't get stylus, etc.  You swear your stylus and eraser and touch work in Vista?

---

### Post by Riverhed on 2008-12-14
Hey guys, I'm a new Linux/Ubuntu user with a tx2500 at my wits' end trying to get my stylus working. Waiting with baited breath to see what you can come up with, because I've been through every tutorial I can find (including gali98's), with no luck.

I wish I could offer some suggestions or insight, but instead I'm hoping you guys can magically find a solution. If you want to take a look at any config's or outputs, let me know.

Thanks,
Drew

---

### Post by murderslastcrow on 2008-12-14
Alright, I made the code into the .xinitrc file in my home/username/ directory like you asked. It was automatically hidden and I checked "allow running as an executable" after displaying hidden files.

Just for reference, the xinitrc in etc/X11/xinit/ doesn't have a dot before it, and remains completely uncommented as it was. I restarted once and everything is completely the same as before, no reactivity. Oh, and like I said earlier, I have an on-screen digitizer with a stylus. The stylus isn't electronic at all- in fact, I've used Nintendo DS styluses with it XD. So yeah, there isn't an eraser to be noticed. The only real hardware that can activate is the digitized screen and the screen rotation- everything else is without drivers. Just a little piece of plastic.

And yes, it always worked in Vista, never had any issues. I can do so much more with Linux, though, so I'd hate to go back just for that. I probably wouldn't even if this weren't fixable- just buy a bamboo tablet. XD But it sure would be nice to have the screen as it was. I'm sure that with time this will be a very simplified subject, since it is pretty recent at the moment.

Thanks for the files, anyway. Any more ideas?

---

### Post by murderslastcrow on 2008-12-14
Okay, this is hilarious.

So, I just called the manufacturer to verify my model number. I gave them all my information, along with my order number, etc. My order says it was a tx2000 model, along with the printing on the packaging. However, they said they sent a tx1000 with that order.

So I put in my product number online for the auto-detection wizard, and turns out the computer it a tx1000 (which might explain the lack of erasers and hardware pens).

=_= ; Utterly ridiculous. So yeah, apparently this is another issue altogether. *researches forums once more with this in mind* If you guys still have any ideas for how to make this model work, I'd be glad to know. Sorry for the mix up, especially for the people who've been spending their free time just trying to assist me. I can't believe they sent me the wrong computer.

---

### Post by murderslastcrow on 2008-12-14
[http://ubuntuforums.org/showthread.php?t=983773&highlight=tx1000+tablet](http://ubuntuforums.org/showthread.php?t=983773&highlight=tx1000+tablet)

That fixed it immediately. I'm so sorry for those of you who are still having this issue with the newest versions of the tablet. Thank you so much for your time! I wouldn't consider it useless, though- I did learn a few things about linux during the course of things, so I'm better off for it.

:3 Ubuntu rocks, hardcore. XD

---

### Post by DrakeGis on 2008-12-14
First of all, thanks to all of you for making sense of all the other posts on touchscreen/tablet.
I have an HP pavilion tx2500, AMD64, running Intrepid 64bits (kernel 2.6.27-9-generic). I followed your instructions, I un-installed the proprietary ATI drivers, ran the tutorial from gali98 (november 3rd--- [http://ohioloco.ubuntuforums.org/showpost.php?p=5469447&postcount=5](http://ohioloco.ubuntuforums.org/showpost.php?p=5469447&postcount=5) ), modify my /etc/X11/xinit/xinitrc and used the (for tx2500) /etc/X11/xorg.conf (both provided by Favux), and still nothing works. Every time I rebooted I did a lsmod and only after un-installing the ATI drivers wacom appeared in the answer. It seems that ATI prevents wacom to be loaded or something... which lead me to my first question: Would I have to choose between compiz and tablet functionality ?  (If so, that is really bad). 
 Here are outputs for
 dmesg | grep Wacom
[   18.048515] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:14.5/usb6/6-2/6-2:1.0/input/input10
[   18.292550] input: Wacom ISDv4 93 as /devices/pci0000:00/0000:00:14.5/usb6/6-2/6-2:1.1/input/input11
[   18.354005] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver


 ls -l /dev/input/by-path
total 0
lrwxrwxrwx 1 root root  9 2008-12-14 18:38 pci-0000:00:13.2-usb-0:2:1.0-event- -> ../event9
lrwxrwxrwx 1 root root 10 2008-12-14 18:38 pci-0000:00:14.5-usb-0:2:1.0-event-mouse -> ../event10
lrwxrwxrwx 1 root root  9 2008-12-14 18:38 pci-0000:00:14.5-usb-0:2:1.0-mouse -> ../mouse1
lrwxrwxrwx 1 root root  9 2008-12-14 18:38 pci-0000:00:14.5-usb-0:2:1.1- -> ../mouse2
lrwxrwxrwx 1 root root 10 2008-12-14 18:38 pci-0000:00:14.5-usb-0:2:1.1-event- -> ../event11
lrwxrwxrwx 1 root root  9 2008-12-14 18:38 platform-i8042-serio-0-event-kbd -> ../event1
lrwxrwxrwx 1 root root 10 2008-12-14 18:38 platform-i8042-serio-1-event-mouse -> ../event12
lrwxrwxrwx 1 root root  9 2008-12-14 18:38 platform-i8042-serio-1-mouse -> ../mouse3
lrwxrwxrwx 1 root root  9 2008-12-14 18:38 platform-pcspkr-event-spkr -> ../event8


Any ideas what is going on with this  that still doesn't work ? 
Thanks again.

---

### Post by Favux on 2008-12-14
Hi murderslastcrow,

Great!  Mystery solved.  That's why your input output's didn't look right.  By the way I finished going through your install and make outputs.  I couldn't find an error.  In fact towards the end yours installed a library mine didn't.  So I think you are loading a wacom kernel module.  But since you don't have a wacom tablet it isn't doing anything.  The next kernel upgrade will break the wacom driver anyway.

I noticed on Jaunty that touchpad support was a high priority item.  So with Jaunty the TX1000 may work out of the box.

Why don't you see if they will exchange the TX1000 for a TX2000?  It sounds like you wanted a TX2000 to begin with.

**murderslastcrow** could you please mark this thread **solved**.  It's in thread tools at the top of the posts.

---

### Post by Favux on 2008-12-14
Hi Riverhed and DrakeGis,

Since this is a solved thread, please join me at my Rotation HOW TO thread:

   [http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")

fbdelivers just got his TX2500 working using a TX2500 xorg.conf I posted him.  Read through the thread and we can get going.

Thanks.

---

### Post by tekrytor on 2008-12-16
Re: Would I have to choose between compiz and tablet functionality ?

I'm posting from my HP tx2500us running 64-bit Ubuntu 8.10 kernel 2.6.27-10-generic. I followed the gali98 tutorial on wacom tablet installation and had to install Compiz to get the rotation button working. The only thing I still need it the stylus/eraser/touch to also rotate with the display. I hope that answers your question.

tektytor

---

### Post by Riverhed on 2008-12-16
Well, my concern isn't so much rotating the screen. It's not something I do a whole lot anyway, though it would be nice to have because I want this to function as completely as possible. My main concern at this point is getting the stylus to work completely. Since my last post I've got touch working perfectly, and my stylus can right-click using the side button, and eraser seems to work (gets a response from the screen, but haven't tried it in an application yet). The problem I'm having is that when I touch the stylus to the screen it doesn't do anything, and in fact seems to bug out the input for a second (the cursor locks in place and stops following the stylus, but if I take the stylus away from the screen and put it back it follows again, or if I use the touch pad it works again).

I'm going to fool around with my xorg.conf and see if I can't get it to recognize the stylus touching the screen as a touch event, but I'm not terribly hopeful about that. Anyone have any other suggestions?

---

