---
title: "New user,new install,with issues"
date: 2014-01-17
forum: Hardware
---

### Post by d.mayfair on 2014-01-17
Hi there.
I'm new to Linux so please bear with me.
I have just installed Xubuntu 13.10 alongside xp on the following computer.

e-Machines ER1401
[COLOR=#FFFFFF][FONT=verdana]

[/FONT][/COLOR]* AMD Athlon™ II Dual Core K325 64 bit
* NVIDIA® nForce® 9200 Chipset,
* Memory - 2GB DDR3 RAM | 2 x SODIMM slot
* Hard Drive - 250GB SATA
* Connectivity - hdmi to lcd tv,optical sound output

The issues I have.
Firstly no sound.When running on XP the sound can be heard thru the tv speakers.With Xubuntu nothing.When I change the volume it shows up but nothing comes out of the tv.I have yet to try the optical output as I'm waiting on a cable.
Secondly,I have a usb dvd drive.When I play a CD with VLC player it shows that it is playing.....no sound output again....but I am also unable to eject the disc,neither manually pressing the drive door nor by using the vlc interface.

I read somewhere there's an issue with the kernel on a previous version of Xubuntu with regards to the sound .Could that be my problem too ?
When I bring up device manager in windows it tells me I have Nvidia Hi Def Audio and Realtek Hi Def Audio

Any thoughts ?
[COLOR=#FFFFFF][FONT=verdana]

[/FONT][/COLOR][COLOR=#FFFFFF][FONT=verdana]


[/FONT][/COLOR]

---

### Post by Bucky Ball on 2014-01-17
Welcome. You can open a terminal and paste:

alsamixer

... and see if anything is muted in there.

For a friendlier version, install gnome-alsamixer; that has a GUI. 

If this fails, you can install Pulseaudio Volume Control (pavucontrol) and have a good look around. Let us know how you go.

---

### Post by d.mayfair on 2014-01-17
Pulse audio is already installed and I've tried all the settings to no avail

---

### Post by mikewhatever on 2014-01-17
You can click the speaker icon, and select Sound Preferences, then check or select which device is in use in the Output Devices tab.

---

### Post by Bucky Ball on 2014-01-17
Yes, but is Pulseaudio Volume Control installed? If not, install it and have a look around that.

Did you launch alsamixer from a terminal?

---

### Post by mikewhatever on 2014-01-17
> **Bucky Ball said:**
> Yes, but is Pulseaudio Volume Control installed? If not, install it and have a look around that.

Did you launch alsamixer from a terminal?

It should be in Xubuntu 13.10 by default.

Switching devices from alsamixer is f6 here.

---

### Post by d.mayfair on 2014-01-17
> **Bucky Ball said:**
> Yes, but is Pulseaudio Volume Control installed? If not, install it and have a look around that.

Did you launch alsamixer from a terminal?

Pulseaudio volume control is installed.

Yes I launched alsamixer and switched to Nvidia sound card but still the same.

---

### Post by d.mayfair on 2014-01-17
I found this
[http://askubuntu.com/questions/309293/no-sound-through-hdmi-cable-nvidia](http://askubuntu.com/questions/309293/no-sound-through-hdmi-cable-nvidia)

---

### Post by Bucky Ball on 2014-01-17
There is an entry for HDMI audio in the Output tab of PAVControl. Check to see that it is configured correctly and not muted.

---

### Post by d.mayfair on 2014-01-17
Nothing is muted mate,I've gone all thru the configuration settings already,tried every output

---

### Post by Bucky Ball on 2014-01-17
No worries, then. We're just trying to help, but I can feel your frustration so leave you to it. Good luck. ;)

---

### Post by d.mayfair on 2014-01-23
Moving on then,I tried an optical cable,still no sound.

I have found I have the following hardware devices.
card 0 : NVidia (HDA NVidia),device 0:ALC662 rev1 Analog (ALC662 rev1 analog)
repeat for device 1 except substitute digital
and device 3 hdmi

ALC622 being the Realtek codec I went to their site and downloaded the Linux driver (3.0) version 5.18,extracted and installed.
I don't know if I've done it right but anyway there's still no sound.

There's a multitude of driver options that come when I go to other drivers,I've tried a couple to no avail

I'm at a loss as to what to do next.
There does appear to be a fair few problems with NVidia and Linux when I do a google search.
Would I have more joy trying a different distro ?

---

### Post by stalkingwolf on 2014-01-23
Try mint 13.  i have 3 computers with nvidia sound all work . one is connected to my tv.  i have sound both from the tv and thru my stereo system.

---

### Post by d.mayfair on 2014-01-23
I already tried Mint 13 xfce and couldn't get it to instal

---

### Post by d.mayfair on 2014-01-24
Unbelievable !!!
You know I said earlier I'd tried an optical cable with no joy.Well I'd previously ordered one off Ebay because the one I had was too short and was already being used by my satellite receiver.
Whilst waiting for it to arrive I'd moved the computer so the short cable would reach but it didn't work.
I was just about to try a different distro when the new cable arrived in the post so I thought nothing to lose,I'll plug it in anyway.....lo and behold the dam thing bursts into life.
We have sound !!! :)

---

### Post by Bucky Ball on 2014-01-24
Excellent news!

Please mark thread as solved to help others by following the instructions in my signature. 

Enjoy. ;)

---

### Post by d.mayfair on 2014-03-09
Sorry to resurrect a solved thread BUT........I'm still having sound issues,this time 5.1
I can get stereo but not surround sound.I updated to nvidia driver version 331 and the computer wouldn't boot.I reverted back but still it wouldn't boot.

I'm know going to have to re-install Xubuntu AND Xbmc.:(

Any suggestions as to how I can get around this ?

---

### Post by d.mayfair on 2014-03-10
I'm now using the latest driver (nvidia 319) from additional drivers.
I've set the number of channels in pulse to 6 using these commands

sudo gedit /etc/pulse/daemon.conf
default-sample-channels=6

But,I don't get any 5.1 output options in Alsamixer.

Help ! :)

Her's what I get with Alsamixer

[http://i97.photobucket.com/albums/l234/stokedaz/IMG_20140310_161519_577.jpg](http://i97.photobucket.com/albums/l234/stokedaz/IMG_20140310_161519_577.jpg)

---

### Post by Bucky Ball on 2014-03-10
I suggest you post a new thread - with a descriptive thread title - in [*Multimedia & Video*]("http://ubuntuforums.org/forumdisplay.php?f=334") rather than continue with this one. You're eighteen posts deep on a solved thread with a title that doesn't describe any problem, let alone this new one (most people post here because they have issues). You will greatly improve your chances of help.
 
Thanks.

---

### Post by d.mayfair on 2014-03-10
will do,thanks

---

