---
title: "Wacom pointer stays put when hovering pen"
date: 2011-03-20
forum: Hardware
---

### Post by LancerNZ on 2011-03-20
I'm not sure when this happened, I suspect just now after a system update.

Basically, using my Wacom CTH-460/K under Ubuntu 10.04 is fine except that if I click something (like a menu) then my mouse stops (appears to freeze) working until I lift the pen well away from the drawing pad and lower it again somewhere else, at which point the mouse cursor jumps to the new area. This is very annoying in art packages as it tend to connect a painted line between the two spots.

Putting it simply, if I am painting something, when I lift my brush from the drawing pad, the mouse pointer stays put instead of following the floating movement of the touchpad pen around, until I touch the pad elsewhere, at which point it jumps, dragging paint along the way in a straight line.

I have also noticed that touch sensitivity (e.g. use your finger) is no longer working with the wacom tablet and Ubuntu.

Any ideas on how to fix this problem?

---

### Post by Favux on 2011-03-21
Hi LancerNZ,

It sounds like your tablet is no longer on the Wacom drivers but probably on the evdev driver.

To get it working you had to do something to update your wacom.ko, the usb kernel driver.  If it was a kernel update you may need to recompile the wacom.ko.

The other thing that seems to be happening to some folks is the 10-wacom.conf at /usr/lib/X11/xorg.conf.d seems to have been removed by an update for some reason.  So check for that first.

---

### Post by LancerNZ on 2011-03-21
Thanks for relying.

I'm not sure how to go about "update your wacom.ko, the usb kernel driver". I've started playing around with dangerous looking pages ([http://ubuntuforums.org/archive/index.php/t-1522070.html](http://ubuntuforums.org/archive/index.php/t-1522070.html) and [http://kishalmi.net/cms/node/90](http://kishalmi.net/cms/node/90)) but without success. They seem to be adding last minute "if you are using...." alterations all over the place and are really hard to follow.

The file /usr/lib/X11/xorg.conf.d/10-wacom.conf... **does not exist**, as you say.

I believe I used to get my tablet working with the instructions from here:
[http://frankgroeneveld.nl/2010/04/11/get-wacom-bamboo-fun-pen-working-in-ubuntu-lucid/](http://frankgroeneveld.nl/2010/04/11/get-wacom-bamboo-fun-pen-working-in-ubuntu-lucid/)

```
sudo add-apt-repository ppa:doctormo/wacom-plus
sudo apt-get update
sudo apt-get install wacom-dkms
```

But not anymore, as this results in...
```
wacom-dkms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

...so it looks like I'm stuck with the problem of my tablet not working.

I have a deadline I'm now not meeting; why does Ubuntu seem to annually break important things like Wacom / Nvidia drivers on kernel updates? I chose Linux because I wanted it to be "reliable".

If you can help me with some steps - please do.

---

### Post by Favux on 2011-03-21
Several folks seem to be having problems with Martin's PPA, I don't know why.  I don't think his original one had your model but he just updated it a week ago or so.  I'm not sure if yours is in it although it should be.  You have one of the 5 new models released in October 2010 it looks like.

Irie's PPA seems to be working for the newer models because he's using input-wacom.  See the link to his PPA just before part I. of the [Bamboo P & T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").

Remove Martin's PPA through Synaptic first otherwise the dkms stuff will interfere with putting in a new wacom.ko.

---

### Post by LancerNZ on 2011-03-21
I have downloaded linuxwacom-0.8.8-11.tar.bz2 from [http://cdnetworks-us-2.dl.sourceforge.net/project/linuxwacom/linuxwacom/0.8.8-10/linuxwacom-0.8.8-11.tar.bz2](http://cdnetworks-us-2.dl.sourceforge.net/project/linuxwacom/linuxwacom/0.8.8-10/linuxwacom-0.8.8-11.tar.bz2)

I untared this and performed...
```
./configure --enable-wacom
make
(sudo) make install
```
...or something to that effect. it told me

```
Your wacom.ko is available under 
    /home/lancer/Downloads/hardware/linuxwacom-0.8.8-11/src/2.6.30
```

According to **uname -r** I have kernel "2.6.32-30-generic"

So... I am now performing...

```
sudo cp /home/lancer/Downloads/hardware/linuxwacom-0.8.8-11/src/2.6.30/wacom.ko /lib/modules/2.6.32-30-generic/updates/dkms/wacom.ko

sudo cp /home/lancer/Downloads/hardware/linuxwacom-0.8.8-11/src/2.6.30/wacom.ko /lib/modules/2.6.32-28-generic/kernel/drivers/input/tablet/wacom.ko 
```

Unplugging the wacom tablet and performing **modprobe wacom** does not improve the performance in any way.

...so now a reboot... (fingers crossed)


P.S. What's a PPA and how do I remove Martin / David / Gloria's / Whoever's PPA?

---

### Post by LancerNZ on 2011-03-21
Update: After a reboot, no change. :(

Whoever "Martin" is, I'm not amused.

---

### Post by LancerNZ on 2011-03-21
Used Synaptic to unsinstall wacom-dkms
...reboot... (sudo) rmmod / modprobe... no difference

Used Synaptic to unsinstall xserver-xorg-input-wacom
...reboot... rmmmod / modprobe... no difference

Ubuntu stalled on restart a couple of times.

Should I put them back?

---

### Post by Favux on 2011-03-21
Uninstalling xserver-xorg-input-wacom uninstalls xserver-xorg-input-all and you need -all for xf86-input-wacom to work.

Quick review.  There are two drivers the wacom.ko which is the usb kernel driver and your model is not in the default Lucid wacom.ko.

Then there is the X driver from xf86-input-wacom, wacom_drv.so which is what the xserver-xorg-input-wacom package contains.  Reinstall that so you get -all back.  The default xf86-input-wacom in Lucid doesn't have your model either.

The quickest way to get it working would be IRIE's PPA.

Also please lets find out your exact tablet model, enter in a terminal:
```
lsusb
```
so we can get the product ID.

---

### Post by LancerNZ on 2011-03-21
):P Thanks for sticking with me on this!

I should probably mention that there are two lots of drivers I've tried to install (from the above)...

[LIST]
[*]linuxwacom-0.8.8-11.tar.bz2
[*]xf86-input-wacom-0.10.9.tar.bz2
[/LIST]
They aren't the same. The first tells me to install the second, saying it's correct for my version, but I don't know how to install the second.

Here's the command you asked for...

```
lancer@lancer-laptop:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:00cb Microsoft Corp. Basic Optical Mouse v2.0
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 005: ID 056a:00d1 Wacom Co., Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 003 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I just re-synapticed in both of those files - now rebooting.

---

### Post by Favux on 2011-03-21
OK, that's the original Bamboo Pen and Touch, the CTH460 which I have.

So all you need is linuxwacom-0.8.8-11 for the wacom.ko, the usb driver.  That's what your getting by compiling that.  It's trying to tell you you can use it for the wacom.ko but you need xf86-input-wacom for the X driver.  So part I.  If the dkms stuff is still installed it will prevent the new wacom.ko from going into place, but it should have removed when you uninstalled the PPA through Synaptic Package Manager.

Then you need to clone the xf86-input-wacom git repository to get the X driver.  Don't use the 0.10.9 tar, that has a know bug with the pad.  So part II.  Be sure to do the 1.8 macro part.

---

### Post by LancerNZ on 2011-03-21
Okay...

First up, last time I compiled wacom.ko, it stated there were now multiple versions - I'm wondering if I should tidy some up, although at this point, I can't see where they are...

```
lancer@lancer-laptop:~$ ls /lib/modules/2.6.32-28-generic/kernel/drivers/input/tablet/
acecad.ko  aiptek.ko  gtco.ko  kbtab.ko  wacom.ko
lancer@lancer-laptop:~$ ls /lib/modules/2.6.32-30-generic/updates/dkms/
nvidia-current.ko  wacom.ko
```

From here I am, through synaptic, reinstalling **xserver-xorg-input-wacom**, **xserver-xorg-inpt-all**, but uninstalling **wacom-dkms**

rebooting now... but then what? Not sure where **xf86-input-wacom git repository** is or how to use it.

---

### Post by Favux on 2011-03-21
Right, you need to remove the wacom.ko in the dkms directory.  So uninstalling the PPA didn't remove it?

Then do part I. and part II. of the Bamboo P&T HOW TO.  That's about 10-15 minutes first time through and it will work.  Part II. is cloning the git repository.

---

### Post by LancerNZ on 2011-03-21
**Part I.**

This part went reasonably well, but I noticed a "wrong version" claim and thought I should point it out...
On configure I was told...
```
Your wacom.ko is available under 
    /home/lancer/Downloads/hardware/wacom_try_again/linuxwacom-0.8.8-11/src/2.6.30

NOTE: the X driver in this package only supports Xorg servers older than 1.7.
          You are running a newer version. 
Please build the X driver from xf86-input-wacom.
The kernel driver provided in this package is independent of 
the X server version
```


On returning after a reboot, there is nothing in **lsmod | grep wacom** until I plug the tablet in. Then I get...
```
lancer@lancer-laptop:~$ lsmod | grep wacom
wacom                  30693  0 
```


**Part II.**

```
sudo apt-get install git-core
```
...that works

```
wget http://sourceforge.net/projects/linuxwacom/files/xf86-input-wacom/xf86-input-wacom-0.10.11.tar.bz2/download
```

...this gives me a file called "download"... is this right?

```
sudo cp /usr/share/aclocal/xorg-macros.m4 /usr/share/aclocal/xorg-macros.m4.bak
cp: cannot stat `/usr/share/aclocal/xorg-macros.m4': No such file or directory
```

Looks like I'm stuck here. Not sure whether to proceed with the next instructions. You said to be sure to do the very part which is now failing.

---

### Post by LancerNZ on 2011-03-21
Well, I've taken this about as far as I can without more help. Part II of those instructions must have been written for another distro or something? I'm on Ubuntu 10.04, with Nvidia drivers.

I tried ignoring the errors, but on the autogen stage at the end of Part II, I got...

```
lancer@lancer-laptop:~/Downloads/hardware/wacom_try_again/git/xf86-input-wacom$ ./autogen.sh --prefix=/usr
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
configure.ac:45: error: xorg-macros version 1.8 or higher is required but 1.5.0 found
/usr/share/aclocal/xorg-macros.m4:39: XORG_MACROS_VERSION is expanded from...
configure.ac:45: the top level
autom4te: /usr/bin/m4 failed with exit status: 1
aclocal: /usr/bin/autom4te failed with exit status: 1
autoreconf: aclocal failed with exit status: 1
```

My deadline for the current Digital Painting assignment is in 11 hours. (9pm tomorrow, it's midnight now). I kind of need these things working.

---

### Post by Favux on 2011-03-21
Hi LancerNZ,

Thank you very much.  You were right, it is not suppose to be "download", it is suppose to be "util-macros-1.8.0.tar.bz2"!

Apparently I got a copy/paste error somehow in a recent edit.  Sorry for not catching that sooner.  It should work now.

---

### Post by LancerNZ on 2011-03-21
Didn't work. :(

On Pt 2, this time around, I only did... ```
wget http://xorg.freedesktop.org/releases/individual/util/util-macros-1.8.0.tar.bz2
sudo cp /usr/share/aclocal/xorg-macros.m4 /usr/share/aclocal/xorg-macros.m4.bak

=====> For some reason this is no longer giving me a "not found" error?!

tar xjvf util-macros-1.8.0.tar.bz2
cd util-macros-1.8.0
./configure --prefix=/usr
make
sudo make install
cd ..
cd [folder I made for when installing git]

cd xf86-input-wacom
./autogen.sh --prefix=/usr
make
sudo make install
[Now reboot.]
```...as opposed to the full ```
wget http://xorg.freedesktop.org/releases/individual/util/util-macros-1.8.0.tar.bz2
sudo cp /usr/share/aclocal/xorg-macros.m4 /usr/share/aclocal/xorg-macros.m4.bak
tar xjvf util-macros-1.8.0.tar.bz2
cd util-macros-1.8.0
./configure --prefix=/usr
make
sudo make install
cd ..
cd [folder I made for when installing git]
git clone git://linuxwacom.git.sourceforge.net/gitroot/linuxwacom/xf86-input-wacom
sudo apt-get update
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev libxrandr-dev libncurses5-dev xutils-dev autoconf libtool pkg-config
sudo apt-get upgrade
[You can also try running this line below once.]
sudo apt-get build-dep xf86-input-wacom
cd xf86-input-wacom
./autogen.sh --prefix=/usr
make
sudo make install
[Now reboot.]
```...because the git stuff seemed to be downloading fine in last nights attempts. Is this a bad assumptuion and I need to repeat the steps for Part II in full?

At the end of Part 2, **/usr/lib/X11/xorg.conf.d/10-wacom.conf** does not exist

Rebooting and plugging in my wacom tablet results in the original hover problem, with the mouse cursor not following the pen after a single click.

---

### Post by Favux on 2011-03-21
No that should have worked.  I would have done a *make clean* before the *./autogen.sh --prefix=/usr* but that should be a minor niggle.

I'm hoping all you need to do is install a 10-wacom.conf and reboot for it to work.  The /usr/lib/X11/xorg.conf.d is a non-standard location for xorg.conf.d.  That's because the Debian/Ubuntu X server 1.7 is actually a hybrid between an early 1.8 and 1.7.  To get rid of HAL/.fdi files and go to xorg.conf.d/.conf files.  That's why xf86-input-wacom couldn't install a wacom.conf.  So follow the instructions in *III. Configure the Wacom Bamboo P&T tablet* a).  Just use the gedit line for Lucid to create the file and copy the entire contents of the sample wacom.conf into it and reboot.

---

### Post by LancerNZ on 2011-03-21
:KS Getting there...

The wacom now works with pressure sensitivity, dual point (both pen and eraser) and finger touch.

There is a new problem though: if I click ant of the wacom tablet side buttons, the tablet gets stuck on whatever paint brush I'm using and neither the tablet or mouse can click on other buttons, options, or other programs. This means I can't even access Applications menu etc and have to cold-boot with [CTRL][ALT][DEL] (then wait 60 seconds because that window is not in focus and I can't click on it).

---

### Post by Favux on 2011-03-21
Great, real progress finally!

A bunch of xsetwacom parameter names changed with xf86-input-wacom-0.10.11, see:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom#Table_of_New_Parameter_Names](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Xsetwacom#Table_of_New_Parameter_Names)
and  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)

Also Button 4 may actually be Button 8 for you.

---

### Post by LancerNZ on 2011-03-21
I'm not sure I'm doing it right...
```
lancer@lancer-laptop:~$ xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button 1 1
Unknown parameter name 'Button'.
lancer@lancer-laptop:~$ xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button 2 2
Unknown parameter name 'Button'.
lancer@lancer-laptop:~$ xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button 3 3
Unknown parameter name 'Button'.
lancer@lancer-laptop:~$ xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button 4 4
Unknown parameter name 'Button'.
```

---

### Post by Favux on 2011-03-21
No, that should be right assuming xf86-input-wacom installed correctly.  You may have two xsetwacom executable binaries.  xsetwacom should be at /usr/bin.  Check to see if there is another one at /usr/local/bin.  If there is delete it.  That's in Troubleshooting near the bottom of the HOW TO.

---

### Post by LancerNZ on 2011-03-21
After getting rid of **/usr/local/bin/xsetwacom**...
```
lancer@lancer-laptop:~$ xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button 1 1
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  143 (XInputExtension)
  Minor opcode of failed request:  37 (X_ChangeDeviceProperty)
  Value in failed request:  0x0
  Serial number of failed request:  19
  Current serial number in output stream:  23
lancer@lancer-laptop:~$ xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button 2 2
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  143 (XInputExtension)
  Minor opcode of failed request:  37 (X_ChangeDeviceProperty)
  Value in failed request:  0x0
  Serial number of failed request:  19
  Current serial number in output stream:  20
lancer@lancer-laptop:~$ xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button 3 3
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  143 (XInputExtension)
  Minor opcode of failed request:  37 (X_ChangeDeviceProperty)
  Value in failed request:  0x0
  Serial number of failed request:  19
  Current serial number in output stream:  23
lancer@lancer-laptop:~$ xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button 4 4
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  143 (XInputExtension)
  Minor opcode of failed request:  37 (X_ChangeDeviceProperty)
  Value in failed request:  0x0
  Serial number of failed request:  19
  Current serial number in output stream:  23
```Not sure where in the HOWTO troubleshooting I should look. It mentions installing headers (kernel) but I'm pretty sure that's what started the original problem.

---

### Post by Favux on 2011-03-21
Have you tried using Button1 instead of Button 1?  The part about xsetwacom is at the bottom of Troubleshooting, but that just covers what I already told you.

---

### Post by LancerNZ on 2011-03-21
```
lancer@lancer-laptop:~$ xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button1 1
Parameter 'Button1' is no longer in use. It was replaced with 'Button'.
lancer@lancer-laptop:~$ xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button2 2
Parameter 'Button2' is no longer in use. It was replaced with 'Button'.
lancer@lancer-laptop:~$ xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button3 3
Parameter 'Button3' is no longer in use. It was replaced with 'Button'.
lancer@lancer-laptop:~$ xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button4 4
Parameter 'Button4' is no longer in use. It was replaced with 'Button'.
```

---

### Post by LancerNZ on 2011-03-21
Perhaps is has something to do with the message I reported getting from the end of Part I?
```
Your wacom.ko is available under 
    /home/lancer/Downloads/hardware/wacom_try_again/linuxwacom-0.8.8-11/src/2.6.30

NOTE: the X driver in this package only supports Xorg servers older than 1.7.
          You are running a newer version. 
Please build the X driver from xf86-input-wacom.
The kernel driver provided in this package is independent of 
the X server version
```
I'm not sure how to go about installing that one they recommend though.

---

### Post by LancerNZ on 2011-03-21
....should I repeat the steps around the git registry stage? I'm a bit nervous to poke things.

---

### Post by Favux on 2011-03-21
The message is confusinig you.
> Your wacom.ko is available under 
    /home/lancer/Downloads/hardware/wacom_try_again/linuxwacom-0.8.8-11/src/2.6.30
That means the usb kernel driver/module wacom.ko was successfully compiled and tells you where it is.
> NOTE: the X driver in this package only supports Xorg servers older than 1.7.
          You are running a newer version. 
Please build the X driver from xf86-input-wacom.
The kernel driver provided in this package is independent of 
the X server version
That tells you linuxwacom can not make a X driver for X server 1.7 or higher.  You have to use xf86-input-wacom to build an X driver for X server 1.7 and higher.  Hence part II.

If you've verified there aren't two xsetwacom's go ahead and repeat part II. and reclone xf86-input-wacom.  It shouldn't hurt anything.

---

### Post by LancerNZ on 2011-03-21
I decided a workaround for the freezing touchpad buttons might be to assign them to keyboard keys. What seems to be happening is when I push a button down, it doesn't release, thus not allowing a second click after that (not even to focus on another window or menu).

Therefore, I typed...
```
xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button 1 "key a"
xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button 2 "key b"
xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button 3 "key c"
xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button 8 "key d"
```

This effectively disables the touchpad buttons of course (until we figure out how to go about properly configuring them, whether to reinstall what etc), but at least I can paint in my programs with the pen now. Not ideal, but will for now save me having to reboot and lose a lot of work anytime I accidentally press a touchpad button.

When I do this though, I notice that pressing the touch pad buttons only allows one instance of the assigned key. Then they seem to do nothing, unless I randomly hit them lots of times, then occasional letters (a,b,c or d) occur.

---

### Post by Favux on 2011-03-21
Good.

I don't think you are describing a new bug because my pad works fine.  There were some recent commits dealing with the pad though.  I'm wondering if your xsetwacom executable somehow isn't the new one and that's why you're having the problem.

Meet your deadline and when you get a chance reclone the xf86-input-wacom git repository and see if the newly cloned xsetwacom copying over your current one fixes things.

---

### Post by LancerNZ on 2011-03-21
I went through the Part II again but it juet kept telling me everything was already installed and I ended up with the same faults. I did this through a complete new directory for the git things, namely a **/home/lancer/Downloads/hardware/wacom_try2/** directory.

Then I thought about what you were saying; about the "new" xsetwacom being in there and wondered if it had not overwritten the /usr/bin (or whatever) version. So, I went in and tested the new one as so...

```
cd /home/lancer/Downloads/hardware/wacom_try2/xf86-input-wacom/tools$
./xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button 1 1
./xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button 2 2
./xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button 3 3
./xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button 8 4
```
This gave me _no errors_ indicating that the xsetwacom in here can indeed handle the button assignments. Perhaps it's simply not transfered to the right app directory on make install?
Then, once these buttons were assigned I pressed the buttons on my touchpad.
:( They still locked everything up. It's as if the touchpad allows a single press of any button, but will not release the touch.

---

### Post by Favux on 2011-03-21
We can test your theory by manually copying the new xsetwacom into place.  Check to make sure I got the directory path correct.
```
sudo cp /home/lancer/Downloads/hardware/wacom_try2/xf86-input-wacom/tools/xsetwacom /usr/bin/xsetwacom
```
Then reboot.  If it doesn't work like it did in the compile directory right click on both xsetwacoms and check the Date in Properties to make sure they are the same.

---

### Post by LancerNZ on 2011-03-22
Did not work, but gave the usual errors with trying to assign buttons. The modified dates are not the same, although I expect this is because the /usr/bin version has the time & date it was created through the copy.

---

### Post by Favux on 2011-03-22
Right, but it had the copy date and time, correct?  OK, that blows the idea that somehow a PPA was blocking the xsetwacom update.

I have no clue as to what's wrong.  If it worked in the compile directory it should work in the /usr/bin directory.  Hmmm.

---

### Post by LancerNZ on 2011-03-22
Thing is, it's not working in the compile directory. Despite that version apparently accepting binding numbers, it still has the current main issue: that when a tablet button is pressed, it gets stuck. I can't click anything else after then. Even unplugging the wacom leaves the mouse buttons disabled.

---

### Post by LancerNZ on 2011-03-22
Here's what I managed to pull off using the tablet in tonight's Speed Painting competition.

_Theme_: Invasion
_Time limit_: 1hr 30min (although I completed this in 1:15)
_Software I used_: MyPaint, Inkscape, Gimp

[IMG]http://img853.imageshack.us/img853/5756/invasion1hr15min.jpg[/IMG]

Glad we got the drivers going as much as we did or this would not have been possible in the time. Be cool if we could completely fix things though. Perhaps install **wacom-dkms** through Synaptic?

---

### Post by Favux on 2011-03-22
Sweet!  And no gun to blast the "Invaders" with, poor guy.

Well I'll try to review what we've got so far and try to figure out what's wrong.  Right now I'm clueless.  Are you doing any configuration in xorg.conf.d or xorg.conf I don't know about?  Or using a xsetwacom script?

---

### Post by LancerNZ on 2011-03-23
Thanks.

I was glad when I saw you were answering this thread. An earlier search pointed to a thread where someone posted your *HowTo* page, stating that you specifically were someone who knows what they are doing in terms of getting a Wacom up and running on Linux. At least we have pressure sensitivity so far.

My **/usr/lib/X11/xorg.conf.d/10-wacom.conf** is as follows...

```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection
```

My **/etc/X11/xorg.conf** is as follows...

```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

---

### Post by junapp on 2011-04-16
Hello - just wanted to throw out a big 'thanks' for this thread. Haven't worked my way through it just yet, but have the exact same behaviour as described in post 1 and had installed in the same fashion.

Exact same model CTH-460, so will work through the instructions and attempt to report back at progress.

I am completely new with using a tablet, and thought that this can't seriously be the way this works (lifting the pen well off the surface to get the cursor to move again). Glad to see it isn't.

---

### Post by InnerBushman on 2011-11-20
Hi.
I have a Wacom tablet that WAS working with the driver from doctormo PPA. I have not use it for a while (couple of system updates) and now it does not work like it should.

Problem: when i point and click with the stylus it works fine until i lift the stylus back again.
When hovering it does not update the cursor position until i take it out of range and put it back. If i press it again it points alright but not when hovering.
Touch-pad and BT mouse works fine while the hovering stylus freezes.

Can anyone point me to where should i start looking for the reason?
Thanks in advance,

Bushman

U 10.04LTS
Wacom Bamboo CTL-460

---

### Post by Favux on 2011-11-20
Hi InnerBushman,

Run these commands in a terminal:
```
xinput list
```
and
```
xsetwacom list
```
Then post the outputs.  It sounds like the tablet is no longer on the Wacom X driver but instead on the evdev driver.

---

### Post by InnerBushman on 2011-11-20
xinput gives:
```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation            id=12    [slave  pointer  (2)]
&#9116;   &#8627; Bluetooth Laser Mouse                       id=13    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Pen                        id=14    [slave  pointer  (2)]
&#9116;   &#8627; Wacom Bamboo 4x5 Finger                     id=15    [slave  pointer  (2)]
(...)
```and xsetwacom gives no output.

Seems you'r right. Now, how do i get back to the previous driver?

---

### Post by Favux on 2011-11-20
Since you are using Lucid (10.04) the likely cause is your 10-wacom.conf disappeared.  Part III. of the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") will show you how to manually re-install it.  After a reboot the tablet should be working again.

If that turns out to be what happened feel free to post on the "invalid" Launchpad bug report regarding the vanishing 10-wacom.conf:  [https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/770082](https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/770082)

---

### Post by InnerBushman on 2011-11-21
Thank you for help.
Recreating the file by hand fixed the problem. Tho i'm not sure i didn't  break anything in the process cause i get config files parse error on  boot when X starts o_O Then i choose "restart X" and my comp works  normally.
I'll look into it later. Thanks for help with the tablet. ;]

---

