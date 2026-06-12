---
title: "Touchpad Scrolling Region in 8.10"
date: 2008-11-04
forum: Hardware
---

### Post by CrazyBoyD on 2008-11-04
The vertical scrolling region on my touchpad is too wide, extending past the actual vertical scrolling region as marked on the touchpad.  In previous versions of Ubuntu, I fixed this in the xorg.conf file, but in 8.10 this doesn't have a synaptics touchpad section.  How do I fix this in 8.10?

---

### Post by kyozo on 2008-11-04
As I understand it, xorg.conf is no longer used to configure input devices, instead HAL is used.

you can configure HAL devices runtime using the xinput command.

permanent configuration is done by creating a file in /etc/hal/fdi/policy

you can read about the file and the format here.
[Ubuntu Wiki - input configuration with HAL]("https://wiki.ubuntu.com/X/Config#Input%20Configuration%20with%20HAL")

I think you can use something like this, I use this for scroll configuration of my trackpoint. The thing to notice is the input.x11_options. keys, here you can take the properties from your xorg.conf and use them with HAL.

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
	<device>
		<match key="info.product" string="Synaptics Inc. Composite TouchPad / TrackPoint">
			<merge key="input.x11_options.ZAxisMapping" type="string">4 5</merge>
			<merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
			<merge key="input.x11_options.EmulateWheel" type="string">true</merge>
			<merge key="input.x11_options.EmulateWheelButton" type="string">2</merge>
			<merge key="input.x11_options.EmulateWheelTimeout" type="string">200</merge>
		</match>
	</device>
</deviceinfo>

```

Hope it helps, I think it would be great if someone who really understands what HAL does, and how you configure it would write an article about it, I can't seem to find too much information on the web about HAL, and how it works.

Cheers

Kyozo

---

### Post by CrazyBoyD on 2008-11-04
Thanks for the tip on the fdi files, kyozo.  I ended up getting it to work with an fdi file like this:

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.RightEdge" type="string">5800</merge>
  </match>
 </device>
</deviceinfo>
```

For anyone else with this problem, type

```
gksudo gedit /etc/hal/fdi/policy/vertscroll.fdi
```

into the command prompt, paste this file in and save it, then reboot and you should be set.  Make sure the encoding is right, it didn't seem to work for me until I made sure of that.  Also, the 5800 number is hardware specific.  You'll probably need to change it unless you have a Gateway ML-3109.  Hopefully this can save you needing to figure out how an fdi file works, though.

---

### Post by monkeys on 2008-11-17
I tried this solution, but am still stumped.

I have a post [here]("http://ubuntuforums.org/showthread.php?p=6194566#post6194566"). Have any ideas?

---

### Post by CrazyBoyD on 2008-11-17
It turns out my solution didn't take.  It didn't work at first so I kept tweaking the file until it did, but then it stopped working again after a reboot.  Seems the fdi configuration files don't work too well yet.

---

### Post by monkeys on 2008-11-18
Huh, I think I've solved my issue. I've rebooted already and it seems to work. If you're interested, you can check my thread but it doesn't offer anything that insightful.

---

