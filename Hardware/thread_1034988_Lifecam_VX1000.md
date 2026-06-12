---
title: "Lifecam VX1000"
date: 2009-01-09
forum: Hardware
---

### Post by tbj61898 on 2009-01-09
Hello, 
I'm a new UBUNTU 32bit user. Here are some HW details:
ASUS M2V, ATHLON/Opteron 64X2, NVIDIA 7300LE, MS Lifecam VX1000, Trust USB Card (my MoBo has usb port but there was a time I needed some more), Firewire card VT6306.

Speaking about MS Lifecam VX1000  ID: 045e:00f7

I was loosing any hopes then I looked at [http://moinejf.free.fr/webcam.html](http://moinejf.free.fr/webcam.html) and it reports my cam as WORKING. But no /dev/video#? showed in my system, but green led on the camera was ON.

So I had a look in the system and find out these modules loaded:
- snd_usb_audio - which sounds good because this cam have a mic
- sn9c102 - which didn't seem good because the official driver is gspca_sonixj

I activated v4l debug by:
echo 0x0f >/sys/module/gspca_main/parameters/debug

and here's what I read in dmesg:
sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.47pre49
usb 1-1: SN9C105 PC Camera Controller detected (vid:pid 0x045E:0x00F7)
usb 1-1: No supported image sensor detected for this bridge

No good. because official information say it must be sonixj driver.

So I went to /etc/modprobe.d/ and wrote to blacklist-custom (which was empty):
blacklist sn9c102

Then reboot. Webcam green led OFF. After reboot there was no gspca_ module loaded, just snd_usb_audio and lib, indeed echoing 0x0f for debug v4l wasn't working.

So here's what I did:
# modprobe gspca_sonixj

And dmesg told me:
[  192.400418] Linux video capture interface: v2.00
[  192.415421] gspca: main v2.2.0 registered
[  192.421073] usbcore: registered new interface driver sonixj
[  192.423098] sonixj: registered

still no "video" in /dev. So I set debug in gspca_main and plug/unplug my webcam. I also try to plug it in in my Trust pci usb card. No result. It didn't show in lsusb anymore.

So I:
# modprobe sn9c102

dmesg:
[  448.069317] sn9c102: V4L2 driver for SN9C1xx PC Camera Controllers v1:1.47pre49
[  448.071515] usbcore: registered new interface driver sn9c102

no sensor error? seems good! But still no /dev/video#?

I don't know if it makes any sense but, I went vi /etc/modules and added:
gspca_sonixj 

reboot. No /dev/video, no new messages in dmesg.

vi /etc/modprobe.d/blacklist-custom and removed "blacklist sn9c102". 

reboot. and again dmesg 
[   12.787432] usb 2-2: No supported image sensor detected for this bridge

lsmod showed:
usbcore               148848  10 gspca_sonixj,gspca_main,snd_usb_audio,snd_usb_lib,zd1211rw,btusb,sn9c102,ehci_hcd,uhci_hcd

But still no luck with /dev/video#?

According to uname -a:
Linux myhostname 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Lnux

I *should* have latest version of modules, with support for my webcam... but I can't get it to work.

Yeeees I know I can buy another one as cheap as a pizza, but here I'd like to know what's wrong with my system.

Any help/idea appreciated and thanks for taking your time to read until the end!

Andrè

:confused:

---

### Post by tbj61898 on 2009-01-11
I managed to get the Lifecam VX-1000 working and I want to share with you what I did (maybe there was a shorter way to this!).

If you are only interested in the solution please descriptions skip below.

Base: freshly new installed UBUNTU 8.10

After going thru what You can read on the first post of this thread I decided to send a mail to the maintainer (and very nice person) of [http://moinejf.free.fr](http://moinejf.free.fr)

He told me two important things:
- if there is sn9c102 driver is compiled, only this handles the webcam
- to read a bit better his [README]("http://moinejf.free.fr/gspca_README.txt") file

:-)

So I managed to search a bit about [sn9c102]("http://www.linux-projects.org/downloads/FAQ.html") and it appears to be a closed-source driver. 

So I got back to LinuxTV and downloaded the latest drivers, as suggested by Mr. Moine.

[COLOR="Red"]SOLUTION[/COLOR]

I opened a shell as root on my system and:
# wget [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.gz](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.gz)
# tar zxvf tip.tar.gz
# cd v4l... (whatever the newly created directory name is)
# make all
# make install

then I edited /etc/modprobe.d/blacklist-custom and added:
blacklist sn9c102

# reboot

After reboot /dev/video0 is OK

So I started camorama but it still can't find /dev/video0 so I did a "ls -la /dev/video0" to find out it's own root and group video permission set. 

so I did:
# usermod -a -G video myUserName

But still no luck from camorama. Back to Mr. Moine webpage I discovered he wrote a little utility to just test the drivers, SVV. next steps:
# wget [http://moinejf.free.fr/svv.c](http://moinejf.free.fr/svv.c)
To compile it, just look at first lines of the C code, in my case I was supposed to execute:
# gcc -Wall svv.c -o svv $(pkg-config gtk+-2.0 --cflags --libs) -lv4lconvert

Still no luck. ld complains missing gtk/gtk.h, not found!

So I:
# apt-get install libgtk2.0-dev

Later svv compilation couldn't find lv4lconvert! So I started synaptic, search for libv4l and set these options:
install libv4l-dev
reinstall libv4l

This time svv compilation went OK and I could correctly see my room via webcam.

Camorama still refused to work but this time I went straight to cheese, which seems to be good. 
# apt-get install cheese

Et voilà, everything worked!

notice: You may not need all these steps to get your lifecam to work, remember I'm a noob like You so, if in doubts, just ask some veteran!

Ciao,
Andrè :popcorn:

---

### Post by leachyboy2001 on 2009-01-20
Thanks Andre!
This got my Lifecam 1000 working too.
And you are right there is an easier way with out all the steps.

I compiled the drivers you mention here adding sudo to the make install line and also made the changes to the blacklist-custom file:

> I opened a shell as root on my system and:
# wget [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.gz](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.gz)
# tar zxvf tip.tar.gz
# cd v4l... (whatever the newly created directory name is)
# make all
# sudo make install

then I edited /etc/modprobe.d/blacklist-custom and added:
blacklist sn9c102

# reboot
Then after rebooting 
open a shell and type ```
sudo gstreamer-properties
```
Go to the video tab, and select in the Input device section, plugin: v4l2 and device: USB Camera

Working perfectly in Ekiga 2.0.12 and Cheese with todays update 2.24.2

---

### Post by mr_raider on 2009-01-25
Thanks for the tips. It now works with Cheese. I can't get it to work with skype however. Any thoughts?

---

### Post by tbj61898 on 2009-01-25
> **mr_raider said:**
> Thanks for the tips. It now works with Cheese. I can't get it to work with skype however. Any thoughts?

We may need some details here... did you select video device under skype options? which skype version are you using? any error message?

---

### Post by mr_raider on 2009-01-25
I'm using Skype 2.0.0.72 with Ubuntu 8.10 AMD64.

Device in skype settings /dev/video0. When I click on test, I get static.

Camorama also gives an error message (unable to capture image) and closes.

---

### Post by stuarttaylor on 2009-02-01
Following Andre's instructions, my camera started working (Thanks Andre!)

But I have also been having the same problems as mr_raider, as Camorama and Skype are still having problems.

When running Skype from the terminal, the following (unhelpful?) messages appear during the camera test, with the device was set as /dev/video0

```
Starting the process...
Skype Xv: Xv ports available: 64
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 355
```

Camorama will crash out and close, but Skype (2.0.0.72) shows a similar screen (Static) to the test screen that shows when running gstreamer-properties with the video input set to v4l (not v4l2).

I'm very much a newbie when it comes to playing with device drivers and so on, but I'm guessing that both Skype and Camorama are still trying to use the original v4l library as standard.

Has anyone had any luck with the microphone for this camera?

---

### Post by tbj61898 on 2009-02-01
Just as MrRaider you both seem to have issues with Skype but I'm not able to be of help here... 

Anyway lifecam microphone ain't working for me, also.

---

### Post by msright1981 on 2009-02-01
Hi,

Any one got it to work with skype yet? My friend seems to have the same exact problem with skype. Any help will be appreciate it. Please help so I can get some free pizza tonite :).

---

### Post by Meghnaad on 2009-02-07
Thank you !

My LifeCam VX-1000 is working perfectly (ubuntu 8.10)

Will check it on skype and Update the Status !

---

### Post by yauipop on 2009-02-20
Same problem with skype here. Any suggestions?

Thanks in advance!

---

### Post by rbolio on 2009-02-23
do you all use 8.10? damn... i was about to go buy that webcam...any recomendations anyone?

---

### Post by gezus on 2009-02-28
Nicely done.  This also worked for my Fedora 10 install.

However my camera when it's turned on is quite pink it seems.

---

### Post by Cauda_Draconis on 2009-03-01
I tried Andre's instructions, but "make all" causes errors. 
```
 $ make all
make -C /home/vicky/v4l-dvb-c770b20d15c6/v4l all
make[1]: Entering directory `/home/vicky/v4l-dvb-c770b20d15c6/v4l'
No version yet, using 2.6.28-8-generic
make[1]: Leaving directory `/home/vicky/v4l-dvb-c770b20d15c6/v4l'
make[1]: Entering directory `/home/vicky/v4l-dvb-c770b20d15c6/v4l'
scripts/make_makefile.pl
Updating/Creating .config
Preparing to compile for kernel version 2.6.28
File not found: /lib/modules/2.6.28-8-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: Leaving directory `/home/vicky/v4l-dvb-c770b20d15c6/v4l'
make[1]: Entering directory `/home/vicky/v4l-dvb-c770b20d15c6/v4l'
Updating/Creating .config
Preparing to compile for kernel version 2.6.28
File not found: /lib/modules/2.6.28-8-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
make[1]: Leaving directory `/home/vicky/v4l-dvb-c770b20d15c6/v4l'
make: *** [all] Error 2
```
It doesn't seem to be able to find the build/.config file for my kernel (2.6.28-8-generic). 

Anyone know what to do?

---

### Post by ddastoor on 2009-03-09
Hi I followed the instructions above and managed to get the video working for Skype (Ubuntu 8.10 Intrepid)
System: Dell Inspiron 6400 Lapton for the MS LifeCam vx1000 webcam.

However the sound is not working.
Any ideas ?

---

### Post by louislmao on 2009-03-21
hi i followed everything but im stuck at the part where i have to put the diectory

im a total noob and have no idea how to do that

help please!!!!

---

### Post by bturig on 2009-03-29
Followed leachyboy2001 post #3 steps. On Ubuntu 8.10 on Dell Inspiron E1405. Can confirm Cheese and Skype video work. But no audio (microphone) yet.

---

### Post by biker3 on 2009-03-31
Me in a kernel 2.6.26-1-amd64, and after to post #3 steps, I can use it in aMSN and cheese, but in Skype I only can see a green square with a lot of lines, so when we try to tune a TV channel:confused:

---

### Post by kenn e on 2009-04-01
My vx-1000 continues to remain dark :(  please help.

dmesg:
[PHP][    0.000000] Linux version 2.6.27-14-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) ) #1 SMP Fri Mar 13 18:00:20 UTC 2009 (Ubuntu 2.6.27-14.30-generic)
[    0.000000] BIOS-provided physical RAM map:
[/PHP]
...
[PHP][    2.008879] USB Universal Host Controller Interface driver v3.0
[    2.020674] [COLOR="Red"]Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after[/COLOR]
[[/PHP]
... I'm thinking this might be the problem, but don't know how to change it. I'm coming from a FreeBSD background, so i'm a linux noob, but not completely stunned.

[PHP][   12.682085] Linux video capture interface: v2.00
[   12.702183] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
[   12.702343] iTCO_wdt: Found a ICH9DH TCO device (Version=2, TCOBASE=0x0460)
[   12.702423] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   12.744764] usbcore: registered new interface driver snd-usb-audio
[   12.774743] saa7130/34: v4l2 driver version 0.2.14 loaded
[   12.774904] saa7134 0000:06:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   12.774910] saa7133[0]: found at 0000:06:01.0, rev: 209, irq: 22, latency: 32, mmio: 0x90004800
[   12.774915] saa7133[0]: subsystem: 1461:f11d, board: UNKNOWN/GENERIC [card=0,autodetected]
[   12.774926] saa7133[0]: board init: gpio is 40000
[   12.924874] saa7133[0]: i2c eeprom 00: 61 14 1d f1 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   12.924884] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[   12.924893] saa7133[0]: i2c eeprom 20: 01 40 01 32 32 01 01 43 88 ff 00 56 ff ff ff ff
[   12.924901] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.924910] saa7133[0]: i2c eeprom 40: ff 22 00 c0 96 ff 03 30 15 00 ff ff ff ff ff ff
[   12.924919] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.924927] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.924936] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.924945] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.924953] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.924962] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.924971] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.924979] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.924988] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.924997] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.925005] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.925384] saa7133[0]: registered device video0 [v4l2]
[   12.925414] saa7133[0]: registered device vbi0
[   12.939295] saa7134 ALSA driver for DMA sound loaded
[   12.939319] saa7133[0]/alsa: saa7133[0] at 0x90004800 irq 22 registered as card -2[/PHP]

if i remove and reconnect my cam, i get this. Seems something is missing - the driver v4l2 attaching to the camera.

[PHP][  827.062476] usb 4-1.1: USB disconnect, address 5
[  830.888617] usb 4-1.6: new full speed USB device using ehci_hcd and address 6
[  830.981862] usb 4-1.6: configuration #1 chosen from 1 choice
[/PHP]

Can anyone help, do you need more info?
this is a core2duo intel system, about 1 year old. Hoping to get both cam and mic working, neither are.

---

### Post by Genetherapy on 2009-04-01
Thank you so much guys!
Have been following dead-end threads for the last few hours trying to get my drivers working until I found this.  Works great now!

---

### Post by dieviou on 2009-04-10
Wish I'll soon join the successfull lifecam-users too...
(I'm a beginner on ubuntu and with terminal codes)
The device is recognised, but I get no image:

root@gideon-desktop:~# lsusb
Bus 005 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 004: ID 045e:00f7 Microsoft Corp. LifeCam VX-1000.
Bus 004 Device 002: ID 046d:c30e Logitech, Inc. UltraX Keys (X)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 03f0:4d11 Hewlett-Packard PSC 1400
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Thanks

---

### Post by stanca on 2009-04-26
I always managed to make my webcam working using the driver from here [http://linuxtv.org/hg/~jfrancois/gspca/](http://linuxtv.org/hg/~jfrancois/gspca/) .Take the bz2 file from above.
Just extract it,open the new directory,open in terminal and:
make
sudo make install
Then reboot and that's all,how simple can it be now but I was looking for this for over 2 months.
It works fine with cheese.
With this driver even my kworld plus tv analog usb stick tuner is working with tvtime,but not in the same time with the webcam,this is a wellknown issue.:popcorn:

---

### Post by october1917 on 2009-05-02
stanca you said that you managed to make your webcam to work. You mean work with Skype too?

---

### Post by stanca on 2009-05-02
I didn't try,I don't use it.

---

### Post by jelofson on 2009-05-03
I did the driver install via the instructions above for my lifecam vx-1000 and it now detects the camera, but all I get is a green screen. No actual image.

It's too bad this is such a problem. I have a logitech that works fine. Out of the box. I know it's tough when none of the hardware manufacturers design things for linux.

I just bought this camera, but I am going to take it back and get a logitech similar to my other one. I believe it uses a different driver.


Oh well.

---

### Post by daniel311 on 2009-05-16
> **jelofson said:**
> I did the driver install via the instructions above for my lifecam vx-1000 and it now detects the camera, but all I get is a green screen. No actual image.
...

Oh well.

I've got exactly the same problem, here in my fresh jaunty installation + new gpca drivers.

---

### Post by osterchrisi on 2009-05-21
Hi, 

when I download the spca5xx driver, extract and go to the terminal, then type 'make' I get the following code:

```
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/chrisi/Desktop/gspcav1-20071224 CC=cc modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/chrisi/Desktop/gspcav1-20071224/gspca_core.o
/home/chrisi/Desktop/gspcav1-20071224/gspca_core.c:54:27: Fehler: asm/semaphore.h: No such file or directory
/home/chrisi/Desktop/gspcav1-20071224/gspca_core.c: In Funktion »spca5xx_ioctl«:
/home/chrisi/Desktop/gspcav1-20071224/gspca_core.c:2463: Fehler: Implizite Deklaration der Funktion »video_usercopy«
/home/chrisi/Desktop/gspcav1-20071224/gspca_core.c: Auf höchster Ebene:
/home/chrisi/Desktop/gspcav1-20071224/gspca_core.c:2609: Fehler: unbekanntes Feld »owner« in Initialisierung angegeben
/home/chrisi/Desktop/gspcav1-20071224/gspca_core.c:2609: Warnung: Initialisierung von inkompatiblem Zeigertyp
/home/chrisi/Desktop/gspcav1-20071224/gspca_core.c:2611: Fehler: unbekanntes Feld »type« in Initialisierung angegeben
/home/chrisi/Desktop/gspcav1-20071224/gspca_core.c: In Funktion »spca50x_create_sysfs«:
/home/chrisi/Desktop/gspcav1-20071224/gspca_core.c:2769: Fehler: Implizite Deklaration der Funktion »video_device_create_file«
/home/chrisi/Desktop/gspcav1-20071224/gspca_core.c:2780: Fehler: Implizite Deklaration der Funktion »video_device_remove_file«
/home/chrisi/Desktop/gspcav1-20071224/gspca_core.c: In Funktion »spca5xx_probe«:
/home/chrisi/Desktop/gspcav1-20071224/gspca_core.c:4301: Fehler: inkompatible Typen in Zuweisung
make[2]: *** [/home/chrisi/Desktop/gspcav1-20071224/gspca_core.o] Fehler 1
make[1]: *** [_module_/home/chrisi/Desktop/gspcav1-20071224] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.28-11-generic'
make: *** [default] Fehler 2

```

Sorry, I know it's German, but maybe someone understands the lines anyway... 
I just updated to 9.04.

Would appreciate any help, thanks!

---

### Post by daniel311 on 2009-05-23
Hi osterchrisi,

you downloaded old files (2007)? Where did you download from? Try this one and run 'make' and 'make install' in the extracted folder.

-> [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.gz](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.gz)

---

### Post by osterchrisi on 2009-05-24
Oh, thanks for that. Now at least, I have a green screen :)

...

---

### Post by leachyboy2001 on 2009-05-27
I was able to fix with this see post:
[http://ubuntuforums.org/showthread.php?p=7355850#post7355850]("http://ubuntuforums.org/showthread.php?p=7355850#post7355850")

---

### Post by rbolio on 2009-05-28
got the green screen aswell.... how recomended is the "kernel update" mentioned in the other post?.....

---

### Post by osterchrisi on 2009-05-28
Worked for me!

---

### Post by mr_raider on 2009-05-31
Anyone got it working under 9.04?

---

### Post by zentrum on 2009-06-09
Hey!

I am using Debian with a 2.6.30 kernel. Video is working well with the VX-1000, but no sound. Modules are properly loaded (snd_usb_audio, snd_usb_lib). Mic is not muted (although, it was not possible to change the settings via kmix-kde4)

arecord -l tells: 

card 1: camera [USB camera], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

but it is not possible to record anything with arecord. After research this problem is common. Anyone, who got the mic working? 

Best regards!

---

### Post by zentrum on 2009-06-10
Okay, this was too hastily. I played around a bit with arecord. 

arecord -D hw:2 -f S16 test.wav gives:

arecord: pcm_read:1617: read error: Eingabe-Ausgabefehler

I hope this is not simply a syntax error, but maybe a bug in alsa
and snd_usb_audio or related module. Can somebody confirm this?

Maybe this helps, too:
cat /proc/asound/camera/stream0 gives:

USB camera at usb-0000:00:1d.0-1, full speed : USB Audio

Capture:
  Status: Stop
  Interface 2
    Altset 1
    Format: 0x2 (16 bits)
    Channels: 1
    Endpoint: 4 IN (NONE)
    Rates: 8000, 16000

---

### Post by mr_raider on 2009-06-27
HAs anyone gotten it to work in Jaunty under kernel 2.6.28? Or am I doomed to upgrade kernels?

---

### Post by Mdyter on 2009-07-31
[zentrum]("http://ubuntuforums.org/member.php?u=852271") , you found anything to solve the problem with the mic?

---

### Post by Cabel on 2009-08-01
I upgraded using check kernel from the other post:

[http://ubuntuforums.org/showthread.p...50#post7355850](http://ubuntuforums.org/showthread.p...50#post7355850)

and it now works with no additional fixes required other than the automatic kernel updates in check kernel.

Unfortunately although it works with cheese, unfortunately skype it still doesn't work with skype

I am running a lifecam VX-1000 on the 64bit version of 9.04

---

### Post by osterchrisi on 2009-08-01
I got it running with Kernel Check too.
I have Jaunty kernel 2.6.29.4-ultimate right now and Skype is also recognizing and working with the camera.

---

### Post by stanca on 2009-08-05
Since with the kernel 2.6.28-13 my webcam stoped working in any way no matter what I tried to do too,inclusively the usb tv tuner.:(:confused:

---

### Post by Nate Shoffner on 2009-08-05
I can't locate /etc/modprobe.d/blacklist-custom  for some reason.  All else went well, but the file does not exist.  I did the following:

			 				I opened a shell as root on my system and:
# wget [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.gz](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.gz)
# tar zxvf tip.tar.gz
# cd v4l... (whatever the newly created directory name is)
# make all
# sudo make install
# reboot 			 		

Like I said, I could not locate the blaicklist-custom file.  Is this why the camera still is not working?  When I start Cheese I get a a solid green picture.  Thank you.

---

### Post by sgilbert on 2009-08-07
Running Jaunty with Kernel 2.6.30.4.  Cam was working with cheese but not skype.  I tried steps on post #3 but i think that wasn't a good idea since I regressed now.  Green screen in cheese.

I'm tired of all that tweaking, I think I'll working on something more useful, dual-booting winXP.

---

### Post by jtuchscherer on 2009-08-30
I got the webcam working in skype and cheese on a fresh 64bit Jaunty install after installing the driver from here :

[http://linuxtv.org/hg/~jfrancois/gspca/](http://linuxtv.org/hg/~jfrancois/gspca/)

and then installing: 

[PHP]sudo apt-get install lib32v4l-0[/PHP]

and then using this as my Skype launcher:

[PHP]LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype[/PHP]

I need to use the lib32 folder because I am on a 64bit machine. If you are on a 32bit it might work for you to use this command:

[PHP]LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype[/PHP]

---

### Post by jesterthejedi on 2009-09-13
> **Cauda_Draconis said:**
> I tried Andre's instructions, but "make all" causes errors. 
```
 $ make all
make -C /home/vicky/v4l-dvb-c770b20d15c6/v4l all
make[1]: Entering directory `/home/vicky/v4l-dvb-c770b20d15c6/v4l'
No version yet, using 2.6.28-8-generic
make[1]: Leaving directory `/home/vicky/v4l-dvb-c770b20d15c6/v4l'
make[1]: Entering directory `/home/vicky/v4l-dvb-c770b20d15c6/v4l'
scripts/make_makefile.pl
Updating/Creating .config
Preparing to compile for kernel version 2.6.28
File not found: /lib/modules/2.6.28-8-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: Leaving directory `/home/vicky/v4l-dvb-c770b20d15c6/v4l'
make[1]: Entering directory `/home/vicky/v4l-dvb-c770b20d15c6/v4l'
Updating/Creating .config
Preparing to compile for kernel version 2.6.28
File not found: /lib/modules/2.6.28-8-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
make[1]: Leaving directory `/home/vicky/v4l-dvb-c770b20d15c6/v4l'
make: *** [all] Error 2
```
It doesn't seem to be able to find the build/.config file for my kernel (2.6.28-8-generic). 

Anyone know what to do?

make distclean
make clean
make menuconfig - remove un-needed stuff like tuners/audio, we need gspca
make
sudo make install
reboot and test cam.

---

### Post by stanca on 2009-10-07
Now you may need just this once:
```
sudo apt-get install subversion build-essential linux-headers-$(uname -r) && wget http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2 && tar xf tip.tar.bz2 && cd gspca-* && make && sudo make install && sudo depmod -ae $(uname -r)
``` ;)

---

### Post by jesterthejedi on 2009-10-12
> **stanca said:**
> Now you may need just this once:
```
sudo apt-get install subversion build-essential linux-headers-$(uname -r) && wget http://linuxtv.org/hg/~jfrancois/gspca/archive/tip.tar.bz2 && tar xf tip.tar.bz2 && cd gspca-* && make && sudo make install && sudo depmod -ae $(uname -r)
``` ;)

Fails on the tuner module:
/home/billy/gspca-111c1cbc759b/v4l/firedtv-1394.c:283: error: implicit declaration of function 'hpsb_unregister_protocol'
make[3]: *** [/home/billy/gspca-111c1cbc759b/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/billy/gspca-111c1cbc759b/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-13-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/billy/gspca-111c1cbc759b/v4l'
make: *** [all] Error 2

---

### Post by jaschenk on 2009-10-18
> **leachyboy2001 said:**
> Thanks Andre!
This got my Lifecam 1000 working too.
And you are right there is an easier way with out all the steps.

I compiled the drivers you mention here adding sudo to the make install line and also made the changes to the blacklist-custom file:


Then after rebooting 
open a shell and type ```
sudo gstreamer-properties
```Go to the video tab, and select in the Input device section, plugin: v4l2 and device: USB Camera

Working perfectly in Ekiga 2.0.12 and Cheese with todays update 2.24.2


This process works with Jaunty and a VX-3000 MS lifechat webcam as well.
cameramonitor does nto work, but cheese and other apps work fine no issues!

---

### Post by Ceyce on 2009-12-12
> **leachyboy2001 said:**
> Thanks Andre!
This got my Lifecam 1000 working too.
And you are right there is an easier way with out all the steps.

I compiled the drivers you mention here adding sudo to the make install line and also made the changes to the blacklist-custom file:


Then after rebooting 
open a shell and type ```
sudo gstreamer-properties
```Go to the video tab, and select in the Input device section, plugin: v4l2 and device: USB Camera

Working perfectly in Ekiga 2.0.12 and Cheese with todays update 2.24.2
Thanks, it worked for 9.04.
But in 9.10 I did the same steps, and it doesnt start work.
Someone have tips for ubuntu 9.10?

P.S.
Sorry for my bad English

---

### Post by leachyboy2001 on 2009-12-13
Since upgrading to 9.10 karmic I can't seem to compile any of these drivers.  Will post make output tomorrow...

>  CC [M]  /media/stuff/gspca-bdc9ee6ae5f2/v4l/dvb-usb-dvb.o
  CC [M]  /media/stuff/gspca-bdc9ee6ae5f2/v4l/dvb-usb-remote.o
  CC [M]  /media/stuff/gspca-bdc9ee6ae5f2/v4l/usb-urb.o
  CC [M]  /media/stuff/gspca-bdc9ee6ae5f2/v4l/pt1.o
  CC [M]  /media/stuff/gspca-bdc9ee6ae5f2/v4l/va1j5jf8007s.o
  CC [M]  /media/stuff/gspca-bdc9ee6ae5f2/v4l/va1j5jf8007t.o
  CC [M]  /media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-avc.o
  CC [M]  /media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-ci.o
  CC [M]  /media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-dvb.o
  CC [M]  /media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-fe.o
  CC [M]  /media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.o
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:21:17: error: dma.h: No such file or directory
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:22:21: error: csr1212.h: No such file or directory
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:23:23: error: highlevel.h: No such file or directory
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:24:19: error: hosts.h: No such file or directory
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:25:22: error: ieee1394.h: No such file or directory
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:26:17: error: iso.h: No such file or directory
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:27:21: error: nodemgr.h: No such file or directory
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:40: warning: 'struct hpsb_iso' declared inside parameter list
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:40: warning: its scope is only this definition or declaration, which is probably not what you want
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c: In function 'rawiso_activity_cb':
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:56: error: dereferencing pointer to incomplete type
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:57: error: implicit declaration of function 'hpsb_iso_n_ready'
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:64: error: dereferencing pointer to incomplete type
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:65: error: implicit declaration of function 'dma_region_i'
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:65: error: dereferencing pointer to incomplete type
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:65: error: expected expression before 'unsigned'
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:66: warning: assignment makes pointer from integer without a cast
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:67: error: dereferencing pointer to incomplete type
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:71: error: dereferencing pointer to incomplete type
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:85: error: implicit declaration of function 'hpsb_iso_recv_release_packets'
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c: In function 'node_of':
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:90: error: dereferencing pointer to incomplete type
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:90: warning: type defaults to 'int' in declaration of '__mptr'
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:90: warning: initialization from incompatible pointer type
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:90: error: invalid use of undefined type 'struct unit_directory'
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c: In function 'node_lock':
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:97: error: implicit declaration of function 'hpsb_node_lock'
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:97: error: 'EXTCODE_COMPARE_SWAP' undeclared (first use in this function)
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:97: error: (Each undeclared identifier is reported only once
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:97: error: for each function it appears in.)
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:98: error: 'quadlet_t' undeclared (first use in this function)
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:98: error: expected expression before ')' token
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c: In function 'node_read':
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:106: error: implicit declaration of function 'hpsb_node_read'
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c: In function 'node_write':
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:111: error: implicit declaration of function 'hpsb_node_write'
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c: In function 'start_iso':
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:122: error: implicit declaration of function 'hpsb_iso_recv_init'
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:122: error: dereferencing pointer to incomplete type
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:124: error: 'HPSB_ISO_DMA_DEFAULT' undeclared (first use in this function)
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:126: warning: assignment makes pointer from integer without a cast
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:133: error: implicit declaration of function 'hpsb_iso_recv_start'
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:136: error: implicit declaration of function 'hpsb_iso_shutdown'
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c: In function 'stop_iso':
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:147: error: implicit declaration of function 'hpsb_iso_stop'
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c: At top level:
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:162: warning: 'struct hpsb_host' declared inside parameter list
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c: In function 'fcp_request':
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:175: error: dereferencing pointer to incomplete type
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:176: error: dereferencing pointer to incomplete type
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c: In function 'node_probe':
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:190: error: dereferencing pointer to incomplete type
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:190: warning: type defaults to 'int' in declaration of '__mptr'
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:190: warning: initialization from incompatible pointer type
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:190: error: invalid use of undefined type 'struct unit_directory'
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:195: error: dereferencing pointer to incomplete type
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:195: error: 'quadlet_t' undeclared (first use in this function)
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:196: error: implicit declaration of function 'CSR1212_TEXTUAL_DESCRIPTOR_LEAF_DATA'
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:196: error: dereferencing pointer to incomplete type
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:196: warning: assignment makes pointer from integer without a cast
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c: At top level:
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:252: warning: 'struct unit_directory' declared inside parameter list
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c: In function 'node_update':
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:254: error: dereferencing pointer to incomplete type
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c: At top level:
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:262: error: variable 'fdtv_driver' has initializer but incomplete type
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:263: error: unknown field 'name' specified in initializer
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:263: warning: excess elements in struct initializer
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:263: warning: (near initialization for 'fdtv_driver')
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:264: error: unknown field 'id_table' specified in initializer
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:264: warning: excess elements in struct initializer
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:264: warning: (near initialization for 'fdtv_driver')
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:265: error: unknown field 'update' specified in initializer
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:265: warning: excess elements in struct initializer
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:265: warning: (near initialization for 'fdtv_driver')
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:266: error: unknown field 'driver' specified in initializer
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:266: error: extra brace group at end of initializer
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:266: error: (near initialization for 'fdtv_driver')
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:269: warning: excess elements in struct initializer
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:269: warning: (near initialization for 'fdtv_driver')
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:272: error: variable 'fdtv_highlevel' has initializer but incomplete type
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:273: error: unknown field 'name' specified in initializer
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:273: warning: excess elements in struct initializer
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:273: warning: (near initialization for 'fdtv_highlevel')
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:274: error: unknown field 'fcp_request' specified in initializer
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:274: warning: excess elements in struct initializer
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:274: warning: (near initialization for 'fdtv_highlevel')
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c: In function 'fdtv_1394_init':
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:281: error: implicit declaration of function 'hpsb_register_highlevel'
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:282: error: implicit declaration of function 'hpsb_register_protocol'
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:285: error: implicit declaration of function 'hpsb_unregister_highlevel'
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':
/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.c:292: error: implicit declaration of function 'hpsb_unregister_protocol'
make[3]: *** [/media/stuff/gspca-bdc9ee6ae5f2/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/media/stuff/gspca-bdc9ee6ae5f2/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/media/stuff/gspca-bdc9ee6ae5f2/v4l'
make: *** [all] Error 2


It looks like everything it going fine until it gets to the firedtv drivers, then it takes a dump, any one have any ideas?

---

### Post by leachyboy2001 on 2009-12-19
I got it working found this thread [http://ubuntuforums.org/showthread.php?t=1321194&highlight=vx-1000](http://ubuntuforums.org/showthread.php?t=1321194&highlight=vx-1000)

extract your drivers source
go into the directoy (cd gspacBLAHBLAH)
then run make, let it go through until it fails
THEN
nano v4l/.config (This file won't be there until you run make the first time)
Change CONFIG_DVB_FIREDTV=m to CONFIG_DVB_FIREDTV=n.
then make
then sudo make install
reboot
should be working :)

---

### Post by Ceyce on 2009-12-19
> **leachyboy2001 said:**
> I got it working found this thread [http://ubuntuforums.org/showthread.php?t=1321194&highlight=vx-1000](http://ubuntuforums.org/showthread.php?t=1321194&highlight=vx-1000)

extract your drivers source
go into the directoy (cd gspacBLAHBLAH)
then run make, let it go through until it fails
THEN
nano v4l/.config (This file won't be there until you run make the first time)
Change CONFIG_DVB_FIREDTV=m to CONFIG_DVB_FIREDTV=n.
then make
then sudo make install
reboot
should be working :)
I try it, but  there were no .config file, even not after extraction of downloaded stuff.

---

### Post by zerwas on 2009-12-31
> **Ceyce said:**
> I try it, but  there were no .config file, even not after extraction of downloaded stuff.

You have to execute the command "make" before the file appears. Compare with my [other reply]("http://ubuntuforums.org/showpost.php?p=8569519&postcount=4"):
> **zerwas said:**
> Okay,

first we need to open a [terminal]("https://help.ubuntu.com/community/UsingTheTerminal"). To do this, go to Applications menu -> Accessories -> Terminal.

Now you enter these commands *(one by one)*:
```
cd /tmp
wget http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2
tar xvfj tip.tar.bz2
cd v4l*
make
```
Wait, until it is finished (it will finish with an error).
Now, execute this command to open a file with a text editor:
```
gksudo gedit /tmp/v4l*/v4l/.config
```
Search for the line 
and change it to

Now click on "Save", close the text editor and get back to the terminal where you enter:
```
make
sudo make install
```

Now reboot your computer and your webcam should work.

---

### Post by Ceyce on 2010-01-03
[B]zerwas
[/B]I did this steps, and this is the result:
[http://xmages.net/upload/e01ec1a6.png](http://xmages.net/upload/e01ec1a6.png)

But thanks for trying help. Do you know what else can I do?

---

### Post by S.Q.Lapp on 2010-01-03
i've got the same result. camera works but image splits into stripes. looks like configured incorrect image dimensions. does anyone knows how to fix it?

ubuntu 9.10 karmic koala x86_64

---

### Post by tibike on 2010-01-04
same error here! 
worked well a couple of weeks ago... 
now this new v4l-dvb-b6b82258cf5e shows gray-ish pink-ish horizontal lines. 
any idea where a can get the old package from??

---

### Post by jesterthejedi on 2010-01-19
It's got a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460118](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/460118)

---

### Post by stanca on 2010-01-20
Worked for me at last just following step by step your tutorial.
Thank you very much guys::D:popcorn:

---

### Post by Ceyce on 2010-01-29
It works now!!!! :D
I did those steps again, and it get worked!

---

### Post by stanca on 2010-01-29
Just don't forget to repeat the whole operation again at every kernel update.;)
Edit:Worked with latest kernel update too(2.6.31-19)!:P
In Lucid Lynx Alpha2 with 2.6.32-13 kernel version the webcam is working automatically,without any other extra driver,just install cheese and see.

---

### Post by kyleabaker on 2010-02-23
> **S.Q.Lapp said:**
> i've got the same result. camera works but image splits into stripes. looks like configured incorrect image dimensions. does anyone knows how to fix it?

ubuntu 9.10 karmic koala x86_64

You got the camera working in 9.10 x86_64? I've been trying to get mine working in 9.10 x86_64 for months with no success at all. What exactly have you tried thus far?

> **stanca said:**
> Just don't forget to repeat the whole operation again at every kernel update.;)
Edit:Worked with latest kernel update too(2.6.31-19)!:P
In Lucid Lynx Alpha2 with 2.6.32-13 kernel version the webcam is working automatically,without any other extra driver,just install cheese and see.

Your signature suggests you're using 10.04 x86_64 with the vx-1000 webcam working out of the box. Is that so? I may just upgrade soon if its working on its own. I've been digging through duplicate threads about this web cam and haven't had any luck with it in 9.10 x86_64.

EDIT:
After still not getting my cam to work in Ubuntu 9.10 x86_64, I just upgraded to Ubuntu 10.04 x86_64 (alpha 3 in a couple days) and its working by default (as you said stanca)! Finally I can use my web cam in Ubuntu.

If any one else is still having problems with this web cam, I would suggest that you either be patient until Ubuntu 10.04 is released or (if you're feeling brave) upgrade to an alpha or beta release (later).

Note, however, that the mic/audio is not working so I have to use a separate mic for now. Anyone know of a fix for the web cam's mic?

---

### Post by jesterthejedi on 2010-02-25
This is always been a tricky cam to use. It works, then breaks, then works again. I wish the Devs would stick with a working driver and include it in the release. I will test it out on my Lucid box tonight. *crosses fingers*

---

### Post by jesterthejedi on 2010-02-25
It's buggy as hell. Half the time it wont load any image, then it alternates from showing garbage or a slow refresh. I tried both 640x480 and 320x240 only the latter give any output.

---

### Post by executorvs on 2010-03-13
I can get the image to work all  right with a little tweaking of the v4l2 settings in lucid but can't get anything from the mic. has anyone ever gotten this mic working?

---

### Post by zillacles on 2010-03-13
I got my mic working. I posted what I did here:

[http://ubuntuforums.org/showthread.php?t=1333343](http://ubuntuforums.org/showthread.php?t=1333343)

---

### Post by cleverbubbles123 on 2010-04-02
9.10 karmic, all is well. the tutorial by [leachyboy2001]("http://www.uluga.ubuntuforums.org/member.php?u=312574"), post no.3, did the trick fine for me.
Thanks a lot!

---

### Post by Ron_ on 2010-05-18
I am using Ubuntu 9.10 amd64.  Has anyone tried   [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2) drivers on a 64-bit system?  I _really_ don't want to break what I've got (including proprietary nVidia drivers for my monitor.)

Also, have people explored ALSA backports to get the camera and mic working?  Which Ubuntu version of ALSA are you using?

---

### Post by kyleabaker on 2010-07-07
If you're having a problem getting the mic working with the vx-1000 camera, take a look at this:

The webcam driver maintainer has suggested a way to fix this if anyone else wants to try and help me get something working permanently. I'm sure if we get this working he will push an update soon. More details here:

[http://ubuntuforums.org/showthread.php?t=1516541&p=9560552](http://ubuntuforums.org/showthread.php?t=1516541&p=9560552)

---

### Post by Ron_ on 2010-07-07
Kyle just showed me how to produce sound here: [http://ubuntuforums.org/showthread.php?p=9560972#post9560972](http://ubuntuforums.org/showthread.php?p=9560972#post9560972) (post #12.)  Many thanks.

---

### Post by kyleabaker on 2010-07-12
I've posted a patch to fix the Microsoft LifeCam VX-1000 where the microphone stops working or doesn't work at all.

Please test this patch and let me know if it fixes your webcam. It may also fix the Microsoft VX-3000 if it is having mic problems where the microphone stops working.

All the details are here:
[http://ubuntuforums.org/showthread.php?p=9581593#post9581593]("http://ubuntuforums.org/showthread.php?p=9581593#post9581593")

---

### Post by D-Dan on 2011-01-09
Anyone still struggling getting this cam working with skype, I just managed it after a week of hacks, cludges and hair tearing failed to solve the problem.

Patch gspca as per kyleabaker for sound.

Start skype with

```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```

(Note the change to lib32 from previous suggestions).

There are three versions of v4lcompat.so. (the other is in lib64, so try that if neither of the others don't work).

---

### Post by tibike on 2012-02-29
Hi jesterthejedi, 
Have you gotten this to work?
I get the same crooked image with a new 11.10 install.

---

