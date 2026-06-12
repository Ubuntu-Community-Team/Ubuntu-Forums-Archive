---
title: "Webcam - so close yet so far"
date: 2006-12-19
forum: Hardware &amp; Laptops
---

### Post by hartz on 2006-12-19
Hi there.

I am sure that I am very close to getting my webcam to work, but I'm not there yet.  I am just missing something small.

I have read a great many posts on identifying the driver, checking USB and kernel modules, etc.

Currently all the video4linux / v4l2 apps that I have installed give me some variation of an error indicating that /dev/video0 is not a video4linux device.

For example, **camgrab** prints:
> /dev/video0: no v4l device

Also **webcam** prints:
> reading config file: /home/hartz/.webcamrc
can't get rgb24 data


**camstream** opens a window, but on the terminal it prints:
> CVideoDevice::CVideoDevice() could not query capabilities; is this really a video device?
CVideoDevice::ResetImagesRGB()
CVideoDevice::ResetImagesYUV()

I have the following configuration:
Ubuntu **Edgy with kernel 2.6.17-10-386** - for what it is worth, this was previously a 6.06 instalation which I upgraded using apt-get dist-upgrade.
The camera is a **Genius TREK 310**

lsusb:
> Bus 002 Device 003: ID 0c45:608f Microdia 
Bus 002 Device 002: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

lsmod|grep usb
> snd_usb_audio          78880  0 
snd_usb_lib            17536  1 snd_usb_audio
snd_rawmidi            25600  1 snd_usb_lib
snd_hwdep               9860  1 snd_usb_audio
snd_pcm                80520  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    55428  12 snd_usb_audio,snd_rawmidi,snd_seq_device,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
usbcore               130304  7 sn9c102,snd_usb_audio,snd_usb_lib,acx,ehci_hcd,ohci_hcd

and grep -i usb /var/log/messages
> Dec 20 18:43:06 linwarg kernel: [17179576.268000] hub 2-0:1.0: USB hub found
Dec 20 18:43:06 linwarg kernel: [17179576.668000] usb 2-8: new high speed USB device using ehci_hcd and address 2
Dec 20 18:43:06 linwarg kernel: [17179576.800000] usb 2-8: configuration #1 chosen from 1 choice
Dec 20 18:43:06 linwarg kernel: [17179576.800000] hub 2-8:1.0: USB hub found
Dec 20 18:43:06 linwarg kernel: [17179592.540000] acx: Loaded combined PCI/USB driver, firmware_ver=default
Dec 20 18:43:06 linwarg kernel: [17179595.120000] usbcore: registered new driver acx_usb
Dec 20 19:36:31 linwarg kernel: [17182822.376000] usb 2-8.1: new full speed USB device using ehci_hcd and address 3
Dec 20 19:36:31 linwarg kernel: [17182822.484000] usb 2-8.1: configuration #1 chosen from 1 choice
Dec 20 19:36:32 linwarg kernel: [17182822.936000] usbcore: registered new driver snd-usb-audio
Dec 20 19:36:32 linwarg kernel: [17182822.960000] usb 2-8.1: SN9C103 PC Camera Controller detected (vid/pid 0x0C45/0x608F)
Dec 20 19:36:32 linwarg kernel: [17182823.160000] usb 2-8.1: OV7630 image sensor detected
Dec 20 19:36:32 linwarg kernel: [17182823.240000] usb 2-8.1: V4L2 device registered as /dev/video0
Dec 20 19:36:32 linwarg kernel: [17182823.240000] usbcore: registered new driver sn9c102
Dec 20 20:10:07 linwarg kernel: [17184837.868000] usb 2-8.1: Initialization succeeded
Dec 20 22:44:06 linwarg kernel: [17194076.248000] usb 2-8.1: Device /dev/video0 is busy...


So it seems that my camera is recognized by the kernel, the modules are loaded and attached to one another, and the device node created.  Yet it doesn't work.  Any advice, ideas, suggestions?

Thanx,
  _Hartz

P.S. I have experienced lockups on Linux since I started playing with the webcam, particularly on loading modules or on plugging the camera in.  When the system locks up, I can not break out even with Ctrl-Alt-F1 or Ctrol-Alt-Backspace, and CAPSLOCK/NUMLOCK stops  working - the only outcome is to power-cycle the machine.

---

### Post by hartz on 2006-12-20
This forum is surprisingly busy, so bump!

---

### Post by hartz on 2006-12-25
Hello all.

I'm still at it.  I've upgraded my kernel to 2.6.19.1, but still have problems.

When I plug in the camera, the following appears in the messages log file

> Dec 26 15:58:32 linwarg kernel: [ 4674.968000] usb 2-8.1: new full speed USB device using ehci_hcd and address 4
Dec 26 15:58:32 linwarg kernel: [ 4675.076000] usb 2-8.1: Product: USB camera
Dec 26 15:58:32 linwarg kernel: [ 4675.076000] usb 2-8.1: configuration #1 chosen from 1 choice
Dec 26 15:58:32 linwarg kernel: [ 4675.076000] usb 2-8.1: SN9C103 PC Camera Controller detected (vid/pid 0x0C45/0x608F)
Dec 26 15:58:32 linwarg kernel: [ 4675.088000] usb 2-8.1: OV7630 image sensor detected
Dec 26 15:58:32 linwarg kernel: [ 4675.112000] usb 2-8.1: V4L2 device registered as /dev/video0


lsmod shows the following which I believe is good:

> hartz@linwarg:/$ lsmod|grep usb
snd_usb_audio          82304  0 
snd_usb_lib            17920  1 snd_usb_audio
snd_rawmidi            27136  1 snd_usb_lib
snd_hwdep              10628  1 snd_usb_audio
snd_pcm                86280  4 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    58500  12 snd_usb_audio,snd_rawmidi,snd_seq_device,snd_hwdep,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
usbcore               157572  7 uhci_hcd,sn9c102,snd_usb_audio,snd_usb_lib,ehci_hcd,ohci_hcd


Yet I still have trouble with basically all webcam software, eg:

> 
hartz@linwarg:/$ camgrab
/dev/video0: no v4l device

hartz@linwarg:/$ webcam
reading config file: /home/hartz/.webcamrc
can't get rgb24 data

hartz@linwarg:/$ xawtv
This is xawtv-3.95, running on Linux/i686 (2.6.19.1)
xinerama 0: 1600x1200+1600+0
xinerama 1: 1600x1200+0+0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  67
  Current serial number in output stream:  67
hartz@linwarg:/$ camorama



So.... Still hopeful ... anybody out there able to help me here?

---

### Post by loell on 2006-12-25
you still haven't posted the webcam's name and model.

---

### Post by Shay Stephens on 2006-12-25
Webcam drivers are broken in edgy.  If you must have webcam support, use dapper or wait for a possible fix with fiesty.  I'm not necessarily saying to give up in edgy, but your chances are slim.

---

### Post by loell on 2006-12-25
> **Shay Stephens said:**
> Webcam drivers are broken in edgy.  If you must have webcam support, use dapper or wait for a possible fix with fiesty.  I'm not necessarily saying to give up in edgy, but your chances are slim.

is there any link to back this up?

my webcam works ;)  i believe that there are many pepople who have working webcams on edgy.

---

### Post by Shay Stephens on 2006-12-25
Hmm, yes, I didn't want to say **all** webcams were busted, but the philips webcams and some others (i.e. all the ones I own) don't work right in edgy.

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/56090](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/56090)

---

### Post by loell on 2006-12-25
i see, thanks

---

### Post by hartz on 2006-12-26
> **loell said:**
> you still haven't posted the webcam's name and model.
I believe I did, in BOLD face at that, but for the record, here it is again:

It is a **Genius TREK 310.**  The Chipset is the Sonix SN9C103, and it has got an OV7630 image sensor.  The ID bits are **0c45:608f Microdia**.  The kernel modules, sn9c102, loads automatically, so I believe that the device is indeed recognized by linux.

This camera has got one special feature:  built-in infrared LEDs, coupled with IR sensitivity.  It wasn't very expensive at all, and I fear it is not the best quality possible, but the night-mode is what made this camera attractive to me.

I connected the camera up to a windows machine and after much struggling with the software managed to get it to work - I was able to record video clips, take snapshots, etc, so the camera appears to be fully functional.

I have checked that reported bug link posted by Shay Stephens, and the problem description does not appear to be similar to my symptoms - in my case most of the programs doesn't even load, these just exit with an error messages.

I am wondering ... what is the difference between Video-4-linux and V4L2 ... Are the two compatible, backward compatible, etc?  According to the messages log file, I see that /dev/video2 is a V4L2 device, but most of my software says Video-4-linux in the APT description. kdetv is the notable exception here, and the only program I have that actually loads, though it spews continuous messages about an Unknown format error - I have tried many options in this program to no avail.

Thanks all for your responses - I am sure I will beat this obstacle and learn something about Linux in the process.

---

### Post by loell on 2006-12-26
Video-4-linux is the previous api or identified as v4l1 while v4l2 is the current api. i think v4l2 is backward compatible with v4l1

this [Link]("http://www.linux-projects.org/modules/newbb/viewtopic.php?topic_id=230&forum=3") seem interesting 

the problem could be the video format that the webcam uses.

---

### Post by hartz on 2006-12-27
Hi Loell,

Indeed I think you are exactly right in your conclusion. :-k   This seems to be the same as the problem I am having.  Would anybody happen to know how would one go about correcting such a problem? :confused: 

I don't realy have a windows machine that I can use and in any case having a machine just for a webcam seems overkill.  So maybe I must buy a different camera, but this would be a very sad day if I had to revert to Windows to solve a problem I had under Linux :(  and this would explain why not more people are switching over to Linux :(  getting hardware to work is sometimes just difficult under Linux. :( 

This is very sad for me, so hopefully

---

### Post by loell on 2006-12-27
your webcam will not be a waste ;)  , maybe in the next six months or so , hopefully there will be someone who can decode the proper format.

next time, do inquire hardware prices and linux comapatibility by simply googling the hardware specific name and model
ie ( product name and linux) it will just pop out if there someone before you tried the hardware in linux and if there's any specific problem for that piece of hardware. and this is always a good rule to follow :)

---

### Post by hartz on 2006-12-28
Well, I have not given up hope yet.  I have started a separate thread on compiling 3rd-party drivers (here: [http://www.ubuntuforums.org/showthread.php?t=326761)](http://www.ubuntuforums.org/showthread.php?t=326761)).

I found a newer version of the driver that my camera uses, eg the sn9c10x driver, here: [http://www.linux-projects.org/modules/mydownloads/](http://www.linux-projects.org/modules/mydownloads/)

Hopefully it will work better :-)

---

### Post by screening on 2007-02-06
Hi, I made this petition for genius.
Please sign in, the link is under "PetitonOnline" in the post, thanks!
[http://laexprimidoradeneuronas.blogspot.com/2007/02/petitiononline.html]("http://laexprimidoradeneuronas.blogspot.com/2007/02/petitiononline.html")

---

### Post by hartz on 2007-06-16
I have had some limited success in getting this camera to work.

1. [http://www.linux-projects.org/modules/mydownloads/](http://www.linux-projects.org/modules/mydownloads/)
Download the driver, as well as the program videoview.
According to the website Videoview is better compliant with v4l2, the Video-4-Linux standard.  In my experience the program does indeed get some picture from the camera, however the quality .... sucks.

I am in the process of getting the driver compiled, I'll probably put up a mini-howto once I got it working.

2. [http://rzr.online.fr/wiki.php?WebCam](http://rzr.online.fr/wiki.php?WebCam)
This page got some hints about how to use the spca5xx driver, which I will also test.

3. [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)
According to this page many similar chips works with the spca5xx driver.  If the one I've got works too this would be great since spca5xx is in the Ubuntu APT repositories (in source format, but still)

4. [https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras)
Information on camera support

5. [http://www.linux.com/howtos/Webcam-HOWTO/index.shtml](http://www.linux.com/howtos/Webcam-HOWTO/index.shtml)
The Linux "webcam howto" page.

---

