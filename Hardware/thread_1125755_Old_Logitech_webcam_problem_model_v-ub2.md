---
title: "Old Logitech webcam problem model v-ub2"
date: 2009-04-14
forum: Hardware
---

### Post by Fazl on 2009-04-14
First off, I just want to let everyone know that I am a newbie at Linux and am just stumbling my way through this. With that said, here is my issue.

I have an IBM T43 running Xubuntu 8.10. I have a Logitech Quickcam Express that I am trying to get working with my Skype, Cheese, and VLC but I can't seem to get the programs to recognize the camera. I have the drivers loaded and when I go to Terminal, the camera shows up like this

fazl@fazl-laptop:~$ dmesg

[23848.092040] usb 6-1: new full speed USB device using uhci_hcd and address 6
[23848.283483] usb 6-1: configuration #1 chosen from 1 choice
[23848.287897] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.6 $Date: 2006/11/04 08:38:14 $)
[23848.287904] quickcam: Kernel:2.6.27-11-generic bus:6 class:FF subclass:FF vendor:046D product:0870
[23848.316102] quickcam: Sensor HDCS-1000/1100 detected
[23848.319297] quickcam: Registered device: /dev/video0

fazl@fazl-laptop:~$ lsusb

Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 006: ID 046d:0870 Logitech, Inc. QuickCam Express
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

fazl@fazl-laptop:~$ lsmod | grep video

videodev               41344  1 quickcam
v4l1_compat            22404  1 videodev
video                  25232  0 
output                 11008  1 video


To me, it seems that Xubuntu recognizes the webcam, but when I try to run Cheese with the webcam from Terminal, I get

fazl@fazl-laptop:~$ cheese -d /dev/video0
** Message: Error: Stream contains no data.
gsttypefindelement.c(785): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream


** (cheese:26044): WARNING **: could not generate thumbnail for /home/fazl/Videos/Webcam/2009-04-14-172355.ogv (video/ogg)


(cheese:26044): Gtk-CRITICAL **: gtk_widget_queue_draw: assertion `GTK_IS_WIDGET (widget)' failed
 

For some reason, I don't get any data coming from the webcam. I know it works because I had it working on my computer when it was an XP machine. When I try to get the webcam on Skype, or VLC, it doesn't even recognize that there is any camera installed.

I'd like to get this working because if I have a computer where the drivers are running properly but I cannot get the data to the programs, I don't see how another camera would help.I don't know if I am missing any specific modules or anything and honestly, I really have no idea what I am doing in this. The person who installed Xubuntu for me doesn't have any ideas either and I've actually had more luck making stuff work than he has! Is there anyone who can help??!!!

---

### Post by Denestria on 2009-04-14
[The ubuntu wiki]("https://wiki.ubuntu.com/SkypeWebCams") lists your camera as *Works with gstfakevideo - but unstable.*
Logitech Quickcam Express - Ubuntu 7.10 - 046d:0870 - quickcam

and links to this post about getting gstfakevideo installed and working.
[http://ubuntuforums.org/showthread.php?p=3856516#post3856516/](http://ubuntuforums.org/showthread.php?p=3856516#post3856516/)

---

### Post by Fazl on 2009-04-14
Thanks for the help. Seems like its making some progress although I am a little lost as to what I am doing. So far, this is what I did. I followed the command codes

fazl@fazl-laptop:~$ svn checkout [http://gstfakevideo.googlecode.com/svn/trunk/](http://gstfakevideo.googlecode.com/svn/trunk/) gstfakevideo

A    gstfakevideo/README-AMD64
A    gstfakevideo/gstfakevideo
A    gstfakevideo/gstfakevideo.c
A    gstfakevideo/README
A    gstfakevideo/Makefile
A    gstfakevideo/gst.c
Checked out revision 3.

fazl@fazl-laptop:~$ sudo apt-get install libgstreamer0.10-dev pkg-config

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgstreamer0.10-dev is already the newest version.
pkg-config is already the newest version.
pkg-config set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

fazl@fazl-laptop:~$ cd gstfakevideo

fazl@fazl-laptop:~/gstfakevideo$ make

gcc -O2 -Wall -m32  `pkg-config gstreamer-0.10 --cflags` -ldl `pkg-config gstreamer-0.10 --libs` -shared -fpic gst.c gstfakevideo.c -o libgstfakevideo.so
gst.c: In function ‘cb_handoff’:
gst.c:85: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result

fazl@fazl-laptop:~/gstfakevideo$ sudo make install

cp libgstfakevideo.so /usr/local/lib
chmod 0755 /usr/local/lib/libgstfakevideo.so
cp gstfakevideo /usr/local/bin
chmod 0755 /usr/local/bin/gstfakevideo

fazl@fazl-laptop:~/gstfakevideo$ sudo mv/dev/video0

sudo: mv/dev/video0: command not found

fazl@fazl-laptop:~/gstfakevideo$ sudo mv /dev/video0

mv: missing destination file operand after `/dev/video0'
Try `mv --help' for more information.

fazl@fazl-laptop:~/gstfakevideo$ gstfakevideo v4lsrc device=/dev/video1 ! ffmpegcolorspace

gst.c create_pipeline (155): pipeline created
gst.c create_pipeline (159): pipeline linked
gst.c shim_ioctl (201): request=80685600 nr 0
gst.c shim_ioctl (313): result=-1 error=515 Unknown error 515

gst.c shim_ioctl (201): request=803c7601 nr 1
gst.c shim_ioctl (208): VIDIOCGCAP
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c bus_callback (105): Error: Device "/dev/video1" does not exist.


So thats as far as I got. I am not sure what that means, but it looks to me like it is saying that the information just doesnt have a pathway. I'm missing something.. just don't know what

---

### Post by Denestria on 2009-04-14
Looks like you are doing pretty well. You just missed the end of the move command.  So try this part again

```
sudo mv /dev/video0 /dev/video1
```

then

```
gstfakevideo v4lsrc device=/dev/video1 ! ffmpegcolorspace
```

---

### Post by Fazl on 2009-04-14
I did it and this is what i got. Shouldn't it have made the directory on its own?

fazl@fazl-laptop:~$ sudo mv /dev/video0 /dev/video1

mv: cannot stat `/dev/video0': No such file or directory

Dunno what happened

---

### Post by Denestria on 2009-04-15
You may need to reboot to make the system recreate the device file.

Then check to see if it is there.
```
ls /dev/video*
```

and if it is try the last two commands again.  Or let me know if a device other than /dev/video**0** is listed.

I don't have this webcam so I can't test any of this out.  I'm just trying to help you get through the instructions from the other post!

---

### Post by Fazl on 2009-04-15
I put in the code and got that. Apparently I have only that. I'm gonna try to reboot and see if that works.

fazl@fazl-laptop:~$ ls /dev/video*

/dev/video1

---

### Post by Fazl on 2009-04-15
and after a reboot i got

fazl@fazl-laptop:~$ ls /dev/video*

/dev/video0

Sooo... what does this mean?

---

### Post by Denestria on 2009-04-15
Ok, camera is at video0 again so now you need to mv it to video1.

```
sudo mv /dev/video0 /dev/video1
```
```
gstfakevideo v4lsrc device=/dev/video1 ! ffmpegcolorspace
```

---

### Post by Fazl on 2009-04-15
Ok, so i got this again

fazl@fazl-laptop:~$ ls /dev/video*

/dev/video1

Now, i tried this...

fazl@fazl-laptop:~$ gstfakevideo v4lsrc device=/dev/video1 ! ffmpegcolorspace

and got.... 

gst.c create_pipeline (155): pipeline created
gst.c create_pipeline (159): pipeline linked
gst.c shim_ioctl (201): request=80685600 nr 0
gst.c shim_ioctl (313): result=-1 error=515 Unknown error 515

gst.c shim_ioctl (201): request=803c7601 nr 1
gst.c shim_ioctl (208): VIDIOCGCAP
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c bus_callback (105): Error: Could not open device "/dev/video1" for reading and writing.

How could it be there but not available for writing? I dunno.. this is way more complicated than i thought!

---

### Post by Denestria on 2009-04-15
Permissions for this file are set for the group "video" so make sure you are in the video group.

In a terminal type *groups*.
It should look something like:
denestria adm cdrom audio **video** plugdev scanner netdev lpadmin powerdev admin sambashare

---

### Post by Fazl on 2009-04-15
Punched it in and this is what i got

fazl@fazl-laptop:~$ groups

fazl adm dialout cdrom plugdev lpadmin admin sambashare

Is that right?

---

### Post by Denestria on 2009-04-15
Add yourself to the video group:
```
sudo usermod -a -G video fazl
```
Log out and log in to make the change take effect.

The changes we made yesterday aren't permanent yet so if you have shut the computer down since then we'll have to go through this part again.

```
ls /dev/video*
```

**if** the output is */dev/video0* then:

```
sudo mv /dev/video0 /dev/video1
gstfakevideo v4lsrc device=/dev/video1 ! ffmpegcolorspace

```

**if** the output of ls /dev/video* is */dev/video1* then:
```
gstfakevideo v4lsrc device=/dev/video1 ! ffmpegcolorspace
```

---

### Post by Fazl on 2009-04-15
Ok, here's what I got

fazl@fazl-laptop:~$ groups

fazl adm dialout cdrom video plugdev lpadmin admin sambashare

----------Reboot-----------

fazl@fazl-laptop:~$ ls /dev/video*

/dev/video0

fazl@fazl-laptop:~$ sudo mv /dev/video0 /dev/video1
[sudo] password for fazl: 

fazl@fazl-laptop:~$ ls /dev/video*

/dev/video1


fazl@fazl-laptop:~$ gstfakevideo v4lsrc device=/dev/video1 ! ffmpegcolorspace

gst.c create_pipeline (155): pipeline created
gst.c create_pipeline (159): pipeline linked
gst.c shim_ioctl (201): request=80685600 nr 0
gst.c shim_ioctl (313 ): result=-1 error=515 Unknown error 515

gst.c shim_ioctl (201 ): request=803c7601 nr 1
gst.c shim_ioctl (208 ): VIDIOCGCAP
gst.c shim_ioctl (313 ): result=0 error=0 Success

gst.c bus_callback (105): Error: Could not get/set settings from/on resource.

fazl@fazl-laptop:~$ gstfakevideo v4lsrc device=/dev/video1 ! ffmpegcolorspace

gst.c create_pipeline (155): pipeline created
gst.c create_pipeline (159): pipeline linked
gst.c shim_ioctl (201): request=80685600 nr 0
gst.c shim_ioctl (313 ): result=-1 error=515 Unknown error 515

gst.c shim_ioctl (201): request=803c7601 nr 1
gst.c shim_ioctl (208 ): VIDIOCGCAP
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c bus_callback (105): Error: Could not get/set settings from/on resource.
ALSA lib pcm.c:2196: (snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2196: (snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1619: (bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619: (bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
gst.c bus_callback (105): Error: Could not get/set settings from/on resource.
gst.c shim_ioctl (201): request=80685600 nr 0
gst.c shim_ioctl (313): result=-1 error=515 Unknown error 515

gst.c shim_ioctl (201): request=803c7601 nr 1
gst.c shim_ioctl (208): VIDIOCGCAP
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=800e7606 nr 6
gst.c shim_ioctl (236): VIDIOCGPICT
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=400e7607 nr 7
gst.c shim_ioctl (243): VIDIOCSPICT depth:24, colorspace:15
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=80207609 nr 9
gst.c shim_ioctl (255): VIDIOCGWIN
gst.c shim_ioctl (313): result=0 error=0 Success

gst.c shim_ioctl (201): request=4020760a nr 10
gst.c shim_ioctl (259): VIDIOCSWIN
gst.c shim_ioctl (313): result=0 error=0 Success

Starting the process...
Skype Xv: Xv ports available: 0
Skype XShm: XShm support enabled


Also, note that I took a look at the Webcam testing in the skype video tab and it recognizes it on dev/video1 but when I hit the TEST button, the screen just freeze like the webcam portion is locked up. My IM's and calls still continue fine.

---

### Post by Denestria on 2009-04-16
We made some progress but now there is a whole new batch of problems.

> ALSA lib pcm_bluetooth.c:1619: (bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)
There has been recent discussion of this [sound problem here]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/285412").

> Xv: Xv ports available: 0
Ports available should be at least 2.  I think this is a video card driver issue?  You might run gstreamer-properties and check the video settings in there, I'm not sure.

Apparently this webcam worked in versions of Ubuntu prior to 8.10.  I don't think there is anything else I can do.  Unless someone else can offer advice you might be stuck.

---

