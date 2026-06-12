---
title: "Howto: Sony Vaio VGN-CR21* &amp; Ubuntu 7.10 (Gutsy Gibbon)"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by murmel on 2007-12-26
[SIZE="4"]How to get Sony Vaio VGN-CR* working[/SIZE]
[LIST]**Installation of Ubuntu 7.10 Gutsy Gibbon**  Use the [alternative edition](ftp://ftp.sunet.se/pub/os/Linux/distributions/ubuntu/ubuntu-cd/7.10/ubuntu-7.10-alternate-i386.iso). (Desktop Edition doesn't work because of the graphic card)[/LIST]
[LIST][SIZE="3"]**Problem:** Gnome won't start and startx gives errors (using Radeon Mobility X3200[/SIZE]
[SIZE="3"]**Solution:**[/SIZE]

*Update ubuntu and install xorg-driver-fglrx (You may have to comment the CD-ROM in /etc/apt/sources.list)*
```

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo /etc/init.d/gdm restart
```
*Source: [ubuntuformus.org](http://ubuntuforums.org/showthread.php?t=497679)*


[LIST]**Second solution:**
```
sudo apt-get update
sudo apt-get dist-upgrader
sudo apt-get install linux-restricted-modules-$(uname -r)
wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-01-x86.x86_64.run --no-check-certificate
sudo apt-get install build-essential dh-make debhelper debconf libstdc++5 dkms
sudo sh ati-driver-installer-8-01-x86.x86_64.run --buildpkg Ubuntu/gutsy
```

Now tell the restricted-driver-manager that you'll install the driver manually.
```
sudo nano /etc/default/linux-restricted-modules-common
```
add fglrx to the disabled modules
```
DISABLED_MODULES="fglrx"
```
Install the drivers (make sure that there's only the .deb's you've created with the ati-driver-installer!):
```
sudo dpkg -i *.deb
```
Configure the driver:
```
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```
and now restart:
```
sudo shutdown -hr now
```
*Source: [wiki.cchtml.com](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_8.1_Driver_Manually)*[/LIST][/LIST]


[LIST][SIZE="3"]**Problem:** No sound.
**Solution:**[/SIZE]

[i]This for the sound card (Intel Corporation 82801H (ICH8 Family))
Edit /etc/modprobe.d/alsa-base (**sudo nano /etc/modprobe.d/alsa-base**) and add this in the bottom of it[/i]
```
options snd-hda-intel model=vaio
```
*then do this*
```
sudo apt-get install linux-backports-modules-$(uname -r)
```
*Source: [linuxtechie.wordpress.com](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)*
***A reboot would be preferred!***[/LIST]

[LIST][SIZE="3"]**Problem:** Compiz and Extra at the Visual Effects doesn't work.
**Solution:**[/SIZE]

[i][**Note:** Looks like this is not needed when you've installed the graphic drivers manually.

*You have to install xserver-xgl, then do these things:*
```
sudo nano /etc/X11/xorg.cfg
```
*change to or add this (at the bottom):*
```
Section "Extensions"
Option "Composite" "Enable"
EndSection
```
*then install xserver-xgl and reboot:*
```
sudo apt-get install xserver-xgl
sudo shutdown -r now
```
*(this may change your keyboard layout, just change it in "System -> Preferences -> Keyboard -> Layouts")*[/LIST]

[LIST][SIZE="3"]**Problem:** Webcam (05ca:1839 Ricoh Co., Ltd) doesn't work.
**Solution:**[/SIZE]

*Download: r5u870-0.20.tar.bz2  (attached to this thread) and extract it* 
```
tar xf r5u870-0.20.tar.bz2
```
[/i]Then install it:[/i]
```
cd r5u870-VCC6/
sudo make
sudo make install
```
*Load all the necessary modules:*
```
sudo modprobe videodev
sudo modprobe video-buf
sudo modprobe v4l1-compat
sudo modprobe v4l2-common
sudo modprobe r5u870
```
*Copy the firmware to /lib/firmware:*
```
sudo cp ./r5u870_1839.fw /lib/firmware
```
[i]And chmod /etc/video0 (maybe it's called video1 or something els for you)
(This may require a reboot to find it)[/i]
```
sudo chmod 666 /dev/video0
```
*Try it out with xawtv (change /Etc/video0 to the one that is right for you)*
```
sudo apt-get install xawtv
xawtv -c /dev/video0 -geometry 320x240
```
[i]Source: [alegria071.blogspot.com](http://alegria071.blogspot.com/2007_08_01_archive.html) (Spanish, I can't understand a word more than the commands. Used [Google Translate](http://www.google.com/translate_t) to understand some stuff there.)
You should also read the README in the archive (r5u870-0.20.tar.bz2)![/i]
[LIST][SIZE="2"]**Works with:**[/size]

[i]aMSN
The latest [Skype Beta](http://www.skype.com/go/getskype-linux-beta-dynamic) 
Cheese (sudo apt-get install cheese)!
Motion (sudo apt-get install motion) works fine! But haven't gotten motioneye working. (Edit /etc/motion/motion.conf and change target_dir and chmod 777 your target dir)[/i][/list]

**If there is any problem with colours or something like that, try with a reboot.**[/list]

[B]I hope this will help other Vaio users into the world of Ubuntu!

Feedback is appreciated!

- Simon

---

### Post by mauriciohf1 on 2007-12-27
Thank you, the solution for the sound problem works on a vaio-cr120E is a US version. Your motioneye is working is the other thing that have not work for me?.

Mauricio H (COL)

---

### Post by murmel on 2007-12-27
I don't know, yet, how to get the WebCam working.. But I'm trying and I will post when I've found a solution! =)

---

### Post by nimrod on 2007-12-29
Thanks! This post helped med get my sound working on my Sony Vaio VGN-FZ19VN. Thanks again!

---

### Post by OrionFyre on 2007-12-30
the
```
options snd-hda-intel model=vaio
```
and
```
sudo apt-get install linux-backports-modules-$(uname -r)
```

solved my audio enigma.

THe sound would not work until I plugged in headphones, I would hear music out of the 'phones then once unplugged the sound would come from the speakers fine.

Once I did those two and rebooted I got the wonderful Ubuntu drum roll at the login screen.
You are my hero!

Guess who's getting a big internet huggsies!?! Yes, you! *HUGGSIES*

---

### Post by murmel on 2007-12-30
I'm glad that it helped you! I've just been reinstalling my laptop some times and I really had to have this stuff gatherd.. somewhere.. to help myself.. And I thought others maybe needed it too ;)

Whoopidoo :):guitar:

---

### Post by gusanto on 2007-12-30
I bought Sony Vaio VGN-NR120ES on the boxing day and tried to run several live CD Linux distros.  The results were varied.  Ubuntu 7.10 failed to boot, just stopped and nothing happened.  Ubuntu 7.04 succesfully boot after pressing F6, breek=top, then modprobe piix, exit (as suggested by one link, forgot where), but wireless not detected and display is only smaller than the actual screen (15.4 inchies).
My questions:
1. Any idea how to run the live CD (later I will install it on HD) Ubuntu 7.10 on this laptops?  Any specific issue on how dual boots with Windows Vista on this laptops that needs to be concerned?
2. Can I run alternate CD as a live CD?
3. Any link (specific for this laptops; I tried googling but did find any) for dual boots of this laptops?
Thanks.

---

### Post by murmel on 2007-12-30
I have no idea how it is with the dualboot but I don't think it'll be a problem!
When it comes to the live cd you HAVE to use the Alternative disc. That's because the graphiccard isn't supported out of the box. :(
I'll post how to install the webcam soon.

---

### Post by murmel on 2007-12-30
I've now added how to get the webcam (05ca:1839 Ricoh Co., Ltd) working!

---

### Post by OrionFyre on 2007-12-30
```
orionfyre@orionfyre-laptop:~/temp/r5u870-VCC6$ sudo make
[sudo] password for orionfyre:
make -C /lib/modules/2.6.22-14-generic/build M=/home/orionfyre/temp/r5u870-VCC6 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/orionfyre/temp/r5u870-VCC6/r5u870_md.o
  CC [M]  /home/orionfyre/temp/r5u870-VCC6/usbcam.o
  LD [M]  /home/orionfyre/temp/r5u870-VCC6/r5u870.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/orionfyre/temp/r5u870-VCC6/r5u870.mod.o
  LD [M]  /home/orionfyre/temp/r5u870-VCC6/r5u870.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
orionfyre@orionfyre-laptop:~/temp/r5u870-VCC6$ sudo make install
make -C /lib/modules/2.6.22-14-generic/build M=/home/orionfyre/temp/r5u870-VCC6 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make INSTALL_MOD_PATH= INSTALL_MOD_DIR=extra \
                -C /lib/modules/2.6.22-14-generic/build M=/home/orionfyre/temp/r5u870-VCC6 modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  INSTALL /home/orionfyre/temp/r5u870-VCC6/r5u870.ko
  DEPMOD  2.6.22-14-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
install -m 0644 -o root -g root r5u870_1830.fw r5u870_1832.fw r5u870_1833.fw r5u870_1834.fw r5u870_1835.fw r5u870_1836.fw r5u870_1870_1.fw r5u870_1870.fw r5u870_1810.fw r5u870_183a.fw /lib/firmware
/sbin/depmod -a
orionfyre@orionfyre-laptop:~/temp/r5u870-VCC6$ sudo modprobe videodev
orionfyre@orionfyre-laptop:~/temp/r5u870-VCC6$ sudo modprobe video-buf
orionfyre@orionfyre-laptop:~/temp/r5u870-VCC6$ sudo modprobe v4l1-compat
orionfyre@orionfyre-laptop:~/temp/r5u870-VCC6$ sudo modprobe v4l2-common
orionfyre@orionfyre-laptop:~/temp/r5u870-VCC6$ sudo modprobe r5u870
orionfyre@orionfyre-laptop:~/temp/r5u870-VCC6$ sudo cp ./r5u870-VCC6/r5u870_1839.fw /lib/firmware
cp: cannot stat `./r5u870-VCC6/r5u870_1839.fw': No such file or directory
orionfyre@orionfyre-laptop:~/temp/r5u870-VCC6$ sudo cp r5u870_1839.fw /lib/firmware
orionfyre@orionfyre-laptop:~/temp/r5u870-VCC6$ sudo chmod 666 /dev/video0
chmod: cannot access `/dev/video0': No such file or directory
orionfyre@orionfyre-laptop:~/temp/r5u870-VCC6$ sudo chmod 666 /dev/video1
chmod: cannot access `/dev/video1': No such file or directory
orionfyre@orionfyre-laptop:~/temp/r5u870-VCC6$ sudo chmod 666 /etc/video1
chmod: cannot access `/etc/video1': No such file or directory
orionfyre@orionfyre-laptop:~/temp/r5u870-VCC6$ 
```

OK I get to the CHMOD.... and i have problems. I cannot find the video0 or video1 or any 'video'
as you can see my problems started with the copy "cp ./r5u870-VCC....":lolflag:

---

### Post by murmel on 2007-12-30
Copy the firmware to /lib/firmware:
```
sudo cp ./r5u870_1839.fw /lib/firmware
``` 

This is how it should be done! (When you're in the extracted directory!)
I've updated it, forgot it when i posted. This should probably work!

---

### Post by OrionFyre on 2007-12-30
:guitar: you rock murmel, 
```

orionfyre@orionfyre-laptop:~/temp/r5u870-VCC6$ sudo cp ./r5u870_1839.fw /lib/firmware
[sudo] password for orionfyre:
orionfyre@orionfyre-laptop:~/temp/r5u870-VCC6$ sudo chmod 666 /dev/video0
chmod: cannot access `/dev/video0': No such file or directory
orionfyre@orionfyre-laptop:~/temp/r5u870-VCC6$ 

```

Ok, the cp works, but now I have no such file or directory still on the chmod.
:confused:

EDIT: Ok, no one told this noob a reboot was necesarry! lol 
after rebooting I found video0 in /dev/ and ran chmod.

When I run xawtv, my webcam comes up! YAY! except now all i get is the like the green channel. I have no red or blue.
but looking at it on the positive side I was at 0% working, now I'm at 33% with only 1 channel! lol.
```
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-generic)
WARNING: Your X-Server has no DGA support.
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
orionfyre@orionfyre-laptop:~$ 

```

---

### Post by murmel on 2007-12-30
hmm..
```
sudo find /dev/* -name video* -print
```
Is there any video-device there?

Allrigt! Nice that it worked with a reboot!
Make a lsusb and tell me what your webcam's serialnumber is?
```
lsusb | grep ricoh
```
 if you got a Sony Vaio

---

### Post by OrionFyre on 2007-12-30
```
Bus 006 Device 002: ID 05ca:1839 Ricoh Co., Ltd
```

---

### Post by murmel on 2007-12-30
I do also get that error message. But try right-clicking on the picture of yourself and maybe you'll be able to correct the colours there..

---

### Post by OrionFyre on 2007-12-30
Well thats odd... when I try to grab the slider bars and move them, they only go one direction, to the right. And moving them only turns the very left of the screen red instead of green.

I did go through the whole make, make install, WHOLE process twice... might that have something to do with it? I wouldn't think so because it would all go to the same names right? Other programs that use the webcam don't access it properly.

For example on a website that uses flash the webcam activity light blinks on for a second, then blips dark for a split second then repeats.

when I try using 'webcam' it blinks the light on and off.

---

### Post by murmel on 2007-12-30
I haven't found anything else than xawtv and aMSN that works with it yet. But I'm looking for it right now!
Try "sudo make uninstall" and then "sudo make install"

---

### Post by OrionFyre on 2007-12-30
:) like the song "always look on the bright side of life"
it looks like I have a night vision camera! lol

---

### Post by murmel on 2007-12-30
Hehe, are you sure that you've done like the howto says?
Try it with aMSN and/or Skype (beta, new link in the howto!)

---

### Post by murmel on 2007-12-30
It works good with the program "cheese" (sudo apt-get install cheese)!! =)

---

### Post by OrionFyre on 2007-12-30
:guitar:
well now isn't that strange! Suddenly i have color other than "night vision" mode LOL.

Murmel, you are indeed a god to me, my shrine to buddha, maitreya and the infinite bodhisattvas will be replaced with a single letter sized sheet in landscape with Times font at 128 pt with a simple name "murmel" :)

For generations my family shall sing praise to your name! (wow, ok got a little klingon there)

but i am still at a loss as to why flash will only display the black screen and the security light on the cam blinks rapidly...

---

### Post by murmel on 2007-12-31
Hehe, that's sweet! Assalam Alaikum, or that's arabic. But sound cool! =)
Do you mean flash like in flashplayer? And that's it black when you're trying to run it ie. with youtubes videouploader?
I haven't gotten it working yet, but I'll try and when I do I'll post a way of getting it working.

For now, the programs that I've found working with this configuration is xawtv, cheese, aMSN and the latest Skype Beta.

:guitar:

---

### Post by OrionFyre on 2007-12-31
Well on some websites that use flash to upload your video stream for others to view it displays only a black screen, and the activity light on the camera blinks extremely fast. Like flash isn't getting the camera initialized. Anywyas I think I'm content for now that most of everything is working!

---

### Post by murmel on 2007-12-31
Hehe, yeah! Maybe there's something wrong with you flashplayer... ? I don't really get what the problem is... But I can't get the video upload at youtube working. Maybe it's the same problem?

---

### Post by murmel on 2008-01-01
Motion now works to!
```
sudo apt-get install motion
```
Edit target_dir in /etc/motion/motion.conf
```
sudo nano /etc/motion/motion.conf
```
```
[...]
target_dir /your/dir
[...]
```
Now chmod 777 /your/dir
```
sudo chmod 777 /your/dir
```
then run ```
motion
```
and it takes pictures of everything that moves! =D

---

### Post by junkMonkey on 2008-01-01
This also works for the VGN-CR220E!

---

### Post by murmel on 2008-01-01
> **junkMonkey said:**
> This also works for the VGN-CR220E!
Did everything in this guide work with CR220E ? =)

---

### Post by mic_la on 2008-01-01
Thanks for the sound tip. It made it work on my   sony vayo VGN-CR290EAN. Here are the details of my experience as there is one step slightly different:
Ububtu 7.10 Gutsy Gibbon
1) Edit /etc/modprobe.d/alsa-base (sudo nano /etc/modprobe.d/alsa-base) and add this in the bottom of it
options snd-hda-intel model=vaio
(I commented out the last line saying:options snd-cmipci mpu_port=0x330 fm_port=0x388)
then:
2) sudo apt-get install linux-backports-modules-$(uname -r)
then:
3) reboot

You wrote a fantastic post :)  
mic_la

---

### Post by murmel on 2008-01-02
> **mic_la said:**
> Thanks for the sound tip. It made it work on my   sony vayo VGN-CR290EAN. Here are the details of my experience as there is one step slightly different:
Ububtu 7.10 Gutsy Gibbon
1) Edit /etc/modprobe.d/alsa-base (sudo nano /etc/modprobe.d/alsa-base) and add this in the bottom of it
options snd-hda-intel model=vaio
(I commented out the last line saying:options snd-cmipci mpu_port=0x330 fm_port=0x388)
then:
2) sudo apt-get install linux-backports-modules-$(uname -r)
then:
3) reboot

You wrote a fantastic post :)  
mic_la
Hehe, thank you very much! I just gatherd stuff that I've found. Not I but the community itself who should get the credits! I'm just a simple messenger ;)

RIDE ON! =)

---

### Post by mauriciohf1 on 2008-01-02
murmel thanks the solution you wrote for the webcam also work fine in my VGN-CR120E. then i install skype 1.4 because i don t want to use the beta version. I note that the integrate microfone is not working,  when i plug a microphone it s work. i want to know if your integrate microfone works? and how you did? 

Mauricio H (COL) 

pos --> I read the blog of the webcam in spanish it only said that is for debian and no much more. You especification are better.

---

### Post by murmel on 2008-01-02
Hehe, I guess you know Spanish? :)

If you've installed as it says in this howto it should work. But I had to go into the Volumecontrol and add all the tracks under Edit -> Preferences
There I have: Full volume on everyone at Playback but muted ATAPI Mic, at Recording have I full volume on all of them and at Options I have "Front Mic" as Input Source 1, "Mic" as Input Source 2, and "CD" as Input Source 3. Maybe this will help you? Maybe you have selected wrong "Sound In" in Skype? 
Try it out!

- Simon

---

### Post by angelo costa on 2008-01-02
Hi, i'm running Feisty x64 and i'm getting this error:

angelo@machina:~/r5u870-VCC6$ sudo modprobe r5u870
FATAL: Error inserting r5u870 (/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/r5u870.ko): Invalid module format

could someone help me?

---

### Post by murmel on 2008-01-02
> **angelo costa said:**
> Hi, i'm running Feisty x64 and i'm getting this error:

angelo@machina:~/r5u870-VCC6$ sudo modprobe r5u870
FATAL: Error inserting r5u870 (/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/r5u870.ko): Invalid module format

could someone help me?
That's maybe because you're using x64? I don't know if this will work with x64. But I'll se if I can find drivers that'll work.

---

### Post by angelo costa on 2008-01-02
Thanks

---

### Post by angelo costa on 2008-01-02
Did anyone get the Fn keys working?

The brightness applet is working fine and volume, mute, display off were working out of the box but Fn not.

isn't working:
Fn+F5
Fn+F6
Fn+F7
Fn+F10
Fn+F12

---

### Post by OrionFyre on 2008-01-02
HAH! now I know it's got to be something software. Motion doesn't work! alrighty.

Been planning on wiping everything and started completely over. now that I have all the configuring down pat.

---

### Post by murmel on 2008-01-03
> **angelo costa said:**
> Did anyone get the Fn keys working?

The brightness applet is working fine and volume, mute, display off were working out of the box but Fn not.

isn't working:
Fn+F5
Fn+F6
Fn+F7
Fn+F10
Fn+F12

I haven't got it working yet. If someone finds a way, please post it! =)

> **OrionFyre said:**
> HAH! now I know it's got to be something software. Motion doesn't work! alrighty.

Been planning on wiping everything and started completely over. now that I have all the configuring down pat.

You have yo change the premissions of target_dir (you'll find it in /etc/motion/motion.conf).
That's how I got it working..

---

### Post by derick on 2008-01-03
Just wanted to add another thanks.  Fixed both the issues I was having with my volume controls only affecting the headphones out (which also produced no sound in any case) and also fixed my web-cam. :)

---

### Post by murmel on 2008-01-03
> **derick said:**
> Just wanted to add another thanks.  Fixed both the issues I was having with my volume controls only affecting the headphones out (which also produced no sound in any case) and also fixed my web-cam. :)
I'm glad you got it working!

---

### Post by mauriciohf1 on 2008-01-03
Angelo i am running Ubuntu Gutsy (64 bits) and everything is working. murmel try 64bits version is more fast than 32 bits and it work perfectly on Intel centrino duo.

Mauricio H (COL)

---

### Post by angelo costa on 2008-01-03
It's working now!

I removed all files and started again configuring and it's working.

Obrigado mauriciohf1.

---

### Post by murmel on 2008-01-03
> **angelo costa said:**
> It's working now!

I removed all files and started again configuring and it's working.

Obrigado mauriciohf1.
Sweet! That's good to know!
I hope it's working allright for you!

---

### Post by mauriciohf1 on 2008-01-04
Now the microphone problems are solve. it was easy only in the terminal i put alsamixer and in the first -Input So- i changed to "front mi" and -ATAPI MI- i changed to mute pressing m or pressing the cursor down and everything solve. Now i can say that my ubuntu is working perfectly thanks to everybody who participate in this forum especially to murmel. Gracias

Mauricio H (COL)

this is my lspci 

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
08:07.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:07.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:07.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

and lsusb

Bus 006 Device 002: ID 05ca:1839 Ricoh Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0000:0000
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000

---

### Post by murmel on 2008-01-04
> **mauriciohf1 said:**
> Now the microphone problems are solve. it was easy only in the terminal i put alsamixer and in the first -Input So- i changed to "front mi" and -ATAPI MI- i changed to mute pressing m or pressing the cursor down and everything solve. Now i can say that my ubuntu is working perfectly thanks to everybody who participate in this forum especially to murmel. Gracias

Mauricio H (COL)

this is my lspci 

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
08:07.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:07.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:07.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

and lsusb

Bus 006 Device 002: ID 05ca:1839 Ricoh Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 0000:0000
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000
Hehe, sweet! But is your FN-keys and suspension mode working? (When close the lid?)

---

### Post by junkMonkey on 2008-01-04
> **murmel said:**
> Did everything in this guide work with CR220E ? =)

Most of everything worked. I didn't have a problem with Gnome starting up or with my video card so I didn't play with that set of instructions. 

However, the Sound and WebCam instructions (which were what I was having trouble with) worked perfectly! Good Job!

Thanks again!

---

### Post by murmel on 2008-01-04
> **junkMonkey said:**
> Most of everything worked. I didn't have a problem with Gnome starting up or with my video card so I didn't play with that set of instructions. 

However, the Sound and WebCam instructions (which were what I was having trouble with) worked perfectly! Good Job!

Thanks again!
That's great!

---

### Post by ademel on 2008-01-04
Thanks for all your help! Now my sound and video on the VAIO is working fine, but I still seem to have a problem with compiz...

It tells me "desktop effects could not be enabled." 

When I type compiz in the terminal, it gives me this: 

Checking for Xgl: present.
Checking for nVidia: not present.
Checking for Xgl: present.
Enabling Sgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Familed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display: 1.0

Unfortunately I am a linux newbie so I have no idea what to do here. Any ideas? Your help is greatly appreciated.

---

### Post by murmel on 2008-01-04
> **ademel said:**
> Thanks for all your help! Now my sound and video on the VAIO is working fine, but I still seem to have a problem with compiz...

It tells me "desktop effects could not be enabled." 

When I type compiz in the terminal, it gives me this: 

Checking for Xgl: present.
Checking for nVidia: not present.
Checking for Xgl: present.
Enabling Sgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Familed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display: 1.0

Unfortunately I am a linux newbie so I have no idea what to do here. Any ideas? Your help is greatly appreciated.
Weird,, have you enabled your video card in the restricted manager?
Have you edited xorg.conf and enabled compiz?

---

### Post by ademel on 2008-01-04
Wow, fast reply! Murmel, you're amazing!

As to your question, I followed your directions for enabling compiz. My xorg.cfg file contains:

Section "Extensions"
Option "Composite" "Enable"
EndSection


When I click on the restricted drivers manager, it says "Your hardware does not need restricted drivers." :confused:
 
Edited to add: as far as the xorg.conf file, I have no idea how to enable compiz within it. How do I do that?

---

### Post by ademel on 2008-01-04
Hmm well I looked this up and it seems the reason compiz isn't working is because the hardware is blacklisted: 

the graphics card is:

VGA Compatible Controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
PCI ID: 8086:2a02

Supposedly you can tell compiz to skip checks in terminal but then video will be messed up sometimes. 

Do you have a different graphics card (which would be strange, since we have the same laptop) or have you found a different way around this problem?

---

### Post by puhchi on 2008-01-04
Hi everybody, I have a little question . How you make your mic to work???
This is the only problem that I have. Thanks in advance guys. Ubuntu rox :guitar:

---

### Post by murmel on 2008-01-04
> **puhchi said:**
> Hi everybody, I have a little question . How you make your mic to work???
This is the only problem that I have. Thanks in advance guys. Ubuntu rox :guitar:
I wrote it somewhere in this thread how I got i working. It's just unmuting and volume setup in the volume control. =)

---

### Post by murmel on 2008-01-20
I've now added how to install the graphic driver manually (to get the latest!).
This method only worked for me when re-installing ubuntu. Didn't get it to work when I've already used the first method.. Use this method only if you know how to get it working or if you're doing it on a clean install! =)

- Simon

---

### Post by pwn on 2008-01-28
The webcam now works for Sony Vaio AR590E. 

I did get the following error with xawtv, and not sure what's wrong exactly.
```

wotanist@Renderman:~$ xawtv -c /dev/video0 -geometry 320x240
[: 12: (opcode:: unexpected operator
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-generic)
xinerama 0: 1920x1200+0+0
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  67
  Current serial number in output stream:  67

```

It works well in Cheese. Though I don't use the webcam, I'm glad I got one more device working on the my Vaio. Thanks for the great guide. Couldn't have done it by myself

---

### Post by murmel on 2008-01-28
Hehe, thanks! I'm always gald that it helped someone else than myself!

---

### Post by clovis_ll on 2008-02-06
thanks! i got my sony cr320 singing again. now if i could only make it see (webcam)

back to terminal for me!!!! yey!!

:D

---

### Post by clovis_ll on 2008-02-06
i keep getting this errors.

clovis2@clovis2-utop:~/Documents/r5u870-VCC6$ sudo modprobe videodev
WARNING: /etc/modprobe.d/alsa-base.save.1 line 40: ignoring bad line starting with 'sudo'
clovis2@clovis2-utop:~/Documents/r5u870-VCC6$ sudo modprobe video-buf
WARNING: /etc/modprobe.d/alsa-base.save.1 line 40: ignoring bad line starting with 'sudo'

is this right?

---

### Post by clovis_ll on 2008-02-06
anyone???

---

### Post by murmel on 2008-02-06
I haven't seen that error message before. But try to reboot? Maybe redo the webcam part. Check if sudo is install (don't know why it shouldn't). Login with root and try to modprobe them.

---

### Post by clovis_ll on 2008-02-06
it still gives me the error.

on the install part, what is [/i] ?

heres what i did

i downloaded the file on my tmp flder
i did **tar xf r5u870-0.20.tar.bz2**

then
**cd r5u870-VCC6  ( i did not put the slash after it because it gives me error)**
[B]sudo make
sudo make install[/B]

i start to get problems on
[B]
sudo modprobe videodev[/B]

if i did the rest, same errors comes up.

i tried the root option as well and same errors..

---

### Post by s0n|k on 2008-02-09
If i shut the lid or put the laptop into standby, the wireless/battery/power lights remain lit. It doesn't do that with Vista... How can I make it fully go into standby? Also, when I raise the lid I usually have to POR the machine. It rarely comes back from being in standby. Anyone else have these problems? I have a CR320E. 


P.S. Thanks for the tips above. That was a lot easier than adding support in the kernel.

---

### Post by erikringmar on 2008-02-13
HIya,

I have just bought a Vaio CR series computer (VGN-CR490EBN) but I can't install Ubuntu on it.  The problem seems to be with Xorg which isn't loading right.  You seem to have solved this problem, but how do you get internet access before you have a working install?  I can't apt-get into anything.  Is commenting the CR/ROM somehow the answer to the connectivity problem?

grateful for any help!

yours,

Erik

---

### Post by erikringmar on 2008-02-13
HIya,

I have just bought a Vaio CR series computer (VGN-CR490EBN) but I can't install Ubuntu on it.  The problem seems to be with Xorg which isn't loading right.  You seem to have solved this problem, but how do you get internet access before you have a working install?  I can't apt-get into anything.  Is commenting the CR/ROM somehow the answer to the connectivity problem?

grateful for any help!

yours,

Erik

---

### Post by murmel on 2008-02-14
Download the alternative cd and use it! =)

---

### Post by erikringmar on 2008-02-21
Hi there Mr Murmel,

My mistake was that I didn't realize I actually had internet access from the command line.  I followed your instructions and they worked great.  I cannot thank you enough.  Well, let me try: thanks, thanks, thanks, thanks (they are now counting thanks on this forum, right?)

yours,

Erik

---

### Post by murmel on 2008-02-21
Hehe, thre's always a pleasure to help!

---

### Post by w3me on 2008-02-23
Thanks, the sound is working now... I have a VGN-CR150F.. the camera still doesn't work, and also the brightness is not working...

---

### Post by w3me on 2008-02-24
I got a VGN-CR150f.. the sound works now, thanx... But the Visual effects dont work... 

I modified xorg.conf and added 

Section "Extensions"
Option "Composite" "Enable"
EndSection

and installed xserver-xgl

but didnt work..

and also the brigthness is not working

---

### Post by w3me on 2008-02-24
The camera is working now.. thank you so much...
. :guitar:

---

### Post by murmel on 2008-02-25
Hehe, sweet! NP!

---

### Post by w3me on 2008-02-25
> **ademel said:**
> Thanks for all your help! Now my sound and video on the VAIO is working fine, but I still seem to have a problem with compiz...

It tells me "desktop effects could not be enabled." 

When I type compiz in the terminal, it gives me this: 

Checking for Xgl: present.
Checking for nVidia: not present.
Checking for Xgl: present.
Enabling Sgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Familed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display: 1.0

Unfortunately I am a linux newbie so I have no idea what to do here. Any ideas? Your help is greatly appreciated.

I have the same problem, if somebody solved it, please post it.

---

### Post by andy6363 on 2008-02-26
I'm also trying to get my webcam to work.  I'm not having any success, looking through the forums.


I have a Sony Viao VGN-CR123E.  Any help would be appreciated.
Let me know if you need any more information about my computer.

---

### Post by mixandgo on 2008-02-27
I have the sony vaio vgn-cr220e and my webcam works with the ricoh driver 

you can find it here :

[http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870)

hope that helps

---

### Post by andy6363 on 2008-02-28
Hmm... 

I get the downloading part, entering svn *** into the terminal, but when I try to continue to the installing section where you 'make', I get errors, saying that no targets are specified.

I feel that I am a newbie, oh wait, I am a newbie at Gutsy.  haha..  
Well, in the end, my webcam is still not working.  In Skype beta at the video webcam test, the led turns on but the image remains black.
I'm thinking I've tried so many installations that I might have confused the computer?  Is there a way to uninstall?  

Thanks for you help.  It's deeply appreciated.

---

### Post by N0_Named_Guy on 2008-03-04
Hello people...

I have a Sony Vaio CR-11S... The white one... All works fine... Sound, Video, Compiz, Bluetooth and Wireless...

What wasn't working from the begining were the Sound and the Compiz...

I've followed step by step the instructions in this post to put my webcam to work... It installed, reconized the /dev/video0 but when I run xawtv, it goes away, as well when I run cheese... It says that there was a BadAlloc error...

I've installed motion too... It is weird... When I run motion, the light before the camera turns on, and when I move it says it saves JPEG images... It does in fact...

But why the hell the xawtv and cheese doesn't work??

---

### Post by polydenece on 2008-04-09
I have a CR123/B and i installed cheese yesterday and it worked fine however it started giving badalloc errors after i enabled compiz. now i changed my compiz settings back and cheese cannot detect my webcam. what should i do?

---

### Post by Si_442 on 2008-07-17
I'm trying to get the webcam driver installed onto my Sony Vaio CR21Z-R laptop but having little success, following the steps I get to 'sudo make' but get the following error. Does anybody know how to get around this?

si@Laptop:~/Desktop/r5u870-VCC6$ sudo make

make -C /lib/modules/2.6.24-19-generic/build M=/home/si/Desktop/r5u870-VCC6 V=0 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/si/Desktop/r5u870-VCC6/r5u870_md.o
In file included from /home/si/Desktop/r5u870-VCC6/r5u870_md.c:55:
/home/si/Desktop/r5u870-VCC6/usbcam.h:36:29: error: media/video-buf.h: No such file or directory
make[2]: *** [/home/si/Desktop/r5u870-VCC6/r5u870_md.o] Error 1
make[1]: *** [_module_/home/si/Desktop/r5u870-VCC6] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [all] Error 2

---

