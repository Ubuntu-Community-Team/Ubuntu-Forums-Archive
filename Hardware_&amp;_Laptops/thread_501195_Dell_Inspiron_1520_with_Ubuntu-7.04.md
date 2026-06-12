---
title: "Dell Inspiron 1520 with Ubuntu-7.04"
date: 2007-07-14
forum: Hardware &amp; Laptops
---

### Post by linux23dragon on 2007-07-14
**[SIZE=5]For people who are looking to install Ubuntu-7.04 on a Dell Inspiron 1520 [/SIZE]**

**[COLOR="Blue"]I've also posted this howto on [linux-profiles]("http://www.linux-profiles.com/").  Check it out ;)[/COLOR]**

UPDATE: (07-10-07) Included Dell Wiki support fixes that should benefit the Dell Inspiron 1520.  Added the Netgear Rangemax WiFi, to the working hardware list.
UPDATE: (07-09-07) Included more Ubuntu-7.04 64bit hints (Including the Grub boot splash fix).
  


[SIZE=3]This forum will get this list of hardware configured and working correctly, with Ubuntu-7.04:-[/SIZE]

Ethernet [COLOR="Green"](working)[/COLOR]
Internal Wifi ([SIZE=1]Intel IPW3945*, bcm43xx, Netgear Rangemax DG834PN, Intel Wireless N)[/SIZE] [COLOR="Green"](working)[/COLOR]
Bluetooth [COLOR="Green"](working)[/COLOR]
Firewire IEEE1394 [COLOR="Green"](working)[/COLOR]
Intel or Nvidia 8600M GT or ATI Graphics Cards [COLOR="Green"](working)[/COLOR]
HD Sound card [COLOR="Green"](working)[/COLOR]
USB ports [COLOR="Green"](working)[/COLOR]
LCD Display [COLOR="Green"](working)[/COLOR]
Keyboard [COLOR="Green"](working)[/COLOR]
Mousepad (with mouse buttons) [COLOR="Green"](working)[/COLOR]
Multimedia buttons [COLOR="Green"](working)[/COLOR]
Web Cam [COLOR="Green"](working)[/COLOR]
DVD +/- Burner [COLOR="Green"](working)[/COLOR]
Digital Microphone [COLOR="Green"](working)[/COLOR]
Audio input/outputs *1 [COLOR="Green"](working)[/COLOR]
Graphics [COLOR="Green"](working)[/COLOR]
VGA output [COLOR="Green"](working)[/COLOR]
S-Video out connector  [COLOR="Green"](working)[/COLOR]

[SIZE=3]Not yet working correctly:-[/SIZE]

Internal modem (The driver has been known to disable the audio)



*1: An important note on the microphone: the Sound Recorder program in the Applications menu under Sound & Video should not be used for testing purposes.
It resets parts of the mixer (most importantly it reduces InMux to 0 and disables ADCMux) which will cause the mic to not work. Instead, install Audacity using the command 
"sudo apt-get install audacity" in a terminal. It can record and do a lot more.

* The  IPW3945 driver works, but can be unstable at times.  Please read **WiFi driver details** below for more information.



_**[SIZE=5]Hints on setting up your hardware while installing Ubuntu[/SIZE]**_

You should be able to install Ubuntu-7.04 with the [alternate CD]("http://www.ubuntu.com/getubuntu/download") (You can install Ubuntu in text mode).  
You will have issues with the Ubuntu-7.04 live CD, due to the fact that the piix  driver (that drives the DVD burner) fails to load and stalls the system at boot up.   You can install Ubuntu-6.10
 and upgrade to Ubuntu-7.04 if you really need the GUI installation method (refer to Note 1).

The MD5 Sum ( for the ubuntu-7.04-alternate-i386.iso) should be:- ```
 ff0cc7c9ed5157f0ff8c0f2213973f49
``` 
After installation, you will need to choose the "recovery mode" boot option. (Use the escape key to get the Grub menu).


[COLOR="Gray"]NOTE 0:- On some 64bit systems (using Ubuntu-64bit), you will not have a "boot splash" screen.  You will only see a black screen while
                the system boots.   To fix this issue please refer to the [ubuntu-7.04+64+bit+boot+vga+grub]("http://ubuntuforums.org/showthread.php?t=454392&highlight=ubuntu-7.04+64+bit+boot+vga+grub") thread.
              

NOTE 1:- If you can't install Ubuntu-7.04 by using the alternate CD (text mode), then install  [Ubuntu-6.10]("http://www.ubuntu.com/getubuntu/downloadmirrors")
               using the graphical interface.  You will then be able to upgrade to Ubuntu-7.04, using the Update Manager.   You may need to use the **[SIZE=2]ATI Graphics card owners[/SIZE]**
               section if the Xserver does not run  correctly (no mater what Graphics card you have).  Also see NOTE 2: (Found at the "ALL Graphics Cards" section of this hint)
[/COLOR]



Log in as root and backup your /etc/X11/xorg.conf. You will need to edit it:-
```
sudo -i
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```



Now choose the following Graphics card (that your system has) --> 




**[SIZE=2]Intel Graphics card owners (Under Review.  Please post if the instructions work o.k or not for you.)[/SIZE]** 

[COLOR=Red]*You will need to be connected to a local network to do the following*[/COLOR]

Remove out dated Intel driver:-

```

apt-get remove xserver-xorg-video-i810

```
Update the /etc/apt/sources.list using Vim:

```

cp -i /etc/apt/sources.list /etc/apt/sources.list_backup &&
vi /etc/apt/sources.list
```
Add the "feisty-proposed" and uncomment (or add) the "feisty-backports" sources:-
```

deb http://ca.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe
```

Exit out of vim ("Esc"  "Shift+:"  "wq") and update the sources.list
```

aptitude -y update

```
[COLOR="Gray"]NOTE: you might need to only use "aptitude". (which will give you menu options).[/COLOR]
Please make sure you have updated the Linux kernel to 2.6.20-16. 


Install the new Intel driver:-

```

apt-get install xserver-xorg-video-intel
```
Reconfigure /etc/xorg.conf


Use Vim to edit /etc/X11/xorg.conf:-
```
vi /etc/X11/xorg.conf
```
Check to see if you have the device driver "intel"  (located  at  “Section Device”)
You may need to change "intel" to "i810" for xorg to work correctly.



**[SIZE=2]Nvidia Graphics card owners[/SIZE]**

The Xserver will correctly load the "nv" driver. But the "nv" driver may not correctly support "very new" graphics cards (like the G80). Sometimes the 
problem can also be in relation with the BIOS (firmware). If you find that the Xserver fails to start up, then use Vim to edit /etc/X11/xorg.conf:-

```
vi /etc/X11/xorg.conf
```
Change the device driver “nv” to "vesa" (located  at  “Section Device”)

You will be loading the Nvidia drivers later on.


**[SIZE=2]ATI Graphics card owners[/SIZE]**

The Xserver will correctly load the "vesa" or the "ati" driver. But the "vesa" driver has a broken refresh rate detection (with ATI cards), and the 
new ATI graphics card may not work with the "ati" driver. Sometimes the problem can be in relation with the BIOS (firmware). If you find that 
the Xserver fails to start up, then use Vim to edit /etc/X11/xorg.conf:-

```
vi /etc/X11/xorg.conf
```
Change the device driver “ati” to “vesa” (located  at  “Section Device”)?
ATI card owners might need to make sure if the resolution is o.k to use.  You might need to use 800x600 or 640x480 (as the only option) @ 24bit.
Also make sure you have the monitor Horizontal and Vertical settings (located at the “Section Monitor”). 

```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
        "HorizSync 36-52"
        "VertRefresh 36-60"
EndSection

```


You will be loading the ATI drivers later on.


**[SIZE=2]Any Graphics Cards[/SIZE]**
Make sure that the Default Depth (located at "Section Screen") is set to "16" or "24".

Notice that the "Subsection Display" has different  "Mode" sections for other possible color Depths.  Please ensure that you
have set up the correct screen resolution to the color depth you want to use.   

Once you have finished editing the /etc/X11/xorg.conf,  reboot.
Allow all the automatic updates before continuing on.


[COLOR="Gray"]NOTE 0: I recommend using the default depth of "24", if you intend to run Beryl.  

NOTE 1: If you have the Ubuntu 7.04 DVD,  then please read the "**DVD fix**" found in the
               "**Handy system configuration hints for Feasty**" section before you reboot.

NOTE 2: If you have booted from Ubuntu-6.10 and added the needed changes to "/etc/X11/Xorg.conf" (Using the above hints). Try to restart the Xserver:-
               ```
[COLOR="Gray"]startx[/COLOR]
```You now should be able to install Ubuntu-6.10 in graphical mode. Then upgrade to Ubuntu-7.04.

NOTE 3: If you still not able to start the Xserver, then try removing the “/etc/X11/xorg.conf” file. This will allow the Xserver to scan and optimally configure all of the 
               hardware devices, on your system. The following instructions will make a backup of your xorg.conf ( xorg.conf-bk), and then remove xorg.conf. 
               We can restore xorg.conf it later on.
               ```
[COLOR="Gray"]sudo cp -a /etc/X11/xorg.conf /etc/X11/xorg.conf-bk &&
               sudo rm /etc/X11/xorg.conf[/COLOR]
```
               Restart the Xserver:-
               ```
[COLOR="Gray"]startx[/COLOR]
```
               Now we can restore xorg.conf:-
               ```
[COLOR="Gray"]sudo cp -a /etc/X11/xorg.conf-bk /etc/X11/xorg.conf[/COLOR]
```
               Look at "/var/log/Xorg.0.log". There is lots of hints in the automatic "scan" (found in Xorg.0.log). Find the video driver and screen resolution used, and 
               substitute the values at "Section Device" and "Subsection Display" in "/etc/X11/xorg.conf" using Vi.[/COLOR]







[COLOR=brown][INDENT]
------------[SIZE=2]How to use the Vi editor[/SIZE]---------------------------------
**[SIZE=2]To edit (or add text) in Vi:-[/SIZE]**

Press the “i” key (without the quotes) to enter text.

**[SIZE=2]To delete text:-[/SIZE]**

Press the “Esc”  key (without the quotes) when you have finished entering text
Press the “delete” key (without the quotes) when the cursor is under the letter or value you need to delete.

**[SIZE=2]To save and exit Vim:-[/SIZE]**

Press the “Esc”  key (without the quotes) when you have finished entering text.
Press the “Shift (and) :” keys together (without the (and) and quotes) to get to the Vi command line, and then type the keys “wq” two Write to file and Quit.

If you want quit without saving in Vi, then use the “q!” command like so:-

Esc
Shift :
q!
 -----------[SIZE=2]EOF on How to use the Vi editor[/SIZE]-------------------------
[/INDENT][/COLOR]





_**[SIZE=5]Handy system configuration hints for Feasty[/SIZE]**_



[SIZE=3]**Ubuntu-7.04 64bit Development tools and other software packages**[/SIZE]

You may need to use the Synaptic Package Manager to install "build-essential", "subversion"
and others if you get any messages like this(when using some commands in the terminal):-

```
[COLOR="DarkOrchid"]Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate[/COLOR]
```




[SIZE=3]**IRQ Balancing for Dual Core (SMP)**[/SIZE]

Search (in the Synaptic Package Manager) to see if you have the irqbalance package installed.
IRQ balancing is a must for proper IRQ sharing with SMP (or in our case Multi core) systems.




[SIZE=3]**DVD fix**[/SIZE]

See this link for more information on getting the DVD player to work:-

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/CD_media_not_recognized](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/CD_media_not_recognized)

Use gedit (or vi) to edit /etc/modules:
```
 sudo gedit /etc/modules
```And add the following line:
```
piix
```There is no need to rebuild the kernel image at all. Just reboot :)

Open up a terminal and check the DVD setup.  Look out for DMA and I/O (16-Bit or 32-Bit), using the following command:

```
sudo hdparm /dev/hda
```If DMA is not enabled, then:
```
sudo gedit /etc/hdparm.conf
```And add this at the end of hdparm.conf file:
```
/dev/hda {
        dma = on
        interrupt_unmask = on
        io32_support = 1
}
```


[COLOR=RED]***Note: Never use  "hdpram" commands to SATA drives (like:- /dev/sda or /dev/sdc ...).  You might kill your system/software
(The 1520 uses PATA for the DVD Burner, but uses SATA for the Hard Drive.  The following commands will only effect the DVD Burner on 
the 1520, which is what you want)***[/COLOR]


[SIZE=3]**Web Cam [COLOR="Green"](32bit and 64bit tested)[/COLOR]**[/SIZE]
The Dell Inspiron 1520 uses the UVC-Linux Web Cam driver.
Copy and past the following instructions in the terminal to install an updated version of linux-uvc driver:-

```
 sudo apt-get install subversion build-essential linux-headers-$(uname -r) &&
svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk &&
cd trunk &&
make &&
sudo install -v -m644 uvcvideo.ko /lib/modules/$(uname -r)/kernel/ubuntu/media/usbvideo/uvcvideo.ko &&
sudo depmod -ae 
``` 


Reboot :)

This driver only supports V4L2.  Currently you can use Ekiga and aMSN (SVN version).
Patches for other Web cam programs (tvtime, mythtv,xawtv) are found here:-  [http://svn.berlios.de/wsvn/linux-uvc](http://svn.berlios.de/wsvn/linux-uvc)

[COLOR="Gray"]NOTE: Ubuntu-7.04 64bit users may need to use the Synaptic Package Manager to install:
             Subversion,  linux-headers-$(uname -r) and build-essential.[/COLOR]


[SIZE=3]**Nvidia and ATI Graphics card setup**[/SIZE]

Use Alberto Milone's "Envy" ([http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)) to install the Nvidia or ATI  drivers.

[COLOR="Gray"]NOTE: Ubuntu-7.04 64bit users may need to use Synaptic Package Manager to install:
            
             ia32-libs, libqt3-mt-dev, kernel-wedge, rpm, sharutils, libgtk2.0-dev, 
             libxxf86misc-dev, libxtst-dev, libxxf86vm-dev and libxinerama-dev[/COLOR]




[SIZE=3]**Intel Graphics card setup**[/SIZE]

Setting Screen Resolution for Intel Chip sets information (If you don't like the default Screen Resolution) :-
```

sudo dpkg-reconfigure -phigh xserver-xorg
```
This should allow you to pick both the driver (intel) and the resolutions you want.
More information about wide screen resolutions:- 
[http://ubuntuforums.org/showthread.p...creen  +laptop]("http://ubuntuforums.org/showthread.php?t=351647&highlight=intel+widescreen+laptop")




[SIZE=3]**WiFi driver details**[/SIZE]

Check to see if you already have the restricted driver running.

[COLOR="Blue"]There is a Wireless hard switch on the side (left) of the Notebook (Next to a small LED).[/COLOR]


**ipw3945**

At the moment, the ipw3945 driver works, but can play up from time to time (If you leave the Notebook off for a long period of time). We are looking into this issue now. 
So far, you can sometimes recover the WiFi connection, after you connect to via Ethernet. The Dell BIOS update (A03), does not fix the issue. 
If any one can help with resolving this (ipw3945 driver) WiFi issue, then please feel free to post your ideas.

There is already a bug report about it [here]("https://bugs.launchpad.net/ubuntu/+bug/134515").  So please help out so we all can get this issue fixed ASAP.
Also please see this [thread]("http://ubuntuforums.org/showthread.php?p=3285326#post3285326") as well.


**bcm43xx** (Please confirm that these instructions work "as is" for you)

First, make sure the wireless is turned on in the BIOS, and that if you have the switch controlling the WiFi, that the switch is also turned on. :wink:

Add this to your /etc/apt/sources.list:
```
deb http://ubuntu.cafuego.net edgy-cafuego bcm43xx
```

Get the repo key:
```
wget http://ubuntu.cafuego.net/969F3F57.gpg -O- | sudo apt-key add -
```
 
Update package list and install the broadcom firmware
```
sudo apt-get update && sudo apt-get install bcm43xx-firmware
```

Load the kernel module (if you blacklisted it for ndiswrapper, make sure to remove it from /etc/modprobe.d/blacklist)
```
sudo modprobe bcm43xx
```

Now the WiFi light should come on and you should see the interface listed:
```
iwconfig
```

You can find more information from [ubuntuforums.org]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy#head-d2623559f21cb2d6373aaa3a17dece9d8f2abb50")


[SIZE=3][B]
HD Audio card setup  [/B][/SIZE]

Make sure you have the complete Alsa system installed:-
```
sudo apt-get install alsa-base alsa-tools alsa-oss alsa-utils alsa-firmware-loaders
```
Edit the /etc/modprobe.d/alsa-base file:
```
sudo gedit /etc/modprobe.d/alsa-base
```And add this line:
```
options snd-hda-intel model=dell-laptop
```
update and load modules: 
```
sudo update-modules &&
sudo modprobe snd-hda-intel model=dell-laptop ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss
```






_**Add-on_Packages**_
Here is some information about Ubuntu add ons from the Dell (Wiki Support):- [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Add-on_Packages](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Add-on_Packages)

**_Dell Fixes_**
There are some Dell supported [fixes]("http://linux.dell.com/wiki/index.php/Ubuntu_7.04") that could also work for the Inspiron 1520 Notebook



_**UBUNTU WIKI HELP**_

Please use this Ubuntu Wiki link to configure other Software and Hardware setups:- [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)



_**[SIZE=5]Notes[/SIZE]**_

Most issues may be solved once Ubuntu-7.XX will come out in October.



**[SIZE=3]Changelog:[/SIZE]**

(15th Jul 07) Added Notes and URL fixes. Added some more details
(20th Jul 07) Added note by [ynef]("http://ubuntuforums.org/member.php?u=1224")
(22 Jul 07) Fixed DVD Burner issues
(27th Jul 07)  Added Intel driver links and information thanks to [odin1965]("http://ubuntuforums.org/member.php?u=93068")
(28th Jul 07) Added more Dell support.  More information about kernel modules and Intel Graphics from [specker]("http://ubuntuforums.org/member.php?u=326856")
(28th Jul 07) Improved Intel Grapthics support, thanks for pointing out this information [URL="http://ubuntuforums.org/member.php?u=93068"]odin1965
[/URL](12th Aug 07) Now using "checkinstall" to install Alsa.  Thanks goes to [DarthTibault]("http://ubuntuforums.org/member.php?u=149571")
(13th Aug 07) Web Cam working thanks to [carminez]("http://ubuntuforums.org/member.php?u=347577")
(20 Aug 07) Reformat.  Thanks for testing and feedback [oliparcol]("http://ubuntuforums.org/member.php?u=357007")
(25 Aug 07) Added bcm43xx WiFi support, thanks goes to [Altimar]("http://ubuntuforums.org/member.php?u=367390")
(27-08-07) Added note about the Ubuntu 7.04 DVD, thanks goes to [Leebobs]("http://ubuntuforums.org/member.php?u=6743")
(31-08-07) Added MD5 Sum for ubuntu-7.04-alternate-i386.iso.  Thanks [Juanete]("http://ubuntuforums.org/member.php?u=370749")
(1-09-07) Fixed jack audio output issues thanks to  [ jeff_p]("http://ubuntuforums.org/member.php?u=249111").  Changed IEEE1394 status, thanks [unattached]("http://ubuntuforums.org/member.php?u=372826")
(02-09-07) Removed Alsa link for support reasons

---

### Post by manchoy on 2007-07-16
Hi linux23dragon,

I read thru your post, finally i managed to boot my inspiron 1520 using Ubuntu livecd, but eventually, i cant load the X window. Afterward, it only show me the command window. Im using ubuntu 6.08 which downloaded from ubuntu site. I already follow all your instruction such as set the vga mode. Which option you choose to boot ubuntu? normal boot or safe graphical mode? Hope to see your reply soon with more detail steps ;) Thanks in advance

---

### Post by linux23dragon on 2007-07-16
> **manchoy said:**
> Hi linux23dragon,

I read thru your post, finally i managed to boot my inspiron 1520 using Ubuntu livecd, but eventually, i cant load the X window. Afterward, it only show me the command window. Im using ubuntu 6.08 which downloaded from ubuntu site. I already follow all your instruction such as set the vga mode. Which option you choose to boot ubuntu? normal boot or safe graphical mode? Hope to see your reply soon with more detail steps ;) Thanks in advance



I have not tried installing with Ubuntu-6.08 live CD.  I have only used, (and recommend to use Ubuntu- 6.10) install CD.  You can boot the install CD  in normal graphical mode.

The X server will error out when it first loads.  This is normal because it automaticly sets up you grathics card to run with the nv driver.  The nv driver does not yet support the Nvidia Geforce-8600M, so you need to change the xorg.conf divice driver "nv" to "vesa"

Once you get to the Xorg error message you need to press Ctrl-Alt F2 keys.  You should find yourself at a new terminal.  Type the command "sudo -i" (without the quotes). That will put you in super user mode.

Next you need to use vim, to edit the xorg.conf file, like this:-

(Type this following command in the terminal)

vi /etc/X11/xorg.conf

Scroll down untill you find:-   Section "Device"


change "nv" to "vesa" (press the "i" key on your keyboard to edit the file.  use the "delete" key to delete text.  And to save, you need to use the "Shift - :" keys, and then press the "wq" keys.

Once you have finshed, log out of root by typing "exit".  Then start the xserver by typing "startx" in the terminal.

I'll be updateing the instructions later on today once I get back from work.

EDIT:
Instruction changes, are now in.

---

### Post by manchoy on 2007-07-17
oh yeah, thanks for your clear guidance. By the way, i was trying to edit the file after i failed to load the X server. But it keep saying the file open in read only mode. Since the ubuntu are not installed yet into hard drive. If i not mistaken, all the linux files are loaded in memory and it should be read-only right?

---

### Post by linux23dragon on 2007-07-17
> **manchoy said:**
> oh yeah, thanks for your clear guidance. By the way, i was trying to edit the file after i failed to load the X server. But it keep saying the file open in read only mode. Since the ubuntu are not installed yet into hard drive. If i not mistaken, all the linux files are loaded in memory and it should be read-only right?

Yep.
You can only save changes (like"/etc/X11/xorg.conf"), when you are in supper user (root) mode.  Also, the system can change and/or save the configuration information in the RAM image as well.

---

### Post by manchoy on 2007-07-17
wow, its wonderful. I will try it out in next couple of hours. Hopefully it will run ;) I will post the result once i successfully installed it! Thanks ya linux23dragon

---

### Post by manchoy on 2007-07-17
Arggggggggggggggghhh, i get stucked!!! while i starting the xserver, why nothing appear on my screen? and the hard disk stop responding and now i cant even to shut down my laptop properly....help!!

---

### Post by linux23dragon on 2007-07-17
> **manchoy said:**
> Arggggggggggggggghhh, i get stucked!!! while i starting the xserver, why nothing appear on my screen? and the hard disk stop responding and now i cant even to shut down my laptop properly....help!!


O.K  I'm not sure about the xserver, as I don't see the error output.  Can you please check if /etc/X11/xorg.conf is correct?

To shut down the pc, you need to type halt in the terminal as root user like this.

sudo -i 
halt

This is because GDM (Gnome Desktop Manager) is not loaded at this time.   The GDM had to exit out, when the xserver first failed to load (during bootup).


Also.  You are using Ubuntu-6.10?

Edit:

I forgot to ask.
Does you laptop have an Nvidia or ATI grathics card?

---

### Post by manchoy on 2007-07-17
my screen just blank...no response...my laptop just like being shut down, so i cant type anything since the laptop was shut down ;) Ya, my laptop bundled with Nvidia graphic card

Im using version 6.06 downloaded from official site. How can i download version 6.10 livecd? Thanks

---

### Post by linux23dragon on 2007-07-17
> **manchoy said:**
> my screen just blank...no response...my laptop just like being shut down, so i cant type anything since the laptop was shut down ;) Ya, my laptop bundled with Nvidia graphic card

Im using version 6.06 downloaded from official site. How can i download version 6.10 livecd? Thanks

You can download a image of Ubuntu-6.10 from:-
[http://filer-1.filearena.net/pub/ubuntu-releases/6.10/ubuntu-6.10-desktop-i386.iso](http://filer-1.filearena.net/pub/ubuntu-releases/6.10/ubuntu-6.10-desktop-i386.iso)

Or for 64bit:-
[http://filer-1.filearena.net/pub/ubuntu-releases/6.10/ubuntu-6.10-desktop-amd64.iso](http://filer-1.filearena.net/pub/ubuntu-releases/6.10/ubuntu-6.10-desktop-amd64.iso)

And burn the image to a blank CD ROM.

I've also updated my first post to include some instructions that might (hopfully) help.

---

### Post by manchoy on 2007-07-17
Same problem again, no display for my screen. I reinstall again using ver 6.10. Help........headache...any other suggestion?

Check list:

1) Boot with version 6.10 livecd
2) Change vga mode to 1024x768x32 and F6 option enabled
3) Booting...loading all files and drivers
4) Error...cant start x server
5) Type sudo -i in terminal (pressed CTRL+ALT+F2)
6) Type vi /etc/X11/xorg.conf
7) Edit "nv" to "vesa"
8) Save xorg.conf by :wq
9) Type exit
10) Type startx
11) Nothing shown and hard disk stop responding, cant eject dvdrom , laptop just "died" like that

---

### Post by winstanr on 2007-07-17
I've managed to install to 1520 using the 7.04 desktop cd. 

If you select the text based installation it will install, but the xserver does not work. If you modify X11.conf as described to VESA and then restart, you will get a part functioning machine. 

Then if you install the Envy package, the nvidia video problem is corrected. The only thing that does not work is the DVD.  Does anyone have any suggestions as to how I can get DVD to work without going back to 6.10? as my wife will not be happy me rebuilding her brand new machine ;)

---

### Post by manchoy on 2007-07-17
text based? Is there any option for text based installation?

---

### Post by winstanr on 2007-07-17
I should have said that I installed from the 7.04 **DVD**, not CD. Perhaps the menu options are different?

---

### Post by clint0r on 2007-07-17
Text based install worked for myself as well (download the alternate desktop cd iso) using jfs as my filesystem.

1680x1050 rez not working, can only pick up to 1024x768 so far.  Any hints on getting widescreen resolutions working?

edit: envy is the bomb!

---

### Post by manchoy on 2007-07-17
text based option you mean is manual installation or while you installing linux, you can see each action taken by linux core?Im confusing of your text based installation. ;) Recap again, i managed to load all linux files and drivers into RAM drive but after i edit the xorg.conf, i still cannot start my x server, my screen just blank and nothing happen after i typed startx

---

### Post by linux23dragon on 2007-07-17
> **manchoy said:**
> text based option you mean is manual installation or while you installing linux, you can see each action taken by linux core?Im confusing of your text based installation. ;) Recap again, i managed to load all linux files and drivers into RAM drive but after i edit the xorg.conf, i still cannot start my x server, my screen just blank and nothing happen after i typed startx


Hi manchoy

Can you please post your hardware configuration details please?

---

### Post by manchoy on 2007-07-17
my h/w:

Dell Inspiron 1520 model
Intel Core 2 CPU T5250 1.50GHz
2GB RAM
Nvidia GeForce 8600M GT 
120 GB SATA HDD

---

### Post by linux23dragon on 2007-07-17
> **manchoy said:**
> my h/w:

Dell Inspiron 1520 model
Intel Core 2 CPU T5250 1.50GHz
2GB RAM
Nvidia GeForce 8600M GT 
120 GB SATA HDD


So you don't have bluetooth, WiFi or WiFi router, DVD +/- burner?

Can you list the hardware thats on the Dell recept?

---

### Post by linux23dragon on 2007-07-17
> **clint0r said:**
> Text based install worked for myself as well (download the alternate desktop cd iso) using jfs as my filesystem.

1680x1050 rez not working, can only pick up to 1024x768 so far.  Any hints on getting widescreen resolutions working?

edit: envy is the bomb!

Could it be that you changed the resolution at the 24 bit colour section, but the xserver is set to run at 16 bit colour?

Edit:
Could you please write the list of hardware you have (built in the 1520 Notebook) from the Dell invioce please?

---

### Post by manchoy on 2007-07-17
The hardware is just exactly the same as you mentioned previouly in your first post.

The resolution i picked before booting was 1024x768x**32**, i need to configure that in xorg.conf as well?

---

### Post by linux23dragon on 2007-07-18
> **manchoy said:**
> The hardware is just exactly the same as you mentioned previouly in your first post.

The resolution i picked before booting was 1024x768x**32**, i need to configure that in xorg.conf as well?

"1024x768" should already be set up correctly in /etc/X11/xorg.conf

---

### Post by manchoy on 2007-07-18
em, then why there is no display on my screen ? What is the causes actually? Headached

---

### Post by linux23dragon on 2007-07-18
> **manchoy said:**
> em, then why there is no display on my screen ? What is the causes actually? Headached

Can you please run the following commands after you start the X server please:-

(in an new terminal:- Ctrl+Alt+F3)

ls /var/log

Then look for the "xorg" log file.  It might look somthing like "xorg.0.log"

Once you have identfied the xorg log file name then use vi to read the log output at the end of the file.

example:

vi /var/log/xorg.log
or
vi /var/log/xorg.0.log

That log file should tell you everything that went wrong.


Edit:  I've updated the orginal post to include additional information about the "/etc/X11/xorg.conf" setup.

---

### Post by linux23dragon on 2007-07-18
> **winstanr said:**
> I've managed to install to 1520 using the 7.04 desktop cd. 

If you select the text based installation it will install, but the xserver does not work. If you modify X11.conf as described to VESA and then restart, you will get a part functioning machine. 

Then if you install the Envy package, the nvidia video problem is corrected. The only thing that does not work is the DVD.  Does anyone have any suggestions as to how I can get DVD to work without going back to 6.10? as my wife will not be happy me rebuilding her brand new machine ;)

That is good news. 

Could you please list the hardware you have thats listed in the Dell invioce please.

I have not yet looked into the DVD issues yet.  But I will start to work on it this weekend.

Thanks

---

### Post by manchoy on 2007-07-18
Hi,

Let me figure it out tonight...hope it works ;)

---

### Post by ynef on 2007-07-18
I've managed to get Ubuntu working using the text mode install (alternative CD). My screen is running the native 1440x900 resolution and looks great. 

However, the nvidia driver is not working and I hope to avoid that third-party script that was in the first post (I hate circumventing the package manager). "nvidia-glx" plain just doesn't work, and "nvidia-glx-new" shuts down the computer immediately, and I am told that it shut down automatically due to overheating. That can't be right, so obviously the driver is doing things that it shouldn't. 

Also, the DVD doesn't work -- which is infuriating, since Ubuntu managed to get installed from the DVD! I have no idea why it doesn't work. Looking for either devices called "hd*" or "sd*" in /dev reports only my harddrive as sda and all of its partitions.

---

### Post by linux23dragon on 2007-07-18
> **ynef said:**
> I've managed to get Ubuntu working using the text mode install (alternative CD). My screen is running the native 1440x900 resolution and looks great. 

However, the nvidia driver is not working and I hope to avoid that third-party script that was in the first post (I hate circumventing the package manager). "nvidia-glx" plain just doesn't work, and "nvidia-glx-new" shuts down the computer immediately, and I am told that it shut down automatically due to overheating. That can't be right, so obviously the driver is doing things that it shouldn't. 

Also, the DVD doesn't work -- which is infuriating, since Ubuntu managed to get installed from the DVD! I have no idea why it doesn't work. Looking for either devices called "hd*" or "sd*" in /dev reports only my harddrive as sda and all of its partitions.

Support for the Nvidia Geforce-8600M GT is only included in the new Nvidia driver (100.14.11).  
Envy will be included in Ubuntu-7.10 (Due October) if that helps with getting you to try it out.

I must say that I never had any issues with Envy.  It is the only easy way of installing and seting up the Nvidia/ATI Graphics card Drivers.  Of course, you can try to download and install the driver yourself.  But you might be waiting until October otherwise.

---

### Post by aeo24 on 2007-07-18
I just ordered a 1420 which is nearly identical to the 1520. The information in the post is great and it looks like il have to get myself a copy of the alternate CD. Also i used envy on my desktop to install the driver it is awesome. Its so easy it isn't even funny. I would suggest getting it asap and saving yourself some trouble.

---

### Post by nick.inspiron6400 on 2007-07-18
I would love a orange/red 1520 and with Ubuntu!!

---

### Post by ynef on 2007-07-18
> **linux23dragon said:**
> Support for the Nvidia Geforce-8600M GT is only included in the new Nvidia driver (100.14.11).  
Envy will be included in Ubuntu-7.10 (Due October) if that helps with getting you to try it out.

I must say that I never had any issues with Envy.  It is the only easy way of installing and seting up the Nvidia/ATI Graphics card Drivers.  Of course, you can try to download and install the driver yourself.  But you might be waiting until October otherwise.

Whether Envy itself is included as a package isn't important to me -- what it does, however, is: installing a driver by circumventing the package manager is, in my opinion, not a clever thing to do. Once the kernel upgrades, you'll be stuck with a broken system and you need to run some script again.

However, I think I will try it anyway. It would be nice if everything on this computer (just got it today) except the DVD worked. Too bad about the DVD. :(

[edit] I just tried it, any my nvidia card is working perfectly as far as I can tell! Also, to anyone who thinks like I do about envy: it creates .deb files that can be uninstalled, so there's really nothing to worry about. Yes, you do have to run it when the kernel changes or when you upgrade to the next version of Ubuntu, but it is still a lot better than using the nvidia installer.

---

### Post by ynef on 2007-07-18
> **linux23dragon said:**
> 
HD Sound card (you need to recompile the "Alsa drivers", "Alsa libs" and "Alsa-tools" for better sound quality. You may also need "Alsa firmware").


Any information on how to do this and what version you've got working?

---

### Post by clint0r on 2007-07-18
> **linux23dragon said:**
> Could it be that you changed the resolution at the 24 bit colour section, but the xserver is set to run at 16 bit colour?

Edit:
Could you please write the list of hardware you have (built in the 1520 Notebook) from the Dell invioce please?

I was able to get the widescreen resolutions after installing envy.  Manually changed xorg.conf to boot up with 24 bit colour.

I don't have my invoice handy.

Dell Inspiron 1520 (brown)
Intel C2D 1.8GHz
2GB @ 667Mhz
Seagate Momentus 160GB 7200PM  (120GB that came with it is being used for external usb)
Intel Wireless N
Bluetooth
8x DVD Writer is the only hardware not working right now.

---

### Post by linux23dragon on 2007-07-18
> **ynef said:**
> Any information on how to do this and what version you've got working?

I recommend this Ubuntu Wiki link ([http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide) ) to compile and correctly set up your sound card drivers.  You can get the Alsa drivers and libs (1.0.14)  from [http://www.alsa-project.org/](http://www.alsa-project.org/)

---

### Post by ranjhith on 2007-07-18
> **ynef said:**
> I've managed to get Ubuntu working using the text mode install (alternative CD). My screen is running the native 1440x900 resolution and looks great. 

However, the nvidia driver is not working and I hope to avoid that third-party script that was in the first post (I hate circumventing the package manager).

Just bought a Ruby Red Inspiron 1520. But comes with a "Intel Graphics Media Accelerator X3100" & a 1680x1050 screen. :) Any config inputs to get this working? I see a lot of discussions for nVidia card. How is it with Intel?

---

### Post by bakketti on 2007-07-18
Thanks for all of the great info. I just got my new Inspiron 1420 up and running. Everything is working great minus the DVD and sound. I suspect the sound just needs some configuring. But the DVD... I have no clue...

---

### Post by ynef on 2007-07-19
> **linux23dragon said:**
> I recommend this Ubuntu Wiki link ([http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide) ) to compile and correctly set up your sound card drivers.  You can get the Alsa drivers and libs (1.0.14)  from [http://www.alsa-project.org/](http://www.alsa-project.org/)

Then I have two more questions:

[LIST=1]
[*]will compiling my own alsa drivers and stuff need to be updated manually once the kernel is upgraded (same "don't circumvent the package manager" line of thinking as before) and
[*]what can I expect to gain from this?
[/LIST]

The reason I ask the last question is that my sound "sort of " works with the modules that came with 7.04 -- however, I can't use them in games such as Savage or Neverball because there is too much static and lag. I guess I can live with that, but a big disappointment is that I can't use my microphone. I use VoIP instead of a real phone, so this is very important to me.

> **ranjhith said:**
> Just bought a Ruby Red Inspiron 1520. But comes with a "Intel Graphics Media Accelerator X3100" & a 1680x1050 screen. :) Any config inputs to get this working? I see a lot of discussions for nVidia card. How is it with Intel?

Nope, no idea. I specifically got a model with Nvidia since I know that their Linux drivers are good. So while I don't know if it will work for you, I just needed to set the display depth to 24 in my xorg.conf file. That worked with the "vesa" drivers too, actually.

---

### Post by linux23dragon on 2007-07-19
> **ynef said:**
> Then I have two more questions:

[LIST=1]
[*]will compiling my own alsa drivers and stuff need to be updated manually once the kernel is upgraded (same "don't circumvent the package manager" line of thinking as before) and[/LIST]

If the kernel modules is upgraded, then you will only need to recompile the Alsa-driver.  All the other Libs, Tools and Firmware can be left as is, since they were compiled aganst the same Alsa-driver.

Just to add:

It would be a good idea to keep the Alsa driver source in /usr/src.  Just in case you need it again.  


> **ynef said:**
> [*]what can I expect to gain from this?


The reason I ask the last question is that my sound "sort of " works with the modules that came with 7.04 -- however, I can't use them in games such as Savage or Neverball because there is too much static and lag. I guess I can live with that, but a big disappointment is that I can't use my microphone. I use VoIP instead of a real phone, so this is very important to me.

You will no longer have the static or lag issues you now currently have.    

I have not yet looked into Audio I/O  (like mic inputs) yet, so I cannot comment.  But it could be O.K. after you update and setup Alsa according to the WiKi instructions.

---

### Post by linux23dragon on 2007-07-19
Just posting to let you know that I have updated the first post to include Sound card driver instructions.

I'm still yet to find out how to set up Intel grathics cards with the Dell Notebook.  It might be possible to search for that information from other forums ATM.

Please post if you have any luck on the (Intel Grathics card) matter.  

Thanks

---

### Post by ynef on 2007-07-19
Well, I appear to have gotten the mic working. Sadly, I didn't carefully write down my steps, but I have done (at least!) the following:
[LIST]
[*]installed new ALSA drivers, libs and utils as suggested in the first post,
[*]added the following line to /etc/modprobe.d/alsa-base: "options snd-hda-intel model=ref",
[*]rebooted with the mic plugged in during bootup and
[*]written "sudo alsactl names" and "sudo alsactl store",
[/LIST]

I restarted between each step, and can now select a whole lot more in the mixer than before. My mic works if I have the following settings: 

Recording tab: full InMux and InVol
Switches tab: ADCMux enabled (don't know what it does)
Options tab: Digital Input Soucrse: Digital Mic 1 (the mic is, AFAIK, not digital) and Input Source: Mic

[edit] Keeping the mic plugged in during boot (at least now during a reboot since the post was made) did not seem to be important to the overall success.

---

### Post by linux23dragon on 2007-07-19
> **ynef said:**
> Well, I appear to have gotten the mic working. 

Excellent :)

I take it that your games sound a lot nicer too?

Now Its time to get the DVD burner working ;)

I'll Be doing a lot research on it tomorrow night, but I won't update the post until Sunday (due to testing).

We might need to blacklist unneeded kernel driver modules, so I've got to get it right first time.

---

### Post by ynef on 2007-07-19
> **linux23dragon said:**
> 
I take it that your games sound a lot nicer too?


Well, the sound is a lot nicer, but not completely flawless: when many "voices" should be heard, the sound will get choppy and laggy -- the effect can best be described as water ripples. But hey: it works, and I can use VoIP -- I'm happy. :-)

> **linux23dragon said:**
> 
Now Its time to get the DVD burner working ;)

I'll Be doing a lot research on it tomorrow night, but I won't update the post until Sunday (due to testing).

We might need to blacklist unneeded kernel driver modules, so I've got to get it right first time.

I've tried to (in the BIOS) disable the Flash Cache Module and set the SATA to ATA operation instead of the default, but no such luck. Do you have Ubuntu 6.10 installed too? If it is so simple that 7.04 loads a module that conflicts with the right one, a simple "diff" between the modules loaded in 6.10 and 7.04 should do it. I fear that the module itself has changed, though.

---

### Post by ynef on 2007-07-19
An important note on the microphone: the Sound Recorder program in the Applications menu under Sound & Video should **not** be used for testing purposes. It resets parts of the mixer (most importantly it reduces InMux to 0 and disables ADCMux) which will cause the mic to not work. Instead, install Audacity using the command "sudo apt-get install audacity" in a terminal. It can record and do a lot more.

---

### Post by linux23dragon on 2007-07-19
> **ynef said:**
> 
I've tried to (in the BIOS) disable the Flash Cache Module and set the SATA to ATA operation instead of the default, but no such luck. Do you have Ubuntu 6.10 installed too? If it is so simple that 7.04 loads a module that conflicts with the right one, a simple "diff" between the modules loaded in 6.10 and 7.04 should do it. I fear that the module itself has changed, though.

Yep I've already tried the BIOS options too.  

Could the old SATA driver be included in the 2.6.20 kernel too?

I don't have  Ubuntu 6.10 installed ATM, as it has been upgraded to 7.04.  But it might be worth booting the 6.10 live CD.

---

### Post by jmjosebest on 2007-07-19
Hello, someone has configured the WiFi N ??

---

### Post by manchoy on 2007-07-19
Finally, Ubuntu 7.04 is living in my dell 1520. hooooooooooooooooooooooooorray.......Next step going to install my nvidia GC ;) . Thanks for all guidances here

---

### Post by bakketti on 2007-07-20
linux23dragon,

I'm on a Inspiron 1420. Tried running through the sound card steps in your first post. I downloaded the packages and ran your commands. So far, no luck with getting sound up and running.  I wonder if the 1420 is running a slightly different sound card. Unfortunately, I'm not an expert on sound and linux so I am at a loss.

Thanks a bunch for your help though. I'm very happy that everything else is working on my new machine! :)

Also on a side note, if our laptops models are also coming preloaded with Ubuntu on them, why are we having problems with our DVDs and sound cards? Assuming we have the same hardware as the Ubuntu machines, I'd assume everything would work out of the box.

---

### Post by linux23dragon on 2007-07-20
> **bakketti said:**
> linux23dragon,

I'm on a Inspiron 1420. Tried running through the sound card steps in your first post. I downloaded the packages and ran your commands. So far, no luck with getting sound up and running.  I wonder if the 1420 is running a slightly different sound card. Unfortunately, I'm not an expert on sound and linux so I am at a loss.

Thanks a bunch for your help though. I'm very happy that everything else is working on my new machine! :)

Also on a side note, if our laptops models are also coming preloaded with Ubuntu on them, why are we having problems with our DVDs and sound cards? Assuming we have the same hardware as the Ubuntu machines, I'd assume everything would work out of the box.


Dell Inspiron 1420 eh? :)
Well I've just updated the Alsa instructions, test them while is hot :)

---

### Post by odin1965 on 2007-07-20
Has anyone tried 7.04 on the 1520 with Intel X3000 graphics card? I ordered mine that way as I did not really need any high end graphics. I see that one of the desktop Ubuntu Dell sold in the US has this GC.

---

### Post by odin1965 on 2007-07-20
Also, to echo what bakketti asked, Why so many problems with identical hardware to the 1420 which comes with 7.04 preinstalled. Has anyone got one of these yet? How is it working?

---

### Post by Oofda33 on 2007-07-20
I just ordered my 1720 :).  I just loaded Ubuntu on one of my co-workers Compaq Presario 6000 and found the following post by "soapytheclown":

[http://ubuntuforums.org/showthread.php?t=458164&highlight=v6000]("http://ubuntuforums.org/showthread.php?t=458164&highlight=v6000")

  This information worked like a champ when installing on the Compaq.  I am wondering if it may have some helpful information for installing Ubuntu on a Dell.


This statement in particular:

1. Installing and booting

A quick forum search will tell you that in order to boot the live cd for installation requires the "noapic" or "nolapic" flag to be used. 

This works but like me im sure alot of people had no idea what this option does however i found that it it stops usb hotplugging to work, which means unless the device (ie usb stick or mouse) is plugged in at startup it wont work, however this can be fixed using another flag with the noapic which is: "irqpoll noirqdebug"

[COLOR="DarkRed"]so.. turn you computer on make sure it boots form the cd when the option to start the live disc comes on press the F6 key and type in:

"noapic irqpoll noirqdebug" [without the quotes] followed by return, it should boot up and install as normal![/COLOR]

could someone try this out and post their results please.

Thanks

---

### Post by linux23dragon on 2007-07-21
> **Oofda33 said:**
> I just ordered my 1720 :).  I just loaded Ubuntu on one of my co-workers Compaq Presario 6000 and found the following post by "soapytheclown":

[http://ubuntuforums.org/showthread.php?t=458164&highlight=v6000]("http://ubuntuforums.org/showthread.php?t=458164&highlight=v6000")

  This information worked like a champ when installing on the Compaq.  I am wondering if it may have some helpful information for installing Ubuntu on a Dell.


This statement in particular:

1. Installing and booting

A quick forum search will tell you that in order to boot the live cd for installation requires the "noapic" or "nolapic" flag to be used. 

This works but like me im sure alot of people had no idea what this option does however i found that it it stops usb hotplugging to work, which means unless the device (ie usb stick or mouse) is plugged in at startup it wont work, however this can be fixed using another flag with the noapic which is: "irqpoll noirqdebug"

[COLOR="DarkRed"]so.. turn you computer on make sure it boots form the cd when the option to start the live disc comes on press the F6 key and type in:

"noapic irqpoll noirqdebug" [without the quotes] followed by return, it should boot up and install as normal![/COLOR]

could someone try this out and post their results please.

Thanks

I've tried those kernel options, and others as well, with no results.  Does the  Compaq have the same Intel  SATA controllers?

IDE interface: Intel Corporation Mobile IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation Mobile SATA AHCI Controller (rev 02)

---

### Post by linux23dragon on 2007-07-21
> **ynef said:**
> Well, the sound is a lot nicer, but not completely flawless: when many "voices" should be heard, the sound will get choppy and laggy -- the effect can best be described as water ripples. But hey: it works, and I can use VoIP -- I'm happy. :-)



I've tried to (in the BIOS) disable the Flash Cache Module and set the SATA to ATA operation instead of the default, but no such luck. Do you have Ubuntu 6.10 installed too? If it is so simple that 7.04 loads a module that conflicts with the right one, a simple "diff" between the modules loaded in 6.10 and 7.04 should do it. I fear that the module itself has changed, though.



I can't see any ich8m detection in the kernel logs.  Are we meant to have ich8m, or is it missing?
And I think we are meant to have the E-IDE driver working to.

So we should have /dev/hda  device node for our DVD burner.

---

### Post by linux23dragon on 2007-07-21
> **linux23dragon said:**
> I can't see any ich8m detection in the kernel logs.  Are we meant to have ich8m, or is it missing?
And I think we are meant to have the E-IDE driver working to.

So we should have /dev/hda  device node for our DVD burner.


And here is some cuts from the current kernel log:-

Jul 21 01:46:01 kernel: [    1.707360] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jul 21 01:46:01 kernel: [    1.707365] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx  

Here you can see that the E-IDE driver gets loaded, but there is no information about /dev/hda (The DVD burner) anywhere in the kernel log.  And there should be a ICH8M device/driver information too, but its not loaded or detected.



Here is part of the kernel log showing how the SATA hard drive is set up (mixed with USB and other devices).  All is working so far.




Jul 21 00:44:29  kernel: [    3.025538] libata version 2.20 loaded.
Jul 21 00:44:29  kernel: [    3.027320] ahci 0000:00:1f.2: version 2.1
Jul 21 00:44:29  kernel: [    3.027345] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 17 (level, low) -> IRQ 17
Jul 21 00:44:29  kernel: [    3.032485] ieee1394: Initialized config rom entry `ip1394'
Jul 21 00:44:29  kernel: [    3.033308] USB Universal Host Controller Interface driver v3.0
Jul 21 00:44:29  kernel: [    4.028649] ahci 0000:00:1f.2: nr_ports (3) and implemented port map (0x5) don't match
Jul 21 00:44:29  kernel: [    4.028668] PCI: Setting latency timer of device 0000:00:1f.2 to 64
Jul 21 00:44:29  kernel: [    4.028676] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x5 impl SATA mode
Jul 21 00:44:29  kernel: [    4.028678] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part
Jul 21 00:44:29  kernel: [    4.028757] ata1: SATA max UDMA/133 cmd 0xf884c900 ctl 0x00000000 bmdma 0x00000000 irq 17
Jul 21 00:44:29  kernel: [    4.028773] ata2: DUMMY
Jul 21 00:44:29  kernel: [    4.028830] ata3: SATA max UDMA/133 cmd 0xf884ca00 ctl 0x00000000 bmdma 0x00000000 irq 17
Jul 21 00:44:29  kernel: [    4.028840] scsi0 : ahci
Jul 21 00:44:29  kernel: [    4.512252] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 21 00:44:29  kernel: [    4.513723] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
Jul 21 00:44:29  kernel: [    4.513727] ata1.00: ATA-7: ST9120822AS, 3.CDD, max UDMA/133
Jul 21 00:44:29  kernel: [    4.513729] ata1.00: 234441648 sectors, multi 8: LBA48 NCQ (depth 31/32)
Jul 21 00:44:29  kernel: [    4.514526] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
Jul 21 00:44:29  kernel: [    4.514529] ata1.00: configured for UDMA/133
Jul 21 00:44:29  kernel: [    4.514534] scsi1 : ahci
Jul 21 00:44:29  kernel: [    4.514656] scsi2 : ahci
Jul 21 00:44:29  kernel: [    4.823979] ata3: SATA link down (SStatus 0 SControl 300)
Jul 21 00:44:29  kernel: [    4.824071] scsi 0:0:0:0: Direct-Access     ATA      ST9120822AS      3.CD PQ: 0 ANSI: 5
Jul 21 00:44:29  kernel: [    4.824994] b44.c:v1.01 (Jun 16, 2006)
Jul 21 00:44:29  kernel: [    4.825014] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Jul 21 00:44:29  kernel: [    4.828553] eth0: Broadcom 4400 10/100BaseT Ethernet 00:19:b9:80:a7:fb
Jul 21 00:44:29  kernel: [    4.828638] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 20 (level, low) -> IRQ 19
Jul 21 00:44:29  kernel: [    4.828648] PCI: Setting latency timer of device 0000:00:1a.0 to 64
Jul 21 00:44:29  kernel: [    4.828652] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Jul 21 00:44:29  kernel: [    4.828760] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Jul 21 00:44:29  kernel: [    4.828792] uhci_hcd 0000:00:1a.0: irq 19, io base 0x00006f20
Jul 21 00:44:29  kernel: [    4.828888] usb usb1: configuration #1 chosen from 1 choice
Jul 21 00:44:29  kernel: [    4.828911] hub 1-0:1.0: USB hub found
Jul 21 00:44:29  kernel: [    4.828916] hub 1-0:1.0: 2 ports detected
Jul 21 00:44:29  kernel: [    4.833479] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
Jul 21 00:44:29  kernel: [    4.833490] sda: Write Protect is off
Jul 21 00:44:29  kernel: [    4.833492] sda: Mode Sense: 00 3a 00 00
Jul 21 00:44:29  kernel: [    4.833505] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 21 00:44:29  kernel: [    4.833545] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
Jul 21 00:44:29  kernel: [    4.833552] sda: Write Protect is off
Jul 21 00:44:29  kernel: [    4.833554] sda: Mode Sense: 00 3a 00 00
Jul 21 00:44:29  kernel: [    4.833567] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 21 00:44:29  kernel: [    4.833571]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 sda7<6>ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 20
Jul 21 00:44:29  kernel: [    4.932012] PCI: Setting latency timer of device 0000:00:1a.1 to 64

---

### Post by linux23dragon on 2007-07-21
I don't think that the Jmicron driver is installed in 2.6.20-16-generic.  This could be it.

Now Its time to configure the kernel to support the Jmicron driver, and recompile the kernel.

Edit:  This is beyond the scope of most end users so I wont update the post on how to do it.  I myself am going to wait for an kernel upgrade or the next Ubuntu release.  
         In short.
        Too hard :(

The funny thing is, that other distributions work well with this Notebook.  Although the kernels are a little older (2.6.17, 2.6.18, 2.6.19)

---

### Post by manchoy on 2007-07-21
Regarding installing the NVIDIA gc, i followed this instruction:

1) sudo apt-get install linux-generic

2) sudo apt-get install nvidia-glx-new

3) sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

4) sudo nvidia-xconfig --no-composite

But, with no luck, i cant manage to start my x server with new xorg.conf, my laptop model is Dell inspiron 1520, Linux23dragon...plz help me...... i even change the depth to 24, still cannot ;(

---

### Post by linux23dragon on 2007-07-21
> **manchoy said:**
> Regarding installing the NVIDIA gc, i followed this instruction:

1) sudo apt-get install linux-generic

2) sudo apt-get install nvidia-glx-new

3) sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

4) sudo nvidia-xconfig --no-composite

But, with no luck, i cant manage to start my x server with new xorg.conf, my laptop model is Dell inspiron 1520, Linux23dragon...plz help me...... i even change the depth to 24, still cannot ;(


Why have you not installed Envy?

Try this:

Ctrl+Alt+F2

Login as a user.

Restore your /etc/X11/xorg.conf_backup :

sudo mv  /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

You now should be able to restart the X server.  Install Envy (the URL Link is found on my first post).  Then just run Envy (fond in  the start menu "System tools").

Envy will do all the hard work for you automatically.  That Includes setting up  xorg.conf.

---

### Post by linux23dragon on 2007-07-21
**I've found a fix for the DVD player thanks to tak.ack**

Post has been updated with the DVD fix.

Enjoy :)

---

### Post by manchoy on 2007-07-21
ya...i downloaded the ENVY, but when i install it...it said Error: Dependency is not satisfiable: module-assistant. Thats why i follow another instruction here.. [http://albertomilone.com/latest_nvidia_udsf_feisty.html]("http://albertomilone.com/latest_nvidia_udsf_feisty.html")

---

### Post by linux23dragon on 2007-07-22
> **manchoy said:**
> ya...i downloaded the ENVY, but when i install it...it said Error: Dependency is not satisfiable: module-assistant. Thats why i follow another instruction here.. [http://albertomilone.com/latest_nvidia_udsf_feisty.html]("http://albertomilone.com/latest_nvidia_udsf_feisty.html")

Try this:

sudo apt-get install build-essential

---

### Post by manchoy on 2007-07-22
Ya, finally i managed to install ENVY. Previously I installed it through terminal, but in the middle it failed. Afterwards the envy found in my system tools menu. Thus, i lauched ENVY and start install it, so weird about installation ;) But is fun!!! It seems like everything in my linux looks blurry. I'm not sure whether is my settings problem or what. But at least i fixed the blurry after read this thread [ here ]("http://ubuntuforums.org/showthread.php?t=99482")

I just installed BERYL, it looks cool but it doesn't looks smooth? Is there any options to play around?

---

### Post by carminez on 2007-07-22
Has anyone figured out how to get the Wireless to work?

I know its a Intel IPW3945, and I came across some pages with infor/drivers

[http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

But I haven't had any luck with them yet. 

BTW, thanks to linux23dragon for all you research into getting things working for the Inspiron 1520!

---

### Post by linux23dragon on 2007-07-23
> **carminez said:**
> Has anyone figured out how to get the Wireless to work?

I know its a Intel IPW3945, and I came across some pages with infor/drivers

[http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

[http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

But I haven't had any luck with them yet. 

BTW, thanks to linux23dragon for all you research into getting things working for the Inspiron 1520!


I am able to use the default restricted driver for for the WiFi mini card.  But the WiFi connections sometimes work or don't work.  I've tried playing around with BIOS settings too.


Is the default restricted driver (currently) in use?

---

### Post by linux23dragon on 2007-07-23
I've posted more updates.

Included Dell support links
Intel Graphics and WiFi info
DVD Burner DMA fix (and other testing options)
A lot more clean ups

Check it out :)

---

### Post by carminez on 2007-07-23
> **linux23dragon said:**
> I am able to use the default restricted driver for for the WiFi mini card.  But the WiFi connections sometimes work or don't work.  I've tried playing around with BIOS settings too.


Is the default restricted driver (currently) in use?

No, the default restricted driver is not in use, I have no eth1, just eth0. I was getting some weird system hanging when I would login, and then see a NetworkManager error, probably related. At this point I'm thinking of trying a clean install with the 7.04 alt cd and see if I can get better results that way, I had previously gone with 6.10 to 7.04.

---

### Post by odin1965 on 2007-07-23
I received my 1520 this morning and am attempting to install 7.07. I decided to use the alternate CD method mentioned here. It installs and I get to where it restarts and the X server fails. Problem is, mine has the Intel video and when I edit the xorg.conf, it already has "vesa" set as the driver and still doesn't work. Any sugestions?

---

### Post by linux23dragon on 2007-07-23
> **odin1965 said:**
> I received my 1520 this morning and am attempting to install 7.07. I decided to use the alternate CD method mentioned here. It installs and I get to where it restarts and the X server fails. Problem is, mine has the Intel video and when I edit the xorg.conf, it already has "vesa" set as the driver and still doesn't work. Any sugestions?

Please check to see if (or add) /etc/X11/xorg.conf has Horizontal and Vertical refresh rates under  Section "Monitor" 





Also try to reduce the screen resolution to 800x600

I understand that the VESA is broken for some ATI cards, its possible that the same is true with some Intel cards.  

I still need to look deeper into this.  I'll be on the look out for more info


EDIT Have a go with the intel  driver "i810" it just might work.

---

### Post by linux23dragon on 2007-07-23
> **carminez said:**
> No, the default restricted driver is not in use, I have no eth1, just eth0. I was getting some weird system hanging when I would login, and then see a NetworkManager error, probably related. At this point I'm thinking of trying a clean install with the 7.04 alt cd and see if I can get better results that way, I had previously gone with 6.10 to 7.04.

That also happened to me when I was setting up a Dell Inspiron 6400.  I ended up reinstalling Ubuntu in the end.  It resolved the issues for me.

I think that the restricted Intel driver should be in use, once you first boot the Ubuntu-6.10 live CD.  As I remember that it was running (after I had installed 6.10).

---

### Post by linux23dragon on 2007-07-25
> **carminez said:**
> No, the default restricted driver is not in use, I have no eth1, just eth0. I was getting some weird system hanging when I would login, and then see a NetworkManager error, probably related. At this point I'm thinking of trying a clean install with the 7.04 alt cd and see if I can get better results that way, I had previously gone with 6.10 to 7.04.


I want to look into trying to install the Intel drivers from here [http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

I have been able to use the WiFi (WEP enabled), but if I turn off the Notebook for a few hours, the WiFi will no longer connect to the external router.

I have to find a way to fix this issue.  Also the Dell links might be of good use here.

---

### Post by linux23dragon on 2007-07-25
> **linux23dragon said:**
> I want to look into trying to install the Intel drivers from here [http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

I have been able to use the WiFi (WEP enabled), but if I turn off the Notebook for a few hours, the WiFi will no longer connect to the external router.

I have to find a way to fix this issue.  Also the Dell links might be of good use here.



Ah,


There is bug fixes (yay) from here: [http://ipw3945.sourceforge.net/#issues](http://ipw3945.sourceforge.net/#issues)

Edit:  I want to try this out ASAP.  But the owner is so happy with the work I've done already, he can't give it back.  So I can only work on it this weekend.  Could someone try this fix out and report your findings please?

---

### Post by Oofda on 2007-07-25
Does anyone know if the 1520 and 1720 have the same stuff in them?  I am hoping to use this thread to load Ubuntu on my second hard drive in my 1720.  Thank you so much for helping everyone out linux23dragon, kudo's to you.  I have been playing with Ubuntu for a little while now but don't have the skills to fix stuff with the terminal without someone telling me how.  I love Linux and have gotten a few of my workmates to install it and try it out.  Every one of them are so surprised, they never knew it was so good.  

Keep up the good work dragon!  you're a great asset to this forum.

---

### Post by odin1965 on 2007-07-25
You'd have to go thru the dell setup page for the 1520 and the 1720 and see if the same hardware is available for both. I ordered a 1520 and was able to keep the hardware the smae as the 1420 that comes with Ubuntu. Make sure you get the Intel wireless. The 1720 is probably the same as the other two.

---

### Post by Davron on 2007-07-26
So complicated... Didn't have any problems with SUSE 9 on Inspiron 5150.

Now I'm stuck with ubuntu + 1520.

I tried about 10 times. Screen problem - can't see anything

I've tried it through virtual pc AND manually.


> Please remove the disc, close the trey (if any) 
and press ENTER to concinue -
[http://img209.imageshack.us/img209/7559/ubuntuissueqc7.jpg](http://img209.imageshack.us/img209/7559/ubuntuissueqc7.jpg)


I did - nothing happens. 

Any ideas?
Thanks

---

### Post by Davron on 2007-07-26
Hi, I got a problem here  - 

I was installing ubuntu and when it was creating a new partition - I canceled it since it didn't seem to be doing anything,

then I tried to boot vista again but it won't boot!

Any ideas? Am I screwed?

Thanks

---

### Post by odin1965 on 2007-07-26
I have my 1520 working with the Intel Graphic, but only at 1024X768 for the moment, and still have to fix a few sound problems. 

As I noted earlier, I elected to use the 7.04 alternate CD to install. Upon reboot, my xserver was broken, even with the driver set to vesa in xorg.conf. I followed the link at the first of this thread to the files Dell installs;

[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Add-on_Packages](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Add-on_Packages)

There I found xserver-xorg-video-i810_1.7.4-0ubuntu2_i386.deb and 915resolution_0.5.3-0ubuntu1_i386.deb which are both installed on Dells with the Intel video. These are both newer than the ones listed in my repositories. Possibly they are backported from Gutsy or maybe I could have just added the correct repository. What I did was google both and came up with the
following 2 links;

[http://people.ubuntu.com/~kyle/crestline-i810/xserver-xorg-video-i810_1.7.4-0ubuntu2_i386.deb](http://people.ubuntu.com/~kyle/crestline-i810/xserver-xorg-video-i810_1.7.4-0ubuntu2_i386.deb)
[http://people.ubuntu.com/~kyle/915resolution_0.5.3-0ubuntu1_i386.deb](http://people.ubuntu.com/~kyle/915resolution_0.5.3-0ubuntu1_i386.deb)

So I downloaded them to my home folder using wget;
wget
[http://people.ubuntu.com/~kyle/crestline-i810/xserver-xorg-video-i810_1.7.4-0ubuntu2_i386.deb](http://people.ubuntu.com/~kyle/crestline-i810/xserver-xorg-video-i810_1.7.4-0ubuntu2_i386.deb)
wget [http://people.ubuntu.com/~kyle/915resolution_0.5.3-0ubuntu1_i386.deb](http://people.ubuntu.com/~kyle/915resolution_0.5.3-0ubuntu1_i386.deb)

Then I insalled them using dpkg

sudo dpkg -i xserver-xorg-video-i810_1.7.4-0ubuntu2_i386.deb
sudo dpkg -i 915resolution_0.5.3-0ubuntu1_i386.deb

and then;

startx

and it works. 

Now just to get sound fixed and widescreen resolutions. My wireless works with Intel restricted driver out of the box and I was able to install the conexant modem driver from the Dell link above.

---

### Post by odin1965 on 2007-07-26
I had sound out of the box (well after fixing the Intel video) on my 1520, but it would stop working. Worked for MP3's, but when I played a DVD, there would be no sound. And after that there would be no sound at all until I restarted.
  Now, after adding the restricted Modem Driver from the Dell website, [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Add-on_Packages](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Add-on_Packages), there is no sound at all. The volume control applet says there are no devices to control.

Results from  lspci -nvvv are;

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio
Controller (rev 02)
	Subsystem: Dell Unknown device 01f1
	Flags: fast devsel, IRQ 20
	Memory at fe9fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

I followed the ALSA wiki up to 'sudo modprode snd-hda-intel' and when I type this I don't get message in return and the sound still doesn't work. I tried turning off the restricted modem drivers and restarting but no luck.

---

### Post by odin1965 on 2007-07-26
Sound is back after using Synaptic to uninstall the conexant modem driver,
hsfmodem_7.60.00.06oem_i386.deb that came from the Dell website. I can live without the modem for a while if I can get sound to work. I don't have a DVD here to test the sound, but I'm sure it still doesn't work.

---

### Post by linux23dragon on 2007-07-26
> **Davron said:**
> Hi, I got a problem here - 
 
I was installing ubuntu and when it was creating a new partition - I canceled it since it didn't seem to be doing anything,
 
then I tried to boot vista again but it won't boot!
 
Any ideas? Am I screwed?
 
Thanks
 
 
Hi
 
You might want to boot your Notebook with the Vista installation disk. It might have some recovery tool on it.
 
If that does not work out, then reinstall Windows or install Ubuntu and run Windows in a VM.
 
However, I can't support Vista in any way. I don't have any copy of Vista at all.
 
If you want to resize the Windows pation table (using the partion tool on the Ubuntu instalation disk), then you should use the defrag and scandisk tools in Windows first.  However, I'm not sure if this Idea will still work with Vista.

---

### Post by linux23dragon on 2007-07-26
> **odin1965 said:**
> I have my 1520 working with the Intel Graphic, but only at 1024X768 for the moment, and still have to fix a few sound problems. 
 
As I noted earlier, I elected to use the 7.04 alternate CD to install. Upon reboot, my xserver was broken, even with the driver set to vesa in xorg.conf. I followed the link at the first of this thread to the files Dell installs;
 
[http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Add-on_Packages](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Add-on_Packages)
 
There I found xserver-xorg-video-i810_1.7.4-0ubuntu2_i386.deb and 915resolution_0.5.3-0ubuntu1_i386.deb which are both installed on Dells with the Intel video. These are both newer than the ones listed in my repositories. Possibly they are backported from Gutsy or maybe I could have just added the correct repository. What I did was google both and came up with the
following 2 links;
 
[http://people.ubuntu.com/~kyle/crestline-i810/xserver-xorg-video-i810_1.7.4-0ubuntu2_i386.deb](http://people.ubuntu.com/~kyle/crestline-i810/xserver-xorg-video-i810_1.7.4-0ubuntu2_i386.deb)
[http://people.ubuntu.com/~kyle/915resolution_0.5.3-0ubuntu1_i386.deb](http://people.ubuntu.com/~kyle/915resolution_0.5.3-0ubuntu1_i386.deb)
 
So I downloaded them to my home folder using wget;
wget
[http://people.ubuntu.com/~kyle/crestline-i810/xserver-xorg-video-i810_1.7.4-0ubuntu2_i386.deb](http://people.ubuntu.com/~kyle/crestline-i810/xserver-xorg-video-i810_1.7.4-0ubuntu2_i386.deb)
wget [http://people.ubuntu.com/~kyle/915resolution_0.5.3-0ubuntu1_i386.deb](http://people.ubuntu.com/~kyle/915resolution_0.5.3-0ubuntu1_i386.deb)
 
Then I insalled them using dpkg
 
sudo dpkg -i xserver-xorg-video-i810_1.7.4-0ubuntu2_i386.deb
sudo dpkg -i 915resolution_0.5.3-0ubuntu1_i386.deb
 
and then;
 
startx
 
and it works. 
 
Now just to get sound fixed and widescreen resolutions. My wireless works with Intel restricted driver out of the box and I was able to install the conexant modem driver from the Dell link above.
 
 
Thanks for the report.  I'll be updating the post later on today with your findings :)
 
I've been working on updating the Intel WiFi driver.  I'm still testing it out.  If its any good then I'll update WiFi information later on today too.

---

### Post by Davron on 2007-07-26
> **linux23dragon said:**
> Hi
 
You might want to boot your Notebook with the Vista installation disk. It might have some recovery tool on it.
 
If that does not work out, then reinstall Windows or install Ubuntu and run Windows in a VM.
 
However, I can't support Vista in any way. I don't have any copy of Vista at all.
 
If you want to resize the Windows pation table (using the partion tool on the Ubuntu instalation disk), then you should use the defrag and scandisk tools in Windows first.  However, I'm not sure if this Idea will still work with Vista.

Hey thanks. I got it working, I deleted ubuntu's partition using widows xp cd and then rebooted and fixed partition errors with the checkdisk,

now I have only Vista.

I gave it another try, I used Wubi - still no luck, Ubuntu 7.04 "has been installed successfully" but it won't boot - 

It seems like it's working but then after the ubuntu loading bar - the screen turns black,


I've never used this so I am kind of new, even though I am pretty good with computers. 

So I thought I should do something like xorg.conf editing - but couldn't even find the config file (using windows),

Ideas?

Thanks a bunch!

---

### Post by odin1965 on 2007-07-27
Quote;
There I found xserver-xorg-video-i810_1.7.4-0ubuntu2_i386.deb and 915resolution_0.5.3-0ubuntu1_i386.deb which are both installed on Dells with the Intel video. These are both newer than the ones listed in my repositories. Possibly they are backported from Gutsy or maybe I could have just added the correct repository. 

Once I was up and running, I enabled the fiesty-proposed and the backports repositories in Synaptic and both these are now available in the correct versions from Synaptic. Here is my /etc/apt/sources.list for reference

# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

---

### Post by linux23dragon on 2007-07-27
More updates

I've added: 

  [SIZE=2][B][U]Ubuntu Hardware and Software Support for Feisty
[/U][/B]
[SIZE=1]That should cover lots of things.


[/SIZE][/SIZE]

---

### Post by linux23dragon on 2007-07-28
> **Davron said:**
> Hey thanks. I got it working, I deleted ubuntu's partition using widows xp cd and then rebooted and fixed partition errors with the checkdisk,

now I have only Vista.

I gave it another try, I used Wubi - still no luck, Ubuntu 7.04 "has been installed successfully" but it won't boot - 

It seems like it's working but then after the ubuntu loading bar - the screen turns black,


I've never used this so I am kind of new, even though I am pretty good with computers. 

So I thought I should do something like xorg.conf editing - but couldn't even find the config file (using windows),

Ideas?

Thanks a bunch!

Are you using a Intel Graphics card?

Perhaps the last update I've done (in the first post) might help you out.


I don't think Windows supports other file systems.

---

### Post by linux23dragon on 2007-07-28
> **manchoy said:**
> text based? Is there any option for text based installation?


Just updated the URL information

---

### Post by odin1965 on 2007-07-28
In trying to set the i8xx driver to widescreen using 915resolution, I came across this thread;
[http://ubuntuforums.org/showthread.php?t=351647&highlight=intel+widescreen+laptop](http://ubuntuforums.org/showthread.php?t=351647&highlight=intel+widescreen+laptop)

Near the end it suggests using the newer intel driver xserver-xorg-video intel in synaptic. I installed it, which removed the older driver, and, BINGO, 1280x800 by default. I still can't get the 14440x900, but 1280x800 is about all MY eyes can handle on a 15" monitor. I will keep trying to get the higher res, but it's not so important now.

I can't figure why Dell is using the older driver and the 915 hack, rather than the nwer driver. Is it possible the 1420 is not widescreen, so they didn't need the new one? Anyone got one to test and post here?

---

### Post by linux23dragon on 2007-07-28
> **odin1965 said:**
> In trying to set the i8xx driver to widescreen using 915resolution, I came across this thread;
[http://ubuntuforums.org/showthread.php?t=351647&highlight=intel+widescreen+laptop](http://ubuntuforums.org/showthread.php?t=351647&highlight=intel+widescreen+laptop)

Near the end it suggests using the newer intel driver xserver-xorg-video intel in synaptic. I installed it, which removed the older driver, and, BINGO, 1280x800 by default. I still can't get the 14440x900, but 1280x800 is about all MY eyes can handle on a 15" monitor. I will keep trying to get the higher res, but it's not so important now.

I can't figure why Dell is using the older driver and the 915 hack, rather than the nwer driver. Is it possible the 1420 is not widescreen, so they didn't need the new one? Anyone got one to test and post here?


Thanks for reporting that odin1965.  I've updated the first post to include the setup fixes.

EDIT: Does this help in getting even higher resolutions? 

```

  sudo dpkg-reconfigure -phigh xserver-xorg
```That idea was from [drakos]("http://ubuntuforums.org/member.php?u=282229") :- "This should allow you to pick *intel* instead of i810 and pick the resolutions you want. Then just reboot X and it should work."

[http://ubuntuforums.org/showthread.php?t=511607](http://ubuntuforums.org/showthread.php?t=511607)

---

### Post by carminez on 2007-07-29
Anyone get wireless to work with the previous post's links?

I noticed in Vista the wireless card shows as 4965AGN, and came across this [http://intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi](http://intellinuxwireless.org/?p=iwlwifi&n=howto-iwlwifi)

But I'm not having any luck with it, missing files etc when doing make, and I'm years removed from building stuff, so if anyone can put out detailed instructions so that I don't have debug, it would be appreciated. 

Also haven't got webcam to work... might involve something with the spca5xx driver... [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by linux23dragon on 2007-07-30
[SIZE=3][COLOR=Red](30th-07-07)[/COLOR]
[/SIZE]                                                 [SIZE=3][COLOR=Red]Volunteer needed to maintain this forum!![/COLOR][/SIZE]
  
 [SIZE=3][COLOR=Red]I had to give the 1520 Notebook back to its owner. And I think it is best if someone who owns this Very Nice Notebook, should continue on with this work. You only need to finish the Intel WiFi, and Intel Graphics configurations.[/COLOR][/SIZE]

---

### Post by odin1965 on 2007-07-30
> **linux23dragon said:**
> [SIZE=3][COLOR=Red](30th-07-07)[/COLOR]
[/SIZE]                                                 [SIZE=3][COLOR=Red]Volunteer needed to maintain this forum!![/COLOR][/SIZE]
  
 [SIZE=3][COLOR=Red]I had to give the 1520 Notebook back to its owner. And I think it is best if someone who owns this Very Nice Notebook, should continue on with this work. You only need to finish the Intel WiFi, and Intel Graphics configurations.[/COLOR][/SIZE]

  Would give it a try. I can't really comment on getting the Intell wirelss to work, though. Mine worked perfect and even used the restricted driver right from the get go, with no configuration at all.
 I am continuing to refine the Intel graphics, though. I tried sudo dpkg-reconfigure -phigh xserver-xorg, and picked 1440x900, but it still doesn't let me use that res for some reason. It did enable a few really od resolutions that I didn't pick though, like 1280x1280 (????). Plus it enabled the ability to rotate the display on mine.

---

### Post by alex1974 on 2007-07-30
Hi everybody,

i#m just installing ubuntu on my inspiron 1520.
Just one question so far:
what exactly is dell media direct? does it work with ubuntu?
it seems it needs a partition? how big? and where? at the end or the beginning. Does it matter?

When I just formatted the harddrive during installation I found that the size is 149,5 Gb? Thats 10,5 GB less than it should be. I can't select them. Is this the hidden Dell Partition for restoring and utillity and media direct?

Hope somebody can help I#m stucked.
Thanks Alex

---

### Post by Davron on 2007-07-30
> **alex1974 said:**
> Hi everybody,

When I just formatted the harddrive during installation I found that the size is 149,5 Gb? Thats 10,5 GB less than it should be. I can't select them. Is this the hidden Dell Partition for restoring and utillity and media direct?



Well all hard drives are "less than they should be". Even iPods, Zens, MemorySticks, SD cards etc. I'd say about 5% is always not available.

I don't know how media direct works but it might be on some hidden partition (?).

---

### Post by carminez on 2007-07-30
> **odin1965 said:**
> Would give it a try. I can't really comment on getting the Intell wirelss to work, though. Mine worked perfect and even used the restricted driver right from the get go, with no configuration at all.
 I am continuing to refine the Intel graphics, though. I tried sudo dpkg-reconfigure -phigh xserver-xorg, and picked 1440x900, but it still doesn't let me use that res for some reason. It did enable a few really od resolutions that I didn't pick though, like 1280x1280 (????). Plus it enabled the ability to rotate the display on mine.

I don't understand how some people have gotten the Intel Wireless to work with restricted drivers. I have done about 6 different installations of ubuntu at this point on this 1520, starting with 6.10 and upgrading to 7.04, to straight installs to 7.04, and no luck. 

How exactly are you telling it to load the restricted drivers? Should I bother trying Ndiswrapper for this?

---

### Post by linux23dragon on 2007-07-30
> **odin1965 said:**
> Would give it a try. I can't really comment on getting the Intell wirelss to work, though. Mine worked perfect and even used the restricted driver right from the get go, with no configuration at all.
I am continuing to refine the Intel graphics, though. I tried sudo dpkg-reconfigure -phigh xserver-xorg, and picked 1440x900, but it still doesn't let me use that res for some reason. It did enable a few really od resolutions that I didn't pick though, like 1280x1280 (????). Plus it enabled the ability to rotate the display on mine.
 
 
Thanks odin1965. That is one up for Intel graphics.
 
Is there anyone who is willing to go for the WiFi setup?
 
Please email me if you are still want to give this project a go :)

---

### Post by linux23dragon on 2007-07-31
> **carminez said:**
> I don't understand how some people have gotten the Intel Wireless to work with restricted drivers. I have done about 6 different installations of ubuntu at this point on this 1520, starting with 6.10 and upgrading to 7.04, to straight installs to 7.04, and no luck. 

How exactly are you telling it to load the restricted drivers? Should I bother trying Ndiswrapper for this?


                                                [FONT=Times New Roman, serif][SIZE=3]If you have the Intel 3945 abg WiFi, then you don't need  Ndiswrapper at all.  The driver should be called by the kernel every time you boot up the Notebook.   Have you tried to see if you have the restricted kernel modules installed?[/SIZE][/FONT]
 

 [FONT=Times New Roman, serif][SIZE=3]Use the Synaptic package manager to search for:- linux-restricted-modules[/SIZE][/FONT]
 

 [FONT=Times New Roman, serif][SIZE=3]Make sure the versions you have installed [/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=3] are [/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=3]2.6.20.*[/SIZE][/FONT]

---

### Post by carminez on 2007-07-31
> **linux23dragon said:**
> [FONT=Times New Roman, serif][SIZE=3]If you have the Intel 3945 abg WiFi, then you don't need  Ndiswrapper at all.  The driver should be called by the kernel every time you boot up the Notebook.   Have you tried to see if you have the restricted kernel modules installed?[/SIZE][/FONT]
 

 [FONT=Times New Roman, serif][SIZE=3]Use the Synaptic package manager to search for:- linux-restricted-modules[/SIZE][/FONT]
 

 [FONT=Times New Roman, serif][SIZE=3]Make sure the versions you have installed [/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=3] are [/SIZE][/FONT][FONT=Times New Roman, serif][SIZE=3]2.6.20.*[/SIZE][/FONT]

Yes, they were installed. That's why I was confused to how it worked for some people and not me. 

When I checked the logs I don't even see a mention of trying to load the driver, and when I do a modprobe ipw3945 it tells me it doesn't find the device. The wireless is turned on in the BIOS, I can easily boot into Vista and it sees the card and connects. But Vista sees it as the 4965 I mentioned previously. Is the 3945 and 4965 the same card, just Vista recognizes it differently? I did come across something on intellinuxwireless.com that mentioned sometimes the driver for 4965 worked for people and sometimes the 3945 did.

---

### Post by odin1965 on 2007-07-31
> **carminez said:**
> Yes, they were installed. That's why I was confused to how it worked for some people and not me. 

When I checked the logs I don't even see a mention of trying to load the driver, and when I do a modprobe ipw3945 it tells me it doesn't find the device. The wireless is turned on in the BIOS, I can easily boot into Vista and it sees the card and connects. But Vista sees it as the 4965 I mentioned previously. Is the 3945 and 4965 the same card, just Vista recognizes it differently? I did come across something on intellinuxwireless.com that mentioned sometimes the driver for 4965 worked for people and sometimes the 3945 did.

What is your output from lspci? This is the relevant portion with my intel wireless card.

0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation Unknown device 1020
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at fe8ff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

---

### Post by carminez on 2007-08-01
> **odin1965 said:**
> What is your output from lspci? This is the relevant portion with my intel wireless card.

0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
	Subsystem: Intel Corporation Unknown device 1020
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at fe8ff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>


```

00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 0c)
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, fast devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Root Port (rev 0c) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fa000000-feafffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
        Capabilities: [88] Subsystem: Dell Unknown device 01f1
        Capabilities: [80] Power Management version 3
        Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [a0] Express Root Port (Slot+) IRQ 0

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 6f20 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 6f00 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 0, IRQ 21
        Memory at fed1c400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0b, subordinate=0b, sec-latency=0
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Dell Unknown device 01f1
        Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0c, subordinate=0c, sec-latency=0
        Memory behind bridge: f9f00000-f9ffffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Dell Unknown device 01f1
        Capabilities: [a0] Power Management version 2

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0d, subordinate=0e, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: f9c00000-f9efffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [90] Subsystem: Dell Unknown device 01f1
        Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 6f80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 6f60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 6f40 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at fed1c000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
        Memory behind bridge: f9b00000-f9bfffff
        Capabilities: [50] Subsystem: Dell Unknown device 01f1

00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 02)
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 6fa0 [size=16]

00:1f.2 SATA controller: Intel Corporation Mobile SATA AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
        I/O ports at 6eb0 [size=8]
        I/O ports at 6eb8 [size=4]
        I/O ports at 6ec0 [size=8]
        I/O ports at 6ec8 [size=4]
        I/O ports at 6ee0 [size=32]
        Memory at febfb800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/2 Enable-
        Capabilities: [70] Power Management version 3
        Capabilities: [a8] #12 [0010]

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
        Subsystem: Dell Unknown device 01f1
        Flags: medium devsel, IRQ 10
        Memory at febfb700 (32-bit, non-prefetchable) [size=256]
        I/O ports at 10c0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0407 (rev a1) (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at ef00 [size=128]
        [virtual] Expansion ROM at fea00000 [disabled] [size=128K]
        Capabilities: [60] Power Management version 2
        Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [78] Express Endpoint IRQ 0

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, fast devsel, latency 64, IRQ 17
        Memory at f9bfe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 05) (prog-if 10 [OHCI])
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at f9bfd800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: [dc] Power Management version 2

03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) (prog-if 01)
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at f9bfd400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 12)
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 64, IRQ 4
        Memory at f9bfd500 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 64, IRQ 4
        Memory at f9bfd600 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, medium devsel, latency 64, IRQ 4
        Memory at f9bfd700 (32-bit, non-prefetchable) [size=256]
        Capabilities: [80] Power Management version 2

0c:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
        Subsystem: Intel Corporation Unknown device 1120
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at f9ffe000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: [c8] Power Management version 3
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Endpoint IRQ 0

```

FYI, my machine has came with the Bluetooth installed.

---

### Post by carminez on 2007-08-01
The messages in the logs referring to the wireless only appear after I do a modprobe ipw3945, otherwise there is no mention of the wireless. 

```

Aug  1 01:01:29 bigredmachine kernel: [ 2322.676000] ieee80211_crypt: registered algorithm 'NULL'
Aug  1 01:01:29 bigredmachine kernel: [ 2322.684000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Aug  1 01:01:29 bigredmachine kernel: [ 2322.684000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Aug  1 01:01:29 bigredmachine kernel: [ 2322.728000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
Aug  1 01:01:29 bigredmachine kernel: [ 2322.728000] ipw3945: Copyright(c) 2003-2006 Intel Corporation

```

```

Aug  1 01:01:29 bigredmachine kernel: [ 2322.684000] ieee80211: 802.11 data/management/control stack, git-1.1.13
Aug  1 01:01:29 bigredmachine kernel: [ 2322.684000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
Aug  1 01:01:29 bigredmachine kernel: [ 2322.728000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
Aug  1 01:01:29 bigredmachine kernel: [ 2322.728000] ipw3945: Copyright(c) 2003-2006 Intel Corporation

```

---

### Post by odin1965 on 2007-08-02
> **carminez said:**
> ```

(snip)
0c:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
        Subsystem: Intel Corporation Unknown device 1120
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at f9ffe000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: [c8] Power Management version 3
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Endpoint IRQ 0

```

FYI, my machine has came with the Bluetooth installed.

Anyone else got one with bluetooth and wireless that works? I ordered mine without because the Ubuntu 1420 didn't have it, so I assumed there was some problem with it.

You could open it up and remove the bluetooth card and see if it recognizes the wireless. :) I'm more used to desktops so I have no idea how hard that would be.

---

### Post by Naci Sey on 2007-08-02
Really appreciate this thread. My new Dell Inspiron 1520 arrives in a couple of weeks and I intend to add ubuntu to it. Thanks to the info here, I'll start with 6.10 and likely wait for a later version than 7.04.

Re the graphics card tips, there's no mention of the **Intel® Graphics Media Accelerator X3000**. which is the default option and the one I chose. Do the tips above also apply to it, or only to the Nvidia GeForce cards?

---

### Post by odin1965 on 2007-08-02
> **Naci Sey said:**
> Really appreciate this thread. My new Dell Inspiron 1520 arrives in a couple of weeks and I intend to add ubuntu to it. Thanks to the info here, I'll start with 6.10 and likely wait for a later version than 7.04.

Re the graphics card tips, there's no mention of the **Intel® Graphics Media Accelerator X3000**. which is the default option and the one I chose. Do the tips above also apply to it, or only to the Nvidia GeForce cards?

Mine has the Intel X3000, so all my posts with regard to intel graphics are in relation to this card. AS you will read it works great with a little work. I started right with 7.04. If I were doing it again, I would go directly with the newer intel driver that I mention in this thread. I also provided a link to another thread with a lot of Intel widescreen info.

---

### Post by carminez on 2007-08-02
> **odin1965 said:**
> Anyone else got one with bluetooth and wireless that works? I ordered mine without because the Ubuntu 1420 didn't have it, so I assumed there was some problem with it.

You could open it up and remove the bluetooth card and see if it recognizes the wireless. :) I'm more used to desktops so I have no idea how hard that would be.

I don't know how keen I am to opening up my new laptop to play around with it ;)

I did disable the bluetooth in the BIOS and it didn't seem to make any difference with my wireless network card. 

I did notice that the wireless card seems to be on IRQ 10 and there is another device using IRQ 10, could that be the issue? 

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
        Subsystem: Dell Unknown device 01f1
        Flags: medium devsel, IRQ 10
        Memory at febfb700 (32-bit, non-prefetchable) [size=256]
        I/O ports at 10c0 [size=32]

Is there a way to force the use of a different IRQ for a device????

---

### Post by kimastergeorge on 2007-08-03
> **carminez said:**
> ```

0c:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
        Subsystem: Intel Corporation Unknown device 1120
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at f9ffe000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: [c8] Power Management version 3
        Capabilities: http://ubuntuforums.org/showthread.php?p=3069765[d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [e0] Express Endpoint IRQ 0

```

FYI, my machine has came with the Bluetooth installed.

I got that same output, and I figure that the part I left in is the important part.

I know that I got a 4965agn wireless card instead of the standard abg card, and I didn't get bluetooth.

I'm currently checking if this thread: [http://ubuntuforums.org/showthread.php?p=3069765](http://ubuntuforums.org/showthread.php?p=3069765) will be of any help, and also checking [http://intellinuxwireless.org/](http://intellinuxwireless.org/)

I'll post back here if I get any results.

---

### Post by stncttr908 on 2007-08-05
I have a 1420 and my ethernet is not detected upon installing 6.10 in order to upgrade to 7.04.  Any ideas?  I tried the drivers on the Broadcom site but I haven't had any luck.

---

### Post by oliparcol on 2007-08-06
I have juste installed Ubuntu 7.04 directly with alternate CD. I have to boot in recuperation mode to change nv to vesa driver in xorg.conf. Everything is working well exept the boot screen and logout screen isn't showing, someone has the same problem ?

Thanks,
Oliparcol

---

### Post by kimastergeorge on 2007-08-06
Oliparcol,

I have the same problem (except I used Envy to install the Nvidia drivers--I recommend that you do, too).

---

### Post by oliparcol on 2007-08-06
same, I used envy too so I've got nVidia latest drivers but nothing changed, I still have the problem.

---

### Post by alex1974 on 2007-08-07
I got my laptop with the vvidia setup and thanks to this forum it worked smooth so far. Even if I'm not a linux-guru I just followed the instructions. I think thats a good point for ubuntu and this forum.

Some questions though are unanswered. What is with the unmaskirq and the io-? support. Should we enable it? It was mentioned in the first post but there was no clue what to do.
Thanks so long,
Alex

---

### Post by jbizzler on 2007-08-07
I'm worried about the future of Linux on this notebook. I know I can't install Fedora 7 on it because that doesn't have piix, and when I tried using the 7.10 kernel on 7.04, that removed piix support as well. ata_piix doesn't seem to do the trick for either of these. Any ideas?

---

### Post by linux23dragon on 2007-08-07
> **jbizzler said:**
> I'm worried about the future of Linux on this notebook. I know I can't install Fedora 7 on it because that doesn't have piix, and when I tried using the 7.10 kernel on 7.04, that removed piix support as well. ata_piix doesn't seem to do the trick for either of these. Any ideas?

Not supported or not configured in the kernel?  could it be black listed?
I'll have to find out for myself to see if there is a way to include the piix if its not there.  Could of been replaced by another driver too.

---

### Post by linux23dragon on 2007-08-08
> **linux23dragon said:**
> Not supported or not configured in the kernel?  could it be black listed?
I'll have to find out for myself to see if there is a way to include the piix if its not there.  Could of been replaced by another driver too.

OK,  Here is a bug report about the missing piix (replaced by ata_piix).

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119905](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/119905)

There is a patch you can try out.  Its possible that we might get this fix in Ubuntu-7.10.

Patch location:-
[http://launchpadlibrarian.net/8656831/patch](http://launchpadlibrarian.net/8656831/patch)

So please test and send your reports.

---

### Post by linux23dragon on 2007-08-08
> **alex1974 said:**
> Some questions though are unanswered. What is with the unmaskirq and the io-? support. Should we enable it? It was mentioned in the first post but there was no clue what to do.
Thanks so long,
Alex

[SIZE="4"]IO_support to 32-bit[/SIZE]
The DVD burner is running in 16bit mode but can run in 32bit mode.  


[SIZE="4"]unmaskirq[/SIZE]:-
Turning on this option will allow Linux to unmask other interrupts while processing a disk interrupt. 
This option lets Linux attend to other interrupt-related tasks (i.e., network traffic) while waiting for your disk to return with the data it asked for.

You can find more information about the hdpram from linuxdevcenter.com:-

[http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html?page=1](http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html?page=1)

I will be updating the post to include all of the options later on this week :)

---

### Post by odin1965 on 2007-08-08
My wireless on my 1520 will no longer connect to any access points, open or protected. Driver seems fine, radio on, can see access points, bu Network Manager just spins and the balls stay grey, and it says "attempting to connect to xxxxxx". Output from lshw -C network, iwconfig and iwlist scan seem fine, see below.

> 
andy@delllap:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0c:00.0
       logical name: eth1
       version: 02
       serial: 00:1b:77:5f:e5:23
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 multicast=yes wireless=unassociated
       resources: iomemory:fe8ff000-fe8fffff irq:17
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:83:8f:a5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 ip=192.168.0.111 latency=64 multicast=yes
       resources: iomemory:fe5fe000-fe5fffff irq:17
andy@delllap:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0c:00.0
       logical name: eth1
       version: 02
       serial: 00:1b:77:5f:e5:23
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 multicast=yes wireless=unassociated
       resources: iomemory:fe8ff000-fe8fffff irq:17
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:83:8f:a5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 ip=192.168.0.111 latency=64 multicast=yes
       resources: iomemory:fe5fe000-fe5fffff irq:17
andy@delllap:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"eascan1"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:17:9A:4D:AA:79   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:34   Missed beacon:0

andy@delllap:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:17:9A:4D:AA:79
                    ESSID:"eascan1"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=88/100  Signal level=-45 dBm  Noise level=-45 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 20ms ago


Thing is, occasionally it will work. Have search this forum for a week trying to fix this, but all other threads seem driver related and that doesn't seem to be the problem here. Have tried Wicd and Wifi Radar too and they did not work either.

---

### Post by alex1974 on 2007-08-08
Found another one!
Sound is not working? Well the login sound is audible and seems normal.
But I can't listen to musik. I even can't figure out wether my sound card is installed and working. It's too confusing for me.
lspci -v says:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

What does that mean? What is the name of my sound card. Even tried the wiki link but didn't solve it.

---

### Post by linux23dragon on 2007-08-08
> **alex1974 said:**
> Found another one!
Sound is not working? Well the login sound is audible and seems normal.
But I can't listen to musik. I even can't figure out wether my sound card is installed and working. It's too confusing for me.
lspci -v says:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Unknown device 01f1
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

What does that mean? What is the name of my sound card. Even tried the wiki link but didn't solve it.

Thanks for the input.  I'll be changing the Audio section so that you will now only build and configure the audio system.  I might need to include the Alsa-Firmware as well. 

The "options snd-hda-intel model=ref" for /etc/modprobe.d/alsa-base is correct but you can have "options snd-hda-intel model=3stack" or "options snd-hda-intel model=8stack".

Currently I have been able to get very good sound out put with most audio Apps (mp3, wave, ogg, avi) but OpenAL and RT Audio Apps seems to lag still.  I'm not sure If I can fix that, but I'll be working out a way to improve thoses issues too.

---

### Post by linux23dragon on 2007-08-09
Updated the Sound Audio section.

---

### Post by carminez on 2007-08-09
> **linux23dragon said:**
> [SIZE="4"]IO_support to 32-bit[/SIZE]
The DVD burner is running in 16bit mode but can run in 32bit mode.  


[SIZE="4"]unmaskirq[/SIZE]:-
Turning on this option will allow Linux to unmask other interrupts while processing a disk interrupt. 
This option lets Linux attend to other interrupt-related tasks (i.e., network traffic) while waiting for your disk to return with the data it asked for.

You can find more information about the hdpram from linuxdevcenter.com:-

[http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html?page=1](http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html?page=1)

I will be updating the post to include all of the options later on this week :)

I was having issues copying  2GB file off a DVD, kept failing at about 448MB. Adding io32_support = 1 to /etc/hdparm.conf solved that problem. Thanks!

Still no webcam or wifi :(

---

### Post by DarthTibault on 2007-08-10
I prefer debs over a normal install from source, so instead of doing:
```
./configure
make
sudo make install
```
I'd prefer to use checkinstall to create a deb:
```
./configure
make
sudo checkinstall
```
The reason I'm mentioning this here is because I'm uncertain of some of the extra lines:
```
sudo install -v -m755 -d /usr/share/doc/alsa-plugins-1.0.14 
sudo install -v -m644 doc/{README*,*.txt} \
                    /usr/share/doc/alsa-plugins-1.0.14
```
What exactly do they do? Just copy the docs?
I want to be sure a checkinstall will work. I'd normally just try and see, but my laptop is still in preproduction :(
(waiting sucks)

---

### Post by linux23dragon on 2007-08-10
> **DarthTibault said:**
> 
The reason I'm mentioning this here is because I'm uncertain of some of the extra lines:
```
sudo install -v -m755 -d /usr/share/doc/alsa-plugins-1.0.14 
sudo install -v -m644 doc/{README*,*.txt} \
                    /usr/share/doc/alsa-plugins-1.0.14
```
What exactly do they do? Just copy the docs?)

Correct,  The doc commands copy the README*,*txt to /usr/shre/doc/alsa* and makes sure that the file  permissions are correctly set.   You can omit the doc install commands if you want.

> **DarthTibault said:**
> I prefer debs over a normal install from source, so instead of doing:
```
./configure
make
sudo make install
```
I'd prefer to use checkinstall to create a deb:
```
./configure
make
sudo checkinstall
```

Can someone test that out, so I can update the post please?
This would indeed be a better choice for package management. 

Thanks DarthTibault, for your input.

---

### Post by linux23dragon on 2007-08-10
Updated the DVD Burner section

---

### Post by alex1974 on 2007-08-11
Ich habe versucht den Sound anhand der neuen Anleitung zu installieren. Funktioniert aber noch nicht. Login-Sound funktioniert, aber Rhythmbox hängt sich auf beim Versuch Lieder abzuspielen.

Mit dmesg finde ich folgendes:
[   19.064000] ALSA /home/alex/Desktop/alsa-driver-1.0.14/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:558: hda_intel: azx_get_response timeout, switching to polling mode...
[   19.388000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[   20.068000] ALSA /home/alex/Desktop/alsa-driver-1.0.14/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:564: hda_intel: azx_get_response timeout, switching to single_cmd mode...

Habe ich da was übersehen bei der Installation?
Da sollte ich glaube nicht /home/alex/Desktop... stehen, oder?

In der Anleitung steht download der Versionen 1.0.14, meine alsa-base und utils ist aber 1.0.13-3ubuntu laut synaptic.

---

### Post by linux23dragon on 2007-08-11
> **alex1974 said:**
> Ich habe versucht den Sound anhand der neuen Anleitung zu installieren. Funktioniert aber noch nicht. Login-Sound funktioniert, aber Rhythmbox hängt sich auf beim Versuch Lieder abzuspielen.

Mit dmesg finde ich folgendes:
[   19.064000] ALSA /home/alex/Desktop/alsa-driver-1.0.14/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:558: hda_intel: azx_get_response timeout, switching to polling mode...
[   19.388000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[   20.068000] ALSA /home/alex/Desktop/alsa-driver-1.0.14/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:564: hda_intel: azx_get_response timeout, switching to single_cmd mode...

Habe ich da was übersehen bei der Installation?
Da sollte ich glaube nicht /home/alex/Desktop... stehen, oder?

In der Anleitung steht download der Versionen 1.0.14, meine alsa-base und utils ist aber 1.0.13-3ubuntu laut synaptic.


I don't know how to read German, but I have seen that kernel log message before.

The Alsa drivers still work, but the kernel thinks that the Alsa drivers are in the Alsa driver directory located at /home/alex/Desktop/alsa-driver-1.0.14/*/../hda_intel.c:564: hda_intel.


Maybe, the driver install is incomplete.  I'm looking into this now.


I did not look into that issue since the audio was working O.K.

Rhythmbox should work O.k but can seem to be slow.  It does appear to be finishing both the ripping and encoding, before it moves on to the next track.  

Other ripper software will Rip one track and move on to rip another, before the encoding is finished.  This gives the impression that it is working faster.

---

### Post by ynef on 2007-08-11
> **alex1974 said:**
> Ich habe versucht den Sound anhand der neuen Anleitung zu installieren. Funktioniert aber noch nicht. Login-Sound funktioniert, aber Rhythmbox hängt sich auf beim Versuch Lieder abzuspielen.

Mit dmesg finde ich folgendes:
[   19.064000] ALSA /home/alex/Desktop/alsa-driver-1.0.14/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:558: hda_intel: azx_get_response timeout, switching to polling mode...
[   19.388000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[   20.068000] ALSA /home/alex/Desktop/alsa-driver-1.0.14/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:564: hda_intel: azx_get_response timeout, switching to single_cmd mode...

Habe ich da was übersehen bei der Installation?
Da sollte ich glaube nicht /home/alex/Desktop... stehen, oder?

In der Anleitung steht download der Versionen 1.0.14, meine alsa-base und utils ist aber 1.0.13-3ubuntu laut synaptic.

I'll answer this in English, since I'll make fewer stupid mistakes that way. :)

Synaptic won't know what version of the ALSA software you're using, if you compile it yourself and install it (as this thread recommends). If you type "alsactl -v" in a terminal, what version does it report?

Are you certain that you have installed the codecs needed for MP3 playback? Does any other sound work for you? Since sound seems to be working, that might be the problem. Install all the gstreamer plugins you can find using synaptic.

---

### Post by alex1974 on 2007-08-11
first I'm sorry for the german. I was just confused but you guessed the problem right.

alsactl -v
alsactl version 1.0.14

it shows the version I installed
can I just uninstall and install again properly?

---

### Post by linux23dragon on 2007-08-11
> **ynef said:**
> I'll answer this in English, since I'll make fewer stupid mistakes that way. :)

Synaptic won't know what version of the ALSA software you're using, if you compile it yourself and install it (as this thread recommends). If you type "alsactl -v" in a terminal, what version does it report?

Are you certain that you have installed the codecs needed for MP3 playback? Does any other sound work for you? Since sound seems to be working, that might be the problem. Install all the gstreamer plugins you can find using synaptic.


Ah, I  found this at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Can you try adding this option to /etc/modprobe.d/alsa-base

```

options snd-hda-intel probe_mask=1
```

Also see what output you get with this command:

```

cat /proc/asound/card0/codec\#*
```

---

### Post by alex1974 on 2007-08-11
alex@alex-laptop:~$ cat /proc/asound/card0/codec\#*
Codec: SigmaTel STAC9205
Address: 0
Vendor Id: 0x838476a0
Subsystem Id: 0x102801f1
Revision Id: 0x100204
Default PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=0
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1

Do you want to see the rest? Thats a lot of stuff.

As far as I see all available gstreamer plugins are installed.

---

### Post by linux23dragon on 2007-08-11
> **alex1974 said:**
> alex@alex-laptop:~$ cat /proc/asound/card0/codec\#*
Codec: SigmaTel STAC9205
Address: 0
Vendor Id: 0x838476a0
Subsystem Id: 0x102801f1
Revision Id: 0x100204
Default PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=0
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1

Do you want to see the rest? Thats a lot of stuff.

No, thats cool.  Do you still see this same message when you reboot?

```

ALSA /home/alex/Desktop/alsa-driver-1.0.14/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:558: hda_intel: azx_get_response timeout, switching to polling mode...
```

---

### Post by alex1974 on 2007-08-11
after rebbot I see the same output.

in the dmesg and in the cat... code

---

### Post by alex1974 on 2007-08-11
I installed with ./configure make make install. Is there a way to remove them and install again.
Maybe that solves the problem.
They are not listed in the synaptic.

---

### Post by DarthTibault on 2007-08-11
> **alex1974 said:**
> I installed with ./configure make make install. Is there a way to remove them and install again.
I don't know what you should do to fix your problems, but to answer your question: to uninstall a 'sudo make install' all you have to do is 'sudo make uninstall' from the same directory. This of course only works if you still have that directory (else you have to ./configure and make again). (which is why I prefer debs).

---

### Post by alex1974 on 2007-08-11
sudo make uninstall is not working. Can I just delete them?
I downloaded checkinstall and will do it from now on with checkinstall.

---

### Post by linux23dragon on 2007-08-11
> **alex1974 said:**
> sudo make uninstall is not working. Can I just delete them?
I downloaded checkinstall and will do it from now on with checkinstall.

Yea,  I think the checkinstall is a better option too :)
I did not know about checkinstall until now (thanks to DarthTibault).

Also, There is good news about the web cam.  It looks like we can use the UVC-Linux drivers.  The main developer has written a patch (for the 1420) that might get the Web cam to work correctly with the 1520 as well.
 
[https://lists.berlios.de/pipermail/linux-uvc-devel/2007-August/001949.html](https://lists.berlios.de/pipermail/linux-uvc-devel/2007-August/001949.html)

Any one want to give this a try?
Not sure were to get the patch from.
EDIT:  here is the SVN download URL:

svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk

---

### Post by alex1974 on 2007-08-11
I couldn't uninstall the alsa-stuff so I deleted it and reinstalled it in usr/src/alsa using checkinstall.
But still dmesg shows that the drivers were searched for at Desktop.

P.S.: For the instruction on page 1:
./configure did just work with sudo
sudo make checkinstall did just work as sudo checkinstall
No .deb were build. Error output occured.

---

### Post by linux23dragon on 2007-08-11
> **alex1974 said:**
> I couldn't uninstall the alsa-stuff so I deleted it and reinstalled it in usr/src/alsa using checkinstall.
But still dmesg shows that the drivers were searched for at Desktop.

P.S.: For the instruction on page 1:
./configure did just work with sudo
sudo make checkinstall did just work as sudo checkinstall
No .deb were build. Error output occured.

OK, so all we need to do is:-  sudo checkinstall?
Oh.  OK, thanks for the report.

EDIT:  I've changed the instructions.  Are they correct?

---

### Post by DarthTibault on 2007-08-11
> **alex1974 said:**
> I couldn't uninstall the alsa-stuff so I deleted it and reinstalled it in usr/src/alsa using checkinstall.
But still dmesg shows that the drivers were searched for at Desktop.

P.S.: For the instruction on page 1:
./configure did just work with sudo
sudo make checkinstall did just work as sudo checkinstall
No .deb were build. Error output occured.

Has anyone had success with the checkinstall method? As I said before, I don't have the laptop yet, so I can't try it myself.
I have no idea what is causing your problems... what exactly did you do? Something extra you haven't mentioned yet?

EDIT: wait, I've seen the "No .deb were build. Error output occurred."-error before, are you sure ./configure was successful?

> **linux23dragon said:**
> OK, so all we need to do is:-  sudo checkinstall?
Oh.  OK, thanks for the report.

EDIT:  I've changed the instructions.  Are they correct?

I hadn't noticed you changed the first post, but it looks OK now: you never do ./configure with sudo, and you use 'sudo checkinstall' (no make) instead of 'sudo make install'. Just as I wrote a few posts back.

---

### Post by carminez on 2007-08-11
> **linux23dragon said:**
> 
Also, There is good news about the web cam.  It looks like we can use the UVC-Linux drivers.  The main developer has written a patch (for the 1420) that might get the Web cam to work correctly with the 1520 as well.
 
[https://lists.berlios.de/pipermail/linux-uvc-devel/2007-August/001949.html](https://lists.berlios.de/pipermail/linux-uvc-devel/2007-August/001949.html)

Any one want to give this a try?
Not sure were to get the patch from.
EDIT:  here is the SVN download URL:

svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk

This webcam fix doesn't entirely work. 

I downloaded the source, added the section for /* OmniVision OEM Dell Notebook */ to the uvc_driver.c file  down on line 1661...
```

	/* OmniVision OEM Dell Notebook */
	{ .match_flags		= USB_DEVICE_ID_MATCH_DEVICE
				| USB_DEVICE_ID_MATCH_INT_INFO,
	  .idVendor		= 0x05a9,
	  .idProduct		= 0x2640,
	  .bInterfaceClass	= USB_CLASS_VIDEO,
	  .bInterfaceSubClass	= 1,
	  .bInterfaceProtocol	= 0,
	  .driver_info		= UVC_QUIRK_PROBE_MINMAX },

```

and compiled and then copied the uvcvideo.ko file over the one in /lib/modules/2.6.20-16-generic/usb/media. After rebooting I still got the same messages in the log, but I did have a /dev/video0 now which I didn't have before. So I went and tried Camorama to see if it would work, and it said it couldn't connect to /dev/video0, but, the blue light did flash near the webcam when Camorama started and exited, so there is some progress. I replied to the developer with the feedback, let's see if anything happens.

I was able to install kdetv and when I run it I can see video, which is promising and it seems to be using Video4Linux2, but not what more to make of this. I'll have to see if I can get any other webcam apps to work.

UPDATE:
I installed aMSN and the webcam worked. I had another computer with a webcam at home, so I connected both with MSN accounts and was able to see video on both ends. Problem is that since I wasn't able to test this yet with another person on the other end, I'm not sure if the sound works as well, but so far so good.

---

### Post by linux23dragon on 2007-08-11
> **carminez said:**
> This webcam fix doesn't entirely work. 

I downloaded the source, added the section for /* OmniVision OEM Dell Notebook */ to the uvc_driver.c file  down on line 1661...
```

	/* OmniVision OEM Dell Notebook */
	{ .match_flags		= USB_DEVICE_ID_MATCH_DEVICE
				| USB_DEVICE_ID_MATCH_INT_INFO,
	  .idVendor		= 0x05a9,
	  .idProduct		= 0x2640,
	  .bInterfaceClass	= USB_CLASS_VIDEO,
	  .bInterfaceSubClass	= 1,
	  .bInterfaceProtocol	= 0,
	  .driver_info		= UVC_QUIRK_PROBE_MINMAX },

```

and compiled and then copied the uvcvideo.ko file over the one in /lib/modules/2.6.20-16-generic/usb/media. After rebooting I still got the same messages in the log, but I did have a /dev/video0 now which I didn't have before. So I went and tried Camorama to see if it would work, and it said it couldn't connect to /dev/video0, but, the blue light did flash near the webcam when Camorama started and exited, so there is some progress. I replied to the developer with the feedback, let's see if anything happens.

I was able to install kdetv and when I run it I can see video, which is promising and it seems to be using Video4Linux2, but not what more to make of this. I'll have to see if I can get any other webcam apps to work.

UPDATE:
I installed aMSN and the webcam worked. I had another computer with a webcam at home, so I connected both with MSN accounts and was able to see video on both ends. Problem is that since I wasn't able to test this yet with another person on the other end, I'm not sure if the sound works as well, but so far so good.

Thats great :)

I understand that the UVC-Linux drivers only supports V4L2, and a lot of Web cam applications only support V4L.

But the good news is,  people have sent in some patch fixes for some of them:

[http://svn.berlios.de/wsvn/linux-uvc](http://svn.berlios.de/wsvn/linux-uvc)

You will also need to upgrade to Ekiga-2.0.4 or higher too (if you need to use it).

---

### Post by alex1974 on 2007-08-12
Hello, sorry yesterday it was late and I got confused. It's ./configure make and sudo checkinstall.
I happend to install the alsa stuff on the desktop and sudo make uninstall didn't work. So I just deleted them. Then I reinstalled them in /usr/src/alsa (this time with checkinstall). But still dmesg shows it looks for them on the desktop?!?

Any solution?

---

### Post by linux23dragon on 2007-08-12
> **alex1974 said:**
> Hello, sorry yesterday it was late and I got confused. It's ./configure make and sudo checkinstall.
I happend to install the alsa stuff on the desktop and sudo make uninstall didn't work. So I just deleted them. Then I reinstalled them in /usr/src/alsa (this time with checkinstall). But still dmesg shows it looks for them on the desktop?!?

Any solution?

I'm now trying out this:

```

./configure \
   --with-moddir=/lib/modules/`uname -r`/kernel/drivers/sound \
   --with-kernel=/lib/modules/`uname -r`/build \
   --with-sequencer=yes \
   --with-oss=yes \
   --with-isapnp=no \
   --with-cards=all
```

---

### Post by linux23dragon on 2007-08-12
> **linux23dragon said:**
> I'm now trying out this:

```

./configure \
   --with-moddir=/lib/modules/`uname -r`/kernel/drivers/sound \
   --with-kernel=/lib/modules/`uname -r`/build \
   --with-sequencer=yes \
   --with-oss=yes \
   --with-isapnp=no \
   --with-cards=all
```

This configure option works better for me, so I've updated the Alsa driver section.  You now should be able to "copy paste" all the commands, please test :)

I have tested the web cam as well.  it works well :)

---

### Post by linux23dragon on 2007-08-12
UPDATE

Added note about Web Cam and WiFi digital mic is working well to BTW.

[COLOR="Blue"]There is a Wireless hard switch on the bottom left hand side of the Notebook (Next to a small LED).[/COLOR]

---

### Post by linux23dragon on 2007-08-13
> **stncttr908 said:**
> I have a 1420 and my ethernet is not detected upon installing 6.10 in order to upgrade to 7.04.  Any ideas?  I tried the drivers on the Broadcom site but I haven't had any luck.

Have a look at this specker s post here:-


[http://ubuntuforums.org/showthread.php?t=509408&highlight=1420&page=9](http://ubuntuforums.org/showthread.php?t=509408&highlight=1420&page=9)

---

### Post by linux23dragon on 2007-08-13
> **oliparcol said:**
> I have juste installed Ubuntu 7.04 directly with alternate CD. I have to boot in recuperation mode to change nv to vesa driver in xorg.conf. Everything is working well exept the boot screen and logout screen isn't showing, someone has the same problem ?

Thanks,
Oliparcol

Has this "boot screen and logout screen" issue been fixed?
Its possible that the /boot/grub/menu1st  needs updateing.


Try this command (I think):-

EDIT: try this

 [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_display_Splash_Image_for_GRUB_menu_on_boot-up](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_display_Splash_Image_for_GRUB_menu_on_boot-up)

---

### Post by linux23dragon on 2007-08-13
Web Cam install instructions are now included.

Is alsa driver instructions working O.K?

---

### Post by linux23dragon on 2007-08-13
> **DarthTibault said:**
> Has anyone had success with the checkinstall method? As I said before, I don't have the laptop yet, so I can't try it myself.
I have no idea what is causing your problems... what exactly did you do? Something extra you haven't mentioned yet?

EDIT: wait, I've seen the "No .deb were build. Error output occurred."-error before, are you sure ./configure was successful?


I've added the correct $(uname -r) to the configure options. 

Hope that helps

---

### Post by linux23dragon on 2007-08-14
UPDATE (14-Aug-07) Fixed a lot of bad bugs.  Made note of the Checkinstall commands.

I just installed Ubuntu on my desktop to test the commands. 

Sorry :(

EDIT: checkinstall is now removed.

---

### Post by oliparcol on 2007-08-14
> **linux23dragon said:**
> Has this "boot screen and logout screen" issue been fixed?
Its possible that the /boot/grub/menu1st  needs updateing.


Try this command (I think):-

EDIT: try this

 [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_display_Splash_Image_for_GRUB_menu_on_boot-up](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_display_Splash_Image_for_GRUB_menu_on_boot-up)

apparently, my problem was caused by the 64bit version of ubuntu. I reinstalled ubuntu with the 32 bit alternate cd and everything is working smoothly.

Thanks,

---

### Post by linux23dragon on 2007-08-14
> **oliparcol said:**
> apparently, my problem was caused by the 64bit version of ubuntu. I reinstalled ubuntu with the 32 bit alternate cd and everything is working smoothly.

Thanks,

Yea, I have just installed a 64bit Ubuntu and currently have the same issues.  32bit Ubuntu works fine.
64bit Kubuntu  worked O.K  for me (on another AMD64 PC).  I hope that wasn't just me getting lucky.

---

### Post by carminez on 2007-08-14
Webcam update...

aMSN - The webcam picture works, but doesn't seem to send voice. I know the mic works because right from aMSN I can send someone a voice clip and it works. 

Ekiga Softphone - Version 2.0.3 does not work since it doesn't have Video4Linux2 (V4L2) support. So I followed instructions for upgrading from here [http://wiki.ekiga.org/index.php/Linux_Users#Feisty_i386](http://wiki.ekiga.org/index.php/Linux_Users#Feisty_i386) and that installs Ekiga 2.0.9, which does have V4L2 support. I start up Ekiga and then go into the preferences and go to the Video devices and change the video driver to be V4L2, the picture flashes in the Ekiga window, then Ekiga crashes. All subsequent attempts to start Ekiga fail. When I run it from a terminal it says "Segmentation fault (core dumped)." 

Skype for Linux does not seem to support Video Call, only the Windows and Mac versions do. I tried with vesion 1.3 and 1.4 beta.

Gyachi - Which is a Yahoo messenger client, webcam also did not work there.

---

### Post by linux23dragon on 2007-08-14
> **carminez said:**
> Webcam update...

aMSN - The webcam picture works, but doesn't seem to send voice. I know the mic works because right from aMSN I can send someone a voice clip and it works. 

Ekiga Softphone - Version 2.0.3 does not work since it doesn't have Video4Linux2 (V4L2) support. So I followed instructions for upgrading from here [http://wiki.ekiga.org/index.php/Linux_Users#Feisty_i386](http://wiki.ekiga.org/index.php/Linux_Users#Feisty_i386) and that installs Ekiga 2.0.9, which does have V4L2 support. I start up Ekiga and then go into the preferences and go to the Video devices and change the video driver to be V4L2, the picture flashes in the Ekiga window, then Ekiga crashes. All subsequent attempts to start Ekiga fail. When I run it from a terminal it says "Segmentation fault (core dumped)." 

Skype for Linux does not seem to support Video Call, only the Windows and Mac versions do. I tried with vesion 1.3 and 1.4 beta.

Gyachi - Which is a Yahoo messenger client, webcam also did not work there.

aMSN needs a plugin, or the correct alsa program to record Audio.  I have only tested the svn version BTW.
Ekiga-2.0.3 worked O.K. for me.  Was that just my luck?  I will try to give Ekiga-2.0.9 a try later today.  Perhaps you need to remove the hidden Ekiga directory (In your home folder), as the config scripts are to old?  Are you using Ubuntu 64bit?

Skype does work well with Audio and mic.  Is there no plugin for video?

---

### Post by carminez on 2007-08-15
> **linux23dragon said:**
> aMSN needs a plugin, or the correct alsa program to record Audio.  I have only tested the svn version BTW.
Ekiga-2.0.3 worked O.K. for me.  Was that just my luck?  I will try to give Ekiga-2.0.9 a try later today.  Perhaps you need to remove the hidden Ekiga directory (In your home folder), as the config scripts are to old?  Are you using Ubuntu 64bit?

Skype does work well with Audio and mic.  Is there no plugin for video?

the aMSN thing is just weird since it can record sound clips and send them in IM, just is not transmitting the audio in a webcam session. I'll look around and see about seeing if there is anything more recent than version 0.97b out there.

There was no hidden ekiga folder in my home directory, unless it is named something not obvious, there is no .ekiga or anything that resembles that.

There is no plugin for Skype, they don't have video in the linux version of the app. The voice worked great in Skype, I have not had any issues with audio at all, I never had to recompile anything for it, it worked from day 1 in Feisty.

I am using 32bit. I was never able to install the 64bit in any fashion, be it regular CD or Alt CD so I stayed with the 32bit since that was the only version I was able to get far enough into the install process. 

I have the 2.2GHz Duo CPU with the Bluetooth, so who knows if the hardware configuration is just different from the other 1520's that don't have the exact same makeup. It would kind of make sense with all the differences I've encountered from what other's have experienced in this forum. 
```

Here is my exact hardware as listed in my invoice...
Item #        Description
222-9009,  Inspiron 1520 Intel Core 2 Duo T7500 2.2GHz 800MHZ 4M L2 Cache
311-7215,  2GB DDR2 667MHz 2 Dimm
320-5462,  15.4 inch Wide Screen WSXGA+ TrueLife LCD for Inspiron 1520
320-5639,  256MB Nvidia GeForce 8600M GT
341-4768,  120GB 5400RPM SATA Hard Drive
430-0493,  Integrated 10/100 Network Card and Modem for Inspiron
313-5197,  8X DVD+/-RW Dual Layer Drive
313-4783,  Integrated High Definition Audio 2.0
430-2337,  Intel 4965AGN Wireless-N Mini Card
320-5691,  Integrated 2.0M Pixel Webcam
312-0526,  85 WHr 9-cell Lithium Ion Primary Battery for Inspiron 1520
430-2348,  Dell Wireless 355 Bluetooth Mod

```

---

### Post by EL-Sato on 2007-08-16
just wanted to say thanks for the guide :D i installed ubuntu studio (its not a live cd so i could install it directly with no problem) in my inspiron 1720 and fixed almost everything following this guide, seems to work fine now (except for the HD sound card and the sound I/O but i can live with that until october, maybe its fixed in the 7.10, lets hope xD)

---

### Post by linux23dragon on 2007-08-16
> **carminez said:**
> the aMSN thing is just weird since it can record sound clips and send them in IM, just is not transmitting the audio in a webcam session. I'll look around and see about seeing if there is anything more recent than version 0.97b out there.[

I have built a svn version of [[COLOR="RoyalBlue"]aMSN[/COLOR]]("http://www.adam.com.au/linux23d/linux23d/msn_15-08-07-1_i386.deb") yesterday.  And I've also built  [[COLOR="RoyalBlue"]Snack-2.2.10[/COLOR]]("http://www.adam.com.au/linux23d/linux23d/unix_2.2.10-1_i386.deb") using checkinstall.  And I have also played a bit with this [[COLOR="RoyalBlue"]Snack plugin[/COLOR]]("http://www.adam.com.au/linux23d/linux23d/snack2.2.10.tar.bz").  I've tested them with the low latency kernel.  The plugin is unstable, so you will see crash logs while setting up the Mic.  But you will have a option to select "ignore", and then can change the recording device.  You might see aMSN freeze a little while testing the mic playback.  aMSN runs OK after the setup.

You can give them a go if you like.

At this moment the recorded sound has pops in it.  But its a good demo of work in progress.

ps: You might need to chown (change owner) to the Snack plugin.  Might need to install asound or libasound too (if you haven't already)

EDIT: (Just to add from my latest post) you also might need to install t tk8.4, tk8.4-dev,  tcl8.4, tcl8.4-dev,  tcl8.3 and tcl8.3-dev as well.
EDIT 2: also check if you have  libpng and libjpeg installed too

---

### Post by amf on 2007-08-16
Successfully installed Ubuntu 7.04 following these instructions on Inspiron 1520 originally supplied with Vista - many thanks.
Only problem is after installing Dell´s modem drivers the sound completely vanishes. Not recognised at all.
Deleting the drivers, sound is then OK but cannot use modem.
Any comment or help please would be appreciated.

---

### Post by carminez on 2007-08-16
> **linux23dragon said:**
> I have built a svn version of [[COLOR="RoyalBlue"]aMSN[/COLOR]]("http://www.adam.com.au/linux23d/linux23d/msn_15-08-07-1_i386.deb") yesterday.  And I've also built  [[COLOR="RoyalBlue"]Snack-2.2.10[/COLOR]]("http://www.adam.com.au/linux23d/linux23d/unix_2.2.10-1_i386.deb") using checkinstall.  And I have also played a bit with this [[COLOR="RoyalBlue"]Snack plugin[/COLOR]]("http://www.adam.com.au/linux23d/linux23d/snack2.2.10.tar.bz").  I've tested them with the low latency kernel.  The plugin is unstable, so you will see crash logs while setting up the Mic.  But you will have a option to select "ignore", and then can change the recording device.  You might see aMSN freeze a little while testing the mic playback.  aMSN runs OK after the setup.

You can give them a go if you like.

At this moment the recorded sound has pops in it.  But its a good demo of work in progress.

ps: You might need to chown (change owner) to the Snack plugin.  Might need to install asound or libasound too (if you haven't already)

I installed your aMSN, when I run it I get an error "Loading TkCximage failed. This module is needed to run aMSN. Please compile aMSN first, instructions on how to compile are located in the file INSTALL"

I had tried to compile my own version from amsn-0.97RC1 source, buth when I tried to run configure, it would tell me that it couldn't find the Tcl folder or that I didn't have tcl-dev installed. I have tcl8.5 installed and tcl8.4 and tcl8.4-dev.

---

### Post by carminez on 2007-08-16
> **amf said:**
> Successfully installed Ubuntu 7.04 following these instructions on Inspiron 1520 originally supplied with Vista - many thanks.
Only problem is after installing Dell´s modem drivers the sound completely vanishes. Not recognised at all.
Deleting the drivers, sound is then OK but cannot use modem.
Any comment or help please would be appreciated.

I had the same problem when I installed the modem driver. I will never use the modem so I didn't install the driver the next time I installed the OS.

---

### Post by linux23dragon on 2007-08-17
> **carminez said:**
> I installed your aMSN, when I run it I get an error "Loading TkCximage failed. This module is needed to run aMSN. Please compile aMSN first, instructions on how to compile are located int eh file INSTALL"

Have you got tk8.4, tk8.4-dev and tcl8.4, tcl8.4-dev installed?

I also have tcl8.3, tcl8.3-dev  installed as well.

> **carminez said:**
> 
I had tried to compile my own version from amsn-0.97RC1 source, buth when I tried to run configure, it would tell me that it couldn't find the Tcl folder or that I didn't have tcl-dev installed. I have tcl8.5 installed and tcl8.4 and tcl8.4-dev.

I used this configure option:

./configure  --with-tcl=/usr/lib/tcl8.4 --with-tk=/usr/lib/tk8.4 --includedir=/usr/include

---

### Post by carminez on 2007-08-17
> **linux23dragon said:**
> Have you got tk8.4, tk8.4-dev and tcl8.4, tcl8.4-dev installed?

I also have tcl8.3, tcl8.3-dev  installed as well.



I used this configure option:

./configure  --with-tcl=/usr/lib/tcl8.4 --with-tk=/usr/lib/tk8.4 --includedir=/usr/include

I didn't have all those installed, so I installed them, and libpng and libjpeg, then used the .configure you have. The make install seemed to work, but make deb errored...
```

dh_builddeb --destdir="./distrib/DEB" --filename="amsn_0.97RC1-svnexported.deb"
dpkg-deb - error: Debian revision (`svnexported') doesn't contain any digits
dpkg-deb: 1 errors in control file
dh_builddeb: command returned error code 512
make[1]: *** [binary-arch] Error 1
make[1]: Leaving directory `/home/carmine/Desktop/amsn-0.97RC1'
make: *** [deb] Error 2

```

When I try to just run the amsn that got created with make install, I get the same TkCximage error.

Could this be a tcl/tk 8.5 related issue? I do have 8.5 installed as well.

---

### Post by jebbiss on 2007-08-17
I was just wondering if these instruction would work with a Dell Vostro 1500 since it is basically the same laptop?

Thanks

---

### Post by bibou91 on 2007-08-17
I can not connect my external hard drive on my vostro 1500 which is like an inspiron 1520.
I can however use my MX revolution on it. So USB works.

Does anyone have any clue?

---

### Post by linux23dragon on 2007-08-17
> **bibou91 said:**
> I can not connect my external hard drive on my vostro 1500 which is like an inspiron 1520.
I can however use my MX revolution on it. So USB works.

Does anyone have any clue?

Open your system log (from the menu bar).

System->Administration->System log

Then select the kernel.log.  Plug in the external USB hard drive and look at the log information that will output to the kernel log.

---

### Post by linux23dragon on 2007-08-17
> **carminez said:**
> I didn't have all those installed, so I installed them, and libpng and libjpeg, then used the .configure you have. The make install seemed to work, but make deb errored...

Can you use checkinstall?  

> **carminez said:**
> 
When I try to just run the amsn that got created with make install, I get the same TkCximage error.

Could this be a tcl/tk 8.5 related issue? I do have 8.5 installed as well.

You could try to uninstall tcl/tk 8.5, and see if aMSN will work (might need to reinstall aMSN).

Of course, you could try to configure with tcl/tk 8.5 to see if that works out.

---

### Post by oliparcol on 2007-08-18
so I've installed Ubuntu 7.04 32bit version with alternate cd. The sound is working well except the microphone and I can't listen music with exaile!

I've tried to add this line: options snd-hda-intel model=ref
but when I reboot my computer, I have sound only on the laptop speaker and not on my external speakers (plug with green jack).

thanks,
oliparcol

EDIT: I've tested compilation method for ALSA driver but I've still got the same problems: microphone isn't working and Exaile too

---

### Post by linux23dragon on 2007-08-18
> **oliparcol said:**
> so I've installed Ubuntu 7.04 32bit version with alternate cd. The sound is working well except the microphone and I can't listen music with exaile!

I've tried to add this line: options snd-hda-intel model=ref
but when I reboot my computer, I have sound only on the laptop speaker and not on my external speakers (plug with green jack).

thanks,
oliparcol

EDIT: I've tested compilation method for ALSA driver but I've still got the same problems: microphone isn't working and Exaile too

Can you use alsamixer (in the terminal) and make sure InMux and ADCMux is set to on, and not muted?
You might need to use digital mic1 as well.   I'm yet to see if I can get the external speakers to work myself.  Its possible that you need to use the oss mixer too.

I don't have the Notebook with me ATM sorry.

EDIT: can you plase try adding this to /etc/modprobe.d/alsa-base
```

options snd-hda-intel model=6stack-digout
```

Then reboot.

---

### Post by bibou91 on 2007-08-18
I've the same issue as above too.

Yesterday it was working but now anymore today.
I try to add the lane on alsa-base but it doesn't work better. 

I talk about the plug of jacks.


Thanks for your help about my USB problem, you do great job!

---

### Post by carminez on 2007-08-18
Has anyone tried putting a PC Card in the Inspiron 1520???

Does this only support a new style of PC Cards?

I tried to put one of my existing PC Cards in there to try it out and it didn't fit all the way in.

EDIT
[http://www.expresscard.org/web/site/qa.jsp](http://www.expresscard.org/web/site/qa.jsp)

---

### Post by oliparcol on 2007-08-19
so with this new command: 
```
options snd-hda-intel model=6stack-digout
```
my external speakers are working.
But my microphone still not works even if I choose Digital mic 1. I will check with oss mixer.

EDIT:Yeah, my microphone works, I used the gnome mixer, digital Mic 1 and ADCMux and it works !
EDIT#2: Apparently, my microphone works but not with Wengophone... I will check if there is an easy solution

---

### Post by bibou91 on 2007-08-19
This works for me also.

However with this line, I can not use the laptop speaker even when my jack is un plugged.
Do you have a solution to make both works?

I've only the left microphone who works, is that normal?

EDIT: Now it's different: The speakers work with the jack or  not,,, and the jack out works too :)

---

### Post by linux23dragon on 2007-08-19
Thanks for the reports.  I've updated the front page :)

More work to do yet (64bit).  But most of the gear is working now.

Who is going to test the VGA out put for us? :)

Edit:  Did you guys think its worth the trouble recompiling the the Audio drivers?

---

### Post by bibou91 on 2007-08-19
I tested it yesterday it works fine on my vostro (I have a 8600GT) in twin or separate screen.

However I had to edit xorg because it was hard to set my laptop in main screen.

No problem for the vga port, if you want me to post some more i can help.

---

### Post by carminez on 2007-08-19
> **bibou91 said:**
> I tested it yesterday it works fine on my vostro (I have a 8600GT) in twin or separate screen.

However I had to edit xorg because it was hard to set my laptop in main screen.

No problem for the vga port, if you want me to post some more i can help.

I tried getting the vga to output on my previous laptop and I wasn't successful. If you can list out what you did that would be great and I can try it with the Inspiron 1520. The one of the only reasons I still have a Vista partition is so I can watch movies on my TV, I would love to stop using it for that.

---

### Post by bibou91 on 2007-08-19
I do that when I've so time, I'm watching TV at the moment :)

---

### Post by bibou91 on 2007-08-19
First you have to plug your vga connector on your laptop.

Then you write
```
sudo nvidia-settings
```

X Server Display Configuration
-> Detect Display
->Then you can configure your second screen. Twin or Seperate and his resolution.
->Save to X Configure file
->Once it's done, you have to restart x. (Ctrl+Alt+BackSpace)

And then enjoy your 2nd screen.

I didn't find in nvidia settings how to change the screen order. 
In fact my LCD screen is set as the first, and my laptop screen as the second. so it bothers me... you can fix it by editing xorg.conf

```
sudo gedit /etc/xorg.conf
```

at the end of the file you must have something like that...
```

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard0"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1680x1050 +0+0; DFP: 800x600 +0+0; DFP: 640x480 +0+0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard1"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
EndSection
```

Just inverse the id of the screen to make it looks like that 

```

Section "Screen"
    Identifier     "Screen0" # my laptop screen is the main screen now
    Device         "Videocard0"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1680x1050 +0+0; DFP: 800x600 +0+0; DFP: 640x480 +0+0"
EndSection

Section "Screen"
    Identifier     "Screen1" # my vga screen is secondary
    Device         "Videocard1"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
EndSection
```

It rocks now! :)

---

### Post by oliparcol on 2007-08-20
so the built-in mic is working with this mixer configuration:
[[IMG]http://img364.imageshack.us/img364/8933/mixerfx6.th.png[/IMG]](http://img364.imageshack.us/my.php?image=mixerfx6.png)
But a plugged microphone doesn't work. 

Concerning the problem of external/computer speakers I will try this: [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_not_working_properly](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_not_working_properly)

Concerning the webcam, apparently, I've got some errors when I try video with wengo. I will try to solve this

EDIT: Ok, so the webcam and the integrated mic are working with ekiga. Concerning wengo problem with V4L2, apparently, it's a wellknown bug.

EDIT2: If ubuntu is installed directly with the 7.04 version, it's useless to compile the sound drivers because they are working out of the box (note: maybe the integrated microphone wasn't working outofthebox)

---

### Post by linux23dragon on 2007-08-20
> **oliparcol said:**
> so the built-in mic is working with this mixer configuration:
[[IMG]http://img364.imageshack.us/img364/8933/mixerfx6.th.png[/IMG]](http://img364.imageshack.us/my.php?image=mixerfx6.png)
But a plugged microphone doesn't work.  Concerning the problem of external/computer speakers I will try this: [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_not_working_properly](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_not_working_properly)

Concerning the webcam, apparently, I've got some errors when I try video with wengo. I will try to sovle this

EDIT: Ok, so the webcam and the integrated mic are working with ekiga. Concerning wengo problem with V4L2, apparently, it's a wellknown bug.

EDIT2: If the ubuntu is installed directly with the 7.04 version, it's useless to compile the sound drivers because they are working out of the box (note: maybe the integrated microphone wasn't working outofthebox)


This could be a nice addition:-

/etc/acpi/suspend.d/86-1420-sound.sh
```

 #!/bin/sh
 killall mixer_applet2
 modprobe -r snd_hda_intel
```

/etc/rc.local
```

 modlist=`lsmod | grep snd_hda`
 [ -z "$modlist" ] && modprobe snd_hda_intel model=6stack-digout
```



So the 7.04 alternate CD is a better option to upgrading from 6.10?


I will test to see if the new Alsa and hsfmodem_7.60.00.06oem_i386.deb driver works too.  If not, then I'll remove the Alsa install instructions.

I've just added some Intel graphics information.  I don't think anyone can use the instructions "before" installing Ubuntu.  But I need to find a easy way to get the Intel cards to work right.

Its most likely best to use the new instructions, after the installation.  

Please test and report your findings :)

---

### Post by oliparcol on 2007-08-20
> **linux23dragon said:**
> This could be a nice addition:-

/etc/acpi/suspend.d/86-1420-sound.sh
```

 #!/bin/sh
 killall mixer_applet2
 modprobe -r snd_hda_intel
```

/etc/rc.local
```

 modlist=`lsmod | grep snd_hda`
 [ -z "$modlist" ] && modprobe snd_hda_intel model=6stack-digout
```



These commands don't change anything for me.

> **linux23dragon said:**
> 

So the 7.04 alternate CD is a better option to upgrading from 6.10?



yeah, i think so. The only thing to do is, after the install, at the first boot to choose "rescue kernel" and change nv to vesa in "/etc/X11/xorg.conf".  Apparently, its possible to install directly ubuntu 7.04 with the desktop cd, if the live cd boot with rescue graphical mode, or something like that (untested).

> **linux23dragon said:**
> 
I will test to see if the new Alsa and hsfmodem_7.60.00.06oem_i386.deb driver works too.  If not, then I'll remove the Alsa install instructions.


I don't think there is newer alsa driver than 1.0.14 version. Personnaly, when I've installed 7.04 with alternate cd, the sound was working without doing nothing. Then I've updated alsa drivers with this command:
```
sudo apt-get install alsa-base alsa-tools alsa-oss alsa-utils alsa-firmware-loaders
```
and the sound was still working. After, I've added these lines:
```
options snd-hda-intel model=ref
options snd-hda-intel model=6stack-digout
```
but it didn't do nothing.

I will try to remove these two lines and see if the microphone is still working

EDIT: ok so I've removed these two lines:
```
options snd-hda-intel model=ref
options snd-hda-intel model=6stack-digout
```
So the integrated microphone is still working and my external speakers (plugged with a jack) are still working too. I suppose if we want sound with the internal speakers, we have to add this line:
```
options snd-hda-intel model=ref
```
I have a 2.0 speaker kit so maybe a larger speakers kit won't work so easily.

---

### Post by linux23dragon on 2007-08-20
> **oliparcol said:**
> These commands don't change anything for me.



yeah, i think so. The only thing to do is, after the install, at the first boot to choose "rescue kernel" and change nv to vesa in "/etc/X11/xorg.conf".  Apparently, its possible to install directly ubuntu 7.04 with the desktop cd, if the live cd boot with rescue graphical mode, or something like that (untested).



I don't think there is newer alsa driver than 1.0.14 version. Personnaly, when I've installed 7.04 with alternate cd, the sound was working without doing nothing. Then I've updated alsa drivers with this command:
```
sudo apt-get install alsa-base alsa-tools alsa-oss alsa-utils alsa-firmware-loaders
```
and the sound was still working. After, I've added these lines:
```
options snd-hda-intel model=ref
options snd-hda-intel model=6stack-digout
```
but it didn't do nothing.

I will try to remove these two lines and see if the microphone is still working

EDIT: ok so I've removed these two lines:
```
options snd-hda-intel model=ref
options snd-hda-intel model=6stack-digout
```
So the integrated microphone is still working and my external speakers (plugged with a jack) are still working too. I suppose if we want sound with the internal speakers, we have to add this line:
```
options snd-hda-intel model=ref
```
I have a 2.0 speaker kit so maybe a larger speakers kit won't work so easily.

Well, its time for a big clean up :)

I'll remove the Alsa drivers and only have the alternate CD option.

Then we need to look into Gusty (7.10).  Unless someone wants to do this (I don't own a Dell Inspiron 1520 Notebook)?

I'm just using my Sisters Boyfriends Notebook ATM.  So I don't have it on me every day.



EDIT:  I've just removed any thing to do with Ubuntu-6.10 and installing Alsa-1.0.14.  And I've added information about the Desktop and  alternate cd options without all the hand holding :)


Please check and report any problems

---

### Post by bibou91 on 2007-08-20
I've a new problem.

My NVIDIA driver just doesn't want to load when i first start the laptop.
It says that the kernel module and my driver versions don't match

I've to re-install the driver everytime i boot,,, then it works.

any clue?

---

### Post by oliparcol on 2007-08-20
did you use envy to install the driver ? [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by bibou91 on 2007-08-20
> **oliparcol said:**
> did you use envy to install the driver ? [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

It works now! Thank you :)

---

### Post by carminez on 2007-08-21
WEBCAM Update...

Looks like Ekiga 2.0.9 was pushed out for upgrade. I installed and video seems to work eventhough during the configuration it didn't seem to recognize. Once I finished the config it did start displaying the webcam. 

I'll let you know when I can find someone to test Ekiga with me if it works completely. 

One thing I have noticed both in Ubuntu and in Vista, the mic is very soft. I had the volume all the way up and was talking loud when testing the mic even in Vista, and the volume of the recording was rather low.

---

### Post by TheKind on 2007-08-21
Hello,
Ubuntu 6.10 is installed and working (i mean, with 1024x768 and not a lot things working). But now i don't know how to connect my laptop on the internet to update ubuntu and go to 7.04.

Ethernet doesn't work and my wifi isn't detected.
Can someone help me ?

Edit: Actually, ethernet is working ^^

---

### Post by DarthTibault on 2007-08-21
> **carminez said:**
> One thing I have noticed both in Ubuntu and in Vista, the mic is very soft. I had the volume all the way up and was talking loud when testing the mic even in Vista, and the volume of the recording was rather low.

I think that's a quite common problem with microphones (at least I've always had that problem). You can fix it by going to volume control -> edit -> preferences. There you make the Mic Boost switch visible, then you go to the switches tab and enable it. Problem solved.

---

### Post by TheKind on 2007-08-21
Does anyone know how to make my Wifi Draft-N card working with Ubuntu ???

**lspci:**

```
0c:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)

```

---

### Post by bibou91 on 2007-08-21
> **TheKind said:**
> Does anyone know how to make my Wifi Draft-N card working with Ubuntu ???

**lspci:**

```
0c:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)

```

Here is the How to

[https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty?highlight=%284965%29](https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty?highlight=%284965%29)

To make it works when you start the laptop you have to edit 

/etc/modules

and the line : ndiswrapper

---

### Post by TheKind on 2007-08-21
My wifi connexion works well now with ndiswrapper :KS

---

### Post by bibou91 on 2007-08-21
I also have sometimes issues when I boot and wifi is turned on.

But it doesn't know if both problems are linked.

---

### Post by linux23dragon on 2007-08-21
> **bibou91 said:**
> I also have sometimes issues when I boot and wifi is turned on.

But it doesn't know if both problems are linked.

That happens to you, with that WiFi card too?
Well, could it be to do with the WiFi/bluetooth kill switch?

I ask this question because of the following observations:-

Inspiron 6400 (No Bluetooth Installed):-

WiFi card: any
Kill switch location: on keyboard "Fn" + "F2"
BIOS Option settings: Enable or Disable WiFi Kill Switch 
Notes: No issues

Inspiron 1520 (Bluetooth Installed):-

WiFi card: any
Kill switch location: A Hard switch on the far back, left hand side of the Notebook.
BIOS Option settings: A Selection of One or another or all Wireless devices (Enable, Disable, All)
Notes:  WiFi may not operate after leaving the Notebook off for a long time.  The kill switch also has a spring loaded position (as well as on/off).

Could this be a Inspiron 1520 BIOS bug?
If you turned on the kill switch before you boot the 1520.  Will the WiFi work after you turn off the kill switch (after you log on)?
Does problem happen in Vista?

---

### Post by bibou91 on 2007-08-21
I don't really use vista often.

Well it's weird.

If I turn on the switch when I boot it doesn't work

If I turn off then turn on for a second time it freezes too.

The wifi quit working when i turn off the switch

(I've a vostro 1500 but it's the same thing)

---

### Post by oliparcol on 2007-08-21
apparently, there is a new bios for ubuntu 7.04 release by dell yesterday: [http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R164678&SystemID=INS_PNT_PM_1520&servicetag=&os=UBLN&osl=en&deviceid=12915&devlib=0&typecnt=0&vercnt=2&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=221269](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R164678&SystemID=INS_PNT_PM_1520&servicetag=&os=UBLN&osl=en&deviceid=12915&devlib=0&typecnt=0&vercnt=2&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=221269)
there is a new category in the dell support center for downloading driver called: "Ubuntu Desktop Edition 7.04". Dell begin to love linux :)

---

### Post by carminez on 2007-08-21
> **DarthTibault said:**
> I think that's a quite common problem with microphones (at least I've always had that problem). You can fix it by going to volume control -> edit -> preferences. There you make the Mic Boost switch visible, then you go to the switches tab and enable it. Problem solved.

Mic Boost doesn't exist for me. Maybe you have a different sound card in your Inspiron 1520, I have just the Integrated High Definition Audio 2.0

---

### Post by carminez on 2007-08-22
> **oliparcol said:**
> apparently, there is a new bios for ubuntu 7.04 release by dell yesterday: [http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R164678&SystemID=INS_PNT_PM_1520&servicetag=&os=UBLN&osl=en&deviceid=12915&devlib=0&typecnt=0&vercnt=2&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=221269](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R164678&SystemID=INS_PNT_PM_1520&servicetag=&os=UBLN&osl=en&deviceid=12915&devlib=0&typecnt=0&vercnt=2&catid=-1&impid=-1&formatcnt=1&libid=1&fileid=221269)
there is a new category in the dell support center for downloading driver called: "Ubuntu Desktop Edition 7.04". Dell begin to love linux :)

Who wants to be the first person to test upgrading the BIOS?

---

### Post by carminez on 2007-08-22
> **bibou91 said:**
> I don't really use vista often.

Well it's weird.

If I turn on the switch when I boot it doesn't work

If I turn off then turn on for a second time it freezes too.

The wifi quit working when i turn off the switch

(I've a vostro 1500 but it's the same thing)

I've used the wireless in Vista with no problems at all, works everytime, even when I turn the switch on and off while in Vista or not.

---

### Post by DarthTibault on 2007-08-22
> **carminez said:**
> Mic Boost doesn't exist for me. Maybe you have a different sound card in your Inspiron 1520, I have just the Integrated High Definition Audio 2.0

Ah, no it's a screenshot taken on my desktop-pc. I just presumed the switch would be available on the inspiron as well.

---

### Post by oliparcol on 2007-08-22
> **carminez said:**
> Who wants to be the first person to test upgrading the BIOS?
I just update my bios yesterday... nothing has changed apparently...

---

### Post by linux23dragon on 2007-08-22
UPDATE


[SIZE=3]**IRQ Balancing for Duel Core2**[/SIZE]

Search (in the Synaptic Package Manager) to see if you have the irqbalance package installed.
IRQ balancing is a must for popper IRQ sharing with SMP (or in our case Multi core) systems.


I just found out that Ubuntu does not install this package.  It should help improve performance a bit :)

---

### Post by alex1974 on 2007-08-22
My mic is working. opend the digital and closed the others.
But I can still not connect the external speakers (music box). I tried it with every connection on/off.
My alsa-base looks like:

```
# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=ref
options snd-hda-intel probe_mask=1
options snd-hda-intel model=6stack-digout
```

any idea?

---

### Post by Altimar on 2007-08-22
Hello all, I have found this thread extremely helpful and wanted to say thanks to all contributers.

Linux23dragon, great job, but for the sake of clarity I'd like to make a few suggestions and then some random comments about things I've experienced that others may (or may not) think are interesting. 

In the hardware list you have Nvidia 8600M GT (working), ATI Graphics (working), and HD Sound card (working) in there twice.

Under "Have not tested:" you list "PS2 connectors". I think maybe you are confusing the S-video out for a PS/2?

I ordered my 1520 with the Dell 1390 (bcm43xx) card intending to buy an Atheros card afterwards, but I ended up getting the 1390 to work with the new bcm43xx kernel driver. I think you should at least note that it can work. I don't remember exactly what I did, because I spent a lot of time working on it before I realized I had left the hardware switch off. #-o  I switched it on and voila! If you like, I can try to backtrack and write up some instructions but I think it may not have been more than apt-getting the firmware cutter and loading the kernel module.

About the webcam, Ekiga seems to recognize it, but I have not tested with another client yet. I've also tried aMSN, but it won't let me chat with myself and none of my (3) MSN friends were on at the time. However, I'm really more interested in using it on Yahoo. I see some reports that Kopete will work with a webcam over MSN and Yahoo. I think I will try testing this after work today. There is also something called GYachI which is supposed to support webcams over Yahoo, but it looks like development stopped about a year ago.

In my quest to find a way to switch bluetooth on/off, I stumbled across a Dell project called [libSMBIOS]("http://linux.dell.com/libsmbios/main/index.html") which is some tools to change various BIOS settings. It looked very promising, but unfortunately it appears to have been abandoned over a year ago. I downloaded it, had to install a few dependencies, compiled, and installed it, but it would not run on this machine. I think we need to put some pressure on Dell to update it to support newer models (or look into modifying it ourselves).

I originally wanted to keep the Dell MediaDirect partition, and just deleted the Vista partition and then carved it up into several partitions for windows and linux. From my understanding the MediaDirect partition may use files from the windows partition, but even after deleting it and creating new partitions, I was able to boot it. For a while. Then it stopped working, telling me that it couldn't access the partition, suggesting turning off bitlocker or something. So I deleted the MediaDirect partition. About a week or two later (after getting Ubuntu running pretty well) I got the bright idea to press the MediaDirect button to see what it would do. I figured it was set up to simply boot some certain partition (partition 4 or the last partition). Well, I don't know what exactly that button really does, but I definitely want to disable it now, because what it effectively did was to completely muck up the partition table and make the machine totally unbootable. It was an extraordinarily good thing I had just backed up every partition earlier that day. I recreated the partitions, partimaged them back and was back in business in under an hour. \\:D/  So, a word of warning to everyone, DON'T push that button!

I'd still like to have something similar to MediaDirect. I'm surprised I have not heard of a project like this using a stripped-down, quick-booting linux kernel with all the necessary media stuff. To be honest,  I really haven't looked yet, since it's a pretty low priority, but has anyone else come across anything like this?

One last thing. Has anybody tried to install Windows XP or 2000 on this machine? I need one or the other for work, but neither one has drivers for the SATA disk. I suppose I'll have to [modify an install disk with the drivers]("http://www.maximumpc.com/article/How-To--Slipstream-your-XP-installation?page=0%2C0"), but I'd have thought XP SP2 would work...

---

### Post by carminez on 2007-08-22
> **Altimar said:**
> Hello all, I have found this thread extremely helpful and wanted to say thanks to all contributers.

Linux23dragon, great job, but for the sake of clarity I'd like to make a few suggestions and then some random comments about things I've experienced that others may (or may not) think are interesting. 

In the hardware list you have Nvidia 8600M GT (working), ATI Graphics (working), and HD Sound card (working) in there twice.

Under "Have not tested:" you list "PS2 connectors". I think maybe you are confusing the S-video out for a PS/2?

I ordered my 1520 with the Dell 1390 (bcm43xx) card intending to buy an Atheros card afterwards, but I ended up getting the 1390 to work with the new bcm43xx kernel driver. I think you should at least note that it can work. I don't remember exactly what I did, because I spent a lot of time working on it before I realized I had left the hardware switch off. #-o  I switched it on and voila! If you like, I can try to backtrack and write up some instructions but I think it may not have been more than apt-getting the firmware cutter and loading the kernel module.

About the webcam, Ekiga seems to recognize it, but I have not tested with another client yet. I've also tried aMSN, but it won't let me chat with myself and none of my (3) MSN friends were on at the time. However, I'm really more interested in using it on Yahoo. I see some reports that Kopete will work with a webcam over MSN and Yahoo. I think I will try testing this after work today. There is also something called GYachI which is supposed to support webcams over Yahoo, but it looks like development stopped about a year ago.

In my quest to find a way to switch bluetooth on/off, I stumbled across a Dell project called [libSMBIOS]("http://linux.dell.com/libsmbios/main/index.html") which is some tools to change various BIOS settings. It looked very promising, but unfortunately it appears to have been abandoned over a year ago. I downloaded it, had to install a few dependencies, compiled, and installed it, but it would not run on this machine. I think we need to put some pressure on Dell to update it to support newer models (or look into modifying it ourselves).

I originally wanted to keep the Dell MediaDirect partition, and just deleted the Vista partition and then carved it up into several partitions for windows and linux. From my understanding the MediaDirect partition may use files from the windows partition, but even after deleting it and creating new partitions, I was able to boot it. For a while. Then it stopped working, telling me that it couldn't access the partition, suggesting turning off bitlocker or something. So I deleted the MediaDirect partition. About a week or two later (after getting Ubuntu running pretty well) I got the bright idea to press the MediaDirect button to see what it would do. I figured it was set up to simply boot some certain partition (partition 4 or the last partition). Well, I don't know what exactly that button really does, but I definitely want to disable it now, because what it effectively did was to completely muck up the partition table and make the machine totally unbootable. It was an extraordinarily good thing I had just backed up every partition earlier that day. I recreated the partitions, partimaged them back and was back in business in under an hour. \\:D/  So, a word of warning to everyone, DON'T push that button!

I'd still like to have something similar to MediaDirect. I'm surprised I have not heard of a project like this using a stripped-down, quick-booting linux kernel with all the necessary media stuff. To be honest,  I really haven't looked yet, since it's a pretty low priority, but has anyone else come across anything like this?

One last thing. Has anybody tried to install Windows XP or 2000 on this machine? I need one or the other for work, but neither one has drivers for the SATA disk. I suppose I'll have to [modify an install disk with the drivers]("http://www.maximumpc.com/article/How-To--Slipstream-your-XP-installation?page=0%2C0"), but I'd have thought XP SP2 would work...

That kinda scares me that the MediaDirect button can cause that damage by just pressing it. I guess I will try to disconnect it by popping the hood, or superglue it so I don't accidentially press it :)

As for Windows XP or 2000... I've installed both but as virtual machines inside of Ubuntu. You could try that instead of finding a way around the SATA drivers. I use innotek's VirtualBox (virtualbox.org) that is available in Automatix.

For webcam, I was able to get aMSN to work with video only, not audio also. GYachI did not work with the webcam. Have not tried Kopete, its just a matter of finding something that will support has support for V4L2.

---

### Post by derouge on 2007-08-22
This is great .. if you have a connection. The problem of course comes when you dont. And I don't. I've tried configuring both the laptop's wireless card and plugging the ethernet cable directly into the laptop. Neither work, but both work under Vista. Whats the fix?

---

### Post by carminez on 2007-08-23
> **bibou91 said:**
> Here is the How to

[https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty?highlight=%284965%29](https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty?highlight=%284965%29)

To make it works when you start the laptop you have to edit 

/etc/modules

and the line : ndiswrapper

Ok, I followed the directions in that link and then added ndiswrapper to /etc/modules and it almost worked. 

I was able to scan and see wireless networks, but couldn't connect to my network. I was able to connect to a Staples store hot spot which is more than 400 meters away which was cool. 

I figured out eventually the problem with connecting to my network. Back in January I was trying to get my previous Ubuntu laptop (Inspiron 8000) connected to the wifi but the Linksys card I had did not want to connect if I had any type of security enabled on the router, so I had to disable WEP and decided to do MAC address filtering to secure things and that seemed to work. 

Well, I noticed that this Intel 4965 card was seeing my network, but when it tried to connect it wasn't getting an IP from DHCP. So I plugged the ethernet back in and disabled MAC filtering on the router and I was then able to connect. So then I enabled WEP to secure things and reconnected without an issue. 

So I guess if I want to get my old Inspiron 8000 on wifi, I'll have to buy a new wifi card for it :)

BTW, my router is a Linksys WRT54G.

---

### Post by zidboy on 2007-08-23
hello to all:
I have dell inspiron 1520, 4gb ram, gforce 8600 512, Sound integrated Blaster and have the following problem:
The video card (it works) without any problem.
The sound card (it works), but has two problems, it does not initiate with sound and in addition I can listen to po the headsets but simultaneously I listen to the loudspeakers.

If somebody can help me with this problem, please serious of much aid to be able to solve the problem since notebook is new my and I want that it is without problems.

Greetings

---

### Post by linux23dragon on 2007-08-23
> **Altimar said:**
> Hello all, I have found this thread extremely helpful and wanted to say thanks to all contributers.

Linux23dragon, great job, but for the sake of clarity I'd like to make a few suggestions and then some random comments about things I've experienced that others may (or may not) think are interesting. 

You are welcome, and I also would like thank the all the contributers for their input, (that includes you to Altimar ) 

It is because of the user feed back and testing, that we all can get the Dell Inspiron 1520 Notebook configured and working correctly.  It is the only way I can document this (rather big) "hint". 

Thanks :)

> **Altimar said:**
> 
In the hardware list you have Nvidia 8600M GT (working), ATI Graphics (working), and HD Sound card (working) in there twice.

Under "Have not tested:" you list "PS2 connectors". I think maybe you are confusing the S-video out for a PS/2?

Nice catch.  I've just put the corrections in.


> **Altimar said:**
> 
I ordered my 1520 with the Dell 1390 (bcm43xx) card intending to buy an Atheros card afterwards, but I ended up getting the 1390 to work with the new bcm43xx kernel driver. I think you should at least note that it can work. I don't remember exactly what I did, because I spent a lot of time working on it before I realized I had left the hardware switch off. #-o  I switched it on and voila! If you like, I can try to backtrack and write up some instructions but I think it may not have been more than apt-getting the firmware cutter and loading the kernel module.

Cool.  Thats another device we can add to the base :)
If you (or someone) can confirm how you got the bcm43xx driver working?  If it just works out of the box (as you suspect), then I'll just add the device without adding any hints (apart from driver source location).  But if it has taken you a bit of working out, then please share the information, for all to see :)


> **Altimar said:**
> 
About the webcam, Ekiga seems to recognize it, but I have not tested with another client yet. I've also tried aMSN, but it won't let me chat with myself and none of my (3) MSN friends were on at the time. However, I'm really more interested in using it on Yahoo. I see some reports that Kopete will work with a webcam over MSN and Yahoo. I think I will try testing this after work today. There is also something called GYachI which is supposed to support webcams over Yahoo, but it looks like development stopped about a year ago.

Ekiga-2.0.3 allows the web cam to work as it does support V4L2.  aMSN is also supports V4L2, but I found (my self) that the sound needs a plugin called "Snack".  I have built and tested the Snack plugin with the aMSN from SVN.  It works O.K. but I had to hack at it a bit.

You can check it out out if you like.  Just remember that it is development version, so it won't be stable.
  
[[COLOR="RoyalBlue"]aMSN[/COLOR]]("http://www.adam.com.au/linux23d/linux23d/msn_15-08-07-1_i386.deb")
[[COLOR="RoyalBlue"]Snack-2.2.10[/COLOR]]("http://www.adam.com.au/linux23d/linux23d/unix_2.2.10-1_i386.deb")
[[COLOR="RoyalBlue"]Snack plugin[/COLOR]]("http://www.adam.com.au/linux23d/linux23d/snack2.2.10.tar.bz")

You need to make sure you have the correct dependency s installed.  Please see on this page for more information.

[COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=501195&highlight=dell+1520&page=16](http://ubuntuforums.org/showthread.php?t=501195&highlight=dell+1520&page=16)[/COLOR]

Kopete can use V4L2 web cams, but it is not working right yet.  There is lots of talk on the Linux-UVC mailing list about patching and stuff.  Currently Kopete does not correctly work with the web cam driver.

You can try other web cam applications.  But in general, they must support V4L2.

> **Altimar said:**
> 
In my quest to find a way to switch bluetooth on/off, I stumbled across a Dell project called [libSMBIOS]("http://linux.dell.com/libsmbios/main/index.html") which is some tools to change various BIOS settings. It looked very promising, but unfortunately it appears to have been abandoned over a year ago. I downloaded it, had to install a few dependencies, compiled, and installed it, but it would not run on this machine. I think we need to put some pressure on Dell to update it to support newer models (or look into modifying it ourselves).

I think all of that firmware is now built into the kernel drivers.  In the Dell Inspiron you can find a BIOS setting that controls the kill switch to turn off/on any wireless device.  It is up to you how you like to set up that kill switch.  But by default, the kill switch controls all of the devices at the same time.

EDIT: I take that comment back.  But perhaps it is in the CMOS already?  Any how I will have a look into it later his week.



> **Altimar said:**
> 
I originally wanted to keep the Dell MediaDirect partition, and just deleted the Vista partition and then carved it up into several partitions for windows and linux. From my understanding the MediaDirect partition may use files from the windows partition, but even after deleting it and creating new partitions, I was able to boot it. For a while. Then it stopped working, telling me that it couldn't access the partition, suggesting turning off bitlocker or something. So I deleted the MediaDirect partition. About a week or two later (after getting Ubuntu running pretty well) I got the bright idea to press the MediaDirect button to see what it would do. I figured it was set up to simply boot some certain partition (partition 4 or the last partition). Well, I don't know what exactly that button really does, but I definitely want to disable it now, because what it effectively did was to completely muck up the partition table and make the machine totally unbootable. It was an extraordinarily good thing I had just backed up every partition earlier that day. I recreated the partitions, partimaged them back and was back in business in under an hour. \\:D/  So, a word of warning to everyone, DON'T push that button!

I'd still like to have something similar to MediaDirect. I'm surprised I have not heard of a project like this using a stripped-down, quick-booting linux kernel with all the necessary media stuff. To be honest,  I really haven't looked yet, since it's a pretty low priority, but has anyone else come across anything like this?

Was that after you installed the libSMBIOS?


> **Altimar said:**
> 
One last thing. Has anybody tried to install Windows XP or 2000 on this machine? I need one or the other for work, but neither one has drivers for the SATA disk. I suppose I'll have to [modify an install disk with the drivers]("http://www.maximumpc.com/article/How-To--Slipstream-your-XP-installation?page=0%2C0"), but I'd have thought XP SP2 would work...

Yep, I have installed a copy of Windows XP and have  tried Vista as well.

I used a VM called VirtualBox (Innotek).

Windows XP media works too.  I cant use Vista, so I've scraped it all together.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Virtualbox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Virtualbox)

Have fun :)


EDIT: here is a screen shot of Windows Runnning on top of Linux :)

[www.adam.com.au/linux23d/linux23d/Screenshot.png](www.adam.com.au/linux23d/linux23d/Screenshot.png)

---

### Post by np_ on 2007-08-23
I have a Inspiron 1520 with the Intel graphics card. I've followed the instructions as best I could:

-Installed Ubuntu 7.04 with the alternate CD. I set it up to dual boot.
-Probably because I set it up to dual boot, I get the Grub menu without having to press Escape. X failed to start in normal mode and I got a command prompt, so I just continued from there (There is no "rescue kernel" mode. There is a "recovery mode", however.)
-Removed xserver-xorg-video-i810
-Updated the repository list (I find nano easier to use, I suspect other newbies would too) and then ran aptitude -y update
-Installed apt-get install xserver-xorg-video-intel
-Ran dpkg-reconfigure -phigh xserver-xorg, switched to Intel and accepted the default resolutions
-Checked xorg.conf, and it indeed has "intel" in "Section Device".
-startx

The result is that half the time the screen goes from black to less black and stays there, the other half it goes from black to less black back to the command prompt with an error message. [Here is my Xorg.log]("http://userstyles.org/Xorg.0.log"). The relevant bits:

```
(EE) GARTInit: Unable to open /dev/agpgart (No such file or directory)
(WW) intel(0): /dev/agpgart is either not available, or no memory is available
for allocation.  Using pre-allocated memory only.
(==) intel(0): VideoRam: 7676 KB
(II) intel(0): Attempting memory allocation with tiled buffers and 
	       large DRI memory manager reservation:
(II) intel(0): Allocating 1790 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(II) intel(0): Attempting memory allocation with tiled buffers and 
	       small DRI memory manager reservation:
(II) intel(0): Allocating 1790 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(II) intel(0): Attempting memory allocation with untiled buffers and 
	       large DRI memory manager reservation:
(II) intel(0): Allocating 1790 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(II) intel(0): Attempting memory allocation with untiled buffers and 
	       small DRI memory manager reservation:
(II) intel(0): Allocating 1790 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(WW) intel(0): Not enough video memory.  Disabling DRI.
(II) intel(0): Allocating 1790 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(EE) intel(0): Couldn't allocate video memory

Fatal server error:
AddScreen/ScreenInit failed for driver 0
```
Any ideas? Did I miss something?

---

### Post by linux23dragon on 2007-08-23
> **np_ said:**
> I have a Inspiron 1520 with the Intel graphics card. I've followed the instructions as best I could:

-Installed Ubuntu 7.04 with the alternate CD. I set it up to dual boot.
-Probably because I set it up to dual boot, I get the Grub menu without having to press Escape. X failed to start in normal mode and I got a command prompt, so I just continued from there (There is no "rescue kernel" mode. There is a "recovery mode", however.)
-Removed xserver-xorg-video-i810
-Updated the repository list (I find nano easier to use, I suspect other newbies would too) and then ran aptitude -y update
-Installed apt-get install xserver-xorg-video-intel
-Ran dpkg-reconfigure -phigh xserver-xorg, switched to Intel and accepted the default resolutions
-Checked xorg.conf, and it indeed has "intel" in "Section Device".
-startx

The result is that half the time the screen goes from black to less black and stays there, the other half it goes from black to less black back to the command prompt with an error message. [Here is my Xorg.log]("http://userstyles.org/Xorg.0.log"). The relevant bits:

```
(EE) GARTInit: Unable to open /dev/agpgart (No such file or directory)
(WW) intel(0): /dev/agpgart is either not available, or no memory is available
for allocation.  Using pre-allocated memory only.
(==) intel(0): VideoRam: 7676 KB
(II) intel(0): Attempting memory allocation with tiled buffers and 
	       large DRI memory manager reservation:
(II) intel(0): Allocating 1790 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(II) intel(0): Attempting memory allocation with tiled buffers and 
	       small DRI memory manager reservation:
(II) intel(0): Allocating 1790 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(II) intel(0): Attempting memory allocation with untiled buffers and 
	       large DRI memory manager reservation:
(II) intel(0): Allocating 1790 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(II) intel(0): Attempting memory allocation with untiled buffers and 
	       small DRI memory manager reservation:
(II) intel(0): Allocating 1790 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(WW) intel(0): Not enough video memory.  Disabling DRI.
(II) intel(0): Allocating 1790 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(EE) intel(0): Couldn't allocate video memory

Fatal server error:
AddScreen/ScreenInit failed for driver 0
```
Any ideas? Did I miss something?

Thanks for writting in.  I  will try to help you fix this issue ASAP.  Currently I'm at work so I can only ask a question or two ATM.  But I will start working on this issues once I get home.  

In the mean time, can you please post a copy of your /etc/X11/xorg.conf file please?

And can you try using (for now) just the "vesa" driver?


The only issues I find in your log file is this section:-

```

(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ, 965GM,
	G33, Q35, Q33
(II) Primary Device is: PCI 00:02:0
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset 965GM found

```

And this section:-
```

(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 7616 kB
(II) intel(0): VESA VBE OEM: Intel(r)GM965/PM965/GL960 Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r)GM965/PM965/GL960 Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
```


Thanks for reporting.  And I have just fixed the kernel boot option.  But It also looks like I need to review the Intel graphics section as well.

---

### Post by np_ on 2007-08-23
I tried switching to vesa, but it says that there are no matching modes and that screens were found, but none were configured.

[My xorg.conf](http://userstyles.org/xorg.conf).

---

### Post by linux23dragon on 2007-08-23
> **np_ said:**
> I tried switching to vesa, but it says that there are no matching modes and that screens were found, but none were configured.

[My xorg.conf](http://userstyles.org/xorg.conf).

Can you add "HorizSync" and "VertRefresh" to Section "Monitor":

```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync 	47 - 64
	VertRefresh	50-75
EndSection
```

And change the subSection modes like:-

```

SubSection "Display"
		Depth		24
		Modes		"800x600" "640x480"
	EndSubSection
```

You might need to use "640x480".  

It's a "get you going fix", but we will have a proper fix later today.

---

### Post by np_ on 2007-08-23
Thanks for the suggestion. Should I use the vesa driver or the intel driver?

Edit:
Well, I tried both. With intel, no change. With vesa and 640x480 only, I'm in! (My god, the wireless works out of the box!)

---

### Post by linux23dragon on 2007-08-24
> **np_ said:**
> Thanks for the suggestion. Should I use the vesa driver or the intel driver?

Edit:
Well, I tried both. With intel, no change. With vesa and 640x480 only, I'm in! (My god, the wireless works out of the box!)

OK, Its time for some eye opening fun :)

Our first step is to make Xorg auto guess what driver is best for your setup. :)

Now to do this we will need to remove the /etc/X11/xorg.conf file.  (we will back it up)

```

sudo mv /etc/X11/xorg.conf  /etc/X11/xorg.conf-24-08-07
```

And then reboot.

Now what happens is, Xorg will try to test and configure your system (without generating a /etc/X11/xorg.conf file), and will try to run without any issues.

It should work out, unless it thinks that it needs to use the VESA driver.

After you reboot the Notebook. can you please post the xorg.0.log?

EDIT: Even if it (for some reason) does not work out.  Can you please post the xorg.0.log

To recover xorg, use this command.

```

sudo mv  /etc/X11/xorg.conf-24-08-07 /etc/X11/xorg.conf
```

Then reboot.

---

### Post by oliparcol on 2007-08-24
did someone have installed ubuntu 7.10 tribes 3 ?

---

### Post by Altimar on 2007-08-24
> **linux23dragon said:**
> 

Cool.  Thats another device we can add to the base :)
If you (or someone) can confirm how you got the bcm43xx driver working?  If it just works out of the box (as you suspect), then I'll just add the device without adding any hints (apart from driver source location).  But if it has taken you a bit of working out, then please share the information, for all to see :)

Yeah, I think you should go ahead and put down that it works. I'll list the steps that I think are correct and you can just put a note that these instructions are not confirmed and to please ask us for help if they do not work (or confirm that they do work).

EDIT: Forgot to attribute instructions from [ubuntuforums.org]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy#head-d2623559f21cb2d6373aaa3a17dece9d8f2abb50")

First, make sure the wireless is turned on in the BIOS, and that if you have the switch controlling the WiFi, that the switch is also turned on. :wink:

Add this to your /etc/apt/sources.list:
```
deb http://ubuntu.cafuego.net edgy-cafuego bcm43xx
```

Get the repo key:
```
wget http://ubuntu.cafuego.net/969F3F57.gpg -O- | sudo apt-key add -
```
 
Update package list and install the broadcom firmware
```
sudo apt-get update && sudo apt-get install bcm43xx-firmware
```

Load the kernel module (if you blacklisted it for ndiswrapper, make sure to remove it from /etc/modprobe.d/blacklist)
```
sudo modprobe bcm43xx
```

Now the WiFi light should come on and you should see the interface listed:
```
iwconfig
```


> **linux23dragon said:**
> 
Ekiga-2.0.3 allows the web cam to work as it does support V4L2.  aMSN is also supports V4L2, but I found (my self) that the sound needs a plugin called "Snack".  I have built and tested the Snack plugin with the aMSN from SVN.  It works O.K. but I had to hack at it a bit.


Yeah, Ekiga works for me, but I'm not familiar with it and I really just want to use the webcam with friends over Yahoo. I guess I'll look into what Ekiga can do.


> **linux23dragon said:**
> 
Kopete can use V4L2 web cams, but it is not working right yet.  There is lots of talk on the Linux-UVC mailing list about patching and stuff.  Currently Kopete does not correctly work with the web cam driver.

You can try other web cam applications.  But in general, they must support V4L2.


So I see. Since it appears that V4L2 has been the new standard for a year or two, I don't understand why there are exactly two programs that can use it and everything else will only work with V4L. :confused: I guess I'll be waiting on Kopete. By the way, is pidgin in any repositories? I couldn't find it, unless they're still calling it gaim in the repos.


> **linux23dragon said:**
> 
I think all of that firmware is now built into the kernel drivers.  In the Dell Inspiron you can find a BIOS setting that controls the kill switch to turn off/on any wireless device.  It is up to you how you like to set up that kill switch.  But by default, the kill switch controls all of the devices at the same time.

Was that [partition trashing] after you installed the libSMBIOS?


No, it was before, I think. All I did was install it and try to read some BIOS values, but it gave some error indicating that it didn't recognize the model and could get the tokens. I then uninstalled it. 
I found a reference to what you said about the SMBIOS being in the kernel and believe you are correct about it, but I found a review that said Feisty was not compiled to support it... Anyhow, I had decided to change the BIOS option so the wireless switch controls the Bluetooth only since I'm on WiFi pretty much all the time.


> **linux23dragon said:**
> 
Yep, I have installed a copy of Windows XP and have  tried Vista as well.

I used a VM called VirtualBox (Innotek).

Windows XP media works too.  I cant use Vista, so I've scraped it all together.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Virtualbox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Virtualbox)


Yeah, I was planning on trying out VMWare actually, but I'm not sure about VPN support. Have you ever tried using one on a VM? Also, I will be interested in playing a few games (UT07, Starcraft2) later on so I will need windows on a partition.


Another topic that I haven't really seen discussed is standby and hibernate modes. I admit I only tried hibernate once, but it didn't work. The screen went dark and the hard drive was doing something for a bit and then stopped. I waited for about two minutes and it was still on, so I think I pressed the spacebar and the screen came back with the login screen. 

I was wondering if the problem could be related to having a swap partition smaller than physical memory. I've seen a lot of advice to newbies to make a 512MB swap if they have 2GB of RAM, which seems like a bad idea to me unless you never try to hibernate when using more than 512MB of RAM (which probably isn't hard, I rarely used more than 256MB on my last laptop running FC5). Anyway I made a 2GB swap partition to match my RAM, but I wonder if it's maybe a couple MBs short and so refuses to hibernate. Anybody know more about this? I guess I'll play around with it a bit this weekend.


I'm a bit confused about the intel audio situation. I held off on recompiling alsa because of the time it would take, and now I see you changed your instructions to just getting packages and changing /etc/modprobe.d/alsa-base. What exactly will this change for me, because out of the box the sound worked for me as well as the microphone, but it's kind of weird. For instance, if I plug in external speakers, the laptop speakers stay on. I was also used to having separate controls for laptop speaker volume and headphone/external volume. Do your instructions fix this?

Thanks again for all the help!

---

### Post by carminez on 2007-08-24
> **Altimar said:**
> 
Yeah, I was planning on trying out VMWare actually, but I'm not sure about VPN support. Have you ever tried using one on a VM? Also, I will be interested in playing a few games (UT07, Starcraft2) later on so I will need windows on a partition.


Another topic that I haven't really seen discussed is standby and hibernate modes. I admit I only tried hibernate once, but it didn't work. The screen went dark and the hard drive was doing something for a bit and then stopped. I waited for about two minutes and it was still on, so I think I pressed the spacebar and the screen came back with the login screen. 

I was wondering if the problem could be related to having a swap partition smaller than physical memory. I've seen a lot of advice to newbies to make a 512MB swap if they have 2GB of RAM, which seems like a bad idea to me unless you never try to hibernate when using more than 512MB of RAM (which probably isn't hard, I rarely used more than 256MB on my last laptop running FC5). Anyway I made a 2GB swap partition to match my RAM, but I wonder if it's maybe a couple MBs short and so refuses to hibernate. Anybody know more about this? I guess I'll play around with it a bit this weekend.


I can only comment about the VPN on a VM and hibernate...

I've had Windows (XP/2000) virtual machines running and had them use Microsoft VPN connections or the Nortel VPN Client and have had no issues. During the time the VM was using a VPN, I would also have the Host machine be on a separate VPN for just local traffic and everything worked fine. So it is possible.

My swap partition is 2.97GB and hibernate had the same behavior for me.

---

### Post by odin1965 on 2007-08-24
I still have not gotten my wireless back up (intel 3945ABG). Anyone else having troubles with this on the 1520? I have another thread going at [http://ubuntuforums.org/showthread.php?t=525152](http://ubuntuforums.org/showthread.php?t=525152) as some others with this card in different laptops are having similar problems.

Could someone with working wireless and a 3945ABG on the Dell 1520 post the output from 'lshw -C network' in the other thread so as to not clutter up this one until we find a solution?

---

### Post by np_ on 2007-08-24
> **linux23dragon said:**
> OK, Its time for some eye opening fun :)

Our first step is to make Xorg auto guess what driver is best for your setup. :)

Now to do this we will need to remove the /etc/X11/xorg.conf file.  (we will back it up)

```

sudo mv /etc/X11/xorg.conf  /etc/X11/xorg.conf-24-08-07
```

And then reboot.

Now what happens is, Xorg will try to test and configure your system (without generating a /etc/X11/xorg.conf file), and will try to run without any issues.

It should work out, unless it thinks that it needs to use the VESA driver.

After you reboot the Notebook. can you please post the xorg.0.log?

EDIT: Even if it (for some reason) does not work out.  Can you please post the xorg.0.log

To recover xorg, use this command.

```

sudo mv  /etc/X11/xorg.conf-24-08-07 /etc/X11/xorg.conf
```

Then reboot.

Alright, without xorg.conf, it started up correctly in 1280x800, 61Hz. [Here is my Xorg.0.log](http://userstyles.org/Xorg.0.log).

---

### Post by linux23dragon on 2007-08-25
> **Altimar said:**
> Yeah, I think you should go ahead and put down that it works. I'll list the steps that I think are correct and you can just put a note that these instructions are not confirmed and to please ask us for help if they do not work (or confirm that they do work).

Will do.

> **Altimar said:**
> 
 By the way, is pidgin in any repositories? I couldn't find it, unless they're still calling it gaim in the repos.

Yea they still use the old gaim.  You can compile the source code you self if you really need it.   Use "checkinstall" (instead of make install) to create a *.deb package file.

> **Altimar said:**
> 
Yeah, I was planning on trying out VMWare actually, but I'm not sure about VPN support. Have you ever tried using one on a VM? Also, I will be interested in playing a few games (UT07, Starcraft2) later on so I will need windows on a partition.

I think you can install a native client UT7 (now UT3 ?) on Linux.
Here is some information about it:-

[http://www.linuxgames.com/news/feedback.php?identiferID=9414&action=flatview](http://www.linuxgames.com/news/feedback.php?identiferID=9414&action=flatview)

> **Altimar said:**
> 
Another topic that I haven't really seen discussed is standby and hibernate modes. I admit I only tried hibernate once, but it didn't work. The screen went dark and the hard drive was doing something for a bit and then stopped. I waited for about two minutes and it was still on, so I think I pressed the spacebar and the screen came back with the login screen.

I have not looked into that yet.  I know the Notebook will go into sleep mode.  And if you close the Notebook (while its on), you will find yourself with a "Unlock" login screen.  Thats all I have checked out so far.

> **Altimar said:**
> 
I was wondering if the problem could be related to having a swap partition smaller than physical memory. I've seen a lot of advice to newbies to make a 512MB swap if they have 2GB of RAM, which seems like a bad idea to me unless you never try to hibernate when using more than 512MB of RAM (which probably isn't hard, I rarely used more than 256MB on my last laptop running FC5). Anyway I made a 2GB swap partition to match my RAM, but I wonder if it's maybe a couple MBs short and so refuses to hibernate. Anybody know more about this? I guess I'll play around with it a bit this weekend.

That is yet to be proven too.

> **Altimar said:**
> 
I'm a bit confused about the intel audio situation. I held off on recompiling alsa because of the time it would take, and now I see you changed your instructions to just getting packages and changing /etc/modprobe.d/alsa-base. What exactly will this change for me, because out of the box the sound worked for me as well as the microphone, but it's kind of weird. For instance, if I plug in external speakers, the laptop speakers stay on. I was also used to having separate controls for laptop speaker volume and headphone/external volume. Do your instructions fix this?

When I first installed Ubuntu-7.04 (by upgrading from 6.10), I had found that the sound quality was not that good on the Inspiron 1520.  So I ended up rebuilding Alsa, in the hope that I could get better sound (with games and general input/output audio applications)

And it worked.  I had better sound and more mixer options too.  The default Alsa driver in the kernel is 1.0.14a (not the final release 1.0.14?).  I've also have been playing around with the configuration of the driver, so it reflects the kernel configuration options.  So I can make sure that all of the Audio system options works with Alsa-1.0.14, as by default.

I also had some user reports that confirmed they had better audio.  But since (At the time) I did not have any idea how to package the builds (due to the Alsa drivers already installed in the kernel), I had pushed to experiment with what we got.  

But it appears that people (who have installed from the alternate installation disk) can use the microphone and have good sound (by default?)

You can give it a try if you like.  It appears that you can use "force" options.

---

### Post by linux23dragon on 2007-08-25
> **np_ said:**
> Alright, without xorg.conf, it started up correctly in 1280x800, 61Hz. [Here is my Xorg.0.log](http://userstyles.org/Xorg.0.log).


Please try out this  [xorg.conf]("www.adam.com.au//linux23d//linux23d/xorg.conf")

And post the Xorg.0.log.

You can play around with it (if you like) :)

By the looks of things, you can use Beryl too.

---

### Post by linux23dragon on 2007-08-25
> **odin1965 said:**
> I still have not gotten my wireless back up (intel 3945ABG). Anyone else having troubles with this on the 1520? I have another thread going at [http://ubuntuforums.org/showthread.php?t=525152](http://ubuntuforums.org/showthread.php?t=525152) as some others with this card in different laptops are having similar problems.

Could someone with working wireless and a 3945ABG on the Dell 1520 post the output from 'lshw -C network' in the other thread so as to not clutter up this one until we find a solution?

Hi odin1965

I have also tried to look for a good fix for the Intel 3945ABG Pro.

I can get it running after I connect to Ethernet.  Funny stuff eh?  I'm not sure if it has anything to do with the kill switch, or the network connection or drivers.  Could it be with the drivers?

Is the WiFi set to roaming mode in your Network Settings?
Does things change if you disable the kill switch in the Bios (or just have the kill switch enabled only for the WiFi?)

---

### Post by odin1965 on 2007-08-25
> **linux23dragon said:**
> Hi odin1965

I have also tried to look for a good fix for the Intel 3945ABG Pro.

I can get it running after I connect to Ethernet.  Funny stuff eh?  I'm not sure if it has anything to do with the kill switch, or the network connection or drivers.  Could it be with the drivers?

Is the WiFi set to roaming mode in your Network Settings?
Does things change if you disable the kill switch in the Bios (or just have the kill switch enabled only for the WiFi?)

Funny thing is, even when my wireless worked, the RF kill switch did not, even though it was enabled in the BIOS. I have tried every combo of roaming mode and manual config that there is. At first I thought it was network manager but now I think there is some issue with the firmware or driver. It IS possible that my wireless card is defective, I may have to reinstall vista to see if that works, shudder :). Though i'd probably pick up another card and try that first.

---

### Post by linux23dragon on 2007-08-25
> **odin1965 said:**
> Funny thing is, even when my wireless worked, the RF kill switch did not, even though it was enabled in the BIOS. I have tried every combo of roaming mode and manual config that there is. At first I thought it was network manager but now I think there is some issue with the firmware or driver. It IS possible that my wireless card is defective, I may have to reinstall vista to see if that works, shudder :). Though i'd probably pick up another card and try that first.

O.K here is a "bad" question for you.

Does the restricted driver manager show that the WiFi driver is in use?

I just thought I'd ask, as you never know your luck some times :)


Edit: I have an idea !!

If you are going to extremes by reinstalling Vista, then try his out first.

First install linux-2.6.20-15 and then copy ipw3945.ucode and pw3945.ko to $(uname -r) like this (you might want to backup those files first):-

sudo cp /lib/firmware/2.6.20-15-generic/ipw3945.ucode /lib/firmware/$(uname -r)/ipw3945.ucode
sudo cp /lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/ipw3945/ipw3945.ko  /lib/modules/$(uname -r)/kernel/ubuntu/wireless/ipw3945/ipw3945.ko 
depmod -ae


then reboot.

PS: make sure that the boot loader (/boot/grub/menu.lst) is going to boot up $(uname -r)

EDIT: Can you please try using Discover1 and/or Discover as well.  You can install it using Synaptic

Discover is a hardware identification system based on the libdiscover1
library.  Discover provides a flexible interface that programs can use to
report a wide range of information about the hardware that is installed on a
Linux system. It functions at boot-time by probing the available system
busses and loading the appropriate drivers based on data provided in the
discover1-data package.

---

### Post by linux23dragon on 2007-08-25
> **zidboy said:**
> hello to all:
I have dell inspiron 1520, 4gb ram, gforce 8600 512, Sound integrated Blaster and have the following problem:
The video card (it works) without any problem.
The sound card (it works), but has two problems, it does not initiate with sound and in addition I can listen to po the headsets but simultaneously I listen to the loudspeakers.

If somebody can help me with this problem, please serious of much aid to be able to solve the problem since notebook is new my and I want that it is without problems.

Greetings

Please post the output  after running this command in a terminal.

```

cat /proc/asound/cards
```

---

### Post by np_ on 2007-08-25
> **linux23dragon said:**
> Please try out this  [xorg.conf]("www.adam.com.au//linux23d//linux23d/xorg.conf")

And post the Xorg.0.log.

You can play around with it (if you like) :)

By the looks of things, you can use Beryl too.

It works again, and [here's Xorg.0.log](http://userstyles.org/Xorg.0.log). Is this what I should be sticking with, or are there other changes to make? Either way thanks a bunch.

---

### Post by carminez on 2007-08-25
> **carminez said:**
> Ok, I followed the directions in that link and then added ndiswrapper to /etc/modules and it almost worked. 

I was able to scan and see wireless networks, but couldn't connect to my network. I was able to connect to a Staples store hot spot which is more than 400 meters away which was cool. 

I figured out eventually the problem with connecting to my network. Back in January I was trying to get my previous Ubuntu laptop (Inspiron 8000) connected to the wifi but the Linksys card I had did not want to connect if I had any type of security enabled on the router, so I had to disable WEP and decided to do MAC address filtering to secure things and that seemed to work. 

Well, I noticed that this Intel 4965 card was seeing my network, but when it tried to connect it wasn't getting an IP from DHCP. So I plugged the ethernet back in and disabled MAC filtering on the router and I was then able to connect. So then I enabled WEP to secure things and reconnected without an issue. 

So I guess if I want to get my old Inspiron 8000 on wifi, I'll have to buy a new wifi card for it :)

BTW, my router is a Linksys WRT54G.

Since I got the Intel 4965 wireless card working, I have been getting intermittent computer freezes. Is anyone else experiencing this behavior? It only seems to happen when the wireless card is connected, if I am on a wired network there is not problem.

---

### Post by linux23dragon on 2007-08-25
> **np_ said:**
> It works again, and [here's Xorg.0.log](http://userstyles.org/Xorg.0.log). Is this what I should be sticking with, or are there other changes to make? Either way thanks a bunch.

No it should be all good from here.

Please try installing (from step2) [compizfusion]("http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty").

Please report on how it turned out :)

I have used this article myself, and I get software updates all the time.  I Never had any real issues with it.

---

### Post by linux23dragon on 2007-08-25
> **carminez said:**
> Since I got the Intel 4965 wireless card working, I have been getting intermittent computer freezes. Is anyone else experiencing this behavior? It only seems to happen when the wireless card is connected, if I am on a wired network there is not problem.

So you are using DHCP or roaming mode to connect to your router?

Does anyone have the same issues?

---

### Post by carminez on 2007-08-25
> **linux23dragon said:**
> So you are using DHCP or roaming mode to connect to your router?

Does anyone have the same issues?

Roaming mode

---

### Post by odin1965 on 2007-08-25
> **linux23dragon said:**
> O.K here is a "bad" question for you.

Does the restricted driver manager show that the WiFi driver is in use?


Yes, the restricted driver is definitly being used. As well, output from iwlist scan and iwconfig seem normal as well.

> **linux23dragon said:**
> 
Edit: I have an idea !!

First install linux-2.6.20-15 and then copy ipw3945.ucode and pw3945.ko to $(uname -r) like this (you might want to backup those files first):-

sudo cp /lib/firmware/2.6.20-15-generic/ipw3945.ucode /lib/firmware/$(uname -r)/ipw3945.ucode
sudo cp /lib/modules/2.6.20-15-generic/kernel/ubuntu/wireless/ipw3945/ipw3945.ko  /lib/modules/$(uname -r)/kernel/ubuntu/wireless/ipw3945/ipw3945.ko 
depmod -ae

2.6.20-15 is still installed from original. So basically I am copying over the firmware and module from the older kernel to my current one. then running depmod to update  dependencies for the modules? Good idea, I didn't know where the original firmware was.

> 
EDIT: Can you please try using Discover1 and/or Discover as well.  You can install it using Synaptic

Discover is a hardware identification system based on the libdiscover1
library.  Discover provides a flexible interface that programs can use to
report a wide range of information about the hardware that is installed on a
Linux system. It functions at boot-time by probing the available system
busses and loading the appropriate drivers based on data provided in the
discover1-data package.

I will try this first, then copy over the firmware and module. I have doubts that the copying thing will work as I currently have the machine dual booting my original updated 7.074 and a fresh install of 7.04 and wireless acts the same on both. Plus the PClinuxOS live CD that originally worked in my machine does not now.

---

### Post by linux23dragon on 2007-08-26
> **odin1965 said:**
> Yes, the restricted driver is definitly being used. As well, output from iwlist scan and iwconfig seem normal as well.



2.6.20-15 is still installed from original. So basically I am copying over the firmware and module from the older kernel to my current one. then running depmod to update  dependencies for the modules? Good idea, I didn't know where the original firmware was.



I will try this first, then copy over the firmware and module. I have doubts that the copying thing will work as I currently have the machine dual booting my original updated 7.074 and a fresh install of 7.04 and wireless acts the same on both. Plus the PClinuxOS live CD that originally worked in my machine does not now.


Its time to start some serious research :)

We can (at the moment) use quick fixes, like this following example.  Because we can auto execute the command while booing, or login as user.

```

sudo -i 
ifdown eth1 && ifup eth1
```

Here is some information I googled.

Ubuntu Bugs: 
[https://bugs.launchpad.net/ubuntu/+bug/108152](https://bugs.launchpad.net/ubuntu/+bug/108152)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/128360](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/128360)

This looks interesting too:
[http://www.bughost.org/bugzilla/show_bug.cgi?id=956](http://www.bughost.org/bugzilla/show_bug.cgi?id=956)

EDIT

And found out were to get more information about the driver.  (After using google I had found this information from Gentoo and others).

[http://gentoo-wiki.com/HARDWARE_ipw3945](http://gentoo-wiki.com/HARDWARE_ipw3945)
[http://www.mail-archive.com/debian-laptop@lists.debian.org/msg49497.html](http://www.mail-archive.com/debian-laptop@lists.debian.org/msg49497.html)
[http://www.linuxquestions.org/questions/showthread.php?t=460831](http://www.linuxquestions.org/questions/showthread.php?t=460831)

Could be even more info out there :)
Any one want to help us out here?

---

### Post by linux23dragon on 2007-08-26
> **carminez said:**
> Roaming mode

One last questions.  Have you tried using "IRQ Balance"?

That might not be the solution.  But its worth trying out.  But at the same time I need to know if "IRQ Balance" is causing any possible issues as well.

Currently, we also need to look for solutions to other WiFi (3945) related problems as well.  Your issues could be in relation to it.

---

### Post by carminez on 2007-08-26
> **linux23dragon said:**
> One last questions.  Have you tried using "IRQ Balance"?

That might not be the solution.  But its worth trying out.  But at the same time I need to know if "IRQ Balance" is causing any possible issues as well.

Currently, we also need to look for solutions to other WiFi (3945) related problems as well.  Your issues could be in relation to it.

Yup, I had the IRQ Balancing installed prior to getting the wifi 4965 operational. I haven't tried upgrading the BIOS yet, I'll give that a shot and see if anything changes. I'll have to try to pay closer attention to what is going on when it the machine freezes, sometimes it happens while I am away from the desk. But during the times I have witnessed it, there has been a constant flashing of the wifi light, but I'll have to try to investage it further, I hadn't seen anything in the logs that looked out of the ordinary. 

Also, with the 4965, the only security I have been able to get to work was WEP, nothing else has worked so far.

---

### Post by np_ on 2007-08-26
> **linux23dragon said:**
> No it should be all good from here.

Please try installing (from step2) [compizfusion]("http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty").

Please report on how it turned out :)

I have used this article myself, and I get software updates all the time.  I Never had any real issues with it.

Thanks a bunch. I installed beryl from Synaptec but I wasn't really interested in it so I just got rid of it.

---

### Post by gideon07 on 2007-08-26
I just purchased a Inspiron 1520 and am installing Ubuntu.  I am stuck at getting the graphics card to work.  I tried all of the instructions on this thread including the xorg.conf file in the quote below, and am not having good luck.  I have attached my Xorg0.log file (using the xorg.conf file previously mentioned).  I would greatly appreciate any help.  

I have the Intel integrated graphics card and the high resolution 1680x1050 screen.  

Here is a quick summary of what I have tried already.
[LIST]
[*]both the amd64 and i386 alternate installs
[*]removed the i810 module and installed the intel module as given in the instructions
[*]tried various resolutions using vesa, intel, and i810 as the drivers
[*]removed the xorg.conf file altogether
[/LIST]

I have not had any success.  With the intel driver, it appears that the xserver is unable to open /dev/agpgart and with the vesa driver it is unable to open /dev/fb.  

I have had success with the SVGA output and the vesa driver.  When I switch back to the laptop display, it worked but was very dim.

Again, I would greatly appreciate any help.

> **np_ said:**
> It works again, and [here's Xorg.0.log](http://userstyles.org/Xorg.0.log). Is this what I should be sticking with, or are there other changes to make? Either way thanks a bunch.

---

### Post by linux23dragon on 2007-08-26
> **gideon07 said:**
> 

Again, I would greatly appreciate any help.


Please post your xorg.conf file.
And please run the xserver without the /etc/X11/xorg.conf file, and then post the Xorg.0.log file.

I'll look into it later on today, (as I'm working right now).

Anyone want to give it a go?

**EDIT**
You are still using:- 

 Current Operating System: Linux omni 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686

Please try to upgrade the kernel to 2.6.20-16-generic 


And if you have already done this, then please make sure that you are booting the correct kernel (/boot/grub/menu.lst).
You can also check the boot options by pressing the escape key (for a menu list) before grub boots the default kernel image 

To upgrade your system, you only need to use this command in the terminal (while logged in as root)```

aptitude -y update
``` .


Please ask, if you have questions on how to do this.

---

### Post by linux23dragon on 2007-08-27
Update to hint.

Scraped.

---

### Post by Leebobs on 2007-08-27
Hello,

**NOTE: I was using the Ubuntu 7.04 DVD to install**

I followed the guide on my 1520 and it worked fine, with one (easily solved) problem. When I first used the guide, after tweaking xorg.conf I got into the desktop fine, I then installed all of the updates and got a number of dependency errors.

It turns out, that this is because update manager was looking for my DVD and I hadn't applied the DVD drive fix yet!

A quick reinstall later, I did the DVD fix (using the command line and VI) straight after tweaking xorg.conf. After the reboot I had a working GUI and DVD drive and the updates worked flawlessly.

Leebobs :)

PS: Will all this be working by default in 7.10?

---

### Post by linux23dragon on 2007-08-27
> **Leebobs said:**
> Hello,

**NOTE: I was using the Ubuntu 7.04 DVD to install**

I followed the guide on my 1520 and it worked fine, with one (easily solved) problem. When I first used the guide, after tweaking xorg.conf I got into the desktop fine, I then installed all of the updates and got a number of dependency errors.

It turns out, that this is because update manager was looking for my DVD and I hadn't applied the DVD drive fix yet!

A quick reinstall later, I did the DVD fix (using the command line and VI) straight after tweaking xorg.conf. After the reboot I had a working GUI and DVD drive and the updates worked flawlessly.

Leebobs :)



Thats great :)

I'll be updating the forum to include the update manager (DVD) information.  Thanks :)


> **Leebobs said:**
> 

PS: Will all this be working by default in 7.10?

Its all in the air at the moment.  Can someone test the betas?

---

### Post by gideon07 on 2007-08-27
> **linux23dragon said:**
> 

**EDIT**
You are still using:- 

 Current Operating System: Linux omni 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686

Please try to upgrade the kernel to 2.6.20-16-generic 


That was it!  You are a genius!  I had to open aptitude and manually select the 2.6.20-16-generic kernel.  The command-line update/upgrade wouldn't do it.  (I expected it would have with the install option, but I didn't try that.)

I have attached my xorg.conf and the Xorg.0.log file.  One strange behavior is that the xorg.conf file specifies a maximum resolution of 1280x800, but the server automatically started at 1680x1050.  The Xorg.0.log file indicates that the server added the 1680x1050 mode-line.

---

### Post by linux23dragon on 2007-08-27
> **gideon07 said:**
> That was it!  You are a genius!  I had to open aptitude and manually select the 2.6.20-16-generic kernel.  The command-line update/upgrade wouldn't do it.  (I expected it would have with the install option, but I didn't try that.)

I have attached my xorg.conf and the Xorg.0.log file.  One strange behavior is that the xorg.conf file specifies a maximum resolution of 1280x800, but the server automatically started at 1680x1050.  The Xorg.0.log file indicates that the server added the 1680x1050 mode-line.



Please try out the xorg.conf file attached.

---

### Post by gideon07 on 2007-08-27
> **linux23dragon said:**
> Please try out the xorg.conf file attached.
I'll try it this evening.  Right now I am off to work.

---

### Post by odin1965 on 2007-08-27
> **linux23dragon said:**
> Its time to start some serious research :)

We can (at the moment) use quick fixes, like this following example.  Because we can auto execute the command while booing, or login as user.

```

sudo -i 
ifdown eth1 && ifup eth1

Here is some information I googled.

Ubuntu Bugs: 
[https://bugs.launchpad.net/ubuntu/+bug/108152](https://bugs.launchpad.net/ubuntu/+bug/108152)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/128360](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/128360)

This looks interesting too:
[http://www.bughost.org/bugzilla/show_bug.cgi?id=956](http://www.bughost.org/bugzilla/show_bug.cgi?id=956)

EDIT

And found out were to get more information about the driver.  (After using google I had found this information from Gentoo and others).

[http://gentoo-wiki.com/HARDWARE_ipw3945](http://gentoo-wiki.com/HARDWARE_ipw3945)
[http://www.mail-archive.com/debian-laptop@lists.debian.org/msg49497.html](http://www.mail-archive.com/debian-laptop@lists.debian.org/msg49497.html)
[http://www.linuxquestions.org/questions/showthread.php?t=460831](http://www.linuxquestions.org/questions/showthread.php?t=460831)

Could be even more info out there :)
Any one want to help us out here?

Weird, 
[CODE]
sudo -i 
ifdown eth1 && ifup eth1
```
gives me; 
```
ifdown: interface eth1 not configured
Ignoring unknown interface eth1=eth1.
```

My wireless extensions see eht1 just fine, iwconfig and iwlist scan both work.

AS to all the links, I've seen most of them and many many more. lots of problems and symptoms that are similar. It's not looking for a needle in a haystack, it's like looking for a certain  needle in a stack of needles :) consensus is that the ipw3945 works well, but when it goes south, there's la lot of things it could be. nm-applet, dbus, hal, the microcode, the module, userspace daemon.

Copying over the ucode and module gave my a different output to lshw, see this thread, [http://ubuntuforums.org/showthread.php?t=530352](http://ubuntuforums.org/showthread.php?t=530352), but it didn't fix it.

I am going to put my 3945 pci card into my buddy's Acer tomorrow when he comes back to work (he doesn't know it yet), and see if it works in his. If it does, I will attempt to build the newer driver that uses the newer mac stack and see if I can get that to run. I may try a tribe 4 CD as well, though I am reading lots of problems with that as well.

---

### Post by Juanete on 2007-08-27
> **zidboy said:**
> hello to all:
The sound card (it works), but has two problems, it does not initiate with sound and in addition I can listen to po the headsets but simultaneously I listen to the loudspeakers.
Greetings

I was having the same "earphones won't mute speakers" problem. This was always like this, it doesn't matter if I boot with the jack pluged in or not. I've added the 3 lines to alsa-base file and I've also tried this: " [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) " but it's still the same. The built-in mic is working great, have not tested an external one yet. The reason why I said "was having" is that at a point the earphones just stoped working (It's not the earphones, I checked) now I can only get audio out of this thing by the speakers.

Tried irqloadbalancing two days ago ---> temp is now a little lower, not much performance improvement (at least on CompizFusion)

Just tried BIOS update --> can't tell the difference with the old one...

--------------------------------------------------------------
juanete@Sophie:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 20
--------------------------------------------------------------
juanete@Sophie:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
--------------------------------------------------------------
juanete@Sophie:~$ cat /proc/asound/card0/codec\#*
Codec: SigmaTel STAC9205
Address: 0
Vendor Id: 0x838476a0
Subsystem Id: 0x102801f1
Revision Id: 0x100204
Default PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=0
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
--------------------------------------------------------------

BTW, great thread! got everything else working thanks to this thread!

Juanete

---

### Post by gideon07 on 2007-08-28
> **linux23dragon said:**
> Please try out the xorg.conf file attached.

This file works the same as the previous xorg.conf file.  I have attached the Xorg.0.log file.  None of the intermediate resolutions are shown in the Gnome screen resolution selection menu.  The only ones listed are
1680x1050
1280x800
1280x768
1024x768
800x600
640x480
1680x1680 (I have no idea how this one was included)

I also noticed that the behavior is not well defined when I have my external monitor plugged in.  It defaults to the 1680x1680 resolution (which neither display supports, so half of the desktop is not visible.

It is working good enough for me right now, but if we can get it further along for the next release, I am willing to help.  By the way, how do I test a beta version of the next release?

---

### Post by linux23dragon on 2007-08-28
> **gideon07 said:**
> This file works the same as the previous xorg.conf file.  I have attached the Xorg.0.log file.  None of the intermediate resolutions are shown in the Gnome screen resolution selection menu.  The only ones listed are
1680x1050
1280x800
1280x768
1024x768
800x600
640x480
1680x1680 (I have no idea how this one was included)

I also noticed that the behavior is not well defined when I have my external monitor plugged in.  It defaults to the 1680x1680 resolution (which neither display supports, so half of the desktop is not visible.

Yea, that is strange.

I guess that the screen resolutions will need to be included.  Xorg will choose to pick the best resolutions for your LCD and Graphics card setup. 

I have no idea why 1680x1680 is there.  But if it works then, "wow".

EDIT:  I think you need to make another monitor section in your xorg.conf.  There is a post on how to do it on this forum.

Like this example:

[http://ubuntuforums.org/showthread.php?t=501195&highlight=dell+1520&page=18](http://ubuntuforums.org/showthread.php?t=501195&highlight=dell+1520&page=18)

> **gideon07 said:**
> 
It is working good enough for me right now, but if we can get it further along for the next release, I am willing to help.  By the way, how do I test a beta version of the next release?

Just download a image from one of these URL's:

[http://cdimage.ubuntu.com/releases/gutsy/tribe-4/](http://cdimage.ubuntu.com/releases/gutsy/tribe-4/)
[http://cdimage.ubuntu.com/releases/gutsy/tribe-5/](http://cdimage.ubuntu.com/releases/gutsy/tribe-5/)

Burn it to CD and see if the Notebook will boot and configure correctly :)

We need to post bug reports ASAP

---

### Post by Slasher Fun on 2007-08-28
I tried Gutsy Tribe 5 :
* nVidia proprietary driver doesn't load correctly (error loading module, I have to come back to the "nv" free drivers), so I have a slow display
* no sound at all
--> Back to feisty...

By the way, did anybody find out how to desactivate the internal loudspeakers when hearphones are plugged in ?

---

### Post by felimwhiteley on 2007-08-28
Thanks for this HowTo, got a few of my issues fixed. the irqbalance does improve performance quite a bit with respect to Firewire/i400. I run Rysnc backup in KDE's Keep App. This used to grind the machine to a halt without irqbalance. Not sure on specific timing update but it has gone from locking up the machine during backups to being totally usable now so nice fix, Thanks !

Yeah I've got that same issue with the Audio not muting the speakers when headphones are in. It's a bit annoying it must be said. I've not upgraded the Audio drivers though, mine worked fine otherwise so I left it.

---

### Post by oliparcol on 2007-08-28
concerning the problem of speakers vs headphone, I think, if the computer boot with a jack plugged in, the internal speakers don't work and, at the opposite, if there is no jack plugged, the internal spakers work. But its true, its annoying to be obliged to turn off, turn on the computer to switch the audio between headphones and speakers...

EDIT: I forgot to specify that I compiled the alsa new drivers

---

### Post by Juanete on 2007-08-28
Hi again,
I'm still having trouble with the whole earphones jack/speakers thing. I'v done this " [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_not_working_properly](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_not_working_properly) " and removed the 3 "extra" lines from alsa-base and now if I boot with the earphones pluged in the speakers wont work, if I don't, both speakers and earphones work at the same time. I'll keep trying...

What about IRDA? I've seen my sweet little Sophie has one under the multimedia keys but I have no idea how to use it (it would be great beeing able to control rhythmbox from bed! or why not... the webcam jejejeje.....)

Bye!

---

### Post by zidboy on 2007-08-28
> **Juanete said:**
> I was having the same "earphones won't mute speakers" problem. This was always like this, it doesn't matter if I boot with the jack pluged in or not. I've added the 3 lines to alsa-base file and I've also tried this: " [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) " but it's still the same. The built-in mic is working great, have not tested an external one yet. The reason why I said "was having" is that at a point the earphones just stoped working (It's not the earphones, I checked) now I can only get audio out of this thing by the speakers.

Tried irqloadbalancing two days ago ---> temp is now a little lower, not much performance improvement (at least on CompizFusion)

Just tried BIOS update --> can't tell the difference with the old one...

--------------------------------------------------------------
juanete@Sophie:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 20
--------------------------------------------------------------
juanete@Sophie:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
--------------------------------------------------------------
juanete@Sophie:~$ cat /proc/asound/card0/codec\#*
Codec: SigmaTel STAC9205
Address: 0
Vendor Id: 0x838476a0
Subsystem Id: 0x102801f1
Revision Id: 0x100204
Default PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x0f, stepsize=0x05, mute=0
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
--------------------------------------------------------------

BTW, great thread! got everything else working thanks to this thread!

Juanete

Juanete:  have the same configuration that yours, and installed all the libs of alsa, and formed everything what it has left in the forums, but even so profit not to be able to form the affluent sound.

If you have some tutorial or guide with who it can form my affluent card, I thank for much and excuses to you much by the English since I am Latin American, rather for Chile.

Greetings and thanks

---

### Post by Altimar on 2007-08-28
> **Juanete said:**
> 
What about IRDA? I've seen my sweet little Sophie has one under the multimedia keys but I have no idea how to use it (it would be great beeing able to control rhythmbox from bed! or why not... the webcam jejejeje.....)


The 1[457]20 Inspirons all come with a [Consumer IR]("http://en.wikipedia.org/wiki/Consumer_IR") port. When you order the notebook, on the Accessories page under TV Tuner & Remote Control, there are options for a $29 "Remote Control for Vista Home Premium" and a $15 Dell Travel Remote Control, IR. I purchased the latter when I ordered my 1520. 

The travel remote is a little tiny thing that slides into the ExpressCard slot on the left side of the notebook. [This user review]("http://www.notebookreview.com/default.asp?newsID=3846") includes a picture of it. It has 17 buttons in total.

I have tried it and it works well, just like the front media buttons, plus buttons that generate keycodes like Up, Down, Left, Right, PageUp, PageDown, Enter, and several others. I can check it out with xev  and post a full listing after work today. It appears to have pretty good range, at least ten feet or so (I'll have to try it out in a larger room). I used it the other day to give my parents a slideshow of vacation pics (they were impressed!). In my opinion, it is definitely worth it.

The only way I see to buy one after purchasing the computer is to get a [refurbished one from dell]("http://accessories.us.dell.com/sna/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=FW331") for $10.99 plus S&H ($5). They are listed to be compatible with 1420, 1521, 1720, 1721. Notably absent is the 1520:confused:, but it definitely works with mine. They are actually listed as refurbished, but from a post on notebook forums, a guy said he bought several of them and they appeared to be brand new, which is reasonable, since they started selling them only a couple months ago.

EDIT: Pic of the remote with the keycodes [IMG]http://jaymiller.dyndns.org/images/travelRemote.jpg[/IMG]

---

### Post by linux23dragon on 2007-08-29
Posted an Update for all who wish to play with the sound card.   But I must stress, I don't think it will solve the stereo jack output problems.


UPDATE

Alsa should be working well.  But if you feel the need to install Alsa-1.0.14 then please, only use this how too.

[http://ubuntuforums.org/showthread.php?t=530374&highlight=alsa+intel+hda](http://ubuntuforums.org/showthread.php?t=530374&highlight=alsa+intel+hda)

---

### Post by linux23dragon on 2007-08-29
> **Slasher Fun said:**
> I tried Gutsy Tribe 5 :
* nVidia proprietary driver doesn't load correctly (error loading module, I have to come back to the "nv" free drivers), so I have a slow display
* no sound at all
--> Back to feisty...

By the way, did anybody find out how to desactivate the internal loudspeakers when hearphones are plugged in ?


It boots :)

Well thats step forward.

Hopefully, We can get the Nvidia drivers installed in October.

Sound is not that much of an issues for us.  Well get it working :)

But, the bug reports must be posted.

---

### Post by Juanete on 2007-08-29
> **zidboy said:**
> 

If you have some tutorial or guide with who it can form my affluent card, I thank for much and excuses to you much by the English since I am Latin American, rather for Chile.

Greetings and thanks

First of all, I don't know what da' hack you mean with "affluent card" maybe this is because I'm Latin American too (San Luis-Argentina), and my english is not all that good. "Si queres decimelo en criollo asi te entiendo". 


> **Altimar said:**
> The 1[457]20 Inspirons all come with a [Consumer IR]("http://en.wikipedia.org/wiki/Consumer_IR") port. When you order the notebook, on the Accessories page under TV Tuner & Remote Control, there are options for a $29 "Remote Control for Vista Home Premium" and a $15 Dell Travel Remote Control, IR. I purchased the latter when I ordered my 1520. 


Yap, I've seen it on dell.com but I bought my laptop at dell.com.ar and they don't sell it here (It's the same by phone). Would you buy one for me? LOL.
It's great to know that it works, I'll try to use an old TV remote.

> **linux23dragon said:**
> Posted an Update for all who wish to play with the sound card.   But I must stress, I don't think it will solve the stereo jack output problems.


Hum, too bad, making it work would make it perfect! Thank's for the info, I'll do a fresh install with the alternative CD (my first install was with version 6.10 and then updated to 7.04) and see how it goes.

BTW, is everyone having this problem or it's just a few of us?

Bye!

---

### Post by linux23dragon on 2007-08-29
> **Juanete said:**
> Hum, too bad, making it work would make it perfect! Thank's for the info, I'll do a fresh install with the alternative CD (my first install was with version 6.10 and then updated to 7.04) and see how it goes.

Cool :)

Can you please report if you find that upgrading Ubuntu-6.10 to 7.04 is easier than just installing the alternative CD? 



> **Juanete said:**
> BTW, is everyone having this problem or it's just a few of us?


You mean the Jack audio output?

After looking around on google, it would appear that everyone (no matter what Linux distribution used) has this problem with the 1520.

---

### Post by adromidon on 2007-08-30
Well I can not even get my installation to run it seems that it can not load some driver I am not sure which one but i get an error saying that no sutiable device could be found for installiton

---

### Post by derouge on 2007-08-30
How did you get the multimedia keys working?

---

### Post by linux23dragon on 2007-08-30
> **derouge said:**
> How did you get the multimedia keys working?

The multimedia keys/buttons work without any need for configuration (while in the GUI).  They work great for me.

How are they working for you?

---

### Post by linux23dragon on 2007-08-30
> **adromidon said:**
> Well I can not even get my installation to run it seems that it can not load some driver I am not sure which one but i get an error saying that no sutiable device could be found for installiton

What Ubuntu disk/image did you use?

---

### Post by linux23dragon on 2007-08-30
I've updated the Web cam instructions.  There is no longer any need to patch the driver :)

The Linux-UVC site looks to be bogged down  ATM too :(

---

### Post by Juanete on 2007-08-30
> **linux23dragon said:**
> 
Can you please report if you find that upgrading Ubuntu-6.10 to 7.04 is easier than just installing the alternative CD? 

Sure will do! 

Here's the md5 sum, it's not so easy to find in the webpage. MD5 --> " ff0cc7c9ed5157f0ff8c0f2213973f49 *ubuntu-7.04-alternate-i386.iso "

I think I'll try to install ubuntustudio later. (just in case someone cares and/or have done it before)

> **linux23dragon said:**
> 
You mean the Jack audio output?

After looking around on google, it would appear that everyone (no matter what Linux distribution used) has this problem with the 1520.

I googled it too, all I could find was this thread, I feel famous!!! LOL. 
I'll be waiting to see if this gets solved on 7.10.


Bye! see you after the reinstall!

---

### Post by zidboy on 2007-08-30
**Juanete,** mira tengo el siguiente problema:   Tengo un dell inpiron 1520, le instale Ubuntu Fesity ya que tenia problemas con la tarjeta de video (Nvidia 512), la cosa es que logre instalarlo, pero el problema lo tengo con la tarjeta de sonido, la cual al iniciar el sistema esta en mute siempre.

Lo otro es que escucho por los auidfonos y por los parlantes a la vez y lo manejo por un controlador, asi que si bajo en los audifonos bajo en los parlantes.

cuando ejecuto este comando sale esto:

$ lspci -v | grep Audio00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

Estan todos los paquetes Alsa instalados, pero aun asi no funciona bien.

Admeas este equipo tiene una camara web integrada la cual tampoco e podido configurar ya que los link que encuentro casi siempre estan muertos y no e podido bajar los paquetes de instalacion.

Juanete, si pudieses ayudarme por favor, quiero dejar mi sistema estable y no con pifias.

Saludos

---

### Post by Juanete on 2007-08-30
If you all excuse me, I'll answer this one in spanish. I'm thinking about translating linux23dragon's thread and take it to ubuntu-es if he allows me. 
If you have any complains I'll move this discussion to a spanish talking(writing?) forum.

> **zidboy said:**
> Lo otro es que escucho por los auidfonos y por los parlantes a la vez y lo manejo por un controlador, asi que si bajo en los audifonos bajo en los parlantes.


Primero que nada, ¿como instalaste ubuntu? Yo instale la version 6.10 y despues actualize a 7.04. Cuando detecte el problema me puse a toquetear un poco (lo que aclare en posts anteriores) y asi quedo.
El tema de que siempre arranca en mute no tengo idea como solucionarlo, voy a ver si encuentro algo este finde. 
El problema de los audifonos es con el que he estado renegando desde que instale ubuntu. En mi caso, cuando arranco la PC con los auriculares conectados, suenan solo los auriculares y no los parlantes. Y si no estan conectados cuando arranca la PC, suenan los parlantes y los auriculares todo junto. Segun quien creo este hilo (se ve que sabe muuucho, yo soy nuevo en esto), este problema no tendria solucion. Habra que esperar a que salga la version 7.10 para ver si funciona bien.


> **zidboy said:**
> 
Admeas este equipo tiene una camara web integrada la cual tampoco e podido configurar ya que los link que encuentro casi siempre estan muertos y no e podido bajar los paquetes de instalacion.


La camara la instale como decia en la pagina 1 de este hilo, ahora esta mas resumido, se ve que saco un par de cosas que no hacian falta. En fin, anda a la pagina 1 y esta todo para hacerla andar, para que te funcione con el aMSN tenes que bajar otra version que no esta en los repositorios comunes, algo asi como aMSN svn, buscalo en google que seguro lo encontras, ha y fijate de bajarte el paquete irqloadbalancing como dice por ahi, mejora el rendimiento de los procesadores multicore.

Saludos!

Bye!

---

### Post by jeff_p on 2007-08-30
I am still having audio problems.  I have read the entire thread, and a lot of the suggestions here have helped me.  But, my "headphone jack" still does not work.


I have read some posts that imply that this jack may NEVER work under linux.  Is this the case?  Is there a way that I can troubleshoot this?  Also, are there any work-arounds that I can try?

---

### Post by linux23dragon on 2007-08-30
> **jeff_p said:**
> I am still having audio problems.  I have read the entire thread, and a lot of the suggestions here have helped me.  But, my "headphone jack" still does not work.


I have read some posts that imply that this jack may NEVER work under linux.  Is this the case?  Is there a way that I can troubleshoot this?  Also, are there any work-arounds that I can try?


It will work one day.   Have you filed a bug report yet?
I recommend fileing a bug report about it, as it is the only way people can know that the problem needs to be seen too.

It can be fixed :)

In the mean time, if anyone is willing to figure out a work around for this "headphone jack" problem. please fell free to post.  We can all help and test :)

---

### Post by jeff_p on 2007-08-30
Hello linuxdragon!

I haven't filed a bug report yet...I fear I may have misconfigured my laptop somehow.  I would love to see some alsa-base files from people who have gotten this working!

Apparently, my soundcard is an SB600 Azalia, from ATI.  I have done some searches for solutions in other threads, but none of them have worked.

Here is the stuff I added to alsa-base myself:
--------
options snd-hda-intel model=ref
options snd-hda-intel model=STAC9205
options snd-hda-intel probe_mask=1
options snd-hda-intel model=6stack-digiout
--------

So far, I have the mixer working to control my external laptop speakers.  The mic doesn't work, and neither does the headphone jack.  Can anyone see a mistake that I made?

Thanks!

---

### Post by RandomUsr on 2007-08-31
OK, So I followed the steps for the video card and i get errors starting x
vesa no matching modes 
and
screen found, but none have a useable configuration which is the same thing that happened before
I can boot to bash and that's it

what gives?

---

### Post by linux23dragon on 2007-08-31
> **RandomUsr said:**
> OK, So I followed the steps for the video card and i get errors starting x
vesa no matching modes 
and
screen found, but none have a useable configuration which is the same thing that happened before
I can boot to bash and that's it

what gives?




Please refer to the "**ATI Graphics card owners**" section, found under  the 
_**"Hints on setting up your hardware while installing Ubuntu"**_.


That should fix the issues you are having, no matter what Graphics card you are using.



Can you please tell me what Graphics card you are using?
Are you using the upgrade option (6.10 - 7.04)?

---

### Post by linux23dragon on 2007-08-31
> **Juanete said:**
> If you all excuse me, I'll answer this one in spanish. I'm thinking about translating linux23dragon's thread and take it to ubuntu-es if he allows me. 
If you have any complains I'll move this discussion to a spanish talking(writing?) forum.


Thats an honorable question Juanete.

But I would prefer that I translated the **_Dell Inspiron 1520 with Ubuntu-7.04_** thread.  Then I would be able to sync the information with this original English version.

You know I have the same hint on [linux-profiles.com]("http://www.linux-profiles.com/).  You can imagine how frustrating it would be to users, if all three copy's were out of sync from one another. 

I have been informed that there is a tool I can use to translate documents (over the net).  Does any one know the name for such a tool?

Because I might as well do Germany, France and Greece as well :)


Thanks for the MD5 Sum Juanete.  You have made life easier for a lot of people who care about such things :)

---

### Post by bibou91 on 2007-08-31
Using these softwares actually don't work.

You might prefer have a spanish friend who helps you unless you want to look ridiculous ;)

---

### Post by gideon07 on 2007-08-31
I tried Ubuntu Gutsy.  Here is what I found.

Video Card: Intel Integrated Graphics
[LIST]
[*]Works out of the box
[*]Fonts are scaled by dpi this results in much larger fonts than I would like.  I can alter this if I manually start x with "startx -- -dpi 72".  Does anyone know how to add options to the startx command in the default boot sequence?
[*]in Ubuntu 7.04 it worked only after installing with the alternate install CD and following the directions in this how-to
[/LIST]

Sound Card: Intel 82801H
[LIST]
[*]Does not work.
[*]Initially it appeared to be detected and the multimedia buttons showed the volume changing, but no sound was produced
[*]After installing updates it appears that the sound device is not detected at all
[*]In Ubuntu 7.04 worked flawlessly installing with alternate install CD 
[/LIST]

DVD drive
[LIST]
[*]Works!
[*]In Ubuntu 7.04 worked only after following the directions in this how-to
[/LIST]

Wireless Networking: Broadcom 1390
[LIST]
[*] did not work initially
[*] now works after following [Altimar's instructions]("http://ubuntuforums.org/showthread.php?t=501195&page=22")
[*] In Ubuntu 7.04 followed the same procedure
[/LIST]

Suspend
[LIST]
[*]logs me out when I resume
[*] In Ubuntu 7.04 worked flawlessly out of the box (although it was slower)
[/LIST]

Hibernate
[LIST]
[*]Option doesn't exist in Gutsy
[*]In Ubuntu 7.04 work flawlessly out of the box
[/LIST]

Everything else such as the trackpad works well.  I haven't tested the system exhaustively.

---

### Post by jeff_p on 2007-08-31
Good news for people having trouble with the headphone jack!

In /etc/modprobe.d/alsa-base , put in "snd-hda-intel model=dell-laptop" instead of "snd-hda-intel model=ref".

I did this, and now my headphone jack works properly.  The speakers turn off when I plug my headphones in, and I am happy :)

Now I need to get the mic working!

---

### Post by zidboy on 2007-08-31
> **Juanete said:**
> 
Primero que nada, ¿como instalaste ubuntu? Yo instale la version 6.10 y despues actualize a 7.04. Cuando detecte el problema me puse a toquetear un poco (lo que aclare en posts anteriores) y asi quedo.
El tema de que siempre arranca en mute no tengo idea como solucionarlo, voy a ver si encuentro algo este finde. 

Trate de instalar varias sitribuciones, Kubuntu, Ubuntu, Debian y me resulto con Slackware, pero no tomaba la tarjeta de sonido, asi que en los foros descubri que para instalarlo en el inspiron 1520 habia que hacerlo con Fesity Fawn, asi que lo hice e instale bien mi tarjeta de video, la cosa es que cuando instale el feisty arranco en mute, arregle el sonido y lo volvi a arrancar y sono, pero despues no.....y no se por que.

> **Juanete said:**
> 
El problema de los audifonos es con el que he estado renegando desde que instale ubuntu. En mi caso, cuando arranco la PC con los auriculares conectados, suenan solo los auriculares y no los parlantes. Y si no estan conectados cuando arranca la PC, suenan los parlantes y los auriculares todo junto. Segun quien creo este hilo (se ve que sabe muuucho, yo soy nuevo en esto), este problema no tendria solucion. Habra que esperar a que salga la version 7.10 para ver si funciona bien.

Si dices que existen los mismos problemas habra que esperar hasta la nueva version aunque, estoy viendo la posivilidad de instalar Suse, aunque no me decido aun, ya que Ubuntu es mas amigable, que las otras distribuciones, pero quiero lograr tener mi PC estable


> **Juanete said:**
> 
La camara la instale como decia en la pagina 1 de este hilo, ahora esta mas resumido, se ve que saco un par de cosas que no hacian falta. En fin, anda a la pagina 1 y esta todo para hacerla andar, para que te funcione con el aMSN tenes que bajar otra version que no esta en los repositorios comunes, algo asi como aMSN svn, buscalo en google que seguro lo encontras, ha y fijate de bajarte el paquete irqloadbalancing como dice por ahi, mejora el rendimiento de los procesadores multicore.


Si si tambien lo intenete pero siempre los servidores estan abajo y no logro bajar lo necesario al igual que los de alsa, los tuve que conseguir en otras paginas, ademas cuando bajo los programas en C, para la camara y quiero compilarlos me da un problema al hacer el MAKE....en fin tratare de resolver el problema con la famosa camara.

Un saludo JUANETE y si tienes alguna novedad por ahi me avisas ya que como dije antes quiero dejar el PC filete!!!!, osea estable.

---

### Post by unattached on 2007-08-31
happy to report, that Firewire IEEE1394 is working out of the box with my sony cam and kino. guess you can add this to the list of working hardware..

---

### Post by DarthTibault on 2007-08-31
> **jeff_p said:**
> In /etc/modprobe.d/alsa-base , put in "snd-hda-intel model=**dell-laptop**"

LOL, that is so painfully obvious, how come we didn't see this before :P

---

### Post by bibou91 on 2007-08-31
> **gideon07 said:**
> I tried Ubuntu Gutsy.  Here is what I found.

Video Card: Intel Integrated Graphics
[LIST]
[*]Works out of the box
[*]Fonts are scaled by dpi this results in much larger fonts than I would like.  I can alter this if I manually start x with "startx -- -dpi 72".  Does anyone know how to add options to the startx command in the default boot sequence?
[*]in Ubuntu 7.04 it worked only after installing with the alternate install CD and following the directions in this how-to
[/LIST]

Sound Card: Intel 82801H
[LIST]
[*]Does not work.
[*]Initially it appeared to be detected and the multimedia buttons showed the volume changing, but no sound was produced
[*]After installing updates it appears that the sound device is not detected at all
[*]In Ubuntu 7.04 worked flawlessly installing with alternate install CD 
[/LIST]

DVD drive
[LIST]
[*]Works!
[*]In Ubuntu 7.04 worked only after following the directions in this how-to
[/LIST]

Wireless Networking: Broadcom 1390
[LIST]
[*] did not work initially
[*] now works after following [Altimar's instructions]("http://ubuntuforums.org/showthread.php?t=501195&page=22")
[*] In Ubuntu 7.04 followed the same procedure
[/LIST]

Suspend
[LIST]
[*]logs me out when I resume
[*] In Ubuntu 7.04 worked flawlessly out of the box (although it was slower)
[/LIST]

Hibernate
[LIST]
[*]Option doesn't exist in Gutsy
[*]In Ubuntu 7.04 work flawlessly out of the box
[/LIST]

Everything else such as the trackpad works well.  I haven't tested the system exhaustively.

I've the sound working under gutsy.
Follow the howto in this thread
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/122560](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/122560)
```

sudo apt-get install alsa-source
cd && mkdir alsa-patched && cd alsa-patched
tar -jxvf /usr/src/alsa-driver.tar.bz2
cd modules/alsa-driver/
wget -O alsa-kernel/pci/hda/patch_analog.c http://launchpadlibrarian.net/9021234/patch_analog.c
./configure --with-cards=hda-intel && make
sudo make install
sudo cp ./modules/snd-hda-intel.ko /lib/modules/$( uname -r )/ubuntu/media/snd-hda-intel/
sudo depmod -a
```

Thank you so much for the "dell-laptop" I'm so happy!

---

### Post by linux23dragon on 2007-08-31
Has any one tried to use the following kernel boot options?


"/boot/grub/menu.lst"

```

pci=nommconf idle=poll pci=routeirq
```

---

### Post by linux23dragon on 2007-09-01
> **bibou91 said:**
> Using these softwares actually don't work.

You might prefer have a spanish friend who helps you unless you want to look ridiculous ;)

Well if thats true(?), then I would consider it as an option, since we have a volunteer :)

---

### Post by DarthTibault on 2007-09-01
> **linux23dragon said:**
> [QUOTE=bibou91;3285102]Using these softwares actually don't work.

You might prefer have a spanish friend who helps you unless you want to look ridiculous ;)Well if thats true(?)[/QUOTE]
Have you never tried on-line translations à la Babelfish?? Don't you know any other languages? I mean, languages are HARD :p and very very different. There are a lot of rules, and also a lot of unwritten rules (When I learned English I had to cope with a lot of 'it sounds better'-rules, you can't tell a computer to do that).
So yeah, finding volunteers would be the way to go ;)

---

### Post by DarthTibault on 2007-09-01
There's a kernel update today, I found these in the changelog:

>   * Dell Inspiron 1420 no external audio
    - GIT-SHA dc24b94b0d384a70b400d56f97060351f800c3df
    - Bug #119898
  * Touchpad not recognized on Dell Inspiron 1420
    - GIT-SHA 9cfe7aefbb8d5755a636eb104348175738eb4fe0
    - Bug #129477

---

### Post by alex1974 on 2007-09-01
Yep,
there was a kernel update and now the sound is not working. touchpad is o.k.
any idea?

---

### Post by DarthTibault on 2007-09-01
> **alex1974 said:**
> Yep,
there was a kernel update and now the sound is not working. touchpad is o.k.
any idea?

I'm guessing the update messed with the alsa-base file, so go to  /etc/modprobe.d/alsa-base again,  and give jeff_p's suggestion of using "snd-hda-intel model=dell-laptop" another try.

---

### Post by alex1974 on 2007-09-01
I tried the dell-laptop in the alsa-base but still after reboot sound is not working.

dmesg:
```
[  216.968000] snd_hda_codec: disagrees about version of symbol snd_ctl_add
[  216.968000] snd_hda_codec: Unknown symbol snd_ctl_add
[  216.968000] snd_hda_codec: disagrees about version of symbol snd_ctl_find_id
[  216.968000] snd_hda_codec: Unknown symbol snd_ctl_find_id
[  216.968000] snd_hda_codec: disagrees about version of symbol snd_ctl_new1
[  216.968000] snd_hda_codec: Unknown symbol snd_ctl_new1
[  216.968000] snd_hda_codec: disagrees about version of symbol snd_component_add
[  216.968000] snd_hda_codec: Unknown symbol snd_component_add
[  216.968000] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_list
[  216.968000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_list
[  216.968000] snd_hda_codec: disagrees about version of symbol snd_pcm_hw_constraint_step
[  216.968000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step
[  216.972000] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[  216.972000] snd_hda_intel: Unknown symbol snd_pcm_new
[  216.972000] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[  216.972000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[  216.972000] snd_hda_intel: disagrees about version of symbol snd_card_register
[  216.972000] snd_hda_intel: Unknown symbol snd_card_register
[  216.972000] snd_hda_intel: disagrees about version of symbol snd_card_free
[  216.972000] snd_hda_intel: Unknown symbol snd_card_free
[  216.972000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[  216.972000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[  216.972000] snd_hda_intel: Unknown symbol snd_hda_bus_new
[  216.972000] snd_hda_intel: Unknown symbol snd_hda_build_pcms
[  216.972000] snd_hda_intel: Unknown symbol snd_hda_codec_new
[  216.972000] snd_hda_intel: Unknown symbol snd_hda_queue_unsol_event
[  216.972000] snd_hda_intel: disagrees about version of symbol snd_card_new
[  216.972000] snd_hda_intel: Unknown symbol snd_card_new
[  216.972000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[  216.972000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[  216.972000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[  216.972000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[  216.972000] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[  216.972000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[  216.972000] snd_hda_intel: Unknown symbol snd_hda_calc_stream_format
[  216.972000] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[  216.972000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[  216.972000] snd_hda_intel: Unknown symbol snd_hda_suspend
[  216.972000] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[  216.972000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[  216.972000] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[  216.972000] snd_hda_intel: Unknown symbol snd_card_disconnect
[  216.972000] snd_hda_intel: Unknown symbol snd_hda_resume
[  216.972000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[  216.972000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[  216.972000] snd_hda_intel: Unknown symbol snd_hda_build_controls
[  216.972000] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[  216.972000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[  216.972000] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[  216.972000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
```

has anybody the same problem?

---

### Post by bibou91 on 2007-09-01
If you have done a kernel update, you might consider re-compiling your alsa drivers.


--------

You should try to translate a spanish page in english... with a translator and you'll have your own answer :)

---

### Post by alex1974 on 2007-09-01
did try to reinstall according to the instructions on the first page of the forum. but I get:

```
alex@alex-laptop:~$ sudo update-modules &&
> sudo modprobe snd-hda-intel model=ref ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

a few weeks ago, there was another instruction to set up alsa. they have changed now. could there be a problem?

---

### Post by DarthTibault on 2007-09-01
I can think of two other things:
1) perhaps it correctly autodetects the driver now, but the lines you added in the alsa-base file conflict with the autodetection -> remove those lines
2) it's the same problem as in Gutsy, bibou91 already told us how to fix it ([http://ubuntuforums.org/showpost.php?p=3288090&postcount=273](http://ubuntuforums.org/showpost.php?p=3288090&postcount=273))

I'm only guessing though

[edit]
also check if your speakers aren't muted in volume-control (I read some updates do this).

---

### Post by linux23dragon on 2007-09-01
> **alex1974 said:**
> did try to reinstall according to the instructions on the first page of the forum. but I get:

```
alex@alex-laptop:~$ sudo update-modules &&
> sudo modprobe snd-hda-intel model=ref ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

a few weeks ago, there was another instruction to set up alsa. they have changed now. could there be a problem?


Yea,  I found out that those old instructions rendered the sound card driver useless.  I changed the instructions to fix that issue.

Can you please try using this command

```

sudo modprobe snd-hda-intel ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss
```




Thanks for the report.

EDIT

Can you please try the audio hint I've written?  I've have not yet had the chance to test it on the Dell Inspiron Notebook.  But it should be O.K.
But if you get stuck, or have any questions then please ask.  I (and others) can get you up and running :)

[http://ubuntuforums.org/showthread.php?t=530374&highlight=alsa+intel+hda](http://ubuntuforums.org/showthread.php?t=530374&highlight=alsa+intel+hda)

Eventually The hint will be used for Ubuntu-7.10.  I think all it needs is a copy instruction in the kernel driver section.

---

### Post by linux23dragon on 2007-09-01
> **DarthTibault said:**
> Have you never tried on-line translations à la Babelfish?? Don't you know any other languages? I mean, languages are HARD :p and very very different. There are a lot of rules, and also a lot of unwritten rules (When I learned English I had to cope with a lot of 'it sounds better'-rules, you can't tell a computer to do that).
So yeah, finding volunteers would be the way to go ;)

Then I had better give the go ahead then.  :)

---

### Post by alex1974 on 2007-09-01
```
alex@alex-laptop:~$ sudo modprobe snd-hda-intel ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

---

### Post by linux23dragon on 2007-09-01
> **alex1974 said:**
> ```
alex@alex-laptop:~$ sudo modprobe snd-hda-intel ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

It appears that the kernel you are running is different to the kernel source you had compiled against or something.

can you run this command in the terminal please?
```
$(uname -r)
```

And compare the kernel version to the kernel modules or kernel source you have installed?
Was the kernel source updated?

EDIT

I do hope that the kernel headers are O.K (correct version as well?).  Because I remember that the pakage "linux-libc-dev" was updated too.

---

### Post by linux23dragon on 2007-09-01
> **DarthTibault said:**
> 
2) it's the same problem as in Gutsy, bibou91 already told us how to fix it ([http://ubuntuforums.org/showpost.php?p=3288090&postcount=273](http://ubuntuforums.org/showpost.php?p=3288090&postcount=273))

I'm only guessing though



Yea, the Gusty Alsa Intel driver fix installs the driver in "/lib/modules/$( uname -r )/ubuntu/media/snd-hda-intel"
The default Alsa Intel driver location for Ubuntu-7.04 is  "/lib/modules/$( uname -r )/kernel/sound/pci/hda".


Otherwise the instructions (without the patch) is the same.

---

### Post by alex1974 on 2007-09-01
o.k. I tried your instructions. Now the sound settings are accessible again but still no sound.
dmesg:
hda_intel: azx_get_response timeout, switching to polling mode...
[   18.907000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[   19.343000] hda_intel: azx_get_response timeout, switching to single_cmd mode...

---

### Post by linux23dragon on 2007-09-01
> **alex1974 said:**
> o.k. I tried your instructions. Now the sound settings are accessible again but still no sound.
dmesg:
hda_intel: azx_get_response timeout, switching to polling mode...
[   18.907000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)
[   19.343000] hda_intel: azx_get_response timeout, switching to single_cmd mode...

OK, that is good news.

If you see your sound card information after using this command:
```

cat /proc/asound/cards
```

Then remove the following lines from /etc/modprobe.d/alsa-base

```
options snd-hda-intel model=6stack-digout
options snd-hda-intel probe_mask=1
```

Then reboot.

If that does not work, then try removing this line as well. (Since we are using a newer driver) 

```
options snd-hda-intel model=dell-laptop
```

Of course, make sure that the sound card is not muted.

---

### Post by alex1974 on 2007-09-01
o.k. I removed the lines in the alsa-base. Sound is working on and off. No startup sounds pidgin sounds working, rhythmbox not though the music preview in nautilus is.
I have the feeling that the whole system is a bit shaky after the kernel update.
Sometimes nautilus is refusing to start. A popup says a error occured and nautilus can't work right now. Than the terminal doesn't do what I want. The deskbar applet wants to quit from time to time. Whats going on?
Has anybody the same problems after the update or did I mess things up?
Alex

---

### Post by Exab on 2007-09-01
I installed Kubuntu 7.04 in text mode no problem. Sound worked out of the box, but it was a bit wacky, I couldn't switch the speakers sound off to use headphones. 

I decided to recompile alsa with the lowlatency kernel. Now it all works pretty well, but I can only use headphones in the mic jack with the "Line in as output" switch on. Then I have to disable "Front" output and leave the "Surround" switch on to have output to my headphones.

There's 1 advantage there, there is no parasite sounds in the mic jack like the headphones one. But is this how everyone does it? It seems a bit weird of a set up... isn't there a more intuitive way of doing it?

---

### Post by bibou91 on 2007-09-01
> **alex1974 said:**
> o.k. I removed the lines in the alsa-base. Sound is working on and off. No startup sounds pidgin sounds working, rhythmbox not though the music preview in nautilus is.
I have the feeling that the whole system is a bit shaky after the kernel update.
Sometimes nautilus is refusing to start. A popup says a error occured and nautilus can't work right now. Than the terminal doesn't do what I want. The deskbar applet wants to quit from time to time. Whats going on?
Has anybody the same problems after the update or did I mess things up?
Alex

Why don't you move to gutsy. I don't have much problem with the new distrib.

---

### Post by bibou91 on 2007-09-01
> **Exab said:**
> I installed Kubuntu 7.04 in text mode no problem. Sound worked out of the box, but it was a bit wacky, I couldn't switch the speakers sound off to use headphones. 

I decided to recompile alsa with the lowlatency kernel. Now it all works pretty well, but I can only use headphones in the mic jack with the "Line in as output" switch on. Then I have to disable "Front" output and leave the "Surround" switch on to have output to my headphones.

There's 1 advantage there, there is no parasite sounds in the mic jack like the headphones one. But is this how everyone does it? It seems a bit weird of a set up... isn't there a more intuitive way of doing it?

That's a cool trick dude!

No i don't so. Because it's not the natural way to do it! So i don't think it exists.

---

### Post by linux23dragon on 2007-09-01
> **alex1974 said:**
> o.k. I removed the lines in the alsa-base. Sound is working on and off. No startup sounds pidgin sounds working, rhythmbox not though the music preview in nautilus is.
I have the feeling that the whole system is a bit shaky after the kernel update.
Sometimes nautilus is refusing to start. A popup says a error occured and nautilus can't work right now. Than the terminal doesn't do what I want. The deskbar applet wants to quit from time to time. Whats going on?
Has anybody the same problems after the update or did I mess things up?
Alex


OK there is two more steps we can do.

Check to see if you have any of these two hidden files in your home directory:-
```

~.asoundrc
~.asoundrc.asoundconf
```

If they are there then delete them. And then reboot.

Of course you can also try having "options snd-hda-intel model=reff"  in the alsa-base and remove "options snd-hda-intel model=dell-laptop"

The system should work ok.

If none of these steps work, then please post the output from the following command.

```

ls -la /lib/modules
```


EDIT:  My siters boyfriend is coming over with the 1520 Notebook.  So I'll be testing this new Alsa driver setup later on today.

---

### Post by jbizzler on 2007-09-01
Okay, could you please summarize the whole ALSA configuration for Gutsy? It's hard to decide what to do since there are 3 pages of some things working and some things not.

---

### Post by linux23dragon on 2007-09-01
> **jbizzler said:**
> Okay, could you please summarize the whole ALSA configuration for Gutsy? It's hard to decide what to do since there are 3 pages of some things working and some things not.

_**The current issues with Ubuntu-7.04:**_

Users who had compiled the Alsa driver (before they upgraded the kernel yesterday) are finding that the driver no longer works.

This is because the Alsa driver was compiled against the old kernel version (before yesterdays kernel update).  So those users now need to recompile the Alsa driver (with the updated kernel source), if they want the sound card to work.

This is the current fix for Ubuntu-7.04(if you compiled the driver before the kernel upgrade):-

```
sudo apt-get install libncurses5-dev gettext libncursesw5-dev speex  libspeex-dev liba52-0.7.4-dev libsamplerate0-dev jackd jack-rack libjack0.100.0-dev checkinstall  build-essential linux-headers-$(uname -r) &&
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2 &&
tar xf alsa-driver-1.0.14.tar.bz2 &&
cd alsa-driver-1.0.14 &&
./configure \
--with-sequencer=yes \
--with-oss=yes \
--with-cards=hda-intel &&
make &&
sudo checkinstall &&
cd ../ &&
sudo rm -rf alsa-driver-1.0.14 &&
sudo depmod -ae
```

The default driver location is located at "/lib/modules/$( uname -r )/kernel/sound/pci/hda"



**_The issues with Gusty:_**

The kernel in Gusty has been set up differently to support a bug fix.
More details can be found in this bug report.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/122560](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/122560)

This is the current fix(?) so far:-

```
sudo apt-get install alsa-source
cd && mkdir alsa-patched && cd alsa-patched
tar -jxvf /usr/src/alsa-driver.tar.bz2
cd modules/alsa-driver/
wget -O alsa-kernel/pci/hda/patch_analog.c http://launchpadlibrarian.net/9021234/patch_analog.c
./configure --with-cards=hda-intel && make
sudo make install
sudo cp ./modules/snd-hda-intel.ko /lib/modules/$( uname -r )/ubuntu/media/snd-hda-intel/
sudo depmod -a
```


Note how you need to copy "snd-hda-intel.ko" to "/lib/modules/$( uname -r )/ubuntu/media/snd-hda-intel/"

EDIT: The funny thing is, that the "snd-hda-codec.ko" is not mentioned (in the instructions).  It is normally in the same directory as the "snd-hda-intel.ko"

---

### Post by Juanete on 2007-09-01
Hi again.
I still can't get the headphone jack to work properly, I'v installed ubuntu and ubuntustudio in the last 24 hs, I've done the "dell-laptop" thing, and I still have the same problem. Is there something in my /home partition that may cause this? that's the only thing I kept from my previous install.

BTW, I think that installing 6.10 and upgrading to 7.04 is way easier for a human being (at least after you start the X) than installing it with the alternate CD, the thing is: do I get exactly the same system?

@linux23dragon: ok, as soon as I get some free time I'll start translating.

Bye!

EDIT: 
------------------------------------
~.asoundrc
~.asoundrc.asoundconf
------------------------------------
Nop, they're not there

---

### Post by BoneSaw on 2007-09-01
ahh thanks. i was wondering why my sound didnt work suddenly.

---

### Post by jbizzler on 2007-09-02
Nope, those instructions did me no good. All I did was install the Tribe 5 Alternate CD, ran the software update, and followed those Gutsy instructions there. Now, volume control just says "No volume control GStreamer plugins and/or devices found."

---

### Post by linux23dragon on 2007-09-02
> **jbizzler said:**
> Nope, those instructions did me no good. All I did was install the Tribe 5 Alternate CD, ran the software update, and followed those Gutsy instructions there. Now, volume control just says "No volume control GStreamer plugins and/or devices found."

I have not even looked at Gusty yet.  But to me it seems strange that they don't copy "snd-hda-codec.ko" to the same directory.

Can you try these commands:


```

sudo apt-get install alsa-source
cd && mkdir alsa-patched && cd alsa-patched
tar -jxvf /usr/src/alsa-driver.tar.bz2
cd modules/alsa-driver/
wget -O alsa-kernel/pci/hda/patch_analog.c http://launchpadlibrarian.net/9021234/patch_analog.c
./configure --with-cards=hda-intel  --with-sequencer=yes --with-oss=yes && make
sudo make install
sudo cp ./modules/snd-hda-intel.ko /lib/modules/$( uname -r )/ubuntu/media/snd-hda-intel/
sudo cp (wherever you locate system)/snd-hda-codec.ko /lib/modules/$( uname -r )/ubuntu/media/snd-hda-intel/
sudo depmod -a
```

---

### Post by bash on 2007-09-02
Anyone managed to get this [Cheese](http://www.getdeb.net/search.php?keywords=cheese) working with the webcam?

---

### Post by jbizzler on 2007-09-02
Works now, but I did it at the same time as the latest updates.

Also, Using the Fn+Up and Fn+Down buttons, it stuck at the two lowest brightnesses. Like, if I keep pressing up, and just switches between those two. The only way to get max brightness is to bring it all the way up before I login, then to not mess with it.

And after using ENVY, I had to change xorg.conf a little myself.

Otherwise, this looks like an amazing distribution. Wi-Fi 4965AGN works out-of-the-box.

---

### Post by carminez on 2007-09-02
> **ubun-two said:**
> Anyone managed to get this [Cheese](http://www.getdeb.net/search.php?keywords=cheese) working with the webcam?

Yup, I installed Cheese 0.2.2 and it works just fine for me.

---

### Post by jbizzler on 2007-09-03
Okay, so far looking good. Here's my Inspiron 1520 Gutsy experience summary.

I used the Tribe 5 Alternate i386 to install on an external harddrive so it doesn't screw with the whole MediaDirect craziness. At first, it sets the Grub root values to (hd1,0), but, even though Linux recognizes my external harddrive as sdb, GRUB still wants it to be (hd0,0).

Amazingly, wired ethernet support doesn't work out-of-the-box, yet Wi-Fi does. First thing I did was run the package updater, and then wired ethernet worked.

Rebooted, and the ALSA fix didn't work right away. I had to install build-essentials, then do this whole thing:
```
sudo apt-get install alsa-source
cd && mkdir alsa-patched && cd alsa-patched
tar -jxvf /usr/src/alsa-driver.tar.bz2
cd modules/alsa-driver/
wget -O alsa-kernel/pci/hda/patch_analog.c http://launchpadlibrarian.net/9021234/patch_analog.c
./configure --with-cards=hda-intel && make
sudo make install
sudo cp ./modules/snd-hda-intel.ko /lib/modules/$( uname -r )/ubuntu/media/snd-hda-intel/
sudo depmod -a
```
There's no boot-up sound or snazzy login sound, though I don't know if there's supposed to be. As far as I can tell, everyhting that's supposed to have sound does.

Installed the Envy package, opened /usr/share/envy/instun/classes.py, and changed the line "elif self.details['osname'] == 'cassandra':#SUPPORT FOR LINUX MINT CASSANDRA" to gutsy; "elif self.details['osname'] == 'gutsy':#SUPPORT FOR LINUX MINT CASSANDRA". Ran  Envy and 3D stuff was iffy at first. I don't know exactly what fixed it, but I eventually got it working after playing with xorg.conf.

If I use desktop normal or advanced effects, 3d apps, like Armagetron Advanced, crash the X server, and I'm brought back to the login screen. If I leave it at no effects, though, that game runs fine.

So, bugs aside, very exciting. Hope Tribe 6 Thursday will be much less buggy like this.

---

### Post by RandomUsr on 2007-09-03
OK DUDE. I appreciate the response regarding the Video card install and such. I don't have an ATI Card. Not even sure if this laptop is one of the few with a removeable video card, which I highly doubt.

I bought this thing because it was the best piece of hardware for the price to get Ubuntu Running with XGL, not that I need XGL. I want to install two key Drivers. The intel linux graphics driver for the X3100 and the Intel Wi-Fi Driver which I "assume" to be iwlwifi driver. Note I AM using the 4965 which provides Wireless N Performance.



The graphics driver is here:

[http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)

and the Wifi Driver is here:

[http://intellinuxwireless.org/](http://intellinuxwireless.org/)



I realize that since I bought a pc without Linux this may not be supported by dell, but I figured that some type of help might be available Free or Pay from Ubuntu and possibly Intel since this should all be compatible.
According to the installation instructions on the Intel wireless site, I do need a current Kernel, such as 2.6.18 or later and I would just as soon run 2.6.22 to be safe. How do I make this happen? 

PS I already have the new Kernel up and running.

---

### Post by carminez on 2007-09-03
> **RandomUsr said:**
> OK DUDE. I appreciate the response regarding the Video card install and such. I don't have an ATI Card. Not even sure if this laptop is one of the few with a removeable video card, which I highly doubt.

I bought this thing because it was the best piece of hardware for the price to get Ubuntu Running with XGL, not that I need XGL. I want to install two key Drivers. The intel linux graphics driver for the X3100 and the Intel Wi-Fi Driver which I "assume" to be iwlwifi driver. Note I AM using the 4965 which provides Wireless N Performance.



The graphics driver is here:

[http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)

and the Wifi Driver is here:

[http://intellinuxwireless.org/](http://intellinuxwireless.org/)



I realize that since I bought a pc without Linux this may not be supported by dell, but I figured that some type of help might be available Free or Pay from Ubuntu and possibly Intel since this should all be compatible.
According to the installation instructions on the Intel wireless site, I do need a current Kernel, such as 2.6.18 or later and I would just as soon run 2.6.22 to be safe. How do I make this happen? 

PS I already have the new Kernel up and running.

I have the 4965 also and got it running with ndiswrapper, but it is a little flaky. I followed the instructions from here [https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty?highlight=%284965%29](https://help.ubuntu.com/community/WifiDocs/Driver/Intel_4965_AGN_WiFi_Driver/Fiesty?highlight=%284965%29)
But the ndiswrapper 1.43 was causing intermittent freezing of the whole machine, so I upgraded it to 1.46 and it is more stable, but sometimes the connection seems to drop after a bootup and then after going to ethernet it will be stable for a while. I tried using the iwlwifi driver instead of going the ndiswrapper route and wasn't able to get it working after trying all sorts of different combinations of drivers, I would think if someone can get iwlwifi working it will probably work better than ndiswrapper.

---

### Post by jbizzler on 2007-09-03
To use iwlwifi, you need the Gutsy kernel, which has mac80211. The latest Gutsy beta release, Tribe 5, had my 4965AGN working immediately. However, doing it in Feisty is very complex. I have no clue about Intel graphics.

---

### Post by carminez on 2007-09-03
> **jbizzler said:**
> To use iwlwifi, you need the Gutsy kernel, which has mac80211. The latest Gutsy beta release, Tribe 5, had my 4965AGN working immediately. However, doing it in Feisty is very complex. I have no clue about Intel graphics.

I didn't want to go with the Gutsy kernel for it, which is why i did ndiswrapper.

Have you had any issues with the 4965 in Gutsy? Freezing? Unable to connect? Losing the connection? Do you have security on your router? WEP, WAP, MAC?

---

### Post by RandomUsr on 2007-09-03
As stated above, I don't want to use Gutsy either. I'd rather update the kernel and run the Intel driver Natively using the iwlwifi driver which requires the mac80211 subsystem and Kernel 2.6.18 or later. I believe the 2.6.20 kernel provides the mac subsystem already installed. Further I believe there may be a third part to that wi-fi card working.


As far as the graphics it's a similar store. The X3100 appears to require a 2d and 3d driver. But curiously Intel has also posted a MESA driver. Are these all required for the graphics to work? I would Find it odd to use all three since 2d is a subset of 3d and that MESA driver looks like a seperate facility all-together.

I hate to sound desperate, but I really want to get this working. This laptop is IDEAL for taking advantage of all these technologies. 

I'll be following up shortly.

---

### Post by linux23dragon on 2007-09-03
> **RandomUsr said:**
> As stated above, I don't want to use Gutsy either. I'd rather update the kernel and run the Intel driver Natively using the iwlwifi driver which requires the mac80211 subsystem and Kernel 2.6.18 or later. I believe the 2.6.20 kernel provides the mac subsystem already installed. Further I believe there may be a third part to that wi-fi card working.


As far as the graphics it's a similar store. The X3100 appears to require a 2d and 3d driver. But curiously Intel has also posted a MESA driver. Are these all required for the graphics to work? I would Find it odd to use all three since 2d is a subset of 3d and that MESA driver looks like a seperate facility all-together.

I hate to sound desperate, but I really want to get this working. This laptop is IDEAL for taking advantage of all these technologies. 

I'll be following up shortly.

Mmmm.

Well, Nvidia does use its own OpenGL libs for Xorg.  And it is easy to compile your own kernel if you really need to.  You could use Ubuntu s kernel configuration file (to set up the kernel) if you are not sure on how to configure it yourself (I'm not sure about the 3rd party divides, add ons or fixes).  

The tool chain (gcc, Binutils, libc with (user space) kernel headers) is meant to be built with (and for) the running kernel.  You could upgrade to a newer Linux kernel "BUT".  If the new kernel depends on headers that has been modified (or rewritten), then you will need to upgraded the whole system (or upgrade lots of other programs and headers).  Or face the possibility of having a system that won't work as expected, or the kernel won't finish compiling at all.


Does any one think it would be a good idea to use *.deb, or just forget about using package management to install the new kernel?

Should we give it a go?

EDIT 1:
We will probably have networking issues if you try running linux-2.6.22 (due to the kernel header changes).  We "might" be able to use linux-2.6.21.  
But as I siad.  I don't know how to go about the kernel fixes that Ubuntu has added in.

EDIT 2: 
Of course "EDIT 1" was an option we have.  It is probably best to stick with Linux-2.6.20.

---

### Post by bibou91 on 2007-09-04
I can't manage my webcam to work with cheese. However it works with amsn.

Any ideas? 

I use gutsy

---

### Post by kinanakel on 2007-09-04
Hi,
  Could anyone run the Beryl desktop on this Inspiron 1520 with NVIDIA card installed? What is the xorg file used?
Thanks in advance.

---

### Post by bash on 2007-09-04
> **bibou91 said:**
> I can't manage my webcam to work with cheese. However it works with amsn.

Any ideas? 

I use gutsy

Same. Information in terminal says something about not being able to acces or write to the device

---

### Post by 1idcat on 2007-09-04
I just got my 1520 a few days ago and am looking to put either feisty or sabayon on it.  How is the feisty 'intstall-fest' going in the forum.  Are most people having luck with their installs?

---

### Post by Altimar on 2007-09-05
> **ubun-two said:**
> Same. Information in terminal says something about not being able to acces or write to the device

I'm on feisty with the newest kernel (2.6.20-16) and I had this problem after it worked with the old kernel in amsn. Check if the device is found: ```
ls /dev/video
```

If it's not found, just run through the webcam driver installation instructions at the beginning of this thread. You'll have to do this after every kernel update.

---

### Post by Altimar on 2007-09-05
> **linux23dragon said:**
> OK there is two more steps we can do.

Check to see if you have any of these two hidden files in your home directory:-
```

~.asoundrc
~.asoundrc.asoundconf
```

If they are there then delete them. And then reboot.

Of course you can also try having "options snd-hda-intel model=reff"  in the alsa-base and remove "options snd-hda-intel model=dell-laptop"

The system should work ok.

If none of these steps work, then please post the output from the following command.

```

ls -la /lib/modules
```

Any update on the sound issues? I tried adding those three lines to alsa-base using the 2.6.20-15 kernel, but it still wasn't muting the laptop speakers when I plugged in headphones. Then I updated the kernel  (2.6.20-16) and it still didn't change anything. I have no .asound* files, and I removed the three lines from alsa-base and tried model=ref. I rebooted in between all of these steps and the sound still works the same: laptop speakers are always on and the headphones work if you plug them in.

I tried as suggested to use the mic jack as an output, but it does not have a separate mixer channel. Eg. if I lower the front speaker channel the external speakers connected to the mic input are lowered. So it's the same situation.

This is crazy. I've never had trouble setting up a sound card. I thought intel was good about documenting and supporting their hardware.:confused:

---

### Post by linux23dragon on 2007-09-05
> **Altimar said:**
> Any update on the sound issues? I tried adding those three lines to alsa-base using the 2.6.20-15 kernel, but it still wasn't muting the laptop speakers when I plugged in headphones. Then I updated the kernel  (2.6.20-16) and it still didn't change anything. I have no .asound* files, and I removed the three lines from alsa-base and tried model=ref. I rebooted in between all of these steps and the sound still works the same: laptop speakers are always on and the headphones work if you plug them in.

I tried as suggested to use the mic jack as an output, but it does not have a separate mixer channel. Eg. if I lower the front speaker channel the external speakers connected to the mic input are lowered. So it's the same situation.

This is crazy. I've never had trouble setting up a sound card. I thought intel was good about documenting and supporting their hardware.:confused:


Hi Altimar

I can help getting it configured.  I have not yet tested the outputs yet so I'm not sure if the current driver can be setup correctly.  But I can try some tests to see if Alsa does support the Jack audio outputs (and external input). 

Can we all try and help setup a ~.asoundrc file (or better, a system "/usr/share/alsa/alsa.conf" setup)?

I need all the help from you guys and girls for feed back, as I don't have the Notebook with me.

OK time for some more fun.



Can anyone please use the alsa-base settings used in the first post and reboot.  Then plug this command into the terminal:-

```
sudo cat /proc/asound/devices
```

Please copy/past the output details for us to see.

---

### Post by Altimar on 2007-09-05
alsa-base:
+options snd-hda-intel model=dell-laptop
+options snd-hda-intel model=6stack-digout
+options snd-hda-intel probe_mask=1


# cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 0]: digital audio playback
  5: [ 0- 0]: digital audio capture
  6: [ 0]   : control

It's also the same output as before adding those three lines and rebooting. Just to clarify, I'm running Feisty 2.6.20-16 from the alt CD install and I have NOT compiled alsa myself. Sound quality is great, just the speakers will not mute when headphones are plugged in.

---

### Post by linux23dragon on 2007-09-05
> **Altimar said:**
> alsa-base:
+options snd-hda-intel model=dell-laptop
+options snd-hda-intel model=6stack-digout
+options snd-hda-intel probe_mask=1


# cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 0]: digital audio playback
  5: [ 0- 0]: digital audio capture
  6: [ 0]   : control

It's also the same output as before adding those three lines and rebooting. Just to clarify, I'm running Feisty 2.6.20-16 from the alt CD install and I have NOT compiled alsa myself. Sound quality is great, just the speakers will not mute when headphones are plugged in.

Wow, you don't get many playback or capture devices.

I have found this Intel HDA Wiki article from [alsa.opensrc.org]("http://alsa.opensrc.org/index.php/Hda").  It has lots of model options like:- ```
sudo modprobe snd_hda_intel model=6stack 6-jack in back, 2-jack in front
```

EDIT:  I think that was meant to be ```
sudo modprobe snd_hda_intel model=6stack
``` And that option is meant to provide 6-jack in back, 2-jack in front? 

Oh yea, you might want to unload the current modules first, by using the "-r" like

```
 sudo modprobe -r snd_hda_intel model=6stack-digout &&
 sudo modprobe -r snd-hda-intel model=dell-laptop
``` 



Then see if you get more device options (or test sound outputs). 
```
sudo cat /proc/asound/devices
```

---

### Post by Altimar on 2007-09-06
Removing the modules did not work because "Module snd_hda_intel is in use.", so I tried just "options snd-hda-intel model=6stack" in alsa-base and rebooted. It's still not working and I get the same output from `cat /proc/asound/devices`. 

I have noticed that if I boot up with headphones plugged in, the laptop speakers will be muted (until reboot) while the headphones will work.

Off-topic... Anybody else have trouble with compiz making window titlebars disappear and/or just be very sluggish/crash-prone even with the nvidia binary drivers?

---

### Post by atomicdad on 2007-09-06
I was able to to install the i386 version with little trouble and it seems to be running fairly well right now. But now i'm thinking that I would like the speed provided with the 64 bit version. Does anyone have any experience loading it on the 1520, would the alternate install be similar as described for the 32 bit version?

While I have been a "user" on Linux and Unix systems this is a first for actually installing myself.

---

### Post by linux23dragon on 2007-09-07
> **atomicdad said:**
> I was able to to install the i386 version with little trouble and it seems to be running fairly well right now. But now i'm thinking that I would like the speed provided with the 64 bit version. Does anyone have any experience loading it on the 1520, would the alternate install be similar as described for the 32 bit version?

While I have been a "user" on Linux and Unix systems this is a first for actually installing myself.

Apart from the flash player and possible frame buffer issues (Noted with my Nvidia system), I don't think you will have to many problems.

I'm going to install Ubuntu-7.04 64bit myself today (on my custom built PC).  So I can run both 64bit and 32bit applications.

[COLOR="YellowGreen"]EDIT: I was able to use the VGA option to fix the frame buffer issues when booting up from the live CD .
1024x768 32bit
but I don't think that fixes the issues when you reboot (settings are not saved).  I'm going to find out how to include a boot option to grub once I have finished installing the basic system.  Its possible that a system update might fix the issue as well


EDIT 2: I just finshed installing Ubuntu-7.04 64bit and had boot splash issues.  I searched and found this thread [ubuntu-7.04+64+bit+boot+vga+grub]("http://ubuntuforums.org/showthread.php?t=454392&highlight=ubuntu-7.04+64+bit+boot+vga+grub").  Works well for me.[/COLOR]

Any one have any comments about 64bit Ubuntu?

---

### Post by linux23dragon on 2007-09-07
> **Altimar said:**
> 
Off-topic... Anybody else have trouble with compiz making window titlebars disappear and/or just be very sluggish/crash-prone even with the nvidia binary drivers?

All I can think of is this question.  Is the  "Extensions" set to enabled in /etc/X11/xorg.conf?

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


Any one have the same issues?

---

### Post by linux23dragon on 2007-09-07
UPDATE: (07-09-07) Included more Ubuntu-7.04 64bit hints (Including the Grub boot splash fix).

Please report if you have any issues :)

---

### Post by gideon07 on 2007-09-07
> **atomicdad said:**
> I was able to to install the i386 version with little trouble and it seems to be running fairly well right now. But now i'm thinking that I would like the speed provided with the 64 bit version. Does anyone have any experience loading it on the 1520, would the alternate install be similar as described for the 32 bit version?

While I have been a "user" on Linux and Unix systems this is a first for actually installing myself.

I installed the amd64 version following these same instructions and everything seemed to work fine.  As far as speed is concerned, I did a benchmark test on Matlab with both the 32-bit and 64-bit versions and there was no difference in speed.  This may be because Matlab did not automatically detect that it could use its 64-bit libraries.  Anyone know why uname -i just gives "unknown" in Ubuntu and what to do to obtain the hardware platform from the command-line?

---

### Post by linux23dragon on 2007-09-07
> **gideon07 said:**
> I installed the amd64 version following these same instructions and everything seemed to work fine.

I had issues with my own setup myself.  So I put in some notes just in case someone might have the same issues. 




> **gideon07 said:**
> Anyone know why uname -i just gives "unknown" in Ubuntu and what to do to obtain the hardware platform from the command-line?


Yep.  It is incorrect :)

Install "fastlink" (if you haven't already):-

```
sudo apt-get install fastlink
```

And then try using this command:-

```
 $(uname -i)
```

EDIT:  Correct me if I'm wrong, but I don't think that the kernel 2.6.20 supports (natively) the core2 Duo.

---

### Post by atomicdad on 2007-09-07
Thanks all. I started the install last night, but it was late, I was tired, and had a few beers in me (not a good combination). All seemed to be going well until I tried a first reboot and and it wouldn't let me get into the 64bit version (not enough disk space or something or other). Somehow I screwed up my partitions. It is not all too bad, I still can boot into Vista and the 32bit version, so I didn't bugger things up too much. I am going to try again after a little while but I am going to first wipe out the 32 bit version, repartition the drive and try it clean.

As far as difference between 32bit and 64bit, at work we have several linux workstations that we run model generation and finite element analysis codes. The difference is similar to when many moons ago I ditched my IBM XT machine and got a new Pentium machine ( well almost).:)

---

### Post by Mamsaac on 2007-09-11
Ok, I'm really desperate to have Ubuntu on my laptop and I just can't even install by using Edgy.

It's the inspiron 1520, 2gb of ram, 160gigs of hdd (sata), intel graphics card.

I tried with Ubuntu Feisty live-cd, initially and it didn't work, so I searched and found this topic. After a long time of not being able to download any of the CD images, I finally managed to download them two days ago and burnt them. Honestly, I had a great experience using Edgy... and since this is my school laptop, I can't take any risk on ruining the laptop right now (especially because I have all my projects in here), so I want to try a live-cd before installing anything.

Eventually, I tried the Live-Cd of Edgy (as I thought it was supposed to work, according to what I read in this thread) but it just didn't. It sends me an error with the X server and graphics do not start. After that, it just froze and didn't start anything.

Was Ubuntu Edgy supossed to run out of the box without parameters or should I use some parameters to make it work?

I really need the help, thanks in advance. Any information you need, tell me and I will try to provide it the best as possible.

---

### Post by bibou91 on 2007-09-11
With the live cd  you have to add the line break=top and then when bash won't load: modprobe piix / exit



**Can someone explain me how to set up the modem**... I definatly need it even if i would lose my sound.

---

### Post by bibou91 on 2007-09-11
I forgot to add that's very urgent

---

### Post by DarthTibault on 2007-09-11
> **bibou91 said:**
> **Can someone explain me how to set up the modem**... I definatly need it even if i would lose my sound.

Just follow the link to the add-on packages (it's also in the first post): [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Add-on_Packages](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Add-on_Packages) :roll: 

Did you even look? :-?

[edit] in case you missed it, here are the install instructions from the Dell site:

> * Download the hsfmodem_(version).deb to your desktop.
* Double-click the hsfmodem_(version).deb file. The Package Installer will launch
* Click "Install Package"
* The system prompts you for your system password. Type your password in the password field and press .
* The Installing Package File window appears. Click on the empty right triangle to the left of the word Terminal in the Installing Package File window.
* A terminal window appears within the Installing Package File window. Click anywhere inside the terminal window and press . The system builds the correct driver for your system.
* Press to accept the default when the terminal prompts you to enter a region name for the modem.
* After a few seconds, the name of the window changes from Installing Package File to Installation Finished. Click Close. 

---

### Post by bibou91 on 2007-09-11
or dpkg -i --------.bin ;)
I was worryin more about what /dev it uses... to set up the dial connection.

merci bien.

---

### Post by Mamsaac on 2007-09-11
> **bibou91 said:**
> With the live cd  you have to add the line break=top and then when bash won't load: modprobe piix / exit



**Can someone explain me how to set up the modem**... I definatly need it even if i would lose my sound.

Did as you said, and it didn't work... 

So, what I did was:
-Boot from the cd. Use F6 and added break=top and pressed enter. It started and quickly sent me to a command line.
-There I wrote "modprobe piix" (without "" of course). Did something which was not commented on screen and then I wrote exit. It started to load again. Loaded to things, including checking the file systems.

There the problems started. First, the X server didn't load. Then, after sending the warning message and telling me it would be disabled for now, it went back to what I call "goals" screen (which says "Doing this...[OK] etc...) still showing as last option "Checking file systems [OK]" and it just kept there for 10 minutes... I even went to the kitchen for something to eat because I wanted to give it a chance.

Any information I need to provide to fix this problem will be granted if possible. I really would appreciate more help. Thanks in advance.

---

### Post by Mamsaac on 2007-09-12
Ignore my last posts... I'm already in there :)

Now, the question for me is: what about MediaDirect and Windows Vista? I will have to keep Windows Vista since I got a few programs I need for school. Will be any problems with the partitions? I think I'm gonna have a few problems with them :S

Right now, the partitions are like this:

sda1.- (SOME DELL UTILITIES) FAT16, 47mb
sda2.-(VISTA) NTFS 45gb
sda3 (EXTENDED){
-------sda4.-FAT32 102gb
-------sda5.-(MEDIA DIRECT) fat32 2gb
}

I think I will need some help in this thing, because I personally have no idea about how Media Direct works.

Also, is installation from Edgy safe and quickly? Other than the X Server (I just read the two notes about it) and graphics... is there anything else to note?

---

### Post by DarthTibault on 2007-09-12
> **bibou91 said:**
> or dpkg -i --------.bin ;)
I was worryin more about what /dev it uses... to set up the dial connection.

merci bien.

Ah well, I haven't tried it myself, but for the setting up part:
I think it's as simple as going to System->Administration->Network
Type your password, and configure the modem.

If you need the cli way to do it I can't help you, never used a modem in Linux.

---

### Post by Altimar on 2007-09-12
> **Mamsaac said:**
> Now, the question for me is: what about MediaDirect and Windows Vista? I will have to keep Windows Vista since I got a few programs I need for school. Will be any problems with the partitions? I think I'm gonna have a few problems with them :S

Right now, the partitions are like this:

sda1.- (SOME DELL UTILITIES) FAT16, 47mb
sda2.-(VISTA) NTFS 45gb
sda3 (EXTENDED){
-------sda4.-FAT32 102gb
-------sda5.-(MEDIA DIRECT) fat32 2gb
}

I think I will need some help in this thing, because I personally have no idea about how Media Direct works.

I just wanted to warn you about the MediaDirect button. I'm still not entirely sure what it does, but if you have changed the partition table from the way it is shipped and you press that button, it may hose all your partitions. I'm getting tired of recreating and re-imaging my partitions. :-(  Thank God for PartImage and a USB HDD. :-)

I ended up giving up on the MediaDirect partition. I have read various accounts of people keeping it and modifying the windows boot loader to also boot linux. I don't want to go that route and wouldn't miss MediaDirect any more than vista. I am personally looking into installing DSL or Puppy to quickly boot and watch DVDs or view photos, etc. Maybe even install it to an SD card (quicker than HDD?).

Other things I have learned (please avoid my mistakes) is that an OEM full install XP Pro CD will not install on this computer. It flashes "Setup is inspecting your hardware" for a second then blank screen and CD spins down. 

Also that windows 2000 doesn't really care for partitions created by linux. It wouldn't install on the partition I had created for it, nor on a newly created one from the unpartitioned space I had left. I gave up and upon reboot, Grub on the MBR was gone. I reinstalled it and Ubuntu started booting, but it wouldn't log me in because the /home partition was MIA (as well as /data ). At this point, I booted the 2000 CD (slipstreamed w/ SATA drivers as was my XP CD) and deleted all partitions, created a new one, installed on it and used windows to recreate all my old partitions. Then I PartImaged my linux partitions back and reinstalled Grub and I was good to go. Phew! Everything's back to normal, but it's extremely aggravating that windows would destroy the partition table because it didn't understand it. Unless I'm just an idiot... Anyway, moral of the story: Backup first!

---

### Post by Mamsaac on 2007-09-12
Ok... The thing is, I really don't understand what the hell MediaDirect does.

What I know is:
A few weeks ago I resized my Windows Vista partition, deleted the Back Up partition (10gb) and moved the WV partition to the left. Created a partition after the Windows Vista partition that filled everything. When I tried to load Vista again, it wouldn't because it was b eing detected as D: and not as C:. D: is read as a data partition and thus, the OS didn't load. Since I couldn't load Ubuntu Feisty and I didn't have Edgy, I didn't know what to do... I checked on GParted and it still had the boot flag and was detected with the "OS" thing... I had no idea about what to do, and since I had all the important archives backed up, I decided to reinstall mediadirect and create the partitions by using it.

What would happen if I decided to delete MediaDirect's partition (all the extended partition)? Would booting Windows Vista screw up? As long as I don't have everything installed on Ubuntu I don't want to risk losing Windows Vista, since I use my laptop for school every day.

How should I delete/create/move/resize partitions in order to install Ubuntu? A recommended partition list would be helpful.

---

### Post by Metaleks on 2007-09-13
I would rather wait for 7.10 to come out, a few more weeks!  It looks more promising.  However, would you guys recommend that I stick with Ubuntu 6.10 until then?  Are there any known issues with the Inspirion 1520 and Ubuntu 6.10?  I'm hesitant to install 7.04 on my laptop, which is why I'm asking.  Seems that there are a lot of issues.

---

### Post by Juanete on 2007-09-13
> **Mamsaac said:**
> Ignore my last posts... I'm already in there :)

Now, the question for me is: what about MediaDirect and Windows Vista? I will have to keep Windows Vista since I got a few programs I need for school. Will be any problems with the partitions? I think I'm gonna have a few problems with them :S

Right now, the partitions are like this:

sda1.- (SOME DELL UTILITIES) FAT16, 47mb
sda2.-(VISTA) NTFS 45gb
sda3 (EXTENDED){
-------sda4.-FAT32 102gb
-------sda5.-(MEDIA DIRECT) fat32 2gb
}

I think I will need some help in this thing, because I personally have no idea about how Media Direct works.

Also, is installation from Edgy safe and quickly? Other than the X Server (I just read the two notes about it) and graphics... is there anything else to note?

Hi there! This is how I've arranged my partition table, Ubuntu Studio works great, Vista works as great as it can and Media Direct works properly too (and I have a separate /home partition)

sda1 - DELL
sda2 - WVista
sda4 -  /
sda3 - Extended part (can't have more than 4 primary partitions on a  single HDD)
-sda8 - /home
-sda7 - Swap
-sda5 - Music and stuff (it's FAT so I can access the partition from lin and WV)
-sda6 - DELL


Bye!

---

### Post by Mamsaac on 2007-09-13
> **Juanete said:**
> Hi there! This is how I've arranged my partition table, Ubuntu Studio works great, Vista works as great as it can and Media Direct works properly too (and I have a separate /home partition)

sda1 - DELL
sda2 - WVista
sda4 -  /
sda3 - Extended part (can't have more than 4 primary partitions on a  single HDD)
-sda8 - /home
-sda7 - Swap
-sda5 - Music and stuff (it's FAT so I can access the partition from lin and WV)
-sda6 - DELL


Bye!

Thanks. I don't understand perfectly how extended partitions work, but that's something I will have to read myself (don't worry on giving me any links, it would be a shame if I didn't look for that myself).

As you already know my partitions... would this work without messing anything up?

sda1.- (SOME DELL UTILITIES) FAT16, 47mb
sda2.-(VISTA) NTFS 33gb
------- / Ext3 12gb
sda3 (EXTENDED){
------- /home Ext3 12gb
------- swap 4gb
------- FAT32 86gb
-------sda5.-(MEDIA DIRECT) fat32 2gb
}

What I would try to do, is only:
INSIDE THE EXTENDED PARTITION{
1.-Delete the existant FAT 32 partition
2.-Create an Ext3 Partition 12gb size
3.-create a swap partition of 4gb
4.-Create a FAT32 partition of 86gb
}
5.-Resize de NTFS partition from 45gb to 33gb.
6.-Create an Ext3 partition
7.-Install Edgy and use the first Ext3 partition as root, the Ext3 partition inside the extended as /home and the swap...

Would it work and not mess up the MBR?

Does anyone know what MediaDirect does to the MBR? I think that's where I get lost and freak out a little bit. I'm afraid that after installing Ubuntu Edgy, access to Windows Vista will mess up.

And thanks for all the help, I really feel lost from time to time :)

---

### Post by hellmet on 2007-09-14
I've an Inspiron 1520 that I got two days back. When I tried the code for Intel from the first post, I still am not able to get into X. When I try reconfiguring xserver, it says it didn't find any Graphical device at all. Maybe I'm missing something.. please help me guys.

---

### Post by linux23dragon on 2007-09-14
> **hellmet said:**
> I've an Inspiron 1520 that I got two days back. When I tried the code for Intel from the first post, I still am not able to get into X. When I try reconfiguring xserver, it says it didn't find any Graphical device at all. Maybe I'm missing something.. please help me guys.


Please post the Xorg.0.log.

---

### Post by hellmet on 2007-09-14
```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 13 22:41:05 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    /usr/share/fonts/X11/misc,
    /usr/X11R6/lib/X11/fonts/misc,
    /usr/share/fonts/X11/cyrillic,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/X11R6/lib/X11/fonts/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.3
    X.Org Video Driver: 1.1
    X.Org XInput driver : 0.7
    X.Org Server Extension : 0.3
    X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.1
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2a00 card 1028,01f1 rev 0c class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2a02 card 1028,01f1 rev 0c class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,2a03 card 1028,01f1 rev 0c class 03,80,00 hdr 80
(II) PCI: 00:1a:0: chip 8086,2834 card 1028,01f1 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card 1028,01f1 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card 1028,01f1 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,284b card 1028,01f1 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,283f card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,2841 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,2845 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2830 card 1028,01f1 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card 1028,01f1 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card 1028,01f1 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card 1028,01f1 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev f2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2815 card 1028,01f1 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,2850 card 1028,01f1 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,2828 card 1028,01f1 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,283e card 1028,01f1 rev 02 class 0c,05,00 hdr 00
(II) PCI: 03:00:0: chip 14e4,170c card 1028,01f1 rev 02 class 02,00,00 hdr 00
(II) PCI: 03:01:0: chip 1180,0832 card 1028,01f1 rev 05 class 0c,00,10 hdr 80
(II) PCI: 03:01:1: chip 1180,0822 card 1028,01f1 rev 22 class 08,05,01 hdr 80
(II) PCI: 03:01:2: chip 1180,0843 card 1028,01f1 rev 12 class 08,80,00 hdr 80
(II) PCI: 03:01:3: chip 1180,0592 card 1028,01f1 rev 12 class 08,80,00 hdr 80
(II) PCI: 03:01:4: chip 1180,0852 card 1028,01f1 rev 12 class 08,80,00 hdr 80
(II) PCI: 0c:00:0: chip 8086,4222 card 8086,1020 rev 02 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,13), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 11: bridge is at (0:28:0), (0,11,11), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 12: bridge is at (0:28:1), (0,12,12), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 12 non-prefetchable memory range:
    [0] -1    0    0xfe800000 - 0xfe8fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 13: bridge is at (0:28:3), (0,13,14), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 13 I/O range:
    [0] -1    0    0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 13 non-prefetchable memory range:
    [0] -1    0    0xfe600000 - 0xfe7fffff (0x200000) MX[B]
(II) Bus 13 prefetchable memory range:
    [0] -1    0    0xf0000000 - 0xf01fffff (0x200000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
    [0] -1    0    0xfe500000 - 0xfe5fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation Mobile Integrated Graphics Controller rev 12, Mem @ 0xfea00000/20, 0xe0000000/28, I/O @ 0xefe8/3
(--) PCI: (0:2:1) Intel Corporation Mobile Integrated Graphics Controller rev 12, Mem @ 0xfeb00000/20
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
    [0] -1    0    0xfe8ff000 - 0xfe8fffff (0x1000) MX[B]
    [1] -1    0    0xfe5fd700 - 0xfe5fd7ff (0x100) MX[B]
    [2] -1    0    0xfe5fd600 - 0xfe5fd6ff (0x100) MX[B]
    [3] -1    0    0xfe5fd500 - 0xfe5fd5ff (0x100) MX[B]
    [4] -1    0    0xfe5fd400 - 0xfe5fd4ff (0x100) MX[B]
    [5] -1    0    0xfe5fd800 - 0xfe5fdfff (0x800) MX[B]
    [6] -1    0    0xfe5fe000 - 0xfe5fffff (0x2000) MX[B]
    [7] -1    0    0xfe9fbf00 - 0xfe9fbfff (0x100) MX[B]
    [8] -1    0    0xfed1c000 - 0xfed1c3ff (0x400) MX[B]
    [9] -1    0    0xfe9fc000 - 0xfe9fffff (0x4000) MX[B]
    [10] -1    0    0xfed1c400 - 0xfed1c7ff (0x400) MX[B]
    [11] -1    0    0xfeb00000 - 0xfebfffff (0x100000) MX[B](B)
    [12] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
    [13] -1    0    0xfea00000 - 0xfeafffff (0x100000) MX[B](B)
    [14] -1    0    0x000010c0 - 0x000010df (0x20) IX[B]
    [15] -1    0    0x0000eff0 - 0x0000efff (0x10) IX[B]
    [16] -1    0    0x00006ee0 - 0x00006eef (0x10) IX[B]
    [17] -1    0    0x00006ec8 - 0x00006ecb (0x4) IX[B]
    [18] -1    0    0x00006ec0 - 0x00006ec7 (0x8) IX[B]
    [19] -1    0    0x00006eb8 - 0x00006ebb (0x4) IX[B]
    [20] -1    0    0x00006eb0 - 0x00006eb7 (0x8) IX[B]
    [21] -1    0    0x00006fa0 - 0x00006faf (0x10) IX[B]
    [22] -1    0    0x00000374 - 0x00000374 (0x1) IX[B]
    [23] -1    0    0x00000170 - 0x00000177 (0x8) IX[B]
    [24] -1    0    0x000003f4 - 0x000003f4 (0x1) IX[B]
    [25] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [26] -1    0    0x00006f40 - 0x00006f5f (0x20) IX[B]
    [27] -1    0    0x00006f60 - 0x00006f7f (0x20) IX[B]
    [28] -1    0    0x00006f80 - 0x00006f9f (0x20) IX[B]
    [29] -1    0    0x00006f00 - 0x00006f1f (0x20) IX[B]
    [30] -1    0    0x00006f20 - 0x00006f3f (0x20) IX[B]
    [31] -1    0    0x0000efe8 - 0x0000efef (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xfe8ff000 - 0xfe8fffff (0x1000) MX[B]
    [1] -1    0    0xfe5fd700 - 0xfe5fd7ff (0x100) MX[B]
    [2] -1    0    0xfe5fd600 - 0xfe5fd6ff (0x100) MX[B]
    [3] -1    0    0xfe5fd500 - 0xfe5fd5ff (0x100) MX[B]
    [4] -1    0    0xfe5fd400 - 0xfe5fd4ff (0x100) MX[B]
    [5] -1    0    0xfe5fd800 - 0xfe5fdfff (0x800) MX[B]
    [6] -1    0    0xfe5fe000 - 0xfe5fffff (0x2000) MX[B]
    [7] -1    0    0xfe9fbf00 - 0xfe9fbfff (0x100) MX[B]
    [8] -1    0    0xfed1c000 - 0xfed1c3ff (0x400) MX[B]
    [9] -1    0    0xfe9fc000 - 0xfe9fffff (0x4000) MX[B]
    [10] -1    0    0xfed1c400 - 0xfed1c7ff (0x400) MX[B]
    [11] -1    0    0xfeb00000 - 0xfebfffff (0x100000) MX[B](B)
    [12] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
    [13] -1    0    0xfea00000 - 0xfeafffff (0x100000) MX[B](B)
    [14] -1    0    0x000010c0 - 0x000010df (0x20) IX[B]
    [15] -1    0    0x0000eff0 - 0x0000efff (0x10) IX[B]
    [16] -1    0    0x00006ee0 - 0x00006eef (0x10) IX[B]
    [17] -1    0    0x00006ec8 - 0x00006ecb (0x4) IX[B]
    [18] -1    0    0x00006ec0 - 0x00006ec7 (0x8) IX[B]
    [19] -1    0    0x00006eb8 - 0x00006ebb (0x4) IX[B]
    [20] -1    0    0x00006eb0 - 0x00006eb7 (0x8) IX[B]
    [21] -1    0    0x00006fa0 - 0x00006faf (0x10) IX[B]
    [22] -1    0    0x00000374 - 0x00000374 (0x1) IX[B]
    [23] -1    0    0x00000170 - 0x00000177 (0x8) IX[B]
    [24] -1    0    0x000003f4 - 0x000003f4 (0x1) IX[B]
    [25] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [26] -1    0    0x00006f40 - 0x00006f5f (0x20) IX[B]
    [27] -1    0    0x00006f60 - 0x00006f7f (0x20) IX[B]
    [28] -1    0    0x00006f80 - 0x00006f9f (0x20) IX[B]
    [29] -1    0    0x00006f00 - 0x00006f1f (0x20) IX[B]
    [30] -1    0    0x00006f20 - 0x00006f3f (0x20) IX[B]
    [31] -1    0    0x0000efe8 - 0x0000efef (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xfe8ff000 - 0xfe8fffff (0x1000) MX[B]
    [5] -1    0    0xfe5fd700 - 0xfe5fd7ff (0x100) MX[B]
    [6] -1    0    0xfe5fd600 - 0xfe5fd6ff (0x100) MX[B]
    [7] -1    0    0xfe5fd500 - 0xfe5fd5ff (0x100) MX[B]
    [8] -1    0    0xfe5fd400 - 0xfe5fd4ff (0x100) MX[B]
    [9] -1    0    0xfe5fd800 - 0xfe5fdfff (0x800) MX[B]
    [10] -1    0    0xfe5fe000 - 0xfe5fffff (0x2000) MX[B]
    [11] -1    0    0xfe9fbf00 - 0xfe9fbfff (0x100) MX[B]
    [12] -1    0    0xfed1c000 - 0xfed1c3ff (0x400) MX[B]
    [13] -1    0    0xfe9fc000 - 0xfe9fffff (0x4000) MX[B]
    [14] -1    0    0xfed1c400 - 0xfed1c7ff (0x400) MX[B]
    [15] -1    0    0xfeb00000 - 0xfebfffff (0x100000) MX[B](B)
    [16] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
    [17] -1    0    0xfea00000 - 0xfeafffff (0x100000) MX[B](B)
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [19] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [20] -1    0    0x000010c0 - 0x000010df (0x20) IX[B]
    [21] -1    0    0x0000eff0 - 0x0000efff (0x10) IX[B]
    [22] -1    0    0x00006ee0 - 0x00006eef (0x10) IX[B]
    [23] -1    0    0x00006ec8 - 0x00006ecb (0x4) IX[B]
    [24] -1    0    0x00006ec0 - 0x00006ec7 (0x8) IX[B]
    [25] -1    0    0x00006eb8 - 0x00006ebb (0x4) IX[B]
    [26] -1    0    0x00006eb0 - 0x00006eb7 (0x8) IX[B]
    [27] -1    0    0x00006fa0 - 0x00006faf (0x10) IX[B]
    [28] -1    0    0x00000374 - 0x00000374 (0x1) IX[B]
    [29] -1    0    0x00000170 - 0x00000177 (0x8) IX[B]
    [30] -1    0    0x000003f4 - 0x000003f4 (0x1) IX[B]
    [31] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [32] -1    0    0x00006f40 - 0x00006f5f (0x20) IX[B]
    [33] -1    0    0x00006f60 - 0x00006f7f (0x20) IX[B]
    [34] -1    0    0x00006f80 - 0x00006f9f (0x20) IX[B]
    [35] -1    0    0x00006f00 - 0x00006f1f (0x20) IX[B]
    [36] -1    0    0x00006f20 - 0x00006f3f (0x20) IX[B]
    [37] -1    0    0x0000efe8 - 0x0000efef (0x8) IX[B](B)
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 7.2.0, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.1.0
    ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "i810"
(II) Loading /usr/lib/xorg/modules/drivers//i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 14.94.94
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.1.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
    compiled for 4.3.99.902, module version = 1.0.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
    compiled for 4.2.0, module version = 1.0.0
    Module class: XFree86 XInput Driver
    ABI class: XFree86 XInput driver, version 0.3
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ, 965GM,
    G33, Q35, Q33
(II) Primary Device is: PCI 00:02:0
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset 965GM found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xfe8ff000 - 0xfe8fffff (0x1000) MX[B]
    [5] -1    0    0xfe5fd700 - 0xfe5fd7ff (0x100) MX[B]
    [6] -1    0    0xfe5fd600 - 0xfe5fd6ff (0x100) MX[B]
    [7] -1    0    0xfe5fd500 - 0xfe5fd5ff (0x100) MX[B]
    [8] -1    0    0xfe5fd400 - 0xfe5fd4ff (0x100) MX[B]
    [9] -1    0    0xfe5fd800 - 0xfe5fdfff (0x800) MX[B]
    [10] -1    0    0xfe5fe000 - 0xfe5fffff (0x2000) MX[B]
    [11] -1    0    0xfe9fbf00 - 0xfe9fbfff (0x100) MX[B]
    [12] -1    0    0xfed1c000 - 0xfed1c3ff (0x400) MX[B]
    [13] -1    0    0xfe9fc000 - 0xfe9fffff (0x4000) MX[B]
    [14] -1    0    0xfed1c400 - 0xfed1c7ff (0x400) MX[B]
    [15] -1    0    0xfeb00000 - 0xfebfffff (0x100000) MX[B](B)
    [16] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
    [17] -1    0    0xfea00000 - 0xfeafffff (0x100000) MX[B](B)
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [19] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [20] -1    0    0x000010c0 - 0x000010df (0x20) IX[B]
    [21] -1    0    0x0000eff0 - 0x0000efff (0x10) IX[B]
    [22] -1    0    0x00006ee0 - 0x00006eef (0x10) IX[B]
    [23] -1    0    0x00006ec8 - 0x00006ecb (0x4) IX[B]
    [24] -1    0    0x00006ec0 - 0x00006ec7 (0x8) IX[B]
    [25] -1    0    0x00006eb8 - 0x00006ebb (0x4) IX[B]
    [26] -1    0    0x00006eb0 - 0x00006eb7 (0x8) IX[B]
    [27] -1    0    0x00006fa0 - 0x00006faf (0x10) IX[B]
    [28] -1    0    0x00000374 - 0x00000374 (0x1) IX[B]
    [29] -1    0    0x00000170 - 0x00000177 (0x8) IX[B]
    [30] -1    0    0x000003f4 - 0x000003f4 (0x1) IX[B]
    [31] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [32] -1    0    0x00006f40 - 0x00006f5f (0x20) IX[B]
    [33] -1    0    0x00006f60 - 0x00006f7f (0x20) IX[B]
    [34] -1    0    0x00006f80 - 0x00006f9f (0x20) IX[B]
    [35] -1    0    0x00006f00 - 0x00006f1f (0x20) IX[B]
    [36] -1    0    0x00006f20 - 0x00006f3f (0x20) IX[B]
    [37] -1    0    0x0000efe8 - 0x0000efef (0x8) IX[B](B)
(II) resource ranges after probing:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xfe8ff000 - 0xfe8fffff (0x1000) MX[B]
    [5] -1    0    0xfe5fd700 - 0xfe5fd7ff (0x100) MX[B]
    [6] -1    0    0xfe5fd600 - 0xfe5fd6ff (0x100) MX[B]
    [7] -1    0    0xfe5fd500 - 0xfe5fd5ff (0x100) MX[B]
    [8] -1    0    0xfe5fd400 - 0xfe5fd4ff (0x100) MX[B]
    [9] -1    0    0xfe5fd800 - 0xfe5fdfff (0x800) MX[B]
    [10] -1    0    0xfe5fe000 - 0xfe5fffff (0x2000) MX[B]
    [11] -1    0    0xfe9fbf00 - 0xfe9fbfff (0x100) MX[B]
    [12] -1    0    0xfed1c000 - 0xfed1c3ff (0x400) MX[B]
    [13] -1    0    0xfe9fc000 - 0xfe9fffff (0x4000) MX[B]
    [14] -1    0    0xfed1c400 - 0xfed1c7ff (0x400) MX[B]
    [15] -1    0    0xfeb00000 - 0xfebfffff (0x100000) MX[B](B)
    [16] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
    [17] -1    0    0xfea00000 - 0xfeafffff (0x100000) MX[B](B)
    [18] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [19] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [20] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [21] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [22] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [23] -1    0    0x000010c0 - 0x000010df (0x20) IX[B]
    [24] -1    0    0x0000eff0 - 0x0000efff (0x10) IX[B]
    [25] -1    0    0x00006ee0 - 0x00006eef (0x10) IX[B]
    [26] -1    0    0x00006ec8 - 0x00006ecb (0x4) IX[B]
    [27] -1    0    0x00006ec0 - 0x00006ec7 (0x8) IX[B]
    [28] -1    0    0x00006eb8 - 0x00006ebb (0x4) IX[B]
    [29] -1    0    0x00006eb0 - 0x00006eb7 (0x8) IX[B]
    [30] -1    0    0x00006fa0 - 0x00006faf (0x10) IX[B]
    [31] -1    0    0x00000374 - 0x00000374 (0x1) IX[B]
    [32] -1    0    0x00000170 - 0x00000177 (0x8) IX[B]
    [33] -1    0    0x000003f4 - 0x000003f4 (0x1) IX[B]
    [34] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [35] -1    0    0x00006f40 - 0x00006f5f (0x20) IX[B]
    [36] -1    0    0x00006f60 - 0x00006f7f (0x20) IX[B]
    [37] -1    0    0x00006f80 - 0x00006f9f (0x20) IX[B]
    [38] -1    0    0x00006f00 - 0x00006f1f (0x20) IX[B]
    [39] -1    0    0x00006f20 - 0x00006f3f (0x20) IX[B]
    [40] -1    0    0x0000efe8 - 0x0000efef (0x8) IX[B](B)
    [41] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [42] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 0.1.0
    ABI class: X.Org Video Driver, version 1.1
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
(--) intel(0): Chipset: "965GM"
(--) intel(0): Linear framebuffer at 0xE0000000
(--) intel(0): IO registers at addr 0xFEA00000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using XAA for acceleration
(--) intel(0): Will try to allocate texture pool for old Mesa 3D driver.
(II) intel(0): Will try to reserve 32768 kiB of AGP aperture space
    for the DRM memory manager.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.2.0
    ABI class: X.Org Video Driver, version 1.1
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "SEC", prod id 12631
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.1
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 7616 kB
(II) intel(0): VESA VBE OEM: Intel(r)GM965/PM965/GL960 Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r)GM965/PM965/GL960 Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "SEC", prod id 12631
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 512 kB GTT.
(II) intel(0): detected 7676 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(++) intel(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.2.0
    ABI class: X.Org Video Driver, version 1.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 0.1.0
    ABI class: X.Org Video Driver, version 1.1
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd0000009
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] 0    0    0xe0000000 - 0xefffffff (0x10000000) MS[B]
    [1] 0    0    0xfea00000 - 0xfeafffff (0x100000) MS[B]
    [2] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [3] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [4] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [5] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [6] -1    0    0xfe8ff000 - 0xfe8fffff (0x1000) MX[B]
    [7] -1    0    0xfe5fd700 - 0xfe5fd7ff (0x100) MX[B]
    [8] -1    0    0xfe5fd600 - 0xfe5fd6ff (0x100) MX[B]
    [9] -1    0    0xfe5fd500 - 0xfe5fd5ff (0x100) MX[B]
    [10] -1    0    0xfe5fd400 - 0xfe5fd4ff (0x100) MX[B]
    [11] -1    0    0xfe5fd800 - 0xfe5fdfff (0x800) MX[B]
    [12] -1    0    0xfe5fe000 - 0xfe5fffff (0x2000) MX[B]
    [13] -1    0    0xfe9fbf00 - 0xfe9fbfff (0x100) MX[B]
    [14] -1    0    0xfed1c000 - 0xfed1c3ff (0x400) MX[B]
    [15] -1    0    0xfe9fc000 - 0xfe9fffff (0x4000) MX[B]
    [16] -1    0    0xfed1c400 - 0xfed1c7ff (0x400) MX[B]
    [17] -1    0    0xfeb00000 - 0xfebfffff (0x100000) MX[B](B)
    [18] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
    [19] -1    0    0xfea00000 - 0xfeafffff (0x100000) MX[B](B)
    [20] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
    [21] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
    [22] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
    [23] 0    0    0x0000efe8 - 0x0000efef (0x8) IS[B]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [25] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [26] -1    0    0x000010c0 - 0x000010df (0x20) IX[B]
    [27] -1    0    0x0000eff0 - 0x0000efff (0x10) IX[B]
    [28] -1    0    0x00006ee0 - 0x00006eef (0x10) IX[B]
    [29] -1    0    0x00006ec8 - 0x00006ecb (0x4) IX[B]
    [30] -1    0    0x00006ec0 - 0x00006ec7 (0x8) IX[B]
    [31] -1    0    0x00006eb8 - 0x00006ebb (0x4) IX[B]
    [32] -1    0    0x00006eb0 - 0x00006eb7 (0x8) IX[B]
    [33] -1    0    0x00006fa0 - 0x00006faf (0x10) IX[B]
    [34] -1    0    0x00000374 - 0x00000374 (0x1) IX[B]
    [35] -1    0    0x00000170 - 0x00000177 (0x8) IX[B]
    [36] -1    0    0x000003f4 - 0x000003f4 (0x1) IX[B]
    [37] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [38] -1    0    0x00006f40 - 0x00006f5f (0x20) IX[B]
    [39] -1    0    0x00006f60 - 0x00006f7f (0x20) IX[B]
    [40] -1    0    0x00006f80 - 0x00006f9f (0x20) IX[B]
    [41] -1    0    0x00006f00 - 0x00006f1f (0x20) IX[B]
    [42] -1    0    0x00006f20 - 0x00006f3f (0x20) IX[B]
    [43] -1    0    0x0000efe8 - 0x0000efef (0x8) IX[B](B)
    [44] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
    [45] 0    0    0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(EE) GARTInit: Unable to open /dev/agpgart (No such file or directory)
(WW) intel(0): /dev/agpgart is either not available, or no memory is available
for allocation.  Using pre-allocated memory only.
(**) intel(0): VideoRam: 7676 KB
(II) intel(0): Attempting memory allocation with tiled buffers and 
           large DRI memory manager reservation:
(II) intel(0): Allocating 5680 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(II) intel(0): Attempting memory allocation with tiled buffers and 
           small DRI memory manager reservation:
(II) intel(0): Allocating 5680 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(II) intel(0): Attempting memory allocation with untiled buffers and 
           large DRI memory manager reservation:
(II) intel(0): Allocating 5740 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(II) intel(0): Attempting memory allocation with untiled buffers and 
           small DRI memory manager reservation:
(II) intel(0): Allocating 5740 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(WW) intel(0): Not enough video memory.  Disabling DRI.
(II) intel(0): Allocating 5740 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(EE) intel(0): Couldn't allocate video memory

Fatal server error:
AddScreen/ScreenInit failed for driver 0



```

---

### Post by s26c.sayan on 2007-09-14
At first look it seems the problem occurs since only 7676KB of VidRAM is being allocated. Try increasing the Video RAM allocated in your xorg.conf file, and if possible, also in the BIOS.


However, since GARTInit fails to find device /dev/agpgart, this might also have something to do with the kernel. If my suggestion to increase VidRAM dint work, you might try the following :

1) Try booting onto the CLI, instead of auto loading X. 
2) Check if the modules agpgart and intel_agp are loaded or not. If not, manually load them
3) Check for /dev/agpgart : ls -l /dev/agpgart
 If the device is still not created, try upgrading to the latest kernel from the CLI.

-------
Edit : Also, try using the new 'intel' drivers instead of the old 'i810' ( sudo apt-get install xserver-xorg-video-intel)

---

### Post by linux23dragon on 2007-09-14
> **hellmet said:**
> ```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 13 22:41:05 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    /usr/share/fonts/X11/misc,
    /usr/X11R6/lib/X11/fonts/misc,
    /usr/share/fonts/X11/cyrillic,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/X11R6/lib/X11/fonts/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.3
    X.Org Video Driver: 1.1
    X.Org XInput driver : 0.7
    X.Org Server Extension : 0.3
    X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.1
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2a00 card 1028,01f1 rev 0c class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2a02 card 1028,01f1 rev 0c class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,2a03 card 1028,01f1 rev 0c class 03,80,00 hdr 80
(II) PCI: 00:1a:0: chip 8086,2834 card 1028,01f1 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card 1028,01f1 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card 1028,01f1 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,284b card 1028,01f1 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,283f card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,2841 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,2845 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2830 card 1028,01f1 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card 1028,01f1 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card 1028,01f1 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card 1028,01f1 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev f2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2815 card 1028,01f1 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,2850 card 1028,01f1 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,2828 card 1028,01f1 rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,283e card 1028,01f1 rev 02 class 0c,05,00 hdr 00
(II) PCI: 03:00:0: chip 14e4,170c card 1028,01f1 rev 02 class 02,00,00 hdr 00
(II) PCI: 03:01:0: chip 1180,0832 card 1028,01f1 rev 05 class 0c,00,10 hdr 80
(II) PCI: 03:01:1: chip 1180,0822 card 1028,01f1 rev 22 class 08,05,01 hdr 80
(II) PCI: 03:01:2: chip 1180,0843 card 1028,01f1 rev 12 class 08,80,00 hdr 80
(II) PCI: 03:01:3: chip 1180,0592 card 1028,01f1 rev 12 class 08,80,00 hdr 80
(II) PCI: 03:01:4: chip 1180,0852 card 1028,01f1 rev 12 class 08,80,00 hdr 80
(II) PCI: 0c:00:0: chip 8086,4222 card 8086,1020 rev 02 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,13), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 11: bridge is at (0:28:0), (0,11,11), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 12: bridge is at (0:28:1), (0,12,12), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 12 non-prefetchable memory range:
    [0] -1    0    0xfe800000 - 0xfe8fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 13: bridge is at (0:28:3), (0,13,14), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 13 I/O range:
    [0] -1    0    0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 13 non-prefetchable memory range:
    [0] -1    0    0xfe600000 - 0xfe7fffff (0x200000) MX[B]
(II) Bus 13 prefetchable memory range:
    [0] -1    0    0xf0000000 - 0xf01fffff (0x200000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
    [0] -1    0    0xfe500000 - 0xfe5fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation Mobile Integrated Graphics Controller rev 12, Mem @ 0xfea00000/20, 0xe0000000/28, I/O @ 0xefe8/3
(--) PCI: (0:2:1) Intel Corporation Mobile Integrated Graphics Controller rev 12, Mem @ 0xfeb00000/20
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
    [0] -1    0    0xfe8ff000 - 0xfe8fffff (0x1000) MX[B]
    [1] -1    0    0xfe5fd700 - 0xfe5fd7ff (0x100) MX[B]
    [2] -1    0    0xfe5fd600 - 0xfe5fd6ff (0x100) MX[B]
    [3] -1    0    0xfe5fd500 - 0xfe5fd5ff (0x100) MX[B]
    [4] -1    0    0xfe5fd400 - 0xfe5fd4ff (0x100) MX[B]
    [5] -1    0    0xfe5fd800 - 0xfe5fdfff (0x800) MX[B]
    [6] -1    0    0xfe5fe000 - 0xfe5fffff (0x2000) MX[B]
    [7] -1    0    0xfe9fbf00 - 0xfe9fbfff (0x100) MX[B]
    [8] -1    0    0xfed1c000 - 0xfed1c3ff (0x400) MX[B]
    [9] -1    0    0xfe9fc000 - 0xfe9fffff (0x4000) MX[B]
    [10] -1    0    0xfed1c400 - 0xfed1c7ff (0x400) MX[B]
    [11] -1    0    0xfeb00000 - 0xfebfffff (0x100000) MX[B](B)
    [12] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
    [13] -1    0    0xfea00000 - 0xfeafffff (0x100000) MX[B](B)
    [14] -1    0    0x000010c0 - 0x000010df (0x20) IX[B]
    [15] -1    0    0x0000eff0 - 0x0000efff (0x10) IX[B]
    [16] -1    0    0x00006ee0 - 0x00006eef (0x10) IX[B]
    [17] -1    0    0x00006ec8 - 0x00006ecb (0x4) IX[B]
    [18] -1    0    0x00006ec0 - 0x00006ec7 (0x8) IX[B]
    [19] -1    0    0x00006eb8 - 0x00006ebb (0x4) IX[B]
    [20] -1    0    0x00006eb0 - 0x00006eb7 (0x8) IX[B]
    [21] -1    0    0x00006fa0 - 0x00006faf (0x10) IX[B]
    [22] -1    0    0x00000374 - 0x00000374 (0x1) IX[B]
    [23] -1    0    0x00000170 - 0x00000177 (0x8) IX[B]
    [24] -1    0    0x000003f4 - 0x000003f4 (0x1) IX[B]
    [25] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [26] -1    0    0x00006f40 - 0x00006f5f (0x20) IX[B]
    [27] -1    0    0x00006f60 - 0x00006f7f (0x20) IX[B]
    [28] -1    0    0x00006f80 - 0x00006f9f (0x20) IX[B]
    [29] -1    0    0x00006f00 - 0x00006f1f (0x20) IX[B]
    [30] -1    0    0x00006f20 - 0x00006f3f (0x20) IX[B]
    [31] -1    0    0x0000efe8 - 0x0000efef (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xfe8ff000 - 0xfe8fffff (0x1000) MX[B]
    [1] -1    0    0xfe5fd700 - 0xfe5fd7ff (0x100) MX[B]
    [2] -1    0    0xfe5fd600 - 0xfe5fd6ff (0x100) MX[B]
    [3] -1    0    0xfe5fd500 - 0xfe5fd5ff (0x100) MX[B]
    [4] -1    0    0xfe5fd400 - 0xfe5fd4ff (0x100) MX[B]
    [5] -1    0    0xfe5fd800 - 0xfe5fdfff (0x800) MX[B]
    [6] -1    0    0xfe5fe000 - 0xfe5fffff (0x2000) MX[B]
    [7] -1    0    0xfe9fbf00 - 0xfe9fbfff (0x100) MX[B]
    [8] -1    0    0xfed1c000 - 0xfed1c3ff (0x400) MX[B]
    [9] -1    0    0xfe9fc000 - 0xfe9fffff (0x4000) MX[B]
    [10] -1    0    0xfed1c400 - 0xfed1c7ff (0x400) MX[B]
    [11] -1    0    0xfeb00000 - 0xfebfffff (0x100000) MX[B](B)
    [12] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
    [13] -1    0    0xfea00000 - 0xfeafffff (0x100000) MX[B](B)
    [14] -1    0    0x000010c0 - 0x000010df (0x20) IX[B]
    [15] -1    0    0x0000eff0 - 0x0000efff (0x10) IX[B]
    [16] -1    0    0x00006ee0 - 0x00006eef (0x10) IX[B]
    [17] -1    0    0x00006ec8 - 0x00006ecb (0x4) IX[B]
    [18] -1    0    0x00006ec0 - 0x00006ec7 (0x8) IX[B]
    [19] -1    0    0x00006eb8 - 0x00006ebb (0x4) IX[B]
    [20] -1    0    0x00006eb0 - 0x00006eb7 (0x8) IX[B]
    [21] -1    0    0x00006fa0 - 0x00006faf (0x10) IX[B]
    [22] -1    0    0x00000374 - 0x00000374 (0x1) IX[B]
    [23] -1    0    0x00000170 - 0x00000177 (0x8) IX[B]
    [24] -1    0    0x000003f4 - 0x000003f4 (0x1) IX[B]
    [25] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [26] -1    0    0x00006f40 - 0x00006f5f (0x20) IX[B]
    [27] -1    0    0x00006f60 - 0x00006f7f (0x20) IX[B]
    [28] -1    0    0x00006f80 - 0x00006f9f (0x20) IX[B]
    [29] -1    0    0x00006f00 - 0x00006f1f (0x20) IX[B]
    [30] -1    0    0x00006f20 - 0x00006f3f (0x20) IX[B]
    [31] -1    0    0x0000efe8 - 0x0000efef (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xfe8ff000 - 0xfe8fffff (0x1000) MX[B]
    [5] -1    0    0xfe5fd700 - 0xfe5fd7ff (0x100) MX[B]
    [6] -1    0    0xfe5fd600 - 0xfe5fd6ff (0x100) MX[B]
    [7] -1    0    0xfe5fd500 - 0xfe5fd5ff (0x100) MX[B]
    [8] -1    0    0xfe5fd400 - 0xfe5fd4ff (0x100) MX[B]
    [9] -1    0    0xfe5fd800 - 0xfe5fdfff (0x800) MX[B]
    [10] -1    0    0xfe5fe000 - 0xfe5fffff (0x2000) MX[B]
    [11] -1    0    0xfe9fbf00 - 0xfe9fbfff (0x100) MX[B]
    [12] -1    0    0xfed1c000 - 0xfed1c3ff (0x400) MX[B]
    [13] -1    0    0xfe9fc000 - 0xfe9fffff (0x4000) MX[B]
    [14] -1    0    0xfed1c400 - 0xfed1c7ff (0x400) MX[B]
    [15] -1    0    0xfeb00000 - 0xfebfffff (0x100000) MX[B](B)
    [16] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
    [17] -1    0    0xfea00000 - 0xfeafffff (0x100000) MX[B](B)
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [19] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [20] -1    0    0x000010c0 - 0x000010df (0x20) IX[B]
    [21] -1    0    0x0000eff0 - 0x0000efff (0x10) IX[B]
    [22] -1    0    0x00006ee0 - 0x00006eef (0x10) IX[B]
    [23] -1    0    0x00006ec8 - 0x00006ecb (0x4) IX[B]
    [24] -1    0    0x00006ec0 - 0x00006ec7 (0x8) IX[B]
    [25] -1    0    0x00006eb8 - 0x00006ebb (0x4) IX[B]
    [26] -1    0    0x00006eb0 - 0x00006eb7 (0x8) IX[B]
    [27] -1    0    0x00006fa0 - 0x00006faf (0x10) IX[B]
    [28] -1    0    0x00000374 - 0x00000374 (0x1) IX[B]
    [29] -1    0    0x00000170 - 0x00000177 (0x8) IX[B]
    [30] -1    0    0x000003f4 - 0x000003f4 (0x1) IX[B]
    [31] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [32] -1    0    0x00006f40 - 0x00006f5f (0x20) IX[B]
    [33] -1    0    0x00006f60 - 0x00006f7f (0x20) IX[B]
    [34] -1    0    0x00006f80 - 0x00006f9f (0x20) IX[B]
    [35] -1    0    0x00006f00 - 0x00006f1f (0x20) IX[B]
    [36] -1    0    0x00006f20 - 0x00006f3f (0x20) IX[B]
    [37] -1    0    0x0000efe8 - 0x0000efef (0x8) IX[B](B)
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 7.2.0, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.1.0
    ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "i810"
(II) Loading /usr/lib/xorg/modules/drivers//i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 14.94.94
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.1.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
    compiled for 4.3.99.902, module version = 1.0.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
    compiled for 4.2.0, module version = 1.0.0
    Module class: XFree86 XInput Driver
    ABI class: XFree86 XInput driver, version 0.3
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ, 965GM,
    G33, Q35, Q33
(II) Primary Device is: PCI 00:02:0
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset 965GM found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xfe8ff000 - 0xfe8fffff (0x1000) MX[B]
    [5] -1    0    0xfe5fd700 - 0xfe5fd7ff (0x100) MX[B]
    [6] -1    0    0xfe5fd600 - 0xfe5fd6ff (0x100) MX[B]
    [7] -1    0    0xfe5fd500 - 0xfe5fd5ff (0x100) MX[B]
    [8] -1    0    0xfe5fd400 - 0xfe5fd4ff (0x100) MX[B]
    [9] -1    0    0xfe5fd800 - 0xfe5fdfff (0x800) MX[B]
    [10] -1    0    0xfe5fe000 - 0xfe5fffff (0x2000) MX[B]
    [11] -1    0    0xfe9fbf00 - 0xfe9fbfff (0x100) MX[B]
    [12] -1    0    0xfed1c000 - 0xfed1c3ff (0x400) MX[B]
    [13] -1    0    0xfe9fc000 - 0xfe9fffff (0x4000) MX[B]
    [14] -1    0    0xfed1c400 - 0xfed1c7ff (0x400) MX[B]
    [15] -1    0    0xfeb00000 - 0xfebfffff (0x100000) MX[B](B)
    [16] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
    [17] -1    0    0xfea00000 - 0xfeafffff (0x100000) MX[B](B)
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [19] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [20] -1    0    0x000010c0 - 0x000010df (0x20) IX[B]
    [21] -1    0    0x0000eff0 - 0x0000efff (0x10) IX[B]
    [22] -1    0    0x00006ee0 - 0x00006eef (0x10) IX[B]
    [23] -1    0    0x00006ec8 - 0x00006ecb (0x4) IX[B]
    [24] -1    0    0x00006ec0 - 0x00006ec7 (0x8) IX[B]
    [25] -1    0    0x00006eb8 - 0x00006ebb (0x4) IX[B]
    [26] -1    0    0x00006eb0 - 0x00006eb7 (0x8) IX[B]
    [27] -1    0    0x00006fa0 - 0x00006faf (0x10) IX[B]
    [28] -1    0    0x00000374 - 0x00000374 (0x1) IX[B]
    [29] -1    0    0x00000170 - 0x00000177 (0x8) IX[B]
    [30] -1    0    0x000003f4 - 0x000003f4 (0x1) IX[B]
    [31] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [32] -1    0    0x00006f40 - 0x00006f5f (0x20) IX[B]
    [33] -1    0    0x00006f60 - 0x00006f7f (0x20) IX[B]
    [34] -1    0    0x00006f80 - 0x00006f9f (0x20) IX[B]
    [35] -1    0    0x00006f00 - 0x00006f1f (0x20) IX[B]
    [36] -1    0    0x00006f20 - 0x00006f3f (0x20) IX[B]
    [37] -1    0    0x0000efe8 - 0x0000efef (0x8) IX[B](B)
(II) resource ranges after probing:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xfe8ff000 - 0xfe8fffff (0x1000) MX[B]
    [5] -1    0    0xfe5fd700 - 0xfe5fd7ff (0x100) MX[B]
    [6] -1    0    0xfe5fd600 - 0xfe5fd6ff (0x100) MX[B]
    [7] -1    0    0xfe5fd500 - 0xfe5fd5ff (0x100) MX[B]
    [8] -1    0    0xfe5fd400 - 0xfe5fd4ff (0x100) MX[B]
    [9] -1    0    0xfe5fd800 - 0xfe5fdfff (0x800) MX[B]
    [10] -1    0    0xfe5fe000 - 0xfe5fffff (0x2000) MX[B]
    [11] -1    0    0xfe9fbf00 - 0xfe9fbfff (0x100) MX[B]
    [12] -1    0    0xfed1c000 - 0xfed1c3ff (0x400) MX[B]
    [13] -1    0    0xfe9fc000 - 0xfe9fffff (0x4000) MX[B]
    [14] -1    0    0xfed1c400 - 0xfed1c7ff (0x400) MX[B]
    [15] -1    0    0xfeb00000 - 0xfebfffff (0x100000) MX[B](B)
    [16] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
    [17] -1    0    0xfea00000 - 0xfeafffff (0x100000) MX[B](B)
    [18] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [19] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [20] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [21] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [22] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [23] -1    0    0x000010c0 - 0x000010df (0x20) IX[B]
    [24] -1    0    0x0000eff0 - 0x0000efff (0x10) IX[B]
    [25] -1    0    0x00006ee0 - 0x00006eef (0x10) IX[B]
    [26] -1    0    0x00006ec8 - 0x00006ecb (0x4) IX[B]
    [27] -1    0    0x00006ec0 - 0x00006ec7 (0x8) IX[B]
    [28] -1    0    0x00006eb8 - 0x00006ebb (0x4) IX[B]
    [29] -1    0    0x00006eb0 - 0x00006eb7 (0x8) IX[B]
    [30] -1    0    0x00006fa0 - 0x00006faf (0x10) IX[B]
    [31] -1    0    0x00000374 - 0x00000374 (0x1) IX[B]
    [32] -1    0    0x00000170 - 0x00000177 (0x8) IX[B]
    [33] -1    0    0x000003f4 - 0x000003f4 (0x1) IX[B]
    [34] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [35] -1    0    0x00006f40 - 0x00006f5f (0x20) IX[B]
    [36] -1    0    0x00006f60 - 0x00006f7f (0x20) IX[B]
    [37] -1    0    0x00006f80 - 0x00006f9f (0x20) IX[B]
    [38] -1    0    0x00006f00 - 0x00006f1f (0x20) IX[B]
    [39] -1    0    0x00006f20 - 0x00006f3f (0x20) IX[B]
    [40] -1    0    0x0000efe8 - 0x0000efef (0x8) IX[B](B)
    [41] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [42] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 0.1.0
    ABI class: X.Org Video Driver, version 1.1
(**) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
(--) intel(0): Chipset: "965GM"
(--) intel(0): Linear framebuffer at 0xE0000000
(--) intel(0): IO registers at addr 0xFEA00000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using XAA for acceleration
(--) intel(0): Will try to allocate texture pool for old Mesa 3D driver.
(II) intel(0): Will try to reserve 32768 kiB of AGP aperture space
    for the DRM memory manager.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.2.0
    ABI class: X.Org Video Driver, version 1.1
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "SEC", prod id 12631
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(II) Loading sub module "vm86"
(II) LoadModule: "vm86"
(II) Loading /usr/lib/xorg/modules//libvm86.so
(II) Module vm86: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 1.1
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 7616 kB
(II) intel(0): VESA VBE OEM: Intel(r)GM965/PM965/GL960 Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r)GM965/PM965/GL960 Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): EDID vendor "SEC", prod id 12631
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 512 kB GTT.
(II) intel(0): detected 7676 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(++) intel(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 1.2.0
    ABI class: X.Org Video Driver, version 1.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
    compiled for 7.2.0, module version = 0.1.0
    ABI class: X.Org Video Driver, version 1.1
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd0000009
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] 0    0    0xe0000000 - 0xefffffff (0x10000000) MS[B]
    [1] 0    0    0xfea00000 - 0xfeafffff (0x100000) MS[B]
    [2] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [3] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [4] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [5] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [6] -1    0    0xfe8ff000 - 0xfe8fffff (0x1000) MX[B]
    [7] -1    0    0xfe5fd700 - 0xfe5fd7ff (0x100) MX[B]
    [8] -1    0    0xfe5fd600 - 0xfe5fd6ff (0x100) MX[B]
    [9] -1    0    0xfe5fd500 - 0xfe5fd5ff (0x100) MX[B]
    [10] -1    0    0xfe5fd400 - 0xfe5fd4ff (0x100) MX[B]
    [11] -1    0    0xfe5fd800 - 0xfe5fdfff (0x800) MX[B]
    [12] -1    0    0xfe5fe000 - 0xfe5fffff (0x2000) MX[B]
    [13] -1    0    0xfe9fbf00 - 0xfe9fbfff (0x100) MX[B]
    [14] -1    0    0xfed1c000 - 0xfed1c3ff (0x400) MX[B]
    [15] -1    0    0xfe9fc000 - 0xfe9fffff (0x4000) MX[B]
    [16] -1    0    0xfed1c400 - 0xfed1c7ff (0x400) MX[B]
    [17] -1    0    0xfeb00000 - 0xfebfffff (0x100000) MX[B](B)
    [18] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
    [19] -1    0    0xfea00000 - 0xfeafffff (0x100000) MX[B](B)
    [20] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
    [21] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
    [22] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
    [23] 0    0    0x0000efe8 - 0x0000efef (0x8) IS[B]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [25] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [26] -1    0    0x000010c0 - 0x000010df (0x20) IX[B]
    [27] -1    0    0x0000eff0 - 0x0000efff (0x10) IX[B]
    [28] -1    0    0x00006ee0 - 0x00006eef (0x10) IX[B]
    [29] -1    0    0x00006ec8 - 0x00006ecb (0x4) IX[B]
    [30] -1    0    0x00006ec0 - 0x00006ec7 (0x8) IX[B]
    [31] -1    0    0x00006eb8 - 0x00006ebb (0x4) IX[B]
    [32] -1    0    0x00006eb0 - 0x00006eb7 (0x8) IX[B]
    [33] -1    0    0x00006fa0 - 0x00006faf (0x10) IX[B]
    [34] -1    0    0x00000374 - 0x00000374 (0x1) IX[B]
    [35] -1    0    0x00000170 - 0x00000177 (0x8) IX[B]
    [36] -1    0    0x000003f4 - 0x000003f4 (0x1) IX[B]
    [37] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[B]
    [38] -1    0    0x00006f40 - 0x00006f5f (0x20) IX[B]
    [39] -1    0    0x00006f60 - 0x00006f7f (0x20) IX[B]
    [40] -1    0    0x00006f80 - 0x00006f9f (0x20) IX[B]
    [41] -1    0    0x00006f00 - 0x00006f1f (0x20) IX[B]
    [42] -1    0    0x00006f20 - 0x00006f3f (0x20) IX[B]
    [43] -1    0    0x0000efe8 - 0x0000efef (0x8) IX[B](B)
    [44] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
    [45] 0    0    0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(EE) GARTInit: Unable to open /dev/agpgart (No such file or directory)
(WW) intel(0): /dev/agpgart is either not available, or no memory is available
for allocation.  Using pre-allocated memory only.
(**) intel(0): VideoRam: 7676 KB
(II) intel(0): Attempting memory allocation with tiled buffers and 
           large DRI memory manager reservation:
(II) intel(0): Allocating 5680 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(II) intel(0): Attempting memory allocation with tiled buffers and 
           small DRI memory manager reservation:
(II) intel(0): Allocating 5680 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(II) intel(0): Attempting memory allocation with untiled buffers and 
           large DRI memory manager reservation:
(II) intel(0): Allocating 5740 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(II) intel(0): Attempting memory allocation with untiled buffers and 
           small DRI memory manager reservation:
(II) intel(0): Allocating 5740 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(WW) intel(0): Not enough video memory.  Disabling DRI.
(II) intel(0): Allocating 5740 scanlines for pixmap cache
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(EE) intel(0): Couldn't allocate video memory

Fatal server error:
AddScreen/ScreenInit failed for driver 0



```

You are using linux-2.6.20-15. Please upgrade the kernel to 2.6.20-16.  Everything looks fine otherwise.

---

### Post by hellmet on 2007-09-14
you guys sure that'll work? I'm gonna try that right now.

---

### Post by hellmet on 2007-09-14
YAYYYYY!! Thanks linux23 and sayan. That tip paid off!!! I'm typing this from Ubuntu finally!!!

---

### Post by mac-duff on 2007-09-14
Hi,
I guess I played a bit to much with it and now I havent sound anymore. When I am trying to do the setup which is one the first site I am receiving following error message:
root@m-d-l:/home/stephan# sudo modprobe snd-hda-intel model=dell-laptop ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd-pcm.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/oss/snd-mixer-oss.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd-pcm.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/oss/snd-pcm-oss.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/oss/snd-mixer-oss.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/seq/snd-seq-device.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/seq/snd-seq.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/seq/snd-seq-midi-event.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/seq/oss/snd-seq-oss.ko': No such file or directory

how can I install the missing driver?
Btw.: Do u have problems with hibernate and Stand by?

cu

---

### Post by linux23dragon on 2007-09-14
> **mac-duff said:**
> Hi,
I guess I played a bit to much with it and now I havent sound anymore. When I am trying to do the setup which is one the first site I am receiving following error message:
root@m-d-l:/home/stephan# sudo modprobe snd-hda-intel model=dell-laptop ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd-pcm.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/pci/hda/snd-hda-intel.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/oss/snd-mixer-oss.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd-pcm.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/oss/snd-pcm-oss.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/oss/snd-mixer-oss.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/seq/snd-seq-device.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/seq/snd-seq.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/seq/snd-seq-midi-event.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.20-16-generic/kernel/sound/acore/seq/oss/snd-seq-oss.ko': No such file or directory

how can I install the missing driver?
Btw.: Do u have problems with hibernate and Stand by?

cu

I've not tested this, but it should work AFAIK.

The easy way is to use the Synaptic package Manager, to reinstall linux-image-2.6.20-16-generic and alsa-base.  Then reinstall the web cam driver and video driver (if you have Nvidia or ATI), using Envy.  After you have done that,  reboot.

---

### Post by mac-duff on 2007-09-15
Hi,
thanks for the reply. I had really to reinstall the driver by my own. Now the sound has come back but in fact my mic in doenst work, and also after hibernating the sound disappears.

Is their another suggestion?

cu

---

### Post by CAD-MAN on 2007-09-15
Hi

I'm using the alternate CD now, to set up Ubuntu to dual boot alongside Vista on my Inspiron 1520. At present it appears to be resizing the partitions, but has been stuck on 100% for about 20 minutes. Previously it was lagging on 0%, but then jumped to 100% almost instantaneously.

I'm starting to get a bit worried because when I reduced my Vista partition (in Vista), it took less than a minute to free up the space. Is there any reason that this should be taking 20 minutes +

Any ideas?

---

### Post by CAD-MAN on 2007-09-15
Its been at least 40 minutes now, and its still stuck on 100%. I'm wondering whether I should just kill the power to my laptop and try again? Or would that cause irreversible damage...?

Please help!!


EDIT: Actually, I've decided that doing that probably would cause irreversible damage, but it is very tempting...

---

### Post by hellmet on 2007-09-15
It seems that even when I plug in a headphone or external speakers into the sound out jack, sound still plays in the laptop speaker. Is there a workaround for this?

---

### Post by CAD-MAN on 2007-09-15
Ok, after my previous mishap, I got tired of waiting, and killed the power. I turned the computer back on, and let it boot to my existing Vista partition. Vista was fine, all was well.

Then I tried to install once more. All went well (it didnt get stuck this time, because I chose manual partitioning).

Whilst installing, it got to about 25% and I got the following three errors consecutively:

```
[!!] Install the base system
Base system installation error

The debootstrap program exited with an error (return volume 1).

Check /var/log/syslog or see virtual console 4 for the details.
```

```
Install the base system
Failed to install the base system
The base system installation into /target/failed.

Check var/log/syslog or see virtual console 4 for the details.
```

```
Install the base system
Installation step failed

An installation step failed. You can try to run the failing item again from the menu, or skip it and choose something else. The failing step is: Install the base system
```


Ok, so I figured that there would be no use in 'skipping the failing step', as the failing step is the part that installs the base Ubuntu system. So, I exited installation.

I have now restarted my computer without the Alternate CD in the drive (hoping to stick with Vista until this gets sorted), but now the bios says:


```
No bootable device--strike F1 to retry boot, F2 for setup utility
Press F5 to run onboard diagnostics
```



So now I cant boot ANYTHING! Am I screwed? Is there a fix for this? Please help!!

---

### Post by CAD-MAN on 2007-09-15
_Update:_ I have found that I am able to boot Vista using the Gparted live CD. When I boot from the CD, a greay screen comes up with a bunch of options. I scroll down, and tell it to boot Partition 3 on the first hard drive. This then boots Vista properly.

However, if I shut the computer down, and try to boot Vista without using Gparted, I get the same error as before. Yet I know that, otherwise,  Vista is completely unaffected by the failed attempt at installing Ubuntu.

So, basically, can anybody (linux23dragon :p) give me a hand in getting this system to install Ubuntu, and then to dual boot Vista and Ubuntu properly please?

Thanks

---

### Post by odin1965 on 2007-09-15
> **CAD-MAN said:**
> _Update:_ I
So, basically, can anybody (linux23dragon :p) give me a hand in getting this system to install Ubuntu, and then to dual boot Vista and Ubuntu properly please?


Using the alternate CD, there should be no issues in getting 7.04 installed. My 1520 installed fine with help from this thread. If you have system rescue CD, try running some of the diagnostic programs to see if your 1520 has a problem. Maybe bad RAM or bad sectors on your disk. System Rescue CD may be able to fix it.

---

### Post by Mamsaac on 2007-09-16
> **Mamsaac said:**
> Thanks. I don't understand perfectly how extended partitions work, but that's something I will have to read myself (don't worry on giving me any links, it would be a shame if I didn't look for that myself).

As you already know my partitions... would this work without messing anything up?

sda1.- (SOME DELL UTILITIES) FAT16, 47mb
sda2.-(VISTA) NTFS 33gb
------- / Ext3 12gb
sda3 (EXTENDED){
------- /home Ext3 12gb
------- swap 4gb
------- FAT32 86gb
-------sda5.-(MEDIA DIRECT) fat32 2gb
}

What I would try to do, is only:
INSIDE THE EXTENDED PARTITION{
1.-Delete the existant FAT 32 partition
2.-Create an Ext3 Partition 12gb size
3.-create a swap partition of 4gb
4.-Create a FAT32 partition of 86gb
}
5.-Resize de NTFS partition from 45gb to 33gb.
6.-Create an Ext3 partition
7.-Install Edgy and use the first Ext3 partition as root, the Ext3 partition inside the extended as /home and the swap...

Would it work and not mess up the MBR?

Does anyone know what MediaDirect does to the MBR? I think that's where I get lost and freak out a little bit. I'm afraid that after installing Ubuntu Edgy, access to Windows Vista will mess up.

And thanks for all the help, I really feel lost from time to time :)

Please, answer that question (is on page 35...), because I really need to feel sure it will work before trying. Thanks in advance for the answer.

---

### Post by CAD-MAN on 2007-09-16
> **odin1965 said:**
> Using the alternate CD, there should be no issues in getting 7.04 installed. My 1520 installed fine with help from this thread. If you have system rescue CD, try running some of the diagnostic programs to see if your 1520 has a problem. Maybe bad RAM or bad sectors on your disk. System Rescue CD may be able to fix it.

I'm guessing you mean this: [http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")? I'll download it now. Which diagnostic programs should I run? (Remember, Im a complete newbie, sorry :oops: )

One of the features is: "MemTest+ test the physical memory, and tells if it is damaged or not", I know this will tell me if its damaged, but will it fix it? If I can't fix it, what do I do?

Thanks again

---

### Post by Perseid on 2007-09-16
> **CAD-MAN said:**
> I'm guessing you mean this: [http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")? I'll download it now. Which diagnostic programs should I run? (Remember, Im a complete newbie, sorry :oops: )

One of the features is: "MemTest+ test the physical memory, and tells if it is damaged or not", I know this will tell me if its damaged, but will it fix it? If I can't fix it, what do I do?

Thanks again

Hi,
I am proud owner (;)) of a vostro 1500 (which is nearly identical to the inspiron 1520) and have been installing my system for the past week.

If you still have the diagnostics partition (which is the first on your harddrive) then you can use that instead. You can access it via the same menu you use to boot CDs. This will run several test and should includea MemTest, too. As far as I know, you can't repair broken RAM.

You did have a CD with GParted right? Check whether your Windows partition has the bootflag. If it doesn't, flag it and reboot. On my system changing the boot flag to the third partition (which has a small Debian installtion) worked without any problems. I use that one to chainload into the other bootloader (1*Windows, 2*Ubuntu, 1*Xubuntu).

[COLOR="Green"](Edit to add reply without double post: )[/COLOR]

> **Mamsaac said:**
> Right now, the partitions are like this:

sda1.- (SOME DELL UTILITIES) FAT16, 47mb
sda2.-(VISTA) NTFS 45gb
sda3 (EXTENDED){
-------sda4.-FAT32 102gb
-------sda5.-(MEDIA DIRECT) fat32 2gb
}


> **Mamsaac said:**
> As you already know my partitions... would this work without messing anything up?

sda1.- (SOME DELL UTILITIES) FAT16, 47mb
sda2.-(VISTA) NTFS 33gb
------- / Ext3 12gb
sda3 (EXTENDED){
------- /home Ext3 12gb
------- swap 4gb
------- FAT32 86gb
-------sda5.-(MEDIA DIRECT) fat32 2gb
}

What I would try to do, is only:
INSIDE THE EXTENDED PARTITION{
1.-Delete the existant FAT 32 partition
2.-Create an Ext3 Partition 12gb size
3.-create a swap partition of 4gb
4.-Create a FAT32 partition of 86gb
}
5.-Resize de NTFS partition from 45gb to 33gb.
6.-Create an Ext3 partition
7.-Install Edgy and use the first Ext3 partition as root, the Ext3 partition inside the extended as /home and the swap...

Would it work and not mess up the MBR?

Does anyone know what MediaDirect does to the MBR? I think that's where I get lost and freak out a little bit. I'm afraid that after installing Ubuntu Edgy, access to Windows Vista will mess up.

And thanks for all the help, I really feel lost from time to time :)

I *believe* your planned installation neither destroys Vista nor MediaDirect*. But the documentation on MediaDirect is very thin. I read that the standard installation boots the active/bootflag partition with the normal button and the last partition (logical) on the harddrive with the MediaDirect button. Vista and Grub installation will destroy MediaDirect, but booting the active partition will still work. Therefore: Never install grub in the MBR. You'll want to put it in /dev/sda3 , which will be you linux partition after you created the new Ext3 partition. In the partition dialog you can flag it with the boot flag, so that this one will be booted instead of the windows partition. Btw, the first logical partition is always /dev/sda5 .
If you have about 10 GB free space on an external harddrive, you can backup your Laptop drive with the help of a Knoppix or some other distributions on bootable CD:
```
# dd if=/dev/sda | gzip > /path/to/external/hard/drive/system_drive_backup.img.gz 
``` [Further information: http://wiki.linuxquestions.org/wiki/Dd]("http://wiki.linuxquestions.org/wiki/Dd")
This took me about 5 hours.

> **Altimar said:**
> I am personally looking into installing DSL or Puppy to quickly boot and watch DVDs or view photos, etc. Maybe even install it to an SD card (quicker than HDD?).

Only the time till you get the first data from the SD-Card is shorter than your harddrive's. The actual transfer rate is slower.

Does someone know how to install the MediaDirect MBR? I believe Vista destroyed it, when I reinstalled it on a smaller partition.

(*Always talking about MediaDirect 3. Just in case someone comes here via google.)

---

### Post by CAD-MAN on 2007-09-16
Thanks for you help Perseid. I'll try that if the Windows repair DVD fails :)

---

### Post by CAD-MAN on 2007-09-16
Ok, now when I boot Vista, everything seems to go fine. I get to the logon screen, and enter my password. Then, it loads my account (but takes far longer than expected). Once loaded, I get this:


```
Setting up personalized settings for:

C:\Windows\system32\Rundll32.exe
C:\Windows\system32\mscories.dll, Install
```

```
Error loading C:\Windows\system32\mscories.dll

The specified module could not be found.
```


Then it tells me that this is only a temporary desktop, and any changes that I make will be lost. Setting (like Firefox being my default browser) are gone, but Firefox is still there and working, which is strange, because I downloaded it, so Vista recognises my system set-up, but can't find my custom settings. The icons for programs that I downloaded are gone, also.


I then get the same pop-up error box as the second one, but with the following files not being found:

```
Error loading C:\Windows\system32\NvCpl.dll

The specified module could not be found.
```

```
Error loading C:\Windows\system32\nvHotkey.dll

The specified module could not be found.
```

```
Error loading C:\Windows\system32\NvMCTray.dl

The specified module could not be found.
```

```
Error loading C:\Windows\system32\nvsvc.dll

The specified module could not be found.
```



I am wondering whether 'nv' might be Nvidia? But there seems to be no problem with graphics...

Any ideas? I really want to get this fixed, so that I can try installing Ubuntu again soon.

Thanks


**_EDIT:_ I've fixed Vista by reinstalling over the partition that Vista was previously residing in. Lost all my settings and data, but as this is a brand new laptop, there were no real worries. Just meant I had to reinstall Firefox, McAfee, and some CAD programs. Wwill definitely try and install Ubuntu again soon, though im not in any real rush after my experiences today/yesterday! May wait for Gutsy, may have another go next weekend...**

---

### Post by Mamsaac on 2007-09-16
> **Perseid said:**
> Hi,
I am proud owner (;)) of a vostro 1500 (which is nearly identical to the inspiron 1520) and have been installing my system for the past week.

If you still have the diagnostics partition (which is the first on your harddrive) then you can use that instead. You can access it via the same menu you use to boot CDs. This will run several test and should includea MemTest, too. As far as I know, you can't repair broken RAM.

You did have a CD with GParted right? Check whether your Windows partition has the bootflag. If it doesn't, flag it and reboot. On my system changing the boot flag to the third partition (which has a small Debian installtion) worked without any problems. I use that one to chainload into the other bootloader (1*Windows, 2*Ubuntu, 1*Xubuntu).

[COLOR="Green"](Edit to add reply without double post: )[/COLOR]





I *believe* your planned installation neither destroys Vista nor MediaDirect*. But the documentation on MediaDirect is very thin. I read that the standard installation boots the active/bootflag partition with the normal button and the last partition (logical) on the harddrive with the MediaDirect button. Vista and Grub installation will destroy MediaDirect, but booting the active partition will still work. Therefore: Never install grub in the MBR. You'll want to put it in /dev/sda3 , which will be you linux partition after you created the new Ext3 partition. In the partition dialog you can flag it with the boot flag, so that this one will be booted instead of the windows partition. Btw, the first logical partition is always /dev/sda5 .
If you have about 10 GB free space on an external harddrive, you can backup your Laptop drive with the help of a Knoppix or some other distributions on bootable CD:
```
# dd if=/dev/sda | gzip > /path/to/external/hard/drive/system_drive_backup.img.gz 
``` [Further information: http://wiki.linuxquestions.org/wiki/Dd]("http://wiki.linuxquestions.org/wiki/Dd")
This took me about 5 hours.


Only the time till you get the first data from the SD-Card is shorter than your harddrive's. The actual transfer rate is slower.

Does someone know how to install the MediaDirect MBR? I believe Vista destroyed it, when I reinstalled it on a smaller partition.

(*Always talking about MediaDirect 3. Just in case someone comes here via google.)


Thanks a lot for that. I'm still not sure of how MediaDirect works (I already screwed up MBR once... I don't wanna do it again) but I believe I'm capable of installing Ubuntu next weekend, when I don't have so many homeworks as I do right now.

---

### Post by yther on 2007-09-18
Hi, would this be an appropriate place to ask for guidance on getting a few things working under Gutsy?  I'm running the Kubuntu flavor, and I've spent several hours writing detailed posts on their forum, which a handful of people have viewed but have gone unanswered.  Before I spend a similar amount of time here, I just want to check.

Non-working stuff:  SigmaTel 9205 sound card (alsa modules load but stays silent); cannot join secure WLANs with Intel 4965 wifi card.

---

### Post by omne on 2007-09-20
> **yther said:**
> Non-working stuff:  SigmaTel 9205 sound card (alsa modules load but stays silent); cannot join secure WLANs with Intel 4965 wifi card.

Hello, I install gutsy on the fresh new inspiron 1520 of my girlfriend.
Here the wifi seems to work perfectly, no strange sound with the sata disk and the webcam works in cheese (don’t have test anything else).
The only problems are :
- the luminosity that have strange behaviors
- the sound… 
First there was no sound at all. The I compile the jbizzler command lines (see post #305) and I can get sound. But when I plug headphone… you known the end.

Maybe we could open a new thread, just for Gusty.

O.

---

### Post by yther on 2007-09-20
> **omne said:**
> Here the wifi seems to work perfectly, no strange sound with the sata disk and the webcam works in cheese (don’t have test anything else).
The only problems are :
- the luminosity that have strange behaviors
- the sound… 
First there was no sound at all. The I compile the jbizzler command lines (see post #305) and I can get sound. But when I plug headphone… you known the end.

Maybe we could open a new thread, just for Gusty.

Perhaps we should, or maybe there already is one... after all, this thread *is* called "Dell Inspiron 1520 with Ubuntu-7.[COLOR="Orange"]04[/COLOR]."  I understand the risks of running a "testing" distribution, but many people seem to feel that anyone running Gutsy and having a problem is on their own.  Anyone using Kubuntu, feel free to read my longer [cry for help]("http://kubuntuforums.net/forums/index.php?topic=3086636.msg88736#msg88736").  :)

I went ahead and bought the 1520 instead of some other models because, after much searching, I had seen many people saying that the sound, wireless, and video cards worked.  It's a bit frustrating that they don't work *for me, right now*, but if they work by the time GG goes stable I'll still be happy.  [SIZE="2"]If I can't stand not hearing bells and music on this thing, I can always boot into [that other OS](http://en.wikipedia.org/wiki/Windows_Vista).[/SIZE]  :-P

This weekend I should have more time for amusing things, such as filing actual bug reports (instead of just whining in the forum) and compiling a few kernels.  As a Gentoo user, I've certainly done *that* before.  ;)

Since you said your wifi card worked without doing anything special, which card do you have?  (You could paste the output of [FONT="Lucida Console", monospace]**lshw -short -class network**[/FONT].)  Mine doesn't have a camera; I went for more disk space instead of a gadget I'd never use.

Anyway, thanks for your reply, and let's have fun seeing what breaks over the next few weeks!

---

### Post by omne on 2007-09-21
> **yther said:**
> Perhaps we should, or maybe there already is one... after all, this thread *is* called "Dell Inspiron 1520 with Ubuntu-7.[COLOR="Orange"]04[/COLOR]."  I understand the risks of running a "testing" distribution, but many people seem to feel that anyone running Gutsy and having a problem is on their own.  Anyone using Kubuntu, feel free to read my longer [cry for help]("http://kubuntuforums.net/forums/index.php?topic=3086636.msg88736#msg88736").  :)
I heard the same strange "click" from the hard drive. It seems to be here with and without the AC. Maybee something to deal with « laptop mode » ? Do you think it can be bad for the drive ?

> **yther said:**
> 
 I can always boot into [that other OS](http://en.wikipedia.org/wiki/Windows_Vista).[/SIZE]  
My girlfriend don’t want to learn vista :o (and she’s not a linux addict)

> **yther said:**
> 
Since you said your wifi card worked without doing anything special, which card do you have?  (You could paste the output of [FONT="Lucida Console", monospace]**lshw -short -class network**[/FONT].)  

/0/100/1c.1/0      eth1        network     PRO/Wireless 3945ABG Network Connection
/0/100/1e/0        eth0        network     BCM4401-B0 100Base-TX

And for the sound :

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

Have a good day.

Omnë

---

### Post by jeff_p on 2007-09-22
I am having trouble with my Broadcom wireless (BCM4310).  I just re-installed using the X86-64 version of Feisty, and I am getting very, very slow wireless access.  It is to the point that pings are failing intermittently, and not because my connection is dropping.

Has anyone had any luck getting BCM4310 to work using X86-64?  I have tried ndiswrapper, bcm43xx-cutter, and some native driver that I compiled.  Has anyone else noticed this problem?

---

### Post by dumbmatter on 2007-09-22
> **omne said:**
> I heard the same strange "click" from the hard drive. It seems to be here with and without the AC. Maybee something to deal with « laptop mode » ? Do you think it can be bad for the drive ?
Yes, it might be very bad for the drive.  I'm no expert, but when I was investigating the same problem, some people were saying that it might result in the drive wearing out in about a year.

I fixed it with this command:

sudo hdparm -B 254 /dev/sda

If that fixes it, you can edit /etc/hdparm.conf to have it automatically set the -B parameter.  Or just put that command in your /etc/rc.local file.

To check on the problem, you can run this command:
sudo smartctl -d ata -a /dev/sda
and find the RAW_VALUE for Load_Cycle_count.  I remember finding somewhere that it was supposed to be able to handle... something in the hundreds of thousands, or maybe millions.  I forget.

---

### Post by omne on 2007-09-23
> **dumbmatter said:**
> Y
I fixed it with this command:

sudo hdparm -B 254 /dev/sda

If that fixes it, you can edit /etc/hdparm.conf to have it automatically set the -B parameter.  

It do the tric. Thank’s.
I found that it can be done throw laptop-mode too.

New kernel today… no new from the sound ! D

---

### Post by mac-duff on 2007-09-23
Hi,
I am looking for kind of Power Management tool to minimize my CPU Speed like the "Power Management" tools from IBM to save a bit energy. Is something like that available because I guess my NB takes to much power

cu

---

### Post by omne on 2007-09-23
> **mac-duff said:**
> Hi,
I am looking for kind of Power Management tool to minimize my CPU Speed like the "Power Management" tools from IBM to save a bit energy. Is something like that available because I guess my NB takes to much power
cu
Did you tried the gnome-applet « cpufreq-applet » ?
And have a look at /etc/laptop-mode/laptop-mode.conf

Omnë

---

### Post by chadwick359 on 2007-09-24
Hey, I've been arguing with a 1521 all night and I'm having a few issues still. No matter what I do I can't force the backlight any brighter than 50% while on battery, even though it is set in the BIOS to be 100% on batt, and I can't get my sound system to work for the life of me. I'm using Gutsy, (I know this is a Feisty guide) and I'm wondering if anybody has any input. Thanks in advance.

---

### Post by Mamsaac on 2007-09-24
Ahhhh, I thought I had it all ready, and I started the installation... there was an error when I tried to install GRUB :(

I'm in a Live-CD of Edgy, here is a screen of my partitions... I couldn't copy the error because the screen is in the lowest resolution. Is there a way to fix this? I don't think it will affect windows at all, so I can still use this computer tomorrow at school, but I would like to know what I did wrong :S

when asked for the place to install GRUB, I put sd0,3, which, I believe, is the root. Here's the picture... you tell me what I did wrong please. And if there's a way to fix it, I will be pleased to do it. 

Thanks a lot for the help, I will really need it

EDIT: 

I reinstalled it as if sda was hda. Done with this :)

---

### Post by mac-duff on 2007-09-24
Hi omne,
havent herad about that tool but the crazy thing is, that by 100% charged the NB is telling me I can use it for 4hours and after 15min is down by 75% and just 2hours avialable

---

### Post by Mamsaac on 2007-09-24
I already fixed the last problem. :D

So, now my only problem left to solve... well, there are two problems:

1- The wireless works out of the box in the Live-CD, but now that it is installed it's not working :S Any ideas on this? My wireless is Intel.PRO/Wireless 3945ABG Network, and the chipset is BCM4401-B0 100Base-TX---- EDIT: ALREADY FIX THIS POINT.

2- I'm not using a xorg.conf file. I moved it to another directory (because the xorg.conf was configured for a 640x480 resolution, which sucks ;)). Here's my log (attachment). It's also Intel. Could anyone help me to create a xorg.conf file? I'm not good in doing that and without Internet it will give me problems.


EDIT 3: a third problem: I can't get sound to work. ALSA is not working and I tried what this thread says and:
> mamsaac@mamsaac-laptop:~$ sudo update-modules &&
> sudo modprobe snd-hda-intel model=dell-laptop ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.17-12-generic/kernel/sound/core/seq/snd-seq-device.ko): Operation not permitted
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.17-12-generic/kernel/sound/core/seq/snd-seq-device.ko): Operation not permitted
FATAL: Error inserting snd_seq (/lib/modules/2.6.17-12-generic/kernel/sound/core/seq/snd-seq.ko): Operation not permitted
WARNING: Error running install command for snd_seq
WARNING: Error inserting snd_seq_midi_event (/lib/modules/2.6.17-12-generic/kernel/sound/core/seq/snd-seq-midi-event.ko): Operation not permitted
FATAL: Error inserting snd_seq_oss (/lib/modules/2.6.17-12-generic/kernel/sound/core/seq/oss/snd-seq-oss.ko): Operation not permitted


The part that is giving me the error is the last one (modprobe snd-seq-oss). Any ideas why it is causing the problem? should I update kernel or what?

EDIT AGAIN: I haven't solved the problem with the sound... When I execute the commands (sudo update-modules && sudo modprobe snd-hda-intel model=dell-laptop ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss) it no longer sends me an error, but sound isn't working yet.




LAST EDIT: Screw all this, I don't want ubuntu anymore <_< just kidding, I already fixed everything AND upgraded to feisty :)  everything is working so perfectly and I feel happy. I had to work a little to get it to work because I did move some things I shouldn't have moved and that made things harder. Whatever, thanks anyway.

---

### Post by Mamsaac on 2007-09-27
Oh damn. I was so happy because I already had "everything ready". Now I notice the fact the webcam is not working. I tried what this thread says but it isn't working.

---

### Post by omne on 2007-09-27
> **Mamsaac said:**
> Oh damn. I was so happy because I already had "everything ready". Now I notice the fact the webcam is not working. I tried what this thread says but it isn't working.
I don’t know what’s in this thread but I solve a webcam problem yesterday : the user was not in the video group (number 44). I just add it ! The group was not in the UI for the groups, so I add it, tell about my two user, reboot. It was OK… but the video group had desepeard from the « group » UI… but it was in /etc/group. I’m going to search for a bug report in launchpad

Olivier.

---

### Post by Mamsaac on 2007-09-27
> **omne said:**
> I don’t know what’s in this thread but I solve a webcam problem yesterday : the user was not in the video group (number 44). I just add it ! The group was not in the UI for the groups, so I add it, tell about my two user, reboot. It was OK… but the video group had desepeard from the « group » UI… but it was in /etc/group. I’m going to search for a bug report in launchpad

Olivier.

Ok, ok... could you please explain me (step by step if possible :$) what you did? I really don't understand how Ubuntu reads the webcams, since I know it doesn't mount them, but I don't understand how it manages them (with which conf files, etc etc)

---

### Post by omne on 2007-09-27
> **Mamsaac said:**
> Ok, ok... could you please explain me (step by step if possible :$) what you did? I really don't understand how Ubuntu reads the webcams, since I know it doesn't mount them, but I don't understand how it manages them (with which conf files, etc etc)
My tric work if you can use your webcam as root (just a right problem).
Trie a « sudo cheese » (if you have cheese if not do install it !) if the webcam work, then maybe you can do the same as me.

This is just a verification :
Do a « gedit /etc/group » in a terminal and make sure that there’s an entry for « video » mine is : « video:x:44:nemo »

So :
My system is in french, so the UI names may not be the same. I trie :

Clic on : System > Administration > Users and groups
Then : « Manage groups »
Search a « video » group. 
* if there’s a video group do « edit » and add your users.
* If you can’t find the group do « add a group »
Name your group « video » and take the id « 44 » (or wathever you find in /etc/group »
Add the members you want to be able to use the webcam.
Reboot.

You can also edit the /etc/group with a sudo but _**it’s a dangerous file**_ it can break your computer.

Hope it can help.
O.

---

### Post by Mamsaac on 2007-09-27
It's working now. I don't know why the instructions from the topic didn't help, but I followed their own wiki (uvc's) and it worked. It was a bit different.

BTW, other than ekiga and AMSN, which programs work fine?

---

### Post by vincent212 on 2007-09-27
I got my 1520 in the mail yesterday. It has the 965 intel graphics chipset. Nothing described in this thread -- or anywhere else for that matter -- got me past not being able to start the x server -- I spent about eight hours trying to get it to work.:(

Since I really need to run linux on this machine I reinstalled vista. Then I installed vmware player and xubuntu. Works great so far.:)

Here are the instructions:
[http://lifehacker.com/software/linux/run-windows-apps-on-your-linux-desktop-229832.php](http://lifehacker.com/software/linux/run-windows-apps-on-your-linux-desktop-229832.php)

---

### Post by Mamsaac on 2007-09-28
I got the same thing you do. I installed first Edgy and then Feisty, following everything from this topic (except the webcam) step by step. if you wanna give it a try, I guess I can help a little.

---

### Post by Slasher Fun on 2007-09-29
Who tried Gutsy beta ? I tried it a few days ago (Tribe 5 and then Sept. 23 daily build), but no sound (no sound device found) and unable to install restricted drivers (X error after doing so). Is it better now ?

---

### Post by CAD-MAN on 2007-09-29
> **Slasher Fun said:**
> Who tried Gutsy beta ? I tried it a few days ago (Tribe 5 and then Sept. 23 daily build), but no sound (no sound device found) and unable to install restricted drivers (X error after doing so). Is it better now ?

I tried the 24th September daily build, and I don't have sound either, and the restricted Nvidia driver doesn't want to work either :(

I followed the instructions on [this thread,]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound") without any luck, I got to the part of getting the Alsa drivers form a fresh kernel, but gnome-desktop got removed, even when I followed the steps to reinstall it (it didn't want to reinstall itself), so I reinstalled my system.

Im just hoping the official Gutsy release will sort out all of these problems :)

---

### Post by omne on 2007-09-29
> **Slasher Fun said:**
> Who tried Gutsy beta ? I tried it a few days ago (Tribe 5 and then Sept. 23 daily build), but no sound (no sound device found) and unable to install restricted drivers (X error after doing so). Is it better now ?
Still no sound here.
But the nvidia drivers work well.

Omne.

---

### Post by vincent212 on 2007-09-29
Just a quick update. 

As you know may there is no way to get Ubuntu 7.04 to work on a 1520 with the intel graphic chipset. But since I like the machine and I use linux for software development I put in many hours to get linux working on the laptop. If you are curious as to what works you can do what I did.

The config I have is this:

1. Vista home premium
2. Intel CPU and and Intel graphic chipset
3. 2GB of mem 
4. 1280x800 native resoulution

Here is what I did:

1. Install Virtual Box vm
2. Download your favorite version of ubuntu iso image (I actually used debian 4.0 because it is 686 as opposed to a 386 build)
3. Start the VM and mount the .iso image as the CD drive and boot from the cd
4. Install the OS on a virtual drive
5. reboot and unmount the CD .iso image
6. Run install guest additions from the VM menu
7. Run install scripts
8. Provide shared folders for file sharing with windows

What this gives me:
1. A fully functional linux with good performance
2. I can share files between linux and vista both ways without any problems (there is a glitch in that you can only copy files to vista shared folder as opposed editing files in the shared folder -- i.e. you need to edit a file on the linux virtual drive and then copy it to /mnt/vista or something like that -- see below)
2. Vista runs my drivers correctly so I can actually use the laptop with my camera and video and my kids can play games on it
3. I'm actually posting this message from my Debian guest on Vista host

What I gave up:
1. Some performance, but really, linux runs prety fast here (my cpu is only 1.8GH)
2. The screen resolution is 1024x768
3. The linux os does not have its own IP address in this config but rather uses the vista ip addresss

:)

Refer to the following if you get stuck:
[http://www.virtualbox.org/](http://www.virtualbox.org/)
[http://forums.virtualbox.org/viewtopic.php?t=840&postdays=0&postorder=asc&start=0](http://forums.virtualbox.org/viewtopic.php?t=840&postdays=0&postorder=asc&start=0)
[http://forums.virtualbox.org/viewtopic.php?t=43&highlight=tips+shared+folder](http://forums.virtualbox.org/viewtopic.php?t=43&highlight=tips+shared+folder)

---

### Post by vincent212 on 2007-09-29
Actually the 1280x800 resolution works fine in the VritualBox vm after installing guest additions on Debian:

1. Install guest extensions
2. add "1280x800" in Section "Screen"
3. restart xwindows

:guitar:

---

### Post by linux23dragon on 2007-09-29
> **vincent212 said:**
> I got my 1520 in the mail yesterday. It has the 965 intel graphics chipset. Nothing described in this thread -- or anywhere else for that matter -- got me past not being able to start the x server -- I spent about eight hours trying to get it to work.:(

Since I really need to run linux on this machine I reinstalled vista. Then I installed vmware player and xubuntu. Works great so far.:)

Here are the instructions:
[http://lifehacker.com/software/linux/run-windows-apps-on-your-linux-desktop-229832.php](http://lifehacker.com/software/linux/run-windows-apps-on-your-linux-desktop-229832.php)

Hi Vincent

There is people on this thread (that has never before used Linux) that has installed Ubuntu-7.04 on the Dell Inspiron 1520 (that has the 965 Intel graphics).

I have also not seen you ask any questions on any matter in regards to installing Ubuntu-7.04.

It's good that you looked around for answers, but..  People can only help you if you have asked questions about the issues "you" had.  


Thanks 

PS: Vista is of topic and is not supported in this thread.

---

### Post by vincent212 on 2007-09-30
linux23dragon I don't know -- there are a few versions of the intel graphics chips as I understand it. Odin1965 posted something here that looked very promising, unfortunately it didnt work for my me.

The drivers are here in source right?
[http://www.intellinuxgraphics.org/documentation.html](http://www.intellinuxgraphics.org/documentation.html)

But where are the .deb packages for each?

Dont get me wrong. I appreciate what you are doing here. Its just that I think there are a large number of variations in hardware and it works for some people and not for others. I think you make it sound a little bit too easy.

I think it would help in your survey if you could collect information about how many people got it to work (and how many did not) and what hardware config they had exactly.

I hope you like my suggestion of using the virtual machine. I think it makes sense for some people. I posted the suggestion here as there could be some frustrated readers of this thread. I was one of them

---

### Post by linux23dragon on 2007-09-30
> **vincent212 said:**
> linux23dragon I don't know -- there are a few versions of the intel graphics chips as I understand it. Odin1965 posted something here that looked very promising, unfortunately it didnt work for my me.

The drivers are here in source right?
[http://www.intellinuxgraphics.org/documentation.html](http://www.intellinuxgraphics.org/documentation.html)

But where are the .deb packages for each?

Odin1965 also worked out how to get the graphics card working with the new Intel driver package.  All of that information is in the first post. 

> **vincent212 said:**
> 
I think it would help in your survey if you could collect information about how many people got it to work (and how many did not) and what hardware config they had exactly.

Most people have got their ATI, Nvidia and Intel graphics working fine.  If they have an issue then they would ask for help.


If you want to try to install Ubuntu-7.04, I'll help you out (if you ask for it).  Otherwise if you are happy with what you have got, then all the better for you.

---

### Post by linux23dragon on 2007-09-30
> **Mamsaac said:**
> It's working now. I don't know why the instructions from the topic didn't help, but I followed their own wiki (uvc's) and it worked. It was a bit different.

BTW, other than ekiga and AMSN, which programs work fine?

I understand that Kopete should work with KDE-4.0.  You did see the patch list from the first post?

---

### Post by linux23dragon on 2007-09-30
> **omne said:**
> Still no sound here.
But the nvidia drivers work well.

Omne.

So this fix does not work any more?

[http://ubuntuforums.org/showpost.php?p=3288090&postcount=273](http://ubuntuforums.org/showpost.php?p=3288090&postcount=273)

---

### Post by omne on 2007-09-30
> **linux23dragon said:**
> So this fix does not work any more?

[http://ubuntuforums.org/showpost.php?p=3288090&postcount=273](http://ubuntuforums.org/showpost.php?p=3288090&postcount=273)

I don’t tried it since the last kernel update : I can do it but I’ll do it after the stable realease : for « normal » user this solution is too hard. I expect ubuntu to propose a better solution.
But I can tried it if you want to know if it work.

Omnë.

---

### Post by DarthTibault on 2007-09-30
Finally got my laptop (after 2 months!!).
Instead of letting the xserver crash and editing the xorg.conf file manually, I just started the 7.04 live CD in 'safe graphics mode', which loads the vesa driver automaticly: much easier. 
When the intel sata error appears I just typed "modprobe piix" followed by "exit" and Ubuntu started.
I found out you're not supposed to resize vista partitions with Gparted the hard way (according to the manual it only works half of the time), I landed in the other half: had to reformat everything (as such I haven't gotten MediaDirect to work, if anyone has a good linux alternative, let me know). 
So after I started over and finished the install I added piix to /etc/initramfs-tools/modules and rebooted. Everything (including sound) seems to work. I did a dist-upgrade, reboot and used envy to install the nvidia drivers.
I do have a few issues:
Sound works, but in alsa mixer I only have PCM
After a suspend audio doesn't work anymore
When I shutdown my pc, at the moment the power is usually cut my screen starts flashing, some weird testscreenish things show up, my harddrive gives an ugly clack noise and then the power is cut.
I don't really care about the flashing, but that harddrive sound doesn't sound healthy. I think I've only seen two people mention the hardrive noise in here... Am I the only one with these issues? Is there a fix?
TIA

DarthTibault

---

### Post by omne on 2007-09-30
> **DarthTibault said:**
> 
When I shutdown my pc, at the moment the power is usually cut my screen starts flashing, some weird testscreenish things show up, my harddrive gives an ugly clack noise and then the power is cut.
I don't really care about the flashing, but that harddrive sound doesn't sound healthy. I think I've only seen two people mention the hardrive noise in here... Am I the only one with these issues? Is there a fix?
DarthTibault

Here is the launchpad entry : [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810)

And a thread on the french forum (with a solution from the launchpad) : [http://forum.ubuntu-fr.org/viewtopic.php?pid=898480#p898480](http://forum.ubuntu-fr.org/viewtopic.php?pid=898480#p898480)

This bug is not in gutsy. 

Omnë.

---

### Post by linux23dragon on 2007-09-30
> **omne said:**
> I don’t tried it since the last kernel update : I can do it but I’ll do it after the stable realease : for « normal » user this solution is too hard. I expect ubuntu to propose a better solution.
But I can tried it if you want to know if it work.

Omnë.

I agree that the end user will find this too hard (as a fix).  I'm aware that the audio fix had worked in the past.

  
I recommend  owners of this laptop to report bugs ASAP to the Ubuntu developers.  It is the only way of making sure that all the issues are fixed and ready to go in the final release of 7.10.

This includes the Sound card, Wifi, Web Cam and the X server driver issues (if any).

---

### Post by linux23dragon on 2007-09-30
> **DarthTibault said:**
> Finally got my laptop (after 2 months!!).
Instead of letting the xserver crash and editing the xorg.conf file manually, I just started the 7.04 live CD in 'safe graphics mode', which loads the vesa driver automaticly: much easier. 
When the intel sata error appears I just typed "modprobe piix" followed by "exit" and Ubuntu started.
I found out you're not supposed to resize vista partitions with Gparted the hard way (according to the manual it only works half of the time), I landed in the other half: had to reformat everything (as such I haven't gotten MediaDirect to work, if anyone has a good linux alternative, let me know). 
So after I started over and finished the install I added piix to /etc/initramfs-tools/modules and rebooted. Everything (including sound) seems to work. I did a dist-upgrade, reboot and used envy to install the nvidia drivers.
I do have a few issues:
Sound works, but in alsa mixer I only have PCM
After a suspend audio doesn't work anymore
When I shutdown my pc, at the moment the power is usually cut my screen starts flashing, some weird testscreenish things show up, my harddrive gives an ugly clack noise and then the power is cut.
I don't really care about the flashing, but that harddrive sound doesn't sound healthy. I think I've only seen two people mention the hardrive noise in here... Am I the only one with these issues? Is there a fix?
TIA

DarthTibault

Can you try substituting "dell-laptop" with the following  model option, to see if the headphones work without the main speakers please?

```
options snd-hda-intel model=laptop
```


What graphics card do you have?

---

### Post by omne on 2007-09-30
> **linux23dragon said:**
> I agree that the end user will find this too hard (as a fix).  I'm aware that the audio fix had worked in the past.

  
I recommend  owners of this laptop to report bugs ASAP to the Ubuntu developers.  It is the only way of making sure that all the issues are fixed and ready to go in the final release of 7.10.

This includes the Sound card, Wifi, Web Cam and the X server driver issues (if any).

There’s already bug reports for the sound isue. Here no problems with the webcam (but I don’t play mutch with it : ekiga don’t work), wifi or X server.

---

### Post by linux23dragon on 2007-09-30
> **omne said:**
> There’s already bug reports for the sound isue. Here no problems with the webcam (but I don’t play mutch with it : ekiga don’t work), wifi or X server.

The web cam works.  You need to use the V4L2 module (enabled in ekiga preferences)  to use it.

---

### Post by DarthTibault on 2007-09-30
HDD noise: FIXED
Big D'OH here, I'd already tried the fix omne reposted, but I forgot to make it executable. So thank you omne for making me look at it again.

@Linux23dragon:
- Using dell-laptop or laptop makes no difference
- I have a NVidia Geforce 8600M GT

I've seen disabling the bootsplash as a workaround, haven't tested it myself as it's just a workaround and not a fix. It doesn't really bother me anyway, I usually close the lid long before it starts flashing...

---

### Post by omne on 2007-09-30
> **linux23dragon said:**
> I agree that the end user will find this too hard (as a fix).  I'm aware that the audio fix had worked in the past.

  
I recommend  owners of this laptop to report bugs ASAP to the Ubuntu developers.  It is the only way of making sure that all the issues are fixed and ready to go in the final release of 7.10.

This includes the Sound card, Wifi, Web Cam and the X server driver issues (if any).

Ok, back again :o). I’m still with gutsy. I install the alsa drivers : sound work. But still the sound isue with headphone (I don’t tried yet tu put « laptop » insead of « dell-laptop »).

And… the wiki (and all network) died after 15-20 minutes (no using the net, but being connected). Plug in back an ethernet cable don’t solve the problem.
In fact, nm-applet died. If I trie a « nm-applet » in a console the answer is : «/usr/bin/esd not found ».
Is the sound kill my network ?

Strange…

---

### Post by CAD-MAN on 2007-09-30
Re: sound issues

linux23dragon, I followed the guide on that link where it says to do the following:

```
sudo apt-get install alsa-source
cd && mkdir alsa-patched && cd alsa-patched
tar -jxvf /usr/src/alsa-driver.tar.bz2
cd modules/alsa-driver/
wget -O alsa-kernel/pci/hda/patch_analog.c http://launchpadlibrarian.net/9021234/patch_analog.c
./configure --with-cards=hda-intel && make
sudo make install
sudo cp ./modules/snd-hda-intel.ko /lib/modules/$( uname -r )/ubuntu/media/snd-hda-intel/
sudo depmod -a
```

I get as far as './configure --with-cards=hda-intel && make', and I get the following response:

```
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.

```

This **_always**_ happens to me whenever I try to run './configure' - it never works!! Can anybody please  tell me where I'm going wrong?

Thanks

---

### Post by omne on 2007-09-30
Did you install build-essential ?
O.

---

### Post by CAD-MAN on 2007-09-30
Don't know if build-essential is installed, I'll check if I can sort out this new (slightly larger problem):

I tried this 'fix' (found[here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/122560"):
 
```

Try this updated Gusty l-u-m package:

wget http:people.ubuntu.com/~rtg/linux-ubuntu-modules-2.6.22-10-generic_2.6.22-10.24_i386.deb-122560.1
sudo dpkg -i linux-ubuntu-modules-2.6.22-10-generic_2.6.22-10.24_i386.deb-122560.1
sudo reboot

```

The first line worked, and it downloaded something, but the second line returned an error. Now, if I click 'Add remove applications', I get the following message:

```
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
```

I got the update fine, but then when I try 'sudo apt-get install -f', I get this:

```
Do you want to continue [Y/n]? Y
(Reading database ... 102772 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-10-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-10-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-10-generic
Cannot find /lib/modules/2.6.22-10-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-10-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-10-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-10-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Help! Please! I just want to get rid of the 2.6.22-10 thing (which I think is some kind of out-dated code...)

---

### Post by CAD-MAN on 2007-09-30
Sorry for the bump, I just want to get this sorted before shutting down my computer...

---

### Post by DarthTibault on 2007-09-30
> **CAD-MAN said:**
> Sorry for the bump, I just want to get this sorted before shutting down my computer...

Well, if the problem lies with the software management system, I'd start synaptic, do an update of the packages, filter on broken packages, see if I can correct them, and to a dist-upgrade.

EDIT:
> ```
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
```

This always happens to me whenever I try to run './configure' - it never works!! Can anybody please tell me where I'm going wrong?
"See `config.log' for more details." would be a good start, though it sounds to me like you didn't install build-essential (as mentioned before).

---

### Post by CAD-MAN on 2007-09-30
This is what I get when I try to remove it in Synaptic:

```
E: linux-ubuntu-modules-2.6.22-10-generic: subprocess post-removal script returned error exit status 1
```

When trying a dist-upgrade:

```
(Reading database ... 102772 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-10-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-10-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-10-generic
Cannot find /lib/modules/2.6.22-10-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-10-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-10-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-10-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Its this 'linux-ubuntu-modules-2.6.22-10-generic' thats messing things up, I think I just need to get rid of it/update it, but I don't know how.


When trying to install build-essential (sudo apt-get install build-essential), I get this:

```
(Reading database ... 102772 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-10-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-10-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-10-generic
Cannot find /lib/modules/2.6.22-10-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-10-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-10-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-10-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


So linux-ubuntu-modules-2.6.22-10-generic is definitely messing about and looks to be the problem.

---

### Post by DarthTibault on 2007-09-30
> **CAD-MAN said:**
> 
So linux-ubuntu-modules-2.6.22-10-generic is definitely messing about and looks to be the problem.

I once had a stubborn broken package like that, can't remember for the life of me how I got rid of it....
Do a reboot. Try again. Make sure you don't boot in 2.6.22-10 and try again. Why did you install modules for an older kernel anyway?

---

### Post by CAD-MAN on 2007-09-30
> **DarthTibault said:**
> I once had a stubborn broken package like that, can't remember for the life of me how I got rid of it....
Do a reboot. Try again. Make sure you don't boot in 2.6.22-10 and try again. Why did you install modules for an older kernel anyway?

I only realised it was for an older kernel after I had done it. I was trying to fix my sound, and followed a guide where installing that module was part of the process. (Im a complete noob)

How do I make sure that I dont boot in 2.6.22-10 when I reboot?

---

### Post by DarthTibault on 2007-09-30
> **CAD-MAN said:**
> 
How do I make sure that I dont boot in 2.6.22-10 when I reboot?

Well, it's probably not even on your drive anymore, but at the grub menu (you may have to press <esc> to see it) you should be able to choose a kernel.

---

### Post by CAD-MAN on 2007-09-30
Thanks for all your help Darth, I'll reboot now, and hope for the best. :)

---

### Post by CAD-MAN on 2007-09-30
I've rebooted and tried everything to get rid of it, still not working :(

This is very annoying, because its preventing me from being able to install or uninstall anything.

---

### Post by linux23dragon on 2007-09-30
> **CAD-MAN said:**
> I've rebooted and tried everything to get rid of it, still not working :(

This is very annoying, because its preventing me from being able to install or uninstall anything.

Hi 


You might need to reinstall (using the synaptic package manager)  "2.6.22-10-generic" because the package manager thinks that "linux-ubuntu-modules-2.6.22-10-generic" is still installed.  And they do not seem to exist on your system.  However "linux-ubuntu-modules-2.6.22-10-generic"  appears to be setup to be used (or default kernel).

To see if this is the case.   In the terminal, use the following commands, to see what kernels you have installed:-

```
 
ls -la /boot &&
ls -la /lib/modules
```

Write the list of installed kernels down on paper (or copy past to a text file), and check to see if you have "linux-ubuntu-modules-2.6.22-10-generic" listed.

If you don't have  "linux-ubuntu-modules-2.6.22-10-generic" installed, then see if you can reinstall  "linux-ubuntu-modules-2.6.22-10-generic"  by using the Sysnaptic pakage manager or in the terminal:-

```

sudo aptitude install linux-ubuntu-modules-2.6.22-10-generic
```
Also  you can try to purge the kernel like so.
```
 sudo aptitude purge linux-ubuntu-modules-2.6.22-10-generic
```
If that does not work out for you then try to install a different kernel (like the low latency kernel).  You can use the same "install" command line above by substituting  "linux-ubuntu-modules-2.6.22-10-generic" with a known gusty kernel like "linux-image-2.6.22-10-lowlatency".  The system should think that "linux-image-2.6.22-10-lowlatency"  is the new default kernel used.


Remember, when you reinstall or install a new kernel, you will need to reinstall 3rd party drivers (like the vidieo card and Web cam drivers)


Can someone list all Gusty kernels please?

---

### Post by CAD-MAN on 2007-10-01
> **linux23dragon said:**
> Hi 


You might need to reinstall (using the synaptic package manager)  "2.6.22-10-generic" because the package manager thinks that "linux-ubuntu-modules-2.6.22-10-generic" is still installed.  And they do not seem to exist on your system.  However "linux-ubuntu-modules-2.6.22-10-generic"  appears to be setup to be used (or default kernel).

To see if this is the case.   In the terminal, use the following commands, to see what kernels you have installed:-

```
 
ls -la /boot &&
ls -la /lib/modules
```

Write the list of installed kernels down on paper (or copy past to a text file), and check to see if you have "linux-ubuntu-modules-2.6.22-10-generic" listed.

If you don't have  "linux-ubuntu-modules-2.6.22-10-generic" installed, then see if you can reinstall  "linux-ubuntu-modules-2.6.22-10-generic"  by using the Sysnaptic pakage manager or in the terminal:-

```

sudo aptitude install linux-ubuntu-modules-2.6.22-10-generic
```
Also  you can try to purge the kernel like so.
```
 sudo aptitude purge linux-ubuntu-modules-2.6.22-10-generic
```
If that does not work out for you then try to install a different kernel (like the low latency kernel).  You can use the same "install" command line above by substituting  "linux-ubuntu-modules-2.6.22-10-generic" with a known gusty kernel like "linux-image-2.6.22-10-lowlatency".  The system should think that "linux-image-2.6.22-10-lowlatency"  is the new default kernel used.


Remember, when you reinstall or install a new kernel, you will need to reinstall 3rd party drivers (like the vidieo card and Web cam drivers)


Can someone list all Gusty kernels please?



After 'ls -la /boot &&
ls -la /lib/modules' :

```
> ls -la /lib/modules
total 17884
drwxr-xr-x  3 root root    4096 2007-10-01 14:24 .
drwxr-xr-x 22 root root    4096 2007-09-30 17:12 ..
-rw-r--r--  1 root root  424170 2007-09-23 22:08 abi-2.6.22-12-generic
-rw-r--r--  1 root root   75326 2007-09-23 22:08 config-2.6.22-12-generic
drwxr-xr-x  2 root root    4096 2007-09-29 14:48 grub
-rw-r--r--  1 root root       0 2007-09-30 17:33 initrd.img-2.6.22-10-generic
-rw-r--r--  1 root root 7523879 2007-09-29 23:16 initrd.img-2.6.22-12-generic
-rw-r--r--  1 root root 7524012 2007-09-29 14:13 initrd.img-2.6.22-12-generic.bak
-rw-r--r--  1 root root  103204 2007-09-28 11:06 memtest86+.bin
-rw-r--r--  1 root root  823920 2007-09-23 22:08 System.map-2.6.22-12-generic
-rw-r--r--  1 root root 1768280 2007-09-23 22:08 vmlinuz-2.6.22-12-generic
total 20
drwxr-xr-x  3 root root  4096 2007-09-30 17:33 .
drwxr-xr-x 18 root root 12288 2007-09-29 23:15 ..
drwxr-xr-x  7 root root  4096 2007-09-29 23:16 2.6.22-12-generic

```

Doesn't look as if 2.6.22-10-generic is there...

Result of 'sudo aptitude install linux-ubuntu-modules-2.6.22-10-generic':

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
The following packages are BROKEN:
  linux-ubuntu-modules-2.6.22-10-generic 
The following packages have been kept back:
  capplets-data ekiga gnome-control-center gnome-power-manager gparted hal 
  hal-device-manager language-pack-es language-pack-gnome-en 
  language-pack-gnome-es language-pack-gnome-pt language-pack-pt libc6 
  libc6-i686 libgnome-window-settings1 libhal-storage1 libhal1 
  libpaper-utils libpaper1 libusplash0 tasksel tasksel-data ubuntu-artwork 
  ubuntu-desktop ubuntu-minimal ubuntu-standard usplash xkb-data 
0 packages upgraded, 0 newly installed, 0 to remove and 28 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  linux-ubuntu-modules-2.6.22-10-generic: Depends: linux-image-2.6.22-10-generic which is a virtual package.
Resolving dependencies...
E: I wasn't able to locate file for the linux-ubuntu-modules-2.6.22-10-generic package. This might mean you need to manually fix this package.
The following actions will resolve these dependencies:

Remove the following packages:
linux-ubuntu-modules-2.6.22-10-generic

Score is -9881

Accept this solution? [Y/n/q/?] Y
The following packages will be automatically REMOVED:
  linux-ubuntu-modules-2.6.22-10-generic 
The following packages have been kept back:
  capplets-data ekiga gnome-control-center gnome-power-manager gparted hal 
  hal-device-manager language-pack-es language-pack-gnome-en 
  language-pack-gnome-es language-pack-gnome-pt language-pack-pt libc6 
  libc6-i686 libgnome-window-settings1 libhal-storage1 libhal1 
  libpaper-utils libpaper1 libusplash0 tasksel tasksel-data ubuntu-artwork 
  ubuntu-desktop ubuntu-minimal ubuntu-standard usplash xkb-data 
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.22-10-generic 
0 packages upgraded, 0 newly installed, 1 to remove and 28 not upgraded.
Need to get 0B of archives. After unpacking 8405kB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 101979 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-10-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-10-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-10-generic
Cannot find /lib/modules/2.6.22-10-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-10-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-10-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-10-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      

```



I tried the purge anyway:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
The following packages have been kept back:
  capplets-data ekiga gnome-control-center gnome-power-manager gparted hal 
  hal-device-manager language-pack-es language-pack-gnome-en 
  language-pack-gnome-es language-pack-gnome-pt language-pack-pt libc6 
  libc6-i686 libgnome-window-settings1 libhal-storage1 libhal1 
  libpaper-utils libpaper1 libusplash0 tasksel tasksel-data ubuntu-artwork 
  ubuntu-desktop ubuntu-minimal ubuntu-standard usplash xkb-data 
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.22-10-generic{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 28 not upgraded.
Need to get 0B of archives. After unpacking 8405kB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 101979 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-10-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-10-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-10-generic
Cannot find /lib/modules/2.6.22-10-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-10-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-10-generic (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-10-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done 
```


What is the low latency kernel?

Thanks for all your help, much appreciated :)


P.S. I get the same damn error message when trying to install the low-latency kernel using sudo aptitude install linux-image--2.6.22-10-lowlatency :(

---

### Post by k2chris1983 on 2007-10-01
> P.S. I get the same damn error message when trying to install the low-latency kernel using sudo aptitude install linux-image--2.6.22-10-lowlatency 

The lowlatency configs your Kernel to run at 1000Mhz instead the default 250Mhz.  So it;s faster

---

### Post by linux23dragon on 2007-10-01
> **CAD-MAN said:**
> 
FATAL: Could not open '/boot/System.map-2.6.22-10-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-10-generic
Cannot find /lib/modules/2.6.22-10-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-10-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-10-generic (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-10-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done [/CODE]


What is the low latency kernel?

Thanks for all your help, much appreciated :)


P.S. I get the same damn error message when trying to install the low-latency kernel using sudo aptitude install linux-image--2.6.22-10-lowlatency :(


Well its time to see if we can trick the system into thinking that it has the missing kernel.

You have the /boot/initrd.img-2.6.22-10-generic so we are now going to try to install dummy software to trick the package manager.   Use the following commands in a terminal:-
```

sudo touch /boot/System.map-2.6.22-10-generic &&
sudo mkdir /lib/modules/2.6.22-10-generic
```

Then try to use the same commands (used in the last post) to remove "2.6.22-10-generic".

If that works out for you, then check to see if the boot loader is setup correctly before shutting down.  You will need to inspect /boot/grub/menu.lst to see what default boot option is used.

Some times the boot loader is easily fixed by installing a different kernel anyway, so you should be OK.

Edit: Use "mc",  it's a nice tool to have.  Just type mc in the terminal and follow the instructions to install the package (if you were able to fix the kernel issues)

---

### Post by Shaidtan on 2007-10-02
I'm sure most of this has been covered, and I apologize if I am repeating anything, but here are some findings that may help you guys out from my adventures in Gentoo on the 1520.

Sound:
Under 2.6.22 I could only get sound to work if I compiled the sound driver into the kernel. As a module it would load but Alsa would fail to detect it. I updated to 2.6.23-r8 and the driver works as a module. Headphone jack detection works with no modifications. The line in does not work (except as a line out) but I have no use for that atm so I haven't played with the options.

Wireless:
I have the BCM43xx card. The in kernel driver works in both the 2.6.22 and 2.6.23 kernels. I use wpa_supplicant and wpa2 encryption works well.

Wired NIC:
The internal nic works fine. With netplug everything is backgrounded nicely.

nVidia:
The 8600GT works with both the 100.14.11 and 100.14.19. Hibernate/Suspend is not supported however. vbetool does not seem to support this card either. External monitors seem to work with FN-F8 and nvidia-settings and xrandr seem decent at changing resolutions. I have experienced some instability with this however in both driver versions.

Hibernate/Suspend:
I'm using sysfs that's built into the 2.6.23 kernel. I haven't played with suspend2 due to the issues with sound described above (I see no point in sleep states if things don't work after resuming). Configuring hibernate-script to restart Alsa and reload the bcm43xx driver (in the common.conf file) renders the system fully usable after hibernate/resume. This seems to work flawlessly in console mode, but is extremely flaky in X with the nVidia driver. Using the vesa driver in X makes hibernate stable.

Using the same configuration suspend to ram works with the exception of no display after resume. Sound and wireless do work however if you don't mind flying blind.

Misc:
I'm using the media buttons through e17 (because I'm lazy) but they work well. Mapping the play/paus/ff/rw/stop buttons to control Audacious works well. I created simple volume up/down/mute scripts to use with the appropriate buttonsI also have the system set to blank the display when the lid is closed.

There are three oddities here that I frankly haven't gotten around to looking into. First is if I press a media button the backlight comes on and I have to wait for the timeout or open/close the lid. Second scripting the lid close event is tricky as the display comes back in standby if I don't put two 'on' lines in the open part of the script. (the combination of these two things is intersting but not detrimental). Third is if an external monitor is connected and active and I close the lid it goes off. I figure I'll fix these things when I get unlazy for an hour or two.


That's all that comes to mind right now. I'll post an addendum if I think of anything else.

---

### Post by DarthTibault on 2007-10-02
> **DarthTibault said:**
> After a suspend audio doesn't work anymore
When I shutdown my pc, at the moment the power is usually cut my screen starts flashing, some weird testscreenish things show up, my harddrive gives an ugly clack noise and then the power is cut

As I already mentioned, I got rid of the harddrive problem. I now also fixed the 'no sound after a suspend problem': adding the scripts mentioned on the Dell 1420n audio wiki page (and making them executable, don't know if it's necessary, but it works). The flashing thing seems to've disappeared as well, though I don't know why, I did try a few things, but I can't really say what did it.

---

### Post by CAD-MAN on 2007-10-02
Its ok, I got fed up with the thing, so I just burnt a CD of my home folder, and reinstalled my system :D

Thanks for your help all of you, much appreciated :)

---

### Post by linux23dragon on 2007-10-02
An update is due soon for Feisty, and Gusty should be released 15 days from now.

Should we use this thread to support Gusty, or should we make a new thread?

Would anyone like to have a go at supporting Gusty, since I don't own this Notebook (I used My sisters boyfriends Notebook to work out some of the issues)?

---

### Post by linux23dragon on 2007-10-02
> **CAD-MAN said:**
> Its ok, I got fed up with the thing, so I just burnt a CD of my home folder, and reinstalled my system :D

Thanks for your help all of you, much appreciated :)

Well done CAD-MAN.  You are doing well for someone who has never used Linux before :) 

Can you see how much control you now have over your own custom system?

---

### Post by omne on 2007-10-03
A new thread is much better I think&#8230; Can you post the link here ?
New kernel today, and new alsa-sound&#8230;
O.

---

### Post by mac-duff on 2007-10-03
Hi,
well, I followed the instruductions from the first site to setup my webcam but when I start try to use it with Amsn or Ekiga the software crashes as well as the web cam (light is still on). 
I also added my user to the video group with no success.... why must in the linux world everything so complicated?

cu

---

### Post by CAD-MAN on 2007-10-03
> **linux23dragon said:**
> Well done CAD-MAN.  You are doing well for someone who has never used Linux before :) 

Can you see how much control you now have over your own custom system?

Thanks linux23dragon :D Yep, I love linux so far, even though I can't quite get everything working as it should. I'll just be sure to back everything up before trying to fix things, so that I don't lose important data.

> **omne said:**
> A new thread is much better I think… Can you post the link here ?
New kernel today, and new alsa-sound…
O.

:o Does this mean that there is hope that we will have sound up and running?! Downloading updates now... fingers crossed eh?

---

### Post by CAD-MAN on 2007-10-03
The update didn't get my sound working, but...

**_I HAVE SOUND WORKING!!!!!!**_ It's great!

Basically, my system didn't even seem to have alsamixer installed, and I'd tried various ways to get the sound working, to no avail.

I followed the guide on this link - [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto") Can't remember where I found this link, or whether I just stumbled on it. I only followed the guide as far as completing the first section (Update to the latest version of ALSA), and then, on reboot, my sound has been up and running! :D

I'm a complete noob and it worked for me, so if your using the Insprion 1520, I don't see why it shouldn't work for you!

---

### Post by linux23dragon on 2007-10-03
> **CAD-MAN said:**
> The update didn't get my sound working, but...

**_I HAVE SOUND WORKING!!!!!!**_ It's great!

Basically, my system didn't even seem to have alsamixer installed, and I'd tried various ways to get the sound working, to no avail.

I followed the guide on this link - [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto") Can't remember where I found this link, or whether I just stumbled on it. I only followed the guide as far as completing the first section (Update to the latest version of ALSA), and then, on reboot, my sound has been up and running! :D

I'm a complete noob and it worked for me, so if your using the Insprion 1520, I don't see why it shouldn't work for you!


Ah so you were able to use the Alsa howto to get the sound card to work in Gusty?
Thats goods news.  I have a better howto [here]("http://ubuntuforums.org/showthread.php?t=530374&highlight=1520+dell+alsa+hda+intel"), That should work OK for gusty as well.  At the moment it is setup for the 7.04 (Feisty) Kernel.  But an edit here and there should get this up and running for Gusty as well.

Thanks for the report.

---

### Post by linux23dragon on 2007-10-03
> **mac-duff said:**
> Hi,
well, I followed the instruductions from the first site to setup my webcam but when I start try to use it with Amsn or Ekiga the software crashes as well as the web cam (light is still on). 
I also added my user to the video group with no success.... why must in the linux world everything so complicated?

cu

It depends on how new the hardware is. Ubuntu will install and work (without the driver setup issues) on earlier computers.   For example, Installing Linux on the 1520 Notebook will need less work (in regards to setting up drivers and such) when Gusty comes out, in 13 days or so.

The web cam looks to be working O.K.  Did you try to use the V4L2 module in ekiga?
Are you using the standard (out of the box, Ubuntu provided) amsn.  Or have you downloaded the latest version of amsn yourself.  I don't think amsn (currently provided by Ubuntu) works.

Edit: 
I forgot to mention that the Linux kernel 2.6.20 had some very big driver changes as well.  This had affected (in our case) the SATA drivers.  The New changes in the Linux kernel will allow for better overall hardware performance improvements. 

Normally Linux does not have the current issues that we have with Ubuntu-7.04.  The kernel 2.6.22 (in 7.10, Gusty) has been improved since then.  And there is also other fixes (and possibly other kernel back ports) that has been supported by Ubuntu.

Remember that some of the computer hardware is built to run on windows.  However, Open source Developers have worked hard (without having most of the hardware specs) to get this hardware to run in Linux and BSD.  
 
The Linux UVC web cam driver support in Linux is very new (about 2 years running I think).  And the good news is, the driver support for your web cam is been getting better and better every month. You will find more future web cam applications will be able to use you web cam, by the end of this year.

Hope this helps.

---

### Post by mac-duff on 2007-10-04
Hi, thx for the reply. well I guess at first I am waiting for the next ubuntu release. But anyway, I am still happy that I can use my headset :D

---

### Post by kirkquitar on 2007-10-05
My 1720 is scheduled to arrive on the 9th, and I'm hoping to install Gutsy Beta. Should the guide for Feisty apply to Gutsy as well? I'm hoping that some of the fixes are in place, so I'll use whichever steps are necessary.

Is there already a Gutsy forum for Dell 1420/1520/1720? Or should I start one if I find that the install worked/had problems. (I can't find one)

---

### Post by CAD-MAN on 2007-10-05
> **kirkquitar said:**
> My 1720 is scheduled to arrive on the 9th, and I'm hoping to install Gutsy Beta. Should the guide for Feisty apply to Gutsy as well? I'm hoping that some of the fixes are in place, so I'll use whichever steps are necessary.


You should have no problems installing Gutsy. I installed it on my 1520 (very similar to the 1720), using the graphical user interface - there was no need to use the alternate CD.

If you have sound issues (as I did), then you could try following the link that I posted in a previous post - worked for me :)

> **kirkquitar said:**
> 
Is there already a Gutsy forum for Dell 1420/1520/1720? Or should I start one if I find that the install worked/had problems. (I can't find one)

Not that Im aware of, but I don't even see the point in making a new one - do we really need two different threads on the same laptop model, where the only difference is a new release of the same operating system?

---

### Post by CAD-MAN on 2007-10-06
Hmm, just done a software update, and the sound has died on me again. :( I guess this is because the kernel was updated - we're on 2.6.22-13 now, instead of 2.6.22-12. Any ideas on why the changes that I made to the system to get the sound working on the old kernel were not brought forward to the new one? (Remember -I'm a noob :)...)

---

### Post by CAD-MAN on 2007-10-06
Fixed it, it seems that I just had to recompile some alsa stuff to get it to work on the new kernel:

```
cd /usr/src/alsa/alsa-driver-1.0.14
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
```

```
cd usr/src/alsa/alsa-lib-1.0.14a
sudo ./configure
sudo make
sudo make install
```

```
cd usr/src/alsa/alsa-utils-1.0.14
sudo ./configure
sudo make
sudo make install

```

:D

---

### Post by linux23dragon on 2007-10-06
> **CAD-MAN said:**
> Fixed it, it seems that I just had to recompile some alsa stuff to get it to work on the new kernel:

```
cd /usr/src/alsa/alsa-driver-1.0.14
sudo ./configure --with-cards=hda-intel
sudo make
sudo make install
```

```
cd usr/src/alsa/alsa-lib-1.0.14a
sudo ./configure
sudo make
sudo make install
```

```
cd usr/src/alsa/alsa-utils-1.0.14
sudo ./configure
sudo make
sudo make install

```

:D

Do you have WiFi?

If so how is the WiFi running for you in Gusty Beta?

---

### Post by CAD-MAN on 2007-10-06
> **linux23dragon said:**
> Do you have WiFi?

If so how is the WiFi running for you in Gusty Beta?

Yep, I do have WiFi - it worked right out of the box. Its a Netgear Rangemax DG834PN

---

### Post by linux23dragon on 2007-10-06
UPDATE: (07-10-07) Included Dell Wiki support fixes that should benefit the Dell Inspiron 1520. Added the Netgear Rangemax WiFi, to the working hardware list.

---

### Post by chess360 on 2007-10-08
Hi all! Attracted by the Beryl mode from youtube I am very interested in Ubuntu. I'm new to Linux.

I downloaded 7.10 beta today (8 Oct 2007). I am running it from the live CD in my Inspiron 1520 to post this.

- It recognizes the display card (GeForce 8600 M) and the wireless lan card (Intel 3945 agb). Both are running well. I could not test run Beryl from the Live CD mode. 
- The sound  card (sigmaltel) is not working.
- The rest is not tested yet. But the applications (Firefox, Open Office 2.3 etc) seem running smoothly.

As I can post this, I guess installing 7.10 is not a problem. The rest, I think, would be relatively easy to fix.

It seems that the best way to install ubuntu on Inspiron 1520 is go for the new version. Personally I will wait for the formal release. It is just 10 days to go. 

Hope this will help other Inspiron 1520 users.

---

### Post by adwatkin19 on 2007-10-08
I have installed the BETA version on my brand new 1520

i can tell you that everything worked but the soundcard

To solve this i followed an earlier solution posted by CADMAN where he downloaded, compiled and installed the latest ALSA drivers, well i followed this, but the 10.0.14 didnt work, but the release candidate ones did work for me, so now i have perfect sound. 

Just one thing i cant seem to check is the microphone, i would like to be working to use through amsn or pidgin, any ideas?

just incase you were wondering my spec is:
centrino dual core (1.5 ghz)
1gb Ram
Nvidia Geforce 8600M GT 256mb
then everything else is the standard

hope that helps people. 

Adam

---

### Post by CAD-MAN on 2007-10-08
> **chess360 said:**
> Hi all! Attracted by the Beryl mode from youtube I am very interested in Ubuntu. I'm new to Linux.

I downloaded 7.10 beta today (8 Oct 2007). I am running it from the live CD in my Inspiron 1520 to post this.

- It recognizes the display card (GeForce 8600 M) and the wireless lan card (Intel 3945 agb). Both are running well. I could not test run Beryl from the Live CD mode. 
- The sound  card (sigmaltel) is not working.
- The rest is not tested yet. But the applications (Firefox, Open Office 2.3 etc) seem running smoothly.

As I can post this, I guess installing 7.10 is not a problem. The rest, I think, would be relatively easy to fix.

It seems that the best way to install ubuntu on Inspiron 1520 is go for the new version. Personally I will wait for the formal release. It is just 10 days to go. 

Hope this will help other Inspiron 1520 users.

Yep, waiting for the 'official' release would probably be best (I just went with the Gutsy beta because I didn't want to wait, and it seemed the best option for me, given my failings with the Feisty alternate CD).

If you find that sound doesn't work when you install, you could try compiling the alsa drivers, lib and utils, as detailed in a previous post. 

Im sure you'll love Ubuntu once you have it up and running (I know I am). I'm a brand new Linux convert, having stepped out of Vista's portals a couple of weeks ago - and Im loving it! sudo aptitude install is genius, as is the flexibility that the command line offers! (Im still a noob!)



> **adwatkin19 said:**
> I have installed the BETA version on my brand new 1520

i can tell you that everything worked but the soundcard

To solve this i followed an earlier solution posted by CADMAN where he downloaded, compiled and installed the latest ALSA drivers, well i followed this, but the 10.0.14 didnt work, but the release candidate ones did work for me, so now i have perfect sound. 

Just one thing i cant seem to check is the microphone, i would like to be working to use through amsn or pidgin, any ideas?

just incase you were wondering my spec is:
centrino dual core (1.5 ghz)
1gb Ram
Nvidia Geforce 8600M GT 256mb
then everything else is the standard

hope that helps people. 

Adam

Ha! I never even realised that the 1520 had a microphone! It won't be much use to me, but I'll see if I can dig out a solution, just for the sake of having a fully functioning system!

Post back if you have any success yourself!

---

### Post by odin1965 on 2007-10-08
So... Have the Intel 3945 wifi issues been fixed in 7.10 beta? It's still a major cramp in my enjoyment of my 1520 with Feisty. I know some had no issues with the 3945 under Feisty, but has anyone who DID NOT have wifi under 7.04, got it now that they are using 7.10 beta? I'm just curious, I guess, I'll probably still wait for final as we are super busy at work right now and I don't have time to play with it.

---

### Post by kirkquitar on 2007-10-09
> **CAD-MAN said:**
> You should have no problems installing Gutsy. I installed it on my 1520 (very similar to the 1720), using the graphical user interface - there was no need to use the alternate CD.

If you have sound issues (as I did), then you could try following the link that I posted in a previous post - worked for me :)


Thanks CAD-MAN, I'll try it out when it comes, did you use the 64 bit or 32 bit version?

---

### Post by Juanete on 2007-10-09
Hi there! I'm back from death, at least for a while...

Yesterday I found a SIM card reader behind the battery, do you guys have it too? I didn't ask for it but I bet I could take advantage of it, in the BIOS I have an option to turn "Internal Cellular" on and off but I still couldn't get it to work, do you guys have it too?. Any ideas?

Bye!

PD: Did any of you fix the whole headphones-speakers issue? (maybe on Gutsy?)

---

### Post by b4d on 2007-10-09
Hi all, great tutorial, despite being sceptical about ubuntu, I gave it a try and i am pleased, working through tutorial, everything works great, except again headphones do not mute my speakers and that's annoying, but I'm trying to hack my way out of here. Take care...

---

### Post by odin1965 on 2007-10-09
I just booted the live desktop CD of 7.10 and, as reported by others, wireless is now working, at least on my WPA work network. A pleasant surprise that the live CD booted and X came right up. So far, am only missing sound. It's  great to have my wifi back.

---

### Post by arachnegl on 2007-10-09
Hi all

I bought a 1520 . (Only 32bit version and not 64bit installed)

7.04 installed fine and sound worked by itself. However the DVD drive. Had to alter a few Nvidia X-server things but all very noobie.

went over to beta of Gutsy and everything worked fine apart from the sound.

I stumbled upon this thread and I have tried Cad man's and linux dragon's advice. Neither works unfortunately.

when I try to detect my sound card at command line I get nothing exists. However in my hardware list I do get '82801H (ICH8 Family) HD Audio Controller' manufactured by Intel

Now I am not sure if this is supported by ALSA as I can't find ICH8 in the matrix (only up till 6).

Has anyone got any ideas?

---

### Post by adwatkin19 on 2007-10-10
> **arachnegl said:**
> Hi all

I bought a 1520 . (Only 32bit version and not 64bit installed)

7.04 installed fine and sound worked by itself. However the DVD drive. Had to alter a few Nvidia X-server things but all very noobie.

went over to beta of Gutsy and everything worked fine apart from the sound.

I stumbled upon this thread and I have tried Cad man's and linux dragon's advice. Neither works unfortunately.

when I try to detect my sound card at command line I get nothing exists. However in my hardware list I do get '82801H (ICH8 Family) HD Audio Controller' manufactured by Intel

Now I am not sure if this is supported by ALSA as I can't find ICH8 in the matrix (only up till 6).

Has anyone got any ideas?


I followed CADMAN's idea about compiling own drivers, but i had to use the release candidate versions from the ALSA website, and it all works now

---

### Post by adwatkin19 on 2007-10-10
i can confirm that if you compile the drivers from the ALSA website, the release candidate ones (tested on gutsy only), when you plug the earphones in they do mute the speakers. 

Also i have the sim card section behind my battery and the internal celluar in the bios settings, but have not tried to do anything with it.

---

### Post by CAD-MAN on 2007-10-10
> **kirkquitar said:**
> Thanks CAD-MAN, I'll try it out when it comes, did you use the 64 bit or 32 bit version?

I used the 32-bit version. Apparently you get some compatibility issues with the 64-bit version, and the performance boost offered by 64 bit isn't fantastic anyway.

> **arachnegl said:**
> Hi all

I bought a 1520 . (Only 32bit version and not 64bit installed)

7.04 installed fine and sound worked by itself. However the DVD drive. Had to alter a few Nvidia X-server things but all very noobie.

went over to beta of Gutsy and everything worked fine apart from the sound.

I stumbled upon this thread and I have tried Cad man's and linux dragon's advice. Neither works unfortunately.

when I try to detect my sound card at command line I get nothing exists. However in my hardware list I do get '82801H (ICH8 Family) HD Audio Controller' manufactured by Intel

Now I am not sure if this is supported by ALSA as I can't find ICH8 in the matrix (only up till 6).

Has anyone got any ideas?

Thats strange, its the same sound card that I have. Do you definitely have the latest version of ALSA? (Found [here]("http://www.alsa-project.org/main/index.php/Main_Page") under 'current versions').

["]This]("[URL="https://help.ubuntu.com/community/HdaIntelSoundHowto"[/URL) is the tutorial I followed, and all I had to do was download and compile the latest version of ALSA, whilst specifying my sound card. Rebooted and all worked smoothly.

I don't know what to suggest if that doesn't work for you. :(

P.S. I don't know about headphone issues, I've not used them!

---

### Post by omne on 2007-10-11
Hello,

Compiling alsa used to solve my sound issue, but since two days, I can’t have it to work.
Do you add something in /etc/modprobe/alsa-base ? I tried with and without the option line with no effect.
I compiled the alsa 1.0.15-rc3 is it the same as you ?

Regards,
Omne.

---

### Post by adwatkin19 on 2007-10-11
> **omne said:**
> Hello,

Compiling alsa used to solve my sound issue, but since two days, I can&#8217;t have it to work.
Do you add something in /etc/modprobe/alsa-base ? I tried with and without the option line with no effect.
I compiled the alsa 1.0.15-rc3 is it the same as you ?

Regards,
Omne.

I used the same one as you, but followed the exact link that CADMAN posted to follow, it worked spot on for me, when i downloaded the new kernal update i recompiled the drivers and got sound back again in just minutes. 

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

thats the link to it, i followed to the end of compiling the drivers and installing all three of them. then went no further. This worked. 

Adam

---

### Post by arachnegl on 2007-10-12
Hi there,

Thanks for your suggestions. I did exactly what you suggested and still no sound. I am very confused as it does seem that we are using the same pc more or less.

There is improvement as the pc now recognises the sound card. But JACK invariably comes up with device HW:0 already in use. and there is no sound on boot up nor during video playback. so that suggests that OSS and/or ESD aren't running.

The only thing that I can ask is did you put:
[INDENT][INDENT][INDENT]options snd-hda-intel model=dell-m44[/INDENT][/INDENT][/INDENT]
in alsa-base??

---

### Post by adwatkin19 on 2007-10-12
> **arachnegl said:**
> Hi there,

Thanks for your suggestions. I did exactly what you suggested and still no sound. I am very confused as it does seem that we are using the same pc more or less.

There is improvement as the pc now recognises the sound card. But JACK invariably comes up with device HW:0 already in use. and there is no sound on boot up nor during video playback. so that suggests that OSS and/or ESD aren't running.

The only thing that I can ask is did you put:
[INDENT][INDENT][INDENT]options snd-hda-intel model=dell-m44[/INDENT][/INDENT][/INDENT]
in alsa-base??

When i compiled the alsa-driver, at the sudo ./configure stage i just put in:

sudo ./configure --with-cards=hda-intel

and just left it like that. in terms of jack, i dont have much experience, so im not sure about that error, i just stick with alsa. 

something else you could look at is right clicking the sound icon near the clock and choosing preferences: and then select the audio system you want, i have just left this as ALSA as i know it works and i am happy with the sound i have. 

sorry i cant be much more help. 

Adam

---

### Post by arachnegl on 2007-10-12
Actually sound does work! 

But I think the ALSA settings are all wrong. For example I can hear certain tracks when I play a DVD: the background music but not the speaking. This makes sense as the two are separated so that different language tracks can be created, but how do I check that polyphony is working? How can I trace what inputs are being used?

I really need JACK to work as I use my computer to make music. JACK rests ontop of ALSA so it isn't an alternative. It handles the communication (audio lines and midi) between the different music softs.

I think that I will do a fresh install when Gutsy stable comes out and hope that that will deal with it. I feel defeated by ALSA though and my limited knowledge of linux sound. I wish there was some sort of resorce that was user-friendly.

Thanks for your help though!!

---

### Post by omne on 2007-10-12
Still nothing here&#8230;
« The sound controleur can&#8217;t find anything to control »
The card is in lspci
Have you see this : 
[https://bugs.launchpad.net/dell/+bug/138070](https://bugs.launchpad.net/dell/+bug/138070)

alsactrl find a card but can&#8217;t made it run.

Omne.

---

### Post by arachnegl on 2007-10-12
hmmm Ive got JACK working and midi so I am happy... still don't understand the DVD issue with only one track playing not two + ... Well at least it will shut me up and stop my whineing. ;)

Thanks

---

### Post by unattached on 2007-10-14
looking forward to gutsy in a few days..

therefore a few questions on dell media direct:

does media direct need a windows partition to work or will it still be able to play dvds for instance without windows partition?

someone posted earlier it would be a problem to remove the media direct partition completely because pressing the media direct button on the laptop could then harm the actual system partition. can anyone confirm this or post their experiences?

thanks

---

### Post by CAD-MAN on 2007-10-14
> **unattached said:**
> looking forward to gutsy in a few days..

therefore a few questions on dell media direct:

does media direct need a windows partition to work or will it still be able to play dvds for instance without windows partition?

someone posted earlier it would be a problem to remove the media direct partition completely because pressing the media direct button on the laptop could then harm the actual system partition. can anyone confirm this or post their experiences?

thanks

I deleted media direct - I'll just be careful to never press the button again! Last time I pressed it it screwed me about completely -  whenever i turned my computer on (with the normal button), it booted into media direct. So I booted a Gparted CD, and simply deleted media direct!

I remember reading somewhere that you can configure the button to boot, say Ubuntu automatically, can't remember where I read it though :(

---

### Post by b4d on 2007-10-14
I formatted everything, but when I press the media direct to boot, i get i think grub error 17 next time I try to boot with power button. Then I turn my laptopt off, and boot again with media direct button, and it works normally again, so pressing the power button will again boot without any problems. Nice boot protection :)

---

### Post by adwatkin19 on 2007-10-16
Can anyone tell me how to get the multimedia buttons on the front of my laptop to work, The volume ones already work, but i would like the play/pause, fwd, rwd, and stop buttons to work. 

Any ideas?

---

### Post by chess360 on 2007-10-16
For your information, I ran Fedora 8 Test 3 (Fedora 7.92) from the Live CD. The sound card worked well. When I plugged in the headphone, the speakers muted.

Hopefully, the official release of Gusty Gibbon will solve the sound problem.

There is one more day to go.

---

### Post by b4d on 2007-10-17
About multimedia buttons, in gnome it worked out of the box, but for fluxbox I've managed to fix them with keytouch app. It's preety straightforward to edit them with it. If you have any questions about it, just ask.

---

### Post by linux23dragon on 2007-10-18
Lots of work has been done with the Intel HDA sound card drivers and codecs with Alsa-1.0.15.

I have written a [[COLOR="Blue"]*_howto_*[/COLOR]]("http://ubuntuforums.org/showthread.php?p=3557036#post3557036"), if you want to try it out on your systems.

It should fix the headphone issues and might give you more PCM devices too.

Support for gusty(in regards to the Alsa howto) is coming soon.  

There is already a post on Gusty support for the Dell Inspiron 1520 [[COLOR="Blue"]_*here*_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=577469&highlight=dell+1520") 

Enjoy :-)

---

### Post by fredronn on 2007-10-18
Just installed Gutsy.

I'm a bit disappointed really. Sound doesn't work, which is strange considering alsa supports the card, and a recompile fixes sound. Suspend doesn't work either, yet it worked fine a few kernels ago. What's changed? I'm really genuinely wondering why suspend was broken. Without suspend I might as well just not have a laptop.

---

### Post by toorima on 2007-10-18
Anyone got the internal card reader to work? Nothing happens when I try it, nothing shows up in dmesg or anything. 
I'm on a Vostro 1500 running gutsy.

---

### Post by Rosaline on 2007-10-18
I've just recieved my very own Dell system with mediadirect and all, which I'd like to replace entirely with a minimal Ubuntu install that boots when the mediadirect button is pressed.

From the hints in [this thread I found](http://forum.notebookreview.com/showthread.php?t=49086&page=8) (see post #73 in particular), it certainly looks to be possible, the bootloader does all the real work. Surely someone has given this a go? :P

I'd consider looking into the magics needed  myself, but those who have been to uni will know how crazy the final year can get :S

**Edit:** [And here's a proper explaination](http://ubuntuforums.org/showpost.php?p=2885856&postcount=6) from this very forum! Neptho seems to have figured out how to do this, is there any chance of a more detailed guide? (On re-reading, I think I'm mistaken, Neptho knows how it works, but has not got dual-booting using the two buttons working)

**Edit - promising find:** I might not have time to get up to speed on the internals of Grub, but I can spare an hour for google searches ;) In looking around, I found [this blog post](http://caffeinbar.com/wp/2007/03/08/start-linux-with-dell-mediadirect-button/) which makes it all look very easy indeed if you have mediadirect 3!

---

### Post by CAD-MAN on 2007-10-19
> **toorima said:**
> Anyone got the internal card reader to work? Nothing happens when I try it, nothing shows up in dmesg or anything. 
I'm on a Vostro 1500 running gutsy.

Mine worked out of the box. :-k

---

### Post by adwatkin19 on 2007-10-19
> **CAD-MAN said:**
> Mine worked out of the box. :-k



Yeah mine worked out of the box too, no issues at all

very strange that it doesn't work when everyone else's work, have you checked the card, as some memory card readers don't like certain cards. My old laptop couldn't read memory cards that i bought from play.com, but they worked in other devices like my PDA phone. i would experiment with that, its also now the reason i only buy sandisk because they ALWAYS work. 

Adam

---

### Post by linux23dragon on 2007-10-19
I've updated the Sound card howto to support Gusty.

Please help test [here]("http://ubuntuforums.org/showthread.php?t=530374&highlight=intel+hda")

---

### Post by adwatkin19 on 2007-10-19
When i connect my VGA out connector to a projector, the maximum resolution i can obtain is only 640 by 480, but i have been able to get higher resolutions with other laptops and the same projectors, can anyone advise me on how i could solve this?

many thanks

Adam

---

### Post by toorima on 2007-10-19
lspci
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

Do you guys get anything in dmesg when you put a card in the card reader? I get nothing and I can't seem to find the card anywhere either. I only have one card to test with (ms pro from sandis) but will see if I can get another.

---

### Post by DarthTibault on 2007-10-19
> **adwatkin19 said:**
> When i connect my VGA out connector to a projector, the maximum resolution i can obtain is only 640 by 480, but i have been able to get higher resolutions with other laptops and the same projectors, can anyone advise me on how i could solve this?

many thanks

Adam
Upgrade to Gutsy

from the release notes:
> **Dynamic screen configuration**

Several drivers, including ones for ATI, nVidia, and Intel graphics chips now support the X Resize and Rotate Extension (xrandr). This enables dynamic monitor detection, and resizing and rotating of video output, for no-fuss support for projectors and external monitors.

If you have this hardware and used MergedFB / Xinerama previously, you may need to update your X configuration to use this new feature. 

---

### Post by odin1965 on 2007-10-19
> **toorima said:**
> Anyone got the internal card reader to work? Nothing happens when I try it, nothing shows up in dmesg or anything. 
I'm on a Vostro 1500 running gutsy.

card reader worked OOTB for me on my 1520 in both Gutsy and Feisty

---

### Post by amf on 2007-10-21
Hi,
Just for information.
I had sound working with Ubuntu 7.04 in my 1520 by using the 'HD Audio card setup howto'.
On installing Ubuntu 7.10 I completely lost sound with the sound card and the sound driver not recognised.
On doing: sudo apt-get install linux-backports-modules-generic
All sound was restored as it was in 7.04
Could be worth a try before employing more complicated procedures. Hope this helps someone.

---

### Post by toorima on 2007-10-21
Could someone with a working card reader show me their lspci, I just tried it with a gutsy livecd and it still didn't work, just in case it was something with my rc install.

---

### Post by odin1965 on 2007-10-22
> **toorima said:**
> Could someone with a working card reader show me their lspci, I just tried it with a gutsy livecd and it still didn't work, just in case it was something with my rc install.

Here's the pertinent info from lspci -vv

```
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) (prog-if 01)
        Subsystem: Dell Unknown device 01f1
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 22
        Region 0: Memory at fe5fd400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
        Subsystem: Dell Unknown device 01f1
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 4
        Region 0: Memory at fe5fd500 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: Dell Unknown device 01f1
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 4
        Region 0: Memory at fe5fd600 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
        Subsystem: Dell Unknown device 01f1
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 4
        Region 0: Memory at fe5fd700 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
```

---

### Post by Mamsaac on 2007-10-23
I have a serious problem with wireless working.

Whenever I need to assign a new ESSID to my eth1, the computer completely freezes. Before this started, I tried installing ipw2200, for which I had to change the IEEE version too. Any ideas on how to fix it?

---

### Post by toorima on 2007-10-24
> **odin1965 said:**
> Here's the pertinent info from lspci -vv

```
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) (prog-if 01)
        Subsystem: Dell Unknown device 01f1
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 22
        Region 0: Memory at fe5fd400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
        Subsystem: Dell Unknown device 01f1
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 4
        Region 0: Memory at fe5fd500 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: Dell Unknown device 01f1
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 4
        Region 0: Memory at fe5fd600 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
        Subsystem: Dell Unknown device 01f1
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 4
        Region 0: Memory at fe5fd700 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
```

Thanks for posting that, that is pretty much what mine looks like too. So lets hope its the card itself thats not compatible, its not my card so... gonna try and get another card and test with.
```
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) (prog-if 01)
        Subsystem: Dell Unknown device 0228
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 22
        Region 0: Memory at f9bfd400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
        Subsystem: Dell Unknown device 0228
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 4
        Region 0: Memory at f9bfd500 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: Dell Unknown device 0228
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 4
        Region 0: Memory at f9bfd600 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
        Subsystem: Dell Unknown device 0228
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64, Cache Line Size: 64 bytes
        Interrupt: pin B routed to IRQ 4
        Region 0: Memory at f9bfd700 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

```

---

### Post by lefthand on 2007-10-24
I'm having the same issue with my card reader. lspci looks exactly the same but nothing is happening.

I know the cards (memory sticks) and reader work from testing it with my windows partition.

Let me know if you find anything toorima, I'll post if I figure it out too.

---

### Post by Flynsarmy on 2007-10-26
I have a sigmatel 92XX C-Major Audio card in my Dell Inspiron 5200 Laptop. Ubuntu doesn't recognise it and i have no sound. Anyone else having this problem?

---

### Post by DarthTibault on 2007-10-26
> **Flynsarmy said:**
> I have a sigmatel 92XX C-Major Audio card in my Dell Inspiron 5200 Laptop. Ubuntu doesn't recognise it and i have no sound. Anyone else having this problem?

I"m guessing you meant the Inspiron 1520, if so do this to fix it:
```

sudo aptitude install linux-backports-modules-generic

```
Reboot and enjoy the sound :)


Is anyone else experiencing REALLY slow logins? It boots fast, but when you login... it takes ages for the panels and desktop to appear.
Also: the logout sound doesn't work and there's no gnome-splash.

---

### Post by linux23dragon on 2007-10-26
> **DarthTibault said:**
> Is anyone else experiencing REALLY slow logins? It boots fast, but when you login... it takes ages for the panels and desktop to appear.
Also: the logout sound doesn't work and there's no gnome-splash.

I did when I tried to use the same home directory I had with 7.04.  But I now have a different home directory and now is faster at logging in.   But I still don't have the gnome-splash and the logout sound still does not work.  Not sure why (apart from the desktop logging out to fast).


Oh, by the way.  If any one is suffering from slow WiFi, internet or network (with Ubuntu-7.10). Then this [***[COLOR="Blue"]solution[/COLOR]***]("http://ubuntuforums.org/showthread.php?p=3627847#post3627847") should work ok for you (as it did for me).  Thats if you haven't done so already.

---

### Post by linux23dragon on 2007-10-27
Ive posted a [***_[COLOR="Blue"]Web cam upgrade[/COLOR]_***]("http://ubuntuforums.org/showthread.php?p=3642769#post3642769") Thread (for Gutsy or Ubuntu-7.04), if anyone is interested.  

EDIT: - Note that the web cam should work by default in Gutsy anyway.  You may need to play around with the brightness controller.

---

### Post by sinabala on 2007-11-12
Hi,

           I had a look at the posts here, couldn't find anything as a solution for my problem.

         When I want to Install Ubuntu 7.04 on my Inspiron 1520 (including Vista Home Premium), when I select "Install Ubuntu" after a few seconds the message below appears and installation process stops:


[B]BusyBox v1.1.3 (Debian 1:1.1.3-3 ubuntu3)  Built-in shell (ash)
Enter 'help' for a list of built-in commands
[/B]

[B][COLOR="Red"]/bin/sh: can't access tty;   job control turned off
(initramfs)
[/COLOR][/B]    
   

What's the solution ?](*,)

---

### Post by DarthTibault on 2007-11-12
> **sinabala said:**
> Hi,

           I had a look at the posts here, couldn't find anything as a solution for my problem.

         When I want to Install Ubuntu 7.04 on my Inspiron 1520 (including Vista Home Premium), when I select "Install Ubuntu" after a few seconds the message below appears and installation process stops:


[B]BusyBox v1.1.3 (Debian 1:1.1.3-3 ubuntu3)  Built-in shell (ash)
Enter 'help' for a list of built-in commands
[/B]

[B][COLOR="Red"]/bin/sh: can't access tty;   job control turned off
(initramfs)
[/COLOR][/B]    
   

What's the solution ?](*,)

Are you sure you looked at the posts? This was the problem that started this thread :P
Why are you installing Feisty btw? Gutsy works a lot better...
Anyhow: start in safe graphics mode, and when the error appears type "modprobe piix" and hit <enter>. Wait for it to finish and type "exit".
Still, I recommend you use Gutsy on the 1520...

---

### Post by odin1965 on 2007-11-12
I just thought I'd post an update on my 1520 since I upgraded to Gutsy. I've been so busy at work that I only had time to try a few things from this thread but they all worked. My sound, including muting the speakers with headphones, now works thanks to this thread. And, oh joy oh bliss, my wireless has been working flawlessly for a week and a half.

When i tried the gutsy live CD my wireless worked, but when I installed it, I was back to no wireless. Plus, NM would frequently lock up when trying to connect. Then I discivered that if I could force it to lock, then log out and back in, it could not detect any network devices at all. BUT, the really weird part. When I restarted, I had wireless. This trick worked every time.

I did this for a few days and tried blacklisting IPV6 and my wireless now works fine. I have no idea if it was something I did or, more likely, an update to NM or something. 

Everything else seems to work, but I haven't had a chance to try Compiz or beryl yet. I'veheard a few rumors that there are problems with the Intel cards.

---

### Post by adromidon on 2007-11-12
> **odin1965 said:**
> I just thought I'd post an update on my 1520 since I upgraded to Gutsy. I've been so busy at work that I only had time to try a few things from this thread but they all worked. My sound, including muting the speakers with headphones, now works thanks to this thread. And, oh joy oh bliss, my wireless has been working flawlessly for a week and a half.

When i tried the gutsy live CD my wireless worked, but when I installed it, I was back to no wireless. Plus, NM would frequently lock up when trying to connect. Then I discivered that if I could force it to lock, then log out and back in, it could not detect any network devices at all. BUT, the really weird part. When I restarted, I had wireless. This trick worked every time.

I did this for a few days and tried blacklisting IPV6 and my wireless now works fine. I have no idea if it was something I did or, more likely, an update to NM or something. 

Everything else seems to work, but I haven't had a chance to try Compiz or beryl yet. I'veheard a few rumors that there are problems with the Intel cards.
My 1520 installs without a hitch using gutsy and no tweaking was neccessary all I did was run the updater after install restart and then it just worked :) Good work Ubuntu on the latest release!

---

### Post by linux23dragon on 2007-11-17
> **odin1965 said:**
> 
When i tried the gutsy live CD my wireless worked, but when I installed it, I was back to no wireless. Plus, NM would frequently lock up when trying to connect. Then I discivered that if I could force it to lock, then log out and back in, it could not detect any network devices at all. BUT, the really weird part. When I restarted, I had wireless. This trick worked every time.

I did this for a few days and tried blacklisting IPV6 and my wireless now works fine. I have no idea if it was something I did or, more likely, an update to NM or something..



I've been havening issues with WiFi myself with my sisters boyfriends Dell 1520, after I upgraded to Gutsy.
I'm now going to try this [*_[COLOR="Teal"]driver swap around[/COLOR]_*]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/144501/comments/17").  It looks easy enough.

UPDATE:  Well the good news is that the driver swap works (apart form the ieee80211_crypt in use issue), but I'm still yet to test if it will work every time I turn on the Notebook.

---

### Post by linux23dragon on 2007-11-18
If you chose to use Envy in Gutsy then I recommend using the 32bit of Gutsy.
If you have an ATI card then only use 32bit Gutsy and make sure you only use the generic kernel because the linux-rt kernel won't work at the moment.

Also note that installing ubuntustudio packages will install the linux-rt kernel.  This is bad for ATI users but is O.K. for Nvidia users at the moment.

64bit gutsy is just to hard to setup and work with, on any Dell Notebook.

I have no idea about Intel users at all, apart from the warnings from odin1965 and others.

Anyone had any luck with Intel graphics?

---

### Post by odin1965 on 2007-11-20
> **linux23dragon said:**
> 

I have no idea about Intel users at all, apart from the warnings from odin1965 and others.

Anyone had any luck with Intel graphics?

I'm running the 32 bit and the Intel graphics didn't need any tweaking and I had 1280x800 by default, which is what I want. 1440x900, though, is not available out of the box. I quickly tried desktop effects and it won't work without some tweaking, which I haven't had time to do yet. Beryl worked great on my 1520 with 7.04.

---

### Post by linux23dragon on 2007-11-22
> **linux23dragon said:**
> I've been havening issues with WiFi myself with my sisters boyfriends Dell 1520, after I upgraded to Gutsy.
I'm now going to try this [*_[COLOR="Teal"]driver swap around[/COLOR]_*]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/144501/comments/17").  It looks easy enough.

UPDATE:  Well the good news is that the driver swap works (apart form the ieee80211_crypt in use issue), but I'm still yet to test if it will work every time I turn on the Notebook.

Will it does not work, if you reboot the Notebook.  In fact, I think you still might need the "mac80211" kernel module running.

I'll wait for the next kernel update before I'll continue on with this idea.

---

### Post by pacut on 2007-11-23
For those you might be interested on: modem works 100% with 7.04 and KPPP

Do you think it would work even under Gutsy ?
Ciao !

---

### Post by verbero on 2007-11-25
I'll admit to not having read the 50 pages of this thread, so flame away if its already been said, but can I get a confirmation that an Ubuntu 7.10 install over Windows on a Dell 1520 will have *everything* working ? Or are there still issues with the nvidia 8600 ? 

As soon as I get a couple of +ve replies the beast will be ordered.

---

### Post by linux23dragon on 2007-11-25
> **verbero said:**
> I'll admit to not having read the 50 pages of this thread, so flame away if its already been said, but can I get a confirmation that an Ubuntu 7.10 install over Windows on a Dell 1520 will have *everything* working ? Or are there still issues with the nvidia 8600 ? 

As soon as I get a couple of +ve replies the beast will be ordered.

Gusty 32bit is the way to go.
Intel IPW3945ABG pro WiFi works ok, and the drivers are getting better.  You might have WiFi connection issues with the 3945ABG pro (for now).  Nvidia 8600 is a good choice.

Anyone have anything to say about other hardware configurations with the 1520?

---

### Post by frogface on 2007-11-29
> **dumbmatter said:**
> Yes, it might be very bad for the drive.  I'm no expert, but when I was investigating the same problem, some people were saying that it might result in the drive wearing out in about a year.

I fixed it with this command:

sudo hdparm -B 254 /dev/sda

If that fixes it, you can edit /etc/hdparm.conf to have it automatically set the -B parameter.  Or just put that command in your /etc/rc.local file.

To check on the problem, you can run this command:
sudo smartctl -d ata -a /dev/sda
and find the RAW_VALUE for Load_Cycle_count.  I remember finding somewhere that it was supposed to be able to handle... something in the hundreds of thousands, or maybe millions.  I forget.

Does anyone know, for a Dell Inspiron 1520, if it is appropriate to change hdparm like this in order to fix the bug [https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)

When I'm using my machine calculate the LOAD CYCLE COUNT on my machine it reports a healthy ~14 cycles/hr but when I just sit there and monitor it using sudo smartctl -a /dev/sda | grep Load_Cycle_Count I get the general impression that it's increasing at a rate of 100's per hour? (question: I dual boot with Windows - does smartctl add in the time I spent in Vista to it's figures - ie. does it physically poll the drive?)

I have looked at this fix [http://ubuntuforums.org/showpost.php?p=3675960&postcount=26](http://ubuntuforums.org/showpost.php?p=3675960&postcount=26) and am tempted to implement it. However, I'm also concerned about HD temperature and what these changes might do. Can someone advise what's the correct solution?

Any help greatly appreciated,
FF

---

### Post by tedk89 on 2008-01-02
First I gotta say thanks because I am a linux newb and your guide helped me setup my fancy laptop :) but I have a question, I know that this laptop has several I believe four temperature sensors hd, cpu1, cpu2, and video card for nvidia 8600m gt.... I have been running my computer pretty hard and its been getting very hot.. Just wondering if you know how I can get the values from these temperature sensors to make sure I am not killing anything.

---

### Post by linux23dragon on 2008-01-05
> **tedk89 said:**
> First I gotta say thanks because I am a linux newb and your guide helped me setup my fancy laptop :) but I have a question, I know that this laptop has several I believe four temperature sensors hd, cpu1, cpu2, and video card for nvidia 8600m gt.... I have been running my computer pretty hard and its been getting very hot.. Just wondering if you know how I can get the values from these temperature sensors to make sure I am not killing anything.

Hi tedk89

There seems to be GUI tools around for system temperatures found at gnome-look.org

Have a look [***_[COLOR="Blue"]here[/COLOR]_***]("http://www.gnome-look.org/index.php?xcontentmode=165")

---

### Post by toorima on 2008-01-05
gkrellm is another good option, shows gpu, cpu and hdd temp among other things

---

### Post by solamanda on 2008-01-07
Hi all, I've been running ubuntu for the last few months with much success on my desktop.  I'm about to order a new laptop but would like some reassurance.

I'm going to order a 1520 with a T7250 and Intel X3100 graphics running Windows XP SP2.  I want to run it dual booting, is this all going to work? (minus the 56k Modem issue)

Many thanks!

---

### Post by linux23dragon on 2008-01-11
> **linux23dragon said:**
> I've been havening issues with WiFi myself with my sisters boyfriends Dell 1520, after I upgraded to Gutsy.
I'm now going to try this [*_[COLOR="Teal"]driver swap around[/COLOR]_*]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/144501/comments/17").  It looks easy enough.

UPDATE:  Well the good news is that the driver swap works (apart form the ieee80211_crypt in use issue), but I'm still yet to test if it will work every time I turn on the Notebook.

OK. 
Dell is now supporting the new driver option.  So Its worth trying the idea out.
You will find the information about it on the Dell Wiki  support  [***_[COLOR="Blue"]here[/COLOR]_***]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues ")

Please report if the WiFi driver swap works O.K or not for you.

---

### Post by DarthTibault on 2008-01-11
> **linux23dragon said:**
> OK. 
Dell is now supporting the new driver option.  So Its worth trying the idea out.
You will find the information about it on the Dell Wiki  support  [***_[COLOR="Blue"]here[/COLOR]_***]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/ipw3945_Wireless_Network_Module_Issues ")

Please report if the WiFi driver swap works O.K or not for you.
Ah yes, I did that as well: before my wifi connection would just drop and make my whole system hang... really annoying. The fix Dell suggests is real easy, and so far everything has been working perfectly.
However: loading the new driver will bring a (small) issue with it: at some point it fails (though you won't notice it) and your card will be called "wifi0_rename". Don't get me wrong: everything still works, it's just that the silly name bothers me.
Here's how you fix it (also very easy):
```
sudo nano /etc/udev/rules.d/70-persistent-net.rules

```
The bottem line should be something like:
```
# PCI device 0x8086:0x4222 (ipw3945)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:1b:77:c7:9a:27", NAME="eth$"
```
which, as you can see, still belongs to the ipw3945 driver. Remove that line, save and exit.
Now run:
```
sudo rmmod iwl3945
sudo modprobe iwl3945

```
And you're done! The rules file should contain the right line now (you can check if you want).
It may be coincidence, but this seems to fix the problem I had with the driver not working after a suspend as well. (You can find the fix to make suspend work on the Dell wiki as well).

---

### Post by lefthand on 2008-01-11
That is an easy fix. Working perfectly for me so far. I was getting really fed up with all the freezes. 

My little blue wifi light doesn't light up at all anymore, I'm sure there is a simple way to fix it, but I don't care enough to look into it. If you'd rather have a flashing light than a stable system you may not want to use this fix :)

thanks linux23dragon for posting this.

---

### Post by b4d on 2008-01-16
```
sudo smartctl -a /dev/sda | more                                                                                                                  
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

Device: ATA      SAMSUNG HM160HI  Version: HH10
Serial number:       S14QJD0P919303
Device type: disk
Local Time is: Wed Jan 16 06:22:42 2008 CET
Device does not support SMART

Error Counter logging not supported

[GLTSD (Global Logging Target Save Disable) set. Enable Save with '-S on']
Device does not support Self Test logging

```

Is this normal and how should i see my Load_Cycle_Count? ty

---

### Post by Altimar on 2008-01-24
If you use /dev/sda it assumes it's a SCSI disk. You have to tell it it's not. Try:

```
sudo smartctl -a **-d ata **/dev/sda
```

---

### Post by solamanda on 2008-01-24
I have installed using 7.10 standard CD fine but sound doesn't work.  I tried following the instructions on the first page but I don't seem to have Alsa system installed?  What do I do now?

Thanks

---

### Post by Altimar on 2008-01-25
Try the instructions in this thread:
[http://ubuntuforums.org/showthread.php?t=607378&highlight=1520+gutsy]("http://ubuntuforums.org/showthread.php?t=607378&highlight=1520+gutsy")

or this one:
[http://ubuntuforums.org/showthread.php?t=625316&highlight=1520+gutsy]("http://ubuntuforums.org/showthread.php?t=625316&highlight=1520+gutsy")

Please let us know if those help you or not.

---

### Post by hunt.topher on 2008-01-28
linux23dragon,

Thanks for this overview. Yours was the first page I found when trying to set up my Inspiron 1520 with Ubuntu Gutsy and it was very helpful.

However I'll note per your request that the wifi driver fix on your post, using bcm43xx-firmware, did not work for me at all. After about 3 days of playing around I figured out that I needed to use ndiswrapper with the Dell R174291 driver and now my wireless works fine. Since I'm guessing that this post is pretty high profile, I think it would be great if you mention that alternative solution and/or include a link to the Dell wiki where I finally got the wireless to work:
[http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper](http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper)

Thanks for an awesome and comprehensive setup howto!

---

### Post by linux23dragon on 2008-01-29
> **hunt.topher said:**
> linux23dragon,

Thanks for this overview. Yours was the first page I found when trying to set up my Inspiron 1520 with Ubuntu Gutsy and it was very helpful.

However I'll note per your request that the wifi driver fix on your post, using bcm43xx-firmware, did not work for me at all.
After about 3 days of playing around I figured out that I needed to use ndiswrapper with the Dell R174291 driver and now my wireless works fine. Since I'm guessing that this post is pretty high profile, I think it would be great if you mention that alternative solution and/or include a link to the Dell wiki where I finally got the wireless to work:
[http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper](http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper)

Thanks for an awesome and comprehensive setup howto!

Thanks hunt.topher for your report.

The  *"Dell Inspiron 1520 with Ubuntu-7.04 thread"*  can in (some sections) help configure Ubuntu-7.10.  But a lot of the information is no longer needed (or is outdated) for Ubuntu-7.10.

But there is configuration information I can write up for Ubuntu-7.10 that includes setting up bluetooth, WiFi, HDA sound card, Graphics drivers, the touch pad and using the linux-rt kernel with Ubuntustudio.

I could start a different thread.  But I will need the help from yourself and others to give me feedback on your configurations as well.

Should I start another detailed thread for Gutsy?

---

### Post by moopere on 2008-02-17
> **lefthand said:**
> That is an easy fix. Working perfectly for me so far. I was getting really fed up with all the freezes. 

My little blue wifi light doesn't light up at all anymore

I assume this used to work with ndiswrapper?  I've never used the windows drivers and have never -ever- had the little blue wifi light come on under Linux....I would have thought this would be a driver thing so perhaps theres a buglet in the linux version of the driver?  Then again, I don't see anyone else complaining about this so maybe its a Dell specific thing.

Cheers,
Craig

---

### Post by DarthTibault on 2008-02-17
> **moopere said:**
> I assume this used to work with ndiswrapper?  I've never used the windows drivers and have never -ever- had the little blue wifi light come on under Linux....I would have thought this would be a driver thing so perhaps theres a buglet in the linux version of the driver?  Then again, I don't see anyone else complaining about this so maybe its a Dell specific thing.

Cheers,
Craig
No, we were talking about the ipw3945 module, which is a very buggy driver that would make the entire system hang quite frequently. We replaced it with the iwl3945 module. The iwl driver included in Gutsy apparently doesn't support the blinking light on the Inspiron. You don't see many people complaining about it because a) people don't really care about a blinking light and b) most people probably still use ipw3945. :)

---

### Post by lefthand on 2008-02-17
After using the iwl3945 for a while, I found that it wasn't really all that much better. I still was freezing up a lot. Finally last week after one of the kernal updates is broke completely. So I did what any sensible linux user would do, I upgraded to the latest alpha of hardy. It's been working beautiful for me since then. No more freezing and I"m getting decent speeds. Still no light but, meh.

---

### Post by DarthTibault on 2008-02-17
> **lefthand said:**
> After using the iwl3945 for a while, I found that it wasn't really all that much better. I still was freezing up a lot. Finally last week after one of the kernal updates is broke completely. So I did what any sensible linux user would do, I upgraded to the latest alpha of hardy. It's been working beautiful for me since then. No more freezing and I"m getting decent speeds. Still no light but, meh.
Are you sure you replaced it correctly? I haven't had a single lockup with iwl.

---

### Post by lefthand on 2008-02-17
> **DarthTibault said:**
> Are you sure you replaced it correctly? I haven't had a single lockup with iwl.

I'm pretty sure, I was getting the correct output when I ran ```
lsmod | egrep 'Module|iwl|ipw'
```

There may have been something else causing the lockups though. Either way, I'm happy with hardy right now, it's shaping up to be a solid release.

---

### Post by linux23dragon on 2008-02-18
> **lefthand said:**
> I'm pretty sure, I was getting the correct output when I ran ```
lsmod | egrep 'Module|iwl|ipw'
```

There may have been something else causing the lockups though. Either way, I'm happy with hardy right now, it's shaping up to be a solid release.

Hi lefthand 

I'm happy someone is trying out Hardy.

Does the audio issues we have had with Gutsy gone, and do we need to bother about the IPv6/IPv4 setup?

Apart from the Codecs, do DVD's play out of the box without any encryption tweaks (libdvdcss2) ?

Does bluetooth work OK with any device (like the mobile phone), without the need for general configuration?

Is the X server going to work correctly out of the box?
 
Are you using a 64bit or 32bit Hardy system?


Sorry about the questions but I'm hopping things are getting  a lot better (compared to what I've seen in the past).

Thanks

---

### Post by lefthand on 2008-02-18
I'm running 32bit and I took the upgrade path instead of a clean install.

Audio worked fine, I tried it off the live cd and it worked there as well, so I assume that issue is over. 

I've only tried one DVD and that crashed totem, but I haven't looked into that yet.

I haven't tried bluetooth, since I don't have any bluetooth devices. 

Bootup is pretty slow still. It seems like it's hanging, but they keeps going. Booting down is very very fast, maybe 15 seconds from when I click the button to when it's off.

Compiz worked by default, but seems a little choppy, I'm sure there's a setting I can flip to help this but I haven't looked into it since it's not too bad.

All in all I'm very happy with it, I can't wait till the next alpha this thursday.

---

### Post by monkeyBox on 2008-03-03
> **Shaidtan said:**
> 
Wireless:
I have the BCM43xx card. The in kernel driver works in both the 2.6.22 and 2.6.23 kernels. I use wpa_supplicant and wpa2 encryption works well.

I have the BCM4310..   Will the kernel drivers work w/ my card?  (ndiswrapper is sucking big-time.)

---

### Post by alxhastngs on 2008-04-28
New Ubuntu user here running 32 bit Hardy off of Wubi (dual boot vista install).


Xserver worked out of the box for me.

Had some issues with it crashing at first, but updating to the newest nvidia drivers (8400M in my 1520) seemed to fix it.  Now its just a little choppy.

Wireless worked fine.

Audio works fine.

Multimedia keys not working.

Havn't tried a DVD yet, and I have no blue tooth devices.

Has anyone been able to get the multimedia keys working in hardy?  Volume control gives me the graphic update for it, but it doesn't change the volume.

---

