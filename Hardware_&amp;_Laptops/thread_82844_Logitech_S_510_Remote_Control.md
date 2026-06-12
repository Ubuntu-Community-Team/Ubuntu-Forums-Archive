---
title: "Logitech S 510 Remote Control"
date: 2005-10-27
forum: Hardware &amp; Laptops
---

### Post by ubernoob on 2005-10-27
When i bought the [Logitech Cordless Desktop S 510 Media]("http://www.logitech.com/index.cfm/products/details/US/EN,CRID=2162,CONTENTID=10711") my evil :twisted:  Windows friends just laught at me, and said I should save my money because i would never get the extra keys to work, and never get the remote control to work eiter. They also said I should buy  [a keyboard more appropriate for linux!]("http://www.3dluvr.com/grid/photo/oldkeyboard_%5B1%5D.jpg") :shock:

Now i really want to prove them wrong, and of course at the same time have a working remote control for my linux box. :)

I began my troubleshooting by starting up "xev".  My first problem is that my remote control doesn't give any response at all. And some of my keyboard buttons doesn't either. (I think this is the same problem.) The most typical keys work. Eg. volume up/down and mute. But zoom in/out plus some other don't give any response. Why? And how can i solve this? I'm already lost. ](*,)

---

### Post by ubernoob on 2005-10-31
anyone?

---

### Post by jordanm on 2006-02-02
Bump...

I just got one of these keyboards and was wondering the same. In particular I am wondering more about the remote.

Thanks, Jordan

---

### Post by minirx7 on 2006-02-06
Me TOO!!

---

### Post by Twizz on 2006-05-12
I'm thinking of buying this keyboard, and was wondering if anybody here had found out how to fix those issues.  Also was wondering what buttons (Mouse/keyboard) actually worked with linux so far.  I dont plan on getting the one with the controller.  I only really need the keyboard/mouse.

---

### Post by ubernoob on 2006-05-13
mouse works fine. And all the music stuff on the right side works. Even if the others don't work, this is the best keyboard i have ever owned, so it will be worth the money :)

The "mode" button with the extra keys from f1 to f12 doesn't work
and not the keys to the left

---

### Post by bmk789 on 2006-05-26
What do the music buttons work with? Theyre not working for me.
All the other keys except the ones down the left side and the shortcuts on the F keys.

---

### Post by Twizz on 2006-05-29
I bought the keyboard now it works great.  The only button that seems to work on the left side of the keyboard is the Home icon.  It brings up Firefox, wich is what I had it do on WIndows when I installed it.  On the right side all the buttons seem to work except the top icon to bring up the music player.  It worked on amerok for me, but I did not try any others since I only use amerok.  F Mode Key dosent work for me either.  Not to big of a problem though.  I really like the keyboard.

---

### Post by celafon on 2007-07-19
Good news :)

[http://www.kernel.org/pub/linux/kernel/people/jikos/random/hid-make-extra-keys-on-logitech-s510-work.patch](http://www.kernel.org/pub/linux/kernel/people/jikos/random/hid-make-extra-keys-on-logitech-s510-work.patch)

Looks like patch is there and should be in Ubuntu kernel soon (gutsy?).

Regards,
Bartek

---

### Post by Dragonstar on 2007-10-18
> **celafon said:**
> Good news :)

[http://www.kernel.org/pub/linux/kernel/people/jikos/random/hid-make-extra-keys-on-logitech-s510-work.patch](http://www.kernel.org/pub/linux/kernel/people/jikos/random/hid-make-extra-keys-on-logitech-s510-work.patch)

Looks like patch is there and should be in Ubuntu kernel soon (gutsy?).

Regards,
Bartek

Not in Gutsy, at least not yet. I also hope that this problem would be solved. It would be nice to  e.g change workplaces with zoom +/-.

---

### Post by Munk81 on 2007-11-10
> **Dragonstar said:**
> Not in Gutsy, at least not yet. I also hope that this problem would be solved. It would be nice to  e.g change workplaces with zoom +/-.

The kernel patch is in Gutsy, you have to activate it with module options for usbhid.


i.e. add a line in /etc/modprobe.d/options:
```

options usbhid quirks=0x46d:0xc517:0x100000

```

With this I get a kernel message "Nov 10 11:30:11 cinemaya kernel: [    7.232000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: Fixing up Logitech keyboard report descriptor",
however I still do not get X-Events for those keys on the keyboard.

---

### Post by hebetude on 2007-11-10
using the module option, I can use the home key now the follow keys don't do anything:
shuffle, rotate, zoom+/-, 100%

I'll tinker with it some more, Oh I agree no X events working.

The bug report mentions something about using evdev, I thought I was /boggle

Just for reference
cat /var/log/messages | grep keyboard
```

Nov 10 12:16:18 dumassA kernel: [   36.723637] input: AT Translated Set 2 keyboard as /class/input/input1
Nov 10 15:36:36 dumassA kernel: [12053.036000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: Fixing up Logitech keyboard report descriptor
Nov 10 16:31:35 dumassA kernel: [   47.773950] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: Fixing up Logitech keyboard report descriptor

```

---

### Post by aardfark on 2007-11-12
Has anyone else had trouble with this keyboard not working before the OS boots?  

I can hit DEL to get to my CMOS, but I'm trying to use GRUB to dual-boot a windows drive, and they keyboard isn't responding at all...

---

### Post by minimec on 2007-11-18
My friends.

Following the last advices of 'Munk81' and 'hebetude', I can happily announce that we are done! The Logitech s510 has no secrets anymore!

So this is what you have to do (Ubuntu Gutsy):

1)  Activate the kernel patch
 
> 

i.e. add a line in /etc/modprobe.d/options:

```


options usbhid quirks=0x46d:0xc517:0x100000

```


 

2)  Change your /etc/X11/xorg.conf using the evdev driver for keyboard and mouse device.

The biggest problem I had was to realize, that even if you don't use the wireless mouse that comes with the keyboard, you have to configure it to have all the buttons!

I also realized, that my hardware is always recognized as /dev/input/event1 (keyboard) and /dev/input/event2 (mouse).You can verify that with 'cat /proc/bus/input/devices'. So you don't have to mess around with udev and the "Phys" option in your xorg.conf (# "phys" is commented out in the example)

That leads us to a rather simple /etc/X11/xorg.conf (in my example a Logitech G5 Mouse is configured as CorePointer). I don't use the wireless mouse.


```


Section "ServerLayout"

    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Logitech s510 Keyboard"
    InputDevice    "Logitech s510 Mouse"	"SendCoreEvents"
    InputDevice    "Logitech G5 Mouse"	
EndSection

Section "InputDevice"
    Identifier     "Logitech s510 Keyboard"
    Driver         "evdev"      
#    Option          "Dev Phys"             "usb-0000:00:1f.2-1/input0"
    Option         "Device"                "/dev/input/event1"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "evdev"		
    Option         "XkbLayout" "ch"
    Option         "XkbVariant" "de"
EndSection

Section "InputDevice"
	Identifier	"Logitech s510 Mouse"
	Driver		"evdev"
#        Option          "Dev Phys"              "usb-0000:00:1f.2-1/input1"
        Option          "Device"                "/dev/input/event2"
	Option 		"SendCoreEvents"	"true"
	Option          "Name" "Logitech USB Receiver"
	Option		"Resolution"	"800"	
	Option		"Emulate3Buttons"	"false"
EndSection

Section "InputDevice"
	Identifier	"Logitech G5 Mouse"
	Driver		"evdev"
	Option		"CorePointer"
	Option          "Name" "Logitech USB Gaming Mouse"
	Option		"ZAxisMapping"		"4 5 6 7 8"
	Option		"Emulate3Buttons"	"false"
EndSection


```



These two steps give me the full power of the s510 Keyboard including the Remote Control! 

Happy configuring... ;)


P.S. @aardfark: I had the same problem when I plugged the receiver on an PCI USB card, rather than on the built in USB ports of the motherboard.
       @all: [https://answers.launchpad.net/ubuntu/+question/14320](https://answers.launchpad.net/ubuntu/+question/14320)  # Deactivate BulletProof X (Oh Lord It's a miracle...;) )

---

### Post by hebetude on 2007-11-18
My hero! I'm going to repost/link to this in some of the other s510 threads I started.

Thanks a lot

---

### Post by JacksonDane on 2007-12-02
Did this, and now my direction keys don't work. UP is working as Print Screen

---

### Post by Aathos on 2007-12-15
I had the same problem, with the up key acting like print screen, but I fixed it.  I am not really sure what did it, but here's what I did:  I went to System->Preferences->Keyboard and changed the Alt/Win key behavior from "default" to "Alt and Meta are on the Alt keys (default)" and under Third level choosers I checked "Press Menu to choose 3rd level."  I also looked at the available keyboard models, without changing anything, and selected a default layout.  I don't know what exactly fixed it, but at least it is a place to start.  

However, I have had a few other problems.  The biggest is that the start key does not work as super, according to xmodmap and xev it is mapped to Super_L, but it isn't being recognized as a modifier key, so I can't use it for shortcuts i.e., Super+Tab.  This functionality is used a lot in compiz. 

Lesser issues are that some of the buttons on the left side are copies of buttons on the right.  For example: Zoom + is next track, 100% is play/pause, and Rotate is volume up. 

I don't know if it makes any difference, but I changed the "XkbLayout" to us, and the "XkbVariant" to dvorak in the xorg.conf.

Despite these few issues, I am very grateful for the work that has been done to support this keyboard.

---

### Post by floquet on 2008-01-16
Thanks for the information. It was really helpful with my keyboard S510.

During this configuration I've had a lot of problems as my GDM will not start. The log said that "can not start the keyboard but I finally found that the problem was in the mouse. As stated in this thread, if the mouse is not properly configured, then the keyboard will not work properly. I had to add then an option to the mouse device in the xorg.conf

Option     "CorePointer"

After this the system was able to start like a charm.

Thanks a lot

---

### Post by desmane on 2008-02-21
Hello people, 

I am watching this thread since the beginning (got the same evil windows friends by the way :) ), and have finally forgotten that there is something like zoom keys. But while activating the kernel patch in modprobe options, I actually felt my heart beating faster \\:D/ So it works, thanks to minimec!!

For those of you, who have problems with the arrow keys, make sure you go to the keyboard preferences, tab to layouts and select keyboard model *evdev-managed keyboard* if it did not happen automatically. The logitech models wont work here. 


**_BUT_**

the thing is that I personally care about the remote only.. it would have been too easy ey??

Now those extra keys act funny, the zoom in and rotate are recognized as next track or raise volume or whatever, the document key is rotate and the fast forward and backward keys still active same as track forward / backward. Since I dont use the F-Mode anyway, there is not really a enhancement as far as I am concerend. 

Is there a cure? :-k or any chance to get this fixed in 8.04? Should it be reported? :confused:

Thanks for any help!!

---

### Post by desmane on 2008-02-21
just to clarify the prev post: 

_THE KERNEL PATCH_

```
static void hidinput_configure_usage(str
 				case 0x302: map_key_clear(KEY_PROG2);		break;
 				case 0x303: map_key_clear(KEY_PROG3);		break;
 
+				/* Reported on Logitech S510 wireless keyboard */
+				case 0x101f: map_key_clear(KEY_ZOOMIN);		break;
+				case 0x1020: map_key_clear(KEY_ZOOMOUT);	break;
+				case 0x1021: map_key_clear(KEY_ZOOMRESET);	break;
+				/* this one is marked as 'Rotate' */
+				case 0x1028: map_key_clear(KEY_ANGLE);		break;
+				case 0x1029: map_key_clear(KEY_SHUFFLE);	break;
+				case 0x1041: map_key_clear(KEY_BATTERY);	break;
+				case 0x1042: map_key_clear(KEY_WORDPROCESSOR);	break;
+				case 0x1043: map_key_clear(KEY_SPREADSHEET);	break;
+				case 0x1044: map_key_clear(KEY_PRESENTATION);	break;
+				case 0x1045: map_key_clear(KEY_UNDO);		break;
+				case 0x1046: map_key_clear(KEY_REDO);		break;
+				case 0x1047: map_key_clear(KEY_PRINT);		break;
+				case 0x1048: map_key_clear(KEY_SAVE);		break;
+				case 0x1049: map_key_clear(KEY_PROG1);		break;
+				case 0x104a: map_key_clear(KEY_PROG2);		break;
+				case 0x104b: map_key_clear(KEY_PROG3);		break;
+				case 0x104c: map_key_clear(KEY_PROG4);		break;
+
 				default:    goto ignore;
 			}
 			break;
```

_THE MISBEHAVIOURASDFLASDING KEYS:_

KEY_ZOOMIN = AUDIONEXT
KEY_ZOOMOUT = EJECT (SO ACTUALLY IS A NEW KEY)
KEY_ZOOMRESET = AUDIO PLAY
KEY_ANGLE = RAISE VOLUME
KEY_SHUFFLE = KEY_ANGLE = RAISE VOLUME


I used xev, the keyboard shortcuts preferences in gnome, and grab key function in xbindkeys-config... I got the latest gnome, using Ubuntu 7.10 Gutsy Gibbon. 

_My Xorg.conf: _

```

Section "Files"
EndSection

Section "InputDevice"
	Identifier "Logitech s510 Keyboard"
	Driver "evdev"
	# Option "Dev Phys" "usb-0000:00:02.1-2/input0"
	Option "Device" "/dev/input/event1"
	Option "CoreKeyboard"
	Option "XkbRules" "xorg"
	Option "XkbModel" "evdev"
	Option "XkbLayout" "de"
	#Option "XkbVariant" "de"
EndSection

Section "InputDevice"
	Identifier "Logitech s510 Mouse"
	Driver "evdev"
	# Option "Dev Phys" "usb-0000:00:02.1-2/input0"
	Option "Device" "/dev/input/event2"
	Option "SendCoreEvents" "true"
	Option "Name" "Logitech USB Receiver"
	Option "Resolution" "800"
	Option "Emulate3Buttons" "true"
	Option "CorePointer"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AR [Radeon 9600]"
	Driver		"ati"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"Acer AL2216W"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AR [Radeon 9600]"
	Monitor		"Acer AL2216W"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1050" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Logitech s510 Keyboard"
	InputDevice "Logitech s510 Mouse" "SendCoreEvents"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

```

okay and to make it complete, here is my modprobe.d options

```
# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2

# Logitech
options usbhid quirks=0x46d:0xc517:0x100000
```



Any ideas would be very much appreciated thanks a lot!!

---

### Post by desmane on 2008-04-06
anybody?     [-o<

---

### Post by njbair on 2008-05-03
When I try this setup the mouse only moves up and down and it won't move side to side. Everything else seems to work fine (as far as I can tell without using the mouse). Reverting to generic mouse and kb in xorg.conf makes the mouse work fine again. I have tried this multiple times with the same result.

---

### Post by minimec on 2008-07-04
My dear friends

&#8222;Hope is a good thing, maybe the best of things, and no good thing ever dies.&#8220;
*(Tim Robbins as Andrew Dufrense in 'The Shawshank Redemption')*

There has been a lot of changes in 'xorg' and 'evdev' with Ubuntu Hardy. As a result the 'gutsy' configuration for our beloved Logibaby S510 is not working anymore. 

Here are the changes:

- The famous 'Quirks'-Patch that some of you may have activated in /etc/modprobe.d/options is integrated in the 2.6.24.** Ubuntu Kernel. So you can delete this.

**- This means that our Logitech S510 is basically supported by Ubuntu Hardy including the missing Zoom +/-, 100%, Rotate and Shuffle!!! (handled by the keyTouch software)**

- The 'evdev' Driver is not needed anymore to configure your keyboard and mouse. You can use 'kbd' and 'mouse' as your keyboard and mouse driver.

- The Logitech S510 is 100% supported by keyTouch 2.4.0.beta. 


Here is the announcement ([http://keytouch.sourceforge.net](http://keytouch.sourceforge.net))

*You can now use all your extra function keys on a USB keyboard too. All required kernel patches are included since Linux kernel 2.6.24. Use this kernel (or a later version) in combination with keyTouch-editor 3.2.0 beta to create keyboard files for your USB keyboard. The created keyboard file can then be imported in the latest beta verion of keyTouch (version 2.4.0 beta). KeyTouch-editor 3.2.0 beta allows you to create one keyboard file for both a PS/2 and USB connection. So after you have added all the keys to the keyboard file while the keyboard was connected via USB, you can then connect the keyboard via PS/2 and set the PS/2 scancode of the key too. If discover any bugs in keyTouch-editor or keyTouch please report them. *


**_Installation keyTouch 2.4.0 beta_**

In our case that means, that we have to compile the new keyTouch Software (version 2.4.0 beta). I also compiled the KeyTouch-editor 3.2.0 beta, as I had to create the keyboard files for me and specially for you ... ;)

You can get the Software here:

keyTouch 2.4.0 beta: [http://sourceforge.net/project/downloading.php?groupname=keytouch&filename=keytouch-2.4.0.tar.gz&use_mirror=dfn](http://sourceforge.net/project/downloading.php?groupname=keytouch&filename=keytouch-2.4.0.tar.gz&use_mirror=dfn)

keyTouch-editor: [http://sourceforge.net/project/downloading.php?groupname=keytouch&filename=keytouch-editor-3.2.0-beta.tar.gz&use_mirror=heanet](http://sourceforge.net/project/downloading.php?groupname=keytouch&filename=keytouch-editor-3.2.0-beta.tar.gz&use_mirror=heanet)

The compilation is rather simple:

- sudo apt-get install libasound2-dev  <--- This is the only dependency you need to compile keyTouch 2.4.0. beta.

- Follow the instructions of the IMPORTANT-INSTALLATION file of keyTouch. The compilation is basically './configure', 'make', 'sudo make install'. The compilation is very easy!

- After you compiled and installed keyTouch you will have the keyTouch-Daemon running after the next boot. 

- The compilation of keyTouch-editor is even simpler, but I guess you don't need the editor.

- You won't have any menu entries for the keyTouch software. Use 'alacarte' to create one or start the software with <Alt><F2>keytouch.


**_The configuration of keyTouch_**

To use keyTouch with your S510 Logibaby you have to import a keyfile for the keyboard. Working on this file I realized, that depending the use of your special keys, you may want a different key file. Example: Let's take the 'a-b-c-d' buttons. Until now, I was able to use them in almost any way I wanted with the quiet powerful shortcut tool of my WM Enlightenment e17. If I would mention them in the keyTouch keyboard file, I would loose this flexibility, as the keyTouch Software would handle them, and I would be limited to the different plugin functions of keyTouch. Same thing with the 'audio buttons'. As the Gnome shortcut tool handles them pretty well as multimedia buttons, there is no reason to change that, because I can use them with more than just one music player. I can use them with Rhythmbox or Exaile for example. If I added these 'audio keys' to the keyTouch file, I would be limited to the plugin architecture of keyTouch, or I would have to use command line options  like 'exaile --next' or 'exaile --stop' to make use of the buttons in combination with Exaile.

In the end I created 3 files:
*(As you can always change the keyboard with keyTouch, you may want to import them all)*

S510-minimal-alpha.Logitech / S510-minimal-remote-alpha.Logitech
(Zoom +/-, 100%, Rotate, Shuffle)

S510-minimec-alpha.Logitech / S510-minimec-remote-alpha.Logitech
(Undo, Redo, Print, Save, Zoom+/-, 100%, Rotate, Shuffle) 

S510-full-alpha.Logitech / S510-full-remote-alpha.Logitech
(all possible special keys of the S510)

These files should work plugging the Keyboard via USB. I cannot tell you if they work with PS/2, as my S510 version doesn't have a PS/2 connection. 

The 'remote' versions add the missing buttons for those lucky guys like me, who have the S510 Remote Control. (Menu, Maximize, Close, Preset 1-3, Back, MEDIA). The 'rewind/fastforward' buttons are mapped to 'previous/next'. They give the same keycode. 

The files are marked 'alpha' because there may be some changes in the future. I will contact the keyTouch developers and send them my keyboard files. So I guess we will have official support for the s510 with the final release of  keyTouch 2.4.0. 


**_/etc/X11/xorg.conf example_**

Section "ServerLayout" 
    Identifier     "Default Layout" 
    Screen      0  "Screen0" 0 0 
    InputDevice    "Generic Keyboard" 	# not needed anymore in Hardy Heron
    InputDevice    "Configured Mouse"	# not needed anymore in Hardy Heron
EndSection 

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option          "CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"ch"
	Option		"XkbVariant"	"de"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option          "CorePointer"
	Option		"Protocol"		"auto"
	Option		"ZAxisMapping"		"4 5 6 7"
	Option		"Buttons"		"7"
EndSection

There seem to be some problems with the 'tilt-wheel' function of the mouse. I also realized, that the mouse is not working correctly, using the 'evdev' driver. The bugs have been filed by others in Launchpad. As I don't use the mouse, I don't want to focus on that. If you have some ideas... ;) 


Let me finish with this...

&#8220;I hope that this letter finds you and finds you well...&#8221;
*(The Shawshank Redemption)*

Your Minimec.

---

### Post by paulderol on 2008-07-09
is there a reason that this might break human theme? or AWN? or wouldn't work as intended?

i am suffering from all three.

human-gnome can't find some of its bits, AWN's power/logoff button is now simply gone, replaced by its placeholder line, and i still can't zoom. is this whole bit incompatible with compiz in general? 64-bit architectures? did i just do it wrong?

keytouch builds, runs, and even identifies my keys properly, but i cannot get it to zoom. should i change something in compiz? in gnome? in keytouch? in gtk?

AAAAH.

---

### Post by minimec on 2008-07-10
Hi

Even if my default WindowManager is Enlightenment e17, I started a gnome/compiz session, regarding the problems you have. 

- I cannot confirm your problems neither with your theme settings nor with the avant-window-navigator. They seem to work ok with my system (32-bit). 

- It is possible that you need to reassign some buttons in the gnome shortcuts tool (Quote: AWN's power/logoff button is now simply gone).

- I have to agree with you, that the Zoom function is not working for me with the 'Enhanced Zoom Plugin' of compiz (even though it was a few days ago...), but I can use the Zoom Buttons with the Picture Viewer (Eye of Gnome). Looks like the Zoom Plugin of Keytouch is ok. Can you confirm that?

regards minimec

---

### Post by minimec on 2008-07-10
Hi

Even if my default WindowManager is Enlightenment e17, I started a gnome/compiz session, regarding the problems you have. 

- I cannot confirm your problems neither with your theme settings nor with the avant-window-navigator. They seem to work ok with my system (32-bit). 

- It is possible that you need to reassign some buttons in the gnome shurtcuts tool (Quote: AWN's power/logoff button is now simply gone).

- I have to agree with you, that the Zoom function is not working for me with the 'Enhanced Zoom Plugin' of compiz (even though it was a few days ago...), but I can use the Zoom Buttons with the Picture Viewer (Eye of Gnome). Looks like the Zoom Plugin of Keytouch is ok. Can you confirm that?

regards minimec

---

### Post by aelfwyne on 2008-07-11
This does not work on Ubuntu Hardy for me.

I installed & ran Keytouch, but when I go to import the file, it gives me an error:
"The syntax version of the keyboard file is not compatible with this version of keytouch"..

(Yes, I extracted the .tar, and attempted to use the Full version for the remote)

I installed from Synaptic, version 2.3.2-2.

EDIT:

Oh... now I see you used a newer version of keytouch than is available through the repository...

*sigh*... NOTHING is ever simple is it?

---

