---
title: "Webcam Logitech QuickCam Pro 9000"
date: 2009-03-12
forum: Hardware
---

### Post by Max-B on 2009-03-12
Hi,
I'm running Ubuntu 8.10 with a webcam Logitech QuickCam Pro 9000. I use it with the tool webcam for grabbing picture every minutes. What I have to do is to read an instrument, that's why I bought an autofocus camera. The problem is that the focus of the camera doesn't work.

Does anybody knows if there is a way to set autofocus o manual focus with this webcam on Ubuntu?

ciao,
Max

---

### Post by Max-B on 2009-03-16
Hi,
I solved my problem and I write here a tutorial to get the focus control of your  Logitech QuickCam Pro 9000 on Ubuntu 8.10.

Download the sub version of the library [libwebcam]("http://www.quickcamteam.net/software/libwebcam") developed by the [QuickCamTeam]("http://www.quickcamteam.net"). Unfortunately I was not able to compile the offical version, that's why I suggest to use the subversion.

```
wget -r http://svn.quickcamteam.net/svn/qct/Linux/
```

Accordingly with the libwebcam's README file the library depends on uvcvideo, libxml2, gengetopt. The first is probably already installed but probably not the other two.

```
sudo apt-get install libxml2-dev gengetopt
```

Move into the directory in which  source files are located

```
cd svn.quickcamteam.net/svn/qct/Linux/
```

Accordingly with the libwebcam's README download the file needed to compile the package:

```
cd Common/include/
wget http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/uvcvideo.h
wget http://svn.berlios.de/svnroot/repos/linux-uvc/linux-uvc/trunk/uvc_compat.h
cd -
```

Compile the package:
```
mkdir build
cd build
cmake ..
make
sudo make install
```

If the compilation end with success, you can try to run uvcdynctrl which probably it will return an error:
```
uvcdynctrl -c
uvcdynctrl: error while loading shared libraries: libwebcam.so.0.1.1: cannot open shared object file: No such file or directory
```

To solve create a soft link of the library required:

```
sudo ln -s /usr/local/lib/libwebcam.so.0.1.1 /usr/lib/libwebcam.so.0.1.1
```

Now uvcdynctrl should work but without the focus control:
```
uvcdynctrl -c
Listing available controls for device video0:
Exposure, Auto Priority
Exposure (Absolute)
Exposure, Auto
Backlight Compensation
Sharpness
White Balance Temperature
Power Line Frequency
Gain
White Balance Temperature, Auto
Saturation
Contrast
Brightness

```

Download the package [guvcview]("http://guvcview.berlios.de/") which will allow us to finally control the focus of the camera.
Add the following lines to /etc/apt/source.lst

```
deb http://ppa.launchpad.net/pj-assis/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/pj-assis/ppa/ubuntu intrepid main
```

Import the key
```
gpg --keyserver keyserver.ubuntu.com --recv 9750A93F69FAF7DA
gpg --export --armor 9750A93F69FAF7DA |sudo apt-key add -
```

Update the packages and install guvcview:

```
sudo apt-get update
sudo apt-get install guvcview
```

At this point we need to edit /etc/udev/rules.d/80-uvcdynctrl.rules as follow:
```

###########################################
# Rules for adding dynamic UVC extension unit controls to UVC devices
################################################
ACTION=="add", SUBSYSTEM=="video4linux", DRIVERS=="uvcvideo", ENV{idVendor}="$at
tr{idVendor}", ENV{idProduct}="$attr{idProduct}", RUN+="/lib/udev/uvcdynctrl"
```

Now let's start guvcview as root in order to control the focus of the webcam

```
sudo guvcview
```

use *sudo guvcview* to configure your default settings. Setting auto-focus here will cause the camera to always auto-focus, for example, in Skype.

Bye
Max-B

P.S. Many thanks to [dannyman]("http://ubuntuforums.org/member.php?u=524896") for revisions of this tutorial

---

### Post by Jaym3s on 2009-04-05
This is a great guide, Thank You!

---

### Post by dannyman on 2009-09-09
Hello,

I just ordered this camera and was then advised that the auto-focus is a Windows driver feature.  i see here that you have a way to set the focus, but I wonder is it true auto-focus or is it simply that you can set, say, a fixed focal length for your application . . .

My intention is to use Skype, and yes, in all likelihood I will road-test the instructions next week.  Thank you for posting!

Sincerely,
-daniel

---

### Post by Max-B on 2009-09-10
> **dannyman said:**
> Hello,
I wonder is it true auto-focus or is it simply that you can set, say, a fixed focal length for your application . . .

With guvcview you will have both the possibilities: set manual-focus or switch to auto-focus mode.
bye,
Max-B

---

### Post by dannyman on 2009-09-22
Hello,

Thanks, this is working fine.

A few observations:

[FONT="Courier New"]wget -r[/FONT] without the space. ;)

Should [FONT="Courier New"]apt-get install cmake[/FONT] as a depend.

The key fetching stuff didn't work for me, but isn't required.

I had to symlink [FONT="Courier New"]libwebcam.so.0.1.2[/FONT] . . .

For editing [FONT="Courier New"]80-uvcdynctrl.rules[/FONT] there's a potential cut-and-paste linewrap issue . . . maybe you can wrap that in PRE instead?

[FONT="Courier New"]guvcview[/FONT] runs just fine without [FONT="Courier New"]sudo[/FONT].  Maybe a brief explanation goes "use [FONT="Courier New"]sudo guvcview[/FONT] to configure your default settings.  Setting auto-focus here will cause the camera to always auto-focus, for example, in Skype."

This is slick!  And so far, guvcview is the best webcam app I've seen on Ubuntu.  Things will be nicer once it gets added to the package repository. :)

---

### Post by Max-B on 2009-09-23
Hello Dannyman,
many thanks for yours revisions. I hope this packages will be included soon in the Ubuntu repositories.
Max-B

---

### Post by wlangston on 2009-10-18
This is a terrific guide.  Thanks Max-B.  This procedure worked great on Jaunty-64bit.

> **dannyman said:**
> 
The key fetching stuff didn't work for me, but isn't required.

The key fetching doesn't work if you copy/paste the commands Max-B has but the commands are essentially correct.  I think the double dashes '--' somehow got converted to a longer single dash.  The following commands worked fine for me:

```

gpg --keyserver keyserver.ubuntu.com --recv 9750A93F69FAF7DA
gpg --export --armor 9750A93F69FAF7DA |sudo apt-key add -

```

---

### Post by Max-B on 2009-10-19
> **wlangston said:**
> This is a terrific guide.  Thanks Max-B.  This procedure worked great on Jaunty-64bit

Thanks guys to help me to find all this errors! I corrected the guide. Thanks wlangston!
ciao,
Max-B

---

### Post by scotta3234 on 2009-10-27
In Karmic I can't seem to get this working. Everything was built and no errors reported Even after creating the soft link, I still can't run uvcdynctrl -c. I get this
  libwebcam.so.0.1.2: cannot open shared object file: No such file or directory

Any suggestions?

*Edit - Seem to fix that problem by soft linking 0.1.2 instead of 0.1.1 however I now get this:

 [libwebcam] Warning: The driver behind device video0 does not seem to support V4L2.
[libwebcam] Unable to open device 'video0'. Device not found.
ERROR: Unable to open device.

I have a webcam in this laptop already so im thinking it's trying to use my built in webcam as video0 and this is videoX how should i proceed?

---

### Post by hobo14 on 2010-01-11
If you get

```
[libwebcam] Unable to open device 'video0'. Device not found.
```

do the following:

```

# uvcdynctrl -l     --> this will list your video devices.  Mine is called 'video1'
# uvcdynctrl -d video1 -c   --> This is instead of "uvcdynctrl -c".  Replace video1 with the name of your device found from the prev line.  

```


EDIT: if you had to do the previous stuff, you'll also need to specify the device name again with "-d video1" when you run guvcview too.

Also, 

# sudo apt-get install guvcview

would not work for me, there were missing dependencies that I couldn't install.  I went to the guvcview website [http://guvcview.berlios.de/]("http://guvcview.berlios.de/") and downloaded the .deb package instead, it worked fine.

---

### Post by andersja on 2010-09-24
FYI I think libwebcam is now packaged in the Ubuntu repositories for Maverick.

This should work in the terminal:

```
sudo aptitude install uvcdynctrl
```

More info + examples of usage here:
[http://forum.skype.com/index.php?showtopic=152201](http://forum.skype.com/index.php?showtopic=152201)

See also:
[https://bugs.launchpad.net/ubuntu/+bug/394635](https://bugs.launchpad.net/ubuntu/+bug/394635)

---

### Post by Hans Verschoor on 2010-10-29
And of course it doesn't work !
Got an 401 HTTP response (Authiriztion) when 'wget'-ting the header files uvcvideo.h and uvc_compat.h
Sometimes i had it with Linux.......
Sorry

---

### Post by javierfh on 2010-12-04
did you ever get it working?
i have the same problem as you and im getting to my nerves. the webcam was working perfectly and sudently stopped working...no idea whats going on.
Any help would be really appreciated.

javi

---

### Post by vklyf8812 on 2011-03-08
Hi,

I am new to ubuntuforums and making my first post/reply to this thread.

I get the following message when I try

uvcdynctrl -l

[libwebcam] Warning: The driver behind device video0 does not seem to support V4L2.
Listing available devices:
[libwebcam] Warning: The driver behind device video0 does not seem to support V4L2.

Has anyone else encountered a similar problem and found a work around?

Any help is appreciated!

And, I am using a Microsoft Lifecam on Ubuntu 10.04

Thanks.

---

### Post by francoisroshgezer on 2011-04-15
Hi all!

much like [vklyf8812]("http://ubuntuforums.org/member.php?u=1258235"), with a first fresh (an not very professional...) post in ubuntuforums.

On search on some help with installing the QuickCam Pro 9000 on my lenovo w510 running Lucid I stumbled upon this thread and Max-B's walkthrough - great! Thanks!

But...

as [Hans Verschoor]("http://ubuntuforums.org/member.php?u=832364") has remarked, the wget links for the modified headers require authiriztion, i.e. are out of bounds for us cannon fodder folks. I downloaded the two headers 

uvcvideo.h
uvc_compat.h


from somewhere else (sorry about that... but there seem to be a lot of places to download these from), which didn't quite do it though: make was still complaining about undefined UVC_CONTROL_AUTO_UPDATE. I found a definition of this param at 

[http://lwn.net/Articles/287912/](http://lwn.net/Articles/287912/)

and edited it into ../Common/include/uvcvideo.h which paved the way to a happy install.
I could then read the camera controls, but guvcview could still not make it work - it was addressing the device but getting errors from all controls (and of course no other prog. could either - from Cheese through skype to my own OpenCv project).
Only plugging the camera directly into the usb 3 (not through a hub) did the trick.

I admit not to have worked systematically - I don't really know what was the real cause for the problems and if merely plugging  the camera in the usb 3 would have solved the issue in the first place. Still, if this is of any help to anyone...

cheers!

FrG

---

### Post by Bruffus on 2012-04-30
Dear all,
apparently quickcamteam.net has been discontinued.
Could you help me finding these drivers somewhere else?
With the latest Ubuntu the quickcam pro 9000 works right away, but without autofocus and without mike.

Thanks in advance

---

