---
title: "Ubuntu on MacBook Pro"
date: 2006-06-17
forum: Hardware &amp; Laptops
---

### Post by phico on 2006-06-17
**MacBook Pro 4 (Penryn) Ubuntu [COLOR="Red"]Single boot[/COLOR]**

-------------------------------------------
This thread was dedicated to first MacBook pro generation .. you can still find information about MBP 1 here bellow (post #5)
now it is has been updated to [COLOR="Red"]ubuntu single boot on MacBook Pro 4 generation (Penryn)[/COLOR] 
(you can run other OS in VMware and boot MacOs on external usb as explained hereafter..)
-------------------------------------------

**[COLOR="Blue"]Install Backup MacOS USB disk[/COLOR]**
You need a backup MacOS at least for firmware update.
- Boot on MacOS installation CD holding "C" key
- Plug the USB disk
- Install MacOS on the USB disk

**[COLOR="Blue"]Partition the main disk[/COLOR]**
- unplug the USB disk
- Boot on MacOS installation CD 
- Open terminal application
- Partition the main disk as this : 
```
diskutil partitionDisk disk0  HFS+ refit 20M Linux linux 100%
```
(efi is going to boot on our small 20M partition where we are
going to install refit. )
- quit the terminal
- plug the usb disk
- open the startup disk utility
- select your usb disk 
- restart

(if your system does not boot on macos usb see troubleshooting below :
try the following :
try 1 : ALT choose boot disk
try 2 : ALT+CMD+P+R then try to boot
try 3 : Remove USB HD and boot holding C key. 
        Open startup disk utility
        Plug USB disk
        Select USB disk
        Restart)


**[COLOR="Blue"]Install refit[/COLOR]**
- download refit image and mount it (refit.sf.net)
- copy efi folder from the refit image to the refit partition
- open terminal application and run enable-always.sh (from the refit partition)

**[COLOR="Blue"]Install ubuntu[/COLOR]**
- Unplug USB disk
- Boot with ubuntu CD  (32 or 64bit)
- refit shoud show linux cd option
- run installation
- make manual partition :
  -> ext3 mounted on / (All free)
  -> swap (between 4-8GB)
- reboot
- run partition tool in refit menu

**[COLOR="Blue"]Ubuntu configuration[/COLOR]**
- At first boot Ubuntu should propose updates
- Install all updates and Nvidia video drivers 

- **Video** : works out of the box

- **Sound** : 
  ```
sudo gedit /etc/modprobe.d/options
```
   - add this line
  ```
options snd_hda_intel model=mbp3
```
   - reboot
   - double click volume icon
   - enable "pcm" and "front" in preferences and unmute them
   - right click volume icon, select PCM

- **Wifi** :
    ```
sudo apt-get install unrar
     sudo apt-get install ndiswrapper-common
     sudo apt-get install ndiswrapper-utils-1.9
```
    - put MacOS installation disk in CD

    ```
cp /media/cdrom/boot\ camp/drivers/broadcom/broadcomxpinstaller.exe .
     unrar -e broadcomxpinstaller.exe 
     sudo ndiswrapper -i bcmwl5.inf 
     sudo ndiswrapper -m
     sudo modprobe ndiswrapper
```

     ```
sudo gedit /etc/modules 
```
       - add this line
     ```
ndiswrapper
```

- **Webcam** : work out of the box

- **Touchapd** : if you want multitouch support (two fingers scrolling, right click, ..) 
you can install driver from [http://web.comhem.se/rydberg/Bits/](http://web.comhem.se/rydberg/Bits/) :


```
wget http://web.comhem.se/rydberg/Bits/bcm5974-0.54-src.zip
unzip bcm5974-0.54-src.zip 
cd bcm5974/
make -C /lib/modules/`uname -r`/build M=$PWD modules
sudo cp bcm5974.ko /lib/modules/`uname -r`/kernel/drivers/input/mouse/
sudo ./scripts/bcm5974-post-install
sudo modprobe bcm5974
```

add these lines to source repositories /etc/apt/sources.list

```
deb http://ppa.launchpad.net/mactel-support/ubuntu hardy main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu hardy main
```

install or upgrade xserver-xorg-input-synaptics:
```
apt-get install xserver-xorg-input-synaptics
```

edit /etc/X11/xorg.conf and put one of [http://web.comhem.se/rydberg/Bits/](http://web.comhem.se/rydberg/Bits/) synaptics config

reboot

- **Function keys** : 

install pommed manually because ubuntu package is not compatible with MBP 4th gen

```
wget http://alioth.debian.org/frs/download.php/2465/pommed-1.20.tar.gz
tar xvfz pommed-1.20.tar.gz
cd pommed-1.20/
sudo apt-get install libconfuse-dev  libasound-dev libaudiofile-dev libofapi-dev libdbus-1-dev pciutils-dev
make pommed
sudo cp pommed/pommed /usr/bin
sudo mkdir /usr/share/pommed
sudo cp  pommed/data/* /usr/share/pommed
sudo cp pommed.conf.mactel /etc/pommed.conf
sudo cp pommed.init /etc/init.d/pommed
sudo chmod u+x /etc/init.d/pommed
sudo cp dbus-policy.conf /etc/dbus-1/system.d/pommed.conf
sudo update-rc.d pommed defaults
sudo /etc/init.d/pommed start
```

- **Touchpad** :
If you want to get multitouch support (two finger scrolling, right click ..)
you can install driver from : [http://web.comhem.se/rydberg/Bits/](http://web.comhem.se/rydberg/Bits/)



**[COLOR="Blue"]4Gb RAM support[/COLOR]**
If you get a MBP with 4Gb RAM then go to my dedicated thread to 
use all your RAM on a 32 bit system
[http://ubuntuforums.org/showthread.php?p=5347489#post5347489](http://ubuntuforums.org/showthread.php?p=5347489#post5347489)

**[COLOR="Blue"]Desktop[/COLOR]**
Finally .. find a suitable desktop for such a great OS on a great Machine !

I built mine on the theme : " Tux the pingouin crunched the apple "  ;-)

It is based on [HumanBlue]("http://www.gnome-look.org/content/show.php?content=40670"), [HumanAzul]("http://www.gnome-look.org/content/show.php?content=37099"), [Tux-Mania]("http://www.gnome-look.org/content/show.php?content=15994")  GDM and a [Tux screenshot]("http://www.gnome-look.org/content/show.php?content=26229") comming from
[http://www.gnome-look.org](http://www.gnome-look.org)

To get rid of brown background while starting, change background color in /etc/gdm.conf
( BackgroundColor=#5B5B5B instead of BackgroundColor=#2b0600 )

(See pictures in attachments)



Reference : [https://wiki.ubuntu.com/MacBookPro/Penryn](https://wiki.ubuntu.com/MacBookPro/Penryn)

---

### Post by Wanderer2005 on 2006-06-17
Great post! Just what I needed before buying my Mac!

---

### Post by rapido on 2006-06-18
Thanks for the great thread.  Audio was a big hangup for me.  After updating to 2.6.15-25, I get sound out of the headphone jack only.   But no audio out of the internal speaker(s).

Any ideas?

---

### Post by rapido on 2006-06-19
Could you grep through any sound/alsa settings in /etc/modutils and /etc/modprobe.d to see if there are any snd-hda-intel specific settings?

If you find anything, please copy the contents of the config file into this thread.

It is quite possible that my sound issue is an alsa configuration problem.

---

### Post by phico on 2006-06-19
--------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------

OLD information for MacBook Pro 1

--------------------------------------------------------------------------------------
--------------------------------------------------------------------------------------



**MacBook Pro Linux**
Here is some installation notes .. rather a compilation of what I found on the internet 
+ configuration of french / belgian-fr keyboard
+ a nice desktop theme

Thanks to rapido, gendo, JDR, alexinfurs, msprunck for their 
feedback and contribution and all the people providing 
drivers and/or useful information about Linux on Macbook 
especially Nicolas Boichat and Ronald S. Bultje

For more information :

[http://www.mactel-linux.org/wiki/Main_Page](http://www.mactel-linux.org/wiki/Main_Page)
[http://modular.math.washington.edu/macbook/](http://modular.math.washington.edu/macbook/)
[http://modular.math.washington.edu/macbook/triboot/](http://modular.math.washington.edu/macbook/triboot/)
[http://bin-false.org/?p=17](http://bin-false.org/?p=17)
[http://desrt.mcmaster.ca/macbook.xhtml](http://desrt.mcmaster.ca/macbook.xhtml)
[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp)
[http://www.jasonparekh.com/?page_id=9](http://www.jasonparekh.com/?page_id=9)
[http://www.ethicalhack.org/howto/triple_boot_howto.html](http://www.ethicalhack.org/howto/triple_boot_howto.html)
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
[http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper](http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper)
[http://blogs.gnome.org/portal/rbultje](http://blogs.gnome.org/portal/rbultje)
[http://www.boichat.ch/nicolas/macbook-tools/](http://www.boichat.ch/nicolas/macbook-tools/)
[http://blogs.vislab.usyd.edu.au/index.php/JohnStavrakakis/2006/07/28/triple_boot_on_macbook_pro_15](http://blogs.vislab.usyd.edu.au/index.php/JohnStavrakakis/2006/07/28/triple_boot_on_macbook_pro_15)
[http://www.ubuntuforums.org/showthread.php?t=225621](http://www.ubuntuforums.org/showthread.php?t=225621)
[https://wiki.ubuntu.com/MacBook](https://wiki.ubuntu.com/MacBook)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)


[COLOR="Blue"][B]For triple boot Mac OS X - Linux - Windows, follow
blue instructions.[/B][/COLOR]

**MacOsX Installation**

[LIST=1]
[*]Install MacOsX pro with a minimum of features.  It may be useful for firmware update or hardware check ..
[*]Boot on MacOsX CD holding Alt key
[*]Follow installation instruction.
[/LIST]

**BootMenu installation **

1.Boot on MacOsX
2.Install bootcamp
[COLOR="Blue"]
For triple boot: Burn MacBook Windows CD driver
[/COLOR]
3.Install rEFIt ([http://refit.sf.net](http://refit.sf.net)) 
[LIST]
[*]install mac image
[*]copy efi to root directory (drag efi folder to MacOs disk)
[*]open a mac os terminal (in utilities)
[*]cd /efi/refit
[*]./enable-always.sh
[/LIST]

**Partionning**

In a MacosX terminal, partition the disc :
```
sudo diskutil resizeVolume disk0s2 10G
```
That sets 10G for MacOsX and the rest for Linux


[COLOR="Blue"]
For triple boot:
```
sudo diskutil resizeVolume disk0s2 10G Linux Linux 52G "MS-DOS FAT32" Windows 30G
```

**Install Windows XP SP2**
Boot, in refit, choose the Windows CDRom.
Launch install, at reboot choose the Windows HardDisk.
Install drivers from BootCamp CD drivers.
Follow my howto to customize Mac keyboard on Windows :
[http://discussions.apple.com/thread.jspa?threadID=608584&tstart=0](http://discussions.apple.com/thread.jspa?threadID=608584&tstart=0)
[/COLOR]

**Install Linux Ubuntu**

[LIST]
[*]Boot on Ubuntu drapper live cd

[COLOR="Blue"]
For triple boot, make a swap file because of partion number limit explained
on [http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp)
Open a terminal. (Application>Accessories>Terminal)
> 
sudo su
mkdir /mnt/linux
mount -t ext3 /dev/sda3 /mnt/linux
sudo dd if=/dev/zero of=/mnt/linux/swap bs=1024 count=2097152
mkswap /mnt/linux/swap
swapon /mnt/linux/swap

[/COLOR]

[*]Click install on disk in Ubuntu
[*]Choose a manual partition : (2Gb of swap and the rest for filesystem) 
do not erase efi 200M partition

[*]define mount :
[LIST]
[*]if possible, do not mount /mount/EFI (select white item in list)
[*]/dev/sda3 => swap
[*]/dev/sda4 => /
[/LIST]

[COLOR="Blue"]
For triple boot
[*]define mount :
[LIST]
[*]/dev/sda3 => /
[/LIST]
Triple boot uses a swap file 
[/COLOR]

[*]Grub installation fails at the end, just ignore it (you are going
to install lilo anyway).  (For people who still want to install Grub they can have a look to this page [https://wiki.ubuntu.com/MacBook](https://wiki.ubuntu.com/MacBook))

[*]Open a terminal : Terminal 1 (Application>Accessories>Terminal)
(the following comes from [http://bin-false.org/?p=17](http://bin-false.org/?p=17) )
> sudo su
mkdir /mnt/ubuntu
mount /dev/sda4 /mnt/ubuntu/
mount -t proc none /mnt/ubuntu/proc
mount -o bind /dev /mnt/ubuntu/dev
chroot /mnt/ubuntu /bin/bash
apt-get install lilo lilo-doc

[SIZE="1"](Remark :Some users report problem to find lilo because no network is not
available in the chroot terminal. It is strange it works for most for us.

If you have that problem, the solution is to reactivate the network in the chroot terminal.
Either manually (ifup eth0), with dhclient
or using the graphical config (gksu network-admin).) 
[/SIZE]

[*]create /etc/lilo.conf 
Add this content:
(with "vi" or Application>Accessories>Text Editor)
```
boot=/dev/sda4
default=Linux
map=/boot/map
delay=20
image=/vmlinuz initrd=/initrd.img
root=/dev/sda4
label=Linux
read-only
```

[COLOR="Blue"]
For triple boot use /dev/sda3 instead
```
boot=/dev/sda3
default=Linux
map=/boot/map
delay=20
image=/vmlinuz initrd=/initrd.img
root=/dev/sda3
label=Linux
read-only
``` 
[/COLOR]

[*]Open a second terminal : Terminal 2
```
sudo parted
print
set 4 boot on
quit
```

[COLOR="Blue"]
For triple boot use /dev/sda3 instead
```
sudo parted
print
set 3 boot on
quit
```
[/COLOR]

[*]Go back to Terminal 1
> lilo -b /dev/sda
exit
umount /mnt/ubuntu/proc
umount /mnt/ubuntu/dev
umount /mnt/ubuntu


[COLOR="Blue"]
For triple boot 
> **lilo -P ignore -b /dev/sda3**
exit
umount /mnt/ubuntu/proc
umount /mnt/ubuntu/dev
umount /mnt/ubuntu
[/COLOR]

[*]Reboot
[*]**Go in the rEFIt partition editor and synchronize MBR**
[*]Choose linux in rEFIt menu
[/LIST]

**Ubuntu configuration**

***Update***

Update your system and install restritected drivers
```

sudo apt-get install linux-restricted-modules-2.6.15-26-686 linux-kernel-headers
sudo apt-get dist-upgrade 

```

Relaunch lilo if kernel has changed
[COLOR="Blue"]
For triple boot 
> **lilo -P ignore -b /dev/sda3**[/COLOR]
For dual boot
```

sudo lilo -b /dev/sda

```

Reboot

***Video***

_Install ATI drivers :_
The following was suggested by Gendo and comes from :
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
disable fglrx module : sudo vi  /etc/default/linux-restricted-modules-common
> DISABLED_MODULES="fglrx"

Uncomment the universe and multiverse repositories  in /etc/apt/sources.list

download drivers from ATI web site and follow this install :
```

wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8.27.10-x86.run
sudo apt-get update
sudo apt-get install module-assistant build-essential
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
chmod +x ati-driver-installer-8.27.10-x86.run
./ati-driver-installer-8.27.10-x86.run --buildpkg Ubuntu/dapper
sudo dpkg -i xorg-driver-fglrx_8.27.10-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.27.10-1_i386.deb
sudo dpkg -i fglrx-control_8.27.10-1_i386.deb
sudo rm /usr/src/fglrx-kernel*.deb
sudo module-assistant prepare,update
sudo module-assistant build,install fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

```
reboot and check with : 
```
fglrxinfo
```
you should have :
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1600 Generic
OpenGL version string: 2.0.5879 (8.26.18)
```


_XGL/compiz installation_

If you want to go further and install compiz and XGL
go to that other link :
[http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper](http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper)
(thanks to Gendo for that suggestion)

After XGL compiz installation :

- add the startcompiz script to the session start program (System>Preferences>Sessions | Startup Programs)

- install gset-compiz, gcomizthemer ant themes and discover compiz ...
>  sudo apt-get install gset-compiz gcompizthemer gcompizthemer-themes
 gset-compiz
Configure effects, key shortcuts with gset-compiz
and customize your theme with gcompizthemer

- I also had to add this line to the startcompiz script
```
killall gnome-panel
```

***DVI Output***

- Install ATI drivers as above 
- Install fglrx package with synaptic
- run ATI config (either from ATI menu or sudo aticonfig)
- configure a clone or large desktop 
for example : 
> sudo aticonfig -f --initial=dual-head --screen-layout=right
- restart X (ctrl-alt-backspace)

[I][B]
Audio[/B][/I]
Install latest Ubuntu kernel 2.6.15-26
relaunch lilo and reboot
```
sudo lilo -b /dev/sda
```
You should hear Ubuntu login sound  
(It seems to work only on MBP17" not on MBP15"...
for MBP15" follow the trick given by Gendo here :
[http://www.ubuntuforums.org/showpost.php?p=1269085&postcount=39](http://www.ubuntuforums.org/showpost.php?p=1269085&postcount=39) 
)

Microphone does not work with "sound recorder" application but
It works with skype 1.3 beta for Linux (but not with skype 1.2)

(I also installed latest alsa drivers (1.0.12rc1) following their 
INSTALL file)  You can also follow the excellent thread here :
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

With old drivers and kernel when headset is plugged in jack, you might
 hear the sound in both headset AND speakers ?!

With new alsa drivers (1.0.12rc1) and kernel ( 2.6.15-26-686 ), 
I do not have this problem any more. 

Finally ... sound is working perfectly on MBP17" 

If you have some issues left, you can have a look to this link,
it contains many useful informations that are not here :
[http://www.jasonparekh.com/?page_id=9](http://www.jasonparekh.com/?page_id=9)

***Wireless***
(the following comes from [http://bin-false.org/?p=17](http://bin-false.org/?p=17) )
[LIST]
[*]sudo modprobe new_wlan_scan_sta
[*]sudo apt-get install network-manager network-manager-gnome
[/LIST]
It works out of the box on my MacBook with my hotspot.  Some people seems to have problems with some wifi routers however.

***Screen brightness***

Nicolas Boichat wrote drivers for screen and keyboard backlight.
[http://www.boichat.ch/nicolas/macbook-tools/](http://www.boichat.ch/nicolas/macbook-tools/)

Here is how to install :

```

sudo apt-get install pciutils-dev
wget http://www.boichat.ch/nicolas/macbook-tools/macbook-tools-0.1.1.tar.bz2
tar xvfj macbook-tools-0.1.1.tar.bz2
cd macbook-tools-0.1.1
sudo rm /usr/local/bin/backlight
sudo make install

```

Use : 
backlight +10
backlight -10

To control backlight with key pressed, you can use a program
developed by alexinfurs available here :
[http://ubuntuforums.org/showthread.php?t=215801](http://ubuntuforums.org/showthread.php?t=215801)

```

sudo apt-get install libvte-dev
sudo ln -s /usr/local/bin/backlight /usr/bin/macbook-backlight
tar xvfz macbook-backlight-control-0.2.tar.gz  (get it from the link above)
cd macbook-backlight-control/src
make
./macbook-backlight-control

```

Try :
Ctrl+F1 
Ctrl+F2

Add macbook-bakclight-control to your session start scripts
System>Preference>Session

To get automatic backlight adjustement from sensors, apply
kernel patch developped by Nicolas Boichat

Thank you to msprunck for his feedback

***Keyboard Backlight***

Nicolas Boichat wrote drivers for screen and keyboard backlight.
See :
[http://www.boichat.ch/nicolas/macbook-tools/](http://www.boichat.ch/nicolas/macbook-tools/)

Follow "Screen brightness" installation

./applesmc 255 
to turn light on
sudo ./applesmc 0
to turn light off
./applesmc 
to see sensors values

works on MBP 17

***Keyboard***

**_Method 1 : using Xmodmap_:** 
With this method you need to start xmodmap script when the session start
but it is easier to modify special keys.  

copy the xmodmap to a custom one :
>  sudo cp /usr/share/xmodmap/xmodmap.be /usr/share/xmodmap/xmodmap.mbp.be
edit that file and change special keys definition
Especially to have an "AltGr" key and a "Delete" key ..
I redefined many other keys to have a full feature keyboard.

You can change it yourself :
- to find a keycode : launch xev and hit the key
- to get the command keyword : look at this website :  [http://wiki.linuxquestions.org/wiki/List_of_keysyms](http://wiki.linuxquestions.org/wiki/List_of_keysyms)
(After a keycode, you can put 4 keyword : "normal key keyword" "shift key keyword" "altgr key keyword" "shift algr key keyword"
for example : a A à @)

Then start xmodmap by : 
```
 xmodmap /usr/share/xmodmap/xmodmap.mbp.be
```

Put it somewhere so that it is loaded automatically

Here is my french - belgian/fr xmodmap file :

```
 
clear Mod1
clear Mod2
!
keycode   8 =
keycode   9 = Escape
keycode  10 = ampersand 1 bar brokenbar
keycode  11 = eacute 2 twosuperior onehalf
keycode  12 = quotedbl 3 threesuperior threequarters
keycode  13 = apostrophe 4 braceleft onequarter
keycode  14 = parenleft 5 braceleft
keycode  15 = section 6 asciicircum
keycode  16 = egrave 7
keycode  17 = exclam 8
keycode  18 = ccedilla 9 braceleft
keycode  19 = agrave 0 braceright
keycode  20 = parenright degree braceright
keycode  21 = minus underscore
keycode  22 = BackSpace Delete Delete
keycode  23 = Tab
keycode  24 = a
keycode  25 = z
keycode  26 = e E EuroSign
keycode  27 = r R registered
keycode  28 = t
keycode  29 = y
keycode  30 = u
keycode  31 = i
keycode  32 = o O at
keycode  33 = p
keycode  34 = dead_circumflex dead_diaeresis bracketleft
keycode  35 = dollar asterisk bracketright EuroSign
keycode  36 = Return
keycode  37 = Control_L
keycode  38 = q
keycode  39 = s
keycode  40 = d
keycode  41 = f
keycode  42 = g
keycode  43 = h
keycode  44 = j
keycode  45 = k
keycode  46 = l
keycode  47 = m
keycode  48 = ugrave percent dead_acute
keycode  49 = less greater backslash
!twosuperior threesuperior
keycode  50 = Shift_L
keycode  51 = backslash sterling dead_grave mu
keycode  52 = w
keycode  53 = x
keycode  54 = c C copyright
keycode  55 = v
keycode  56 = b
keycode  57 = n N asciitilde
keycode  58 = comma question dead_cedilla
keycode  59 = semicolon period
keycode  60 = colon slash Multi_key
keycode  61 = equal plus plusminus
keycode  62 = Shift_R
keycode  63 = KP_Multiply
keycode  64 = Alt_L
keycode  65 = space
keycode  66 = Caps_Lock
keycode  67 = F1 F11
keycode  68 = F2 F12
keycode  69 = F3 F13
keycode  70 = F4 F14
keycode  71 = F5 F15
keycode  72 = F6 F16
keycode  73 = F7 F17
keycode  74 = F8 F18
keycode  75 = F9 F19
keycode  76 = F10 F20
keycode  77 = Num_Lock
keycode  78 = Scroll_Lock
keycode  79 = KP_7
keycode  80 = KP_8
keycode  81 = KP_9
keycode  82 = KP_Subtract
keycode  83 = KP_4
keycode  84 = KP_5
keycode  85 = KP_6
keycode  86 = KP_Add
keycode  87 = KP_1
keycode  88 = KP_2
keycode  89 = KP_3
keycode  90 = KP_0
keycode  91 = KP_Decimal
keycode  92 = 0x1007ff00
keycode  93 =
keycode  94 = at numbersign
! less greater backslash
keycode  95 = F11
keycode  96 = F12
keycode  97 = Home
keycode  98 = Up Up Prior
keycode  99 = Prior
keycode 100 = Left Left Home
keycode 101 = Begin
keycode 102 = Right Right End
keycode 103 = End
keycode 104 = Down Down Next
keycode 105 = Next
keycode 106 = Insert
keycode 107 = Delete
keycode 108 = Delete
keycode 109 = Control_R
keycode 110 = Pause
keycode 111 = Print
keycode 112 = KP_Divide
keycode 113 = Mode_switch
keycode 114 = Break
keycode 115 = Mode_switch
keycode 116 = Mode_switch
keycode 117 = Multi_key
add Mod1 = Alt_L
add Mod2 = Mode_switch

```


**_Method 2 : changing symbol map_:** 


This is for International keyboard (french - belgian/fr ) but
you could adapt it easily to your keyboard

Define your keyboard in xorg.conf
and configure right apple key to alt-gr

```
Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbLayout" "be"
Option "XkbModel" "pc104"
Option "XkbOptions" "lv3:rwin_switch"
EndSection

```

I had to reconfigure some keys that were not properly defined even with macintosh layout (@#,<>..). 

I also made some custom changes to access development keys easily :
[LIST]
[*]Alt-Gr < gives {
[*]Shift AltGr > gives }
[*]AltGr ( gives [
[*]Shift AltGr ) gives ]
[*]mu key gives \
[/LIST]

Here is the hacked part of my /etc/X11/xkb/symbols/be :
```
partial default alphanumeric_keys
xkb_symbols "basic" {

include "latin"

name[Group1]="Belgium";

key <AE01> { [ ampersand, 1, bar, exclamdown ] };
key <AE02> { [ eacute, 2, at, oneeighth ] };
key <AE03> { [ quotedbl, 3, numbersign, sterling ] };
key <AE04> { [apostrophe, 4, onequarter, onehalf ] };
key <AE05> { [ parenleft, 5, bracketleft, threeeighths ] };
key <AE06> { [ section, 6, asciicircum, fiveeighths ] };
key <AE07> { [ egrave, 7, braceleft, seveneighths ] };
key <AE08> { [ exclam, 8, bracketleft, trademark ] };
key <AE09> { [ ccedilla, 9, braceleft, plusminus ] };
key <AE10> { [ agrave, 0, braceright, degree ] };
key <AE11> { [parenright, degree, bracketright, questiondown ] };
key <AE12> { [ minus, underscore, dead_cedilla, dead_ogonek ] };

key <AD01> { [ a, A, at, Greek_OMEGA ] };
key <AD02> { [ z, Z, lstroke, Lstroke ] };
key <AD03> { [ e, E, EuroSign, cent ] };
key <AD11> { [dead_circumflex, dead_diaeresis, bracketleft, dead_abovering ] };
key <AD12> { [ dollar, asterisk, EuroSign, dead_macron ] };

key <AC01> { [ q, Q, ae, AE ] };
key <AC10> { [ m, M, dead_acute, dead_doubleacute ] };
key <AC11> { [ ugrave, percent, dead_acute, dead_caron ] };
key <LSGT> { [ at, numbersign, twosuperior, threesuperior ] };

key <BKSL> { [ backslash, sterling, dead_grave, dead_breve ] };
key <AB01> { [ w, W, guillemotleft, less ] };
key <AB07> { [ comma, question, dead_cedilla, masculine ] };
key <AB08> { [ semicolon, period, horizconnector, multiply ] };
key <AB09> { [ colon, slash, periodcentered, division ] };
key <AB10> { [ equal, plus, dead_tilde, dead_abovedot] };
key <TLDE> { [ less, greater, braceleft, braceright ] };

```

***Configure special keys***

Todo : fn keys are not catchable event ...

[LIST]
[*]Install keylaunch with synaptic and put in in xinitrc script
[*]go to your home directory and create a file .keylaunchrc
[*]add this to the file :
[/LIST]

```
key=.*.F2:backlight +10
key=.*.F1:backlight -10
```

Atlernatively, for backlight control, you can use a programm
developped by alexinfurs availabel here :
[http://ubuntuforums.org/showthread.php?t=215801](http://ubuntuforums.org/showthread.php?t=215801)

***Temperatures***

Hard Disk Temperature:
```

sudo apt-get install hddtemp
hddtemp  /dev/sda

```

That prints the temperature of your harddisk

CPUs Temperature : 
(This code was written by Jan Bernhardt and Ludovi Roussearu under GPL)
```

sudo apt-get install subversion
svn co https://svn.sourceforge.net/svnroot/mactel-linux mactel-linux
cd mactel-linux/trunk/tools/temperature/
make
sudo modprobe msr
sudo ./coretemp

```

That prints temperatures of both CPUs




***Bluetooth***

I was able to send/receive files via bluetooth with a SE P910 phone.

Install bluetooth packages : gnome or kde depending of what you like 
(gnome-bluetooth, kdebluetooth, bluesutil..) they are both working.  
Also obex libraries (qobex, libopenobex)

*_For gnome users :_*
Launch System>Preference>Bluetooth manager
Meneu Device>Scan ... you should see your phone

On the phone search devices, you should see you computer

Launch Applicarions>Accessoires>Bluetooth File Sharing

Phone to computer :
Send a file from the phone to the computer.  A confirmation popup 
is launched and the file is in your home directory !

Computer to phone:
Right click a file, send to, select your device.. that works 

**Touchpad**

I could configure touchpad right click with mouseemu but after each right click it freezes ..
If anybody find out how to get it working please give us feedback.

Install mouseemu (with synaptic or apt-get --install mouseemu)
Edit config file: 
> sudo vi /etc/default/mouseemu

Add that content :

> MID_CLICK="-middle 56 272" # Alt + mouse click = middle click
RIGHT_CLICK="-right 464 272" # Fn + mouse click = right click
SCROLL="-scroll 87" # F11 + mouse movement
TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress

Restart mouseemu :

> sudo  /etc/init.d/mouseemu restart

Requested by JDR.  Any idea ?

**External Mouse**

A little bit out of scope but I manage to get my Logitech MX510
side button working with this in the xorg.conf :
```

Section "InputDevice"
  Identifier  "Configured Mouse"
  Driver      "mouse"
  Option      "CorePointer"
  Option      "Device" "/dev/input/mice"
  Option      "Protocol" "ExplorerPS/2"
  Option      "Emulate3Buttons" "false"
  Option      "Buttons" "5"
  Option      "ZAxisMapping" "4 5"
  Option      "ButtonMapping" "1 2 3 6 7"
  Option      "Resolution" "800"
EndSection

```
(source  [http://www.ubuntuforums.org/showthread.php?t=150116](http://www.ubuntuforums.org/showthread.php?t=150116) )\



**WebCam**


Ronald S. Bultje is writing a driver look at his blog :
[http://blogs.gnome.org/portal/rbultje](http://blogs.gnome.org/portal/rbultje)

Rapido get it working.  His notes are here :
[http://www.ubuntuforums.org/showthread.php?t=225621](http://www.ubuntuforums.org/showthread.php?t=225621)

```

sudo apt-get install libusb-0.1-4 libusb-dev libgcrypt11-dev libglib2.0-dev
wget http://people.freedesktop.org/~rbultje/linux-uvc-0.1.0-e.tar.gz
tar xvfz linux-uvc-0.1.0-e.tar.gz
cd linux-uvc-0.1.0-e/
make
sudo make install
sudo mkdir /mnt/mac
sudo mount -t hfsplus /dev/sda2 /mnt/mac/
sudo ./extract /mnt/mac/System/Library/Extensions/IOUSBFamily.kext/Contents/PlugIns/AppleUSBVideoSupport.kext/Contents/MacOS/AppleUSBVideoSupport
sudo modprobe uvcvideo

```

Then try a soft like Ekiga with V4L2 support.  It works !
See rapido post for more details. [http://www.ubuntuforums.org/showthread.php?t=225621](http://www.ubuntuforums.org/showthread.php?t=225621)

**Access MacOsX partition**

You can still access (in read only mode) your MacOsX partition as this :

> sudo mkdir /mnt/mac
mount -t hfsplus /dev/sda2 /mnt/mac
cd /mnt/mac


**Troubleshooting**

Heat ... under Linux MBP is even hotter than on MacOSx .. 
Especially the harddrive ..

"kernel panic - not syncing: IO-APIC + timer doesn't work!"
occurs often when the usb mouse is plugged at boot.  So either
apply patches or boot with mouse unplugged ... 
(I also had rarely this error with unplugged mouse ..)

**Desktop**
Finally .. find a suitable desktop for such a great OS on a great Machine !

I built mine on the theme : " Tux the pingouin crunched the apple "  ;-)

It is based on [HumanBlue]("http://www.gnome-look.org/content/show.php?content=40670"), [HumanAzul]("http://www.gnome-look.org/content/show.php?content=37099"), [Tux-Mania]("http://www.gnome-look.org/content/show.php?content=15994")  GDM and a [Tux screenshot]("http://www.gnome-look.org/content/show.php?content=26229") comming from
[http://www.gnome-look.org](http://www.gnome-look.org)

To get rid of brown background while starting, change background color in /etc/gdm.conf
( BackgroundColor=#5B5B5B instead of BackgroundColor=#2b0600 )

(See pictures in attachments)




[QUOTE=rapido]Thanks for the great thread.  Audio was a big hangup for me.  After updating to 2.6.15-25, I get sound out of the headphone jack only.   But no audio out of the internal speaker(s).
Any ideas?[/QUOTE]

I had audio in the jack only before upgrading to 2.6.15-25.  Just to be sure, did
launch lilo again after upgrading ?  Check with uname -a

[QUOTE=rapido]Could you grep through any sound/alsa settings in /etc/modutils and /etc/modprobe.d to see if there are any snd-hda-intel specific settings?

If you find anything, please copy the contents of the config file into this thread.

It is quite possible that my sound issue is an alsa configuration problem.[/QUOTE]

Here is the result of requested grep :

```

me@host:/etc/modprobe.d$ grep -i intel /etc/modutils/*
me@host:/etc/modprobe.d$ grep -i intel /etc/modprobe.d/alsa-base
/etc/modprobe.d/alsa-base:options snd-intel8x0m index=-2

```

---

### Post by rapido on 2006-06-19
Here is the reqested uname -a:
Linux fudge 2.6.15-25-686 #1 SMP PREEMPT Wed Jun 14 11:34:19 UTC 2006 i686 GNU/Linux

Is this the same kernel you are using?

---

### Post by phico on 2006-06-20
[QUOTE=rapido]Here is the reqested uname -a:
Linux fudge 2.6.15-25-686 #1 SMP PREEMPT Wed Jun 14 11:34:19 UTC 2006 i686 GNU/Linux

Is this the same kernel you are using?[/QUOTE]

Yes I have the same kernel and the card chipset is a SigmaTel STAC9221 A1

I noticed that I still have two problems however :
- when headset is plugged in jack, I get sound both on speaker and headset
- headset microphone neither integrated microphone do not work

---

### Post by Nelson-Ray on 2006-06-22
I am thinking about ordering a MacBook...I am curious if you have to use the Dapper x86 install cd or the ppc version? The MacBook has that intel duo core chip and Im guessing x86 but not sure?

---

### Post by phico on 2006-06-22
[QUOTE=Nelson-Ray]I am thinking about ordering a MacBook...I am curious if you have to use the Dapper x86 install cd or the ppc version? The MacBook has that intel duo core chip and Im guessing x86 but not sure?[/QUOTE]

Yes you should use x86 CD.  MacBook are intel based.

---

### Post by Gendo on 2006-06-26
I was wondering if anyone resolved rapido's issue. I am having the same issue with my mbp, and I am running the kernel phico mentions, and I have even tried the latest alsa drivers which should be patched to fix this, but I can still not get the speakers to output any audio. I am wondering if anyone who has this working is using a specific .asoundrc or asound.conf that might make a difference. Any information would be appreciated.

---

### Post by phico on 2006-06-27
[QUOTE=Gendo]I was wondering if anyone resolved rapido's issue. I am having the same issue with my mbp, and I am running the kernel phico mentions, and I have even tried the latest alsa drivers which should be patched to fix this, but I can still not get the speakers to output any audio. I am wondering if anyone who has this working is using a specific .asoundrc or asound.conf that might make a difference. Any information would be appreciated.[/QUOTE]

I did not had to install anything special ( or I did not notice it or I was lucky ...)
Anyway If I can help you sharing config of so, just ask.

I have a MBP 17 with Sigmatel STAC9221 A1 chipset
and I choosed HDA Intel (Alsa Mixer) device in my sound config

---

### Post by Gendo on 2006-06-27
Sure if you are using an asound.conf or .asoundrc that information might be helpful as well as what is in /var/lib/alsa/asound.state . I did not realize you had a 17 inch macbook pro, I am using a 15 inch that was released before the glossy and 17 inch models, so I am wondering if maybe something is different with the 17 inch models. From the info in patch_sigmatel.c from the alsa drivers the note on the macs mentions 
 /*
 * Early 2006 Intel Macintoshes with STAC9220X5 codecs seem to have a
 * funky external mute control using GPIO pins.
 */ 
  So I guess it is possible they changed the hardware a bit on the 17 inch models.

---

### Post by phico on 2006-06-27
[QUOTE=Gendo]Sure if you are using an asound.conf or .asoundrc that information might be helpful as well as what is in /var/lib/alsa/asound.state .
[/QUOTE]

I have no asound.conf neither .asoudrc on my system.
asound.state is in attachment

[QUOTE=Gendo]
 From the info in patch_sigmatel.c from the alsa drivers the note on the macs mentions 
 /*
 * Early 2006 Intel Macintoshes with STAC9220X5 codecs seem to have a
 * funky external mute control using GPIO pins.
 */ 
  So I guess it is possible they changed the hardware a bit on the 17 inch models.[/QUOTE]

Yes it might be.  Did you check which chipset you have ?
I though that patch could help me also because, as said above, my
microphone is not yet working.

---

### Post by sam666 on 2006-06-29
Guys,

I installed Ubuntu on My 15" 2.1Ghz macbook pro. I follwed instructions but I noticed the following:


- ATI Graphics is not fully accelerated.. some 2D displays are fast (moving windows, VMware display etc...), but resizing a terminal window or switching from one desktop to another lags considerably.

Did I miss something in the installation? Any ideas?

Should I use 8.26.18 Ati drivers or 8.25.18 ( I used the ones that matched xorg-ati-drivers..: 8.25.18... but tested 8.26.18 as well...)?

I read another post mentionning that to get full acceleration the kernel had to be recompiled without imacfb or something else like Frame buffer... Haven't tried yet. Does anyone know about this?

- Sound does not work, even with 2.6.16-25 686 (didn't investigate a lot yet...) 

- Also, the CPU being multi-core wouldn't it be better to use a SMP kernel? are both core used with an non SMP kernel?

- hdparm -t gives me very bad statistics for my internal (and firewire) drive: something between 20-30 MB/s  reading. I had much more under debian on a less powerfull Dell laptop.

- most hdparm parameters (DMA etc..) return an error...

Any suggestion?

Thanks,
Sam

---

### Post by phico on 2006-06-29
[QUOTE=sam666]
- ATI Graphics is not fully accelerated.. 
 the kernel had to be recompiled without imacfb or something else like Frame buffer...
[/QUOTE]

I did not check that myself.  It is true that some screensavers do not seem to rue very smootly.


imacfb is closely linked to efi.   I recompiled the kernel 2.6.17 with Macbook Pro options with this config :
[http://modular.math.washington.edu/macbook/triboot/config-2.6.16.16](http://modular.math.washington.edu/macbook/triboot/config-2.6.16.16)
and add imacfb but it did not changed anything excepted I lost sound !  A patch is needed
with 2.6.17   It has been posted on mactel-linux-user mailing list


If you do it please feedback.

For sound, It seems some MBP does not have the same chipset as 
mine.  That could explain.  It works with 2.6.15-25-686

[QUOTE=sam666]
both core used with an non SMP kernel?
[/QUOTE]
My kernel is  2.6.15-25-686 #1 SMP PREEMPT Wed Jun 14 11:34:19 UTC 2006 i686 GNU/Linux
Both core are used
[QUOTE=sam666]
- hdparm -t gives me very bad statistics for my internal (and firewire) drive: something between 20-30 MB/s reading. I had much more under debian on a less powerfull Dell laptop.
[/QUOTE]
On my system I get this result on internal 7200rpm drive :
 Timing buffered disk reads:  134 MB in  3.01 seconds =  44.55 MB/sec

---

### Post by Gendo on 2006-06-29
Here is what I did for ATI accelerration 

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

Here is for compiz and XGL

[http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper](http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper)

Good luck!

---

### Post by phico on 2006-06-29
[QUOTE=Gendo]Here is what I did for ATI accelerration 

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

Here is for compiz and XGL

[http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper](http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper)

Good luck![/QUOTE]


Thanks for those links, I added your contribution to the beginning of the thread.

Also I tried to configure the right click on the touchpad.
I managed to get is working but it freeze the touchpad after each click ..
If anyone could find out why .. that could be useful !

Install mouseemu (with synaptic or apt-get --install mouseemu)
Edit config file: 
> sudo vi /etc/default/mouseemu

Add that content :

> MID_CLICK="-middle 56 272" # Alt + mouse click = middle click
RIGHT_CLICK="-right 464 272" # Fn + mouse click = right click
SCROLL="-scroll 87" # F11 + mouse movement
TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress

Restart mouseemu :

> sudo  /etc/init.d/mouseemu restart

---

### Post by Gendo on 2006-07-01
I have been do some research on the sound issue and I have found there does seem to be a difference between the 17" mbp and the 15" mbp. The 17" mbp seems to be more like the mini in the way it behaves which is why I think the speakers are working on the 17". 

For example in windows to disable the internal speaker and have the headphone jack only on the 17" and mini you need to change the 00 REG_BINARY at HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\
Control\Class\{4D36E96C-E325-11CE-BFC1-08002BE10318} from 85 to 05, but this does not work on the 15" mbp and this needs to be changed from 85 to 80. 

I have been poking around in the alsa code (patch_sigmatel.c) trying to add a switch that might toggle this, I have manged to get a switch to display but it really does not do anything as I am really not well versed in alsa's workings. I do think it may have to do with the two calls to stac922x_gpio_mute in stac92xx_init. That or for whatever reason the AUTO_PIN_XXXXs are not getting enumerated properly. However like I said I am not well versed in ALSA and how it works so I am pretty much just throwing darts. 

I also found this table, I am not sure if it is pertinent or not, but just throwing it out there.

00,01
85 88 both
85 85 both
88 88 head phone
88 85 HEADphone
85 both
88 head

---

### Post by rapido on 2006-07-01
Gendo,

I have a little more information to possibly help with the research.  Mostly, on which machines seem to work and which fail ( sound-wise ).  

I have both a 15" mbp, and a 20" Intel Imac.  I have installed Ubuntu on both, and have the same end result on both as far as sound is concerned.  They will each play over the headphone jack only.  I believe that both of these are considered "Early 2006" as far as firmware, etc.  My thought is that if we find a solution for one of these machines, that both will work.

I have not yet confirmed any fully working audio examples of these machines.

But, I have heard of successes with the new Macbook ( [http://desrt.mcmaster.ca/macbook.xhtml](http://desrt.mcmaster.ca/macbook.xhtml) ) and the 17" mbp ( this thread ).

---

### Post by Gendo on 2006-07-01
rapido, I had seen that link earlier, and the patch referenced is what is merged into the latest dev alsa drivers at [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.12rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.12rc1.tar.bz2) and similarly the ubuntu kernel has been patched with similar code. 

The way I figure it the pin settings for the iMac and 15" mbp pro are the same (not working) , and the 17" mbp, mac mini, and regular macbook are the same (working).

I am trying to see if I can reverse the behavior in the alsa code with a toggle, so maybe it could be merged in. But so far I have not had much success other than making the line out and the headphones work for output without being toggled to and unable to be turned off.

I am going to post my results to the alsa devs (see bugtrack that had been started by someone else [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2198](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2198)) in a day or so since there are a few more things I am going to try before giving up.

---

### Post by sam666 on 2006-07-01
About graphic performance. I followed the instruction to get 8.26.18 installed and running and I noticed the following:

1/ - 2d Acceleration doesnt work very well when the fglrx module is loaded (when fglrxinfo shows ATI...

2/ - 2D acceleration works much better when fglrx is not loaded ( when fglrx shows MESA...)

when I mean 2d Acceleration is slow (1/) I mean everything seems fast except resizing a terminal (lags...) and switching desktops (redrawing the windows takes 2-3 seconds)...

Any idea why that is?


Sam

---

### Post by phico on 2006-07-04
[QUOTE=sam666]About graphic performance. I followed the instruction to get 8.26.18 installed and running and I noticed the following:

1/ - 2d Acceleration doesnt work very well when the fglrx module is loaded (when fglrxinfo shows ATI...

2/ - 2D acceleration works much better when fglrx is not loaded ( when fglrx shows MESA...)

when I mean 2d Acceleration is slow (1/) I mean everything seems fast except resizing a terminal (lags...) and switching desktops (redrawing the windows takes 2-3 seconds)...

Any idea why that is?


Sam[/QUOTE]

Yes I confirmed that behaviour.   I noticed however that under XGL/compiz,
switching from desktop is faster than with Gnome Session.  So it might be
related to the Xserver also.  Until now, I would use MESA with a Gnome Session
and ATI with XGL session but I have no explanation why it is like that..

---

### Post by gavinfo on 2006-07-04
Before I think about trying this, I want to make sure I understand the process.  In the section 

**Install Linux Ubuntu**

after

*Grub installation fails at the end, just ignore it.*

it says

*Open a terminal : Terminal 1*

In my imagination at this point I see a black screen with an error message - how do you open up a terminal? (is there some key combination, or is my imagination of it wrong)

---

### Post by phico on 2006-07-04
[QUOTE=gavinfo]Before I think about trying this, I want to make sure I understand the process.  In the section 

**Install Linux Ubuntu**

after

*Grub installation fails at the end, just ignore it.*

it says

*Open a terminal : Terminal 1*

In my imagination at this point I see a black screen with an error message - how do you open up a terminal? (is there some key combination, or is my imagination of it wrong)[/QUOTE]

Only the installation process should crash not the system.  So you can still open a Terminal with the menu Applications>Accessories>Terminal

(Ubuntu installation is done by :
1 - boot the live cd
2 - install from there on the disk (this is the process which crashes at the end .. but you are still in your working live cd system)

---

### Post by gavinfo on 2006-07-04
I see, thanks for that.

---

### Post by Greywhind on 2006-07-04
I'm about to install Ubuntu on my iMac - can anyone tell me whether the partition for it should be as large as I can get it or just enough for the OS itself?

If the OS can read files from other areas of the disk, I would assume that it should be a small partition for Ubuntu. If it can only read from its own partition, I would make it large. Please tell me which one is the case, if anyone knows.

---

### Post by phico on 2006-07-04
[QUOTE=Greywhind]I'm about to install Ubuntu on my iMac - can anyone tell me whether the partition for it should be as large as I can get it or just enough for the OS itself?

If the OS can read files from other areas of the disk, I would assume that it should be a small partition for Ubuntu. If it can only read from its own partition, I would make it large. Please tell me which one is the case, if anyone knows.[/QUOTE]

You can choose the partition as large as you want (as soon as it is large 
enough to install ubuntu)  
I created a very small MacOsX partition because my principal OS is Linux
and I keep MacOsX only for firmware update

You can still mount and access your Mac partition  (read only) as this :

>  sudo  mount -t hfsplus /dev/sda2 /mnt/mac
 cd /mnt/mac

---

### Post by gavinfo on 2006-07-04
Is it possible to change the partition size non-destructively later on? (at least non-destructively for the linux partition, but ideally for both)

Edit: seems diskutil resizeVolume from the Mac side should resize the partitions non-destructively.

---

### Post by phico on 2006-07-04
[QUOTE=gavinfo]Is it possible to change the partition size non-destructively later on? (at least non-destructively for the linux partition, but ideally for both)

Edit: seems diskutil resizeVolume from the Mac side should resize the partitions non-destructively.[/QUOTE]

It should ... but .. maybe It would be safer to test on a simple dual boot install before !

---

### Post by chasisaac on 2006-07-04
[QUOTE=gavinfo]
Edit: seems diskutil resizeVolume from the Mac side should resize the partitions non-destructively.[/QUOTE]

Thanks for the the edit. 

ci

---

### Post by Gendo on 2006-07-05
rapido, or anyone with a 20" iMac could you cat /proc/asound/card0/codec#* and post the results here. This is for the alsa guys.

---

### Post by imrazor on 2006-07-06
OK, I'm stuck. I installed ubuntu and lilo, but I'm stuck at the part that says:

Go in the rEFIt partition editor and synchronize MBR

I get *no* such option. rEFIt gives me four options: Boot Mac OS X from HD, Boot Linux from HD, About and Restart. I've checked the refit.conf file and "hideui" is *not* specified.

When I attempt to "Boot Linux from HD" I get a message:

No bootable device -- insert boot disk and press any key

Fortunately, Boot Mac OS X still functions, so I'm not completely hosed.

So is this because I can't sync the MBR and GPT tables, or because there's something wrong with the Ubuntu install? Is there an alternative way to sync the MBR and GPT tables (with parted maybe?)

EDIT: Figured it out...the location of the tools are hard-coded as /efi/tools. When I unzipped rEFIt it created a directory called refit-0.7 in the root directory, which confused refit when the notebook booted.

---

### Post by phico on 2006-07-06
[QUOTE=imrazor]OK, I'm stuck. I installed ubuntu and lilo, but I'm stuck at the part that says:

Go in the rEFIt partition editor and synchronize MBR

I get *no* such option. rEFIt gives me four options: Boot Mac OS X from HD, Boot Linux from HD, About and Restart. I've checked the refit.conf file and "hideui" is *not* specified.

When I attempt to "Boot Linux from HD" I get a message:

No bootable device -- insert boot disk and press any key

Fortunately, Boot Mac OS X still functions, so I'm not completely hosed.

So is this because I can't sync the MBR and GPT tables, or because there's something wrong with the Ubuntu install? Is there an alternative way to sync the MBR and GPT tables (with parted maybe?)

EDIT: Figured it out...the location of the tools are hard-coded as /efi/tools. When I unzipped rEFIt it created a directory called refit-0.7 in the root directory, which confused refit when the notebook booted.[/QUOTE]

Boot on MacOsX
Go to the config file of refit :  /etc/efi/refit.conf 
Unhide the menu like this :

> #hideui tools funcs hdbadges
#hideui all

Reboot, you should have more options ...

---

### Post by rapido on 2006-07-08
> **Gendo said:**
> rapido, or anyone with a 20" iMac could you cat /proc/asound/card0/codec#* and post the results here. This is for the alsa guys.

```
Codec: SigmaTel STAC9221 A1
Address: 0
Vendor Id: 0x83847680
Subsystem Id: 0x100
Revision Id: 0x103401
Default PCM: rates 0x7e0, bits 0x0e, types 0x1
Default Amp-In caps: ofs=0x00, nsteps=0x0e, stepsize=0x05, mute=1
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
Node 0x02 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x66 0x66]
  Power: 0x0
Node 0x03 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0xff 0xff]
  Power: 0x0
Node 0x04 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x7f 0x7f]
  Power: 0x0
Node 0x05 [Audio Output] wcaps 0xd0c05: Stereo Amp-Out
  Amp-Out caps: N/A
  Amp-Out vals:  [0x7f 0x7f]
  Power: 0x0
Node 0x06 [Audio Input] wcaps 0x1d0541: Stereo
  Power: 0x0
  Connection: 1
     0x17
Node 0x07 [Audio Input] wcaps 0x1d0541: Stereo
  Power: 0x0
  Connection: 1
     0x18
Node 0x08 [Audio Output] wcaps 0x40211: Stereo Digital
  PCM: rates 0x7e0, bits 0x0e, types 0x5
Node 0x09 [Audio Input] wcaps 0x140311: Stereo Digital
  PCM: rates 0x160, bits 0x0e, types 0x5
  Connection: 1
     0x11
Node 0x0a [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x08173f: IN OUT HP
  Pin Default 0x010b4040: [Jack] Line Out at Ext Rear
    Conn = Comb, Color = Green
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x02
Node 0x0b [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x081737: IN OUT
  Pin Default 0x90a30110: [Fixed] Mic at Int N/A
    Conn = ATAPI, Color = Unknown
  Pin-ctls: 0x24: IN
  Connection: 1
     0x04
Node 0x0c [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x081737: IN OUT
  Pin Default 0x90130130: [Fixed] Speaker at Int N/A
    Conn = ATAPI, Color = Unknown
  Pin-ctls: 0x20: IN
  Connection: 1
     0x03
Node 0x0d [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x08173f: IN OUT HP
  Pin Default 0x4000000f: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x02
Node 0x0e [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x0824: IN
  Pin Default 0x4000000f: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x20: IN
Node 0x0f [Pin Complex] wcaps 0x400181: Stereo
  Pincap 0x0837: IN OUT
  Pin Default 0x01813020: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
  Pin-ctls: 0x20: IN
  Connection: 1
     0x05
Node 0x10 [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x014be050: [Jack] SPDIF Out at Ext Rear
    Conn = Comb, Color = White
  Pin-ctls: 0x40: OUT
  Connection: 3
     0x08* 0x17 0x19
Node 0x11 [Pin Complex] wcaps 0x430681: Stereo Digital
  Pincap 0x0810024: IN
  Pin Default 0x4000000f: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x00:
  Power: 0x0
Node 0x12 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x01 0x01]
  Connection: 7
     0x0e* 0x15 0x0f 0x0b 0x0c 0x0d 0x0a
Node 0x13 [Audio Selector] wcaps 0x30010d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x04, stepsize=0x27, mute=0
  Amp-Out vals:  [0x00 0x00]
  Connection: 7
     0x0e 0x15* 0x0f 0x0b 0x0c 0x0d 0x0a
Node 0x14 [Beep Generator Widget] wcaps 0x70000c: Mono Amp-Out
  Amp-Out caps: ofs=0x03, nsteps=0x03, stepsize=0x17, mute=0
  Amp-Out vals:  [0x00]
Node 0x15 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x0820: IN
  Pin Default 0x4000000f: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x00:
Node 0x16 [Volume Knob Widget] wcaps 0x600000: Mono
Node 0x17 [Audio Selector] wcaps 0x300903: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x80 0x80]
  Connection: 1
     0x12
Node 0x18 [Audio Selector] wcaps 0x300903: Stereo Amp-In
  Amp-In caps: N/A
  Amp-In vals:  [0x80 0x80]
  Connection: 1
     0x13
Node 0x19 [Vendor Defined Widget] wcaps 0xf30201: Stereo Digital
Node 0x1a [Audio Output] wcaps 0x30201: Stereo Digital
Node 0x1b [Pin Complex] wcaps 0x400301: Stereo Digital
  Pincap 0x0810: OUT
  Pin Default 0x4000000f: [N/A] Line Out at Ext N/A
    Conn = Unknown, Color = Unknown
  Pin-ctls: 0x00:
  Connection: 1
     0x1a
```

---

### Post by fanopanic on 2006-07-09
Hi there,

I have a 17" MBP and my sound was very noisy (ugly little clicks) both on HP and on the speakers. This did not happen on OSX. Reducing the volume even to very low did not make it go away. 

The solution was to add either
```
options snd-hda-intel "position_fix=1"
```
or
```
options snd-hda-intel "position_fix=2"
```
to /etc/modprobe.d/alsa-base.

---

### Post by phico on 2006-07-14
> **fanopanic said:**
> 
```
options snd-hda-intel "position_fix=2"
```
to /etc/modprobe.d/alsa-base.

position_fix=2 did not work on my MPB 17" .. I had sound card
not recognised any longer ..

Also I added at the begining of the thread some information
to get keyboard backlight working

---

### Post by tomoya846 on 2006-07-17
hi everyone, i got an issue here with my ubuntu on MBP 15"

after the installation of mouseemu, i couldnt use my touchpad anymore! just wondering if anyone knows how to get rid of mouseemu or are there any other ways to solve this problem.

thanks:) 
eddie

---

### Post by phico on 2006-07-17
As said above, I have the same issue.  I could
get the control back with an external mouse.  
It seems mouseemu need some change to work on macbook pro

---

### Post by Gendo on 2006-07-17
Well I figured out a way to get sound working out of the speakers on the 15 incher. It is not elegant at the moment but if you are dying to have sound from the speakers like I was here is a quick hack until the alsa guys can fix it. 

Grab the latest alsa dev release here [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.12rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.12rc1.tar.bz2)

Unpack it somewhere.

in the alsa-driver-1.0.12rc1 folder run

./configure --with-cards=hda-intel --with-sequencer=yes

After it is done go to alsa-driver-1.0.12rc1/alsa-kernel/pci/hda and open up hda_codec.c and comment out lines 2135 and 2147 so it now looks like

	//if (! cfg->line_outs) {
		if (cfg->speaker_outs) {
			cfg->line_outs = cfg->speaker_outs;
			memcpy(cfg->line_out_pins, cfg->speaker_pins,
			       sizeof(cfg->speaker_pins));
			cfg->speaker_outs = 0;
			memset(cfg->speaker_pins, 0, sizeof(cfg->speaker_pins));
		} else if (cfg->hp_pin) {
			cfg->line_outs = 1;
			cfg->line_out_pins[0] = cfg->hp_pin;
			cfg->hp_pin = 0;
		}
	//}

Save the file and then go back to alsa-driver-1.0.12rc1.

Do a make;make install reboot and you should have sound from the speakers. Problem is the headphone jack will not work (the line out toggle will but the speakers will not auto switch off when an input is plugged in). I will work on adding a check box toggle a little later, but I was eager to get my speakers working so someone else may be as eager as I was. Good luck!

---

### Post by phico on 2006-07-18
> **Gendo said:**
> Well I figured out a way to get sound working out of the speakers on the 15 incher. 

Great ! Thanks.  I mentioned your post above.

Did you find a way to get the microphone working ?!

---

### Post by Gendo on 2006-07-18
Well not sure if it was working before, but with my change from above and then if you open volume control 2.14 hit the options tab, set the input source to mic, close it, and then launch sound recorder, I was able to record through the mic. Not sure if the code change had an effect on this or not though, that and it may not work with the 17".

---

### Post by fanopanic on 2006-07-19
> **phico said:**
> position_fix=2 did not work on my MPB 17"

Interestingly enough I have to use position_fix=1 since the latest kernel update. With position_fix=2 the crackling continues.

Edit: Regarding no sound with the fix above: I noticed I have to reboot with headphones plugged in after a kernel upgrade (I kid you not). I will then have sound only in the HP at first, and when I remove them I have sound on the laptop again. Plugging them in again, however, does not turn off the laptop speakers again.
Seems like sound on the MBP is still adventure. :D

---

### Post by phico on 2006-07-19
Thanks for your feedbacks about sound ..

Microphone is still not working with "sound recroder" application but
**It works with Skype 1.3 beta for Linux**  :-D  :-D  (but not with skype 1.2)
At least, it was what I was missing most on the macbook ...

I installed latest alsa drivers, latest kernel and the new skype 1.3 beta. 

Also I get rid of sound in speakers and headset at the same time ..

In one word .. sound is now working perfectly on MPB17 :p :p

---

### Post by zoglesby on 2006-07-21
I have a 15 inch macbook pro and I followed the directions from this [link]("http://blogs.gnome.org/view/rbultje/2006/07/18/1") to get my sound to work but the only time that I hear any sound is when I am loging off with a reboot, so I know the sound works but somthing must be set up wrong.

Edit: So that seems to not be ture. I tried to start the computer up with my headphones pluged in and the sound did work for that boot but it still seems odd that when I reboot I get the logout sound (without ever having pluged in the headphones).

---

### Post by eyebrowman92 on 2006-07-21
How do we go into the rEFIt partition editor to synchronize the MBR?

---

### Post by phico on 2006-07-22
> **eyebrowman92 said:**
> How do we go into the rEFIt partition editor to synchronize the MBR?

please see here  :

[http://ubuntuforums.org/showpost.php?p=1219768&postcount=33](http://ubuntuforums.org/showpost.php?p=1219768&postcount=33)

---

### Post by eyebrowman92 on 2006-07-22
Ok and my MacBook has no sound, even with the new kernel updates. Any suggestions?

---

### Post by phico on 2006-07-23
> **eyebrowman92 said:**
> Ok and my MacBook has no sound, even with the new kernel updates. Any suggestions?

If it is a MBP15 check Gendo trick : [http://ubuntuforums.org/showpost.php?p=1269085&postcount=39](http://ubuntuforums.org/showpost.php?p=1269085&postcount=39)

(It was not needed on MBP17)

---

### Post by phico on 2006-07-27
"kernel panic - not syncing: IO-APIC + timer doesn't work!" at boot
occurs only when the usb mouse (or another usb devide) 
is plugged at boot.  
So either apply patches or boot with mouse unplugged ...

---

### Post by Seq on 2006-07-27
> **phico said:**
> "kernel panic - not syncing: IO-APIC + timer doesn't work!" at boot
occurs only when the usb mouse (or another usb devide) 
is plugged at boot.  
So either apply patches or boot with mouse unplugged ...

This happens to me with no external devices plugged in to my MacBook (not Pro). Although the iSight, Trackpad, and keyboard are all USB I guess, just not external.

---

### Post by phico on 2006-07-28
> **Seq said:**
> This happens to me with no external devices plugged in to my MacBook (not Pro). Although the iSight, Trackpad, and keyboard are all USB I guess, just not external.

Good to know. Thanks.  Indeed I read iSight is USB.

---

### Post by auslander on 2006-07-28
I installed mouseemu and my trackpad is now disabled.  I had to do this:

 sudo /etc/init.d/mouseemu stop

to get it to work again.  This is the case with both a blank /etc/default/mouseemu file and with one that contains this (which I found somewhere else):

MID_CLICK="-middle 56 272" # Alt + mouse click = middle click
RIGHT_CLICK="-right 464 272" # Fn + mouse click = right click
SCROLL="-scroll 87" # F11 + mouse movement
TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress


I have a 15" 2.16GHz MBP.  has anyone got ctrl-click or anything else to get right-click to work?

thanks,

---

### Post by phico on 2006-07-29
> **auslander said:**
> /etc/default/mouseemu file and with one that contains this (which I found somewhere else):

MID_CLICK="-middle 56 272" # Alt + mouse click = middle click
RIGHT_CLICK="-right 464 272" # Fn + mouse click = right click
SCROLL="-scroll 87" # F11 + mouse movement
TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress


I do not see any difference between that config and the one I gave above ?
Did you change something else ?
Indedd touchpad freezes after each right click with that config.

---

### Post by auslander on 2006-07-29
> **phico said:**
> I do not see any difference between that config and the one I gave above ?
Did you change something else ?
Indedd touchpad freezes after each right click with that config.

Yeah, sorry -- that config is from above.  I've been switching between about 10 sources for configs to get it working, I must have become confused.  However, in my case, when I start mouseemu I can move the mouse about 1" on the screen before it freezes, not enough time to even get one right-click out of it.

---

### Post by lordmule on 2006-07-30
This guide was the most helpful for me in getting triple boot going. But I had alot of problems with the bootloader stuff and I have posted how I managed to get it finally going [here]("http://blogs.vislab.usyd.edu.au/index.php/JohnStavrakakis/2006/07/28/triple_boot_on_macbook_pro_15")

good luck lads

---

### Post by rapido on 2006-07-30
I just put together a quick howto on the Built-in iSight.  Here's the thread:
[http://www.ubuntuforums.org/showthread.php?t=225621](http://www.ubuntuforums.org/showthread.php?t=225621)

---

### Post by phico on 2006-07-30
> **rapido said:**
> I just put together a quick howto on the Built-in iSight.  Here's the thread:
[http://www.ubuntuforums.org/showthread.php?t=225621](http://www.ubuntuforums.org/showthread.php?t=225621)


Thank you rapido .. very useful and .. it is working !

---

### Post by phico on 2006-07-31
> **Seq said:**
> This happens to me with no external devices plugged in to my MacBook (not Pro). Although the iSight, Trackpad, and keyboard are all USB I guess, just not external.

You are right Seq .. It has just happen to be also with usb mouse unplugged ...  Though it seems to appear more often with plugged mouse :confused:  :confused:

---

### Post by bfad on 2006-08-05
Lilo will not install for me.  I've booted from the CD, installed Ubuntu and followed the directions, but lilo won't install, I get an error saying:

"Package lilo is not availale, but is referred to by another package.  This may mean that the package is missing, has been obsoleted, or is only available from another source.
E: Package lilo has no instalation canidate"

In fact, I get that same error trying to install anything.  However, if I don't chroot /mnt/ubuntu /bin/bash, installations work fine.  It's as if I don't have internet connection when I've changed root.  

I'm guessing that if I do installations without chroot-ing then I'm "installing" them on the CD and not my hard drive.  Any suggestions?

---

### Post by bfad on 2006-08-05
I solved the issue!  I reinstalled the distribution, and when the Grub error came up, I didn't click okay, but went immediately into the Terminal and ran the commands!

---

### Post by phico on 2006-08-05
> **bfad said:**
> I solved the issue!  I reinstalled the distribution, and when the Grub error came up, I didn't click okay, but went immediately into the Terminal and ran the commands!

Good to know ! thanks for your feedback.
That step may be a source of problem indeed ..
another user reported me that he could not get acess to the network
in the chroot terminal ?!  He had to reconfigure the network manually.

---

### Post by Ross Hend on 2006-08-07
I've followed a lot of the tutorials on this thread, and they all worked! Thank You! I've now got a fully functional install of Ubuntu on my Macbook Pro.

---

### Post by 2cute4u on 2006-08-08
I have a 20" intel imac and I followed the instructions given. I can't seem to get any video with the ati driver.

I've attached my xorg.conf

---

### Post by idn on 2006-08-10
Hi

I have folowed thje instructions up until I have to install lilo, the trouble is I cant find the package anywhere. I also cant find most of the other packages I need to install, as I cant connect to the servers - no wireless - I am kinda stuck. I dont want to reboot because I dont think I will be able to reboot into ubuntu after. Anyone have any ideas?

I have the standard dapper instsll....


Edit: I just downloaded the debs through the synaptic on the live cd then copied them over to the installed copy of ubuntu and installed them using dpkg -i

---

### Post by phico on 2006-08-11
> **idn said:**
> Hi

I have folowed thje instructions up until I have to install lilo, the trouble is I cant find the package anywhere. I also cant find most of the other packages I need to install, as I cant connect to the servers - no wireless - I am kinda stuck. I dont want to reboot because I dont think I will be able to reboot into ubuntu after. Anyone have any ideas?

I have the standard dapper instsll....


Edit: I just downloaded the debs through the synaptic on the live cd then copied them over to the installed copy of ubuntu and installed them using dpkg -i
Hello,

Another user report me simililar issue.  The problem seems no network is
available in the chroot terminal. It is strange it works for most fo us.  

The solution is to reactivate the network in the chroot terminal. 
Either :
- manually (ifup eth0) 
- with dhclient 
- or using the graphical config (gksu network-admin).

---

### Post by idn on 2006-08-11
Yeah there seems to be something wrong with my networking. I cant get wireless to work at the moment. Someone reported some success when they uninstalled network manager and the restricted modules, upgraded everything, then installed network manager and the restricted modules again again.

I also cant seem to find anything on aiglx, in the tutorial you mention xgl but from what i heard aiglx is faster, specially for ati people. Is there a chance you could add a section for installing aiglx? 

Oh one more thing = mouseemu just freezes my mouse whenever its started

Great tutorial tho!


EDIT:  I got the networking going by simply commenting everything but the top two lines in /etc/network/interfaces, then restarting. Everything then worked out the box! Im now on wireless - woot

---

### Post by phico on 2006-08-11
> **idn said:**
> 
I also cant seem to find anything on aiglx, in the tutorial you mention xgl but from what i heard aiglx is faster, specially for ati people. Is there a chance you could add a section for installing aiglx? 

Interesting information.  I did not try it yet.  
It seems there are some incompatibilty between fglrx and aigxl because
they use different version of Xorg.  We should wait for fglrx to
support Xorg 7.1. XGL with ati drivers works ok for now.
Did you install it yourself ?  Is there any link you could suggest about it ?

> **idn said:**
> 
Oh one more thing = mouseemu just freezes my mouse whenever its started


It freezes only my touchpad when right click. It is a known problem.  Mousemu was not written for macbook but for powerbook.  I do not beleive there is a update yet.

---

### Post by idn on 2006-08-11
I tried to install aiglx but an into problems so turned back, but I believe you are right we will proably have to wait until edgy to use aiglx. 

I used xgl before and it worked fine - no speed problems although that was on a top end desktop with all the bells and whistles. 

It just seems to me aiglx would be alot faster as it is a part of the xx server rather than something that  is a hack and sits on top of it 



I was wondering, would it be possible to add a seciton on how to configure lilo - even if it is a bit off topic. It would be good to make the boot silent - so theres none of those debug messages, and also so the text in the console is a little smaller. Its a shame there is no widescreen mode for the console (Ctlr Alt F1), because I tend to use this console alot day to day - makes ne feel retro :) I guess we could use the following for the 15" ppl

# VESA framebuffer console @ 1024x768x32k
vga="792"
# Normal VGA console
# vga = normal
# VESA framebuffer console @ 1024x768x64k
# vga=791
# VESA framebuffer console @ 1024x768x32k
# vga=790
# VESA framebuffer console @ 1024x768x256
# vga=773
# VESA framebuffer console @ 800x600x64k
# vga=788
# VESA framebuffer console @ 800x600x32k
# vga=787
# VESA framebuffer console @ 800x600x256
# vga=771
# VESA framebuffer console @ 640x480x64k
# vga=785
# VESA framebuffer console @ 640x480x32k
# vga=784
# VESA framebuffer console @ 640x480x256
# vga=769
# End LILO global section

May not be important to some but I find when there are a million boot messages going on i might miss soemthing important.

---

### Post by idn on 2006-08-11
Has anyone else noticed that the cap locks key doesnt a actually work? Even the LED doesnt toggle on and off...

---

### Post by idn on 2006-08-12
Hey 

I tried to follow the install guide for xgl but I get the following error when I run startcompiz

compiz.real: No composite extension

Could someone post their xorg.conf? I'm not sure what the problem is

I also get the following problem when i run flgxinfo:

fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

EDIT: I have fixed the above issue by:

sudo aptitude reinstall libgl1-mesa

---

### Post by Ross Hend on 2006-08-17
I noticed a lot of artifacts when using xgl and compiz. However, I'm new to ubuntu and have no idea whether they were the culprit.

And I have to make the point of a previous poster, the caps lock does not function (not that I ever use it).

---

### Post by idn on 2006-08-22
Has anyone got got the fn key working at all? It works for the volume control however it doesnt register when i press it in xev.

---

### Post by Seq on 2006-08-23
> **idn said:**
> Has anyone got got the fn key working at all? It works for the volume control however it doesnt register when i press it in xev.

they Fn key is not supposed to send a key event, it modifies other keys. It is handled in the kernel rather than X

---

### Post by eyseman on 2006-08-26
hi there, 

thx for the great install manual but i still face some probs.
i managed bootloading mac os x and xp on my intel iMac. 
but when it comes to the point of resync the mbr i fail. 
this is my table is see after resync

1 EFI Protective
2 Mac OS X HFS+
3 EFI System FAT
4 FAT 32

shouldn't there be an ext2 line or something like that for ubuntu?

I already checked the workaround manual but i can't find my lilo.conf any more when booting from cd.

Booting "First Hard Disk" out of the Live CD gives me a system hangover.
Any ideas?

best regards,

eyseman

---

### Post by rapido on 2006-08-28
Thought I would post a quick shot of the recent mod to the exterior of my Macbook pro.  I wanted make it clear which OS I am running ( or which I am not, depending on the perspective ).

[IMG]http://www.shiftingheat.com/images/p1000212_sm.jpg[/IMG]

As the photo shows, I created an adhesive, vinyl, Ubuntu logo that just "masks" out the Apple logo.  The center of the logo is cut out to allow the light to glow.

---

### Post by idn on 2006-08-28
Lol, i like the ubuntu sticker.

I have a problem though, I accidently installed typed "lilo -b /dev/sda4" instead of lilo "lilo -b /dev/sda" and now when I try to boot nothing works and I also get two penguin logos :(

---

### Post by frej on 2006-08-28
lilo -u /dev/sdaX should remove lilo from that partition.

---

### Post by perkypat on 2006-09-09
Hello,

I am trying to follow this guide but am stuck. When I type:

lilo -b /dev/sda

It says: command not found

What can I do about this????

PS: I am a bit of a noob i'm afraid...

---

### Post by mejy on 2006-09-10
I am using a MacBook Pro 15" which is already configured for dual boot.  Before I go for triple boot (I'm using parallels at the moment):

Is there any way I can non distructively shrink my windows partition (from 25gb to 15gb)?

Is it possible to revert to the bootcamp boot loader and my dual boot solution, and is it really necessary to use rEFIt?

Is there any chance of data loss on either of my partitions?

Does the rEFIt still look as [ugly as this]("http://refit.sourceforge.net/screen.html")? ;p

Looks like a very usefull how to, but I'm debating sticking with Ubuntu in parallels until a more supported solution comes out (using a beta boot menu on a beta boot solution using a partition setup not mentioned in the how to feels a bit risky).

Thanks in advance.

---

### Post by n00bWillingToLearn on 2006-09-11
> **auslander said:**
> I installed mouseemu and my trackpad is now disabled.  I had to do this:

 sudo /etc/init.d/mouseemu stop

to get it to work again.  This is the case with both a blank /etc/default/mouseemu file and with one that contains this (which I found somewhere else):

MID_CLICK="-middle 56 272" # Alt + mouse click = middle click
RIGHT_CLICK="-right 464 272" # Fn + mouse click = right click
SCROLL="-scroll 87" # F11 + mouse movement
TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress


I have a 15" 2.16GHz MBP.  has anyone got ctrl-click or anything else to get right-click to work?

thanks,

All I had to do was sudo apt-get remove mouseemu. Anyways, it looks like the gentoo people have it working on a macbook (non pro) without mouseemu from [http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Touchpad_in_X11](http://gentoo-wiki.com/HARDWARE_Apple_MacBook#Touchpad_in_X11)
But I have not yet tried that in Ubuntu, or on a macbook pro.

[Edit] Have been working on it but no success so far, probably not usefull :(

---

### Post by wild26 on 2006-09-15
I used BootCamp to partition my MacBook Pro HD, but instead of installing WinXP, I want to install ubuntu.

I have Dapper Drake on a disk, and as I go through the install steps, I run into a point where I can't go any further.

Where the directions say:
[INDENT]define mount :
if possible, do not mount /mount/EFI (select white item in list)
/dev/sda3 => swap
/dev/sda4 => /
[/INDENT]
I don't seem to have enough partitions, and I can't resize the 5G partition I created with BootCamp because the format isn't recognized. What do I do to continue with this install?

**UPDATE:** I have asked a couple IT people at my school for help on this too, and unfortunately they don't know Mac, just Linux. I tried something on my own, and now I have a stray, seemingly unusable 5GB space on my HD and no way to get it back. Any advice?

Thanks.

---

### Post by hajk on 2006-09-16
I guess you used Boot Camp Assistant to make a 5GB "Windows" partition? Once you start the Dapper installation from the liveCD it will soon ask about disk partitioning. Choose Manual Partitioning at this stage, which opens the GParted partitioning tool: there are three partitons visible, of which the third is the newly made "Windows" partition (it may be labeled "unknown partition"). You must delete this partition, thereby creating unallocated space instead. Then back up a few pages and this time choose to install Ubuntu in the largest unallocated space. From here on, the installer will take care of creating and formatting the partitions /dev/sda3 and /dev/sda4 for / and swap.

If still in doubt, have a look at my install notes (see sig) for the MacBook (not Pro), the procedure would be very similar. There's a note on reclaiming the whole HD for Mac OS X as well.

---

### Post by phico on 2006-09-16
> **wild26 said:**
> Any advice?

Thanks.

Look here, this is the best explanation about Macbook partitions 
you can find .. [http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp)
(Section : Disk Partitions and their Limitations )
Hope this help.  If you do not want multi-boot then you have to use Linux Efi but it will be more difficult for firmware updates..)

---

### Post by michaels on 2006-09-16
I follow this instruction to install xgl and compiz on my macbook pro(the package installed csm, cgwd and cgwd-theme), but the compiz doesn't work well. All the windows don't have title bar and can't be moved as well.

could some one tell me what's the problem for it? and how could I fix it?

---

### Post by bhalash on 2006-09-16
My problem seems to be slightly different from other people's in that Ubuntu won't boot at all. To work backwards from the problem, I installed Ubuntu and Windows, partitioning for a tri-boot. I had originally intended to install Gentoo, but time (a new baby) had me leaning towards Ubuntu instead - I had also intended to use reiserfs under Gentoo, so I reformatted the Linux partition. 

The installer ran perfectly, lilo was installed and configured on sda3 and I can mount the partition perfectly fine under the live CD. 

rEFIt resynchronized partitions after installation just fine and its menu Linux listed fine, but when I actually boot...black screen, nothing loads. 

Partitions are listed weirdly under both rEFIt and diskutil under OS X:

```
/dev/disk0
   #:                   type name               size      identifier
   0:  GUID_partition_scheme                    *74.5 GB  disk0
   1:                    EFI                    200.0 MB  disk0s1
   2:              Apple_HFS OSX                24.0 GB   disk0s2
   3:                    EFI                    25.0 GB   disk0s3
   4:   Microsoft Basic Data WINDOWS            25.2 GB   disk0s4
```

disk0s2 shows at just EFI under OS X and rEFIt shows the partition as being "Basic Data (FAT)". 

On the whole, I'm under the impression that the partition is somehow corrupt. Has anyone experienced this and would have an idea as to my options short of wiping everything again?

**EDIT:** Fixed this, it was a rEFIt problem.

---

### Post by ZERO_SHIFT on 2006-09-17
I was wondering if you could run the following on a macbook without the firmware as in istalling only ubuntu on your mac:

iSight
mighty mouse -wireless-

and what about xgl on macbook -not pro- is it possible??

thanks in advance

---

### Post by idn on 2006-09-17
I think you can run aiglx on a macbook (not pro) and so run compiz - i have aiglx running on my other machine and it works fine.

---

### Post by Roner on 2006-09-18
After setting up my iMac 20" with rEFIt triple-boot lilo, I was able to get grub to work under rEFIt. I am running Edgy, so I don't know if it would work with dapper, but it is worth a try.

After you have Ubuntu up and running, uninstall lilo, install and configure grub:
```

sudo dpkg --purge lilo
sudo apt-get install grub
sudo grub-install /dev/sda3
sudo update-grub
sudo vi /etc/grub/menu.lst

```

Here go to the automagic section, and make sure you change all the hd0,0 references to hd0,2; then make sure you change all the references to your Ubuntu partition from the elaborate location grub created to the simple /dev/sda3. You can also tweak grub's wait time and cancel the menu autohide.

When you are done, run once more
```

sudo update-grub

```

And now, upon rebooting and selecting the linux partition, grub should be up and running.

Let me know if it works in Dapper - I am thinking of going back to it.  It seems that the Edgy kernel will include evetually all of the Mactel patches (there are quite a few already there), but it is still not completely stable.

---

### Post by michaels on 2006-09-19
should I run the lilo command everytime my system has been update?

:D

---

### Post by phico on 2006-09-19
> **michaels said:**
> should I run the lilo command everytime my system has been update?

:D


If the kernel has changed, yes.

If you followed the instruction of this thread,
remember that lilo command for triple boot is 
different that for dual boot (dual boot put
lilo boot on mbr while for triple boot I put it on 
/dev/sda3)
If you make a mistake, you can still go back with
lilo -u command.

---

### Post by hajk on 2006-09-19
> **michaels said:**
> should I run the lilo command everytime my system has been update?

:D

That depends... if the /vmlinuz and /initrd symlinks (in the / directory) point to the updated kernel in the /boot directory, and if you use these symlinks in the /etc/lilo.conf file, then you don't need to reinstall lilo after a kernel update to a new (sub)version (like from 2.6.15-25 to 2.6.15-26). Kernel updates automatically change these symlinks to the latest version installed, so you really should use the symlinks...

Sometimes the kernel (sub)version stays the same when the update is just a change in Ubuntu-supplied patches. The same holds in that case.

Good luck!

---

### Post by jordiR on 2006-09-19
I have followed the Roner's howto to install grub and it doesn't work for me, when I try to execute grub-install I get this error:
The file /boot/grub/stage1 not read correctly.
I'm using Edgy.

---

### Post by ZERO_SHIFT on 2006-09-22
Will updates affect the Macbook Booting system, thus should we not update at all.

and is it possible to have the Macbook runnug on ubuntu ONLY??

Thanks

---

### Post by Seq on 2006-09-23
> **hajk said:**
> That depends... if the /vmlinuz and /initrd symlinks (in the / directory) point to the updated kernel in the /boot directory, and if you use these symlinks in the /etc/lilo.conf file, then you don't need to reinstall lilo after a kernel update to a new (sub)version (like from 2.6.15-25 to 2.6.15-26). Kernel updates automatically change these symlinks to the latest version installed, so you really should use the symlinks...

Sometimes the kernel (sub)version stays the same when the update is just a change in Ubuntu-supplied patches. The same holds in that case.

Good luck!

With Grub, this is true. lilo, however, does need to be updated when your kernel changes, symlinks or not. The symlinks make things much easier, as you do not need to update the configuration, just re-run lilo. This is why Grub rocks, I think.

The below quote is from the [LILO mini-HOWTO]("http://tldp.org/HOWTO/LILO-2.html") on TLDP. Emphasis mine:

> 
When Lilo boots the system, it uses BIOS calls to load the Linux kernel off the disk (IDE drive, floppy or whatever). Therefore, the kernel must live in some place that can be accessed by the bios.

**At boot time, Lilo is not able to read filesystem data, and any pathname you put in /etc/lilo.conf is resolved at installation time** (when you invoke /sbin/lilo). Installation time is when the program builds the tables that list which sectors are used by the files used to load the operating system. As a consequence, all of these files must live in a partition that can be accessed by the BIOS (the files are usually located in the /boot directory, this means that only the root partition of your Linux system needs to be accessed via the BIOS).

Another consequence of being BIOS-based is that you must reinstall the loader (i.e., you must reinvoke /sbin/lilo) any time you modify the Lilo setup. **Whenever you recompile your kernel and overwrite your old image you must reinstall Lilo**.


---

### Post by n00bWillingToLearn on 2006-09-24
> **ZERO_SHIFT said:**
> is it possible to have the Macbook runnug on ubuntu ONLY??

It is possible, but not recommended. Among other things, OS x is required for firmware updates. If you want, you can keep OS x installed on an external drive, then reformat your internal drive and use all of that space for Ubuntu. But **you should not get rid of OS x entirely, and you should keep your OS x recovery disks also.**

---

### Post by illmonkey on 2006-10-02
Hello I install Xubuntu on my macbook pro. I've some problems with sound, when i plug my headset the speakers don't mute and I don't have sound on my headset..

I follow these tips :

Grab the latest alsa dev release here [ftp://ftp.alsa-project.org/pub/drive....12rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/drive....12rc1.tar.bz2)

Unpack it somewhere.

in the alsa-driver-1.0.12rc1 folder run

./configure --with-cards=hda-intel --with-sequencer=yes

After it is done go to alsa-driver-1.0.12rc1/alsa-kernel/pci/hda and open up hda_codec.c and comment out lines 2135 and 2147 so it now looks like

//if (! cfg->line_outs) {
if (cfg->speaker_outs) {
cfg->line_outs = cfg->speaker_outs;
memcpy(cfg->line_out_pins, cfg->speaker_pins,
sizeof(cfg->speaker_pins));
cfg->speaker_outs = 0;
memset(cfg->speaker_pins, 0, sizeof(cfg->speaker_pins));
} else if (cfg->hp_pin) {
cfg->line_outs = 1;
cfg->line_out_pins[0] = cfg->hp_pin;
cfg->hp_pin = 0;
}
//}

Save the file and then go back to alsa-driver-1.0.12rc1.

Do a make;make install reboot and you should have sound from the speakers.

[COLOR="Red"]Problem is the headphone jack will not work (the line out toggle will but the speakers will not auto switch off when an input is plugged in). I will work on adding a check box toggle a little later, but I was eager to get my speakers working so someone else may be as eager as I was. Good luck![/COLOR]

Has some solve this problem?

Thank you!

---

### Post by krutoymuzhik on 2006-10-05
Hey guys im sorry for the n00b question, but im stuck at this point:

create /etc/lilo.conf
Add this content:
(with "vi" or Application>Accessories>Text Editor)
Code:

boot=/dev/sda4 default=Linux map=/boot/map delay=20 image=/vmlinuz initrd=/initrd.img root=/dev/sda4 label=Linux read-only

i am trying to search for help on the board but can't find anything.](*,)  How do i create this lilo.conf file? I did the step prior to install lilo and it went fine and d/led etc but just stuck on this part and i dont want to skip it. Any help would be great appreciated. 

Thanks

---

### Post by krutoymuzhik on 2006-10-08
Can no one help me at all? I have asked around diffrent places and no one seems to know. Like i stated above, i am trying to create the lilo.conf. I tryed Vi to know success and even opening gedit as sudo and trying to save it as a lilo.conf file in /etc but it just creates a folder instead. I would really like to get this to work, but im stuck at this time. I appreciate anything someone can give me.

Thanks

---

### Post by hajk on 2006-10-08
I recommend that you use the nano editor, which is much easier to use for a newcomer to Linux. So, in a terminal make sure that you are root (with the # prompt), then open the lilo.conf file with
```

# nano -w /etc/lilo.conf

```
and type the following lines in this file (assuming that your boot/root file is in /dev/sda4):
```

boot=/dev/sda4
default=Ubuntu

map=/boot/map
delay=20
root=/dev/sda4
read-only
compact

image=/vmlinuz
   initrd=/initrd.img
   append="quiet splash lpj=8000000"
   label=Ubuntu

```
Now save the file with Ctl-x, answer Y and hit Enter.

The lpj=8000000 option prevents a kernel panic due to the kernel BogoMips estimate turning out low -- you may have to increase it if you get kernel panics -- but is harmless otherwise. The label is just that, but make sure that it is the same for the default. 

Once you get a bit more experience with Linux, you may want to learn the vi editor -- it is very efficient and fast in use, but the learning curve is steep...

---

### Post by krutoymuzhik on 2006-10-10
> I recommend that you use the nano editor, which is much easier to use for a newcomer to Linux. So, in a terminal make sure that you are root (with the # prompt), then open the lilo.conf file with

Code:
# nano -w /etc/lilo.conf

Well the problem is I dont have a lilo.conf in /etc at all. I installed lilo like it explained in the instructions, but it did not create a lilo.conf. 

This is what im asking, because the instructions state "create" which to me means I must create the lilo.conf and place it in /etc. 

But from what I understand from your instructions is it should already be there?

If someone could clarify this to me that would be great. I appreciate all your help.

---

### Post by hajk on 2006-10-10
You would have had your answer if you had just followed the instruction -- nano (or any editor, for that matter) will create the file if it does not already exist! Neat, huh?

---

### Post by michaels on 2006-10-11
I'm a newbie to ubuntu and I intall ubuntu on my macbook pro following this how-to. However, my wireless card doesn't work. In fact, it worked once and after that it doesn't work any more. And When I open the Networking in the Adminstration, it says the wireless card is active.

Could somebody tell me how to configure it?

Thank you

---

### Post by krutoymuzhik on 2006-10-11
Well I got Ubuntu installed, and got Compiz/XGL running smoothly. Only thing I can find now that is out of ordinary, is when I launch to reFit it shows my OS X, and two Linux Pinguins. One of the linux ones work, the other doesn't. I know it has to do with something I screwed up during the install process because I went through it like 4 times. 

Other than that Hibernate doesn't work, it crashes the system. And my sound doesn't work, but I guess this is fixed by updating the kernel? Is that true with x86 imacs also?

Thanks for the help.

---

### Post by entangled on 2006-10-11
> **ZERO_SHIFT said:**
> Will updates affect the Macbook Booting system, thus should we not update at all.

and is it possible to have the Macbook runnug on ubuntu ONLY??

Thanks

Having tried multi-booting and parallels virtual machine on OSX, I found single booting ubuntu is best on my Mac mini (Macbook should be similar). It is easy to do and gives the least trouble. As far as I can see everything that worked under MacOSX also works under ubuntu (printing is even better) and I have only used 4 GB - despite pruning MacOSX it used 30 GB, but I never found out why it was so greedy.
My old MacOSX is on backup disk if ever I need a firmware update, but these are rare. I also run Windows under vmware server on ubuntu. It is free and works very well.

---

### Post by matt_granucci on 2006-10-14
Does anyone have info on fan control for a 15in Macbook pro? They seem to kick in when the system is already way to hot.

Thanks

---

### Post by The General on 2006-10-18
Hi! Great how-to! :)

I am having a problem booting Linux ... I am on a 15" Macbook Pro. ](*,) I followed the instructions exactly, and for some reason when I choose Linux in rEFIt, it seems to hang with a blank screen. I can't tell if the laptop is off or on, but I have to press the power button twice to get it to turn back on, so I'm thinking that it is on. I have this partition layout:

sda1 = 200MB EFI             ---
sda2 = 80GB Mac OS X         ---
sda3 = 2GB swap              swap
sda4 = 29GB ext3             /

Could the size differences be the problem? I don't know much about lilo but did I need to run liloconfig like it said when I apt-got it? :confused: Is there any way I can use GRUB on here? That would make it so much easier for me as I know GRUB really well. I don't want to screw anything up though, so I'll wait for a response. ;)

Thanks :(

---

### Post by Technoviking on 2006-10-20
> **Roner said:**
> After setting up my iMac 20" with rEFIt triple-boot lilo, I was able to get grub to work under rEFIt. I am running Edgy, so I don't know if it would work with dapper, but it is worth a try.

After you have Ubuntu up and running, uninstall lilo, install and configure grub:
```

sudo dpkg --purge lilo
sudo apt-get install grub
sudo grub-install /dev/sda3
sudo update-grub
sudo vi /etc/grub/menu.lst

```

Here go to the automagic section, and make sure you change all the hd0,0 references to hd0,2; then make sure you change all the references to your Ubuntu partition from the elaborate location grub created to the simple /dev/sda3. You can also tweak grub's wait time and cancel the menu autohide.

When you are done, run once more
```

sudo update-grub

```

And now, upon rebooting and selecting the linux partition, grub should be up and running.


When I do 
```
sudo apt-get install grub
```
I get the error
```
"The file /boot/grub/stage1 not read correctly"
```

any ideas?

---

### Post by mirroredfire on 2006-10-22
Im having some problems, ive decided to try this with kubuntu and it seems to all work until I get to this point:

the command im trying to put in is lilo -b /dev/sda

the prompt is root@ubuntu:/#

/etc/lilo.conf: No such file or directory

ive double checked and that file is DEFINATELY in the /etc folder

I don't see a penguin on rEFIt unless I get my cd in, and the legacy OS option pops up but just says no OS loaded.

I had to change things around a little bit, for one I have my main / set to sda2 and my swap set to sda3, I switched all the coding to reflect that though :hmm:

---

### Post by enj0y on 2006-10-24
I dont know if you noticed but someone wrote an OSX app which lets you set the minimum fan speed on your Macbook / Pro. You can get it here: [http://81.169.182.62/~eidac/software/page5/page5.html]("http://81.169.182.62/~eidac/software/page5/page5.html")
The source code is included, so maybe someone can check whether its easily portable to linux...?
greetings

---

### Post by Technoviking on 2006-10-27
Edgy installs on Macbook Pro fairly easily, still have to use lilo (grub has a problem with the stage1 file).

The only issue I'm having is get get the middle and right mouse buttons mapped to something.

[http://www.ubuntuforums.org/showthread.php?p=1674906](http://www.ubuntuforums.org/showthread.php?p=1674906)

---

### Post by bigbluevan on 2006-10-28
> **Mike said:**
> Edgy installs on Macbook Pro fairly easily, still have to use lilo (grub has a problem with the stage1 file).

The only issue I'm having is get get the middle and right mouse buttons mapped to something.

[http://www.ubuntuforums.org/showthread.php?p=1674906](http://www.ubuntuforums.org/showthread.php?p=1674906)

I did get synaptics driver working but then my hard drive corrupted (I recommend going with ext3 for the journaling not ext2..).  past couple days(after I've recovered from the crash) I've been trying to figure/remember exactly how I got it working.

when I try what I think I did a crash occurs(the crash seems to relate to fglrx) -- simply replace the CorePointer in xorg.conf with what is described here (I may have also changed the Protocol to event) -- someone feel free to try and confirm any of this since I did have it at least working at one point:
[http://wiki.debian.org/MacBookPro](http://wiki.debian.org/MacBookPro)
edit: I just tried to reproduce this but it didn't crash but it didn't get synaptics working either

Presently I'll get this error in /var/log/Xorg.log
```
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"
```

but based on my readings of synaptics, my synaptics driver isn't loading properly.  you can cat /proc/bus/input/devices and if it doesn't list the "SynPS/2 Synaptics TouchPad" or "AlpsPS/2 ALPS TouchPad" then according to the trouble shooting guide of synaptics something is wrong.  Mine just lists a bunch of Apple stuff.

Also, I recommend trying a newer kernel since it will have proper keyboard support (enables the fn as well as pgup/pgdown/home/end keys, etc) - tested and working in 2.6.18 and 2.6.18.1 (I never tested it with the kernel in the starting post.. ).. anyway....

---

### Post by ajslater on 2006-10-28
Grub works fine on edgy on my MBP 15"

I read somewhere that you have to force MB & MPB touchpads into 'raw' mode before the appletouch or xorg synaptics driver loads or it will just emulate  a usb mouse.

---

### Post by bigbluevan on 2006-10-28
I am happy to state I got the synaptics drivers working.  With only one caveat - if I restart X/kdm it doesn't detect the synaptics anymore, so I would need to reboot [I haven't tested this with suspend either which may or may not create problems].

My main source of help came from this post:
[http://www.jasonparekh.com/?page_id=9](http://www.jasonparekh.com/?page_id=9)

The only modification I had to make was that, in addition to what is posted at the above URL, I also needed to add "blacklist tsdev" to /etc/modprobe.d/appletouch
I realized that it was loading the ts0 device due to what it was saying in /proc/bus/input/devices, you need to make sure it only lists mouseX and eventX -- if it has tsX then it means you should blacklist it.

in response to the fan post earlier, there is this although I haven't had the chance to investigate it (and it may not apply to the mbp )
[http://www.jasonparekh.com/?p=11](http://www.jasonparekh.com/?p=11)

another patch he has on his site is for improving 2 finger scrolling, I haven't tested it but when I get the time, hopefully I can experiment:
[http://www.jasonparekh.com/?p=6](http://www.jasonparekh.com/?p=6)

note: the stuff on jason's site appears to be for the macbook not the macbook pro so it may not always apply

---

### Post by jasonparekh on 2006-10-28
> **bigbluevan said:**
> 
My main source of help came from this post:
[http://www.jasonparekh.com/?page_id=9](http://www.jasonparekh.com/?page_id=9)


Awesome, people are using my site :)

I added your suggestions with credit (hope you don't mind--if you do, I'll remove them), thanks!

I highly suggest the trackpad patch.  It smooths the mouse massively (at least for the MB) and allows for two finger detection even when the fingers are touching each other (no gap between fingers).  Also, the fan patch is useful for keeping the MB(P) cool.  Both of these patches should apply and work cleanly on the MBP, but please let me know if you run into issues.

jason

---

### Post by Gendo on 2006-10-30
.

---

### Post by Gendo on 2006-10-30
Just a heads up on the sound for the poster a while back that was looking for a change from me. The latest alsa release 1.0.13 looks to have everything fixed. [http://www.alsa-project.org](http://www.alsa-project.org) , speaker mute when the headphone is plugged in etc. Anyhow download it, compile the driver, lib, and utils packages. Reboot and then make sure to unmute all the channels. Works with Edgy. Good Luck.

---

### Post by Technoviking on 2006-10-30
Just as a warning, I'm going to move this thread to the Laptop area of the forum. The Apple PPC part of the forum is for PPC talk only.

I will leave a permanent re-direct. 

Mike

---

### Post by Technoviking on 2006-10-30
Does the trackpad patch not appear to work with a Macbook Pro.

> **jasonparekh said:**
> Awesome, people are using my site :)

I added your suggestions with credit (hope you don't mind--if you do, I'll remove them), thanks!

I highly suggest the trackpad patch.  It smooths the mouse massively (at least for the MB) and allows for two finger detection even when the fingers are touching each other (no gap between fingers).  Also, the fan patch is useful for keeping the MB(P) cool.  Both of these patches should apply and work cleanly on the MBP, but please let me know if you run into issues.

jason

---

### Post by frigaut on 2006-10-30
I confirm that I have had no success with the trackpad thing on a macbook pro.
synaptic does not detect a synaptic trackpad, even though appletouch is loaded before usbhid, and tsdev is blacklisted.

---

### Post by frigaut on 2006-10-30
> **Gendo said:**
> Just a heads up on the sound for the poster a while back that was looking for a change from me. The latest alsa release 1.0.13 looks to have everything fixed. [http://www.alsa-project.org](http://www.alsa-project.org) , speaker mute when the headphone is plugged in etc. Anyhow download it, compile the driver, lib, and utils packages. Reboot and then make sure to unmute all the channels. Works with Edgy. Good Luck.

hum...did all of that (drivers, libs, utils) using the latest 1.0.13 versions, and unmuted all channels, but no luck, still nothing on the speakers. darn.

just to confirm: I "made install" the drivers and just rebooted. I assume it's the same driver names and that the one that come with edgy and that I don't have to modprobe them?

Same for the libs and utils: I just compiled and installed them, but did nothing else. right?

---

### Post by bigbluevan on 2006-10-31
> **frigaut said:**
> I confirm that I have had no success with the trackpad thing on a macbook pro.
synaptic does not detect a synaptic trackpad, even though appletouch is loaded before usbhid, and tsdev is blacklisted.

Are you using 2.6.18?
[http://lxr.linux.no/source/drivers/usb/input/appletouch.c?v=2.6.18](http://lxr.linux.no/source/drivers/usb/input/appletouch.c?v=2.6.18)
you will most likely need to be running a minimum of 2.6.18, "Geyser 3" is what shows in my dmesg and it doesn't look like a mention of that wasn't added until 2.6.18 (refer to this [diff](http://lxr.linux.no/diff/drivers/usb/input/appletouch.c?v=2.6.18;diffval=2.6.17.13;diffvar=v)).

If the modules have been blacklisted properly, it should list "appletouch" instead of "Apple Computers blahblahtrackpad" in /proc/bus/input/devices

If you are running 2.6.18 and still having issues post the contents of the following:
/proc/bus/input/devices
/var/log/Xorg.0.log
dmesg
/etc/X11/xorg.conf
/etc/modules
/etc/modprobe.d/appletouch
that'd be just about everything needed to diagnose the problem


ALSA stuff:

I also haven't been able to get the sound working.
I followed the instructions here for compiling:
[http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+HD-audio+and+modem.&chip=ICH6%2C+ICH6M%2C+ICH7%2C+ESB2&module=hda-intel](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+HD-audio+and+modem.&chip=ICH6%2C+ICH6M%2C+ICH7%2C+ESB2&module=hda-intel)
I haven't had time to strongly investigate it but IIRC it wasn't compiling the sequencer module and I was receiving a variety of errors as a result of this.  it's been a low priority though but I will post details here if I get it.

---

### Post by ajslater on 2006-10-31
MBP 15" sound works with the 2.6.17 kernel and ALSA 1.0.13

MBP 15" sound also works out of the box with the latest edgy kernel,  2.6.17-10.33, due to recent backported patches.

You may have to check gnome-volume-properties->Switches->"Line In as Output"

If 2.6.18 doesn't work (cause of no Ubuntu patches), try compiling the latest ALSA module.

---

### Post by Technoviking on 2006-11-01
With Edgy, sound works with only headphone, even with the latest alsa driver.

This fix ([http://www.ubuntuforums.org/showpost.php?p=1269085&postcount=39](http://www.ubuntuforums.org/showpost.php?p=1269085&postcount=39)) fails under Edgy.

---

### Post by Stefan Daniel Schwarz on 2006-11-01
While this guide has been a very helpful resource (thanks a lot), it's mainly targetted at the MacBook Pro. As a non-Pro MacBook user, I've written a guide for the "ordinary" White and Black MacBooks. Some parts apply to MacBook Pros, too, for example how to use GRUB instead of LILO. That's why I'm adding a "shameless plug" right here.

[https://wiki.ubuntu.com/MacBook](https://wiki.ubuntu.com/MacBook)

I hope it's useful to all MacBook users, Pro or no! ;)

See ya! :cool:
-- StefanDanielSchwarz

---

### Post by idn on 2006-11-01
I have installed ubuntu ok, but I now wanted to install windows (to play games) :) 

If I install it will I loose my Ubuntu install like what happend with grub sometimes?

Also, how would I resize the mac os partition to make room for windows without messing up my linux partition?

Thanks!

---

### Post by el toro on 2006-11-01
I'm oh-so-close to having a synaptics-enabled appletouch Macbook--I think the only thing that's holding me back is not having the mousedev module available.  appletouch loads and all, and tap-to-click works fine, but I see no messages about the synaptics driver in my Xorg.0.log.  When I make menuconfig, there's no option to modularize mousedev, and modprobing it does no good.  How can I compile the mousedev module?  This is with vanilla 2.6.18.1 sources, patched with latest mactel.

---

### Post by bigbluevan on 2006-11-02
> **el toro said:**
> I'm oh-so-close to having a synaptics-enabled appletouch Macbook--I think the only thing that's holding me back is not having the mousedev module available.  appletouch loads and all, and tap-to-click works fine, but I see no messages about the synaptics driver in my Xorg.0.log.  When I make menuconfig, there's no option to modularize mousedev, and modprobing it does no good.  How can I compile the mousedev module?  This is with vanilla 2.6.18.1 sources, patched with latest mactel.

What does it actually say it is loading in the Xorg.0.log ?  I had the impression that mousedev is compiled in.. and it had generated an object file for me so I assumed it was going to be included in the make which is good enough for me.

---

### Post by Technoviking on 2006-11-02
The grub fix did not work for me on a Macbook Pro 15in 2.00Ghz. rEFIt list Ubuntu as a legecy OS and says missing OS when I try to load it.


> **Stefan Daniel Schwarz said:**
> While this guide has been a very helpful resource (thanks a lot), it's mainly targetted at the MacBook Pro. As a non-Pro MacBook user, I've written a guide for the "ordinary" White and Black MacBooks. Some parts apply to MacBook Pros, too, for example how to use GRUB instead of LILO. That's why I'm adding a "shameless plug" right here.

[https://wiki.ubuntu.com/MacBook](https://wiki.ubuntu.com/MacBook)

I hope it's useful to all MacBook users, Pro or no! ;)

See ya! :cool:
-- StefanDanielSchwarz

---

### Post by Stefan Daniel Schwarz on 2006-11-02
Hello Mike,

what's the output of "sudo parted /dev/sda print" and "sudo fdisk -l"?

This will show you what the GPT partition table contains, and what the MBR partition scheme mirrors.

I'll take a look at it to see what's wrong.

See ya,
-- sds

---

### Post by Seq on 2006-11-02
Alright, I think I found why Grub was not working. I happened to look at sda with cfdisk. When I installed, I must not have deleted the partition Bootcamp had created for me, and instead formatted it as ext3. It's type was listed as NTFS, I changed it to 83 ("Linux") and grub installs fine now.

I probably should have caught that earlier, but how often does one run cfdisk... :)

---

### Post by Technoviking on 2006-11-03
> **Stefan Daniel Schwarz said:**
> Hello Mike,

what's the output of "sudo parted /dev/sda print" and "sudo fdisk -l"?

This will show you what the GPT partition table contains, and what the MBR partition scheme mirrors.

I'll take a look at it to see what's wrong.


It looks like the rEFIt makes it a EFI from linux (83) when I sync.

Mike

---

### Post by Stefan Daniel Schwarz on 2006-11-03
> **Mike said:**
> It looks like the rEFIt makes it a EFI from linux (83) when I sync.

Yes, that's the problem, unfortunately rEFIt breaks GRUB by setting the Linux partition to the wrong type. That's why you have to fix it manually every time you sync (normally you'd only sync once - after the installation).

If you can get GRUB to drop you to the GRUB shell, use the command from my HOWTO. If GRUB doesn't show up at all, sfdisk will also work (but requires booting the Live CD again, which takes a while, that's why I chose the GRUB shell fix for my guide).

For example: "sudo sfdisk -c /dev/sda 3 83" will set /dev/sda3 to the Linux (83) partition type.

See ya
-- sds

---

### Post by Gendo on 2006-11-05
For those still having sound issues, make sure you compile the driver, lib, and then utils packages probably in that order. I compiled the driver package with only the sequencer so I ran

./configure --with-sequencer=yes

Then make sure for the utils and lib packages you set the prefix 

./configure --prefix=/usr

Otherwise the new libs and utils will go into /usr/local and not overwrite any old alsa files you may have.
So the process will go something like this

download all the files from below to a directory somewhere on your machine.

[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.13.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.13.tar.bz2)
[ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.13.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.13.tar.bz2)
[ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.13.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.13.tar.bz2)

cd <to the dir with the alsa13 files you downloaded>

tar xfvj alsa-driver-1.0.13.tar.bz2

tar xfvj alsa-lib-1.0.13.tar.bz2

tar xfvj alsa-utils-1.0.13.tar.bz2

cd alsa-driver-1.0.13

./configure --with-sequencer=yes
make
make install

cd ..

cd alsa-lib-1.0.13

./configure --prefix=/usr
make
make install

cd ..

cd alsa-utils-1.0.13

./configure --prefix=/usr
make
make install

If all this went well then reboot.

After reboot open a terminal and type 

alsamixer

Make sure at the type the version is printed as 1.0.13 and if it is go through to every channel in the console app and unmute them. If all goes well then you will have sound. If you try to unmute in the Gstreamer volume control I do not think it will work. Good luck!

---

### Post by Technoviking on 2006-11-05
The grub shell did not show up for me, thanks for the info.
> **Stefan Daniel Schwarz said:**
> Yes, that's the problem, unfortunately rEFIt breaks GRUB by setting the Linux partition to the wrong type. That's why you have to fix it manually every time you sync (normally you'd only sync once - after the installation).

If you can get GRUB to drop you to the GRUB shell, use the command from my HOWTO. If GRUB doesn't show up at all, sfdisk will also work (but requires booting the Live CD again, which takes a while, that's why I chose the GRUB shell fix for my guide).

For example: "sudo sfdisk -c /dev/sda 3 83" will set /dev/sda3 to the Linux (83) partition type.

See ya
-- sds

---

### Post by Technoviking on 2006-11-05
> **Stefan Daniel Schwarz said:**
> 
I hope it's useful to all MacBook users, Pro or no! ;)

Your iSight guide work great on Macbook Pros also.

One question, your guide work great for the right mouse button, how do i map the middle mouse button?

---

### Post by Technoviking on 2006-11-06
Sounds works perfect for me except for a microphone, internal or plug-in.

---

### Post by Mars Cydonia on 2006-11-06
I have a problem installing edgy on my MBP 17'.

I have downloaded Ubuntu Edgy 6.10 for x86 and booted from the cd without problems but when X start I can see no other then various lines and graphics glitch on my monitor.

I can hear the gnome startup sound but I have no way that Turn Off my MBP.

I have tried with Ubuntu 6.06 LTS and this work but I want to use latest Ubuntu version.

I have also tried with Kubuntu but I have the same problem, boot is ok but when X start I can see only many lines and graphic glitch.

Is there any ways to slove this issue?

Thanks

---

### Post by Stefan Daniel Schwarz on 2006-11-06
> **Mike said:**
> One question, your guide work great for the right mouse button, how do i map the middle mouse button?

Go to the step where it says "To enable mousekeys emulation, turn the lower Enter key into Right Mouse Button".

The way I set it up is "Pointer_Button3, Pointer_Button3, Pointer_Button2, Pointer_Button2" which means press lower Enter key for Right Mouse Button, press AltGr + lower Enter key for Middle Mouse Button.

If you don't have an AltGr key, change it to "Pointer_Button3, Pointer_Button2" which means press lower Enter key for Right Mouse Button, press Shift + lower Enter key for Middle Mouse Button.

I updated the guide accordingly.

See ya
-- sds

---

### Post by Stefan Daniel Schwarz on 2006-11-06
> **Mars Cydonia said:**
> I have a problem installing edgy on my MBP 17'.

I have downloaded Ubuntu Edgy 6.10 for x86 and booted from the cd without problems but when X start I can see no other then various lines and graphics glitch on my monitor.

I have tried with Ubuntu 6.06 LTS and this work but I want to use latest Ubuntu version.

Might be a firmware issue, the MacBook Pro (don't have one, can't verify it) has an ATI card, which may have 3D acceleration out of the box in Edgy. Since 3D acceleration only works with updated firmware and/or Boot Camp on MBP's, I recommend you start by making sure your system is up to date and Boot Camp has been installed properly. A wild guess, yes, but the only thing I can offer you now.

See ya
-- sds

---

### Post by Mars Cydonia on 2006-11-06
Thank You for your answer.
I have the latest firmware for my MBP 17 and BootCamp 1.1.2.

I have started installing rEFIt and booted from Ubuntu 6.10; I have also tried to select VGA and 1024x768 but I can't find a way to slove this trouble.

---

### Post by Stefan Daniel Schwarz on 2006-11-06
Quick note to tell you all that I've updated my guide how to install Ubuntu 6.10 "Edgy Eft" on a MacBook.

[https://wiki.ubuntu.com/MacBook](https://wiki.ubuntu.com/MacBook)

Since there have been problems with getting GRUB to work, I added a detailed work-around how to fix it by booting from the live CD and chroot'ing into the installed system to reinstall GRUB properly!

See ya
-- sds

---

### Post by phico on 2006-11-06
[B][COLOR="Red"]
Many of you have been contributing to this thread 
It would be great to put all those contributions together ! 
So I started a wiki page here : 

[http://wiki.ubuntu.com/MacBookPro](http://wiki.ubuntu.com/MacBookPro)[/COLOR]

It is still in draft but I hope we can get it better !
[/B]

---

### Post by phersotty on 2006-11-06
> **Stefan Daniel Schwarz said:**
> Hello Mike,

what's the output of "sudo parted /dev/sda print" and "sudo fdisk -l"?

This will show you what the GPT partition table contains, and what the MBR partition scheme mirrors.

I'll take a look at it to see what's wrong.

See ya,
-- sds

Hi I wandered over here from the MacBook thread.  The above advice identifies my problem.  My /dev/sda3 Starts and Ends on 1 with the message Partition 3 does not end on cylinder boundary.

**Correction:** I think Vista killed my partitions not Edgy.

---

### Post by phico on 2006-11-07
> **Stefan Daniel Schwarz said:**
> 
Since there have been problems with getting GRUB to work, I added a detailed work-around how to fix it by booting from the live CD and chroot'ing into the installed system to reinstall GRUB properly!


Thanks, I added a note and a link to your wiki page for people who want 
to install Grub

---

### Post by phico on 2006-11-09
:confused: :confused: :confused: 


I upgraded to 6.10 and I am :confused:  verry disappointed :confused:  about 
MacBook support in this new release ... :
- No Mactel-linux patches have been included ... 
- No specific Mactel packageds ?!? 
- No keyboard mapping .. ??  

By this thread, it seems though that a lot of people were 
interested in running Ubuntu on their MacBook Pro.  I know
there are many platforms to be supported and Ubuntu people
do their best .. 

May be shocking for some of you ... but you know, 
I discover the new version of InputRemapper on Windows platform.  
This has been written by one single person and ... with this
single tool now Windows supports screen and keyboard auto-light, 
keyboard mapping and fan control ! .... So I really think to 
switch back to my Windows-Cygwin platform and come back to Linux 
when Macbook hardware will be supported by some distrib 
out of the box ..   :-k :-k :-k

---

### Post by rupy on 2006-11-09
Can someone who knows a bit about macbooks/linux/alsa have a look at this thread pls, would really appreciate some help:
[http://ubuntuforums.org/showthread.php?p=1737903#post1737903](http://ubuntuforums.org/showthread.php?p=1737903#post1737903)

---

### Post by Garret Kelly on 2006-11-14
phico: The program you mention didn't come with Windows out-of-the box, yet you expect it of Ubuntu? I don't think you're being fair here. MBPs are (especially the new Core 2 Duos) fairly cutting-edge in terms of hardware; it's unfair to expect immediate support for all of the hardware.

That said, I'm using a new Core 2 Duo MacBook Pro. Has anyone made any advancements in terms of WiFi or sound for this model?

I've been using Edgy on it for a while now using only EFI support (no bootcamp), and I haven't had any problems yet. The only things which don't work perfectly are the sound and WiFi.

---

### Post by Technoviking on 2006-11-14
> **Garret Kelly said:**
> 
That said, I'm using a new Core 2 Duo MacBook Pro. Has anyone made any advancements in terms of WiFi or sound for this model?


What problem are you having with WiFi? It works fine for me, out of the box using either WEP or WPA2.

I have sound working now by upgrading to Alsa 1.0.13 by hand. The only thing I ca not get to work is a microphone, built-in or external.

---

### Post by diegoc on 2006-11-15
> **Garret Kelly said:**
> phico: The program you mention didn't come with Windows out-of-the box, yet you expect it of Ubuntu? I don't think you're being fair here. MBPs are (especially the new Core 2 Duos) fairly cutting-edge in terms of hardware; it's unfair to expect immediate support for all of the hardware.

That said, I'm using a new Core 2 Duo MacBook Pro. Has anyone made any advancements in terms of WiFi or sound for this model?

I've been using Edgy on it for a while now using only EFI support (no bootcamp), and I haven't had any problems yet. The only things which don't work perfectly are the sound and WiFi.

I'm using edgy on a Macbook pro C2D too... Had some problem with sound (could ear sound on headphones only). The solution was trivial:

-Open alsa mixer
-In perferences tag all tracks
-unmute the "side channel"
-select "line in as output"

you should ear sounds now.

Wifi is not working for me too... seems like madwifi is going to add support for our chipset in the future: [http://madwifi.org/ticket/1001](http://madwifi.org/ticket/1001)
I tried to load the windows driver for D-LINK DWA 645 (same chipset) with ndiswrapper but is not working form me (I'm using the 32Bit version of ubuntu)

Bye!

---

### Post by phico on 2006-11-16
> **Garret Kelly said:**
> phico: The program you mention didn't come with Windows out-of-the box, yet you expect it of Ubuntu? I don't think you're being fair here. MBPs are (especially the new Core 2 Duos) fairly cutting-edge in terms of hardware; it's unfair to expect immediate support for all of the hardware.

By out-of-the-box, I mean some way to intall it easily ...
I like Ubuntu but we have to be honest :
- on windows, bootcamp drivers + input remapper and you get a full support (1h ..)
- on ubuntu .. follow the thread here (1/2 day), and .. you 
do not get a full support ..

What I would expect is for example mactel-linux patches 
integrated in the kernel or a module .. (drivers for  
screen and keyboard light do exist but as 
a mactel patch ...)

Also, I have never been able to get internal microphone
working and the webcam driver is better on windows 
(with all my respect to drivers' developers.  They do
a great work but do not have the same support as bootcamp
developpers .. unfair !)

---

### Post by Garret Kelly on 2006-11-17
> **Mike said:**
> What problem are you having with WiFi? It works fine for me, out of the box using either WEP or WPA2.

Madwifi doesn't support the AR5008 yet.

dieogc: Didn't work for me. I'm going to build alsa headrev from svn and see if I can't get it going.

phico: I think Ubuntu's doing pretty well, considering that Apple/Atheros/ATi aren't providing any real support for the development of hardware support for the MBP. As for the backlight, have you tried the userland utils for controlling backlight and keyboard backlight? I'm having no problems with them. I believe they were linked from the wiki MacBookPro page.

--Garret

---

### Post by imrazor on 2006-11-17
I tried Ubuntu out on my MBP 15" Core Duo about 6 months ago, and was really disappointed by the fglrx driver. Has support for the Mobility Radeon X1600 improved at all? I got tired of pixellation and poor 2D/video acceleration and migrated Ubuntu to my desktop. Hopefully things have gotten better since last time I tried...

---

### Post by diegoc on 2006-11-18
> **Garret Kelly said:**
> Madwifi doesn't support the AR5008 yet.

dieogc: Didn't work for me. I'm going to build alsa headrev from svn and see if I can't get it going.

--Garret

**SOUND on MacBook Pro C2D (core 2 duo)**

I garret,
this is really strange, I tryied to reproduce it booting form the live cd and worked! I'll try to describe every single step...

Here it is what i did:

- Boot ubuntu Edgy from live cd
- Trying to play "ubuntu sax.ogg" from the examples contents does not output any sound
- From the volume icon on the right top of the screen, right-click and slect "Open volume control"
- From the volume control window menu select Edit/Preferences
- Activate the "Side" checkbox and close the window
- unmute side
- Select the Switches pane and select the "Line in as output" checkbox
- Play "ubuntu sax.ogg" again, it should work

Just to be sure we have the same hardware, here is the output of "sudo lspci -v" on my MBP :

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Unknown device 8384:7680
        Flags: bus master, fast devsel, latency 0, IRQ 209
        Memory at 90400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0
        Capabilities: [100] Virtual Channel
        Capabilities: [130] Unknown (5)

Still couldn't make the microphone to work!


**WIFI on MacBook Pro C2D (core 2 duo)**
I managed to get the wifi "working" too using ndiswrapper plus the windows driver for Dlink dwa 645 with ndiswrapper:

- Download the windows driver from: [http://support.dlink.com/products/view.asp?productid=DWA%2D645](http://support.dlink.com/products/view.asp?productid=DWA%2D645)
- Install ndiswrapper with "sudo apt-get install ndiswrapper-utils ndiswrapper-utils-1.8" (be sure to install utils-1.8)
- unzip the driver and cd into the decompressed folder
- execute "sudo ndiswrapper -i Driver/net5416.inf" to install the driver
- execute "sudo depmod -a" to rebuild modules dependencies
- execute "sudo modprobe ndiswrapper" to make the kernel load the driver
- execute "ndiswrapper -m" to make the module loaded at boot time
- Wifi should work now! (try "iwconfig wlan0" or use netowrk manager to confgure it)

refer to [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#ndiswrapper](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/connect-to-internet.html#ndiswrapper) for more in depth instructions on ndiswrapper

Hope this will help !

---

### Post by willnight on 2006-11-19
i am not able to get passed this stage:

[COLOR="Green"]# Click install on disk in Ubuntu

# Choose a manual partition : (2Gb of swap and the rest for filesystem)
do not erase efi 200M partition
[COLOR="Black"]am i supposed to see partition for swap? all i see is sda3 that's reserved for linux, and it's locked from 'swapon /mnt/linux/swap' (?)[/COLOR]

For triple boot
# define mount :
    * /dev/sda3 => /
Triple boot uses a swap file
[COLOR="Black"]when i did this, without choosing a swap partition because there isn't one, the installation failed with an error.[/COLOR][/COLOR]

any idea please. i'm ready to give up.

---

### Post by Garret Kelly on 2006-11-23
Hi diegoc,
Right you were. I was attempting to get sound working in a busy lab and didn't hear the sound being played, but it does work.

Has anyone else tried using 2.6.19-rc5 or higher? I tried using the low-latency desktop scheduler, but my mbp makes an incredibly strange whining noise while it's running. The sound itself doesn't sound like it's coming from the speakers, but from around the left side of the keyboard. I'm trying to figure out which module is responsbile. I'm casting awkward glances at the PC speaker module. :P

Also, has anyone had any success getting the mbp to sleep?

--Garret

---

### Post by idn on 2006-11-23
I hope the microphone is fixed soon, its a bit annoying to have to boot into mac osx to use skype or gizmo :(

---

### Post by styllerone on 2006-11-25
hello i have just both a new macbook pro 15"  core 2 duo 
and i have made a triple boot  OS X /UBUNTU/ Windows

but rigth now i'm fithing with wireless on ubuntu 
i tried to do as you say . 
i  download dwa645 dlink drivers  and install it with ndiwraper 
just following your waht you said .
when i finish to install i launched nm-applet and it recognize my wireless network and some other around . but i didn't try to connect to it . i just restart my computer ( that's because of windows habits) . 
and now  i got " No network device found" on the nm-applet .
so i tried to reinstall it once again .. but same message  can't get it to work again .. why did  i restart ...? **** ..
please ubuntu people help ..

---

### Post by willnight on 2006-11-25
i followed the directions verbatim (the following steps):

<*******code*******>
# For triple boot, make a swap file because of partion number limit explained
on [http://wiki.onmac.net/index.php/Trip...t_via_BootCamp](http://wiki.onmac.net/index.php/Trip...t_via_BootCamp)
Open a terminal. (Application>Accessories>Terminal)
Quote:
sudo su
mkdir /mnt/linux
mount -t ext3 /dev/sda3 /mnt/linux
sudo dd if=/dev/zero of=/mnt/linux/swap bs=1024 count=2097152
mkswap /mnt/linux/swap
swapon /mnt/linux/swap

# Click install on disk in Ubuntu
# Choose a manual partition : (2Gb of swap and the rest for filesystem)
do not erase efi 200M partition
# define mount :

    * if possible, do not mount /mount/EFI (select white item in list)
    * /dev/sda3 => swap
    * /dev/sda4 => /



For triple boot
# define mount :

    * /dev/sda3 => /

Triple boot uses a swap file
<*******end code*******>

according to this logic, sda3 is locked as it is seen in parted during partitioning step. i cannot touch that volume while swapon is active. so how the h3ll do i install then?! what am i missing?

also what does this mean int the code: "(2Gb of swap and the rest for filesystem)"? i thought swap was already set up?

heeeeelllllpppppppp!

---

### Post by fonkypij on 2006-11-26
Hello,

To the author of this thread,

Please pay attention that where editing /etc/lilo.conf,

**[COLOR="Red"]you must absolutely provide a correct map=/boot/System.map option instead of map=/boot/map[/COLOR]** like I can read right now.

Then lilo -b /dev/sda3 will become possible without any error.

The lilo -P ignore thing as well as the lilo -P fix (on other sites) are fake advices.

Regards.

---

### Post by Romu on 2006-11-27
Hi all,
I would like to know if some of us have got some success while compiling the MacBook-Tools to manage keyboard and screen backlight  on Edgy :
[http://www.boichat.ch/nicolas/macbook-tools/](http://www.boichat.ch/nicolas/macbook-tools/)

When I try, I always get : pci.h not found of something like this.

And my Linux headers are well installed.

---

### Post by phico on 2006-11-28
> **Romu said:**
> Hi all,
I would like to know if some of us have got some success while compiling the MacBook-Tools to manage keyboard and screen backlight  on Edgy :
[http://www.boichat.ch/nicolas/macbook-tools/](http://www.boichat.ch/nicolas/macbook-tools/)

When I try, I always get : pci.h not found of something like this.

And my Linux headers are well installed.

Did you try :

sudo apt-get install pciutils-dev

as written above ?

---

### Post by Romu on 2006-11-28
> **phico said:**
> Did you try :

sudo apt-get install pciutils-dev

as written above ?

No, but I will ASAP. Thanks a lot, I didn't see.

---

### Post by Romu on 2006-11-28
Great this works pretty well.

But you also give the link :
[Macbook backlight]("http://ubuntuforums.org/showthread.php?t=215801")

To manage the backlight with the keyboard, but it's a completely different way than the previous solution isn't it ?

For me it doesn't work, I always get a message like "unexpected maximum value". But the source web site really specifies this doesn't work on MacbookPro.

So this should be removed from the tutorial or have I missed something?

---

### Post by Romu on 2006-11-29
I found a very simple way to control the screen backlight through the keyboard.

The solution is to use gconf-editor and to bind some metacity commands apps->metacity -> global_keybindings / keybindings_commands

Just DON'T do this with sudo because then you'll assign key bindings for the root user. You can with this tips even think about controlling the keyboard backlight with some shortcuts. But as the command is an absolute value (between 0 - off, and 255 - max), I think it's quite difficult to set a real control.

---

### Post by Novo on 2006-12-02
This is a more detailed way of mapping backlight to FN + F1:

First, install the applesmc and backlight from the initial post, and then...

Go into terminal:

[PHP]
nano ~/.xmodmap
  add to file:
    keycode 67 = F13
    keycode 68 = F14

gconf-editor
  go to:
    /app/metacity/global_keybindings
      edit run_command_1 and set to "F13"
      edit run_command_2 and set to "F14"
  go to:
    /app/metacity/keybinding_commands
      edit command_1 and set to "backlight -10"
      edit command_2 and set to "backlight +10"
[/PHP]

---

### Post by fonkypij on 2006-12-04
Hi guys, 

I'm now trying to add some Parallel Desktop stuff in here...

I'd like to be able to run my boot camped XP from OSX with this VM instead of rebooting.

That would be interesting as you probably aren't this happy about relooping the whole factory just to run Visual Studio 05 or even Counter Strike Source.

But is that truly possible?

I mean... Why not? Considering that you can flawlessly mount the NT filesystem from OSX (which means XP is quite visible), what's the matter with booting from this partition like any VM (VMware or even this "thing" called MS Virtual PC) can do... 

Well, i tryed... I couldn't achieve success yet. First I thought about rEFIt... But it's just a boot manager... It does not wipe out Boot Camp, so there're theorically no problem... So what the heck? I must say I don't know either if Parallel Tools really did install when required on XP. It's an highly critically required tool required to run the virtualization process... And it looks like there are issues with the msi installer too.

That would be quite annoying (who said stupid) to install another XP just after getting through this triple boot tutorial.

Could someone in here make some further investigation?

---

### Post by diegoc on 2006-12-05
> **Novo said:**
> This is a more detailed way of mapping backlight to FN + F1:



Did anybody manage to make Fn work under the new MacBook Pro C2D (Core 2 duo)?

Using Xev I see the keycodes of F1,F2 and so on doesn't change if I press them with or without Fn pressed !

---

### Post by idn on 2006-12-08
Does anyone know how to resize the mac osx partition to make it smaller (from 50GB to 25 GB), and the ubuntu one bigger?

I never use max osx and could do with the extra space on my ubuntu partition. Thanks!

---

### Post by Nasiom on 2006-12-14
](*,) 

Hello World,

I've been trying and reading and trying and reading more ](*,) to get the ATI drivers working in a MacBook Pro 15" (2Ghz) with absolutely no luck at all.

I've followed instructions here and on the wiki.unbuntu.com/MacBookPro page. I get no compilation error but as soon as I reboot I get a serie of blue pixels accross the screen when it reaches about 95-98% of loading (horizontaly - right under the ubuntu progress bar) and then a flickering green one appears?

If I boot in recovery mode and restore xorg.conf from the backup and reboot , everything is fine but of course I'm stuck at 1024x768 with no acceleration at all...

I've also gone and download the latest drivers from ati-amd and redone the whole exercise (compile-install-configure...) and still!

Has anybody succeeded in making this work?

Thanks,
:-k

---

### Post by haller on 2006-12-14
Hi. 
I know maybe this has been described a few times, but i want to tell what i had to do on **FEISTY.**

```

sudo apt-get install xorg-driver-fglrx

sudo aticonfig --initial
```

If you would restart X now, the resolution would be nice, but to get 3D working, i got to add this to /etc/X11/xorg.conf:

Section "Extensions"
Option "Composite" "Disable"
EndSection

Now to see if the wheels are spinning (smoothly):

```
glxgears
```
If you want to adjust colors or switch screen modi:
```
fglrx-control
```

Regarding Feisty i can say that it seems pretty stable at the moment. Keyboard works without touching one config-file (just use System>Settings>Keyboard), except the Apple-Key, suspend works,
Wireless and Keyboard-backlight do not work and the screen-backlight is not adjustable  at the moment, but i did not really try since would like to do things feisty-natively.
 
One bad thing is that the battery runs out fast (1h40 maybe). Maybe its because of the screen brightness. Or maybe its because of wireless or bluetooth? - I cannot use these yet and i dont know if they are on. And i dont know how i could turn them off. 

bye,
 andi

i am using a mbp core 2 duo.

---

### Post by Nasiom on 2006-12-15
:KS  Answering the question about X1600 support in 6.10 edgy

When downloading the drivers from the ati-amd site, make sure you download the Radeon Mobility X1600 drivers as opposed to the Radeon X1600 as per all the posts here are pointing to.!

Now everything is fine but audio and built-in isight camera. (but this is secondary to me)

MacBook Pro 2Ghz - 1GB ram - ATI Radeon Mobility X1600
Mac OS X 10.4.8 , Windows XP SP2 and Ubuntu 6.10 Edgy

Cool triple boot machine now!

:mrgreen:

---

### Post by ramvi on 2006-12-15
So everybody got the dual-screen going? Doesnt work for me... Anyone know what to do? My second monitor just doesnt find it

---

### Post by jharuska on 2006-12-21
> **ramvi said:**
> So everybody got the dual-screen going? Doesnt work for me... Anyone know what to do? My second monitor just doesnt find it

Yes, I have it working. This might help:

[http://ubuntuforums.org/showthread.php?t=301941](http://ubuntuforums.org/showthread.php?t=301941)

---

### Post by dpope on 2006-12-23
> **Mike said:**
> What problem are you having with WiFi? It works fine for me, out of the box using either WEP or WPA2.

I have sound working now by upgrading to Alsa 1.0.13 by hand. The only thing I ca not get to work is a microphone, built-in or external.

I'm glad to see somebody has a mostly working system.  Several things didn't work for me out-of-the-box on kubuntu edgy.  I'm currently trying to get sound, wireless and the trackpad to work well on a new MBP C2D.  I'm planning to install kernel  2.6.18.6 with the mactel patches since several things, including the synaptic driver for the trackpad seem to need a new kernel.  I tried manually downloading and installing alsa 1.0.13 and it still didn't fix my sound problem.   What exactly did you do?  I just did config, make, make install etc... and i assumed it would replace the existing alsa install and be started at boot time but I'm not even sure how to check if this works. 

When I run alsamixer I get:

~$ sudo alsamixer
Password:

alsamixer: function snd_ctl_open failed for default: No such device

Any idea why?  

Very few people here discuss upgrading the kernel or using the mactel patches.  Why doesn't someone just build a 2.6.18 kernel with the mactel patches and post it up in some ubuntu repository?  Even just providing a config file compatible with everything else in Ubuntu would be nice.

---

### Post by dpope on 2006-12-23
The Wiki at:

[https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro)

Claims HFS+ volumes can only be read from (accessed in read-only mode) but I found an old kernel post 

[http://uwsg.iu.edu/hypermail/linux/kernel/0305.0/1603.html](http://uwsg.iu.edu/hypermail/linux/kernel/0305.0/1603.html)

from 2003 claiming linux has read/write access to HFS+.  Also the hfs.txt file in the kernel Documentation/filesystems/ directory suggests that writing is possible.  Can anyone explain this discrepancy?  Is it safe to mount the OS X partition read/write?

thanks

---

### Post by fonkypij on 2007-01-07
> **dpope said:**
> I'm glad to see somebody has a mostly working system.  Several things didn't work for me out-of-the-box on kubuntu edgy.  I'm currently trying to get sound, wireless and the trackpad to work well on a new MBP C2D.  I'm planning to install kernel  2.6.18.6 with the mactel patches since several things, including the synaptic driver for the trackpad seem to need a new kernel.  I tried manually downloading and installing alsa 1.0.13 and it still didn't fix my sound problem.   What exactly did you do?  I just did config, make, make install etc... and i assumed it would replace the existing alsa install and be started at boot time but I'm not even sure how to check if this works. 

When I run alsamixer I get:

~$ sudo alsamixer
Password:

alsamixer: function snd_ctl_open failed for default: No such device

Any idea why?  

Very few people here discuss upgrading the kernel or using the mactel patches.  Why doesn't someone just build a 2.6.18 kernel with the mactel patches and post it up in some ubuntu repository?  Even just providing a config file compatible with everything else in Ubuntu would be nice.

Actually, i've been through the exact same sound problem. I've been trying to get rid of it during 2days (I'm not even talking about nights). 

I ended up installing latest kernel source with mactel **.config**, plus **reinstalling all alsa related packages** (including repository default ubuntu kernel ones) with synaptic (as compiling latest sources didn't help me neither at all), and this solved my problems :)

By the way, still no wireless... Sounds like the latest MBP revisions of the Atheros chip aren't supported for the moment. Even though mactel patches provides you to modprobe the new ath_pci, there are no wireless interface available. I'm waiting for you madwifi guys.

Well i've finally got something quite good with my beryl-svn enabled ubuntu.

Oh yes, about building a ready-to-go kernel... This isn't really necessary. It's just all about getting the corresponding .config and doing a make oldconfig in order to use it properly. Then multithreaded compiling with make -j4 , make install, make modules_install as usual. sudo lilo will do the trick then. 'voilà'

Hope this helps.

PS : Do you know **Desktop Manager** all? It's a Virtual Desktop Manager that provides you... Virtual Desktops (huh huh). 

But the important part is that... There's a hack that allows you using the hdd sensors in order to change the working desktop. 

For those who don't know it, the MBP is equiped with a security sensor that detects whether you're shaking (that's weird I know) the notebook or not. It's all about protecting your hdd from bumps in fact... 

With this hack called "**Smackbook**", I can **rotate my OS X cube (Desktop Manager provides XGL-like special effects)** with just smacking the side of my MBP.

Really funny :)

More details at : [http://squarejelly.blogspot.com/]("http://squarejelly.blogspot.com/") with a superb all-in-one package.

---

### Post by Oddi on 2007-01-09
Hello 

Im a noob in Linux...

I have instaled win xp, but im having trouble installing ubuntu. I follow the tutorial on this thread. 

But when im in step 5 (in install) I get an error: No root file system Invalid mount point

My mount point is : /dev/sda3 => /

please help

---

### Post by str00mff on 2007-01-14
Ok, I followed your instruction : at reboot I could heard some ubuntu stop sounds, but after reboot and login there was no sound & the sound controller of gnome was down. So I try alsamixer and it return me this error : 

alsamixer: function snd_ctl_open failed for default: No such device

I don't understand why. If any of you have an ide, it will be great ! :)

> **Gendo said:**
> Well I figured out a way to get sound working out of the speakers on the 15 incher. It is not elegant at the moment but if you are dying to have sound from the speakers like I was here is a quick hack until the alsa guys can fix it. 

Grab the latest alsa dev release here [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.12rc1.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.12rc1.tar.bz2)

Unpack it somewhere.

in the alsa-driver-1.0.12rc1 folder run

./configure --with-cards=hda-intel --with-sequencer=yes

After it is done go to alsa-driver-1.0.12rc1/alsa-kernel/pci/hda and open up hda_codec.c and comment out lines 2135 and 2147 so it now looks like

	//if (! cfg->line_outs) {
		if (cfg->speaker_outs) {
			cfg->line_outs = cfg->speaker_outs;
			memcpy(cfg->line_out_pins, cfg->speaker_pins,
			       sizeof(cfg->speaker_pins));
			cfg->speaker_outs = 0;
			memset(cfg->speaker_pins, 0, sizeof(cfg->speaker_pins));
		} else if (cfg->hp_pin) {
			cfg->line_outs = 1;
			cfg->line_out_pins[0] = cfg->hp_pin;
			cfg->hp_pin = 0;
		}
	//}

Save the file and then go back to alsa-driver-1.0.12rc1.

Do a make;make install reboot and you should have sound from the speakers. Problem is the headphone jack will not work (the line out toggle will but the speakers will not auto switch off when an input is plugged in). I will work on adding a check box toggle a little later, but I was eager to get my speakers working so someone else may be as eager as I was. Good luck!

---

### Post by aganti on 2007-01-14
Hi,

I am using a 15'' Macbook pro. I tried installing Ubuntu and I am getting the following error. 

sudo diskutil resizeVolume disk0s2 65G
Password:
Started resizing on disk disk0s2 Ganti's HD
Verifying
Resizing Volume
76% ..
Resizing encountered error No space left on device (28) on disk disk0s2 Ganti's HD

I have used around 50GB in my disk and I have got an 80Gig hard drive.
Does anyone know what needs to be done here? Any help is greatly appreciated. 

Thanks,
Ashwin.

---

### Post by rossmurray on 2007-01-25
> **Oddi said:**
> Hello 

Im a noob in Linux...

I have instaled win xp, but im having trouble installing ubuntu. I follow the tutorial on this thread. 

But when im in step 5 (in install) I get an error: No root file system Invalid mount point

My mount point is : /dev/sda3 => /

please help

I'm also having this issue. I'm installing on a 17" iMac Intel Dual Core2.

I've attempted both terminal [mkfs thingamyjig's]("http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu") before attempting install and come up with this 'Invalid Mount Point' error.

Can anybody help?

---

### Post by tigerblue on 2007-01-26
> **dpope said:**
> The Wiki at:

[https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro)

Claims HFS+ volumes can only be read from (accessed in read-only mode) but I found an old kernel post 

[http://uwsg.iu.edu/hypermail/linux/kernel/0305.0/1603.html](http://uwsg.iu.edu/hypermail/linux/kernel/0305.0/1603.html)

from 2003 claiming linux has read/write access to HFS+.  Also the hfs.txt file in the kernel Documentation/filesystems/ directory suggests that writing is possible.  Can anyone explain this discrepancy?  Is it safe to mount the OS X partition read/write?

thanks

While it's technically possible to mount HFS+ partitions rw, it is inadvisable.  Many people have reported inexplicable drive corruption on their HFS+ partitions, sometimes recoverable, sometimes not.

If you don't have anything of value on your OSX partitions, and don't mind re-installing the OS, you *might* be okay using read-write support. Otherwise, I'd avoid it like the plague.

---

### Post by lordmule on 2007-02-01
> **Nasiom said:**
> :KS  Answering the question about X1600 support in 6.10 edgy

When downloading the drivers from the ati-amd site, make sure you download the Radeon Mobility X1600 drivers as opposed to the Radeon X1600 as per all the posts here are pointing to.!

Now everything is fine but audio and built-in isight camera. (but this is secondary to me)

MacBook Pro 2Ghz - 1GB ram - ATI Radeon Mobility X1600
Mac OS X 10.4.8 , Windows XP SP2 and Ubuntu 6.10 Edgy

Cool triple boot machine now!

:mrgreen:

ah very exciting! this may be why it wasnt working good enough!
I tried out the triple boot again when the newer bootcamp was released but was not able to get full 3D acceleration from the graphics card, more like 20-40%.

Are people willing to provide the following information if owning a 15" core duo MBP:

glxinfo
glxgears -printfps (for 15 seconds)
uname -a (for smp kernel or not)
cat /proc/cpuinfo (or simply your CPU clock speed)

I know glxgears aint the best benchmark but I was getting 2500fps when I tried a while back, that was slower than my 6 year old PC :confused: 

I would be very grateful to see such results.

---

### Post by HellSpawn on 2007-02-03
Well, I have installed Ubuntu 6.10 on my Macbook Pro IC2D, it was a great experience, I got almost everything working, even Beryl.... But now I want to get my whole HDD  back  for Mac OS X without having to reinstall the whole system. Anyone knows how to get rid of the partitions and back to the original size without losing any data??

Thanx for any help

---

### Post by leojiang on 2007-02-08
Hi Guys 


Can edgy  be installed in Macbookpro **the External 1394a HD** ?

Thanks

---

### Post by Pizzicatto on 2007-02-20
Hey!
I followed the "Ubuntu on MacBookPro" wiki (by the way it's really good, thanx!!!) and everything went really well!!! Afterwards I installled Beryl as this link describes [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FBeryl_.28ATI.29") and it worked right away!

Problems began today with the last beryl packages update... I installed them and when i rebooted and log in, everything seem to load ok, but just after loading beryl the desktop disappears and instead i got the whole screen white... :confused: ..

Any clue?!?

---

### Post by cocoia on 2007-02-24
Heya Pizzicatto, a lot of people are having this problem with Edgy and the latest Beryl. It's kind of broken. If you try the instructions at the beryl-forum;
[http://forum.beryl-project.org/viewtopic.php?f=36&t=4046&start=0]("http://forum.beryl-project.org/viewtopic.php?f=36&t=4046&start=0")L]

This worked for me, although Beryl's most recent packages aren't the most stable ones, naturally.

I got another problem of my own though;

I am kind of new to the whole kernel-patching thing, and I wanted to compile and install the new kernel (I wanted to go with 2.6.18) and mactel-patch it so my computer doesn't run at, well, 86 degrees ;) but I am kind of lost.

The latest mactel-patches on the mactel-wiki are for what version of the kernel? I have been 'brute-forcing' the problem lately, trying some mactel-patchsets with kernels, but none apply cleanly. What is the best choice, versionwise, to go for, and what is the easiest way to go about applying these patches so I can use the minimal-fan speed command?    I would sincerely appreciate some help on this matter.

Also, I have been incredibly stupid in applying pommed; I used the debian-package, and satisfied it's dependency of it's libdbus. Incredibly, it didn't completely violate the system, but after a downgrade, gnome loses keyboard input, and failsafe reports that settings-manager doesn't work properly - although in failsafe mode,  I do have keyboard input.    I embarked on this stupidity because it wouldn't build. 

Everyone, thanks a lot for the explanations and personal ways of getting everything to work! It's been great so far!

---

### Post by lordmule on 2007-02-25
> **lordmule said:**
> ah very exciting! this may be why it wasnt working good enough!
I tried out the triple boot again when the newer bootcamp was released but was not able to get full 3D acceleration from the graphics card, more like 20-40%.

Are people willing to provide the following information if owning a 15" core duo MBP:

glxinfo
glxgears -printfps (for 15 seconds)
uname -a (for smp kernel or not)
cat /proc/cpuinfo (or simply your CPU clock speed)

I know glxgears aint the best benchmark but I was getting 2500fps when I tried a while back, that was slower than my 6 year old PC :confused: 

I would be very grateful to see such results.

anyone willing to do this so I can get and idea about trying again?

---

### Post by cocoia on 2007-02-25
Ok, lord, here is my output. It's currently running VESA instead of FGLRX, but that will be sorted out soon (dbus stuff). It's shoddy, graphics-wise now, but I ran superb on FGLRX.

glxinfo
```
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample,
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
```

glxgears, 3 outputs, shoddy display
```
1714 frames in 5.0 seconds = 342.800 FPS
1679 frames in 5.0 seconds = 335.483 FPS
1680 frames in 5.0 seconds = 333.872 FPS
```

uname -a
```
Linux menzoberranzan 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux
```

cpuinfo
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2500  @ 2.00GHz
stepping        : 8
cpu MHz         : 2082.159
cache size      : 2048 KB
physical id     : 0
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 2359.29

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2500  @ 2.00GHz
stepping        : 8
cpu MHz         : 2082.159
cache size      : 2048 KB
physical id     : 1
siblings        : 1
core id         : 255
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc pni monitor vmx est tm2 xtpr
bogomips        : 3994.75

```


More soon with FGLRX.

---

### Post by lordmule on 2007-02-25
mostly what Ive got. I noticed generic SMP kernel awesome stuff. 

> It's shoddy, graphics-wise now, but I ran superb on FGLRX.

are you by any chance using the mobile fglrx driver. I dont really know how to verify this, maybe run fglrxinfo

cant wait to see your juicy results, im on the edge of my...

fell off :)

---

### Post by idn on 2007-03-01
hi i was wondering how would i configure lilo if i wanted to have linux two linux distrs instead of linux and windows? I managed to install both ok but when i update lilo the other one gets removed from the selected screen on boot.

They are both installed ok, its just i can never set up grub properly without messing up the otehr distro's grub  :)

---

### Post by Seq on 2007-03-02
> **idn said:**
> hi i was wondering how would i configure lilo if i wanted to have linux two linux distrs instead of linux and windows? I managed to install both ok but when i update lilo the other one gets removed from the selected screen on boot.

They are both installed ok, its just i can never set up grub properly without messing up the otehr distro's grub  :)

I personally prefer grub over lilo. But either way, what you want to do is configure them to install to their respective partitions instead of MBR (which Ubuntu defaults to). That way you can select between the two distros with Refit, instead of having to chain bootloaders.

---

### Post by Kelvin on 2007-03-13
Help please!   :confused: 

I see this question has been asked here but not yet answered and now I'm suffering from it too.

MacBook Pro 15" 2GHz CoreDuo

Following along with the wiki goes fine until partioning time where I am unable to assign / as a mount point for SDA3. Gparted shows it as a ext3 fromated partition.

I have used 2 seperate install disks with the same results. One disk has been used to perform a clean install on another machine already and so is unlikely to be bad.

running fdisk -l shows this line for W95 FAT32 under the system column for /dev/sda3. Does that mean it thinks sda3 is a FAT32-formated partition?

All suggestions are welcome. I'm hungry for a triple-boot MBP!

Thank you!

Kelvin

---

### Post by nspire on 2007-03-20
Well I had Ubuntu (6.0.1) installed nicely on my MBP 2.16ghz Core Duo and then i downloaded and installed all the updates recommended (238 of them, i believe) and then i was suggested to restart. so i shut down (instead of restart), boot up, try to load ubuntu and it just hangs, no matter what i boot with (CD or HD). if i try to boot back into ubuntu from the hd (it worked before i updated) it says no boot device found (or something of the sort). after that, it says to insert bootable device and press any key. i do so, but the keyboard is unresponsive so i have to restart.

anyone know what could've happened? what can i do to bring my ubuntu back and updated? thanks in advance!

---

### Post by koni2005 on 2007-04-01
Same Problem here - although I installed Kubuntu on an external USB drive - and it all worked (with problems) until I installed the recommended updates. No way to boot up either the Live CD / DVD or the USB drive via refit. WTF????

I did install GRUB onto the internal HD - maybe that was a mistake? How can I safely remove it without destroying my MBR - and thereby losing all my data and the well working OSX / XP Partitions...

Any Idea????

---

### Post by idn on 2007-04-03
> **nspire said:**
> Well I had Ubuntu (6.0.1) installed nicely on my MBP 2.16ghz Core Duo and then i downloaded and installed all the updates recommended (238 of them, i believe) and then i was suggested to restart. so i shut down (instead of restart), boot up, try to load ubuntu and it just hangs, no matter what i boot with (CD or HD). if i try to boot back into ubuntu from the hd (it worked before i updated) it says no boot device found (or something of the sort). after that, it says to insert bootable device and press any key. i do so, but the keyboard is unresponsive so i have to restart.

anyone know what could've happened? what can i do to bring my ubuntu back and updated? thanks in advance!

you need to reload lilo to get it to work with every kernel update. Basically you need to boot into the live CD and do the following:

```

sudo su
mkdir /mnt/ubuntu
mount /dev/sda4 /mnt/ubuntu/
mount -t proc none /mnt/ubuntu/proc
mount -o bind /dev /mnt/ubuntu/dev
chroot /mnt/ubuntu /bin/bash

(if you are dualbooting)
lilo -b /dev/sda
(Else, if triple booting)
 lilo -P ignore -b /dev/sda3

```

Where /dev/sda4 is the ubuntu partition, or sda3, whatever you installed it on basically

That should fix it :)

---

### Post by yannoo on 2007-04-11
Hello girls and guys, and thanks for this post (and the wiki) so far, it has helped me a great deal to understand the common problems bound to Ubuntu on MacBook Pro.

I am the new owner of a MacBook Pro (don't know which version) 15" 2.16GHz and got almost everything working without much work by using the Feisty Fawn (7.04) Beta alternate CD. I have a few questions though which I didn't see covered here:

1) how do you know the version of your MBP?
2) did anybody install Feisty Fawn Beta on a MBP already, and got the sound to work?
3) my wireless chip is an Atheros AR5418 802.11a/b/g/n, which seems to be different from what some of you have reported in version 3 of the MBP ( AR5008 ). Can I get this to work with the NDIS wrapper and the drivers mentionned for AR5008?

On a side note, I failed installing Ubuntu about 20 times before realising that the messages telling me that one or another .deb package was corrupt was actually true and that it was because I had, at some point, burnt the ISO image on a RW disk at a higher speed than mentioned on the disk itself. Apparently, that breaks the disk in a way that won't let you write a complete disc without corruption ever again. So if you have corruption reported in one package when you install, consider using a fresh disk, and burn at a low speed.

Another side note is that rEFIt needs its install directory on the Mac OS X partition to work properly, so don't erase that partition. If you do, reinstall everything, making sure to remove all partitions from the disk from Ubuntu Live before you start, and creating a new partition in Mac OS X (using the Utilities) because otherwise it asks on which volume you want to install Mac OS X and doesn't show any volume at all.

---

### Post by yannoo on 2007-04-13
> **yannoo said:**
> 
3) my wireless chip is an Atheros AR5418 802.11a/b/g/n, which seems to be different from what some of you have reported in version 3 of the MBP ( AR5008 ). Can I get this to work with the NDIS wrapper and the drivers mentionned for AR5008?


OK, tested succesfully the AR5418 on my MacBook Pro with Feisty Fawn by using ndiswrapper:
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndiswrapper-source
cd
mkdir drivers
cd drivers
wget <IBM-DriverFor5416-AsMentionedInThisThread>
tar zxvf <IBMDriver.tar.gz>
sudo ndiswrapper -i NET5416.INF
sudo vi /etc/modules <edit to add "ndiswrapper">
sudo modprobe ndiswrapper
sudo iwconfig

```

After this, I might have restarted X, not sure.

---

### Post by yannoo on 2007-04-17
I got the sound working by starting alsamixer and unmuting (pressing "M") for "Speaker". I guess it should have been done instinctively (still on Ubuntu Feisty Beta on MBP 15")

---

### Post by jnev on 2007-05-08
I'm having a problem with this... I installed it according to the guide up to the point where you reboot and synchronize the mbr. when I go into the partition manager all it says is that everything looks good and to press any button to continue. when I click on the linux icon in refit it just shows me a picture of a penguin and doesn't do anything.

please help, thanks.

---

### Post by yannoo on 2007-05-09
Did you read carefully my latest posts? I had more or less the same problem and it was because I didn't carefully write everything in OSX (with BootCamp) before rebooting. It seems like Refit is depending on your OSX partition, so if that one is wrong now, you might have to reinstall everything, starting with OSX.

---

### Post by makaira on 2007-06-28
Disregard post.

---

### Post by fotakis on 2007-09-12
Hello there,

I am trying to install Ubuntu on a Mac Book Pro 17" Intel Core 2 Duo, I am using the alternate Feisty install cd wich has the text install mode. After I select the Linux CD from the refit menu, my keyboard is frozen, and I can't even continue to the text install, has anyone experienced this, and do you know of any work arounds.

Thanks,
Fotis

---

### Post by mjukr on 2007-09-12
Are you able to connect an external USB keyboard?

---

### Post by fotakis on 2007-09-13
I haven't tried it yet and I will need to get a hold of an external usb keyboard :-)

---

### Post by Subversive_One on 2007-10-28
Hello All,

I am attempting to triple boot a Macbook Pro, 17".  Ultimately, I would like to have Leopard, Gutsy and Vista.

I've been trying to follow the tutorial above, with slight variations.  I'm starting with OSX 10.5, in lieu of 10.4.

In the Terminal, when I attempt to manually partition the drive:

[INDENT]diskutil resizeVolume disk0s2 85.5G "Linux" "Linux" 15G "MS-DOS FAT32" "Windows" 15G[/INDENT]

I get an error that tells me that Linux does not appear to be a valid disk format.  Clearly, this is something that has changed between tiger and leopard.

--

What is the best way to get leopard into a triple boot scenario?  Do I start with Tiger... then follow the triple boot instructions, then follow up with an upgrade install to Leopard?

Thanks a bunch

Subversive.

---

### Post by ferdostar on 2007-11-15
Thanks for the great post, it was very helpful on installing the Ubuntu on my Macbook

---

### Post by hardawayd on 2007-12-09
I am having some trouble. i had installed refit and gusty and everything was working fine until i installed Linux Mint. I am having trouble with where grub should be installed. I also installed on a another partition another copy of gusty to try to get grub to launch but it will not. Should i be installing it to the MBR? I now have four linux penguins showing up when i boot but none of them do anything after showing grub 2 launching. Do you know how i can get this cleaned up and working--please. I did not install bootcamp since i thought it was only needed for windows.

---

### Post by echo6 on 2008-01-05
> **Gendo said:**
> until the alsa guys can fix it.
Has this been fixed in any alsa release yet?

---

### Post by echo6 on 2008-01-08
I'm  unable to install the 7.11 ati-drivers due to the following error```
echo6@macbookpro:~$ ./ati-driver-installer-8.27.10-x86.run --buildpkg Ubuntu/gutsy
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.27.10......................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
./ati-installer.sh: 156: Syntax error: Bad substitution
Removing temporary directory: fglrx-install
```

---

### Post by echo6 on 2008-01-10
[http://www2.ati.com/drivers/linux/ati-driver-installer-7.11-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-7.11-x86.x86_64.run)

I got this installed ok.

---

### Post by phico on 2008-07-07
This thread beeing quite outdated .. I updated it with a
MacBook Pro 4 (Penryn) Ubuntu Single boot installation ..

A pure Ubuntu Apple machine without any mac os partition ...

---

### Post by Oscar Pradilla on 2008-07-07
can anyone please look at my post and help me? i'n getting frustrated bcause i have to get back to mac os. Can't find a solution


[http://ubuntuforums.org/showthread.php?t=850745&highlight=macbook+pro](http://ubuntuforums.org/showthread.php?t=850745&highlight=macbook+pro)

---

### Post by Pederm on 2008-07-22
**Perfect !!**
This is just what I need to install a proper OS on my MacBook Pro (Penryn) ! 
Apart from installing also Windows XP and keeping a small scrapped version of Leopard for firmware updates I'll follow the instructions here accurately and let you guys know how that goes ...

---

