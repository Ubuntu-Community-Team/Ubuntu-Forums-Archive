---
title: "Headphone/Speaker Issue On A Chembook"
date: 2009-01-27
forum: Hardware
---

### Post by s1mp13m4n on 2009-01-27
I have a Chembok laptop with Realtek ALC888, 2 Channel HD Audio in it so says the manufactures website.  The issue I am having is that when I plug in headphones the main speakers still play and using the audio controls from the top panel I can not turn them off.  If I play with setings in that panel it effects the speakers and headphones together.  Do I need a driver for this sound card?  Could Linux be using a default driver?  I am new to this Linux stuff so any help will be appreciated.

---

### Post by s1mp13m4n on 2009-01-30
Does anyone have any input on this issue?  I have been looking online and I am not finding much about it.  Thanks for the help.  :)

---

### Post by smo0th on 2009-01-31
when you open the volume control and go to the switches tab, is the headphone option selected?

have you tried switching devices there with file>change device?

---

### Post by s1mp13m4n on 2009-02-01
Yes, there is no "switch" that I can select to change from main laptop speakers to headphones at al.  I have also changed or can switch between an Intel alsa mixer and a Realtek OSS mixer.  I have a Realtek sound card in this laptop but there is no switch in the control panel to turn speakers on or off.

---

### Post by smo0th on 2009-02-01
well, lets try installing these alsa packages:

```
sudo apt-get install alsa-firmware alsa-firmware-loaders alsaplayer-alsa alsaplayer-jack

```

also you could install:

```
sudo apt-get install alsa-tools alsa-tools-gui
```

hope it works, please let us know the results :)

---

### Post by s1mp13m4n on 2009-02-01
here is what I got

paul@laptop:~$ sudo apt-get install alsa-firmware alsa-firmware-loaders alsaplayer-alsa alsaplayer-jack
[sudo] password for paul: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package alsa-firmware
paul@laptop:~$ 

this was the first one, I will try the next one

---

### Post by s1mp13m4n on 2009-02-01
Here is what happened with the second command:

paul@laptop:~$ sudo apt-get install alsa-tools alsa-tools-gui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  oem-config-gtk localechooser-data oem-config
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libfltk1.1
The following NEW packages will be installed:
  alsa-tools alsa-tools-gui libfltk1.1
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 745kB of archives.
After this operation, 2105kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libfltk1.1 1.1.7-6 [400kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe alsa-tools 1.0.15-2ubuntu4 [83.2kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe alsa-tools-gui 1.0.15-2ubuntu4 [262kB]
Fetched 745kB in 5s (143kB/s)          
Selecting previously deselected package libfltk1.1.
(Reading database ... 147102 files and directories currently installed.)
Unpacking libfltk1.1 (from .../libfltk1.1_1.1.7-6_i386.deb) ...
Selecting previously deselected package alsa-tools.
Unpacking alsa-tools (from .../alsa-tools_1.0.15-2ubuntu4_i386.deb) ...
Selecting previously deselected package alsa-tools-gui.
Unpacking alsa-tools-gui (from .../alsa-tools-gui_1.0.15-2ubuntu4_i386.deb) ...
Setting up libfltk1.1 (1.1.7-6) ...

Setting up alsa-tools (1.0.15-2ubuntu4) ...
Setting up alsa-tools-gui (1.0.15-2ubuntu4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
paul@laptop:~$ 

I loked at my mixer controls and I see no change, do I need a restart? did it not do what I am trying to do?  I am trying to learn Linux and I guess there is no better way to do it.  LOL  thanks for the help.

---

### Post by smo0th on 2009-02-01
try restarting the audio:

```
sudo /etc/init.d/pulseaudio restart
```

so you don't have alsa-firmware, well look, you may install packages and drivers using the terminal just as you did before or using synaptic (System>Administration>Synaptic package Manager)

since we have different distros(mine is ubuntu) I recommend you to use synaptic and search for "alsa" then you scroll down in the results and select the alsa packages for your distribution, restart audio and hopefully it'll work [-o< if it doesn't go to synaptic, uninstall ALL alsa packages and reinstall them to see if that fixes it.

---

### Post by s1mp13m4n on 2009-02-01
OK I did what you posted and still no "switch" in my audio mixer controls.  Hmmm, I do not get it.  Any more ideas?  It has to be something simple, I am just new to Linux and do not know the where and how yet.  If this were WinXP I would be set.  LOL  Thanks for the help.

---

### Post by smo0th on 2009-02-01
I never went thru this problem so I'm kinda out of ideas right now, the last thing I would recommend is something you may have done by now, going to System>Preferences>Sound and test the possible combinations there, and System>Administration>Hardware Testing to see if you get something from there. Sorry this is all I have but I'm sure someone else will be able to help out, this community is GREAT :D

Good luck man.

---

### Post by smo0th on 2009-02-01
Talked to a friend who had the same problem, he managed to fix it with:

```
sudo aptitude install module-assistant build-essential
sudo module-assistant prepare,update
sudo module-assistant build,install alsa
```

---

### Post by natmc1 on 2009-02-02
I loaded the Gnome ALSA mixer. I then opened the ALSA mixer and enabled headphone jack sence. This solved my problem of sound coming out the speakers and headphones when headphones are plugged in. Now sound only comes out headphones when they are plugged in.

---

