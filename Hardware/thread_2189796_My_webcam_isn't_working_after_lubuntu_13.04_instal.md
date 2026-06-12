---
title: "My webcam isn't working after lubuntu 13.04 installation"
date: 2013-11-24
forum: Hardware
---

### Post by ksuourgos on 2013-11-24
Hello everybody. I recently installed lubuntu 13.04 and one of the problems I have is that my webcam isn't working, nether in cheese nor in guvcview or skype.I tried the same webcam with another p.c. while runing lubuntu 13.04 via live-cd and when runing guvcview the webcam is showing image. I have no experience with ubuntu and linux in general but opened the terminal and typed some commands I found while serfing the web. I would appreciate any help anyone could give me.


[COLOR=#0000ff][FONT=Lucida Grande]**lsusb**[/FONT][/COLOR]
```
Bus 001 Device 003: ID 045e:0766 Microsoft Corp. 
Bus 002 Device 002: ID 045e:0083 Microsoft Corp. Basic Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



```


[COLOR=#0000ff][B]lsmod | grep "video"
[/B][/COLOR]```
uvcvideo               71279  0 videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
videobuf2_core         39161  1 uvcvideo
videodev               95806  2 uvcvideo,videobuf2_core
video                  18894  1 nouveau



```


[COLOR=#0000ff]**dmesg | grep "video"**[/COLOR]```
[    0.262289] pci 0000:01:00.0: Boot video device[   13.968485] Linux video capture interface: v2.00
[   14.402200] uvcvideo: Found UVC 1.00 device Microsoft LifeCam VX-800 (045e:0766)
[   14.422196] usbcore: registered new interface driver uvcvideo



```

[COLOR=#0000ff][B]lsmod | grep sonixj[FONT=Monaco]
[/FONT][/B][/COLOR](this command gives me nothing)


[COLOR=#0000ff]**guvcview**[/COLOR]
```
guvcview 1.6.0ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'cards.ICH.pcm.surround71.0:CARD=0'
ALSA lib conf.c:4241:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:4720:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM surround71
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.modem
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.modem
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.phoneline
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
video device: /dev/video0 
Init. Microsoft LifeCam VX-800 (location: usb-0000:00:03.3-2)
{ pixelformat = 'YUYV', description = 'YUV 4:2:2 (YUYV)' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 
{ pixelformat = 'RGB3', description = 'RGB3' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 
{ pixelformat = 'BGR3', description = 'BGR3' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 
{ pixelformat = 'YU12', description = 'YU12' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 
{ pixelformat = 'YV12', description = 'YV12' }
{ discrete: width = 640, height = 480 }
    Time interval between frame: 1/30, 
{ discrete: width = 352, height = 288 }
    Time interval between frame: 1/30, 
{ discrete: width = 320, height = 240 }
    Time interval between frame: 1/30, 
{ discrete: width = 176, height = 144 }
    Time interval between frame: 1/30, 
{ discrete: width = 160, height = 120 }
    Time interval between frame: 1/30, 
vid:045e 
pid:0766 
driver:uvcvideo
checking format: 1448695129
fps is set to 1/30
drawing controls


fps is set to 1/30
no codec detected for H264
no codec detected for MP3 - (lavc)
Checking video mode 640x480@32bpp : OK 
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
 Could not grab image (select timeout): Resource temporarily unavailable
write /home/g/.guvcviewrc OK
free controls
cleaned allocations - 100%
Closing portaudio ...OK
Closing GTK... OK



```

I would like to add that I have an on-board usb card. I am writing this because my first problem after installing lubuntu 13.04 was that I could not reach the web. This problem was solved by adding a pci ethernet card and using **_it_** instead of the on-board ethernet card my machine has.

---

