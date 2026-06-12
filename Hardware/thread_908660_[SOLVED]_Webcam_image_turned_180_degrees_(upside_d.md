---
title: "[SOLVED] Webcam image turned 180 degrees (upside down)?"
date: 2008-09-02
forum: Hardware
---

### Post by alek01 on 2008-09-02
Hello,
I have an ASUS S96S with a fresh install of 8.04. everything worked automatically :popcorn:(including function keys for brightness, sound volume etc..) but the intergrated webcam produces a picture upside down. This makes it unuseable with Skype :((main purpose of having the webcam) and Camorama. "Chesse" has an effect option to turn the image 180 degrees but that doesn't solve the problem.
The webcam appears as "Syntek USB Video Camera " dev/video01 "
Do you have any idea where I could start?:confused:
Thank you

---

### Post by sergiom99 on 2008-09-02
> **alek01 said:**
> 
Do you have any idea where I could start?:confused:

Hi, a good idea to start is searching the forums :-)
[http://ubuntuforums.org/search.php?searchid=47358656](http://ubuntuforums.org/search.php?searchid=47358656)

Try looking this thread:
[http://ubuntuforums.org/search.php?searchid=47358656](http://ubuntuforums.org/search.php?searchid=47358656)

Good luck!

---

### Post by IntuitiveNipple on 2008-09-02
> **alek01 said:**
> ...but the intergrated webcam produces a picture upside down.
It isn't unknown for the manufacturers to install the camera *upside-down*. Windows drivers often compensate by flipping the image but Linux drivers, of course, do things properly and expect the hardware to do the same.

What driver is managing the camera? It might have a module option to flip the picture.

---

### Post by alek01 on 2008-09-02
Thks for the info. My driver is the Syntek (the webcam manufacturer for ASUS). I don't know how to open the driver or make changes to the output. Physically turning the webcam is not possible 'cause it is neatly seaed into the frame of the screen.
I wentt o see the previous message'slinks so I'm sure my driver is instaled OK.
What should I do next?
Thks again,

---

### Post by IntuitiveNipple on 2008-09-02
Copy the results of these commands so we can see what the device is:
```

lsusb

udevinfo --query=all --name=/dev/video0 --attribute-walk

```

Even if you did open the case, it is unlikely the camera can be rotated since the image sensor is on a circuit board and that will be custom-fitted and very very unlikely to fit any other way.

---

### Post by Crafty Kisses on 2008-09-03
Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Devices > Video Devices > try changing some of the settings. (try both V4L and V4L2)

To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing slowly.

If Ekiga doesn't work post results of the command > lsusb

---

### Post by alek01 on 2008-09-03
Thanks for your help. Here are t he results of the commands: I see the mention of the stk11xx_driver but don't know how to modify/open it.
Thks again
******************
alain@asus-tux:~$ lsusb
Bus 007 Device 005: ID 174f:6a51  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 047d:105e Kensington 
Bus 004 Device 002: ID 03f0:3402 Hewlett-Packard 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 004: ID 04b4:0101 Cypress Semiconductor Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
alain@asus-tux:~$ udevinfo --query=all --name=/dev/video0 --attribute-walk

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1d.7/usb7/7-6/7-6:1.0/video4linux/video0':
    KERNEL=="video0"
    SUBSYSTEM=="video4linux"
    DRIVER==""
    ATTR{dev}=="81:0"
    ATTR{name}=="Syntek USB Video Camera"
    ATTR{release}=="5"
    ATTR{fps}=="25"
    ATTR{brightness}=="7FFF"
    ATTR{contrast}=="7FFF"
    ATTR{whitebalance}=="7FFF"
    ATTR{colour}=="7FFF"
    ATTR{hflip}=="0"
    ATTR{vflip}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb7/7-6/7-6:1.0/video4linux':
    KERNELS=="video4linux"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb7/7-6/7-6:1.0':
    KERNELS=="7-6:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb_stk11xx_driver"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="02"
    ATTRS{bInterfaceClass}=="ff"
    ATTRS{bInterfaceSubClass}=="ff"
    ATTRS{bInterfaceProtocol}=="ff"
    ATTRS{modalias}=="usb:v174Fp6A51d0005dc00dsc00dp00icFFiscFFipFF"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb7/7-6':
    KERNELS=="7-6"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{dev}=="189:772"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{urbnum}=="19833"
    ATTRS{idVendor}=="174f"
    ATTRS{idProduct}=="6a51"
    ATTRS{bcdDevice}=="0005"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="7"
    ATTRS{devnum}=="5"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Syntek"
    ATTRS{product}=="USB2.0"
    ATTRS{serial}=="??????????????????????????????????????????????????????????????????Syntek    ?USB2.0                  ?Audio                   "

  looking at parent device '/devices/pci0000:00/0000:00:1d.7/usb7':
    KERNELS=="usb7"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{dev}=="189:768"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="75"
    ATTRS{idVendor}=="0000"
    ATTRS{idProduct}=="0000"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="7"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="6"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.24-19-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1d.7"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1d.7':
    KERNELS=="0000:00:1d.7"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x2836"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{subsystem_device}=="0x8263"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="18"
    ATTRS{local_cpus}=="ff"
    ATTRS{modalias}=="pci:v00008086d00002836sv00001043sd00008263bc0Csc03i20"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
*******************************

---

### Post by IntuitiveNipple on 2008-09-03
Thanks, that helps a lot! For information, the driver that manages the camera is **stk11xx**. It has the **vflip** option so let's try it. (You can check all the options the driver offers using the command "modinfo stk11xx").

Unload the driver and then re-load it with the vflip option:
```

sudo modprobe -r stk11xx
sudo modprobe stk11xx vflip=1

```
Now try your applications. If that has solved the issue you can add the option to the system settings so the driver always uses it when it loads:
```

echo "options stk11xx vflip=1" | sudo tee -a /etc/modprobe.d/options

```

---

### Post by alek01 on 2008-09-03
Thanks a million! PROBLEM SOLVED
You are fanstistic. It works perfect now. 
I understand what you've done.
I've been happilly exclusively on Ubuntu one year or so, but thiw new computer had this problem. Now I can continue my opensource delight...
BTW, I love your true observation about intutive interface and true connection...
All the best

---

### Post by vasilis34 on 2008-09-04
I have a similar problem with my camera and I want to adjust the horizontal orientation plus the brightness and contrast. I tried doing what is described in the previous posts but my camera's driver seems to be the uvcvideo driver. I checked the modinfo uvcvideo command but the only parameter I get is trace. 

Could u give me some further help?

---

### Post by IntuitiveNipple on 2008-09-04
> **vasilis34 said:**
> I have a similar problem with my camera and I want to adjust the horizontal orientation plus the brightness and contrast. I tried doing what is described in the previous posts but my camera's driver seems to be the uvcvideo driver. I checked the modinfo uvcvideo command but the only parameter I get is trace. 

Could u give me some further help?
If it is using uvcvideo then it doesn't have the same capabilities. It may be the camera doesn't fully implement the UVC standard - there are several - and therefore uvcvideo can't access all the controls.

Check the boot log for any clues. You might see something like this:
```

grep  uvcvideo /var/log/dmesg

[   39.879066] uvcvideo: Found UVC 1.00 device <unnamed> (05ca:1836)
[   39.879302] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   39.879551] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -32 (exp. 26).
[   39.879553] uvcvideo: Failed to initialize the device (-5).
[   39.879572] usbcore: registered new interface driver uvcvideo

```

---

### Post by VMC on 2008-09-04
> **IntuitiveNipple said:**
> Thanks, that helps a lot! For information, the driver that manages the camera is **stk11xx**. It has the **vflip** option so let's try it. (You can check all the options the driver offers using the command "modinfo stk11xx").

Unload the driver and then re-load it with the vflip option:
```

sudo modprobe -r stk11xx
sudo modprobe stk11xx vflip=1

```
Now try your applications. If that has solved the issue you can add the option to the system settings so the driver always uses it when it loads:
```

echo "options stk11xx vflip=1" | sudo tee -a /etc/modprobe.d/options

```

TJ You have to be the Guru on webcams. How did you figure out about "flipping" the above camera? Great find. You have given the best answers to webcam trouble that I have seen so far!

---

### Post by vasilis34 on 2008-09-04
No I don't get any errors. Here is the output of the command

vasilis@vasilis-laptop:~$ grep  uvcvideo /var/log/dmesg
[   41.942248] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b008)
[   41.944292] usbcore: registered new interface driver uvcvideo
vasilis@vasilis-laptop:~$ 

Generally speaking, what I am trying to find out is how can I tweak my webcam's properties(contrast, brightness, etc). For example I open skype with video and if there isn't enough light I see a really dark picture whereas the same time in cheese the picture looks fine.

---

### Post by IntuitiveNipple on 2008-09-04
> **VMC said:**
> TJ You have to be the Guru on webcams. How did you figure out about "flipping" the above camera? Great find. You have given the best answers to webcam trouble that I have seen so far!
Thanks... it's about time all the hours I've spent working with the kernel and video for my own projects gave some pay-back :)

The 'vflip' option is pretty common in webcam drivers - you wouldn't believe how many manufacturers have put the CCDs (Charge-Coupled Devices) in upside down. The 'hflip' option is good if users want a mirror output.

As with anything technical, if you are precise and get to the crux of an issue the solution will show up. This kind of issue can't be solved with wishy-washy questions or imprecise instructions, or 'cut and paste' solutions, especially for non-technical users. Every step has to be given by example, tested, and contextual explanations help too.

I have to admit also that I get fed up of users blaming the web-cam when in most cases it is crappy application programming and/or not keeping up with the APIs and protocols.

---

### Post by IntuitiveNipple on 2008-09-04
> **vasilis34 said:**
> No I don't get any errors. Here is the output of the command

vasilis@vasilis-laptop:~$ grep  uvcvideo /var/log/dmesg
[   41.942248] uvcvideo: Found UVC 1.00 device Chicony USB 2.0 Camera (04f2:b008)
[   41.944292] usbcore: registered new interface driver uvcvideo
vasilis@vasilis-laptop:~$ 

Generally speaking, what I am trying to find out is how can I tweak my webcam's properties(contrast, brightness, etc). For example I open skype with video and if there isn't enough light I see a really dark picture whereas the same time in cheese the picture looks fine.
Okay, that looks good, so you're happy the driver works but yet again it is an application issue.

If you have a uvcvideo camera you could try installing [luvcview from Michel Xhaard's site](http://mxhaard.free.fr/download.html) (scroll almost to the end of the page for the link to the download).

Here's the instruction for downloading, extracting, building and running it:
```

cd ~
wget http://mxhaard.free.fr/spca50x/Investigation/uvc/luvcview-20070512.tar.gz
tar -xzf luvcview-20070512.tar.gz
cd luvcview-20070512
make

```
Now run it. Set the device path if it isn't video0:
```

./luvcview -f yuv /dev/video0 

```
With that you can try adjusting settings such as brightness, contrast, saturation, and gain in the GUI. It will report what it is doing in the console:
```

luvcview version 0.2.1 
Video driver: x11
A window manager is available
video /dev/video0 
max 127, min 0, step 1, default 63 ,current 64 
Control name:Brightness set to value:64
max 127, min 0, step 1, default 63 ,current 65 
Control name:Brightness set to value:65
max 127, min 0, step 1, default 63 ,current 66 
Control name:Brightness set to value:66
max 127, min 0, step 1, default 63 ,current 67 
Control name:Brightness set to value:67
Set Gain up error
ioctl querycontrol error 22
Control name:Contrast set to value:78
max 127, min 0, step 1, default 52 ,current 79 

```

---

### Post by vasilis34 on 2008-09-04
Thx IntuitiveNipple for your quick reply. I ve installed the programm u refer too and it really works.

Thanks a lot!!!

---

### Post by Streifenhoernchen on 2008-09-12
Hi there,

I hope you can help me with a similar problem, concerning my usb-camera. The output of 

udevinfo --query=all --name=/dev/video0 --attribute-walk

is
```

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:02.2/usb3/3-1/3-1.3/video4linux/video0':
    KERNEL=="video0"
    SUBSYSTEM=="video4linux"
    DRIVER==""
    ATTR{dev}=="81:0"
    ATTR{name}=="GSPCA USB Camera"
    ATTR{stream_id}=="JPEG"
    ATTR{model}=="Z-star Vimicro zc0302"
    ATTR{pictsetting}=="force_rgb=0, gamma=3, OffRed=0, OffBlue=0, OffGreen=0, GRed=256, GBlue=256, GGreen= 256 "

  looking at parent device '/devices/pci0000:00/0000:00:02.2/usb3/3-1/3-1.3/video4linux':
    KERNELS=="video4linux"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:02.2/usb3/3-1/3-1.3':
    KERNELS=="3-1.3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{dev}=="189:262"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 3"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bMaxPower}=="160mA"
    ATTRS{urbnum}=="699"
    ATTRS{idVendor}=="0ac8"
    ATTRS{idProduct}=="0302"
    ATTRS{bcdDevice}=="0100"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="8"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="3"
    ATTRS{devnum}=="7"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="V Micro. Corp."
    ATTRS{product}=="PC Camera"

  looking at parent device '/devices/pci0000:00/0000:00:02.2/usb3/3-1':
    KERNELS=="3-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{dev}=="189:257"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}==" 98mA"
    ATTRS{urbnum}=="1693"
    ATTRS{idVendor}=="0424"
    ATTRS{idProduct}=="a700"
    ATTRS{bcdDevice}=="0000"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="02"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="3"
    ATTRS{devnum}=="2"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="4"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:02.2/usb3':
    KERNELS=="usb3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{dev}=="189:256"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="57"
    ATTRS{idVendor}=="0000"
    ATTRS{idProduct}=="0000"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="3"
    ATTRS{devnum}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="6"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.24-19-generic ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:02.2"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:02.2':
    KERNELS=="0000:00:02.2"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x10de"
    ATTRS{device}=="0x0068"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{subsystem_device}=="0x0c11"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="16"
    ATTRS{local_cpus}=="ff"
    ATTRS{modalias}=="pci:v000010DEd00000068sv00001043sd00000C11bc0Csc03i20"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```

Thus, I don't know which driver is used.
Could you help me?

Streifenhoernchen

---

### Post by IntuitiveNipple on 2008-09-12
When in doubt use the USB vendor and device ID:
```

    ATTRS{idVendor}=="0ac8"
    ATTRS{idProduct}=="0302"

```
The kernel keeps a text-file with a list of all the supported IDs in **/lib/modules/$(uname -r)/modules.usbmap**

You can search that file for the entry that matches. Add the prefix **0x** that indicates these are hexadecimal (base 16) numbers:
```

egrep '0x0ac8.*0x0302'  /lib/modules/$(uname -r)/modules.usbmap

gspca                0x0003      0x0ac8   0x0302    0x0000       0x0000       0x00         0x00            0x00            0x00            0x00               0x00               0x0

```
The first column is the name of the driver; in this case **gspca**.

---

### Post by Streifenhoernchen on 2008-09-13
Thanks for this hint! Is there for the gspca driver a similar workaround as for the stk11xx driver in the first post? In skype the video of my webcam is upside down ... :-(

Streifenhoernchen

---

### Post by IntuitiveNipple on 2008-09-13
When you know the name of a kernel module it is easy to discover what **param**eters it supports. I won't copy the entire output here since there are a lot of alias entries (they are the list of device IDs the module can manage - this is where the lists in modules.pcimap and modules.usbmap come from), but you can do it yourself:
```

modinfo gspca

filename:       /lib/modules/2.6.24-21-generic/ubuntu/media/gspcav1/gspca.ko
license:        GPL
description:    GSPCA/SPCA5XX USB Camera Driver
author:         Michel Xhaard <mxhaard@users.sourceforge.net> based on spca50x driver by Joel Crisp <cydergoth@users.sourceforge.net>,ov511 driver by Mark McClelland <mwm@i.am>
srcversion:     5B17DAD9AD01F291B7EBC04
alias:          usb:v093Ap2463d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v093Ap2472d*dc*dsc*dp*ic*isc*ip*
...
alias:          usb:v0733p0430d*dc*dsc*dp*ic*isc*ip*
depends:        usbcore,videodev,compat_ioctl32
vermagic:       2.6.24-21-generic SMP mod_unload 
parm:           autoexpo:Enable/Disable auto exposure (default=1: enabled) (PC-CAM 600/Zc03xx/spca561a/Etoms Only !!!) (int)
parm:           debug:Debug level: 0=none, 1=init/detection, 2=warning, 3=config/control, 4=function call, 5=max (int)
parm:           force_rgb:Read RGB instead of BGR (int)
parm:           gamma:gamma setting range 0 to 7 3-> gamma=1 (int)
parm:           OffRed:OffRed setting range -128 to 128 (int)
parm:           OffBlue:OffBlue setting range -128 to 128 (int)
parm:           OffGreen:OffGreen setting range -128 to 128 (int)
parm:           GRed:Gain Red setting range 0 to 512 /256  (int)
parm:           GBlue:Gain Blue setting range 0 to 512 /256  (int)
parm:           GGreen:Gain Green setting range 0 to 512 /256  (int)
parm:           compress:Turn on/off compression (not functional yet) (int)
parm:           usbgrabber:Is a usb grabber 0x0733:0x0430 ? (default 1)  (int)
parm:           lightfreq:Light frequency banding filter. Set to 50 or 60 Hz, or 0 for NoFlicker (default=50) Zc03xx only (int)
parm:           force_gamma_id:Forced assigning ID of contrast settings (0=default,1,2,3) Zc03xx only (int)
parm:           force_sensor_id:Forced assigning ID sensor (Zc03xx only). Dangerous, only for experts !!! (int)

```
There is no obvious param that suggest a flip.

---

### Post by Streifenhoernchen on 2008-09-13
Oh, too bad. Well, at least I've learnt something new :-)
Thank you!

Streifenhoernchen

---

### Post by David A Knight on 2008-09-13
> **IntuitiveNipple said:**
> It isn't unknown for the manufacturers to install the camera *upside-down*. Windows drivers often compensate by flipping the image but Linux drivers, of course, do things properly and expect the hardware to do the same.

What driver is managing the camera? It might have a module option to flip the picture.

I have seen this repeated a number of times, and I do not believe this to be 100% accurate.  uvcvideo did work at one point under linux for me, broke again though.  The image was upside down and limited to 1 res.  If I booted into windows, and so let it initialised the hardware, then booted back into linux then the image from the webcam was available in the size I set under windows, but also it was now the correct way round.  This would indicate to me that it is not the drivers at all, but straight forward hardware configuration / correct firmware loading, at least in my case (motion eye in a vaio)

---

### Post by IntuitiveNipple on 2008-09-13
> **David A Knight said:**
> I have seen this repeated a number of times, and I do not believe this to be 100% accurate.  uvcvideo did work at one point under linux for me, broke again though.  The image was upside down and limited to 1 res.  If I booted into windows, and so let it initialised the hardware, then booted back into linux then the image from the webcam was available in the size I set under windows, but also it was now the correct way round.  This would indicate to me that it is not the drivers at all, but straight forward hardware configuration / correct firmware loading, at least in my case (motion eye in a vaio)
Yes, the correction can be done in the firmware image that is loaded into the camera by the driver, or in the driver itself. It depends on the inclination of the manufacturer/OEM/integrator. If those corrections depend on the driver setting an option then it is likely the supplier-maintained driver for Windows will do 'the right thing' whereas the Linux developers usually aren't informed of the requirement or mechanism to make the flip.

Somewhat related to this is the technique of setting up a problematic device (WiFi adapters spring to mind) in Windows first and then doing a warm-restart into Linux so it can inherit the correct device configuration  - since the Linux kernel module doesn't know how to perform the necessary adjustments.

---

### Post by otrojake on 2008-09-30
I stumbled across this thread while trying to make my Syntek integrated webcam on my Asus Z96FM no longer be upside down.  I tried setting the vflip value to 1, but the image was still upside down.  It turns out that the default option was *already* set to 1, so the value needed to be set to 0 for the webcam to display properly.

```

sudo modprobe -r stk11xx
sudo modprobe stk11xx vflip=0
```

That did it for me.  Thanks for pointing me in the right direction, guys!

---

### Post by John Harrington on 2008-10-05
There's a gui for changing the settings on the syntek module, including hflip and vflip, on the fly (without removing the module) here:

[]("http://sourceforge.net/forum/forum.php?thread_id=1976138&forum_id=616182")

---

### Post by John Harrington on 2008-10-06
Oops, that should be here:

[http://sourceforge.net/forum/forum.php?thread_id=1976138&forum_id=616182](http://sourceforge.net/forum/forum.php?thread_id=1976138&forum_id=616182)

---

### Post by tymek666 on 2009-01-01
> **otrojake said:**
> I stumbled across this thread while trying to make my Syntek integrated webcam on my Asus Z96FM no longer be upside down.  I tried setting the vflip value to 1, but the image was still upside down.  It turns out that the default option was *already* set to 1, so the value needed to be set to 0 for the webcam to display properly.

```

sudo modprobe -r stk11xx
sudo modprobe stk11xx vflip=0
```

That did it for me.  Thanks for pointing me in the right direction, guys!

It also works on stkwebcam driver. Thanks a lot guys :)

---

### Post by Carmageddon on 2013-01-12
TI have someone with similar issue where the webcam output is flipped upside down, and even the windows drivers dont always work.
The model is ASus K52F.

I have Ubuntu 12.04LTS installed.

This is the output of the new udevinfo(today it is udevadm info):

```
sasa@sasa-K52F:~/&#1047;&#1072;&#1075;&#1088;&#1091;&#1079;&#1082;&#1080;$ udevadm info --query=all --name=/dev/video0 --attribute-walk

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/video4linux/video0':
    KERNEL=="video0"
    SUBSYSTEM=="video4linux"
    DRIVER==""
    ATTR{name}=="USB 2.0 Camera"
    ATTR{index}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0':
    KERNELS=="1-1.2:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="uvcvideo"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="01"
    ATTRS{bInterfaceClass}=="0e"
    ATTRS{bInterfaceSubClass}=="01"
    ATTRS{bInterfaceProtocol}=="00"
    ATTRS{supports_autosuspend}=="1"
    ATTRS{iad_bFirstInterface}=="00"
    ATTRS{iad_bInterfaceCount}=="02"
    ATTRS{iad_bFunctionClass}=="0e"
    ATTRS{iad_bFunctionSubClass}=="03"
    ATTRS{iad_bFunctionProtocol}=="00"
    ATTRS{interface}=="USB Camera"

  looking at parent device '/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2':
    KERNELS=="1-1.2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 2"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="500mA"
    ATTRS{urbnum}=="957134"
    ATTRS{idVendor}=="13d3"
    ATTRS{idProduct}=="5130"
    ATTRS{bcdDevice}=="1211"
    ATTRS{bDeviceClass}=="ef"
    ATTRS{bDeviceSubClass}=="02"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="4"
    ATTRS{devpath}=="1.2"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Sonix Technology Co., Ltd."
    ATTRS{product}=="USB 2.0 Camera"

  looking at parent device '/devices/pci0000:00/0000:00:1a.0/usb1/1-1':
    KERNELS=="1-1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="249"
    ATTRS{idVendor}=="8087"
    ATTRS{idProduct}=="0020"
    ATTRS{bcdDevice}=="0000"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="2"
    ATTRS{devpath}=="1"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="6"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1a.0/usb1':
    KERNELS=="usb1"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="128"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0002"
    ATTRS{bcdDevice}=="0302"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="1"
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="2"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 3.2.0-29-generic-pae ehci_hcd"
    ATTRS{product}=="EHCI Host Controller"
    ATTRS{serial}=="0000:00:1a.0"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:1a.0':
    KERNELS=="0000:00:1a.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="ehci_hcd"
    ATTRS{vendor}=="0x8086"
    ATTRS{device}=="0x3b3c"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{subsystem_device}=="0x1f27"
    ATTRS{class}=="0x0c0320"
    ATTRS{irq}=="16"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""
    ATTRS{companion}==""
    ATTRS{uframe_periodic_max}=="100"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""


```

AS you can see, no hflip or vflip attributes :(

Any suggestions what to do?

---

### Post by overdrank on 2013-01-12
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

