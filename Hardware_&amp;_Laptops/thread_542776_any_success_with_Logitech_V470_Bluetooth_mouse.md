---
title: "any success with Logitech V470 Bluetooth mouse?"
date: 2007-09-04
forum: Hardware &amp; Laptops
---

### Post by zeus77 on 2007-09-04
I'm thinking about getting myself a Bluetooth mouse... I'm curious if anyone has had luck with the Logitech V470?

Thanks.
zeus77

---

### Post by thetor on 2007-09-04
The v470 looks interesting. I have also been considering getting one, but I didn't think it was out yet?

---

### Post by zeus77 on 2007-09-04
guess you're right -- not out yet...

---

### Post by neokod on 2007-10-10
Hi,

I'm thinking to getting this mouse too.
It's seems to be available now, is anyone have tested it ?

Or if anyone have feedback about logitech blutooth, it's interesting too.

Thanks

---

### Post by Jiipbe on 2007-10-12
Guys. I have it and it's great. It has all the simple features I need, to connect it through the bluetoothed laptop went like a dream and I use it all the time under both XP and Linux. Simple like a charm, looks great, I'm in love ;-)

---

### Post by neokod on 2007-10-15
Hi !

I have it too, but this doesn't works for me. I'm under gutsy / gnome and I have only tested with the bluetooth gnome applet.

When I choose "browse" in the bluetooth applet, the "Bluetooth Laser Travel Mouse" is detected in the liste, but if I select it and clic on the "Connect" button I have this error :

"« obex://[00:07:61:97:2b:e9] » is not a valid location"

Jiipbe, can you tell me if you uses Gutsy under Gnome, and which options you have set in the bluetooth applet please ?

Thanks a lots


PS: This mouse is really beautiful !

---

### Post by neokod on 2007-10-15
Problem found, the package gnome-vfs-obexftp wasn't installed.

It's works great now ! :-)

---

### Post by Laterix on 2007-10-17
I got the mouse today and it seems good. Does anyone know how to get tilt wheel to work under Linux.

---

### Post by ljonesj on 2007-10-17
were can you buy this mouse and what does it look like
never mind i saw a pic thinking of buying a mouse for my gaming computer that is still windows and using a trackball mouse for my linux computer as i sit at a couch will on the internet

---

### Post by meastp on 2007-10-20
Tried the mouse with gutsy/7.10 today, and I'm impressed! The only thing I had to do was to open the bluetooth applet -> input devices -> add mouse.

---

### Post by steveneddy on 2007-10-20
I use the V270 and it works very well with Gutsy.

---

### Post by ifixit on 2007-10-21
> **meastp said:**
> Tried the mouse with gutsy/7.10 today, and I'm impressed! The only thing I had to do was to open the bluetooth applet -> input devices -> add mouse.

Eh?  I'm having a world of trouble getting my Logitech V270 mouse to work.

So far, the only thing which seems to permit the mouse to function is to run *hidd --connect *from the command line after every boot, which is rather less than convenient.

In the Bluetooth Applet installed on my clean 7.10 box, I find your example to be completely bizarre.  There are no items labeled "input devices," or "add mouse."  In fact, the only useful-ish function that the applet seems able to perform is "Browse Device," beyond which is a "Connect" button which consistently returns cryptic OBEX error messages instead of actually working.

What am I missing?

---

### Post by meastp on 2007-10-22
> **ifixit said:**
> Eh?  I'm having a world of trouble getting my Logitech V270 mouse to work.

So far, the only thing which seems to permit the mouse to function is to run *hidd --connect *from the command line after every boot, which is rather less than convenient.

In the Bluetooth Applet installed on my clean 7.10 box, I find your example to be completely bizarre.  There are no items labeled "input devices," or "add mouse."  In fact, the only useful-ish function that the applet seems able to perform is "Browse Device," beyond which is a "Connect" button which consistently returns cryptic OBEX error messages instead of actually working.

What am I missing?

I'm sorry if my example was too rough.

What I did was:
Right-click bluetooth applet
Properties
Services-tab
click input service (make sure it is running (checked))
Add...
select your device (turn on and click connect-button underneath)
click connect

this was all I did

then the mouse showed up in vonded devices...

you may have to experiment with mode of operation and paerhaps check  "automatically authorize incoming requests" I don't remember if I did this before, or after I had connected my mouse.

Any success?

---

### Post by NilsE on 2007-10-22
If all else fails you can do this

Change this line in /et/default/bluetooth

HIDD_OPTIONS="--connect 00:02:61:82:32:b2 --server"

Replace the address with yours

---

### Post by Jiipbe on 2007-11-05
It seems that some can have a little bit of trouble with pairing their bluetooth mouse.

Basically just follow these instructions :

[http://www.linuxquestions.org/linux/answers/Hardware/Bluetooth_Transferring_and_receiving_files_under_Ubuntu](http://www.linuxquestions.org/linux/answers/Hardware/Bluetooth_Transferring_and_receiving_files_under_Ubuntu)

Bluetooth is Bluetooth, Right?

By the way if some of you have a clue on how to make the side buttons function on my Logitech V470, I would very much appreciate the help. Tried evdev but then my video card didn't work anymore!! 

Thank you

---

### Post by Jiipbe on 2007-11-16
Bump

how to get the side buttons to work with this mouse? 

Heeeelllllpppppp!!

---

### Post by monchote on 2007-11-29
Hi everybody!

I'm planning to buy this mouse, but first I'd like to know about a couple of details I'm doubting about:

-Does it start working automatically when you start Gutsy or XP (I'm using both).
-Is it possible to have it paired and working with both OS's (not at the same time but depending on which one you boot). I had some problems doing this with my sonyericsson cellphone.

Thanks a lot in advance.

Cheers!

---

### Post by meastp on 2007-11-30
> **monchote said:**
> Hi everybody!

I'm planning to buy this mouse, but first I'd like to know about a couple of details I'm doubting about:

-Does it start working automatically when you start Gutsy or XP (I'm using both).
-Is it possible to have it paired and working with both OS's (not at the same time but depending on which one you boot). I had some problems doing this with my sonyericsson cellphone.

Thanks a lot in advance.

Cheers!

- I had some problems pairing the mouse in XP, because there is no passphrase for the mouse. Solved this by setting bluetooth security to low.
- Works in Gutsy, and starts working on boot.

---

### Post by gottferdamnt on 2007-12-08
Is there a middle click (wheel button)? On  logitech website I see that the middle button is used to zoom. A middle click is pretty usefull in ff. I hope It works.

---

### Post by meastp on 2007-12-21
Yes, you can click the mouse wheel.

---

### Post by phenolholic on 2008-01-27
ok i followed the instructions. installed the obex app, went to bluetooth preferences > settings > input devices and added my mouse, and even added it to the bluetooth config file with the HIDD_OPTIONS="-i xx:xx:xx:xx:xx:xx --server"
the mouse connects, but theres still no activity (as if it never really connects). it might have to do with the fact i have touchscreen laptop and a touchpad, which had me heavily modify my xorg. any suggestions towards what i should do and/or posting of your xorg would be great. thanks in advance

---

### Post by steveneddy on 2008-02-21
I just bought the new V470 and this thing rocks!

---

### Post by avdzm on 2008-02-23
Hey all,
I just bought the v470, and it's sweet.
It's connect with out any problems,

only that i have to turn it off/on when i restart the laptop.
I can't however get the horizontal scrolls to work.

This is what i've added in xorg.conf any ideas??
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse" or "eyedev"
	Option		"Device"    "/dev/input/event2"
	Option		"CorePointer"
	Option		"Buttons" "7"
	Option		"ZAxisMapping" "4 5"
	Option		"ButtonMapping" "1 2 3 6 7"
	Option		"Emulate3Buttons"	"false"
	Option		"Name"	"Bluetooth Laser Travel Mouse"
EndSection

```

thanks

---

### Post by meastp on 2008-02-24
Hi!

As stated earlier in this thread, my v470 works perfectly, and the only thing I did was connecting and pairing it in the Bluetooth Applet. However, my horizontal scroll buttons / configurable buttons did and does not work with this simple method.

If anyone has had luck with these buttons, please tell us how.

This is the extract of my (auto-generated) xorg.conf file:

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

```

---

### Post by emheo on 2008-02-26
Side buttons work perfectly fine over here with 10mins effort :cool:
Try the following and enjoy.. (I guess you guys only need the stuff in /etc/X11/xorg.conf, added the rest for sake of completeness)

**1. load modules**
use modprobe and add to your /etc/modules
[LIST][*]evdev
[*]ushid[/LIST]

**2. identify mouse**
cat /proc/bus/input/devices
```
...
I: Bus=0005 Vendor=046d Product=b008 Version=0314
N: Name="Bluetooth Laser Travel Mouse"
P: Phys=<<your phys id>>
S: Sysfs=/class/input/input9
U: Uniq=<<your uniq id>>
H: Handlers=mouse3 event9
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=143
...
```

**3. modify touchpad to be a corepointer in /etc/X11/xorg.conf**
```

Section "InputDevice"
    Identifier "Synaptics Touchpad"
    Driver "synaptics"
    option "SendCoreEvents" "true"
    option "Device" "/dev/psaux
    option "Protocol" "auto-dev"
    option "HorizScrollDelta" "0"
    Option "CorePointer"
EndSection
```

**4. enable HHID for bluetooth**
In /etc/defaults/bluetooth set
```
HIDD_ENABLED=1
HIDD_OPTIONS="-i <<your uniq id>> --server"
```

add to /etc/bluetooth/hcid.conf:
```

    device <<your uniq id>> {
    name "Bluetooth Laser Travel Mouse";
    }

```

**5. Connect mouse**
I'm on kde, thus as outlined before:
[LIST][*]Right-click bluetooth applet
[*]Properties
[*]click input service
[*]Add...
[*]select your device (turn on and click connect-button underneath)
[*]click connect[/LIST]

**6. add mouse to xorg.conf**
Add new Input Device section
```

Section "InputDevice"
    Identifier "v470"
    Driver "evdev"
    Option "Name" "Bluetooth Laser Travel Mouse"
    Option "Dev Phys" "<<your phys id>>"
    Option "HWHEELRelativeAxisButtons" "7 6"
    Option "SendCoreEvents" "true"
EndSection
```

then add it to the Server Layout
```

Section "ServerLayout"
    Identifier "Default Layout"
    screen 0 "Default Screen" 0 0
    InputDevice "Generic Keyboard"
    InputDevice "v470"
    InputDevice "Synaptics Touchpad"
EndSection
```

**7. restart X**
Ctrl+Alt+Del

**8. verify buttons**
open konsole, then launch xev
In the window you should see button 6 for left scroll and button 7 events for right scrolls
It should work in Firefox and all other apps from here on

---

### Post by avdzm on 2008-02-26
Hey emheo,
Thanks a lot, my horizontal scrolling works perfectly!!! YEEPEE!!!

By default firefox doesn't support horizontal  scrolling,
the horizontal buttons perform as history actions, back and forward.

to scroll, i found this link and now i can scroll horizontally (in firefox). 
[http://www.macosxhints.com/article.php?story=20050821141856688](http://www.macosxhints.com/article.php?story=20050821141856688)

one more time, YEEPEE!!!

Hey emheo,
I want to ask, what happens when you reboot/restart your computer with the v470 still on?

with me, it doesn't reconnect, i have to turn the mouse off/on to get it connected,
not a big thing, just wondering...

thanks for your help

---

### Post by meastp on 2008-02-27
> **avdzm said:**
> Hey emheo,
Thanks a lot, my horizontal scrolling works perfectly!!! YEEPEE!!!

By default firefox doesn't support horizontal  scrolling,
the horizontal buttons perform as history actions, back and forward.

to scroll, i found this link and now i can scroll horizontally (in firefox). 
[http://www.macosxhints.com/article.php?story=20050821141856688](http://www.macosxhints.com/article.php?story=20050821141856688)

one more time, YEEPEE!!!

Hey emheo,
I want to ask, what happens when you reboot/restart your computer with the v470 still on?

with me, it doesn't reconnect, i have to turn the mouse off/on to get it connected,
not a big thing, just wondering...

thanks for your help

I have no problems with rebooting my computer with the v470 powered on. The intention of this power switch, I believe, is to prevent "accidents" under transport. So it should work, because the mouse will shut down/suspend automatically.

Could you post your xorg.conf?

---

### Post by avdzm on 2008-02-27
```

Section "InputDevice"
	Identifier	"v470"
	Driver		"evdev"
	Option		"Name"	"Bluetooth Laser Travel Mouse"
	Option		"Dev Phys" "00:03:7A:D5:3F:28"
	Option		"HWHEELRelativeAxisButtons" "7 6"
	Option		"SendCoreEvents" "true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
	Option 		"CorePointer"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	InputDevice 	"v470"
	Inputdevice	"Synaptics Touchpad"
EndSection

```

Let me know if you want the whole xorg.conf file or any other file.

---

### Post by emheo on 2008-02-27
avdzm,
did another reboot to verify and even without switching the mouse off, it still reconnects automatically and is instantly available. All I did is described above.
Even if I boot with the mouse switched off, as soon as I switch it on it's available without any other steps.
I'd think that this must be related to your /etc/defaults/bluetooth and /etc/bluetooth/hcid.conf. Did you make sure that you have your uniq id in there and not the phys id?

---

### Post by steveneddy on 2008-02-27
Using Blueman seems to help my bluetooth situation. It just connects easier with Blueman.

---

### Post by avdzm on 2008-02-27
Ok,
I don't know if this changes anything, how did u connect ur mouse?
I went to bluetooth preferences,
then Services,
I click on Input service and added the mouse.

---

### Post by avdzm on 2008-02-28
Hey all,
Well i figured out why it wasn't connecting at boot,
I didn't see the semicolon ";" and the end of...
```

device <<your uniq id>> {
    name "Bluetooth Laser Travel Mouse";
}
```

now it connects, Yeepee!!!

however i have a new problem  :(

at login my mouse doesn't move,
but when i press ctrl+alt+backspace and enter the terminal,
i move the mouse and i see this messages,

Feb 28 18:42:58 avdzm-laptop kernel: [   96.888000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 42
Feb 28 18:42:58 avdzm-laptop kernel: [   96.900000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 42
Feb 28 18:42:58 avdzm-laptop kernel: [   96.912000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 42
Feb 28 18:42:58 avdzm-laptop kernel: [   96.924000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 42
Feb 28 18:42:58 avdzm-laptop kernel: [   96.932000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 42
Feb 28 18:42:58 avdzm-laptop kernel: [   96.944000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 42
Feb 28 18:42:58 avdzm-laptop kernel: [   96.956000] hci_acldata_packet: hci0 ACL packet for unknown connection handle 42

so my guess is, it connects the mouse but doesn't recognize it.

when i turn the mouse off/on it connects fine.

any ideas?

I checked the files again, with emheo's example, 
everything seems correct at least with syntax.

---

### Post by emheo on 2008-02-28
Check [https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/79394](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/79394)

what does hciconfig status say?
Does this help to restart as described?
My last guess, sorry

Did [my earlier post]("http://ubuntuforums.org/showthread.php?p=4409476#post4409476") work for anyone else?

---

### Post by avdzm on 2008-02-28
YEEPEE!!!
yup that fixed it,
Thanks a lot Emheo!

I can't believe that this bug still exists. 
According 
[https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/79394](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/79394)
Post date.

Anyway thanks again

---

### Post by thorcik on 2008-03-14
> **emheo said:**
> Did [my earlier post]("http://ubuntuforums.org/showthread.php?p=4409476#post4409476") work for anyone else?

In my case the only think it did accomplish was disturbing the nvidia driver, forcing my screen to 640*480 resolution and denying the driver any ability to change it. it didn't enable the side buttons. so I reverted to the earlier xorg.conf and it works just fine, I am willing to sacrifice the side buttons in the name of fully operational screen ;o)

oh, maybe the problem is that the ushid module didn't load, it doesn't seem to be avaible on my system.

edit: but the white mouse looks awesome :o)

---

### Post by achutammurarka on 2008-04-20
I downloaded the package gnome-vfs-obexftp and installed it using sudo apt-get install.

Then i tried connecting to my Logitech V 470 mouse 

It says....

Couldn't display "obex://[00:07:61:96:5f:07]".
Check if the service is available.

Comments: My mouse was on at that time.

Can some one pls help.....i am new to linux so please elaborate clearly what i need to do

Thanks

---

### Post by kkjaergaard on 2008-04-25
> **achutammurarka said:**
> It says....

Couldn't display "obex://[00:07:61:96:5f:07]".
Check if the service is available.

I have the same problem. I have gnome-vfs-obexftp and the mouse was switched on.

I'm using Debian.

---

### Post by Ryback on 2008-05-22
Many thanks emheo and avdzm, just picked up this mouse today and the side scrolling is working great with evdev.

---

### Post by huck416 on 2008-05-22
emheo,

Followed your guide (very well explained btw) but it crashes my x-server on restart. KDM says it's loading but the video is garbled. Have to restart in recovery mode and auto fix the x-server which replaces the xorg.conf with the previous version. 

My v470 works generally fine; loads every time at boot but my side scroll doesn't work. Vertical scroll and middle button fine. 

Any thoughts on why it's crashing the video? Thanks.

---

### Post by Eskas on 2008-06-14
sidescrolling doesn't work for me either. I'm using hardy. Seems like there must be some difference between hardy and gutsy. Has anyone got this to work in hardy?

I've followed the instructions from emheo, and get the mouse to work. But not the sidescrolling features.

The log file of the xserver says:

(EE) v470: No Device specified.
(II) UnloadModule: "evdev"
(EE) PreInit returned NULL for "v470"

---

### Post by trevelyon on 2008-06-24
I also have the mouse working well except for horizontal scrolling.  I'm running Hardy here on 2 laptops.  Interesting thing is that if I sudo cat /dev/input/mouse2 (mouse2 is for the v470) I see input from motion and forward / back scrolling but no input at all from horiz scrolling.  This seems to indicate a problem in the evdev kernel module or parameters to it.  Does anyone on Hardy, or 2.6.24-19 kernel, have this working?

Special thanks to emheo and avdzm for their posts here.

---

