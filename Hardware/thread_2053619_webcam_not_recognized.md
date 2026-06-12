---
title: "webcam not recognized"
date: 2012-09-05
forum: Hardware
---

### Post by jlh68 on 2012-09-05
Neither cheese nor guvcview will recognize the onboard camera on my laptop.

How do I check camerea to see if it works?  Camera does not show in the list of input devices.  I don't know if it is a software problem or a hardware problem.  Need a way to check the operation of the camera to rule on the hardware part.

---

### Post by Dy1anW on 2012-09-06
What output do you get when you run the commands:
```
guvcview -v
```and 
```
sudo modprobe -l | grep gspca
```Also, did you check your laptop against the incompatibility list? There's the possibility that your built in cam may not be supported.

---

### Post by Lampi on 2012-09-06
check for device messages:
```
dmesg | less
```
look out for webcam or video - you might see a message that you are missing a firmware or sth else

---

### Post by jlh68 on 2012-09-06
Here is one of the outputs you aske for.  The webcam worked for awhile using both applications and now doesn't work, so I doubt that the webcam is on the incompatable list.  The webcam has worked with cheese since Ubuntu version 10.04.

> john@Nighthawk:~$ sudo modprobe -l | grep gspca
[sudo] password for john: 
kernel/drivers/media/video/gspca/gspca_main.ko
kernel/drivers/media/video/gspca/gspca_benq.ko
kernel/drivers/media/video/gspca/gspca_conex.ko
kernel/drivers/media/video/gspca/gspca_cpia1.ko
kernel/drivers/media/video/gspca/gspca_etoms.ko
kernel/drivers/media/video/gspca/gspca_finepix.ko
kernel/drivers/media/video/gspca/gspca_jeilinj.ko
kernel/drivers/media/video/gspca/gspca_kinect.ko
kernel/drivers/media/video/gspca/gspca_konica.ko
kernel/drivers/media/video/gspca/gspca_mars.ko
kernel/drivers/media/video/gspca/gspca_mr97310a.ko
kernel/drivers/media/video/gspca/gspca_nw80x.ko
kernel/drivers/media/video/gspca/gspca_ov519.ko
kernel/drivers/media/video/gspca/gspca_ov534.ko
kernel/drivers/media/video/gspca/gspca_ov534_9.ko
kernel/drivers/media/video/gspca/gspca_pac207.ko
kernel/drivers/media/video/gspca/gspca_pac7302.ko
kernel/drivers/media/video/gspca/gspca_pac7311.ko
kernel/drivers/media/video/gspca/gspca_se401.ko
kernel/drivers/media/video/gspca/gspca_sn9c2028.ko
kernel/drivers/media/video/gspca/gspca_sn9c20x.ko
kernel/drivers/media/video/gspca/gspca_sonixb.ko
kernel/drivers/media/video/gspca/gspca_sonixj.ko
kernel/drivers/media/video/gspca/gspca_spca500.ko
kernel/drivers/media/video/gspca/gspca_spca501.ko
kernel/drivers/media/video/gspca/gspca_spca505.ko
kernel/drivers/media/video/gspca/gspca_spca506.ko
kernel/drivers/media/video/gspca/gspca_spca508.ko
kernel/drivers/media/video/gspca/gspca_spca561.ko
kernel/drivers/media/video/gspca/gspca_spca1528.ko
kernel/drivers/media/video/gspca/gspca_sq905.ko
kernel/drivers/media/video/gspca/gspca_sq905c.ko
kernel/drivers/media/video/gspca/gspca_sq930x.ko
kernel/drivers/media/video/gspca/gspca_sunplus.ko
kernel/drivers/media/video/gspca/gspca_stk014.ko
kernel/drivers/media/video/gspca/gspca_stv0680.ko
kernel/drivers/media/video/gspca/gspca_t613.ko
kernel/drivers/media/video/gspca/gspca_topro.ko
kernel/drivers/media/video/gspca/gspca_tv8532.ko
kernel/drivers/media/video/gspca/gspca_vc032x.ko
kernel/drivers/media/video/gspca/gspca_vicam.ko
kernel/drivers/media/video/gspca/gspca_xirlink_cit.ko
kernel/drivers/media/video/gspca/gspca_zc3xx.ko
kernel/drivers/media/video/gspca/m5602/gspca_m5602.ko
kernel/drivers/media/video/gspca/stv06xx/gspca_stv06xx.ko
kernel/drivers/media/video/gspca/gl860/gspca_gl860.ko
john@Nighthawk:~$

---

### Post by jlh68 on 2012-09-06
Here is part of the other output:

> john@Nighthawk:~$ guvcview -v
guvcview 1.5.3
video_device: /dev/video0
vid_sleep: 0
cap_meth: 1
resolution: 640 x 480
windowsize: 560 x 700
vert pane: 578
spin behavior: 0
default action: 0
mode: yuyv
fps: 1/30
Display Fps: 0
bpp: 32
hwaccel: 1
avi_format: 3
sound: 1
sound Device: 0
sound samp rate: 0
sound Channels: 0
Sound delay: 0 nanosec
Sound Format: 80 
Pan Step: 2 degrees
Tilt Step: 2 degrees
Video Filter Flags: 0
image inc: 0
profile(default):/home/john/default.gpfl

---

### Post by jlh68 on 2012-09-06
The other half of the output:

> starting portaudio...
ALSA lib pcm_dmix.c:1018: (snd_pcm_dmix_open) unable to open slave
ALSA lib pcm.c:2217: (snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2217: (snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217: (snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib audio/pcm_bluetooth.c:1614: (audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614: (audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614: (audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614: (audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:1018: (snd_pcm_dmix_open) unable to open slave
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
language catalog=> dir:/usr/share/locale type:UTF-8 lang:en_US.UTF-8 cat:guvcview.mo
Screen resolution is (1366 x 768 )
yuyv: setting format to 1448695129
capture method = 1
video device: /dev/video0 
unable to detect video devices on your system (0)
ERROR opening V4L interface: No such file or directory
Init video returned -1
free audio mutex
VIDIOC_REQBUFS - Failed to delete buffers: Invalid argument (errno 22)
closed v4l2 strutures
free controls - vidState
cleaned allocations - 100%
Closing portaudio ...OK
Terminated.
john@Nighthawk:~$ 


---

### Post by jlh68 on 2012-09-06
**Lampi**    
Your request resulted  in many, many lines to look through.  I did not see either a line with Video or Webcam in it.  I looked two or three times.  I did see other input devices though.

> dmesg | less

look out for webcam or video - you might see a message that you are missing a firmware or sth else

---

### Post by jlh68 on 2012-09-06
OK, I hooked up a not so great USB camera and it works with both Cheese and guvcview.  The images are not as good as I was getting on my built in camera.  All of this makes me wonder if the onboard camera "crapped out" or just failed.  If so I wonder where to get a replacement camera.  Of course it may still be a software problem.

---

### Post by jlh68 on 2012-09-06
Something I almost never do, boot into Windows 7.  So I did and opened the Acer CrystalEye camera application, and it could not find the cameral either.  Now I believe that it is a real hardware problem and that I need to replace the Acer CrystalEye camera.

So the onboard camera is not detected by Ubuntu or Win7.  An USB camera is detected by Ubuntu and by both Cheese and guvcview.  Based on that the CrystalEye is now black(out).

Do you all concur? or have other ideas?

---

### Post by Dy1anW on 2012-09-07
It certainly looks that way, yes.

---

