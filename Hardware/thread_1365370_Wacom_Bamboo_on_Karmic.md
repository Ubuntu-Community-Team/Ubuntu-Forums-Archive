---
title: "Wacom Bamboo on Karmic"
date: 2009-12-27
forum: Hardware
---

### Post by Dunatotatos on 2009-12-27
Hi everybody !

I had a tablet Wacom Bamboo. The hardware works (I can use the tablet on Windows Vista). I have read the doc, but the plug-and-play doesn't work.

By following this [thread](http://ubuntuforums.org/showpost.php?p=6546012&postcount=1), I obtain a kernel panic in the restart :p

After a complet reinstallation of Ubuntu, I tried to install wacom-tools and xserver-xorg-input-wacom, but "wacomcpl" open a window where no device is available.

Thanks in advance ;)
Duna

---

### Post by Favux on 2009-12-27
Hi Dunatotatos,

What model Bamboo do you have?

---

### Post by Dunatotatos on 2009-12-27
The Wacom Bamboo. (not Fun or Pen, just Wacom Bamboo)

---

### Post by Favux on 2009-12-27
Hi Dunatotatos,

OK, then you don't need to compile linuxwacom.  The 0.8.4-1 in Karmic is fine for you.  You just need to modify the wacom.fdi.  For explanations and instructions and the new .fdi please see [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176") on the "Wacom tablets in Ubuntu guide/howto" thread.

---

### Post by Dunatotatos on 2009-12-27
Oh cool !

Thank you. I try, and I will come to post the results ;)

---

### Post by Xavier Oddmon on 2009-12-27
I just got a wacom bamboo tablet, and installing the new .fdi file did not seem to change anything. Nothing new is in /dev/input, and it doesn't show up in the gimp. I'm using karmic 64 bit.

---

### Post by Favux on 2009-12-27
Hi Xavier Oddmon,

What model is it?  Is it one of the new Pen and Touches?

---

### Post by Xavier Oddmon on 2009-12-28
No, it's the wacom bamboo pen, model CTL-460

---

### Post by Favux on 2009-12-28
Hi Xavier Oddmon,

That's one of the 5 new Bamboos.  The Touch, the Pen, and the 3 P & T's.  We've sort of been calling them all P & T's.

Your Bamboo is not yet supported by the linuxwacom drivers.  The new-generic rc2 .fdi supports your model.

The good news is that Ayuthia and company have come up with patches that will support your Bamboo Pen.  See [post #2]("http://ubuntuforums.org/showpost.php?p=8099002&postcount=2") on the "New Wacom Bamboo not working".  It has links to the posts with instructions etc.  Use kgingeri's HOW TO.  Be sure to go to tyranos' post to remove the debugging code.  That will get your Pen working.

The other thread gets the Touch and Pad's working for the other models.

Good luck!

---

### Post by Dunatotatos on 2009-12-29
Thank you very much Favux, it works perfectly ;)

---

### Post by Favux on 2009-12-29
Hi Dunatotatos,

Great!  Nice job.  You are welcome.

---

### Post by Xavier Oddmon on 2009-12-29
Alright, i've followed all of these howtos, i've got a huge number of linuxwacom versions compiled, and tried a few fdi files, all to no avail (i cleaned up between them all, i don't have all of these things configured at once). Everything compiles fine, except I had to grab hal-ids from somewhere. Maybe it's because i'm on 64 bit? The tablet works in windows, so it's not a hardware failure (I was beginning to hope it was so i could say it's not a problem on my end)

---

### Post by Favux on 2009-12-29
Hi Xavier Oddmon,

> I had to grab hal-ids from somewhere. Maybe it's because i'm on 64 bit?
No it's a change in Karmic.  Or maybe linuxwacom now needs it because the bluetooth support is now in the kernel?

Is the compiled wacom.ko in place and auto-loading?  Try in a terminal:
```
lsmod | grep wacom
```

---

### Post by Jammet2 on 2009-12-29
Hello there,

Just tried getting my new Bamboo CTH-460 to work on Xubuntu Karmic, using these guides. Haven't spent much time at all figuring out tablets just yet, so I depend on HOWTOs, forums, anything really. :) Please help.

Basically, it's detected as an unknown USB device:

> 
[20270.688018] usb 4-1: new full speed USB device using uhci_hcd and address 4
[20270.860135] usb 4-1: configuration #1 chosen from 1 choice


And that's where I start out. Tried to compile linuxwacom-0.8.4-3 with or without those patches, either or both, to no avail.

> 
make[2]: Leaving directory `/home/jammet/Downloads/wacom/linuxwacom-0.8.4-3/src/xdrv'
Making all in 2.6.31
make[2]: Entering directory `/home/jammet/Downloads/wacom/linuxwacom-0.8.4-3/src/2.6.31'
cp -f ../2.6.27/wacom.h .
cp -f ../2.6.28/wacom_wac.h .
cp -f ../2.6.28/wacom_sys.c .
cp -f ../2.6.28/wacom_wac.c .
cp /lib/modules/2.6.31-16-generic/build/drivers/hid/hid-ids.h .
cp: cannot stat `/lib/modules/2.6.31-16-generic/build/drivers/hid/hid-ids.h': No such file or directory
make[2]: *** [all] Error 1
make[2]: Leaving directory `/home/jammet/Downloads/wacom/linuxwacom-0.8.4-3/src/2.6.31'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jammet/Downloads/wacom/linuxwacom-0.8.4-3/src'
make: *** [all-recursive] Error 1


Perhaps someone could give me a pointer... literally ;).

---

### Post by Dunatotatos on 2009-12-29
```
wget http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h
sudo cp ./hid-ids.h /lib/modules/`uname -r`/build/drivers/hid/hid-ids.h
sudo apt-get install patch
```
Does it help you ?

---

### Post by Favux on 2009-12-29
Hi Jammet2,

Welcome to Ubuntu forums!

The hid-ids.h is a new dependency in Karmic.  To get it:
```
wget http://kernel.ubuntu.com/git-repos/ubuntu/linux-2.6/drivers/hid/hid-ids.h

sudo cp ./hid-ids.h /lib/modules/`uname -r`/build/drivers/hid/hid-ids.h
```
In Section 1 step 3) For Karmic at this [linuxwacom compile HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

Ayuthia also has it in his instructions for patching 0.8.5-4 which is what you should do for your P & T.  That's here:  [http://ubuntuforums.org/showthread.php?t=1321238](http://ubuntuforums.org/showthread.php?t=1321238)

Hope this helps.

---

### Post by Jammet2 on 2009-12-29
Thank you both! =)

I have overcome the compilation problems and have installed that very latest version Favux offered.

The tablet is working. I cannot yet issue any xsetwacom commands, 

> 
# xsetwacom set touch Mode Relative
Error (2): WacomConfigOpenDevice: No such device
Set: Failed to open device 'touch'


But I'll keep reading up.

---

### Post by Favux on 2009-12-29
Hi Jammet2,

Let's see what your:
```
xinput --list
```
and
```
xsetwacom list
```
look like.

---

### Post by Jammet2 on 2009-12-29
Hope it's not too spammy.

> 
# xinput --list
"Wacom Bamboo 4x5 Pen eraser"	id=8	[XExtensionKeyboard]
	Type is Wacom Eraser
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 14720
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 9200
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Wacom Bamboo 4x5 Touch pad"	id=9	[XExtensionKeyboard]
	Type is Wacom Pad
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 6
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 480
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 320
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 255
		Resolution is 1
	Axis 3 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 4 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 5 :
		Min_value is 0
		Max_value is 71
		Resolution is 1
"Wacom Bamboo 4x5 Touch"	id=10	[XExtensionKeyboard]
	Type is Wacom Touch
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 9
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 0
		Resolution is 0
	Axis 1 :
		Min_value is 0
		Max_value is 0
		Resolution is 0
	Axis 2 :
		Min_value is 0
		Max_value is 255
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Wacom Bamboo 4x5 Pen"	id=11	[XExtensionKeyboard]
	Type is Wacom Stylus
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 5
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 14720
		Resolution is 2540
	Axis 1 :
		Min_value is 0
		Max_value is 9200
		Resolution is 2540
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1


> 
# xsetwacom list
Wacom_Bamboo_4x5_Pen_eraser     eraser
Wacom_Bamboo_4x5_Touch_pad     touch
Wacom_Bamboo_4x5_Touch     touch
Wacom_Bamboo_4x5_Pen     stylus


---

### Post by Favux on 2009-12-29
Hi Jammet2,

It looks like you don't have the right .fdi installed yet.  The link is at the bottom of Authia's post, above the attached .fdi.  Here's the direct link:  [http://ubuntuforums.org/showpost.php?p=8367378&postcount=579](http://ubuntuforums.org/showpost.php?p=8367378&postcount=579)

Let me know if you need instructions on installing it.

---

### Post by Jammet2 on 2009-12-29
I have come across these several times, and thought they were handled within hotplugging of the wacom device itself. Sorry.

Simply put, I don't know what to do with these, and which of the three is really the choice of the moment.

Thank you for helping even with these things. Will do well to remember how they work. Looks like they are getting replaced quite often.

---

### Post by Favux on 2009-12-29
Hi Jammet2,

What .fdi means is device information file and it configures the device.  It takes the place of the Wacom configuration sections in xorg.conf with the switch from xorg.conf to HAL/DeviceKit in Jaunty and Karmic.

The instructions would be in [Section 2 b) here]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

You can use the new-generic rc2 one, it's the "final" version.

---

### Post by Jammet2 on 2009-12-29
Okay, that helped a lot, the command works as expected now.

Lastly, all that's left is trying to confgure the Gimp such a way so that it allows me to scroll the image with a finger, and drawing with the pen. No gestures needed. Just dragging things around.

I believe that'll have to wait for now, because the people aren't really using it yet, until they do these exact steps. But I can at least draw using it. Which is what it's for. So there. ;)

Thank you!

---

### Post by Favux on 2009-12-29
Hi Jammet2,

Outstanding!  You've got it.  You're welcome.

For Gimp configure the extended input devices.  See near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom").

---

### Post by eazyigz on 2009-12-30
When I do **lsmod | grep wacom** I get nothing.

---

### Post by Xavier Oddmon on 2009-12-30
> **Favux said:**
> Hi Xavier Oddmon,


No it's a change in Karmic.  Or maybe linuxwacom now needs it because the bluetooth support is now in the kernel?

Is the compiled wacom.ko in place and auto-loading?  Try in a terminal:
```
lsmod | grep wacom
```

wacom.ko is in place, but not auto loading. No errors when i do ```
sudo modprobe wacom
```, but no tablet either.

---

### Post by Favux on 2009-12-30
Hi eazyigz and Xavier Oddmon,

Well first we'll try to rebuild all the dependencies:
```
sudo depmod -a
```
and reboot.

If the wacom.ko still isn't auto-loading add it to the bottom of the modules file in /etc/ as "wacom" (without the quotes):
```
gksudo gedit /etc/modules
```
Save, Close, and reboot.

---

### Post by eazyigz on 2009-12-30
Thanks.  However, wacomcpl still doesn't show any devices.

---

### Post by Favux on 2009-12-30
Hi eazyigz,

Did you install the modified wacom.fdi?  The new-generic rc2 .fdi is attached to the bottom of this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  And the instructions are in Section 2 b).

---

### Post by Xavier Oddmon on 2009-12-30
Alright, i did sudo depmod -a, it took a while, and then I rebooted. Still not loaded, before or after plugging in the tablet. Then, I tried rebooting with the tablet plugged in. Still nothing. I've added wacom to the end of /etc/modules, and now it shows up with lsmod, but I still don't have anything in xsetwacom list, wacomcpl, or the gimp's configure input devices.

---

### Post by Favux on 2009-12-30
Hi Xavier Oddmon,

See post #29 above yours.

---

### Post by Xavier Oddmon on 2009-12-31
Yes, I did install that .fdi file.

---

### Post by PauricTheLodger on 2010-01-31
Hi folks,

Managed to get my Wacom working thanks to the advice here. I have one problem though - if I plug out the Wacom tablet and then plug it in again, it won't work. I'm on Karmic 64 and it's a CTL-460 Bamboo if that helps?

Cheers!
PTL

---

