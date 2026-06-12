---
title: "Easycap - Somagic - Linux Drivers"
date: 2012-04-14
forum: Hardware
---

### Post by Jose Catre-Vandis on 2012-04-14
This info is for the Somagic variant of the easycap DC60 Video convertor. When you plug it in and do an "lsusb" you should see:
```
Bus 00x Device 00x: ID 1 Somagic, Inc.
```

All the work on this has been done by the guys over on:

[https://code.google.com/p/easycap-somagic-linux/](https://code.google.com/p/easycap-somagic-linux/)

but I thought I would replicate it here following my efforts (so this is not my own work!). The current state of the drivers provides you with two options: the userspace programs and the kernel module (buggy?). The benefit of the kernel module is that it gives you a /dev/videoX device and runs with V4L2.

Here is how to install:

**A. Prerequisites**
GNU/Linux with the following programs and libraries installed: wine, git, make, gcc, libusb-1.0-0 (and development headers), libgcrypt11 (and development headers), mplayer, lsusb (optional). On Ubuntu, that can all be installed by running the following command as root:

```
sudo apt-get install wine git build-essential libusb-1.0-0-dev libgcrypt11-dev mplayer usbutils
```

USB 2.0 capable USB port. USB 1.1 will not work (it's too slow).

Somagic variant of the EasyCAP. To determine that: plug in the EasyCAP, run "lsusb", and verify "1 Somagic, Inc."

EasyCAP USB 2.0 Video Adapter with Audio or EasyCAP002 4-Channel USB 2.0 DVR installation CD-ROM.

**B. Downloading git sources**
Go to your home directory and create a folder called easycap
```
cd
mkdir easycap
cd easycap 
git clone 
```

To update it in the future, use "git pull".

**C. Extracting firmware**
Using wine run
```
Drivers/Setup.exe
```
on the EasyCAP installation CD. This should create a file named either
```
Program Files/Common Files/Somagic/SmiUsbGrabber3C/xp/SmiUsbGrabber3C.sys
```
for the EasyCAP DC60 or
```
Program Files/Common Files/Somagic/SmiUsbGrabber3E/xp/SmiUsbGrabber3E.sys
```
for the EasyCAP002.
Then
```
cd ~/easycap/easycap-somagic-linux/tools/somagic-extract-firmware
```
Run
```
make
```
For the EasyCAP DC60 run
```
cp ~/.wine/drive_c/Program\ Files/Common\ Files/Somagic/SmiUsbGrabber3C/xp/SmiUsbGrabber3C.sys
```
or for the EasyCAP002 run
```
cp ~/.wine/drive_c/Program\ Files/Common\ Files/Somagic/SmiUsbGrabber3E/xp/SmiUsbGrabber3E.sys
```
Run
```
sudo ./somagic-extract-firmware SmiUsbGrabber3C.sys
```
to create "/lib/firmware/somagic_firmware.bin".

**Compiling user space programs**
cd ~/easycap/easycap-somagic-linux/user
Run
```
make && sudo make install
```
**Performing user space capture**
Plug in the EasyCAP device.
Run
```
somagic-init
```
to initialize the EasyCAP device, which changes its USB id. If there is no output, initialization was successful. However, to manually verify whether initialization was successful, re-run "somagic-init" or check "lsusb" for the new id "1 Somagic, Inc" (EasyCAP DC60) or "1 Somagic, Inc" (EasyCAP002).

Activate your video source and ensure video is connected, either via CVBS (composite) or S-VIDEO (EasyCAP DC60), or via "2" (EasyCAP002).

Choose and run a usage example from "man somagic-capture".

I had success with:
```
sudo somagic-capture -c --iso-transfers 100 --pal --sync=1 | mplayer -nocache -vf yadif -demuxer rawvideo -rawvideo "pal:format=uyvy:fps=25" -aspect 4:3 -
```

**Building and using the kernel module**
```
cd ~/easycap/easycap-somagic-linux/kernel/
```
```
make
sudo modprobe videodev
sudo insmod somagic.ko
```
You should now get "something if you run
```
mplayer tv:// -tv driver=
```
where X is the number of your easycap video device

So far I have not been able to get colour or a stable synced picture with the kernel module, but it is early days :)

You can make the kernel permanent and load when you insert the usb device:
```
sudo cp somagic.ko /lib/modules/$(uname -r)/kernel/drivers//media/video
depmod -a
```

**[SIZE="2"]Full kudos and credits to the guys on easycap-somagic-linux[/SIZE]**


n.b. You may have an easycap that is not this device, if so, try here:[http://ubuntuforums.org/showthread.php?t=924504](http://ubuntuforums.org/showthread.php?t=924504)

---

### Post by Jose Catre-Vandis on 2012-04-18
Sources and Debs for Version 1.0 now available:

[https://code.google.com/p/easycap-somagic-linux/downloads/list](https://code.google.com/p/easycap-somagic-linux/downloads/list)

You still need to create the firmware file though

---

### Post by ownaginatious on 2012-04-20
Could you upload either the firmware file or the SmiUsbGrabber3C.sys file? I have the EasyCAP DC60, but the driver CD I got installs with a different sys file than specified in the instructions. The file I get is called "SmiUsbGrabber3F.sys", and it appears that the somagic-extract-firmware utility doesn't like it. When I try extracting the firmware, I get:

```

somagic-extract-firmware SmiUsbGrabber.sys 
Somagic firmware was not found in driver file.

```

I'm going to guess whoever I bought this from tried to screw around with the firmware themselves or something; but judging from what I see online - this device is the exact same as all the other EasyCAP DC60 devices going around.

Thanks!

---

### Post by Jose Catre-Vandis on 2012-04-20
@ ownaginatious

Check your pm's

---

### Post by Jose Catre-Vandis on 2012-04-29
See here:

[http://ubuntuforums.org/showthread.php?t=1964103](http://ubuntuforums.org/showthread.php?t=1964103)

for struggles and my solution to recording from somagic easycap

---

### Post by Jose Catre-Vandis on 2012-05-06
Thought I would share my latest efforts in getting the somagic capture device under control for capturing gameplay from the XBox (for my son!).

First, a bash script, using yad to produce dialogs, to produce a playback window. This script is also run inside the recortding script to check everything is OK before recording, hence the cut down window size. You will need to add your sudo password to the script for it to work, and amned your mplayer line to match your device settings

```
#!/bin/bash
#easycap.sh
#playback for somagic easycap

#VARIABLES
#put your password here to get around the sudo
pass=xxxx
#correct lsusb output for somagic device
capdev=$(lsusb | grep 1c88:003c)

#ensures capture device is setup
if [[ -z $capdev ]]; then
echo $pass | sudo -S somagic-init
sleep 2
fi

#turns on the audio input
amixer set 'Mic',0 'Playback' 'on'
#playback chain
echo $pass | sudo -S somagic-capture --ntsc-4.43-50 --sync=1 | mplayer -ontop -noborder -xy 640 -geometry +100+100 -nocache -vf yadif,crop=708:478:4:2 -demuxer rawvideo -rawvideo "ntsc:format=uyvy:fps=30000/1001" -aspect 1.7777 - &

#dialog to close playback
yad --form --title XBOX-Playback --button gtk-quit:1 --center --width 400 --height 100 --field "Click the Quit Button to Exit":LBL
ret=$?
if [[ $ret -eq 1 ]]; then
killall -9 mplayer
#turns off audio input
amixer set 'Mic',0 'Playback' 'off'
fi
exit 0
```

Second, the capture script, which relies on the playback script for a preview, your sudo password, and your ffmpeg capture chain. If you want to save to a different location you will have to edit the "serverlocation" variable

```
#!/bin/bash
# xboxrec.sh
#recording and encoding script for xbox gameplay

#VARIABLES
#the capture line wouldn't work in a variable so written out in all its glory
#gives time based filename to all output files
fname=xbox$(date +%H%M%S)
#allows for sudo usage without entering a password, add password here
pass=xxxx
#re-encoding line
mp4encode="ffmpeg -i $fname.avi -c:v libx264 -preset veryfast -crf 24 -b:a 128k -y -vf yadif,crop=708:478:4:2 $fname.mp4"
#correct lsusb output for somagic device
capdev=$(lsusb | grep 1c88:003c)
#location for re-encoded file
serverlocation=/xxxx/xxxx/xxxx

#human/manual check that all is connected
xboxup=$(yad --form --center --width 400 --on-top --field="Is XBox Connected and Running?":LBL --title XBOX-Recorder)
if [[ -z $xboxup ]]; then
exit 0
fi

#ensures capture device is setup
if [[ -z $capdev ]]; then
echo $pass | sudo -S somagic-init
sleep 2
fi

#preview output before recording?
yad --form --title XBOX-Recorder --field "Do you want to preview output before recording?":LBL --button gtk-yes:1 --button gtk-no:2 --width 400 --height 100 --on-top --center
ret=$?
if [[ $ret -eq 1 ]]; then
#separate playback only script
$HOME/easycap.sh
fi

#start recording?
record=$(yad --form --center --width 400 --height 100 --on-top --field="Start Recording ?":LBL --title XBOX-Recorder)
if [[ -z $record ]]; then
exit 0
else
#ffmpeg capture chain
echo $pass | sudo -S somagic-capture --ntsc-4.43-50 --sync=1 --iso-transfers 20 -B 149 -C 72 --luminance 2 --lum-aperture 3 | ffmpeg -f rawvideo -pix_fmt uyvy422 -vtag 2vuy -s 720x480 -y -an -r ntsc -i - -f alsa -i hw:0,0 -aspect 1.77 -b:v 2200k $fname.avi &
yad --form --field="Click to Stop Recording...":LBL --button="gtk-stop:1" --width 400 --height 100 --center --on-top --title XBOX-Recorder
ret=$?
if [[ $ret -eq 1 ]]; then
killall -9 ffmpeg
fi
fi

#start encoding
echo "now encoding file"
$mp4encode | yad --progress --width 400 --height 100 --percentage 85 --auto-close --progress-text "Encoding File, Please Wait" --title XBOX-Recorder

#move completed file to server:does file exist?:does server destination exist?:if so move it to server
if [[ -e $fname.mp4 ]] && [[ -e $serverlocation ]]; then 
echo "XBOX directory exists"
mv $fname.mp4 $serverlocation
yad --form --field "Moving Encoded File to Server":LBL --timeout 10 --timeout-indicator bottom --width 400 --height 100 --center --title XBOX-Recorder
else
echo "File Not Moved"
fi

#cleanup:delete avi
yad --form --field "Delete Original recording?":LBL --button gtk-yes:1 --button gtk-no:2 --width 400 --height 100 --title XBOX-Recorder
ret=$?
if [[ $ret -eq 1 ]]; then
rm $fname.avi
fi
exit 0

```

---

### Post by cw9000 on 2012-05-07
All I'm getting is black and white, but I've seen people get color so I thought I would use git and download the module thingy.
oh and its 
```
git clone https://code.google.com/p/easycap-somagic-linux/
```
not just "git clone"
 (BTW I'm using opensuse 12.1) 

Well I go to
 ```

cd ~/easycap/easycap-somagic-linux/kernel
make

```
and I get an error
```

No rule to make target `modules'.  Stop.

```
(actually, before this I get an error that it can't find lib/modules/$uname -r/build   so I made that directory)

I'm not very good at looking at makefiles, but it doesn't appear to have any rules for "modules".
What should I change the makefile to?
Thanks
Oh and good work, everybody, on this project.

---

### Post by cw9000 on 2012-05-07
okay sorry for wasting your time.  I had done an upgrade and hadn't rebooted my system.

---

### Post by Jose Catre-Vandis on 2012-05-08
Did you get colour?

I found I had to work my way through all the output options to find the one that worked. Should have been pal but wasn't! Different options for xbox gameplay to xbox dvd playback!

Please share your command line chain for successful output and include hardware being used (e.g. capture from etc.)

---

### Post by cw9000 on 2012-05-11
No I didn't get color.  sorry, I just meant that I could compile the module.  I know nothing about programming modules, so I'm reading up on it over at tldp.org.  It's interesting.


all I do to get output is open up vlc and use file->open capture device and select video4linux2, video device: video1, audio device: hw 0,0 (mic).  And all I have connected to it is the video out of a vcr. 

I'm using DC60-2021.  The only thing I've done with command line is what you've suggested at your posted ubuntu forum link.  Thanks for that btw.

The only thing I've seen color of were the "eascap-somagic-linux/Samples/NTSC_Images". I figured those color images meant someone has color.

I noticed that I had paused vlc playback and left my computer and left the vcr on "play".  When I returned 30 minutes later, I hit "play" on vlc, and although the vcr had stopped, there was still 30 minutes in some kind of buffer, vlc just picked up where it left off.  Where is this buffer, I was wondering? I searched for really big files and couldn't find it. oh well, not really a big deal, just wondering.

EDIT:  okay, strange.  I selected NTSC on video standard in vlc and I have color.  Why I didn't try that earlier,I have no idea.   Now how do I SAVE the stream in color?

---

### Post by Jose Catre-Vandis on 2012-05-12
vlc has a recording function (you may need to tick a box to get it to show up on the interface) so try this first, otherwise you can try calamari's x264 recording script on the google group pages or something like this with ffmpeg/mplayer:
```
somagic-capture --ntsc-4.43-50 --sync=1 --iso-transfers 20 -B 149 -C 72 --luminance 2 --lum-aperture 3 | ffmpeg -f rawvideo -pix_fmt uyvy422 -vtag 2vuy -s 720x480 -y -an -r ntsc -i - -f alsa -i hw:0,0 -aspect 1.77 -b:v 2200k output.avi
``` (You may need to change some settings, especially the ntsc-4.43-50)

---

### Post by cw9000 on 2012-05-12
I don't know what happened.  A couple days ago your command using  somagic-capture and piping that to ffmpeg worked fine.  Now its like  somagic isn't sending the data to ffmpeg.  ffmpeg starts fine, but it  doesn't record any frames, it just stays on 0 fps.

( I should mention, ffmpeg says pix_fmt uyvy422 isn't compatible with mpeg4, so it changed it to yuv420p.)

however, I can just use ffmpeg
```
ffmpeg -f rawvideo -pix_fmt uyvy422 -vtag 2vuy -s 720x480 -y -an  -r ntsc -i /dev/video1 -f alsa -i hw:0,0 -aspect 1.77 -b:v 2200k  output.avi

```

note the /dev/video1.
This comes in color, however I get that darn  "Alsa buffer xrun", and the output isn't synced and skips a bit.  I  tried changing the -b:v from 500k - 3000k and nothing helped (kept  getting alsa buffer xrun, AND output isn't synced). 

 I think I was  getting it synced right with the black and white using somagic-capture.   somagic capture , when NOT piped to ffmpeg(just by itself) , now gives me  "Claim Failed with error -6"  Don't know what that's about.  anybody know how to get somagic-capture working again?  Oh and I can't rmmod somagic.ko.  There is always some process using it.  I could rmmod -f   but I'd like to do it safely.

---

### Post by cw9000 on 2012-05-12
oh, and vlc says "Streaming/Transcoding failed, cannot open encoder", no matter what I try.  Again, I'm using Opensuse 12.1, kernel 3.1.10-1.9-desktop

just so other people with better luck than me:
to record, instead of hitting play in the "open capture device" dialog, you hit the arrow next to it and go down to "convert" and then it opens up another dialog where you put all your settings and filename.

---

### Post by cw9000 on 2012-05-12
well, I ended up just taking the easycap out and plugging it back in.  This allowed me to rmmod somagic.  And then somagic-capture worked again.  So now I have it working with
```
somagic-capture --ntsc --sync=1 --iso-transfers 20 | ffmpeg -f rawvideo -pix_fmt yuv420p -vtag 2vuy -s 720x480 -y -an -r ntsc -i - -f alsa -i hw:0,0 -b:v 2200k output.avi
```

I didn't care for the brightness and contrast change.  and I'm using ntsc (60hz) rather than the 50hz since most things I have used in the past say 29.97 fps.

so, I don't really know what changed, but its working now, thanks.

---

### Post by Jose Catre-Vandis on 2012-05-12
Yay!!

:)

---

### Post by Igor Isaias Banlian on 2012-05-16
Hello, I have a dongle (USB) to watch analog TV called **EasyTV Analog**. It is identified in **GNU/Linux** as:

**Bus 001 Device 008: ID 1c88:0035 Somagic, Inc.**

More information about it on the link below:

**Hungary:** _[http://logout.hu/bejegyzes/azbest/easytv_astar_ast-s-c-u09_analog_usb_tv_tuner/hsz_1-50.html]("http://logout.hu/bejegyzes/azbest/easytv_astar_ast-s-c-u09_analog_usb_tv_tuner/hsz_1-50.html")_

**English:** _[http://translate.google.com/translate?hl=pt&sl=hu&tl=en&u=http%3A%2F%2Flogout.hu%2Fbejegyzes%2Fazbest%2Feasytv_astar_ast-s-c-u09_analog_usb_tv_tuner%2Fhsz_1-50.html]("http://translate.google.com/translate?hl=pt&sl=hu&tl=en&u=http%3A%2F%2Flogout.hu%2Fbejegyzes%2Fazbest%2Feasytv_astar_ast-s-c-u09_analog_usb_tv_tuner%2Fhsz_1-50.html")_

**Portuguese:** _[http://translate.google.com/translate?hl=pt&sl=hu&tl=pt&u=http%3A%2F%2Flogout.hu%2Fbejegyzes%2Fazbest%2Feasytv_astar_ast-s-c-u09_analog_usb_tv_tuner%2Fhsz_1-50.html]("http://translate.google.com/translate?hl=pt&sl=hu&tl=pt&u=http%3A%2F%2Flogout.hu%2Fbejegyzes%2Fazbest%2Feasytv_astar_ast-s-c-u09_analog_usb_tv_tuner%2Fhsz_1-50.html")_

And I would love to be able to use it in **Ubuntu**, so I wanted to know if you of **easycap-somagic-linux** also develop a driver for it...

_**Note:**_

Drivers for ***Windows XP 32-bit***, ***Vista 32-bit***, ***Vista 64-bit***, ***Seven 32-bit***, ***Seven 64-bit***: [http://www.4shared.com/zip/doWe5zkj/AstUsbAtvFM35.html]("http://www.4shared.com/zip/doWe5zkj/AstUsbAtvFM35.html") (***astusbatvfm35.cat, AstUsbAtvFM35.inf, AstUsbAtvFM35.sys, devcon.exe***) [Does _not work_ with *ndiswrapper -l | astusbatvfm35 : invalid driver!*]

**Tunner:**

[IMG]http://logout.drag2web.com/easytv/tuner.jpg[/IMG]

**Decoder:**

[IMG]http://logout.drag2web.com/easytv/adc.jpg[/IMG]

*Sorry for my bad English... I am Brazilian!*

Regards,
Igor Isaias Banlian

---

### Post by Jose Catre-Vandis on 2012-05-16
@ Igor

Not seen anything on the easycap-somagic google groups about the easytv dongle, sorry. Might be better to start a new thread for this one.

---

### Post by pepsimachine15 on 2012-05-16
I also have an easycap002 device that installs the driver SmiUsbGrabber3F.sys and not 3E as expected. I noticed another user also had this issue with his DC60 device. I'm wondering if this new 3F variant is just a combination of both drivers into one file, and the extractor needs updated.

In the meantime, could someone send me the driver for the 002? it is unavailable using a google search.

---

### Post by Jose Catre-Vandis on 2012-05-17
@ pepsimachine, is yours the one with multiple video inputs?

---

### Post by pepsimachine15 on 2012-05-17
yes, it is the "002" device with 4 cvbs inputs and 1 audio.

I also posted a message to the google code project for this device but my account is still waiting approval. i'm hoping they will be able to update the extraction program for the new driver file.

---

### Post by pepsimachine15 on 2012-05-19
bump

anyone with the 3E version of the driver they could send me?

---

### Post by Jose Catre-Vandis on 2012-05-19
Can't help as the E version doesn't come on the C "CD"

Try here:

```
http://easycapexpertti.phpbb3now.com/viewtopic.php?f=13&t=7
```

---

### Post by pepsimachine15 on 2012-05-20
thanks, i did try there. i actually tried everywhere i could possible google. i was able to download a C version in a zip file, but still cannot find an E version anywhere. maybe someone on this forum will read this and be kind enough to upload one to mediafire or something for me.

---

### Post by achillesmyr on 2012-06-12
[COLOR=#888888][FONT=arial][COLOR=#333333]I have a usb-dvr Model DC60 dvd Somagic with yellow dvd of software.
I had a plan to use it for cctv cameras using zoneminder. I will connect to a cctv camera.
all such processes in the post a tutorial I have done well to be detected / dev/video0.
When I try testing with soft **tvtime** is displayed the color green or blank.
Similarly, when I use zoneminder result is a dark picture.

Info: Ubuntu Desktop i386 12:04

Thanks for the help.[/COLOR]

[COLOR=#444444]****[/COLOR]
[COLOR=#444444][B]


[/B][/COLOR]



[/FONT][/COLOR]

---

### Post by valenzuela on 2012-06-29
Dear all,

can you tell me the option to use with the "somagic-capture" command, to show different input video in a Somagic EasyCAP002 device?


I already can obtain video from the mentioned device, through "2" input video (man somagic-capture shows "For the EasyCAP DC60, use the CVBS (composite) input  for  video capture.   For  the EasyCAP002, use the "2" input for video capture.  This is the default.")


How can I capture different input video? (Somagic EasyCAP002 device has four input channels).


Kind regards,
Valenz

---

### Post by ltcong on 2012-08-25
Dear Jose,

I got errors when trying to follow "**make**" in "[B]Building and using the kernel module".
[/B]I compiled the kernel module on Ubuntu having kernel: 2.6.35-22-server
The errors are as follows:
make -C /lib/modules/2.6.35-22-server/build M=/root/Downloads/easycap/easycap-somagic-linux/kernel modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-server'
  CC [M]  /root/Downloads/easycap/easycap-somagic-linux/kernel/somagic_video.o
/root/Downloads/easycap/easycap-somagic-linux/kernel/somagic_video.c: In function ‘allocate_scratch_buffer’:
/root/Downloads/easycap/easycap-somagic-linux/kernel/somagic_video.c:188: error: implicit declaration of function ‘vmalloc_32’
/root/Downloads/easycap/easycap-somagic-linux/kernel/somagic_video.c:188: warning: assignment makes pointer from integer without a cast
/root/Downloads/easycap/easycap-somagic-linux/kernel/somagic_video.c: In function ‘free_scratch_buffer’:
/root/Downloads/easycap/easycap-somagic-linux/kernel/somagic_video.c:211: error: implicit declaration of function ‘vfree’
/root/Downloads/easycap/easycap-somagic-linux/kernel/somagic_video.c: In function ‘rvmalloc’:
/root/Downloads/easycap/easycap-somagic-linux/kernel/somagic_video.c:237: warning: assignment makes pointer from integer without a cast
/root/Downloads/easycap/easycap-somagic-linux/kernel/somagic_video.c: In function ‘vdev_init’:
/root/Downloads/easycap/easycap-somagic-linux/kernel/somagic_video.c:1533: error: ‘struct video_device’ has no member named ‘lock’
make[2]: *** [/root/Downloads/easycap/easycap-somagic-linux/kernel/somagic_video.o] Error 1
make[1]: *** [_module_/root/Downloads/easycap/easycap-somagic-linux/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-server'
make: *** [all] Error 2

Please help me!

---

### Post by nevixa on 2012-11-20
Thank you for the useful guide! I have one problem however:

When I follow the steps under **Building and using the kernel module**, the insmod command gives me the following error:
```
insmod: error inserting 'somagic.ko': -1 Unknown symbol in module
```I also can't seem to get the somagic-capture command to work. I didn't get any errors during all the steps. 

I'm running Ubuntu 12.04 and have a Somagic 4 channel input (the 3F version).

Thank you

---

### Post by monsterbash on 2012-11-21
> **pepsimachine15 said:**
> thanks, i did try there. i actually tried  everywhere i could possible google. i was able to download a C version  in a zip file, but still cannot find an E version anywhere. maybe  someone on this forum will read this and be kind enough to upload one to  mediafire or something for me.

I have the same problem..... I just got 2 "4 Ch USB DVR" with 4 yellow composit video inputs (numbered from 1 to 4) and 1 white audio input (without any marks), detected as:

Bus 001 Device 013: ID 1c88:0007 Somagic, Inc. SMI Grabber (EasyCAP DC60+ clone) (no firmware) [SMI-2021CBE]

As far as I read (at easycap-somagic-linux) this model will need one of these drivers:
SmiUsbGrabber3f.sys
or
SmiUsbGrabber3e.sys

Problem is that I don't have the installation CDs anymore and could not find none of those drivers on-line..... Just found the "c" version....

I would appreciate If any1 could upload those drivers (versions "f" or "e").

Thanks in advance !!!

---

### Post by Gawains Green Knight on 2012-12-17
> **ownaginatious said:**
> Could you upload either the firmware file or the SmiUsbGrabber3C.sys file? I have the EasyCAP DC60, but the driver CD I got installs with a different sys file than specified in the instructions. The file I get is called "SmiUsbGrabber3F.sys", and it appears that the somagic-extract-firmware utility doesn't like it. When I try extracting the firmware, I get:

```

somagic-extract-firmware SmiUsbGrabber.sys 
Somagic firmware was not found in driver file.

```

I'm going to guess whoever I bought this from tried to screw around with the firmware themselves or something; but judging from what I see online - this device is the exact same as all the other EasyCAP DC60 devices going around.

Thanks!
Hi

I have exactly the problem - did you ever sort it out?

---

### Post by JohnnyDisco on 2013-01-04
I have the same problem and I have the device with the 4 video inputs and 1 white one:

Bus 001 Device 013: ID 1c88:0007 Somagic, Inc. SMI Grabber (EasyCAP DC60+ clone) (no firmware) [SMI-2021C]

I have a white mini CD sat in front of me with the drivers etc on but get the same "Somagic firmware was not found in driver file" when I try and extract from the SmiUsbGrabber3F.sys.  

Happy to DD an image of the CD up to the cloud or use my Zip with all the files from /program files/common files/Somagic if that helps any one figure this out.

---

### Post by JohnnyDisco on 2013-01-04
This should fix the issue.


[LIST=1]
[*]Download the source code for the tools here ```
wget [https://easycap-somagic-linux.googlecode.com/files/somagic-easycap-tools_1.0.tar.gz]("https://easycap-somagic-linux.googlecode.com/files/somagic-easycap-tools_1.0.tar.gzhttp://")
```
[*]Install build-essential and the necessary library's you may need, I had to ```
apt-get install build-essential libgcrypt11-dev libusb-1.0-0-dev
```
[*]Unpack with ```
tar xvf somagic-easycap-tools_*VERSION*.tar.gz
```
[*]Then change directory into somagic-extract-firmware and rename somagic-extract-firmware.c to .backup
[*]Go to [http://code.google.com/p/easycap-somagic-linux/source/browse/tools/somagic-extract-firmware/somagic-extract-firmware.c?r=b4e1adcd7535d2487e5bbdaa54686f6fa087ddc1](http://code.google.com/p/easycap-somagic-linux/source/browse/tools/somagic-extract-firmware/somagic-extract-firmware.c?r=b4e1adcd7535d2487e5bbdaa54686f6fa087ddc1) and copy the new source code from here which includes our 3f support.
[*]Now create a new file ```
nano somagic-extract-firmware.c
``` and paste what you copied from the site.
[*]Now run ```
make
``` and then ```
make install
```
[*]You should now have installed the new somagic-extract tool which does extract the 3f file correctly!
[/LIST]
I've attached the binary I made of the tool, if you copy this to the directory of your driver you can run without installing.

Let me know if it works, I'm now stuck on the next stage...

---

### Post by JohnnyDisco on 2013-01-04
Wow!  It still needed more work to actually use the firmware, I have to recompile everything with tweaks but I just got it to initialise... have yet to try the actual capture but I finally got the following.  Will write up shortly...

johnnydisco-ThinkPad-R61e user # lsusb
Bus 002 Device 006: ID 1c88:0007 Somagic, Inc. SMI Grabber (EasyCAP DC60+ clone) (no firmware) [SMI-2021CBE]
Bus 003 Device 002: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
johnnydisco-ThinkPad-R61e user # ./somagic-init 
johnnydisco-ThinkPad-R61e user # lsusb
Bus 002 Device 007: ID 1c88:003f Somagic, Inc. 
Bus 003 Device 002: ID 0a5c:2110 Broadcom Corp. Bluetooth Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by SteveDee on 2013-01-16
> **JohnnyDisco said:**
> ...It still needed more work to actually use the firmware...

I just bought one of these Somagic 4 channel devices: [http://www.amazon.co.uk/Channel-Video-Capture-Camera-Monitor/dp/B005OFKXXK/ref=sr_1_33?s=electronics&ie=UTF8&qid=1358359194&sr=1-33](http://www.amazon.co.uk/Channel-Video-Capture-Camera-Monitor/dp/B005OFKXXK/ref=sr_1_33?s=electronics&ie=UTF8&qid=1358359194&sr=1-33)
..and I'm trying to get it to work.

I can extract the firmware, and is says its written successfully. 

But somagic-init says the file is not recognised.

So any help would be much appreciated.

I think this is what I did:-

On Windows 7:-
Driver: run driver\setup.exe in Windows then found SmiUsbGrabber3F.sys in xp driver folder & copy to Linux machine.

On Linux (Lubuntu 12.10):-
Download/install from here: [http://code.google.com/p/easycap-somagic-linux/downloads/list](http://code.google.com/p/easycap-somagic-linux/downloads/list)
    * somagic-easycap_1.0_i386.deb
    * somagic-easycap-tools_1.0_i386.deb

Install dependencies and suggested packages with:-
 sudo apt-get install libusb-1.0-0 libgcrypt11 mplayer usbutils

 sudo wget [https://easycap-somagic-linux.googlecode.com/files/somagic-easycap-tools_1.0.tar.gz](https://easycap-somagic-linux.googlecode.com/files/somagic-easycap-tools_1.0.tar.gz)

 sudo apt-get install build-essential libgcrypt11-dev libusb-1.0-0-dev

Unpack tools source:-
 sudo tar xvf somagic-easycap-tools_1.0.tar.gz

Change directory into somagic-extract-firmware and rename somagic-extract-firmware.c to .org
Copy new source code (text) from [http://code.google.com/p/easycap-som...686f6fa087ddc1](http://code.google.com/p/easycap-som...686f6fa087ddc1)  which includes 3f support into a new file: somagic-extract-firmware.c.

 sudo make
 sudo make install

 somagic-extract-firmware SmiUsbGrabber3F.sys
   {Firmware written to /lib/firmware/somagic_firmware.bin}
 
 lsusb still says 1c88:0007
 
somagic-init
   {Firmware file /lib/firmware/somagic_firmware.bin was not recognized}

---

### Post by gorotman on 2013-01-18
Hi all.
I have an easycap DC60. 
I used all your guides (installed from deb and also from git, firmware ok and kernel modules loaded).
Now it create the /dev/videoX device.
But every it appears busy, thus no video capture is possible.
I tried with ffmpeg, mplayer, vlc and qv4l2, all give me same response.
....Any idea for help me, please?

Some infos:
Ubuntu 12.10 64bit fresh installation and upgraded.

somagic-capture --test-only's output:
Failed to claim device interface: Device or resource busy

Thanks in advance :D
gorotman

---

### Post by JohnnyDisco on 2013-01-21
> lsusb still says 1c88:0007
 
somagic-init
   {Firmware file /lib/firmware/somagic_firmware.bin was not recognized} 	

Sorry, I haven't been in the forum for a couple of weeks and working on other stuff.  I hope you worked it out because it's difficult to remember the exact steps but essentially you will have the same issue with the init binary file as the firmware extract binary i.e. it doesn't know about the 'f' variety of the device so you need the source code to recompile one which recognises the 3f.

From memory this is what I did:


[LIST]
[*]Unpack tools source:-
 sudo tar xvf somagic-easycap-tools_1.0.tar.gz
[*]Change directory into user and rename somagic-init.c to .org
Copy new source code (text) from [http://code.google.com/p/easycap-somagic-linux/source/browse/user/somagic-init.c]("http://code.google.com/p/easycap-som...686f6fa087ddc1")  which includes 3f support into a new file: somagic-init.c.
[*]sudo make
[*]sudo make install
[/LIST]
Then I got the updated result from lsusb.  I've not had time to figure out the rest following on from this so let me know how you get on.


Also take a look here:


[http://code.google.com/p/easycap-somagic-linux/issues/detail?id=11](http://code.google.com/p/easycap-somagic-linux/issues/detail?id=11)


It's kinda cutting edge but several people are having similar issues to us.



Thanks,
Johnny

---

### Post by SteveDee on 2013-01-21
> **JohnnyDisco said:**
> ...It's kinda cutting edge but several people are having similar issues to us...

I managed to get this working (kind of) on Saturday.

Basically, after downloading the source files (including tools) there are 3 files which must be replaced: somagic-extract-firmware.c, somagic-init.c, somagic-capture.c

I've just been allowed to join the Somagic group here: [http://code.google.com/p/easycap-somagic-linux/](http://code.google.com/p/easycap-somagic-linux/) so you can take a look at the questions I have just posted.

I've attached an image to show the video problem I have.

---

### Post by warzo on 2013-02-04
Hi,
im new to this forum and also to this thread as i got my easycap just some days ago, and now im trying to get it to work under linux. I followed this well writen guide 
(I got the f model so i had to compile it in order to get it to extract and initiate, but that all seems fine, lsusb gives me "Bus 001 Device 003: ID 1c88:003f Somagic, Inc.")
and have gotten as far as 
 
"sudo somagic-capture -c --iso-transfers 100 --pal --sync=1 | mplayer -nocache -vf yadif -demuxer rawvideo -rawvideo "pal:format=uyvy:fps=25" -aspect 4:3 -"
 
This does give me a "libusb_submit_transfer failed with error -1" and "Failed to open VDPAU backend libvdpau_nouveau.so: cannot open shared object file: No such file or directory" Then as it says starting playback a windows popup and disapear and then "Exiting... (End of file)" and im back at the normal terminal.

Further more I tride "sudo modprobe videodev" after running make in the kernel directory and i get no errors but I also get no /dev/video* devices or other video device in /dev. Nor do i get any errors with "sudo insmod somagic.ko".

Anyone able to give a hint what to do or look for next?

---

### Post by SteveDee on 2013-02-05
> **warzo said:**
> ...Anyone able to give a hint what to do or look for next?

I'm curious about which version and flavour of 'buntu your are using?

Could you also try:-
```

sudo somagic-capture --iso-transfers=20 | mplayer -vf yadif,screenshot -demuxer rawvideo -rawvideo "pal:format=uyvy:fps=25" -aspect 4:3 -

```

---

### Post by warzo on 2013-02-07
> **SteveDee said:**
> I'm curious about which version and flavour of 'buntu your are using?
 
Could you also try:-
```

sudo somagic-capture --iso-transfers=20 | mplayer -vf yadif,screenshot -demuxer rawvideo -rawvideo "pal:format=uyvy:fps=25" -aspect 4:3 -

```
 
Sorry I forgot to tell ubuntu version. The version I'm using is 12.04 LTS.

I tried that code above.. the output is:
```

$ sudo somagic-capture --iso-tranfers=20 | mplayer -vf yadif,screenshot -demuxer rawvideo -rawvideo "pal:format=uyvy:fps=25" -aspect 4:3 -
Option rawvideo: Unknown suboption format
Error parsing option on the command line: -rawvideo
MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team

```

After the last line nothing happens, it just sits there and I have to do ctrl+c to be able to do something else with that terminal.

---

### Post by SteveDee on 2013-02-07
> **warzo said:**
> Sorry I forgot to tell ubuntu version. The version I'm using is 12.04 LTS...

I'm using Lubuntu 12.10. My output:-
```

steve@steve-Compaq:~$ sudo somagic-capture --iso-transfers=30 | mplayer -vf yadif,screenshot -demuxer rawvideo -rawvideo "pal:format=uyvy:fps=25" -aspect 4:3 -
MPlayer svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing -.
Reading from stdin...
rawvideo file format detected.
Load subtitles in ./
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
Opening video filter: [screenshot]
Opening video filter: [yadif]
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
[swscaler @ 0x9363780] using unscaled uyvy422 -> yuv420p special converter
VO: [xv] 720x576 => 768x576 Planar YV12 
Selected video codec: [rawuyvy] vfm: raw (RAW UYVY)
==========================================================================
Audio: no sound
Starting playback...

```

...looks like I have a different set of problems.

---

### Post by warzo on 2013-02-08
I have no idea what I've done but now i get as far as 

```
MPlayer svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing -.
Reading from stdin...
```

And there it stops. it does not conitune from there on. But when i hit ctrl+c it prints this

```

MPLayer interrupted by signal 2 in module: demux_open
rawvideo file format detected.
Load subtitles in ./
Failed to open VDPAU backend libvdpau_nvidia.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
Opening video filter: [screenshot]
Opening video filter: [yadif]
==========================================================================
Opening video decoder: [raw] RAW Uncompressed Video
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
[swscaler @ 0xa446d80] using unscaled uyvy422 -> yuv420p special converter
VO: [xv] 720x576 => 768x576 Planar YV12 
Selected video codec: [rawuyvy] vfm: raw (RAW UYVY)
==========================================================================
Audio: no sound
Starting playback...
V:    0.0    0/    0 ??% ??% ??,?% 0 0

Exiting... (Quit)

```

---

### Post by SteveDee on 2013-02-08
> **warzo said:**
> I have no idea what I've done...

[code]MPlayer svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team



It looks like you've upgraded something as "built with gcc-4.6" is now 4.7.

Have you got a working camera connected to input #2?  (You won't see a video display window if camera is connected to input #1).

---

### Post by warzo on 2013-02-08
Sorry, typo, it was gcc-4.6. I do not type in this forum with the same computer as the one i do my testing on.

I have had a camera connected to input 1, but i connected it to input 2 now (counting the input from 1-4). But still the same thing. 

When I hit ctrl+c i can see a windows pop up real quickly but it disapear right away.

---

### Post by SteveDee on 2013-02-09
> **warzo said:**
> ...and there it stops. it does not conitune from there on. But when i hit ctrl+c it prints this...

It looks like its waiting for a signal from your camera. I don't have any intelligent suggestions, just a few diagnostic tips (which you may have already tried).

If a test with one config does not work, unplug then reconnect the EasyCap, change whatever (maybe plug camera into a different input) then do the "somagic-init, ususb, somagic-capture" sequence again. I don't know why, but when things don't work you seem to need to start again with this software.

If you haven't already done this, I would connect the EasyCap + camera to an MS Windows computer and test with the "SuperViewer" supplied with the device disk, it looks like this:-
 [http://1.bp.blogspot.com/-nhRKnbKRQ7A/UQkSUnMxjZI/AAAAAAAAAQY/wec2G1BZz5g/s1600/EasyCapSomagicWin7.jpg](http://1.bp.blogspot.com/-nhRKnbKRQ7A/UQkSUnMxjZI/AAAAAAAAAQY/wec2G1BZz5g/s1600/EasyCapSomagicWin7.jpg)

This will establish that the hardware is working, and you can also confirm that the inputs are labelled correctly (e.g. input "2" is really input "2").

Upgrading you computer from 12.04 to 12.10 may be undesirable, but if you have a spare USB memory stick you could try booting with 12.10 from the stick, installing Somagic software, and testing with this. That may eliminate the difference in mplayer build between your system and mine. If fact, if I get some time next week I may create a 12.04 USB and check it for myself.

---

### Post by warzo on 2013-02-09
> **SteveDee said:**
> It looks like its waiting for a signal from your camera. I don't have any intelligent suggestions, just a few diagnostic tips (which you may have already tried).
 
If a test with one config does not work, unplug then reconnect the EasyCap, change whatever (maybe plug camera into a different input) then do the "somagic-init, ususb, somagic-capture" sequence again. I don't know why, but when things don't work you seem to need to start again with this software.
 
If you haven't already done this, I would connect the EasyCap + camera to an MS Windows computer and test with the "SuperViewer" supplied with the device disk, it looks like this:-
[http://1.bp.blogspot.com/-nhRKnbKRQ7A/UQkSUnMxjZI/AAAAAAAAAQY/wec2G1BZz5g/s1600/EasyCapSomagicWin7.jpg](http://1.bp.blogspot.com/-nhRKnbKRQ7A/UQkSUnMxjZI/AAAAAAAAAQY/wec2G1BZz5g/s1600/EasyCapSomagicWin7.jpg)
 
This will establish that the hardware is working, and you can also confirm that the inputs are labelled correctly (e.g. input "2" is really input "2").
 
Upgrading you computer from 12.04 to 12.10 may be undesirable, but if you have a spare USB memory stick you could try booting with 12.10 from the stick, installing Somagic software, and testing with this. That may eliminate the difference in mplayer build between your system and mine. If fact, if I get some time next week I may create a 12.04 USB and check it for myself.

I've tried it in windows 7 with the supplyed software and it works, though i have only tested channel 1. I could try it on all four channels to see that they are correctly labled and working. I got two separate harddrives that i can swap because it is a computer only for testing this cameracaputer thing out, so i have a disk with windows and anotherone with ubuntu. (have a well equiped lab of my own here at home, with old computerparts :) )

What is that ususb, what does that do and when should that be done?

But I will put if off til tomorrow this testing, as i got other plans for tonight. Tanks for the help so far, i'll get back when i have more information to share.

---

### Post by SteveDee on 2013-02-09
> **warzo said:**
> ...What is that ususb, what does that do and when should that be done?...

Sorry, just a typo error. It should have been: lsusb {just to check that init worked}

---

### Post by warzo on 2013-02-10
I booted into windows 7 and tried each and every channel, and they all apear in the right order and they all work.

As for lsub i see "Buss 001 Device 002: ID 1c88:003f Somagic, Inc."

But this time when I booted into ubuntu i got it to open the mplayer windows. When the camera was connected to channel one it opened the mplayer but i was noi picture, when i pluged the camera into ch.2 the mplayer windows would not open (same as before), but when I pluged it into ch.3 i got picture.

I found that the easycap is /dev/bus/usb/001/004 (at this point). But still I dont have like /dev/video[0-3]. And I find no other devs to get the picture from. So I cant get the picture in to zoneminder for example.

---

