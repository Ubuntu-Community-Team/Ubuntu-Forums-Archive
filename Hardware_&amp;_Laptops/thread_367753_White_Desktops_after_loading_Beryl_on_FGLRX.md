---
title: "White Desktops after loading Beryl on FGLRX"
date: 2007-02-22
forum: Hardware &amp; Laptops
---

### Post by jan. on 2007-02-22
Hi there,
I am so happy ATI released the new drivers, because before I couldn't get FGLRX running in many desperate attemtps, certainly the X1300 has not enjoyed the best support. Anyways. Direct Rendering is up and running. And I even loaded Beryl. The thing is:

When loading Beryl I don't get the Beryl splash screen, but my desktops fade white. The mouse pointer is changing when hovering windows, meaning that the pointer is still visible, but the desktop including windows as well as menus appear to be hidden behind some white overlay. Anyone encountered the same problem? Any solutions?

---

### Post by jan. on 2007-02-22
I should have submitted my settings... Sry. Here they are.

My xorg.conf
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "aticonfig-Screen[0]"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Extensions"
	Option         "Composite" "Disable"
EndSection

Section "Files"
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "de"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "Buttons" "7"
	Option	    "ButtonMapping" "1 2 3 6 7"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "false"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "XaaNoOffScreenPixmaps"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes	  "1280x1024"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```
Anything else needed? I am trying to get it running on a DELL PC, 2 GB RAM, ATI X1300 Graphics Card.

---

### Post by lemoniceblock on 2007-02-22
Hiya, I was also struggling with the white screen for a few days and I've found 2 possible solutions for it around the net:


When you log into your XGL session, open up the terminal and type
```

beryl-manager --no-force-window-manager

```
and the same 'menu' that you would get if you were to right click the Beryl tray icon will show up.  Ignore it and go type into the terminal:
```
beryl-xgl --use-copy
```


The problem with that is that the performance slows down.  I prefer doing this:
Log in to your XGL session open the terminal and type:
```
LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl &
```

Of course, neither of these are of use if you log in to your XGL session and all you get is the white screen.  I had to ctrl+alt+bckspc a few times before my XGL session was 'usable'.  I think one workaround is going to a normal GNOME session and typing either one of those commands in (or both? ^^ ) then logging out and logging back into your XGL session...that has worked for me so far.

Is it possible to write a script so that the the LD_PRELOAD code is 'typed' the moment we log into our XGL sessions just to save the hassle of crossing our fingers and hoping that the white screen isn't there? xD

---

### Post by touchwood on 2007-02-22
I had the same white screen scenario - I looked up the video card type (ASUS Laptop) I am using which is an ATI X1700 which according to ATI's homepage is not supported under Linux. Of course if anyone has an ATI X1700 working with Beryl I would like to hear from them.

Touchwood................

---

### Post by nachotronics on 2007-02-23
Here's a solution I got from _[**Forlong's** post in the beryl forums]("http://forum.beryl-project.org/viewtopic.php?f=43&t=70&st=0&sk=t&sd=a&start=330")_[SIZE="3"]** it consists in downgrading to the last working version from Treviños svn repository. **[/SIZE]

1. Uninstall Beryl completely
```
sudo apt-get remove 'beryl*'
```

2. Remove the SVN-repository (or any other Beryl-repo) so it won't update, till the next tested working version comes out
```
sudo gedit /etc/apt/sources.list
```
Then comment every beryl related line by adding # at the beggining, in my case they looked like this:
```
# deb http://ubuntu.beryl-project.org edgy main
# deb-src http://ubuntu.beryl-project.org edgy main
# deb http://www.beerorkid.com/compiz edgy main-edgy
# deb http://media.blutkind.org/xgl edgy main (latest: beryl 0.1.1)
# deb http://beryl.xglusers.de/ edgy main (latest: beryl 0.1.4; no aquamarine)
# deb http://download.tuxfamily.org/3v1deb edgy beryl-svn ( bleeding edge beryl development, use with care )
```

3. Look for these packages in /var/cache/apt/archives/

beryl_0.2.0+svn20070216-r4103+3v1ubuntu0_i386.deb
beryl-core_0.2.0+svn20070216-r4103+3v1ubuntu0_i386.deb
beryl-manager_0.2.0+svn20070213-r4019+3v1ubuntu0_i386.deb
beryl-plugins_0.2.0+svn20070218-r4130+3v1ubuntu0_i386.deb
beryl-plugins-data_0.2.0+svn20070218-r4130+3v1ubuntu0_all.deb
beryl-settings_0.2.0+svn20070218-r4140+3v1ubuntu0_i386.deb
beryl-settings-bindings_0.2.0+svn20070201-r3550+3v1ubuntu0_i386.deb
emerald_0.2.0+svn20070208-r3810+3v1ubuntu0_i386.deb
libberyldecoration0_0.2.0+svn20070216-r4103+3v1ubuntu0_i386.deb
libberylsettings0_0.2.0+svn20070216-r4103+3v1ubuntu0_i386.deb
libemeraldengine0_0.2.0+svn20070208-r3810+3v1ubuntu0_i386.deb

also optional: emerald-themes_0.2.0+svn20070126-r3229+3v1ubuntu0_all.deb

Or download them from _[**Treviños** svn repository]("http://download.tuxfamily.org/3v1deb/pool/edgy/beryl-svn/")_ or just [_**get the entire set at once from rapidshare -> beryl-svn.tar.gz**_]("http://rapidshare.com/files/17958701/beryl-svn.tar.gz.html")

4. Copy them to another folder e.g. beryl-svn on your desktop

5. Open a terminal and go to that directory
```
cd ~/Desktop/beryl-svn
```

6. Install all packages of that folder:
```
sudo dpkg -i *.deb
```

7. Start beryl by running
```
beryl-manager
```

8. Enjoy\\:D/

---

