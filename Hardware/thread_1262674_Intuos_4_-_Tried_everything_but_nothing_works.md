---
title: "Intuos 4 - Tried everything but nothing works"
date: 2009-09-10
forum: Hardware
---

### Post by simonced on 2009-09-10
Hi all,

Sorry to bother you with this subject but my Intuos 4 is not working at all.
I'm under linux mint 7 that uses the same packages that jaunty.
I tried all the howto about the intuos 4, compiling the last driver (from gali98), rebooting, xorg.conf, .fdi... nothing.

It does works under Windos vista on the same machine.

I'm a linux user for long itme but onthis case I managed nothing.
I'm desperate. Please what info do you need to help me out?

I don't have nothing in /dev/input that starts with wacom, it's a starting point no? I saw this issue nowhere...

Thank you very much by advance.

---

### Post by hansdown on 2009-09-10
Hi simonced.

Not sure if this is helpful.

[http://www.gtk-apps.org/content/show.php?content=104309&forumpage=0&PHPSESSID=xpfyvhcukye](http://www.gtk-apps.org/content/show.php?content=104309&forumpage=0&PHPSESSID=xpfyvhcukye)

It's in synaptic with the same name.

---

### Post by Favux on 2009-09-10
Hi simonced,

If there is no Wacom stuff when you enter in a terminal:
```
dmesg | grep [Ww]acom
```
even though you compiled and installed a newer wacom.ko there is a way to get it to "kick" in.  Assuming the new wacom.ko is present in the right directory (from the copy (cp) command) add "wacom" (without the quotes) to the end of the file 'modules' in "/etc/".  I don't know why some systems need this.  To edit enter in a terminal:
```
gksudo gedit /etc/modules
```
Save, close, and reboot.

Good luck!

---

### Post by simonced on 2009-09-10
Thank you for your answers.

@hansdown : I'll install this package but I'm afraid it's the same I already installed, I'll tell you once I reboot.

@Favux:
Here is the result of the command:
>  dmesg | grep [Ww]acom
[ 6268.900671] usbcore: registered new interface driver wacom
[ 6268.900676] wacom: v1.49-pc-1:USB Wacom Graphire and Wacom Intuos tablet driver
[ 6315.403984] input: Wacom Intuos4 4x6 as /devices/pci0000:00/0000:00:04.0/usb3/3-1/3-1:1.0/input/input12

But before I had the idea to do :
> ~ sudo modprobe wacom
Then when I plug the tablet, I see the /dev/input/wacom as a link to event12
But not working.

Here is the result of lsmod command:
> ~ lsmod| grep wacom
wacom                  30344  0

I'm trying the load module trick and reboot, brb.

---

### Post by simonced on 2009-09-10
Ok, I rebooted an not working yet.

@Hansdown: I didn't know this utility yet but when I launch it it says no tablet detected. But it'll be a good tool when it'll work :-)

@Favux:
The module is automaticly loaded at startup right now.
Here is my lsmod return :
> wacom                  30344  0

Here is my /dev/imput folder in case that helps:
> drwxr-xr-x   2 root root    140 2009-09-11 09:39 by-id
drwxr-xr-x   2 root root    220 2009-09-11 09:39 by-path
crw-r-----   1 root root 13, 64 2009-09-11 18:35 event0
crw-r-----   1 root root 13, 65 2009-09-11 18:35 event1
crw-r-----   1 root root 13, 74 2009-09-11 09:35 event10
crw-r-----   1 root root 13, 75 2009-09-11 09:35 event11
crw-r-----   1 root root 13, 76 2009-09-11 09:39 event12
crw-r-----   1 root root 13, 66 2009-09-11 18:35 event2
crw-r-----   1 root root 13, 67 2009-09-11 18:35 event3
crw-rw----+  1 root root 13, 68 2009-09-11 18:35 event4
crw-r-----   1 root root 13, 69 2009-09-11 18:35 event5
crw-rw----+  1 root root 13, 70 2009-09-11 09:35 event6
crw-r-----   1 root root 13, 71 2009-09-11 09:35 event7
crw-r-----   1 root root 13, 72 2009-09-11 09:35 event8
crw-r-----   1 root root 13, 73 2009-09-11 09:35 event9
crw-r-----   1 root root 13, 63 2009-09-11 18:35 mice
crw-r-----   1 root root 13, 32 2009-09-11 18:35 mouse0
crw-r-----   1 root root 13, 33 2009-09-11 09:35 mouse1
crw-r-----   1 root root 13, 34 2009-09-11 09:35 mouse2
crw-r-----   1 root root 13, 35 2009-09-11 09:39 mouse3
lrwxrwxrwx   1 root root      7 2009-09-11 09:39 wacom -> event12


And because you'll ask sonner or later, my xorg.conf (I have to be careful with this file as it crashes my pc easyly, even in text mode)
> Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

#Pour la souris Microsoft...
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
    Option          "Protocol"              "ExplorerPS/2"
    Option          "Emulate3Buttons"   "false"
    Option          "Buttons"               "7"
    Option          "ZAxisMapping"       "4 5"
	Option 		"ButtonMapping" "1 2 3 6 7"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection

#une autre tentative d'avoir la tablette
Section "InputDevice"
	Driver "wacom"
	Identifier "stylus"
	Option "Device" "/dev/input/wacom" # USB ONLY?
	Option "Type" "stylus"
	Option "USB" "on" # USB ONLY
EndSection

Section "InputDevice"
	Driver "wacom"
	Identifier "eraser"
	Option "Device" "/dev/input/wacom" # USB ONLY?
	Option "Type" "eraser"
	Option "USB" "on" # USB ONLY
EndSection

Section "InputDevice"
	Driver "wacom"
	Identifier "pad"
	Option "Device" "/dev/input/wacom" # USB ONLY
	Option "Type" "pad"
	Option 		"USB" 		"on"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	#Screen		"Default Screen"
	#InputDevice	"Generic Keyboard"
	#InputDevice	"Synaptics Touchpad"
	
	#InputDevice	"Configured Mouse"

	### Uncomment if you have a wacom tablet ###
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice     "pad"
EndSection

I added the server layout section after following some howto and help you gave to other people but I may not need it. That's why some lines are commented because I'm afraid that crashes my pc.
But I do need the Mouse section as it make my 5 buttons mouse working properly.

Well, it already becoming a bit better. What would be the next step?

Thank you for your help.

---

### Post by Favux on 2009-09-10
Hi simonced,

Don't use Wacom Control Panel.  In fact uninstall it through Synaptic.  It'll just complicate things.

Now are you using the two default Jaunty 0.8.2-2 linuxwacom packages?  You didn't try to install another linuxwacom version did you?  You've just compiled a wacom.ko, correct?  Do you know which version?

In Jaunty you do not need to use the xorg.conf.  Rather than remove the Wacom sections and entries in "ServerLayout" comment (#) them out.  Put # in front of every line in the Wacom sections.  After you do that and reboot try removing the comment (#) in front of:
```
Screen "Default Screen"
```
in "ServerLayout" and reboot.  See if that makes things more stable.

Then in a terminal enter "xsetwacom list" and "xinput --list" and let's look at the output.

---

### Post by simonced on 2009-09-10
I just have those 2 packages installed that contains wacom in their name :
- wacom-tools
- xserver-xorg-input-wacom

The compiled driver version is 0.8.4-1.

As I don't need the server layout in my cfg I'll comment everything for wacom and the server layout. I come back after a reboot.

Ok, reboot is not crashing.
I still have the module loaded and the /dev/input/wacon is still here too.

---

### Post by simonced on 2009-09-11
Any idea on the next step?
My reboot is fine but still no tablet, not that easy I suppose :D

---

### Post by Favux on 2009-09-11
Hi simonced,

I'll assume "xsetwacom list" was blank and "xinput --list" called your stuff Intuos 4 something.

Usb should now be established to the tablet with the new wacom.ko.  You should have stylus activity.  If not something still isn't right.

If you do have stylus try this modified wacom.fdi in post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

---

### Post by simonced on 2009-09-11
Here is the xinput output :
> "Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=2	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"U+P Keyboard"	id=4	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"U+P Keyboard"	id=5	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=6	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Microsoft Microsoft IntelliMouse? Explorer"	id=7	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Logitech Trackball"	id=8	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"SynPS/2 Synaptics TouchPad"	id=9	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 1472
		Max_value is 5472
		Resolution is 1
	Axis 1 :
		Min_value is 1408
		Max_value is 4448
		Resolution is 1
No stylus :(

---

### Post by Favux on 2009-09-12
Hi simonced,

Well something isn't right.  Just to recap.

You have the two default Jaunty 0.8.2-2 linuxwacom packages installed.  You did not ever install another version of linuxwacom.

You've compiled and installed only a new 0.8.4-1 wacom.ko using Section 1 of gali98's HOW TO.  And the dmesg shows it is active.

My guess is you now need to install the modified wacom.fdi.

---

### Post by simonced on 2009-09-12
I used the fdi but the "xsetwacom list" still returns nothing :(
I restarted X beetween...

---

### Post by Favux on 2009-09-12
Hi simonced,

Alright.

First are we sure it isn't a hardware problem?  In other words your tablet works in Windows or on another machine?

Second, I hate to do this, but can you look at the questions I've posted and between them and what you've done so far, try to list exactly what you've done to date.  I don't want to be taking you down inadvertent dead-ends.

---

### Post by Favux on 2009-09-12
Hi simonced,

Alright.

First are we sure it isn't a hardware problem?  In other words your tablet works in Windows or on another machine?

Second, I hate to do this, but can you look at the questions I've posted and between them and what you've done so far, try to list exactly what you've done to date.  I don't want to be taking you down inadvertent dead-ends.

---

### Post by simonced on 2009-09-12
Hi Favux,

I'm in dual boot on this machine and the tablet does work under windows vista.

So what I've done so far :
- Trying to set up simply with the xorg.con : not working
- Compiling the new wacom kernel driver and installing in the proper directory
- Autoloading the wacom module (modification of the /etc/modules file)
- Cleaning up my xorg.conf
- Installing the custom fdi.
- Rebooting X and machine many times

As I know the wacom module is loaded and the /dev/input/wacom is created (linked to events12).
References of wacom ar found in dmesg.

Nothing from the command "xsetwacom list" and no wacom in "xinput".

I shouldn't have forgotten nothing...

Hope we'll find what's wrong.
Thank you for you help.

---

### Post by Favux on 2009-09-12
Hi simonced,

Well xinput should be showing the tablet since the wacom.ko seems to be working.  Verify in Synaptic Package Manager that both default Jaunty 0.8.2-2 linuxwacom packages are installed:  xserver-xorg-input-wacom & wacom-tools.  Especially xserver-xorg-input-wacom.  If not install and reboot.

---

### Post by simonced on 2009-09-12
These 2 packages are already instaled.

---

### Post by Favux on 2009-09-12
OK.  There's no active wacom stuff in your xorg.conf.  You didn't do a "sudo make install" with another version of wacomcpl.  You didn't install a custom_wacom.fdi in "/etc/hal/fdi/policy/"?

Reinstall both linuxwacom Packages in Synaptic and reboot.

Double check that the modified 10-wacom.fdi from post #176 is correctly installed in "/usr/share/hal/fdi/policy/20thirdparty/".  Although you should have something like "Wacom Intuos4 etc." in your xinput already even without the .fdi working.

---

### Post by simonced on 2009-09-12
It WOOOOOORKS !!!
Favux you're the tablert master!
WEll I had a custom_wacom but I don't think it was troublesome.
I simply reinstalled the 2 packes and it's magic :-)

And now I have many stuf with "xinput list".
I just need to set-it up because the ring is working opposite and the 2 side buttons of the stylus are swaped.

I'll look for the doc to customize the fdi file for  wacom tablets.

Thank you very much.

---

### Post by simonced on 2009-09-12
A last question, my setup is ok for instance. I managed to swap the stylus buttons 2 and 3.
But doing the same with the pad wheel is not working.
I checked the buttons and they are Button4 and 5. I'd like to swap them too, but no success. I guess there is something specific about them, any idea?

---

### Post by Favux on 2009-09-12
Hi simonced,

Outstanding!  You got it working.  Nice job.  You're welcome.

Well the custom_wacom.fdi would interfere because it executes after the modified 10-wacom.fdi.  So it's good you removed it.

You want to look at the link to the Intous4 thread, which is ceridwen's post #95 here:  [http://ubuntuforums.org/showthread.php?t=1120029&page=10](http://ubuntuforums.org/showthread.php?t=1120029&page=10)  Then you can look through the rest of the thread from there.  They've gotten most things to work, except I think one button.  Which is pretty good if you remember linuxwacom 0.8.2-2 didn't even support the Intous4 usb.

---

### Post by simonced on 2009-09-12
Thank you for you support,

I checked the thread but I'm stuck early because Wacomcpl doesn't work for me, and I don't have .xinitrc created...

Anuway the fdi file is working because some modifications are working like swaping the buttons 2 and 3 of the stylus.
I used xidump to check the number of the buttons of the pad and invert them like I did for the stylus but it's not that trick.

Here is the beginning of my customised fdi :
```
<deviceinfo version="0.2">
  <device>
    <match key="info.category" contains="input">
      <match key="info.product" contains="Wacom">
		<merge key="input.x11_driver" type="string">wacom</merge>
		<merge key="input.x11_options.Type" type="string">stylus</merge>
        <append key="info.callouts.add" type="strlist">hal-setup-wacom</append>
        <append key="wacom.types" type="strlist">eraser</append>
        <append key="wacom.types" type="strlist">cursor</append>
        <append key="wacom.types" type="strlist">pad</append>

		[B]<!-- Modif perso -->
		<match key="input.x11_options.Type" contains="stylus">
			<merge key="input.x11_options.Button2" type="string">3</merge>
			<merge key="input.x11_options.Button3" type="string">2</merge>
		</match>
		<match key="input.x11_options.Type" contains="pad">
			<merge key="input.x11_options.Button4" type="string">5</merge>
			<merge key="input.x11_options.Button5" type="string">4</merge>
		</match>
		<!-- // Modif perso -->[/B]
      </match>
...
```
bold text are my modifications

And here is the xidump that made me check the buttons numbers for the pad:

The list first to check with device to analyse :
```
Virtual core pointer           disabled
Virtual core keyboard          keyboard
AT Translated Set 2 keyboard   extension
U+P Keyboard                   extension
Video Bus                      extension
U+P Keyboard                   extension
Macintosh mouse button emulation extension
Logitech Trackball             extension
Microsoft Microsoft IntelliMouse? Explorer extension
SynPS/2 Synaptics TouchPad     extension
Wacom Intuos4 4x6 eraser       extension
Wacom Intuos4 4x6 cursor       extension
Wacom Intuos4 4x6 pad          extension
Wacom Intuos4 4x6              extension
```

For an obvious reason, the stylus is the last line, but no stylus in the name, but taken in account in the fdi, strange, but this part works so I don't mind.

Here is the result of making a press on the wheel:
```
InputDevice: Wacom Intuos4 4x6 pad
Valuators: Relative   ID: Unreported  Serial Number: Unreported

             x-axis    y-axis   pressure  rotation  throttle    wheel
     data:  +00000    +00000    +00000    +00000    +00000    +00014
      min:  +00000    +00000    +00000    +00000    +00000    +00000
      max:  +31496    +19685    +02047    +00000    +00000    +01023
      res:  +01016    +01016    +00001    +00001    +00001    +00001


Proximity:  IN 
    Focus:
  Buttons:                                4-UP  
     Keys:

```
So if I go opposite with the wheel, the number 5 takes place of 4 above.

Any clue? I can use the tablet for the use I have but the ring is handy...
Thank you for you help.

---

### Post by Favux on 2009-09-12
Hi simonced,

Right.  Your custom_wacom.fdi is what is preventing the modified 10-wacom.fdi in post #176 from working.  It's executed later and so it's controlling the configuration.  That's why "xsetwacom list" is blank (and you're not seeing stylus in xinput) and wacomcpl is not working.  You have to remove the custom_wacom.fdi.

You can add the .fdi button lines to the 10-wacom.fdi if you want or do it through wacomcpl/.xinitrc.  Up to you.

---

### Post by simonced on 2009-09-13
Yes, it's what I did, I don't have custom_wacom anymore.
On the fdi thread/How to it's already well said to use only one file.
So my modifications are from the 10-wacom.fdi file.

---

### Post by Favux on 2009-09-13
Hi simonced,

My mistake.  You were showing your modifications to the default Jaunty 10-wacom.fdi.

That .fdi doesn't parse the names HAL is returning into linuxwacom names which is why wacomcpl isn't working.  This modified 10-wacom.fdi in post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)  does parse the names correctly.

---

