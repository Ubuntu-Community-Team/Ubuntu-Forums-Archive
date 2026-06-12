---
title: "How I got my Hauppauge WinTV USB2 working"
date: 2006-04-09
forum: Hardware &amp; Laptops
---

### Post by dixonstalbert on 2006-04-09
(check out Rafael Gattinger's excellent instructions at [http://www.unet.univie.ac.at/~a9826090/en/projects/linux/hardware/wintv-usb2/]("http://www.unet.univie.ac.at/%7Ea9826090/en/projects/linux/hardware/wintv-usb2/")
)
[SIZE="4"][COLOR="Red"]****[/COLOR][/SIZE]I noticed that this weblink is no longer available so I will try to give you the steps from memory: 


1. The WinTV  needs a driver in order to 'mount' itself at /dev/video0. This driver is in the form of a 'kernel module' which you can obtain from the link below. Before you can install it though, you need to get some helper programs to 'build' and 'install' the module into your kernel. Go System > Administration > Synaptic Package Manager and use search to find (and then install) these programs:

build-essentials
make
linux-kernel-headers
linux-source
gcc-3.4

2. you will also need to get 'hg' program from synaptic package manager. This is a program that handles the archive the driver comes wrapped in.


3. You should now be ready to download   [http://linuxtv.org/hg/v4l-dvb?repo=hg%2Fv4l-dvb&style=gitweb&cmd=changelog&rev=72577298a988#]("http://linuxtv.org/hg/v4l-dvb?repo=hg%2Fv4l-dvb&style=gitweb&cmd=changelog&rev=72577298a988#") and install program using the link below. As I mention below, I simply went to the directory I saved it to and double clicked on it in nautilus and let file-roller open and extract to the /hg-v4l-dvb-72577298a988 directory

4. You will have to modify the Make.config file in /v4l subdirectory before you make and install it. Open it with a text editor and find the following code block and change the CONFIG_VIDEO_BUF_DVB line as shown to = n  
```
ifneq ($(KERNELRELEASE),)
 CONFIG_DVB_CORE := $(shell test $(SUBLEVEL) -ge 10 -a $(PATCHLEVEL) -ge 6 && echo m)
 CONFIG_VIDEO_BUF_DVB :=[COLOR="Red"]n[/COLOR]
 CONFIG_VIDEO_DEV := $(shell test $(PATCHLEVEL) -ge 6 && echo m)
 CONFIG_EM28XX    := $(shell test $(PATCHLEVEL) -ge 6 && echo m)
endif
```

save your changes and open a terminal.

5. use cd command and get to the /v4l subdirectory then put in the following command:

```
sudo make && make install
```


6. The make command will 'build' the modules for a whole bunch of drivers. The terminal window will scroll out the output of this process. make note of any error messages. make install command   will install the drivers into your kernel.

7.  It is a good idea to reboot your computer now and unplug the usbtv2 to make sure no other drivers have installed themselves that could interfere with this driver

8. open a terminal again and type```
sudo modprobe -v em28xx 
``` (em28xx is particular video driver the wintvusb2 uses). 

9. Plug in usbtv2. and install TVTIME application to run usbtv2 

```
sudo apt-get install tvtime
```


9. Open tvtime and see if error 'no capture device found' is gone. if it is gone, then driver is successfully loaded. You probably will have to change some setting in tvtime- check their excellent webpage if you need help with this.  











long version:

Hauppauge makes a variety of USB tv capture devices, many with very similar names.

This is the entry level device that gives you analog reception.  The wintvusb2pvr – which I thought I was buying because of the large label on the box that says 'softPVR'-is the much preferred device.  (I have attached a picture of the box my 'non-PVR' came in.)

This device however will give you a picture just as good as the non-digital channels on your television. 

(you should probably check out [http://www.isely.net/pvrusb2.html]("http://www.isely.net/pvrusb2.html")  before you go shopping for the real PVR version of the USB2.)

Anyways I followed Rafaels instructions, using Nov 19, 2005 snapshot mentioned in Step 4.

After I changed my xorg.conf ( I have an ATI video card and am running a dual monitor 'big desktop'. I had to add Option          "VideoOverlay" "on"
    Option         "OpenGLOverlay" "off" to my "Device" Section), I got a clear picture and I got sound by plugging my   'audio out' into my microphone input and turning up the mic and main volume up all the way.

Unfortunately, the channels numbers were out by 2 and when I went to listen to an mp3 I would forget to turn the volume down again and get blasted out of the room.


I tried getting the latest driver , but linuxtv  has  switched from  CVS  to  Hg  (Mercurial) system ,  so  you have  to set up  Hg  on your system  (link  to instructions on  this  page:  [http://linuxtv.org/repo/]("http://linuxtv.org/repo/") ) 

As of May 19, 2006 latest driver found at [hg clone http://linuxtv.org/hg/v4l-dvb ]("http://www.ubuntuforums.org/hg%20clone%20http://linuxtv.org/hg/v4l-dvb")

has a bug that will crash your system. If your use this link

  [http://linuxtv.org/hg/v4l-dvb?repo=hg%2Fv4l-dvb&style=gitweb&cmd=changelog&rev=72577298a988#]("http://linuxtv.org/hg/v4l-dvb?repo=hg%2Fv4l-dvb&style=gitweb&cmd=changelog&rev=72577298a988#")

it should retreive a tarball from before the bug started in mid-april that should work. unpack the tarball as per Rafael's instructions  Step Number 4.  I used file-roller (as root) and unpacked it to its subdirectory /hg-v4l-dvb-72577298a988 instead of /v4l-kernel, so I had to use this subdirectory for the rest of Rafael's instructions. Also when I got to step 6, I had to use 'make clean' instead of 'make' to clean out stuff from my prior install of the Nov 2005 version.

I rebooted before I did Step 8,  (recommended in Markus Rechburger's linuxtv wiki article)  Now channels were correct numbers and sound was at correct volume. I could not tune into channels 5 and 6 though.

I live in Canada and had to adjust TVTIME NTSC cable mode to 'Nominal'  ( Setup > Channel Management > Change NTSC cable mode)

My next step is to get video recording working. TVTIME has been specifically designed not to do this and so I have to find another app. Unfortunately, TVTIME was relatively easy compared to other apps to get working! 

Xawtv completely crashes my system. I can get a picture but no sound with  mplayer by using the command line  ```
 mplayer   -tv driver=v4l2:chanlist=us-cable:norm=NTSC:outfmt=yuy2:device=/dev/video0:input=0 -vo xv  tv://
``` but thats about it. I have looked into xine but I cannot get scantv to recognize wintvusb2 to build a frequency table . I was able to get values of frequencies by running tvtime-scanner, but I havent found the format for the xine frequency table to manually build one. If someone figures how to record with the WinTV USB2 let me know.

---

### Post by dragonlor20 on 2007-02-03
I think your link to the driver is more/less broken. In any event, the file you want people to download isn't there... I found a file at this link:

[http://www.cadsoft.de/vdr/download.htm](http://www.cadsoft.de/vdr/download.htm)

I am trying it now...

---

### Post by cOzAtS on 2008-03-25
Got that working? If anyone has a solution plz post a link or a tutorial :D:D

---

### Post by patrickfromspain on 2008-03-25
try kaffeine. It's KDE, but it absolutely rocks

---

