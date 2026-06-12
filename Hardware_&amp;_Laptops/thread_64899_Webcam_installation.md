---
title: "Webcam installation?"
date: 2005-09-12
forum: Hardware &amp; Laptops
---

### Post by c-m on 2005-09-12
I have aquired a sony eye toy after hearing they were very good quality cameras for the money. I don't have the slightest clue how to install this in linux, can anyone help with links to guides in english? i got loads of foriegn results.

lsusb shows:
Bus 001 Device 004: ID 054c:0154 Sony Corp.

---

### Post by mlomker on 2005-09-12
[QUOTE=c-m]lsusb shows:
Bus 001 Device 004: ID 054c:0154 Sony Corp.[/QUOTE]

Webcams are difficult and they require a linux driver to operate.  It's possible that the kernel recognizes the chipset already, though, and created a /dev/Video0 or similar for you.

Try the **dmesg** command after insertion and see if it loaded anything.

---

### Post by c-m on 2005-09-12
[QUOTE=mlomker]Webcams are difficult and they require a linux driver to operate.  It's possible that the kernel recognizes the chipset already, though, and created a /dev/Video0 or similar for you.

Try the **dmesg** command after insertion and see if it loaded anything.[/QUOTE]
 i should add that i have a tvcard installed and a satellite pci card so /dev/video 0, 1, 2 , 3 are already in use.

dmesg shows a whole lot of something that doesn't mean anything to me.

> 
carl@carl:~$ dmesg
at76c503a/at76c503.c: wlan0: DeAuth in state 1 ignored
/home/carl/at76c503a/at76c503.c: wlan0: DeAuth in state 1 ignored
/home/carl/at76c503a/at76c503.c: wlan0: DeAuth in state 1 ignored
/home/carl/at76c503a/at76c503.c: wlan0: DeAuth in state 1 ignored
/home/carl/at76c503a/at76c503.c: wlan0: DeAuth in state 1 ignored
/home/carl/at76c503a/at76c503.c: wlan0: ignored AuthFrame in state 1
/home/carl/at76c503a/at76c503.c: wlan0: ignored AuthFrame in state 1
/home/carl/at76c503a/at76c503.c: wlan0: ignored AuthFrame in state 1
/home/carl/at76c503a/at76c503.c: wlan0: ignored AuthFrame in state 1
/home/carl/at76c503a/at76c503.c: wlan0: ignored AuthFrame in state 1
/home/carl/at76c503a/at76c503.c: wlan0: ignored AuthFrame in state 1
/home/carl/at76c503a/at76c503.c: wlan0: ignored AuthFrame in state 1
/home/carl/at76c503a/at76c503.c: wlan0: ignored AuthFrame in state 1
/home/carl/at76c503a/at76c503.c: /home/carl/at76c503a/at76c503.c:2845 assertion dev->istate == JOINING failed
/home/carl/at76c503a/at76c503.c: wlan0: ignored AuthFrame in state 1
/home/carl/at76c503a/at76c503.c: wlan0: ignored AuthFrame in state 1
/home/carl/at76c503a/at76c503.c: wlan0 join_bss ssid 00:11:50:32:16:6d timed out/home/carl/at76c503a/at76c503.c: /home/carl/at76c503a/at76c503.c:2845 assertion dev->istate == JOINING failed
/home/carl/at76c503a/at76c503.c: /home/carl/at76c503a/at76c503.c:2845 assertion dev->istate == JOINING failed
/home/carl/at76c503a/at76c503.c: /home/carl/at76c503a/at76c503.c:2845 assertion dev->istate == JOINING failed
/home/carl/at76c503a/at76c503.c: wlan0: ignored AuthFrame in state 1
/home/carl/at76c503a/at76c503.c: wlan0: ignored AuthFrame in state 1
/home/carl/at76c503a/at76c503.c: /home/carl/at76c503a/at76c503.c:2845 assertion dev->istate == JOINING failed
/home/carl/at76c503a/at76c503.c: wlan0: ignored AuthFrame in state 1
/home/carl/at76c503a/at76c503.c: wlan0 join_bss ssid 00:11:50:32:16:6d timed out/home/carl/at76c503a/at76c503.c: /home/carl/at76c503a/at76c503.c:2845 assertion dev->istate == JOINING failed
/home/carl/at76c503a/at76c503.c: wlan0: ignored AuthFrame in state 1
/home/carl/at76c503a/at76c503.c: wlan0: ignored AuthFrame in state 1



---

### Post by c-m on 2005-09-13
nobody using one of these then in ubuntu? great stuff.

---

### Post by rjmckee on 2005-09-15
Hi c-m,
I have a win-TV card, TVTime works OK, card is mostly used for video grab/editing).
I also have a Creative PCCam-300. Digikam was using the camera just fine with Gentoo but I could not use gnomemeeting and the web cam as the Hauppauge bt878 device always got chosen without any other video devs available.
With ubuntu Digikam partially works. TVTime has problems, and gnomemeting still only recognizes the TV card.
Re: your problem:
1. I don't know what/how to help except to share my experiences with 2 different linuxes;
- Gentoo and Ubuntu both fail with gnomemeeting to find my webcam once the WinTV card is located.
-Digikam & gPhoto both find the webcam as a camera in both linuxes.
- In Gentoo I was reasonably sure (no guarantee!) that my kernel options were correct and that I loaded all neccessary modules. Since Ubuntu works similarly I guess it is possible that these 2 devices are in conflict within the kernel/device management code?
I think my only short term solution (Bah, ugly!) is to remove the TV card when not video editing and use the webcam as a webcam at other times. I have googled for 18 months without success......
Regards,
Ray

---

### Post by c-m on 2005-09-15
right. i've been trying to follow the guide here: [http://216.109.124.98/language/translatedPage?lp=es_en&.intl=uk&tt=url&text=http%3a%2f%2fwww.josemariasotomayor.net%2fwordpress%2findex.php%3fp%3d13](http://216.109.124.98/language/translatedPage?lp=es_en&.intl=uk&tt=url&text=http%3a%2f%2fwww.josemariasotomayor.net%2fwordpress%2findex.php%3fp%3d13)

the driver compiles nicely etc.. but when i run modprobe "modprobe ov51x" I get an error saying "FATAL: Module ov51x not found."

---

### Post by mlomker on 2005-09-16
Try:

[b]
updatedb
locate ov51x
[/b]

There should be a .ko file under /lib/modules/yourkernel.

---

### Post by c-m on 2005-09-16
ah its mainly found in its directory but also here:

/lib/modules/2.6.10/extra/ov51x.ko

but modprobe still will not find it.

carl@carl:~$ modprobe ov51x
FATAL: Module ov51x not found.
carl@carl:~$ modprobe ov51x.ko
FATAL: Module ov51x.ko not found.

---

### Post by mlomker on 2005-09-17
I'll admit that I'm totally guess at this point, but try this.  It is a command that rebuilds a kernel module dependency file.

```

sudo depmod -ae

```

---

### Post by ippiraman on 2005-09-17
Anyone could help me install this type of webcam? I don't know if the kernel supports it but I have a 
/dev/video1394 folder.

$ lsusb
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 093a:2468 Pixart Imaging, Inc.
Bus 001 Device 001: ID 0000:0000

Thanks

---

### Post by mlomker on 2005-09-17
[QUOTE=ippiraman]Anyone could help me install this type of webcam? I don't know if the kernel supports it but I have a 
/dev/video1394 folder.
[/quote]

I'd recommend starting with a Google search.  The model or brand of the camera along with **linux driver** ought to turn some things up.

---

### Post by c-m on 2005-09-17
[QUOTE=mlomker]I'll admit that I'm totally guess at this point, but try this.  It is a command that rebuilds a kernel module dependency file.

```

sudo depmod -ae

```[/QUOTE]

carl@carl:~$ sudo depmod -ae
carl@carl:~$ modprobe ov51x
FATAL: Module ov51x not found.

I've been googling for ages now but still nothing has come up. there must be people using this successfully in linux.

---

### Post by amogz on 2005-09-17
help me in installing webcam in ubuntu....i have a genius webexpress2...tnx

---

### Post by mlomker on 2005-09-17
[QUOTE=c-m]carl@carl:~$ sudo depmod -ae
carl@carl:~$ modprobe ov51x
FATAL: Module ov51x not found.
[/QUOTE]

You don't have more than one kernel do you?  Kernel modules do have to be recompiled on each kernel.  Other than that I'd guess that the installer put it in the wrong directory.

If this command gives you nothing then it's not installed properly.

```

modprobe -l ov*

```

---

### Post by c-m on 2005-09-17
[QUOTE=mlomker]You don't have more than one kernel do you?  Kernel modules do have to be recompiled on each kernel.  Other than that I'd guess that the installer put it in the wrong directory.

If this command gives you nothing then it's not installed properly.

```

modprobe -l ov*

```[/QUOTE]
 yeah i have headers and source for kernel 2.6.10, 2.6.12 and 2.6.13 but 2.6.10 is the only one i use

carl@carl:~$ modprobe -l ov*
FATAL: Can't have multiple wildcards
carl@carl:~$ modprobe ov*
FATAL: Module ov51x_1.65_1.11_mark not found.
carl@carl:~$

---

### Post by mlomker on 2005-09-17
> 
carl@carl:~$ modprobe -l ov*
FATAL: Can't have multiple wildcards


I'm not sure why that command doesn't work for you, it does for me:

```

root@mlomkernote:/media # modprobe -l ov*
/lib/modules/2.6.10-5-amd64-k8/kernel/drivers/media/video/ovcamchip/ovcamchip.ko
/lib/modules/2.6.10-5-amd64-k8/kernel/drivers/usb/media/ov511.ko

```

As a matter of fact, that may be the correct driver right there.

Have you tried **modprobe ov511**?

---

### Post by c-m on 2005-09-17
bingo. "sudo modprobe ov511" hmm now how do i use the thing

---

### Post by c-m on 2005-09-17
how do i find out where the device is in terms /dev/**** since i've tried ./getjpeg -d /dev/video0 and all the way upto 9 but i get the error :

"Could not open device /dev/video1"

---

### Post by mlomker on 2005-09-17
Try **dmesg | grep ov511**.

---

### Post by c-m on 2005-09-17
[QUOTE=mlomker]Try **dmesg | grep ov511**.[/QUOTE]
 > 
carl@carl:~/ov51x-1.65-1.11-mark/test$ dmesg | grep ov511
usbcore: registered new driver ov511
drivers/usb/media/ov511.c: v1.64 for Linux 2.5 : ov511 USB Camera Driver


ignore this bit. added because message length was too short

---

### Post by mlomker on 2005-09-17
Usually it lists the device somewhere around where the driver loads.

Try **dmesg | tail** or **dmesg | more** and page through it.

---

### Post by c-m on 2005-09-17
nah the ov511 driver was only mentioned twice and never was there a reference to /dev/

Is there any software i can use to test the webcam? and can i use it for msn through gaim or amsn or something?

---

### Post by mlomker on 2005-09-18
[QUOTE=c-m]nah the ov511 driver was only mentioned twice and never was there a reference to /dev/

Is there any software i can use to test the webcam? and can i use it for msn through gaim or amsn or something?[/QUOTE]

It's probably not the correct driver, then.

One of the problems with webcams in linux is that there really aren't many programs that will use it.  None of those will work if you don't know what device to point it at...

I have the driver installed for my webcam, for example, but I still don't get a usable picture out of it...just a lot of lines and distorted images.  You could search for **qtcam**, which is a really basic viewer.  There are command-line tools like **vlc** that'll save a snapshot to a directory (so you can add that to a webpage, for example).

---

### Post by linkunderscore on 2005-09-18
[QUOTE=mlomker]It's probably not the correct driver, then.

One of the problems with webcams in linux is that there really aren't many programs that will use it.  None of those will work if you don't know what device to point it at...

I have the driver installed for my webcam, for example, but I still don't get a usable picture out of it...just a lot of lines and distorted images.  You could search for **qtcam**, which is a really basic viewer.  There are command-line tools like **vlc** that'll save a snapshot to a directory (so you can add that to a webpage, for example).[/QUOTE]



thats unfortunate. I think linux should be on the cutting edge of all technologies...not lagging behind. I am amazed at what linux has accomplished over the last 5 years. I hope more companies will start making linux drivers for their stuff from now on. It only makes sense :shrug: How hard would it be for a company to create a linux driver for their product? It would take more time and money but you would also create a larger consumer base. 

I will be a linux user for the rest of my life, and I am sure my purchasing habits will reflect this. Ubuntu has officially converted me. :)

---

### Post by c-m on 2005-09-19
[QUOTE=linkunderscore]thats unfortunate. I think linux should be on the cutting edge of all technologies...not lagging behind. I am amazed at what linux has accomplished over the last 5 years. I hope more companies will start making linux drivers for their stuff from now on. It only makes sense :shrug: How hard would it be for a company to create a linux driver for their product? It would take more time and money but you would also create a larger consumer base. 

I will be a linux user for the rest of my life, and I am sure my purchasing habits will reflect this. Ubuntu has officially converted me. :)[/QUOTE]
 i do try to be careful now with my hardware choices, but some things are just un avoidable (i got given the eyetoy free and its probably the best <£20 webcam about). I also had a skystar which was suppose to be easy to install in linux and it was. But i the only program i found that could do dvb was VDR or xine with VDR plugin. neither worked.

---

### Post by bugmenot on 2005-09-21
If you had taken the time to properly search Google, you'd have found that your vendor and device IDs are listed as supported by the OV511 driver .

```
Sony	EyeToy	N/A	OV519 (054c:0154)	OV7640	Works with ov51x driver
``` 
[http://public.planetmirror.com/pub/ov511/cameras.html](http://public.planetmirror.com/pub/ov511/cameras.html)

Make sure you take the right tool for testing the cam. I don't think dmesg shows the device assignment. Something using v4l is right. Gnomemeeting, VLC?

---

### Post by c-m on 2005-09-21
[QUOTE=bugmenot]If you had taken the time to properly search Google, you'd have found that your vendor and device IDs are listed as supported by the OV511 driver .

```
Sony	EyeToy	N/A	OV519 (054c:0154)	OV7640	Works with ov51x driver
``` 
[http://public.planetmirror.com/pub/ov511/cameras.html](http://public.planetmirror.com/pub/ov511/cameras.html)

Make sure you take the right tool for testing the cam. I don't think dmesg shows the device assignment. Something using v4l is right. Gnomemeeting, VLC?[/QUOTE]
 i did search google hence why i downloaded and installed the ov51x driver in the first place. There is precious little information regarding this camera and linux.

I have tried gnomemeeting and while i can select the camrea "logitec eyetoy camera/"  (under audio devices), and v4l2 as the plugin. Under video and imput devices devices  it states "no devices found?

---

### Post by yyagol on 2006-05-11
Thak you guys finaly i got the module runing
with the help of [COLOR="Lime"]mlomker[/COLOR] ( depmod -ae )
and when i open any apps that uses the driver like **vlc** or **camorama**
i cant get a picture instaed i get a black or a green picture with
a snow stripe on the uper end ....
this is what i get after i try to see a picture
```
@var32:~$ dmesg | grep usb
[4294672.177000] usbcore: registered new driver usbfs
[4294672.177000] usbcore: registered new driver hub
[4294673.388000] usb 2-2: new low speed USB device using ohci_hcd and address 3
[4294673.754000] usb 3-2: new full speed USB device using ohci_hcd and address 2
[4294677.975000] usbcore: registered new driver hiddev
[4294677.988000] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:03.1-2
[4294677.988000] usbcore: registered new driver usbhid
[4294677.988000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4294678.101000] /lib/modules/2.6.15-21-386/kernel/drivers/usb/media/ov511/ov51x.c: USB OV519 video device found
[4294678.572000] /lib/modules/2.6.15-21-386/kernel/drivers/usb/media/ov511/ov51x.c: Sensor is an OV7648
[4294678.885000] /lib/modules/2.6.15-21-386/kernel/drivers/usb/media/ov511/ov51x.c: Device at usb-0000:00:03.2-2 registered to minor 0
[4294678.885000] usbcore: registered new driver ov51x
[4294678.885000] /lib/modules/2.6.15-21-386/kernel/drivers/usb/media/ov511/ov51x.c: v1.65-1.12-mark : ov51x USB Camera Driver
[4294678.969000] usbcore: registered new driver snd-usb-audio
[b][4294904.427000] /lib/modules/2.6.15-21-386/kernel/drivers/usb/media/ov511/ov51x.c: OV519 doesn't need proprietary decompressor. It uses standard JPEG
[4294904.785000] /lib/modules/2.6.15-21-386/kernel/drivers/usb/media/ov511/ov51x.c: EOF without SOF
[4294905.656000] /lib/modules/2.6.15-21-386/kernel/drivers/usb/media/ov511/ov51x.c: EOF without SOF[/b]
```
```
$ lsmod |grep ov
ov51x                  98744  0
videodev                9856  1 ov51x
usbcore               129668  7 snd_usb_audio,snd_usb_lib,ov51x,usbhid,ehci_hcd,ohci_hcd
$ lsmod |grep video
video                  16260  0
videodev                9856  1 ov51x
$ ls -l /dev/video
lrwxrwxrwx 1 root root 6 2006-05-11 11:13 /dev/video -> video0

```
how can i make it work ????:-k





.

---

### Post by yyagol on 2006-05-11
OK i found it
here is what i did :

i download the driver from here [http://projects.stuartrharper.net/OV519.html#Build_Marks_Driver]("http://projects.stuartrharper.net/OV519.html#Build_Marks_Driver")

then did this :
```

tar -xjf ov51x-1.65-1.11-mark.tar.bz2
cd ov51x-1.65-1.11-mark
make
sudo make install
sudo depmod -ae
sudo modprobe ov51x
sudo apt-get install gqcam
```
After i open the **gqcam** i tweak it to use [COLOR="Red"]jpeg[/COLOR] and that was it ;)

---

### Post by toots on 2006-05-15
Hi all..

Try google with those key words:

"ov51x jpeg", the first result leads to this page:
[http://www.rastageeks.org/ov51x-jpeg/index.php/Main_Page](http://www.rastageeks.org/ov51x-jpeg/index.php/Main_Page)

Which provides a working fork of the original driver.
Please read all documentation, FAQ and howtos, a lot of potential issues are explained there.


Romain

---

