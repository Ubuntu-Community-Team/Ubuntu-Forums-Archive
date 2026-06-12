---
title: "Laptop Touchpad How-To"
date: 2004-11-10
forum: Hardware &amp; Laptops
---

### Post by DoubleDangerClub on 2004-11-10
What everyone has been waiting for:

Laptop Touchpad How-To
----------------------------------------------------------
This How-To guide applies to all synaptics touchpads (if you have a laptop, it's more than likely what you have in it as the touchpad).

Open a terminal window and type:  sudo gedit /etc/X11/XF86Config-4

Go to the section:  Section "Module"
Add this line inside this section:  Load     "synaptics"

This line loads your synaptics touchpad settings at startup.
Now, as you scroll down, there should be a section that starts like this:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"

In this section, delete the line that says:  Option     "CorePointer"
This will make sense later on, as the external mouse will be secondary to the touchpad.

As you scroll down further, you should see this section:

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver           "synaptics"
        Option          "SendCoreEvents"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
EndSection

Delete the line that says:  Option      "SendCoreEvents"
Add a line that says:  Option      "SHMConfig"     "on"
The line you deleted will make sense later, as we will make the touchpad the primary pointer device.
The additional line enables your touchpad settings.

Finally scroll down to the bottom and you'll see this section:

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Change the last two lines to look like this:
	InputDevice	"Configured Mouse"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"	"CorePointer"

These additions will make the system set the touchpad to the primary pointer device and the external mouse as the secondary device.

Save the file and reboot!


You thought it was over?  Almost.  We now want to set our settings:
If you open a terminal window and type:  synclient -l
This shows you all of your touchpad settings.
If you reset any of the settings, you will lose them when you log out, so what we need to do is open the config file again:

sudo gedit /etc/X11/XF86Config-4

Now, scroll down to the section that starts like this:

Section "InputDevice"
        Identifier      "Synaptics Touchpad"

Inside this section, you will want to add your settings.
Open another terminal window and type: synclient -l
Now look at the setting you would like to change (I'm going to demonstrate turning off the tap click and the vertical and horizontal scrolling on the side and bottom of the touchpad).  Look at the name of the setting and enter it in this fashion:

	Option		"MaxTapTime"	       "0"
	Option		"VertScrollDelta"	"0"
	Option		"HorizScrollDelta"	"0"

Now save your file and reboot.  All done!!

If you go out on the net, you can find more references to synclient.  I have even caught wind of a GUI version of the settings manager, but this is the most effective way I found to get it done.

I hope this helps.  I was frustrated and finally figured it out, so good luck, and if you have questions about it, feel free to message me.

- Jake a.k.a. DoubleDangerClub

---

### Post by themicah on 2005-01-31
Disclaimer:  I am an almost total newbie.  Please don't assume I know anything. :)

I'm trying to get Ubuntu up and running on a POS Sony PCG-FX250K laptop, and I've been pretty happy so far except that I can't get the scroll function on my touchpad to work.

I've tried fllowing the directions in this thread, and when I make the suggested changes GNOME breaks after the first restart.  Restoring the original XF86Config-4 file and rebooting restores GNOME.

I've double-checked everything and am pretty sure I've followed the directions perfectly.  Is there perhaps a typo in these directions?

---

### Post by unperson on 2005-02-02
I don't claim to understand the X configuration file, but I found I was able to change the touchpad behavior without the lengthy process DoubleDangerClub describes.  I simply added the line

```
Options        "HorizScrollDelta"    "0"
```

to the options in the synaptics section of my /etc/X11/XF86Config file in order to turn off the annoying horizontal scroll feature (which makes you go back and forward in the history in firefox).  Now, this way you can't change settings on the fly as you can if you do it the way DoubleDangerClub describes, but for me that's ok, because I don't need to change my touchpad settings very often.

Two other links that may be of interest:

[http://www.ubuntulinux.org/wiki/SynapticsTouchpadHowto](http://www.ubuntulinux.org/wiki/SynapticsTouchpadHowto)
[http://wiki.debian.net/index.cgi?SynapticsTouchpad](http://wiki.debian.net/index.cgi?SynapticsTouchpad)

---

### Post by themicah on 2005-02-02
Thanks for the reply.

I've since tried this a couple more times, all with the same results: gnome fails to start after altering the XF86Config-4 file.

But I think I may have found the problem:  in Windows, my computer says it has an Alps pointing device, not Synaptics.  So maybe I need a different driver altogethr if I'm going to get vertical scrolling to work?  The touchpad works otherwise.  I just want vertical scrolling.

---

### Post by unperson on 2005-02-02
Yes, the scrolling feature is great.  I find the touchpad really annoying to use without it.  That feature was configured and turned on by default when I installed Warty, though, so it seems likely that it's an issue of you having a different kind of touchpad.

On this page

[http://web.telia.com/~u89404340/touchpad/](http://web.telia.com/~u89404340/touchpad/)

I found the following line, "Can I use this driver with an ALPS Glidepoint device?
Yes, see the README.alps file included in the package for more information."

I will post the contents of /usr/share/doc/xfree86-driver-synaptics here so hopefully someone can tell us what we actually need to do.

> 
It is possible to use the driver with an ALPS Glidepoint device, but
you probably have to change some parameter values. One user reported
success with the following settings:

    LeftEdge             = 60
    RightEdge            = 830
    TopEdge              = 70
    BottomEdge           = 650
    FingerLow            = 25
    FingerHigh           = 30
    MaxTapTime           = 180
    MaxTapMove           = 110
    EmulateMidButtonTime = 75
    VertScrollDelta      = 50
    HorizScrollDelta     = 50
    MinSpeed             = 0.2
    MaxSpeed             = 0.5
    AccelFactor          = 0.01
    EdgeMotionSpeed      = 40
    UpDownScrolling      = 1
    TouchpadOff          = 0

If you use a 2.6 linux kernel, you need to apply the ALPS kernel patch
in the alps.patch file. Note also that the auto-dev protocol option
doesn't work for ALPS devices, so you have to use the "event" protocol
instead and set the device option to the correct event device. (Look
for a mouse device in /proc/bus/input/devices and see which event
device it is connected to.) Here is an example InputDevice section for
the XF86Config file.

Section "InputDevice"
  Driver  	"synaptics"
  Identifier  	"Mouse[1]"
  Option	"Device"  		"/dev/input/event1"
  Option	"Protocol"		"event"
  Option	"LeftEdge"		"60"
  Option	"RightEdge"		"830"
  Option	"TopEdge"		"70"
  Option	"BottomEdge"		"650"
  Option	"FingerLow"		"25"
  Option	"FingerHigh"		"30"
  Option	"MaxTapTime"		"180"
  Option	"MaxTapMove"		"110"
  Option	"EmulateMidButtonTime"	"75"
  Option	"VertScrollDelta"	"50"
  Option	"HorizScrollDelta"	"50"
  Option	"MinSpeed"		"0.2"
  Option	"MaxSpeed"		"0.5"
  Option	"AccelFactor"		"0.01"
  Option	"EdgeMotionSpeed"	"40"
  Option	"UpDownScrolling"	"1"
  Option	"TouchpadOff"		"0"
EndSection

If you use a 2.4 linux kernel, you don't need to patch the kernel, but
you should instead set "Device" and "Protocol" like this:

  Option	"Device"  		"/dev/psaux"
  Option	"Protocol"		"alps"


On some (all?) ALPS hardware, it is not possible to disable tapping
unless you apply the patch below. However, some users have reported
that this patch breaks tap-and-drag operations, which is why the patch
is not included in the main alps.patch file.

--- linux/drivers/input/mouse/alps.c~alps-test3	2004-02-28 20:46:34.000000000 +0100
+++ linux-petero/drivers/input/mouse/alps.c	2004-02-28 20:49:12.000000000 +0100
@@ -87,6 +87,10 @@ static void ALPS_process_packet(struct p
 	y = (packet[4] & 0x7f) | ((packet[3] & 0x70)<<(7-4));
 	z = packet[5];
 
+	if (packet[2] & 1) {
+		z = 35;
+	}
+
 	if (z > 0) {
 		input_report_abs(dev, ABS_X, x);
 		input_report_abs(dev, ABS_Y, y);
@@ -97,7 +101,6 @@ static void ALPS_process_packet(struct p
 	if (z > 30) input_report_key(dev, BTN_TOUCH, 1);
 	if (z < 25) input_report_key(dev, BTN_TOUCH, 0);
 
-	left  |= (packet[2]     ) & 1;
 	left  |= (packet[3]     ) & 1;
 	right |= (packet[3] >> 1) & 1;
 	if (packet[0] == 0xff) {



I'm not sure about the part with patching the kernel.  Perhaps someone else can chime in.

---

### Post by KingArthur10 on 2005-04-03
I can't seem to get Horay to recognize my touchpad on my Dell Laptop.  It's an Inspiron 8600.  For some reason, when I open the sudo gedit /etc/X11/XF86Config-4 file, it gives me a blank file when I open it.  I'm guessing it's not detecting anything.  Any Ideas how I can rectify this situation.  It does have tapping enabled, though, which is annoying as hell, so I dunno if there is a different config file in Horay or what.  Thanks for anyone who can help.

---

### Post by iomicifikko on 2005-04-06
[QUOTE=KingArthur10]I can't seem to get Horay to recognize my touchpad on my Dell Laptop.  It's an Inspiron 8600.  For some reason, when I open the sudo gedit /etc/X11/XF86Config-4 file, it gives me a blank file when I open it.  I'm guessing it's not detecting anything.  Any Ideas how I can rectify this situation.  It does have tapping enabled, though, which is annoying as hell, so I dunno if there is a different config file in Horay or what.  Thanks for anyone who can help.[/QUOTE]
 hoary uses xorg not xfree so the server config file is not XF86Config-4 but "xorg.conf" if i remember (anyway give a look at that directory and ull find soon your config file)

ps: if u got any error (u cannot go in graphical mode) dont worry couse gedit always creates a backup of edited files (in this case xorg.conf~) so restart pc, in grub select recovery mode, when finished loading type "cp /etc....../xorg.conf~ /etc..../xorg.conf" and restart

byez

ps: anyway i have a problem too with touch pad, i dunno exactly how to say that in english but my cursor seem to ride on ice, not too quick but difficult to control in little moves or when u have to select little thinks, any idea?

---

### Post by KingArthur10 on 2005-04-16
[QUOTE=iomicifikko]hoary uses xorg not xfree so the server config file is not XF86Config-4 but "xorg.conf" if i remember (anyway give a look at that directory and ull find soon your config file)

ps: if u got any error (u cannot go in graphical mode) dont worry couse gedit always creates a backup of edited files (in this case xorg.conf~) so restart pc, in grub select recovery mode, when finished loading type "cp /etc....../xorg.conf~ /etc..../xorg.conf" and restart

byez

ps: anyway i have a problem too with touch pad, i dunno exactly how to say that in english but my cursor seem to ride on ice, not too quick but difficult to control in little moves or when u have to select little thinks, any idea?[/QUOTE]


Well, I failed miserably with the whole thing, but I did get the backup restored.  thanks for letting me know it could be restored ;-).  lol.  I ended up teaching myself the "mv" command, and the rename didn't wanna work for me.  ex. "mv /etc/X11/xorg.conf~ /etc/X11/xorg.conf"  Hey, it worked, and that's why matters.  lol.  God It's a pain learning this new command line for when I screw up.  lmao.

---

### Post by Kivrin on 2007-09-07
This has crashed my computer. My graphcis card won't load anymore. I've gone in under emacs and edited the conf file, but bootup now fails halfway through. HELP.

---

