---
title: "Skype &amp; Acer Crystal Eye Webcam"
date: 2009-02-26
forum: Hardware
---

### Post by diamondjim08 on 2009-02-26
On my new Acer 5515S with Ubuntu 8.10, Skype video did not work BUT Ekiga video worked fine. Installed gstfakevideo to get the Acer Crystal Eye webcam to work in Skype (newest version).  Started Skype from terminal: gstfakevideo v4l2src device=/device/dev/video1.  Skype executed and video from the Acer to my Apple on Skype was there for all to see. But the offending computer could not see itself or the Apple computer.  The Apple computer sees the offending computer and itself so therefore the Acer webcam does transmitt out.  If you close Skype on the Acer computer, everything fails leaving the Acer webcam on /dev/video1.
Ekiga stills works perfectly.
I took a look at "skype video hijacker" and stopped there because I was afraid to install more packages that might mess up my new system.

Here is some terminal code that went with the gstfakevideo and the Acer webcam trying to operate...beyond my pay grade BUT it worked partially - great video from the Acer to the Apple; no video on the Acer at all. 
I think the solution is close but it is over my head-thanks a bunch!!:

mashid@mashid-laptop:~$ svn checkout [http://gstfakevideo.googlecode.com/svn/trunk/](http://gstfakevideo.googlecode.com/svn/trunk/) gstfakevideo-read-only
A    gstfakevideo-read-only/README-AMD64
A    gstfakevideo-read-only/gstfakevideo
A    gstfakevideo-read-only/gstfakevideo.c
A    gstfakevideo-read-only/README
A    gstfakevideo-read-only/Makefile
A    gstfakevideo-read-only/gst.c
Checked out revision 3.
mashid@mashid-laptop:~$ cd gstfakevideo-read-only
mashid@mashid-laptop:~/gstfakevideo-read-only$ sudo make
gcc -O2 -Wall -m32  `pkg-config gstreamer-0.10 --cflags` -ldl `pkg-config gstreamer-0.10 --libs` -shared -fpic gst.c gstfakevideo.c -o libgstfakevideo.so
gst.c: In function ‘cb_handoff’:
gst.c:85: warning: ignoring return value of ‘write’, declared with attribute warn_unused_result
mashid@mashid-laptop:~/gstfakevideo-read-only$ su
Password: 
mashid@mashid-laptop:~/gstfakevideo-read-only$ make install
cp libgstfakevideo.so /usr/local/lib
cp: cannot create regular file `/usr/local/lib/libgstfakevideo.so': Permission denied
make: *** [install] Error 1
mashid@mashid-laptop:~/gstfakevideo-read-only$ sudo make insatll
make: *** No rule to make target `insatll'.  Stop.
mashid@mashid-laptop:~/gstfakevideo-read-only$ sudo make install
cp libgstfakevideo.so /usr/local/lib
chmod 0755 /usr/local/lib/libgstfakevideo.so
cp gstfakevideo /usr/local/bin
chmod 0755 /usr/local/bin/gstfakevideo
mashid@mashid-laptop:~/gstfakevideo-read-only$ sudo mv /dev/video0 /dev/video1
mashid@mashid-laptop:~/gstfakevideo-read-only$ gstfakevideo v4l2src device=/dev/video1
gst.c create_pipeline (155): pipeline created
gst.c create_pipeline (159): pipeline linked
gst.c shim_ioctl (201): request=80685600 nr 0
gst.c shim_ioctl (313): result=-1 error=515 Unknown error 515

gst.c shim_ioctl (201): request=803c7601 nr 1
gst.c shim_ioctl (208): VIDIOCGCAP
gst.c shim_ioctl (313): result=0 error=0 Success


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
Skype Xv: Xv ports available: 16
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 57
Skype V4L2: Could not find a suitable capture format
Skype V4L2: Could not find a suitable capture format
Skype V4L2: Could not find a suitable capture format
Skype V4L2: Could not find a suitable capture format
Starting the process...
Skype Xv: Xv ports available: 16
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 57
Skype Xv: No suitable overlay format found
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
Skype Xv: Xv ports available: 16
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 57

---

