---
title: "Howto install displaylink drive with ubunut 10.04"
date: 2010-05-25
forum: Hardware
---

### Post by Face_Man on 2010-05-25
well,

    i  really had problem getting my USB Display Adapter (Kensington Universal Multi-Display Adapter )to work and i hope this could help others.
    

    Installation Guide:

    1- update your linux kernel to linux kernel 2.6.34
        open Terminal:
```
 
cd ~/Desktop
mkdir kernel-2.6.34
cd kernel-2.6.34

```
            
            for 32
```
 
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb
dpkg -i linux-headers-2.6.34-020634_2.6.34-020634_all.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb
dpkg -i linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb
dpkg -i linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb
```
            
            for 64
              ```

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634_2.6.34-020634_all.deb
dpkg -i linux-headers-2.6.34-020634_2.6.34-020634_all.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb
dpkg -i linux-headers-2.6.34-020634-generic_2.6.34-020634_amd64.deb

wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-lucid/linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb
dpkg -i linux-image-2.6.34-020634-generic_2.6.34-020634_amd64.deb

```
                
    2- install Dependencies
        open Terminal:
```

sudo apt-get -y install libusb-dev xorg-dev xserver-xorg-video-displaylink  git-core

```
    
    3- install libdlo
```

cd ~/Desktop
mkdir libdlo
cd libdlo
wget http://people.freedesktop.org/~berniet/libdlo-0.1.2.tar.gz
tar -xzpf libdlo-0.1.2.tar.gz
cd  libdlo-0.1.2
./configure && sudo  make install

```
    
    4- Edit /etc/gdm/Init/Default
```

sudo gedit /etc/gdm/Init/Default

```
        add the following lines to the file /etc/gdm/Init/Default after the defintion of the gdmwhich() function.
```

XRANDR=`gdmwhich xrandr`
if [ "x$XRANDR" != "x" ] ; then
    $XRANDR -o 0
fi

```
        
        like  this
```

gdmwhich () {
   ....
}
        
XRANDR=`gdmwhich xrandr`
if [ "x$XRANDR" != "x" ] ; then
    $XRANDR -o 0
fi
        
sysresources=/etc/X11/Xresources

```
        
    5- Edit xorg.conf
        ```

        Section "ServerLayout"
            Identifier     "Layout0"
            Screen      0  "DisplayLinkScreen"  0 0
            Screen  	1  "Screen0" RightOf "DisplayLinkScreen"
            InputDevice    "Keyboard0" "CoreKeyboard"
            InputDevice    "Mouse0" "CorePointer"
            Option	    "Xinerama" "0" #Could not get this to work it has to be disable
        EndSection
            
        ##################################################{Files and Modules
        Section "Files"
            ModulePath      "/usr/local/lib/xorg/modules/drivers"
            ModulePath      "/usr/lib/xorg/modules"
            ModulePath      "/usr/lib/xorg/modules/drivers"
            ModulePath      "/usr/local/lib"
        EndSection
        
        ##################################################}
            
        ##################################################{Input Devices
        Section "InputDevice"
            Identifier     "Mouse0"
            Driver         "mouse"
            Option         "Protocol" "auto"
            Option         "Device" "/dev/psaux"
            Option         "Emulate3Buttons" "no"
            Option         "ZAxisMapping" "4 5"
        EndSection
            
        Section "InputDevice"
            Identifier     "Keyboard0"
            Driver         "kbd"
        EndSection
        ##################################################{
            
        ##################################################{Default Device
        Section "Monitor"
            Identifier     "Monitor0"
            VendorName     "Unknown"
            ModelName      "Unknown"
            HorizSync       28.0 - 33.0
            VertRefresh     43.0 - 72.0
            Option         "DPMS"
        EndSection
        Section "Device"
            Identifier      "Device0" # use "lspci | grep VGA" to get your Device info
            Driver          "nvidia"
            VendorName      "NVIDIA Corporation"
            Option          "NoLogo"	"True"
        EndSection
        Section "Screen"
            Identifier     "Screen0"
            Device         "Device0"
            Monitor        "Monitor0"
            DefaultDepth    24
            SubSection     "Display"
                Depth       24
                Modes       "1920x1200" "1920x1080" "1680x1050" "1600x1200" "1440x900" "1366x768" "1280x1024" "1280x960" "1280x800"  "1280x768"  "1152x864" "1024x768" "800x600" "640x480" 
            EndSubSection
        EndSection
        ##################################################{
        
        ##################################################{DisplayLink
        Section "Monitor"
            Identifier     "DisplayLinkMonitor"
        EndSection
        Section "Device"
            Identifier  "DisplayLinkDevice"
            Driver		"displaylink"
            Option  	"fbdev" "/dev/fb0"
        EndSection
        Section "Screen"
            Identifier      "DisplayLinkScreen"
            Device          "DisplayLinkDevice"
            Monitor         "DisplayLinkMonitor"
            SubSection "Display"
                Depth       24
                Modes       "1920x1200" "1920x1080" "1680x1050" "1600x1200" "1440x900" "1366x768" "1280x1024" "1280x960" "1280x800"  "1280x768"  "1152x864" "1024x768" "800x600" "640x480" 
            EndSubSection
        EndSection
        ##################################################{
```


    reboot and enjoy your USB graphic card :).
    
    with updating to the new linux kernel i was able to get the maximum screen resolution for my USB graphic card (1920x1080).
    However, I could not get compiz to work, therefore if anyone get compiz to work Plz post how its done.

    References
        [Linux Kernel 2.6.34 installation guide for Ubuntu Linux 10.04 | Ramoonus.nl]("http://www.ramoonus.nl/2010/05/19/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/")
        [freedesktop.org DisplayLink Wiki - HowTo]("http://libdlo.freedesktop.org/wiki/HowTo")
        [Noonday Blog Archive Linux USB video adapter]("http://blogg.noonday.se/2010/01/28/linux-usb-video-adapter/")

---

### Post by peterum on 2010-06-30
i somehow dont get this to work with my displaylink usb adapter and my tv as 2nd monitor...it only shows the starting screen on my tv and if i choose my tv as screen0, it doesnt use the right solution (so i dont have an taskbars) and i get a black screen on my laptop monitor

ur post helped me alot, since i didnt even get the starting screen on my tv before, but it'd be nice if some1 could give me any further help

here's my xorg.conf:
> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg                                                                     

############ Original Video Settings ###########                                                                  

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Depth   16
                Modes   "1280x720"
        EndSubSection
EndSection

#################################################                                                                 

Section "ServerLayout"
        Identifier      "Server Layout"
        Screen  0       "Default Screen" 0 0
        Screen  1       "DisplayLinkScreen" LeftOf "Default Screen"
	Option	    "Xinerama" "0" #Could not get this to work it has to be disable
EndSection

#################################################                                                                 

Section "Files"
            ModulePath      "/usr/local/lib/xorg/modules/drivers"
            ModulePath      "/usr/lib/xorg/modules"
            ModulePath      "/usr/lib/xorg/modules/drivers"
            ModulePath      "/usr/local/lib"
EndSection

############### DisplayLink Stuff ###############                                                                 

Section "Device"
        Identifier      "DisplayLinkDevice"
        driver          "displaylink"
        Option  "fbdev" "/dev/fb0"
EndSection

Section "Monitor"
        Identifier      "DisplayLinkMonitor"
EndSection

Section "Screen"
        Identifier      "DisplayLinkScreen"
	Device          "DisplayLinkDevice"
        Monitor         "DisplayLinkMonitor"
        SubSection "Display"
                Depth   16
		Modes   "1280x720"
        EndSubSection
EndSection


the solution 1280x720 is the solution that works with the adapter and my tv in windows 7

---

### Post by Face_Man on 2010-06-30
well, there is not much you could find on web and if you compare the Mac and Windows drive to the Linux drive you will be shocked. maybe this is the best you can get for now, i am using the displaylink however i cannot move between my screen and there is no compositing manager.

could u post the output of 
   ls /dev/fb*

also 
    uname -r


and make sure the xserver-xorg-video-displaylink package is install

> **peterum said:**
> i somehow dont get this to work with my displaylink usb adapter and my tv as 2nd monitor...it only shows the starting screen on my tv and if i choose my tv as screen0, it doesnt use the right solution (so i dont have an taskbars) and i get a black screen on my laptop monitor

ur post helped me alot, since i didnt even get the starting screen on my tv before, but it'd be nice if some1 could give me any further help

here's my xorg.conf:



the solution 1280x720 is the solution that works with the adapter and my tv in windows 7

---

### Post by peterum on 2010-07-02
thx for the quick reply!

output of ls /dev/fb*

> /dev/fb0

output of uname -r:
> /dev/fb0

the xserver-xorg-video-displaylink package is installed

---

### Post by Face_Man on 2010-07-02
> **peterum said:**
> 

output of uname -r:



the "uname -r" output should look like this :
2.6.34-020634-generic

---

### Post by peterum on 2010-07-02
lol, oops...c&p didnt work right...here's my uname -r

> 2.6.34-020634-generic


---

### Post by Face_Man on 2010-07-02
what is the output for 
    
    lspci | grep VGA

---

### Post by peterum on 2010-07-02
> 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

is it important to have my displaylink usb adapter plugged in when doing that?

---

### Post by Face_Man on 2010-07-02
> **peterum said:**
> is it important to have my displaylink usb adapter plugged in when doing that?

no

---

### Post by Face_Man on 2010-07-02
Goto [http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)

and install you driver and edit you xorg.conf file to use the driver.

---

### Post by peterum on 2010-07-02
i feel stupid..i dont find a driver for my graphic card..
it has to be for the "Intel GMA X4500" right? since that is, what my Samsung R509-Aura T3200 Daria has integrated...
i tried the tutorial u gave me without updating the driver and my tv showed the kubuntu screen once again, my laptop showed nothing. so i unplugged the displaylink and restarted. ubuntu told me that my graphics are incorrect and that i should reconfigure the conf...so i undid (if thats the correct word ;)) my changes, but still dont know what went wrong..or is it mandatory to install the newest driver?

---

### Post by Face_Man on 2010-07-02
> **peterum said:**
> i feel stupid..i dont find a driver for my graphic card..
it has to be for the "Intel GMA X4500" right? since that is, what my Samsung R509-Aura T3200 Daria has integrated...
i tried the tutorial u gave me without updating the driver and my tv showed the kubuntu screen once again, my laptop showed nothing. so i unplugged the displaylink and restarted. ubuntu told me that my graphics are incorrect and that i should reconfigure the conf...so i undid (if thats the correct word ;)) my changes, but still dont know what went wrong..or is it mandatory to install the newest driver?

Well, since you need both screens to work i think you to make sure your vga have the right driver, also xorg.conf have to be configure.
use this to auto configure xorg.conf
     Xorg -configure

---

### Post by peterum on 2010-07-02
thx for your patience...

> Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


Please consult the The X.Org Foundation support 
         at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log


---

### Post by Face_Man on 2010-07-02
> **peterum said:**
> thx for your patience...

no worries, 
well you could do this 
1. write on a paper "Xorg -configure" and "sudo /etc/init.d/gdm stop"
2. click on Ctrl+Alt+F2
3. type " sudo /etc/init.d/gdm stop"
4. type "Xorg -configure"
5. type "sudo reboot"

after you reboot ur PC post the xorg.conf

---

### Post by peterum on 2010-07-02
strange, it seems that nothing has changed...

> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg                                                                     

############ Original Video Settings ###########                                                                  

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Depth   16
                Modes   "1280x720"
        EndSubSection
EndSection

#################################################                                                                 

Section "ServerLayout"
        Identifier      "Server Layout"
        Screen  0       "Default Screen" 0 0
        Screen  1       "DisplayLinkScreen" LeftOf "Default Screen"
	Option	    "Xinerama" "0" #Could not get this to work it has to be disable
EndSection

#################################################                                                                 

Section "Files"
            ModulePath      "/usr/local/lib/xorg/modules/drivers"
            ModulePath      "/usr/lib/xorg/modules"
            ModulePath      "/usr/lib/xorg/modules/drivers"
            ModulePath      "/usr/local/lib"
EndSection

############### DisplayLink Stuff ###############                                                                 

Section "Device"
        Identifier      "DisplayLinkDevice"
        driver          "displaylink"
        Option  "fbdev" "/dev/fb0"
EndSection

Section "Monitor"
        Identifier      "DisplayLinkMonitor"
EndSection

Section "Screen"
        Identifier      "DisplayLinkScreen"
	Device          "DisplayLinkDevice"
        Monitor         "DisplayLinkMonitor"
        SubSection "Display"
                Depth   16
		Modes   "1280x720"
        EndSubSection
EndSection

---

### Post by Face_Man on 2010-07-02
> **peterum said:**
> strange, it seems that nothing has changed...

oK 

clear the xorg.conf and put this on it (just copy and past):

```

Section "ServerLayout"
	Identifier "Server Layout"
	Screen 0 "DisplayLinkScreen" 0 0
	Screen 1 "Default Screen" LeftOf "DisplayLinkScreen"
	Option	 "Xinerama" "0" #Could not get this to work it has to be disable
EndSection

################################################# 

Section "Files"
	ModulePath "/usr/local/lib/xorg/modules/drivers"
	ModulePath "/usr/lib/xorg/modules"
	ModulePath "/usr/lib/xorg/modules/drivers"
	ModulePath "/usr/local/lib"
EndSection


############### Default Video Device ############### 
Section "Device"
	Identifier "Configured Video Device"
EndSection

Section "Monitor"
	Identifier "Configured Monitor"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Monitor "Configured Monitor"
	Device "Configured Video Device"
	SubSection "Display"
		Depth 16
		Modes "1280x720"
	EndSubSection
EndSection


############### DisplayLink Stuff ############### 

Section "Device"
	Identifier "DisplayLinkDevice"
	driver "displaylink"
	Option "fbdev" "/dev/fb0"
EndSection

Section "Monitor"
	Identifier "DisplayLinkMonitor"
EndSection

Section "Screen"
	Identifier "DisplayLinkScreen"
	Device "DisplayLinkDevice"
	Monitor "DisplayLinkMonitor"
	SubSection "Display"
		Depth 16
		Modes "1280x720"
	EndSubSection
EndSection

```

save the file and reboot and you should have both screen running.

if it did not work you could look for your driver here
  [http://downloadcenter.intel.com/Default.aspx?lang=eng](http://downloadcenter.intel.com/Default.aspx?lang=eng)

---

### Post by Face_Man on 2010-07-02
So did it work?

---

### Post by peterum on 2010-07-03
i got it working on my tv with taskbars (the right resolution) now, many thx for that...i dont necessarily need both screens to work at the same time, since i want to work on my tv at home and have the other screen working when displaylink is not pluggied in. it would be a nice bonus though, if both screens are working at the same time.
from the page you gave me, i came to 

[http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)

with this tutorial

[http://intellinuxgraphics.org/install.html](http://intellinuxgraphics.org/install.html)

is there an easier way to update the graphics driver? i'm afraid i'll mess sth. up... :-s


besides that, i get a message when i boot up and have the displaylink plugged in that says that ubuntu is running with suboptimal graphical settings...and i got some colored horizontal lines on the screen after a few mins..i guess thats a problem with the displaylink driver and i have to live with that?!

---

### Post by swamytk on 2010-07-19
Here is how I got it working with my Lilliput DisplayLink based UM-70 USB monitor (17e9:02a9).

[How to get Lilliput DisplayLink based USB Monitor UM-70 (17e9:02a9) working in Ubuntu Linux]("http://karuppuswamy.com/wordpress/2010/07/19/how-to-get-lilliput-displaylink-based-usb-monitor-um-70-17e902a9-working-in-ubuntu-linux/")

Basically I faced two issues:
1. Only external USB monitor was working - I solved this by NOT including BusID line in Video device configuration
2. Mouse was not moving from one screen to another - solved this through mouse-wrapscreen tool available here: [http://digamma.cs.unm.edu/trac.dmohr/wiki/DualscreenMouseUtils](http://digamma.cs.unm.edu/trac.dmohr/wiki/DualscreenMouseUtils)

---

### Post by Don DeGregori on 2010-09-05
I have a DoubleSight DS-70U 7" USB monitor. 10.04 and XP are installed for dual boot. I installed the USB monitor for XP using DoubleSight drivers. It works fine.

Now I want this USB monitor to work with Ubuntu 10.04, when I boot to it. I don't need any switching of monitors. The USB device will be the main and only monitor. From all the posts, I realize a lot of work has involved DisplayLink, and xorg.conf. I'm a complete newbie in this area. I could start trying the scripts. But, since I don't want to switch monitors, I think this task could be easier. I just realized that dual boot involves a menu. How can the USB monitor be turned on to see the menu? Now I think there is to much on the plate.

Don

---

### Post by ml1969 on 2010-10-10
HI,

I'm also new to this.
I installed ubuntu 10.04 Netbook-edition on an Acer Aspire One D150 netbook.
Al works fine. Wlan, lan, printing etc.

So, now I have also a Mimo UM-720S USB-displaylink-Monitor (with touch).

I figured it out that it work with the console but not with the x server.

I used this xorg.conf (in /usr/libX11/xorg.conf.d)

[PHP]
Section "ServerLayout"
    Identifier "Server Layout"
    Screen 0 "DisplayLinkScreen" 0 0
    Screen 1 "Default Screen" LeftOf "DisplayLinkScreen"
    Option     "Xinerama" "0" #Could not get this to work it has to be disable
EndSection

################################################# 

Section "Files"
    ModulePath "/usr/local/lib/xorg/modules/drivers"
    ModulePath "/usr/lib/xorg/modules"
    ModulePath "/usr/lib/xorg/modules/drivers"
    ModulePath "/usr/local/lib"
EndSection


############### Default Video Device ############### 
Section "Device"
    Identifier "Configured Video Device"
EndSection

Section "Monitor"
    Identifier "Configured Monitor"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Monitor "Configured Monitor"
    Device "Configured Video Device"
    SubSection "Display"
        Depth 32
        Modes "1024x600"
    EndSubSection
EndSection


############### DisplayLink Stuff ############### 

Section "Device"
    Identifier "DisplayLinkDevice"
    driver "displaylink"
    Option "fbdev" "/dev/fb0"
EndSection

Section "Monitor"
    Identifier "DisplayLinkMonitor"
EndSection

Section "Screen"
    Identifier "DisplayLinkScreen"
    Device "DisplayLinkDevice"
    Monitor "DisplayLinkMonitor"
    SubSection "Display"
        Depth 16
        Modes "800x480"
    EndSubSection
EndSection

[/PHP]
but when I reboot the Xserver crashes and I go to the console on the USB-DEVICE.

If I delete this conf-file, and reboot I get the main screen working with the x server and the usb device for the console.



This is the xorg.conf after I run xserver -configure

[PHP]
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "record"
    Load  "dri"
    Load  "glx"
    Load  "extmod"
    Load  "dri2"
    Load  "dbe"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    VendorName  "Intel Corporation"
    BoardName   "Mobile 945GME Express Integrated Graphics Controller"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

[/PHP]What can happend?
I google, looked at several sites , also here:
[http://karuppuswamy.com/wordpress/2010/07/19/how-to-get-lilliput-displaylink-based-usb-monitor-um-70-17e902a9-working-in-ubuntu-linux/http://karuppuswamy.com/wordpress/2010/07/19/how-to-get-lilliput-displaylink-based-usb-monitor-um-70-17e902a9-working-in-ubuntu-linux/](http://karuppuswamy.com/wordpress/2010/07/19/how-to-get-lilliput-displaylink-based-usb-monitor-um-70-17e902a9-working-in-ubuntu-linux/http://karuppuswamy.com/wordpress/2010/07/19/how-to-get-lilliput-displaylink-based-usb-monitor-um-70-17e902a9-working-in-ubuntu-linux/)

but it still wont help me.


Michael




P.S. sorry for my bad englisch.

---

### Post by mazenovi on 2010-12-02
I tried to configure a third screen connected with a displaylink (Konig USB VGA) on an ubuntu 10.10 Maverick Meerkat 
First I installed nvidia proprietary driver
Next I followed these instructions [http://ubuntuforums.org/showthread.php?p=9358565](http://ubuntuforums.org/showthread.php?p=9358565) to install displaylink driver libdlo (except for the update of the kernel cause I've already a newer one)
Next when I reboot I have the prompt connexion on the screen connected with displaylink and an extended desktop on my 3 screens \o/
BUT when I log in gdm crash  immediatly!

I found this line in /var/log/syslog

```
Dec  2 12:40:47 bigmaze NetworkManager[1121]: <error> [1291290047.969035] [nm-manager.c:1317] user_proxy_init(): could not init user settings proxy: (3) Could not get owner of name 'org.freedesktop.NetworkManagerUserSettings': no such name
```

and googling say I have to disable Xinerama but is not enable in my /etc/x11/xorg.conf as you can see

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.06  (buildd@palmer)  Mon Oct  4 16:01:38 UTC 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "DisplayLinkScreen"  0 0
    Screen      1  "Screen0" RightOf "DisplayLinkScreen"
    Option         "Xinerama" "0"
EndSection

Section "Files"
            ModulePath      "/usr/local/lib/xorg/modules/drivers"
            ModulePath      "/usr/lib/xorg/modules"
            ModulePath      "/usr/lib/xorg/modules/drivers"
            ModulePath      "/usr/local/lib"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Hitachi/HINT X220W D-sub"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0, CRT-1: nvidia-auto-select +1680+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

##################################################{DisplayLink
        Section "Monitor"
            Identifier     "DisplayLinkMonitor"
        EndSection
        Section "Device"
            Identifier  "DisplayLinkDevice"
            Driver        "displaylink"
            Option      "fbdev" "/dev/fb0"
        EndSection
        Section "Screen"
            Identifier      "DisplayLinkScreen"
            Device          "DisplayLinkDevice"
            Monitor         "DisplayLinkMonitor"
            SubSection "Display"
                Depth       16
                Modes       "1024x768" "800x600" "640x480" 
            EndSubSection
        EndSection
        ##################################################{
```

I suspected a conflict between nvidia and displaylink driver cause using  default or nv driver is not crashing gdm (but I have not extended desktop with it).
So I tried to install latest version of the nvidia driver from here [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

but gdm is still crashing a few seconds after I log in :'(

Any suggestion?

regards

---

### Post by kendoori on 2011-01-26
At this point I still have a green screen on the Displaylink connected monitor.

Tried to follow these instructions with 10.10, with kernel 2.6.35-24. Thinkpad X201 with VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

Am using a Diamond Displaylink adapter, using the displaylink 195 chipset.

I am using a Thinkpad Ultrabase dock, so my normal setup (without Displaylink) is an external 24" display as my main screen, and the X201's LCD as secondary

My Xorg.conf is below. I changed fb0 to fb1 when it didn't work on boot as the /dev/ directory has both.

```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "dri"
    Load  "dbe"
    Load  "extmod"
    Load  "dri2"
    Load  "record"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "CacheLines"             # <i>
        #Option     "Dac6Bit"                # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "NoDDC"                  # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "XvMCSurfaces"           # <i>
        #Option     "PageFlip"               # [<bool>]
    Identifier  "Card0"
    Driver      "intel"
    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

##################################################{DisplayLink
        Section "Monitor"
            Identifier     "DisplayLinkMonitor"
        EndSection
        Section "Device"
            Identifier  "DisplayLinkDevice"
            Driver        "displaylink"
            Option      "fbdev" "/dev/fb1"
        EndSection
        Section "Screen"
            Identifier      "DisplayLinkScreen"
            Device          "DisplayLinkDevice"
            Monitor         "DisplayLinkMonitor"
            SubSection "Display"
                Depth       24
                Modes       "1920x1200" "1920x1080" "1680x1050" "1600x1200" "1440x900" "1366x768" "1280x1024" "1280x960" "1280x800"  "1280x768"  "1152x864" "1024x768" "800x600" "640x480" 
            EndSubSection
        EndSection
        ##################################################{

```

---

### Post by EugenePer on 2011-03-09
> **Face_Man said:**
> no worries, 
well you could do this 
1. write on a paper "Xorg -configure" and "sudo /etc/init.d/gdm stop"
2. click on Ctrl+Alt+F2
3. type " sudo /etc/init.d/gdm stop"
4. type "Xorg -configure"
5. type "sudo reboot"

after you reboot ur PC post the xorg.conf

Hi. I try to work with DisplayLink video adapter on Ubuntu 10.04 and arrived to this forum. 
I have several questions regarding your description on how to get it work:
1. Why we need kernel-2.6.34 and libdlo ?
2. I tried to generate xorg.conf file using this procedure but when I run "Xorg -configure" xserver crashed with segmentation fault. Do you have idea what may be a problem or maybe there is another way to do it ?
Thanks.

---

### Post by talthing on 2011-04-25
I`m trying to install Displaylink on my setup  (10.04, Sabrant UGA USB adapter, IBM X40)

I am able to see the green screen, but I`m not able to get past that point.

Here is what I could find troubleshooting on my own...

I`ve been following Face_Man`s post and this "Mulchmans blog" but can`t seem to find a solution that works....

It seems that my system recognizes the driver, but is ignoring the settings I have in xorg.conf under the displaylink section.  I tried installing xf86-video-displaylink but because I don`t have usr/lib/`uname -r` directory, the installation fails.  The libdlo (ver 0.1.2) drivers that came on a cd with the card installed in /usr/local/lib and I have a mapping under `files` section in my xorg.conf...but this did me no good either.

I know my xorg.conf file is being recognized (because until I added the `default display` when I would add xorg.conf to /etc/X11 my default monitor would be the displaylink screen forcing me to remove it in order see the screen to login)

displaylink troubleshooting

$ uname -r
    2.6.34-020634-generic

$ ls /dev/fb*
    /dev/fb0  /dev/fb1

$ dmesg | grep usb
[    0.319628] usbcore: registered new interface driver usbfs
[    0.319656] usbcore: registered new interface driver hub
[    0.319706] usbcore: registered new device driver usb
[    1.983679] usb 1-3: new high speed USB device using ehci_hcd and address 2
[   10.020356] usb 1-3: dlfb: allocated 4 65024 byte urbs 
[   10.178499] usb 1-3: dlfb: set_par mode 1600x1200
[   10.323648] usb 1-3: dlfb: DisplayLink USB device /dev/fb1 attached. 1600x1200 resolution. Using 7500K framebuffer memory
[   10.324873] usbcore: registered new interface driver udlfb

$ sudo apt-get -y install libusb-dev xorg-dev xserver-xorg-video-displaylink  git-core
    libusb-dev is already the newest version.
    xorg-dev is already the newest version.
    xserver-xorg-video-displaylink is already the newest version.
    git-core is already the newest version.
    0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

$ sudo ./test1    #libdlo test senario
   (test runs a series of shapes and colors ending with `DisplayLink` logo     in multiple positions on the monitor as expected)

$ gedit xorg.conf 
 Section "ServerLayout"
    Identifier "Server Layout"
    Screen 0 "Default Screen" LeftOf "DisplayLinkScreen"
    Screen 1 "DisplayLinkScreen" 0 0
EndSection

################################################# 

Section "Files"
    ModulePath "/usr/lib/xorg"
    ModulePath "/usr/lib/xorg/modules"
    ModulePath "/usr/lib/xorg/modules/drivers"
EndSection


############### Default Video Device ############### 
Section "Device"
    Identifier "Configured Video Device"
EndSection

Section "Monitor"
    Identifier "Configured Monitor"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Monitor "Configured Monitor"
    Device "Configured Video Device"
    SubSection "Display"
        Depth 16
        Modes "1024x768"
    EndSubSection
EndSection


############### DisplayLink Stuff ############### 

Section "Device"
    Identifier "DisplayLinkDevice"
    driver "displaylink"
    Option "fbdev" "/dev/fb1"
EndSection

Section "Monitor"
    Identifier "DisplayLinkMonitor"
EndSection

Section "Screen"
    Identifier "DisplayLinkScreen"
    Device "DisplayLinkDevice"
    Monitor "DisplayLinkMonitor"
    SubSection "Display"
        Depth 16
        Modes "1024x768"
    EndSubSection
EndSection 
Section "Monitor"
    Identifier "DisplayLinkMonitor"
EndSection

Section "Screen"
    Identifier "DisplayLinkScreen"
    Device "DisplayLinkDevice"
    Monitor "DisplayLinkMonitor"
    SubSection "Display"
        Depth 16
        Modes "1024x768"
    EndSubSection
EndSection

---

### Post by Ulysses on 2011-05-30
Hello,

I just got one of these from Tiger Direct and I thought it would be pretty cool.
I already have 2 monitors and I thought this would be a good way to get a third. I'm using 10.10. Haven't troubled to upgrade to Narwahl yet.

I read the thread started here [http://ubuntuforums.org/showthread.php?p=9358565]("http://ubuntuforums.org/showthread.php?p=9358565") and still I have no joy.

Has anyone had any luck with a third screen using this piece of hardware?

I haven't even managed a green screen, either. All that shows up was a random placement of many, many 'Displaylink" icons all over the screen (even that left after I rebooted).

RAR

---

