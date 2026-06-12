---
title: "Fujitsu P1510D Touchscreen in Karmic and Lucid"
date: 2010-09-04
forum: Hardware
---

### Post by kathleenhenri on 2010-09-04
I recently purchased a used Fujitsu P1510D and immediately installed Ubuntu on it. Following instructions found in this thread [http://ubuntuforums.org/showthread.php?t=811200](http://ubuntuforums.org/showthread.php?t=811200) (particularly #37 and #44). I was also able to get the screen rotation buttons working by adding the following repositories.

From the terminal enter
```
sudo gedit /etc/apt/sources.list
```Next, add the software repositories for the fjbtndrv package.
Save and close.
     

```
deb [http://ppa.launchpad.net/khnz/ppa/ubuntu](http://ppa.launchpad.net/khnz/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/khnz/ppa/ubuntu](http://ppa.launchpad.net/khnz/ppa/ubuntu) karmic main
```Then back in terminal enter the following. This adds the key.
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E88D7B6F
``````
sudo apt-get update
sudo apt-get install fjbtndrv
```You might need to install wacom-tools as well.

While all this works fine there was one one problem: the touch doesn't follow rotation of the screen. I have been searching for weeks on line trying to find a solution. I finally ran across this blog[ http://blogs.fsfe.org/alge/?p=111]("http://blogs.fsfe.org/alge/?p=111") and this guy has created .deb files required for activating the touchscreen and the rotate button in Karmic. Plus, the touch follows rotation when you mechanically rotate the screen. Touch still doesn't follow when using the button to rotate the screen. But hey, when you flip the screen on its hinge touch now works in two orientations rather than one. YAY! The address for the .deb files is [http://www.algepop.net/users/alge/p1610/](http://www.algepop.net/users/alge/p1610/). The files were modified to work with the P1610 model but they work great with my P1510D running Karmic.

One thing you have to do is edit the  enable_touchscreen file though. Calibration will be off if you don't.

From terminal enter
```
sudo gedit /usr/bin/enable_touchscreen
```Change line 16 to read:
[COLOR=#000000]use constant SCREEN => (1024,600);[/COLOR] [COLOR=#000000]

Save and close.
[/COLOR]
I have tried to install the files (either as .deb or tar) in Lucid but keep running into one snag. One of the files requires Xrandr and it doesn't seem to be available in Lucid. Xrandr has been replaced with x11-xserver-utils. Is there a way to install Xrandr from another source and remove x11-xserver-utils?

---

### Post by gordintoronto on 2010-09-04
x11-xserver-utils includes xrandr.

---

### Post by Favux on 2010-09-04
Have you checked to see if it's actually asking for 'libxrandr-dev'?

---

### Post by kathleenhenri on 2010-09-05
> **gordintoronto said:**
> x11-xserver-utils includes xrandr.

Yes, I understand. It is comparable to Lucid incorporating wacom-tools into the xserver-xorg-input-wacom package. 

My question is whether or not it is possible to install xrandr from another source. Or if it is even possible or desirable to force the installation from Karmic.

> **Favux said:**
> Have you checked to see if it's actually asking for 'libxrandr-dev'?

The broken dependency clearly stated a missing xrandr package. 

At the moment I am happily running Karmic on my machine, so I am reluctant to reinstall Lucid and test again unless I was sure about the xrandr piece of the puzzle.

---

### Post by neillmitchell on 2010-10-14
Okay, I got this all to work. You _must_ use Albrechts's pre built debs [http://www.algepop.net/users/alge/p1610/](http://www.algepop.net/users/alge/p1610/) as they are patched to work in Ubuntu and register the P Series's screen swivel switch. If you use the shipping Ubuntu version of fjbtndrv it does not register the swivel switch. So uninstall it if you have already got the vanilla version.

Now, you need to install some items using:
sudo apt-get install -y setserial xserver-xorg-dev x11proto-core-dev x11proto-fonts-dev build-essential pkg-config libxrandr-dev libxi-dev libncurses-dev dkms libxosd2 ]

You also need to build the wacom-tools as the Ubuntu xserver-xorg-input-wacom package does not include wacdump.

So go over to [http://linuxwacom.sourceforge.net/index.php/dl](http://linuxwacom.sourceforge.net/index.php/dl) and download the latest version.

cd ~
mkdir tmp
cd tmp
tar -xvjf linuxwacom-0.8.8-10.tar.bz2
cd linuxwacom-0.8.8-10
./configure --prefix=/usr

Check it is going to build wacdump then
make
sudo make install

Now install the pre-build debs

sudo dpkg -i fsc-btns-kernel-source_2.1.0-1uk4_i386.deb
This takes a few minutes as it has to build the kernel module

sudo dpkg -i ]fscd_2.1.0-1uk4_i386.deb
sudo dpkg -i fscrotd_2.1.0-1uk4_i386.deb
sudo dpkg -i fjbtndrv_2.1.0-1uk4_i386.deb
sudo dpkg -i libx11-guitest-perl_0.21-1_i386.deb

Now we have to force the last one because of the missing dependencies
sudo dpkg --force-all -i fsc-p1610_1.2_i386.deb 

Unfortunately Ubuntu will forever complain that this is a broken package and prompt you to remove it every time you install a package. So you need to take it off the radar. 

cd /var/lib/dkpg
sudo gedit status

Search for the block containing fsc-p1610_1.2 and remove the whole entry. There is probably a neater way to do this ;)

If you are using a P1510 you have to edit the enable_touchscreen script to set it for a 1024x600 screen. I also found that if you switch the calibration constants with the commented out ones, the touchscreen is more accurate. Edit the script using:

gedit /usr/bin/enable_touchscreen

Now reboot. Login and type enable_touchscreen from the console. It should all work. Screen rotates when you swivel it and the touchscreen re-calibrates to cope. First time I've ever had this all working under Linux :)
You can then put enable_touchscreen into your startup preferences so it auto runs.

---

### Post by jgraves on 2010-10-22
I've been over this howto many times and can't get the automatic rotation to work.  Is there a way to test the actual hardware switch to see if it is a physical problem or software setup issue?  I've tried using xev and don't see any event when I rotate the p1510d display.  Nothing shows up in the syslog files either.

I'm on 10.10 and the touchscreen works perfectly.  The rotate button works, but I need to manually restart the enable_touchscreen script.

Thanks.

---

### Post by neillmitchell on 2010-10-25
> **jgraves said:**
> I've been over this howto many times and can't get the automatic rotation to work.  Is there a way to test the actual hardware switch to see if it is a physical problem or software setup issue?  I've tried using xev and don't see any event when I rotate the p1510d display.  Nothing shows up in the syslog files either.

I'm on 10.10 and the touchscreen works perfectly.  The rotate button works, but I need to manually restart the enable_touchscreen script.

Thanks.

Did you use the packages above or the default 10.10 ones? You must use the patched debs. I uses the 10.10 debs first and had exactly the same issue. I removed them and then did the steps in my post above and the automatic screen rotate then worked fine.

---

### Post by The Flying Penguin on 2010-11-02
> **neillmitchell said:**
> 

You also need to build the wacom-tools as the Ubuntu xserver-xorg-input-wacom package does not include wacdump.

So go over to [http://linuxwacom.sourceforge.net/index.php/dl](http://linuxwacom.sourceforge.net/index.php/dl) and download the latest version.

cd ~
mkdir tmp
cd tmp
tar -xvjf linuxwacom-0.8.8-10.tar.bz2
cd linuxwacom-0.8.8-10
./configure --prefix=/usr

Check it is going to build wacdump then
make
sudo make install



I'm having two problems with this.

1) Under build options, it says wacdump - no. So how do I make it build wacdump?

2) I get a message that says:
The X driver in this package only supports Xorg servers older than 1.7. You are running a newer version. Please build the X driver from xf86-input-wacom.

---

### Post by theSeinfeld on 2011-03-28
I have successfully build the driver from Conan here:
[https://launchpad.net/~fujitouch/+archive/ppa/+packages](https://launchpad.net/~fujitouch/+archive/ppa/+packages)

All you need is to make sure that mouse is not core pointer in your xorg and you are good to go

---

### Post by synchro505 on 2011-04-09
Sorry for the noob question but how do you make sure the mouse is not the core pointer in xorg?

---

### Post by psixpsi on 2011-12-02
> **theSeinfeld said:**
> I have successfully build the driver from Conan here:
[https://launchpad.net/~fujitouch/+archive/ppa/+packages](https://launchpad.net/~fujitouch/+archive/ppa/+packages)

All you need is to make sure that mouse is not core pointer in your xorg and you are good to go

Hi! I've done it too under Oneiric: installed the package from the page (Natty version).
What do I do next with it? 
Thanks!
Psi

---

