---
title: "Dell Inspiron 1521 with Gutsy 7.10 32 bit working"
date: 2007-11-08
forum: Hardware &amp; Laptops
---

### Post by huck416 on 2007-11-08
I got my Dell Inspiron 1521 to work with Gutsy 7.10 32 bit version. Along the way I had some issues especially with sound and the webcam however, with help from several people on this forum, it all works great. The only thing I haven't tested yet is DVD burning.

Hardware: AMD 64x2 2.2ghz, ATI Radeon Xpress 1270 video, integrated sound (ATI SBx00 which shows as HDA-Intel using STAC 9205 chipset), built-in Omnivision webcam 2gig RAM, 160gig SATA HD 8X DVD+/-RW DL, Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

How it worked:

Left Vista Home Premium installed and booted to live CD of Gutsy 32-bit. Used gui install option and took 100gig for Gutsy and left the rest for Vista (unfortunately still need Wxxxxxxs for a couple things that don't work under VMWare). 

Video:	restricted driver works with no further config - only restart after install.

Then I did a mass install of the following:
```
sudo apt-get install unison unison-gtk kshisen ndiswrapper-common ndiswrapper-utils-1.9 smbfs kpilot firefox

```
I use unison for all my backup and file sync between the laptop and an external usb drive (or 2). Ndiswrapper is required for my wireless to work. NOTE: the restricted driver for the broadcom card didn't work; it kept giving me an error on boot so I dumped it and reverted to using ndiswrapper. More on that. SMBFS is so I can connect to my NAS which is a Windows based file system. Kpilot for my Palm Tungsten E. Now some more specifics.

Network
For wired just installed smbfs to connect to my windows networked files
For wireless, 
Don't use restricted driver. Instead install ndiswrapper-utils 
```
sudo apt-get install ndiswrapper-utils-1.9
``` (check for current version via aptitude search ndiswrapper)

This next line will load ndiswrapper at each boot:
```
sudo echo "ndiswrapper" | sudo tee -a /etc/modules
```

Now you need to find the appropriate Wxxxxxxs driver for your wireless card. For mine it was bcmwl5.inf. You need to extract both the .inf and .sys files. Then load the broadcom driver with ndiswrapper. Run this in the directory of the driver you extracted.

```
sudo ndiswrapper -i bcmwl5.inf
```

Next it was via System Settings > Network Settings > Configure Device > and entered my router WEP info. Then via Knetworkmanager > Other Networks > connect and voila, encrypted wireless.

Palm Tungsten E

You need to add the following to fstab for vmware usb support: 

usbfs /proc/bus/usb usbfs auto 0 0

This is so I can sync some other Palm applications that don't sync with Linux. They are strictly Wxxxxxxs based 

Now to sync with Kontact via Kpilot, create /etc/udev/rules.d/10-custom.rules and the following on one line:

BUS="usb", SYSFS{product}="Palm Handheld*", KERNEL="ttyUSB*", NAME{ignore_remove}="pilot", MODE="666"

Add visor to /etc/modules:

```
sudo echo "visor" | sudo tee -a /etc/modules
```
```
modprobe visor
```
Install kpilot and sync

Webcam
The following eventually worked for me although I had some issues during the installation. There were some dependencies and had to install a few other packages. Sorry, I don't have those listed anymore. Suffice to say, if you have a problem running the command below, it will tell you which you need. I just inserted those before the others in the same command and installed the whole lot in one shot. And it works with Kopete. 

```
sudo apt-get install subversion build-essential linux-headers-$(uname -r) && svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk && cd trunk && make && sudo install -v -m66 uvcvideo.ko /lib/modules/$(uname -r)/kernel/ubuntu/media/usbvideo/uvcvideo.ko && sudo depmod -ae

```

Corrected code for Gutsy from linux23dragon
```
sudo cp -av /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules &&
sudo install -v -m644 uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko && sudo depmod -ae
```

Kopete
It works now although initially it was crashing. The fix package is kdelibs4c2a_3.5.8-0ubuntu3_i386.deb. I'm sorry I don't have the link to where I got this.

Sound

This was a real problem for the longest time. Absolutely no sound. After endless searching through forums and trying almost everything it came down to one simple fix which I applied after the clean install and before any ALSA packages. 

This gave me sound:
```
sudo apt-get install linux-backports-modules-generic
```

This gave me more control over my sound:
```
sudo apt-get install alsamixergui alsa-tools alsa-tools-gui alsa-oss alsaplayer-alsa
```

And it's been running great ever since. The next step is to configure the wireless with WPA2 instead of WEP. After that maybe I'll get some work done. Hope this helps someone.

---

### Post by dhoult on 2007-11-09
Well I'm glad to see someone else with an Inspiron 1521 has provided some useful instruction for dualbooting. Yeah I got a new Inspiron 1521. Everything's the same as yours. I've done dualbooting before on various other computers without any problems. But the 1521 has been a challenge. As your aware, these laptops have Dell Media Direct (that first button above the keyboard), and sets up a partition at the very end of the harddrive. Now to dual boot with Media Direct there will be 5 partitions, Masterboot, Vista, Ubuntu, Swap and Media Direct. The problem is that GParted only allows up 4 partitions. I'm curious how you were able to solve this?? I've tried EasyBCD but the instructions were terrible.
D.
Vancouver

---

### Post by huck416 on 2007-11-09
I skipped a step in my explanation. Not being a fan of any of the "bells and whistles" manufacturers put on machines. I formatted the entire hard drive first getting rid of media direct. I then installed Vista on the entire drive from the restore disk provided. I then installed some of the Dell utilities to get some functionality back but I did not reinstall media  direct; I personally don't need it. From there I proceeded with my Kubunt install.

---

### Post by WoPr on 2007-11-15
Hi huck416!

Do you have Skype 2.0 beta with webcam? If so,  did you do someting more to get it work?

I have an Inpiron 1521 and when I press the TEST button of the Skype vidoe options menu, I get no image, just blank one.

Thanks and best regards

---

### Post by huck416 on 2007-11-15
WoPr,

Sorry, I can't help you on that one. I'm not using Skype at all. I've thought about it and if I try it and get it working I'll be sure to add it my post. Good luck.

Huck416

---

### Post by WoPr on 2007-11-16
Ok!

I see in the Skype-Ubuntu Webcam support that it works with the 1520 webcam, and I thought that the cam of the 1521 was the same, but maybe it is another model.

Thanks a lot a best regards,
WoPr

---

### Post by alexander.forster on 2007-11-16
hi, when i tried to run the code you provided i got this output. 
any help would be very much appreciated
thanks in advance :)

```
$ sudo apt-get install subversion build-essential linux-headers-$(uname -r) && svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk && cd trunk && make && sudo install -v -m66 uvcvideo.ko /lib/modules/$(uname -r)/kernel/ubuntu/media/usbvideo/uvcvideo.ko && sudo depmod -ae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
subversion is already the newest version.
build-essential is already the newest version.
linux-headers-2.6.22-14-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libavahi1.0-cil
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Checked out revision 141.
Building USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
`uvcvideo.ko' -> `/lib/modules/2.6.22-14-generic/kernel/ubuntu/media/usbvideo/uvcvideo.ko'
install: cannot create regular file `/lib/modules/2.6.22-14-generic/kernel/ubuntu/media/usbvideo/uvcvideo.ko': No such file or directory

```

---

### Post by linux23dragon on 2007-11-16
> **alexander.forster said:**
> hi, when i tried to run the code you provided i got this output. 
any help would be very much appreciated
thanks in advance :)

```
$ sudo apt-get install subversion build-essential linux-headers-$(uname -r) && svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk && cd trunk && make && sudo install -v -m66 uvcvideo.ko /lib/modules/$(uname -r)/kernel/ubuntu/media/usbvideo/uvcvideo.ko && sudo depmod -ae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
subversion is already the newest version.
build-essential is already the newest version.
linux-headers-2.6.22-14-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  libavahi1.0-cil
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Checked out revision 141.
Building USB Video Class driver...
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
`uvcvideo.ko' -> `/lib/modules/2.6.22-14-generic/kernel/ubuntu/media/usbvideo/uvcvideo.ko'
install: cannot create regular file `/lib/modules/2.6.22-14-generic/kernel/ubuntu/media/usbvideo/uvcvideo.ko': No such file or directory

```


The install path is only good for Ubuntu-7.04.  To install the web cam driver in Gusty, you will need to change the install path like this (I've also added a line so you have a backup copy of the original driver, if things don't turn out for you). : -
```

sudo cp -av /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko /lib/modules &&
sudo install -v -m644 uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko && sudo depmod -ae
```


If you need more information on the webcam then take a look at this [***_[COLOR="Blue"]thread[/COLOR]_***](" http://ubuntuforums.org/showthread.php?p=3642769#post3642769")

---

### Post by huck416 on 2007-11-16
First of all, a big thanks to linux23dragon for explaining the 7.04 / 7.10 difference. That would explain the problems I had when I ran the code in my initial post. If you don't mind, I'll edit my post to reflect the correct code. As mentioned in my initial post, I'm still a newbie too Linux but am enjoying the learning experience. 

For WoPr, I'm sure I've got the same Omnivision webcam in my 1521 as the 1520 and it works with Kopete fine. I just haven't tried Skype.

Always ready to try something.

Huck

---

### Post by TapaGeuR on 2007-11-19
> **huck416 said:**
> This was a real problem for the longest time. Absolutely no sound. After endless searching through forums and trying almost everything it came down to one simple fix which I applied after...  i've found your thread! OMG! You can't resume it better, it's been months i want to fix my sound. I still have a few things to fix so i'll read more in details your post,  Thanks for the wrap-up of all these infos. ;)

---

### Post by huck416 on 2007-11-20
TapaGeuR,

I hope that after you try some of the things that worked for me, they also solve your problems. Good luck

Huck416

---

### Post by TapaGeuR on 2007-12-02
Thanks! I'm now thinking about which program i should install to use my webcam to take picture or film some movie,  I don't know any program that can do both so if you have some suggestions, they are more then welcome! ;)

---

### Post by pezmanlou on 2007-12-19
Thank you so much; I now have sound!  The output is great but have you gotten the microphone to work?

---

### Post by huck416 on 2007-12-19
pezmanlou,

Haven't tried the mic yet; don't have a use for it yet.

---

### Post by brucedixon on 2008-01-20
Thanks for  the instructions, though I hope I  do not have to tear Vista out and re-install it again, as you seem to say in the beginning of this thing.  

Got a Dell Inspiron 1521 a couple  weeks ago and immediately shrunk the partitions to  make room for a Linux install.  Been waiting for a free day when the workload is not prohibitively high to try it.

If ripping Vista out and re-installling it is really what it takes I almost want to wait a month till I can spend the extra $150 on a 250 GB HD for this thing.  Either way, it's gotta be done, cause I gotta have Linux AND Vista available on this laptop to do what  I gotta do.

I'm guessing that Kubuntu can't read the new version of NTFS either, right?  I am gonna need a common partition whose data can be accessed either from Kubuntu OR Vista, whichever I happen to be running at the moment.

Bruce Dixon
Marietta GA
[www.blackagendareport.com](www.blackagendareport.com)

---

### Post by huck416 on 2008-01-22
You don't have to rip out Vista completely. The first install I did of Gutsy was with Vista intact as it was from the factory. I took it out as I didn't want Dell Media Direct so it was just wasting space. 

As far as a common partition, I installed Ext2 IFS on Vista. Then I was able to mount my entire LInux partition as a network drive in Vista. So now my documents folder is accessible by both OS's without duplication. No issues so far. Good luck

Here's the link to the site where I got the download..

[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

---

### Post by halen666 on 2008-02-08
thank you for helping us, but hey i got a question. how do you get the driver for the wireless card if i am using the 64 bit edition???????

i really need the driver but, dell doesn't have the one for windows 64-bit edition, so i believe that is why the 32-bit edition driver is not working in my ubutnu 7.10 64-edition

thank you

---

### Post by ericstoesser on 2008-02-14
yep.. 64 bt here as well... no luck with the bcmwl5 driver you ae using, but i have an inspiron 1521 as well.... im clueless HEEEEELLLP

---

### Post by huck416 on 2008-02-15
Have you checked out post #8 here: [http://ubuntuforums.org/showthread.php?t=272790?](http://ubuntuforums.org/showthread.php?t=272790?)  It seems Brainfry has got it working. I'm sorry I'm not much help with the 64-bit version. Good luck.

---

### Post by ericstoesser on 2008-03-09
I got wifi working with using ndiswrapper and the newest windows xp driver from the dell website, works great... i got most sound working with the alsa fix... but i'm having a hard time getting my cam to work with stickam and my mic still doesn't work

---

### Post by CloudFX on 2008-03-15
excellent, excellent, excellent. I'm just trying to get my sound working now. I've done both commands to no success. Any advice? .also, Dell released firmware for wireless which you can find when u select the wireless card in the restricted drivers.

---

### Post by rajkumarc2000 on 2008-04-06
Cool, this thread was really helpful for me. It got everything working for me wifi,sound, graphics with OpenGL. 

Thanks a bunch. the only issue was that i had to use the non-free software drivers for my wifi and graphics. this option was given to me only on the Free CD which i got from Ubuntu. :)

Even skype with video started working without any issues.

---

### Post by huck416 on 2008-04-07
Glad the post helps. BTW, have you got your wifi working with WPA2 or just WEP? I'm using WEP at the moment and haven't really tried to configure WPA2; I'm not sure if the broadcomm card in this machine will support it. Also have you got the mic working OK? There have been some issues with that as well.

---

### Post by kronictokr on 2008-04-16
Install kpilot and sync

Webcam
The following eventually worked for me although I had some issues during the installation. There were some dependencies and had to install a few other packages. Sorry, I don't have those listed anymore. Suffice to say, if you have a problem running the command below, it will tell you which you need. I just inserted those before the others in the same command and installed the whole lot in one shot. And it works with Kopete.

Code:

sudo apt-get install subversion build-essential linux-headers-$(uname -r) && svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk && cd trunk && make && sudo install -v -m66 uvcvideo.ko /lib/modules/$(uname -r)/kernel/ubuntu/media/usbvideo/uvcvideo.ko && sudo depmod -ae

quote^^^^^^^^

had to edit this code>>delete<<"kernel"<<in the last file sequence
my sequence was modules/ubuntu/media/usb.....
if yours is like this just delete kerner in the code and re eneter the code, worked for me
new code:
sudo apt-get install subversion build-essential linux-headers-$(uname -r) && svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk && cd trunk && make && sudo install -v -m66 uvcvideo.ko /lib/modules/$(uname -r)/ubuntu/media/usbvideo/uvcvideo.ko && sudo depmod -ae

---

### Post by gmstalk on 2008-06-05
> **huck416 said:**
> pezmanlou,

Haven't tried the mic yet; don't have a use for it yet.

I am trying to get the MIC on my 1521 working. I also have  AMD Turion(tm) 64 X2 version. The webcam works but the mic does not. Did you have any success with the built in microphone?

lspci:
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
	Subsystem: Dell Unknown device 01fc
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
lshw:
   *-multimedia
             description: Audio device
             product: SBx00 Azalia
             vendor: ATI Technologies Inc
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=64 module=snd_hda_intel

---

