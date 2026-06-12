---
title: "Configuring Ubuntu 10.04 in a Fujitsu-Siemens T4010 Tablet PC"
date: 2010-05-16
forum: Hardware
---

### Post by gabrieldiegoteixeira on 2010-05-16
Hello people,

I've been tweaking the installation of Ubuntu 10.04 in my T4010 Tablet PC. Many stuff still don't work, but I would like to describe what I did so far.

First, to boot the livecd you will have to work-around the black screen of death bug of the current 10.04 images. To do so, after you select the language, you hit F6 and select nomodeset and then proceed to the installation normally that (almost) everything must work.

Now I proceeded to the installation of the driver of the buttons near the lcd. You can follow the instructions at [https://launchpad.net/~khnz/+archive/ppa](https://launchpad.net/~khnz/+archive/ppa) to install the package fjbtnrv.

The next step is to setup the Tablet that is not calibrate by default (is that so hard to set automatically in the installation?). To calibrate the stylus go to the terminal and type this:
```
 sudo gedit /usr/lib/X11/xorg.conf.d/10-wacom.conf 
```
the content of the file must looks like this:
```
Section "InputClass"
	Identifier "Wacom class"
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

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection
```

As long as I don't have Parkinson, change it to this:
```
Section "InputClass"
	Identifier "Wacom class"
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

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001"
	MatchDevicePath "/dev/input/event*"

        Option          "TopX"          "78"
        Option          "TopY"          "-56"
        Option          "BottomX"       "24517"
        Option          "BottomY"       "18070"

	Driver "wacom"
EndSection
```

Restart the Xserver by typing (warning: this will close all applications)
```
sudo /etc/init.d/gdm restart
```

If the calibration is not good for you, try calibrating by yourself using xinput_calibrator_x11 (from [http://github.com/tias/xinput_calibrator](http://github.com/tias/xinput_calibrator)) but be aware that the settings that they suggest have a different syntax. Where they say "MinX" "MaxX" "MinY" "MaxY", you should read "TopX" "BottomX" "TopY" "BottomY".

I'm still looking how to enable the 3D acceleration of the Intel 855GM, because without it Google Earth just too slow, although works.

I hope that this helps others

---

### Post by aussiedwarf on 2010-05-17
Nice explanation of what to do. Its a shame that installation  requires that little hack.

On my t4010, fjbtnrv doesn't seem to allow for rotation any more.also the brightness buttons don't seem to work. fjbtnrv did the trick for 9.10. Do you have a similar situation?

---

### Post by babuhumi on 2010-05-30
Thank you!!!

It works perfect on my T4210. However, once I reboot, everything comes back. And I have to restart X server to let the pen work. Do you have any better way to solve it?

Thanks

---

### Post by thebigfatgeek on 2010-06-24
For me the stylus seems to work fine, scroll up and down buttons are ok, Fn button works etc, but I cannot get screen rotation to function. Any ideas to trace the issue would be appreciated

---

### Post by sm8ps on 2010-09-30
Thanks for the input, everybody! However, I had not go the pen working by following gabrieldiegoteixeira's instructions. The pointer was locked the the lower right corner as if the scaling was completely off. The pointer stayed within the display only when the pen tip was extremely close to the upper left corner.
The work-aroung came from user jozze in thread t=1564821&page=8: restarting the X server does the trick. So the pen set-up works differently on an already started system than at system start-up. From the log file, I suspected that X is looking for something that it cannot find. So I did three things:
1.) re-name the X configuration file /usr/lib/X11/xorg.conf.f/10-wacom.conf to 97-wacom.conf.
2.) entered the Options {Top,Bottom}{X,Y} also into the Section "InputClass"/Identifier "Wacom serial class" because that is the one that seems to get loaded. (BTW, I used [0,24576] for the x-, [0,18432] for the y-coordinates.)
This all worked fine and produced a stable recognition of the pointer by X. (I cannot say if all of the mentioned steps are mandatory, though.) On the other hand, X seems to set a much too low pressure setting. Thus everything on screen reacted as if I was double-clicking everything. So I (...)
3.) added 'Option "Threshold" "7" to the said file. 
This all was done after having installed fjbtndrv. I got a stable system now with a fully functional pen. (BTW: trouble-shooters lesson learned: always check if your fix is persistent across re-boots :)

Cheers!
St. Müller, Switzerland

---

### Post by fuji-kun 4010 on 2010-11-02
sorry if this is the wrong place to ask, but i just updated my t4010 from 10.04 to 10.10, and the display no longer rotates... the digitizer will, but the screen itself doesn't rotate and the rotation button no longer works. when i look under "preferences" and "monitors," it also only shows "normal" position and does not allow rotation...

help...

---

