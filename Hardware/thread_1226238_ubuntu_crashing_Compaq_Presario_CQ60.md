---
title: "ubuntu crashing Compaq Presario CQ60"
date: 2009-07-29
forum: Hardware
---

### Post by elajas82 on 2009-07-29
Hello. After endless searching, testing different options i still have a strange problem that maybe some one can help me.
I just got myself new laptop from PC World thrue internet **Compaq Presario CQ60**. It was bundeled with Vista. I was planning to use linux it from the start so i got rid of the Vista and installed linux Mint 7 on it. It was working fine. then i installed additional software that i need like Sun Virtualbox, truecrypt and compiz with emerald themes. Now the funny things start to happen. When i tried to start ether virtualbox, truecrypt or emerald theme settings, my linux mint crashed. I had to manually restart it because nothing responded. After some hopless trys i decided to install Ubuntu. Same thing here + other things that make my laptop freeze completly (camera settings in amsn, some website pages in FF, etc).
Here is my laptop info just incase:

-Computer-
Processor        : 2x AMD Turion Dual-Core RM-72
Memory        : 2837MB (482MB used)
Operating System        : Ubuntu 9.04
User Name        : [blanked out]
Date/Time        : Wed 29 Jul 2009 16:21:29 BST
-Display-
Resolution        : 1366x768 pixels
OpenGL Renderer        : GeForce 8200M G/PCI/SSE2/3DNOW!
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA NVidia
-Input Devices-
 Power Button (FF)
 Lid Switch
 Sleep Button (CM)
 Power Button (CM)
 Macintosh mouse button emulation
 AT Translated Set 2 keyboard
 Video Bus
 PC Speaker
 HP Webcam-101
 SynPS/2 Synaptics TouchPad
Optiarc DVD RW AD-7581S
ATA FUJITSU MHZ2160B

Does anyone have any idea why is this happening or how to correct it. I need virtualbox and truecrypt. 
Please note that i am not very experienced linux user, i have used linux mint so far in intel platform PC-s little time but that is basicly all. Please help me, i do not want to go back to using windows .... :(

---

### Post by lavinog on 2009-07-29
Did you install the proprietary nvidia driver? (I think a dialog comes up after installing ubuntu to tell you that a restricted driver is available...did you install this driver or a driver from a guide?

Can you do a fresh install, then install each of Sun Virtualbox, truecrypt and compiz with emerald themes individually to find out which software causes your system to act funny.
Also explain how you are installing these items? Are you using synaptic/apt-get/aptitude or are you downloading these from a website?

---

### Post by theboomboomcars on 2009-07-29
Did you enable desktop effects?

Another thing to try is using the latest driver from nvidia, if you were already using the one from the repositories.

---

### Post by elajas82 on 2009-07-29
About the nvidia drivers: yes, i installed them like i always do - the nodification comes up, i choose the reccomended one and then after install i restarted like needed.

The software install was in this order:
Ubuntu
Nvidia drivers
compiz with emerald
virtualbox
truecrypt
other apps

I usually use synaptic to install them. 
Also note: in synaptic the virtualbox is version 2.x and after i started it it displayed the info box about new 3.x version. that nodification box also crashed my mint and ubuntu.

I can test the new clean install and then all the apps seperatly.
I will report back later after i finished the test

Thanks all for the help

---

### Post by elajas82 on 2009-07-29
ok, i am back. did some clean reinstalls. After install i only added nvidia driver, nothing else, not even the updates and then tested apps. Here are my results:

truecrypt: all works until i mount a volume, in the password screen the ubuntu freezes
virtuabox: installed the vituabox-osd in synaptic, so far no problems
emerald theme manager: crashes
amsn: when configuring my laptop intecrated webcam, it freezes amsn in microphone step, ubuntu works fine.

these are the apps i have tested so far. I do not want to make another reinstall ...
I can live whitout webcam (i am not so good looking anyway :P), also i can live whitout truecrypt and emerald themes. There were other things that crashed my ubuntu for example adding custom rule in adblock+ in FF and even visiting one page on one site using FF and some other random things but i have not tested them in new clean install.

Any help to track down and fix it strange "bug" is really apriciated

Thanks

---

### Post by lavinog on 2009-07-30
I am not sure if this can catch kernel panics, but you could try this in a terminal window. 
```
dmesg|tail -f
```
leave the terminal visable and then try and mount a volume with truecrypt (start truecrypt from a terminal too.)
When it crashes see if the terminal displays anything.

emerald and the webcam would seem to be related to video driver issues. Truecrypt has me curious.
Does anyone know if Truecrypt uses any fancy graphic effects?

---

### Post by lavinog on 2009-07-30
What type of filesystem are you trying to mount with truecrypt?

Do you have any ext4 filesystems? There was a bug in the first jaunty kernel that caused systems to crash when manipulating large files on ext4 filesystems. A later kernel update addresses this.

---

### Post by elajas82 on 2009-07-30
The filesystem i use is deafult ext3
The truecrypt does not use any fancy graphical effects. It's pretty simple aplication:
You create a crypted filecontainer
open up gui
select the container file and slot where it will be mounted
click "mount" and password dialog pops up
enter password and voila, the filecontainer is mounted as drive

I tried the terminal command you suggested.
First installed trucrypt, then created filecontainer (5 gb, fat32) and then before mounting i started up the terminal. this is only thing it displays:

```
[   95.612231] ath5k phy0: unsupported jumbo
[  122.735382] ath5k phy0: noise floor calibration timeout (2422MHz)
[  123.871950] ath5k phy0: noise floor calibration timeout (2467MHz)
[  182.410027] ath5k phy0: noise floor calibration timeout (2412MHz)
[  182.898159] ath5k phy0: noise floor calibration timeout (2422MHz)
[  218.926663] ath5k phy0: unsupported jumbo
[  262.402145] ath5k phy0: noise floor calibration timeout (2412MHz)
[  262.894409] ath5k phy0: noise floor calibration timeout (2422MHz)
[  333.104251] ath5k phy0: unsupported jumbo
[  333.334211] ath5k phy0: noise floor calibration timeout (2462MHz)
```This was displayed before i even tried to mount the filecontainer and whne i clicked "mount" and ubuntu crashed again, nothing changed in console window.

Also there is one thing i want to clarify: the compiz works fully, all the 3d effects, cube, animations, etc - the full thing works. The emerald themes is the ones that don't work and crash when i try to configure emerald themes settings but like i said, i can live whitout them :)

I hope it helps.

---

### Post by stlsaint on 2009-07-30
looks like you solved you have pin pointed a initial problem...trucrypt...im not that useful when it comes to trucrypt but that seems to be where you need to focus all your attention! and yes your graphics seem to be faulted as well!!

---

### Post by lavinog on 2009-07-30
[ath5k locks up system in jaunty - "ath5k phy0: noise floor calibration timeout" ](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/341952)

It could be possible that the ath5k (wifi) driver is causing the problem. Can you disable wireless and see if those messages stop, then try truecrypt again. It may be helpful to connect with an ethernet cable to help with the debuging.

If this is the case, I would be curious to know what truecrypt needs an internet connection for? Is there a usage feedback feature (many programs are starting to do this)?

---

### Post by lavinog on 2009-07-30
Can you mount truecrypt filecontainers from the terminal?
If so try mounting from the non-graphical console: press alt-f1 to switch to a text mode console. Kernel panics can only display info in text mode currently.

---

### Post by elajas82 on 2009-07-31
Hi again. 
Currently using the internet cable and also switched off my wifi.
Tested truecrypt in console and got one funny result.

First i started another console and this was displayed (in all cases of testing)

```
[   18.669109] vboxdrv: fAsync=1 offMin=0x48bbad32 offMax=0x48bbad32
[   18.669165] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   18.669167] vboxdrv: Successfully loaded version 2.1.4_OSE (interface 0x000a0009).
[   19.736066] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.736070] Bluetooth: BNEP filters: protocol multicast
[   19.763091] Bridge firewalling registered
[   20.973834] ppdev: user-space parallel port driver
[   25.052476] forcedeth 0000:00:0a.0: irq 2301 for MSI/MSI-X
[   25.336724] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   35.436210] eth0: no IPv6 routers present

```

used simple commant to mount

```
truecrypt test.tc /media/truecrypt1
```

First try: the password box almost appeared and then my ubuntu logged me automaticly out, not shutdown but just logout. Ubuntu kept going, nothing changed in the console before logout
Other trys: ubuntu freezed completly, nothing changed in console

---

