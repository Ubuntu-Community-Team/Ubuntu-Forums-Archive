---
title: "Disable touchpad when mouse plugged in"
date: 2008-12-07
forum: Hardware
---

### Post by tornadof3 on 2008-12-07
So, brushing against the touchpad is obviously very annoying and can lead to the cursor jumping around whilst typing, and I nearly always use a usb mouse. So is it possible to have it automatically turn off when mouse is active, and automatically on when mouse not plugged in? The difficulty with disabling touchpad in the system -> preferences -> mouse menu is that if I boot up without a usb mouse, I can't click into the menus!!

Any ideas appreciated.

---

### Post by BramWillemsen on 2009-03-21
I am very interested in this too. I'm sorry if this is considered o be thread necromancy but the question is very relevant to me.

---

### Post by gcvisel on 2009-03-25
Bump this one for me too.  I'm new to laptops, and am always touching the derned touchpad with my thumb as I type.  I can manually turn it off, but having it automatically shut off when there is a usb mouse is a beautiful idea!

---

### Post by efausett on 2009-04-07
Bump this one for me too.
Such an option would be very nice in the mouse control section.

---

### Post by xMarine73 on 2009-05-14
This script works in Ubuntu 8.04, 8.10, and 9.04.  Just make it executable, add it to your startup applications, and don't look back.

Basically it detects when a mouse is plugged in (you need to modify the script in one spot to do this - it's documented in the file) and disables the touchpad.  Unplugging the mouse then re-enables the touchpad.  I've also included a touchpad delay when it's active and you begin typing.

Hope it helps!

---

### Post by cmmckoy on 2009-06-06
I know my noob is showing, but how do you make it executable? :D

EDIT: Nevermind, I saw that you right-click and in the properties there is a checkbox for making it executable.  But I do have another question.  I'm assuming that in the line where it says

if xinput list 'Microsoft Microsoft? 2.4GHz Transceiver v5.0';

I need to put my mouse's device name, is this correct?  If it is, where can I find that?

---

### Post by cmmckoy on 2009-06-06
I read the script all the way this time, saw the thing about xinput list.  When I type xinput list, I get this:

ghost@ghost-laptop:~$ xinput list
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
"AT Translated Set 2 keyboard"	id=2	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=4	[XExtensionPointer]
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
"HID 04b4:0033"	id=5	[XExtensionPointer]
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
"SynPS/2 Synaptics TouchPad"	id=6	[XExtensionPointer]
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


When I unplugged my USB mouse, the HID 04b4:0033 wasn't there when I ran the xinput list again, so I'm assuming this is my mouse?  If so, do I replace 'Microsoft Microsoft? 2.4GHz Transceiver v5.0' with 'HID 04b4:0033'?  This is what I have done, and I get this when I run it in the terminal:

X loaded
"HID 04b4:0033"	id=5	[XExtensionPointer]
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
Can't access shared memory area. SHMConfig disabled?
syndaemon: no process killed


Can someone help me?  I don't know what SHMConfig is, and I don't want to go messing with something unless I know what I'm doing.

---

### Post by xMarine73 on 2009-06-09
The HID is the one I would use, yep.

---

### Post by xMarine73 on 2009-06-09
[SHMConfig information]("https://help.ubuntu.com/community/SynapticsTouchpad") can be found on this page a little ways down.  It should tell you everything you need to know and how to get it running.

---

### Post by TheSundering on 2009-08-01
I followed all the steps but there seems to be a problem with the script. I get this error when I run it.

```

X loaded
"Logitech USB RECEIVER"    id=7    [XExtensionPointer]
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
Can't access shared memory area. SHMConfig disabled?
syndaemon: no process killed

```

I would LOVE to be able to disable the touchpad. Note: I'm running Linux Mint 7 if that makes a difference.

---

### Post by TheSundering on 2009-08-01
Ok fixed the problem for anyone else looking to do this. This is the last step for me and this script WORKS BEAUTIFULLY!. 

THANK YOU Mr. Thompson!

Right from [[URL="https://help.ubuntu.com/community/SynapticsTouchpad"]SHMConfig information](https://help.ubuntu.com/community/SynapticsTouchpad)[/url]

In a [terminal]("https://help.ubuntu.com/community/UsingTheTerminal") type (for Gnome/Ubuntu): 
```

gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi

```

Then put the following code into the empty shmconfig.fdi file and save it.

```

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="input.x11_driver" string="synaptics">
      <merge key="input.x11_options.SHMConfig" type="string">True</merge>
    </match>
  </device>
</deviceinfo>

```

Once again this works absolutely wonderful and it's running right from startup.

Thank you Marine!

---

### Post by xMarine73 on 2009-08-01
You bet!

You just happened to catch me while I was watching my email and was prepared to come out here to post up help.  Glad you were able to get it working.

If you make changes to it, post up and share with the Ubuntu world. :)

---

### Post by zpletan on 2010-09-10
WOOHOO!  I'm using Lucid; just found this!  IT WORKS!

---

### Post by GeekGirl1 on 2010-11-07
Add Maverick Meerkat to the list!

---

### Post by connermcd on 2010-11-17
> **xMarine73 said:**
> This script works in Ubuntu 8.04, 8.10, and 9.04.  Just make it executable, add it to your startup applications, and don't look back.

Basically it detects when a mouse is plugged in (you need to modify the script in one spot to do this - it's documented in the file) and disables the touchpad.  Unplugging the mouse then re-enables the touchpad.  I've also included a touchpad delay when it's active and you begin typing.

Hope it helps!

Thanks for this! Works great!

---

### Post by gsanders99 on 2011-01-06
Not every touchpad is a Synaptics touchpad.  Mine is Elantech, and that's why I had to use the UDEV method.

I recently installed Ubuntu 10.10 32-bit on my ASUS U80A laptop to replace the Kubuntu 10.04 64-bit I had before.  I used the same method for solving the touchpad problem that I had used in my previous post (link below).  This post describes how to create a UDEV rule to unload the module and disable the touchpad when a USB mouse is plugged in.  It's pretty easy to do, only requiring a 2-line file to be created with your text editor.

[http://ubuntuforums.org/showthread.php?t=1530332](http://ubuntuforums.org/showthread.php?t=1530332)

I just had to tweak it a bit, but the end result is that it works for me.  Hope it helps some of the rest of you.

--- UPDATE ----

One other thing I did different was to copy my touchpad.rules file into [COLOR="Red"]/lib/udev/rules.d/[/COLOR] as [COLOR="Red"]97-touchpad.rules[/COLOR]

This made it disable the touchpad if the mouse was already plugged in at boot.

---

### Post by krazynez on 2013-01-18
> **xMarine73 said:**
> This script works in Ubuntu 8.04, 8.10, and 9.04.  Just make it executable, add it to your startup applications, and don't look back.

Basically it detects when a mouse is plugged in (you need to modify the script in one spot to do this - it's documented in the file) and disables the touchpad.  Unplugging the mouse then re-enables the touchpad.  I've also included a touchpad delay when it's active and you begin typing.

Hope it helps!

Hey, thanks for the .sh script it works really well (on 12.04.1). I was using touchpad-indicator however when I would put the computer to sleep it would always turn my touchpad off even with no external mouse plugged in. I also edited it instead of having gnome-panel it works with unity as well.

---

