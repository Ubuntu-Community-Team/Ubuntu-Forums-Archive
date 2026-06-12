---
title: "Touchpad not recognised on Aspire 5738"
date: 2009-12-21
forum: Hardware
---

### Post by nomadluap on 2009-12-21
I have an Acer Aspire 5738 running Karmic. My problem is that my touchpad is not being recognised as a touchpad, it' being recognised as a "ImPS/2 Generic Wheel Mouse" instead, according to "xinput list"


"xinput list" feedback is as follows:

```
"Virtual core pointer"	id=0	[XPointer]
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
"ImPS/2 Generic Wheel Mouse"	id=2	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 7
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
"Sleep Button"	id=3	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=4	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=5	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video WebCam"	id=6	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Power Button"	id=7	[XExtensionKeyboard]
	Type is KEYBOARD
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=8	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 5
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
"Logitech USB-PS/2 Optical Mouse"	id=9	[XExtensionPointer]
	Type is MOUSE
	Num_buttons is 16
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
```

However, when I run "sudo tpconfig -i", I get the following:


```
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).
Sensor type: unknown (0).
Geometry: rectangular/landscape/up.
Packets: absolute, 80 packets per second.
Corner taps disabled;		no tap gestures.
Edge motion: none.
Z threshold: 6 of 7.
2 button mode; corner tap is right button click.
```

Also, there is no trackpad tab in the Mouse preferences window. 


So, how can I make the trackpad appear as a trackpad instead of a generic ps/2 wheel mouse, and get my beloved trackpad tab back?


Any help would be appreciated. 
     
     -Nomadluap

Also, I added i8042.nomux to the linux boot params to fix the trackpad issue, if that helps out at all.

---

### Post by thered on 2009-12-27
I have same machine and same problem...:(

Doesn't seem to be a solution for it, good to know I'm not alone :)

Adding the i8042.nomux made my touchpad very erratic and more or less unusable.  I had to remove it.

running "sudo tpconfig -i" returns "command not found"

---

### Post by abandonedthe_mulletator on 2009-12-27
I have a similar problem on an ASUS K60.  My touchpad works fine but it jumps all the time. I need to disable it but I don't get the "touchpad" tab in the system-preferences-mouse menu.  Also my xorg.conf says this about it:
```
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

```

The touchpad is not listed under lspci either.  What do I need to do?

---

### Post by nomadluap on 2009-12-27
hmm, I don't seem to have an xorg.conf file.

---

### Post by beefstu on 2009-12-27
different laptop, same problem with exactly same outputs as  nomadluap. I've tried several solutions on different posts, so far only succeeded in  making the scrolling on the right side of my touchpad, which did work, only scroll down!

Hope somebody finds a solution, would really like the two finger scrolling back, strangely enough it works in Windows!

---

### Post by nomadluap on 2009-12-27
> **beefstu said:**
> different laptop, same problem with exactly same outputs as  nomadluap. I've tried several solutions on different posts, so far only succeeded in  making the scrolling on the right side of my touchpad, which did work, only scroll down!

Hope somebody finds a solution, would really like the two finger scrolling back, strangely enough it works in Windows!

woah, mine only scrolls down, too. What laptop do you have?

---

### Post by matchett808 on 2009-12-27
well i have the 5738 and i8042.nomux (added to grub to allow the trackpad on/off button to work right) and i have no problems....

---

### Post by beefstu on 2009-12-27
> **nomadluap said:**
> woah, mine only scrolls down, too. What laptop do you have?

Wow wierd! Its a Packard Bell Easynote TJ65, i think they're pretty much the same as Acers as they own the company.

If i scroll down, it does it normally, if i scroll up, it scrolls the page down really fast!

---

### Post by diesal3 on 2010-02-03
> **nomadluap said:**
> hmm, I don't seem to have an xorg.conf file.

I was having the same problems when I was using Karmic, with a Acer Aspire 5738Z. I have since gone back to Jaunty.

---

### Post by nomadluap on 2010-02-03
So it works in jaunty? Anyhow, i hope that they fix it for Lucid.

---

### Post by matchett808 on 2010-02-03
just wait for lucid...my 5738 is running alpha 2 with no mouse problems atall (i dont think i8024 is still in grub...)

---

### Post by nomadluap on 2010-02-08
I don't have my machine with me right now, but you could try "synaptics -device /dev/psaux"

Might get it to work. I think this might be a problem with the new DeviceKit. Ill go try to ask them about it.

---

### Post by thered on 2010-04-30
I've resurrected this thread because since upgrading to Lucid I find I can't scroll at all with my touchpad... this is ***REALLY*** annoying.

I have noticed that the 'touchpad' entry in System>>Preferences now opens the GUI, it didn't before - however changing settings here seems to have no effect.

Any help?

---

### Post by thered on 2010-04-30
As an addendum, I've just been into 'Update Manager' and there is an update called gpointing-device-settings which is 'greyed out' and presumably not available to me.

---

### Post by nomadluap on 2010-04-30
Yeah, I seem to have the new Trackpad tab also. I'll have to check the update manager, though, and see if I can force it to install.

---

### Post by thered on 2010-05-01
I managed to get gpointing-device-settings installed using Synaptics Pacakage Manager.  Uninstalled gsynaptics first then installed gpointing-device-settings.

However :( it made no difference at all - just a different GUI interface as far as I can see.

---

### Post by spiralx on 2010-05-02
Ditto here.  I have installed gpoint-device-settings, also touchfreeze, and they make no difference at all.

This, combined with a disastrous update that didn't work (I've had to destroy the entire partition and re-install from scratch) is not making me feel at all good about 10.04.

I may go back to 9.10 and wait for a decent future upgrade...

---

### Post by spiralx on 2010-05-02
However, I can report that the issue of the toggle button at the top-right corner of the touch-pad switching off but not again, is still solved by the following:


1) sudo gedit /etc/default/grub
2) change the line
           GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to the following
           GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.nomux"
3) save
4) sudo update-grub
5) restart the system

---

### Post by spiralx on 2010-05-02
...just tried un-installing gpointings, and trying the SHM Dialog + gsynaptics option.

No dice there either.

---

### Post by spiralx on 2010-05-03
Found this, which someone had used on a different Acer Aspire, but it works for the 5738 as well:

I fixed it by:

     Code:
     sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps 
You should be able to make it permanent by putting:
     Code:
     options psmouse proto=imps 
in /etc/modprobe.d/options and rebooting

---

### Post by 3esmit on 2010-05-04
Greetings spiralx,

I have a Aspire 5738 and to the On-Off touch pad button works I need to add that parameter to grub.conf by editing it defaults of course.

I dont have this file: /etc/modprobe.d/options and if I put the commands in it, it will autoexecute even if I have it? And sudo requires user password, how that will be managed?

Your workaround make the scrolling works, but it just takes off the touchpad tab from mouse settings in System>Preferences and any other touchpad configuration tool, but its better this way. Im just sad that I cannot auto deactivate the touchpad when using the keyboard.

There is no other way of mantaining the touchpad recognized by the xserver and by synaptics driver in other to configure it in the GUI?

Thank you for the sharing the workaround.

---

### Post by sveicken on 2010-08-19
> **spiralx said:**
> Found this, which someone had used on a different Acer Aspire, but it works for the 5738 as well:

I fixed it by:

     Code:
     sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps 
You should be able to make it permanent by putting:
     Code:
     options psmouse proto=imps 
in /etc/modprobe.d/options and rebooting


Thanks very much! This workaround together with the "i8042.nomux"-workaround solved all my touchpad-problems! Wau,  very cool.

Sven

---

### Post by jimmers on 2010-08-20
Hi Guys,
I have been using an Acer Aspire 5738Z, since Jaunty with no problems, Karmic I had problems with, albeit not with the touchpad, I now run Lucid (Extended version supplied with Ubuntu User) absolutely Brills,
It even picks up my local radio station, which none had before, I know that this may not be of much to you but thought that it should be said.  BTW the 5738Z is a 64 bit machine I run as 32 bit, more of an aside as help.

Luck

---

### Post by Ian Sinclair on 2010-11-19
I had the same problem (Acer Aspire, Ubuntu 10.04) with no touchpad option in the mouse menu. After I set up WiFi, however, the touchpad tab appeared!

---

