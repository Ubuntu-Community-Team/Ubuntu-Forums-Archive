---
title: "acer 3680 How to"
date: 2007-10-02
forum: Hardware &amp; Laptops
---

### Post by ljonesj on 2007-10-02
This is a How to to get everything working for the acer 3680. I have used other people post that have dealt with the problem of no sound, screen resolution, synaptic touch pad setup and the program to get sensitivity setup right for it, and the multimedia install to get mp3 and dvd movies and other codecs to work. I am not going to go into wireless setup as people have many different ways of fixing this either by ndiswrapper, switching out the internal card to one that does work, or like me having an external card that works.

Step 1a due all the updates it will make it easier for you while updates are working 
     
step 1b  (this is from poster jsares) The video resolution was 1024x768. It should be 1280x800. I fixed it buy running:

Code:

sudo apt-get install xserver-xorg-video-intel (after updates have been done)

step 1c The sounds wasn't working. I fixed it by pasting:

Code:

options snd-hda-intel model=auto

at the bottom of:

Code:

/etc/modprobe.d/alsa-base

step 1d the touch pad fix (also from poster jsares)
Code:

/etc/X11/xorg.conf

And add these lines below the mouse section:

Code:

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizScrollDelta" "0"
Option "SHMConfig" "true"
EndSection

Add this line in the ServerLayout section:

Code:

InputDevice "Synaptics Touchpad"

step 1e the touchpad program that allows custom control (by  poster benanzo)

sudo apt-get install xserver-xorg-input-synaptics gsynaptics

(he mentions about adding line in the xorg.conf file. you have already done this to get the touch pad middle scroll function to work so there is no need.)

now to step 2 it will be a big section

This is how to get multimedia to work 

Step 2a reboot after you get all updates and other things working as it will make the screen resolution easier to work with.

Step 2b ok now to get the mp3 playback to work and flash
(thanks to poster Adamant1988)

 For mp3, etc.
Open up Add/Remove programs from your Application bar.

Go to Sound&Video and Find and Check all of the packages below (easily done by searching for gstreamer)

    * "GStreamer ffmpeg video plugin"
    * "GStreamer extra plugins"
    * "GStreamer plugins for aac, xvid, mpeg2, faad"
    * "GStreamer plugins for mms, wavpack, quicktime, musepack"


Then go to Other subsection of Add/Remove and find

    * "Ubuntu restricted extras"

For Flash support

While under the "Other" section enable

    * "Macromedia Flash plugin"

Step 2c

For DVD Playback and Win32 Codecs

Edit the file /etc/apt/sources.list using either of the following commands in a terminal:
Code:

$gksudo gedit /etc/apt/sources.list

to open it in the GUI text editor

or

Code:

$sudo vim /etc/apt/sources.list

to open it in the Vim command line text editor

(me personally i like this command)

sudo nano /etc/apt/sources.list
Add the following lines to add the Medibuntu repository to the file:


Quote:
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

(copy and paste the whole code to the sources list it makes easier and less likely for mistakes)

Import the gpg key for the Medibuntu repository to ensure that the packages are installed without warnings/errors regarding trust:

To do this, run the following command from the terminal:

Code:

wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -

(copy and paste the above in one whole line in the terminal or it will not do right i found out)

Now update the local list of packages to get the list of packages from the newly added Medibuntu repository:

In a terminal execute the following command:

Code:

sudo apt-get update

Now you can install libdvdcss2 and w32codecs using the following command:
Code:

sudo apt-get install libdvdcss2 w32codecs


Thats the end of this little walk through on how to get certain things working in the acer 3680.
Thanks to all the posters and dedicated people that wrote all the ways to get this all to work for this great little computer.

If any one has problems fill free to pm me or even ask for help on the post

---

