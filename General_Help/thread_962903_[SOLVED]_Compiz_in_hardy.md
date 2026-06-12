---
title: "[SOLVED] Compiz in hardy"
date: 2008-10-29
forum: General Help
---

### Post by TadeoDiaz on 2008-10-29
So I just recently installed Hardy (dual boot with XP) on my tower because i was all excited about ubuntu. Everything went well until I installed compiz and tried to run it - all i get is a white screen and I have to do a hard reset. When I try to run AWN it give me a message:

Error: Screen isn't composited. Please run compiz (-fusion) or another composition manager.

I don't know if this is the right forum to post, I am sorry if it isn't, but you guys have always been very helpful with everything. Thanks!

---

### Post by Zzl1xndd on 2008-10-29
Compiz is installed by default on 8.04(hardy) when you say you installed it what exactly did you do?

Also if you could what kind of graphics card are you using?

---

### Post by TadeoDiaz on 2008-10-29
Im sorry

I am running a custom tower with a ATI card. I am not at the tower right now but will post what model as soon as i get to it

---

### Post by Tom--d on 2008-10-29
If its an ATI Graphics Card, go to system > Admin > hardware drivers and install the ATI driver.

Reboot and then enable Compiz.

And when you say you install compiz? how? 'cause Its already install by default.

---

### Post by Zzl1xndd on 2008-10-29
No need to apologize just wanna make sure I fully understand the problem instead of making it worse. Tom--d may in fact be right that the proprietary ATI driver may fix the problem.

---

### Post by TadeoDiaz on 2008-10-29
Thanks for the quick replies guys

Here is what I did:

I installed a fresh copy of Hardy along XP, I updated and then enabled the proprietary driver for ATI cards. Then I followed these instructions:

[http://thegabfather.wordpress.com/2008/05/17/how-to-install-compiz-fusion-in-ubuntu-hardy-heron/](http://thegabfather.wordpress.com/2008/05/17/how-to-install-compiz-fusion-in-ubuntu-hardy-heron/)

I restarted but I still couldn't use the any of the advanced desktop settings

I then tried to start AWN but it gave me the message that I posted in my first comment. I tried manually starting compiz by typing compiz in terminal but got a white screen and I had to force a restart. Every time I try to start AWN it give me the "screen no composited" windows with the error message.

I am currently using the ATI Radeon 9800PRO 128MB

Thanks in advance for your help!

---

### Post by epitaph on 2008-10-30
Are you sure you have the compizconfig-settings-manager package installed? Perhaps a reinstall of it.

```
sudo apt-get install compizconfig-settings-manager
```

Or...

```
sudo apt-get install --reinstall compizconfig-settings-manager
```

---

### Post by TadeoDiaz on 2008-10-30
> **epitaph said:**
> Are you sure you have the compizconfig-settings-manager package installed? Perhaps a reinstall of it.

```
sudo apt-get install compizconfig-settings-manager
```

Or...

```
sudo apt-get install --reinstall compizconfig-settings-manager
```

I've never had problems accessing the settings manager, it's just when I try to start compiz that I get the white screen (I even left it on for 30min to see if it changed or something, but nothing)

I tried reinstalling but I'm still having the same problem.

Do you guys think updating to Ibex could help? I think I might try it this afternoon to see if it makes a difference.

---

### Post by hermes0710 on 2008-10-30
Try creating a new user and login again (as the new one). If everything goes well then it might have to do with your compiz configuration.

---

### Post by TadeoDiaz on 2008-10-30
> **hermes0710 said:**
> Try creating a new user and login again (as the new one). If everything goes well then it might have to do with your compiz configuration.

I tried it but when I try to log into the test account I get the white screen and I have to force restart

---

### Post by TadeoDiaz on 2008-10-30
So I found this forum where the guy was having the same problem and I tried what he did:

[http://www.johnberns.com/2008/07/20/fixing-compiz-fusion-on-ati-radeon-mobility-9800-under-ubuntu-hardy-804/](http://www.johnberns.com/2008/07/20/fixing-compiz-fusion-on-ati-radeon-mobility-9800-under-ubuntu-hardy-804/)

It seemed to work fine, I restarted and ran compiz from console. AWN started and all but everything was really slow. Finally it crapped out on me and now all the graphics are terribly slow (even scrolling). Here is the output that I got from terminal after I started compiz:

```
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
```

---

### Post by epitaph on 2008-10-30
When you get a white screen press alt+f2 and type "metacity --replace" followed by TAB then ENTER.

If this gives you your desktop back (albeit without effects since compiz would be disabled) then it's most likely an issue with the video driver you are using.

The white screen happened to me quite a few times when I tried to use VESA I believe. Perhaps your xorg configuration is a little out of whack?

[edit] What happens when you try to run an OpenGL application? (Google Earth, glxgears, movie players that render using OpenGL)

---

### Post by TadeoDiaz on 2008-10-30
> **epitaph said:**
> When you get a white screen press alt+f2 and type "metacity --replace" followed by TAB then ENTER.

If this gives you your desktop back (albeit without effects since compiz would be disabled) then it's most likely an issue with the video driver you are using.

The white screen happened to me quite a few times when I tried to use VESA I believe. Perhaps your xorg configuration is a little out of whack?

[edit] What happens when you try to run an OpenGL application? (Google Earth, glxgears, movie players that render using OpenGL)

glxgears seems to run just fine. I guess what I was trying to do is get compiz-fusion running to get better graphics. Is there anyway that I can change the settings so that it allows me to use it? Would it be helpful if I installed the driver directly from ATI?

---

### Post by TadeoDiaz on 2008-10-30
> **epitaph said:**
> When you get a white screen press alt+f2 and type "metacity --replace" followed by TAB then ENTER.

If this gives you your desktop back (albeit without effects since compiz would be disabled) then it's most likely an issue with the video driver you are using.

I tried this and when I used your method it gave me the desktop back and displayed this message:

```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4e48 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
```

---

### Post by TadeoDiaz on 2008-10-30
Ok so I at least found a fix for the line:

```
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
```

I found I found it here ([https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/209207](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/209207))


[QUOTE] brad wrote on 2008-06-09: (permalink)

I found the fix for this one.

1. System > Preferences > Advanced Desktop Effects Settings.
2. Scroll down and open "Scale" under the Window Management section.
3. Go to the Bindings Tab and open the first "Initiate Window Picker" configuration.
4. Choose a corner. This allows you to zoom out and see all your windows to choose one.
5. That's it, you now have a valid value for initiate_edge.

If you don't have the first step available, install the package compizconfig-settings-manager. [\QUOTE]

---

### Post by epitaph on 2008-10-30
It looks like you are using the restricted ATi driver already, so I'm not sure the problem is driver related. The behavior on my laptop was essentially exactly what you're describing. That happened to me when the fglrx restricted driver became disabled somehow and when I rebooted it loaded compiz and gave a white screen. So your problem sounds similar. It does look like it's using fglrx though.

Can you post your xorg.conf?

```
gedit /etc/X11/xorg.conf
```

I'm going to throw a disclaimer in and say I'm not the most knowledgable, but perhaps something will catch my eye.

---

### Post by TadeoDiaz on 2008-10-30
Ok I tried a few things and nothing has worked yet

First I tried this: [http://www.freesoftwaremagazine.com/articles/installing_compiz_fusion](http://www.freesoftwaremagazine.com/articles/installing_compiz_fusion)

No luck

I then tried to start compiz in terminal with "compiz &" but I still get the white screen. After replacing with metacity (alt+F2, type metacity --replace, tap and enter) I find that terminal is displaying this message:

```
Detected PCI ID for VGA: 01:00.0 0300: 1002:4e48 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered

```

---

### Post by TadeoDiaz on 2008-10-30
> **epitaph said:**
> It looks like you are using the restricted ATi driver already, so I'm not sure the problem is driver related. The behavior on my laptop was essentially exactly what you're describing. That happened to me when the fglrx restricted driver became disabled somehow and when I rebooted it loaded compiz and gave a white screen. So your problem sounds similar. It does look like it's using fglrx though.

Can you post your xorg.conf?

```
gedit /etc/X11/xorg.conf
```

I'm going to throw a disclaimer in and say I'm not the most knowledgable, but perhaps something will catch my eye.

No worries about it, this is only my 4th month with ubuntu, I just wanted to give it a try on my tower to see if i could completely replace windows.

This is what the xorg.conf file has:

```
# xorg.conf (X.Org X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

I might be wrong on this but shouldn't the line: Configured Video Device be a little more specific, at least identifying that it is ATI video card?

Would it help if I just installed the driver from ATI?

---

### Post by epitaph on 2008-10-30
First try making a new xorg.conf using aticonfig:

```
aticonfig --initial
```

Then post the new xorg.conf.

NOTE: You can restart X using ctrl+alt+backspace but know that it will kill anything open. Or you can reboot.

---

### Post by TadeoDiaz on 2008-10-31
> **epitaph said:**
> First try making a new xorg.conf using aticonfig:

```
aticonfig --initial
```

Then post the new xorg.conf.

NOTE: You can restart X using ctrl+alt+backspace but know that it will kill anything open. Or you can reboot.

This is the new xorg.conf


```
# xorg.conf (X.Org X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
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
	EndSubSection
EndSection
```

However I am still getting the same white screen of death with the output:

```
Detected PCI ID for VGA: 01:00.0 0300: 1002:4e48 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
metaAttempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered

[1]+  Done                    compiz

```

---

### Post by TadeoDiaz on 2008-10-31
So I tried to start compiz & again and when I blindly replaced with metacity I got this screen

[http://img183.imageshack.us/my.php?image=screenshot1wt6.png](http://img183.imageshack.us/my.php?image=screenshot1wt6.png)

I don't know what it means but hopefully im getting a little closer to fixing this so I can get compiz back

---

### Post by epitaph on 2008-10-31
Open up your xorg.conf

```
sudo gedit /etc/X11/xorg.conf
```

Add the following to the configuration file:

```
Section "Extensions"
Option "Composite" "Enable"
EndSection

Section "ServerFlags"
Option "AIGLX" "on"
EndSection

```

Save the file, exit gedit and restart X (ctrl+alt+backspace).

---

### Post by TadeoDiaz on 2008-10-31
> **epitaph said:**
> Open up your xorg.conf

```
sudo gedit /etc/X11/xorg.conf
```

Add the following to the configuration file:

```
Section "Extensions"
Option "Composite" "Enable"
EndSection

Section "ServerFlags"
Option "AIGLX" "on"
EndSection

```

Save the file, exit gedit and restart X (ctrl+alt+backspace).

I was hoping this would do it but I still get the white screen.
Could it be because I'm running mesa drivers? (as per [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)
)

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)
```

It says in the wiki to remove the mesa driver, but when I try with ```
sudo apt-get remove xserver-xgl
``` it tells me:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xserver-xgl is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic libglitz-glx1 libqt4-core python-qt4-common
  libqt4-gui python-sip4 libglitz1 libemeraldengine0 linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by epitaph on 2008-10-31
This is what my fglrxinfo returns on my laptop:

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7412 Release
```

That is definitely a problem. You need the fglrx driver to be handling the OpenGL acceleration.

I'm not exactly sure how, but you need to get fglrx to be your OpenGL renderer.

---

### Post by TadeoDiaz on 2008-10-31
I think i've modified a few too many things, I think im going to just install a clean copy of ubuntu and start from there. Its just sad that I can't get compiz to work on my tower :(

Thanks for all your help epitaph, ill let you know if anything works magically

---

### Post by TadeoDiaz on 2008-11-02
Reformated and installed Intrepid Ibex and everything seems to be working fine. The graphics are a little slower than I expected but can't complain when they are actually working. Thanks to everyone for their help!

---

