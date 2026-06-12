---
title: "Xubuntu Feisty on the Fujitsu ST5032D tablet"
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by bcw on 2007-08-01
Install Xubuntu Feisty, install updates

**Suspend and Hibernate**
...work immediately, except that the backlight does not turn on.  Edit '/etc/default/acpi-support' and make this change:
```
SAVE_VIDEO_PCI_STATE=true
```

**Display and Stylus**
install xvkbd, wacom-tools, & setserial
```
sudo aptitude install xvkbd wacom-tools setserial
```

[http://ubuntuforums.org/showthread.php?p=612960](http://ubuntuforums.org/showthread.php?p=612960)
[http://calkinsc.home.comcast.net/fujitsu_st_4000.html](http://calkinsc.home.comcast.net/fujitsu_st_4000.html)
Xorg installed xorg.conf with wacom entries, but I had to change "/dev/input/wacom" to "/dev/ttyS0", and I had to install 'setserial' with this entry in /etc/serial.conf to configure the digitizer's parameters:
```
/dev/ttyS0 port 0x0220 irq 4 autoconfigure
```

As root, make these changes to the default '/etc/X11/xorg.conf':
```

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	**"/dev/ttyS0"**
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	**"/dev/ttyS0"**
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	**"/dev/ttyS0"**
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

```
...and I added this to tweak font settings so Thunar (et al) matches xfce settings:
```
echo "Xft.dpi: 106" >> ~/.Xresources
```

**Screen Rotation**
xrandr rotates the display on the fly, but does not also re-orient the wacom input.  I  use this script (adapted from [http://www.germane-software.com/~ser/Files/Reviews/HP4200/rotate):](http://www.germane-software.com/~ser/Files/Reviews/HP4200/rotate):)
```

#!/bin/sh
# rotate_display.sh
# Use xrandr & xsetwacom to rotate the display and digitiser

x_min=0
x_max=24700
y_min=0
y_max=18520

#function ROTATE() {
ROTATE() {
  curr=`xrandr | awk '/Current rotation/ { print $4 }'`
  case $curr in
    normal)
      CW
      ;;
    *)
      NORMAL
      ;;
  esac
}


#function PORTRAIT() {
PORTRAIT() {
  #xsetwacom set eraser	BottomX	$x_max
  #xsetwacom set eraser	BottomY	$y_max
  echo portrait
}


#function LANDSCAPE() {
LANDSCAPE() {
  #xsetwacom set eraser	BottomX	$y_max
  #xsetwacom set eraser	BottomY	$x_max
  echo landscape
}


#function NORMAL() {
NORMAL() {
  xrandr -o normal
  xsetwacom set stylus  Rotate NONE
  xsetwacom set eraser  Rotate NONE
  PORTRAIT
}


#function CCW() {
CCW() {
  xrandr -o left
  xsetwacom set stylus 	Rotate CCW
  xsetwacom set eraser 	Rotate CCW
  LANDSCAPE
}


#function CW() {
CW() {
  xrandr -o right
  xsetwacom set stylus 	Rotate CW
  xsetwacom set eraser 	Rotate CW
  LANDSCAPE
}


case $1 in
  -l)
    CCW
    ;;
  -r)
    CW
    ;;
  -n)
    NORMAL
    ;;
  *) 
    ROTATE
    ;;
esac

```

**Stylus text input - Xstroke**
[http://ubuntuforums.org/showthread.php?t=69476&highlight=xstroke](http://ubuntuforums.org/showthread.php?t=69476&highlight=xstroke)
I installed xstroke from the package found in the ubuntu forum:
```
aptitude install xstroke_0.6.cvs20040921-2_i386.deb
```

**Stylus text input - XVkbd**
Edit '/etc/X11/app-defaults/XVkbd' to include the second line to provide a Fitaly keyboard layout (very efficient with practice - who cares about qwerty with a stylus?):
```

#include "XVkbd-common"
#include "XVkbd-fitaly"

```

I also changed the default 'fitaly' layout to get me access to the punctuation keys for programming.  Note that while there are arrow key symbols, I can't get those to shift properly, so I use U(p), D(own), L(eft), R(ight) for key symbols.  Shifting these gets H(ome), E(end), P(age)u(p), P(age)d(own):
```
!! Bret's tweaked fitaly layout to provide punctuation keys
!! XVkbd-fitaly.ad  - sample app-defaults file for xvkbd
!! by Tom Sato <VEF00200@nifty.ne.jp>, http://homepage3.nifty.com/tsato/
!!
!! with contribution from Marshall Rose
!!
!! Last update: 2003-06-23

#include "XVkbd-common"

xvkbd.title: xvkbd - Virtual Keyboard (Bret's Style)

xvkbd.compact: true
xvkbd.form*Repeater.shadowWidth: 1
xvkbd.form*Command.shadowWidth: 1
xvkbd.form*Repeater.height: 28
xvkbd.form*Command.height: 28
xvkbd.form*Repeater.width: 22
xvkbd.form*row0*Repeater.width: 22
xvkbd.Form*F5.horizDistance: 0
xvkbd.Form*F9.horizDistance: 0
xvkbd.form*Command.width: 66
xvkbd.form*Escape.width: 44
xvkbd.form*Tab.width: 35
xvkbd.form*row1.BackSpace.horizDistance: 0
xvkbd.form*BackSpace.width: 35
xvkbd.form*Delete.width: 31
xvkbd.form*Return.width: 66
xvkbd.form*space.width: 66
xvkbd.form*Alt_L.width: 35
xvkbd.form*Control_L.width: 66
xvkbd.form*Caps_Lock.width: 31
xvkbd.form*MainMenu.width: 31
xvkbd.form*MainMenu.height: 28

xvkbd.NormalKeys: \
  F1 F2 F3 F4 F5 F6 F7 F8 F9 F10 F11 F12 BackSpace \n\
  Escape ` \\ z v c h w k ; 1 2 BackSpace Delete \n\
  Caps_Lock Tab ' f i t a l y , 3 4 Return \n\
  Shift_L space n e space 5 6 Shift_R \n\
  ( Up ) = g d o r s b . 7 8 Control_L \n\
  Left Down Right / q j u m p x - 9 0 Alt_L MainMenu

xvkbd.ShiftKeys: \
  F1 F2 F3 F4 F5 F6 F7 F8 F9 F10 F11 F12 BackSpace \n\
  Escape ~ | Z V C H W K : ! @ PrintScreen Insert \n\
  Caps_Lock Tab " F I T A L Y < # $ Return \n\
  Shift_L space N E space % ^ Shift_R \n\
  { Page_Up } + G D O R S B > & * Control_L \n\
  Home Page_Down End ? Q J U M P X _ [ ] Alt_L MainMenu

xvkbd.KeyLabels: \
  F1 F2 F3 F4 F5 F6 F7 F8 F9 F10 F11 F12 back \n\
  Esc ` \\ Z V C H W K ; 1 2 BS Del \n\
  Caps Tab ' F I T A L Y , 3 4 Return \n\
  Shift space N E space 5 6 Shift \n\
  ( U ) = G D O R S B . 7 8  Ctrl \n\
  L D R / Q J U M P X - 9 0 Alt MainMenu

xvkbd.NormalKeyLabels: \
  F1 F2 F3 F4 F5 F6 F7 F8 F9 F10 F11 F12 back  \n\
  Esc ` \\ z v c h w k ; 1 2 BS Del \n\
  Caps Tab ' f i t a l y , 3 4 Return \n\
  Shift space n e space 5 6 Shift \n\
  ( U ) = g d o r s b . 7 8  Ctrl \n\
  L D R / q j u m p x - 9 0 Alt MainMenu

xvkbd.ShiftKeyLabels: \
  F1 F2 F3 F4 F5 F6 F7 F8 F9 F10 F11 F12 back \n\
  Esc ~ | Z V C H W K : ! @ PrSc Ins \n\
  Caps Tab " F I T A L Y < # $ Return \n\
  Shift space N E space % ^ Shift \n\
  { Pu } + G D O R S B > & * Ctrl \n\
  H Pd E ? Q J U M P X _ [ ] Alt MainMenu

```

[http://www.handhelds.org/hypermail/tc1000-linux/1/0196.html](http://www.handhelds.org/hypermail/tc1000-linux/1/0196.html)
I've not gotten GOK to work, I use XVkbd.  I also use KDM instead of GDM:
```
sudo aptitude install kdm
```

To provide a login keyboard for the stylus:
In /etc/kde3/kdm/Xsetup, insert this at the beginning (adjust these numbers depending on whether you start your system in portrait or landscape mode): 
```

   /usr/bin/xvkbd -geometry +200-0 -no-keypad & 

```

and to remove it after login:
In /etc/kde3/kdm/Xstartup, insert this at the beginning:
```

   kill `ps -u root | grep xvkbd | cut -b 1-5`

```

**Fujitsu buttons**
[http://jan.rychter.com/software/fjbtndrv/fjbtndrv.ucw](http://jan.rychter.com/software/fjbtndrv/fjbtndrv.ucw)
I installed the fjbtndrv driver, and now the PgUp/PgDown & Up/Down buttons work.  (All the buttons work)
Unpack Jan's code someplace, and install the kernel headers for your system (use your version in the line below):
```
cd /usr/src/linux-headers-2.6.20-16/include/linux
sudo ln -s autoconf.h config.h
cd <fjbtndrv folder>
make
sudo make install
sudo depmod -ae
echo fjbtndrv >> sudo /etc/modules
sudo modprobe fjbtndrv
```

**Screen backlight**
Install the OSD tools:
```
sudo aptitude install xosd-bin
```

This puts the backlight to visible brightness:
```
echo 8 > /proc/acpi/video/GFX0/LCD/brightness
```
I created a script to change the LCD backlight:
```

root@aphrodite:~# cat /usr/local/bin/backlight
#!/bin/bash
## Note: this does not work for '/bin/sh' - '/bin/bash' must be used
# set the backlight on the Fujitsu ST5032D (0 - 8)

# what is the current setting?
# this is assumed to be an integer: 1 - 8
current_value=`cat /proc/acpi/video/GFX0/LCD/brightness`

# values for a bargraph
declare -a barsize
barsize[0]=0		# not used
barsize[1]=13
barsize[2]=25
barsize[3]=38
barsize[4]=50
barsize[5]=63
barsize[6]=75
barsize[7]=88
barsize[8]=100

# an integer bucket for the new value
declare -i level

# fill the bucket
level=${current_value:37}
echo "current level=$level"

# sometimes it's set to 0 on start ??
if [ $level -lt 1 ]; then
	level=1
fi

if [ $level -gt 8 ]; then
	level=8
fi

case $1 in
        [1-8])
                # user wants to set an explicit value
                level=$1
                ;;

        up)
                # user wants to increment the brightness level
                if [ $level -lt 8 ]; then
                        level=$(( ++level ))
                fi
                ;;

        down)
                # user wants to decrement the brightness level
                if [ $level -gt 1 ]; then
                        level=$(( --level ))
                fi
                ;;
esac

# make the new setting
sudo bash -c "echo $level > /proc/acpi/video/GFX0/LCD/brightness"
echo "Backlight ${barsize[$level]}% - level=$level"
osd_cat --pos=middle --align=center --delay=1 --barmode=percentage --percentage=${barsize[$level]} --text="Backlight ${barsize[$level]}%" --shadow=3 --outline=30 --font=-*-helvetica-*-r-normal-*-*-240-*-*-*-*-*-* --outlinecolour=white --shadowcolour=grey --colour=blue

```

In the backlight script, bash echos the value into a register only root may change, and this only works if sudo authority is granted all the time.  I accomplish this by adding this line to '/etc/sudoers'.  NOTE: you must use 'visudo' to edit this file, and use your login name:
```
Defaults:bret   !authenticate
```

As no screensavers provide an on-screen keyboard, I turn it off (just blank the screen).  However, in Kubuntu, this 'always sudo' setting allowed me to stop the screensaver without entering a password.

Obviously, I think this should be rectified.

**Miscellaneous**
I added a panel to the side of the display, set it to autohide, and added generic Launcher buttons to that, and edited one to call 'backlight up', one to call 'backlight down', and one to call 'rotate', with appropriate icons and names for them.  I have launchers for XVkbd and Xstroke as well, so I can start them without a keyboard attached.

Periodically, the display ceases 3D acceleration.  I've been able to reconfigure the X server, make the stylus input tweaks shown at the top of this post, and they've been restored for several days or weeks.  I don't know the cause:
```
dpkg-reconfigure xserver-xorg
```

There is a project to get SD & Memory Stick support, but it isn't working now.  I know of no support for the fingerprint scanner.  The network devices and sound work fine.

---

### Post by macmils on 2007-08-01
Excellent HOWTO

I'm doing something similar with a Fujitsu 4110 tabletpc. I'm stuck though with the button driver, when I try and compile it I get the error:

fjbuttons.c: In function 'fjbuttons_init':
fjbuttons.c:285 warning: passing argument 2 of 'request_irq' from incompatible pointer type

It carries on and builds the modules, but when it loads I get the following in the dmesg output:

[18893.492000] fjbuttons: initializing...
[18893.492000] IRQ handler type mismatch for IRQ 5
[18893.492000] current handler: uhci_hcd:usb3
[18893.492000]  [<c015410e>] setup_irq+0x12e/0x1e0
[18893.492000]  [<c02ecf0a>] cond_resched+0x2a/0x40
[18893.492000]  [<e0550290>] fjbuttons_irq_handler+0x0/0xa0 [fjbtndrv]
[18893.492000]  [<c0154263>] request_irq+0xa3/0xc0
[18893.492000]  [<c03e7f80>] sysenter_setup+0x80/0x90
[18893.492000]  [<e02cb06d>] fjbuttons_init+0x6d/0x84 [fjbtndrv]
[18893.492000]  [<c014422d>] sys_init_module+0x15d/0x1ba0
[18893.492000]  [<c03e7ea0>] kdump_buf_page_init+0x10/0x40
[18893.492000]  [<c0107a5d>] sys_mmap2+0xcd/0xd0
[18893.492000]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[18893.492000]  =======================
[18893.492000] fjbtndrv: timeout waiting for controller to be ready, resetting...
[18893.496000] fjbtndrv: timeout flushing, this should not happen.
[18893.496000] input: fjbtndrv as /class/input/input11


Any ideas?

---

### Post by bcw on 2007-08-02
> **macmils said:**
> Excellent HOWTO

Thanks.

> Any ideas?

I'm sorry, but I have no special knowledge about this.  I can only offer generic advice.

[LIST=1]
[*]You might be better to post this question on it's own, as more people might see it.
[*]I recommend you publish more about the machine's hardware and the particular Ubuntu version - does it have different serial ports?  Do any of the other components work, and with what settings, if different than what mine uses?
[*]Perhaps you might contact Jan, who wrote this, to ask his help.
[/LIST]
In time, I expect it could tease something out, as I have with other such issues in the past, but I don't have the hardware to work with.

Cheers,
Bret

---

### Post by bcw on 2007-08-03
> **macmils said:**
> 
[18893.492000] fjbuttons: initializing...
[18893.492000] IRQ handler type mismatch for IRQ 5
[18893.492000] current handler: uhci_hcd:usb3


On further reflection, why is the device doing anything with the USB modules?

I wonder if the serial port you chose for the stylus is the proper one?

Does your stylus work, and with what serial setting?

You're still better off finding someone that understands these devices - I don't program at this level.

Cheers,
Bret

---

### Post by bullethead67 on 2007-08-09
*Xorg installed xorg.conf with wacom entries, but I had to change "/dev/input/wacom" to "/dev/ttyS0", and I had to install 'setserial' with this entry in** /etc/serial.conf** to configure the digitizer's parameters:*

I dont have a file called serial.conf in my /etc/ folder what do i do now??

---

### Post by bcw on 2007-08-09
> **bullethead67 said:**
> *Xorg installed xorg.conf with wacom entries, but I had to change "/dev/input/wacom" to "/dev/ttyS0", and I had to install 'setserial' with this entry in** /etc/serial.conf** to configure the digitizer's parameters:*

I dont have a file called serial.conf in my /etc/ folder what do i do now??

Make one.  In this case, as in some others, you might use the tools in the package without any need for persistent configurations, so the configuration file is optional and not created by default.

Simply editing the file as if it existed will create it with many editors, or this command will create an empty instance which you can then edit:
```
sudo touch /etc/serial.conf
```

Cheers,
Bret

---

### Post by bullethead67 on 2007-08-09
OK the pen is working and everything is progressing . I got the button driver installed finally but when i modprobe the button driver my computer locks up. I think I may have possibly messed something up before i found this guide and i may needto reinstall ubuntu to start fresh.

---

### Post by bullethead67 on 2007-09-08
The buttons work great on a fresh install. I even checked all the keycodes. fn and alt dont return a keycode but when pressed and held do change the keycode for the other buttons. The problem im having is after I reboot the changes dont stay. I figured i would just modprobe fjbtndrv but it doenst work. I have reinstalled several times and it seems that the setup for the buttons cant survive a reboot.

There is a new driver on sourceforge but it doesnt let all the buttons work.

---

### Post by bcw on 2007-09-08
As I understand it now, you did this step:
```
echo fjbtndrv >> sudo /etc/modules
```

'man modprobe' tells me that the actual module insertion is handled by the kernel, so perhaps a 'dmesg' right after a boot would show something about the module?

Cheers,
Bret

---

### Post by bullethead67 on 2007-09-10
yes I did do 

echo fjbtndrv >> sudo /etc/modules

now i am trying it without that step to see how it does. so far the buttons work ill see if it can survive a reboot

---

### Post by bullethead67 on 2007-09-11
Diddnt survive reboot. a modprobe  of fjbtndrv  locked the system.  I did a nano of the sudo /etc/modules and added fjbtndrv (it wasnt there for some reason). i also deleted the config.h file (mabye it was only needed for initial setup). now everything is working good. I dont have the buttons mapped yet  but scroll uplclown and pg up down  along with enter. I don't know how to  map keys yet but It get it soon

---

### Post by nuffsed on 2007-09-16
Nice Howto.I could use most of it for my T4210.

One question though. Now when the buttons actually do something. How can I get them to do what I want (ie get the rotatebutton to rotate) and so on. I guess I have to get it to execute a script or something but How??

---

### Post by bcw on 2007-09-16
> **nuffsed said:**
> Nice Howto.I could use most of it for my T4210.

One question though. Now when the buttons actually do something. How can I get them to do what I want (ie get the rotatebutton to rotate) and so on. I guess I have to get it to execute a script or something but How??

The source hard-codes the meaning of the buttions - they only provide characters as written.

I've thought of modifying the code myself to call scripts, and have the scripts in some folder where they could be edited, but I've had no pressing need (re: the bit in my HowTo above where I put such things as 'rotate' and 'backlight up/down' in the 3d panel).  The character definitions have been useful enough for me as is, and objects at rest tend to remain at rest.

I've thought of assigning them different characters on resume or start so that chords of the buttions could be used as a login 'keyboard', as is done in one of the utilities Fujitsu provides with Windows, but I think it's better to solve the general case of getting a login keyboard into the resume/screen-saver login panel for that.

So I have been working on other things.

The key definitions are in the source code if you have other uses for them.

Cheers,
Bret

---

### Post by Ferret-Simpson on 2007-10-06
[http://fjbtndrv.wiki.sourceforge.net/](http://fjbtndrv.wiki.sourceforge.net/) This is the correct driver for the T-series button panels. Also supports decent program launching though the "Shortcut key" option in KDE's menu editor, and rotates the display and wacom when yu rotate the physical screen.

It's a bitch to install on Feisty though, you have to run ./configure about 5 times to install all the development packages it complains about, then get the linuxwacom source code and compile a new library from source that is missing from the Ubuntu install. . . for that, something like.

```
./configure --enable-libwacomcfg
make
sudo make install
```

Then after that, fscd 5.0rc4 doesn't work, use 0.41.

---

