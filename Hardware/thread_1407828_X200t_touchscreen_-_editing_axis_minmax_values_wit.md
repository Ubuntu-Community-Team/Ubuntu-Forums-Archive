---
title: "X200t touchscreen - editing axis min/max values with xinput"
date: 2010-02-15
forum: Hardware
---

### Post by Red Penguin on 2010-02-15
Hi, 

Using 9.10, my X200t touchscreen (Note: not the stylus input) has a 'bezel' around the edge, for example touching the very top-middle of the screen points the cursor to about 2cm below that. This is repeated for all 4 sides of the screen.

xinput list 3 gives

```
"PnP Device (WACf008) touch"	id=3	[XExtensionKeyboard]
	Type is Wacom Touch
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 32
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 1024
		Resolution is 99
	Axis 1 :
		Min_value is 0
		Max_value is 1024
		Resolution is 157
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


```

I'm wondering if 

a) my problem is caused by the Axis_0/1 Min_value & Max_values being incorrect
b) whether the min value can be a negative number
c) how I would change these values using the xinput command

Thanks

RP

PS: Wacomcpl shows no devices, else I'd calibrate that way :)

---

### Post by Favux on 2010-02-15
Hi Red Penguin,

You should be able to get wacomcpl to work for you and allow touch calibration.  Your X200t has the older single touch touch-screen, correct?

Either of the two modified wacom.fdi's attached to the bottom of the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1") should get wacomcpl working.  Instructions are in Section 2 b) if you need them.

---

### Post by Red Penguin on 2010-02-16
Wow, thats a great howto, thanks Favux.

I followed the instructions in the post, first just Section 2b, then the whole way through, but end up with the same result: xinput --list doesn't match xsetwacom list. The respective results (abbreviated) are as follows

```

"stylus"	id=2	[XExtensionKeyboard]
	Type is Wacom Stylus
"stylus touch"	id=4	[XExtensionKeyboard]
	Type is Wacom Touch
"eraser"	id=5	[XExtensionKeyboard]
	Type is Wacom Eraser

```

```
~$ xsetwacom list
stylus     stylus
eraser     eraser

```

So I'm missing touch, and it cannot be configured by wacomcpl. Figures the only one missing is the one I want to fix!

Thanks

RP

---

### Post by Favux on 2010-02-16
Hi Red Penguin,

Thanks.  I added a bit here, and a bit there, and it just grew!  :)

My guess is your PnP digitizer isn't on the touch match line.  I thought that was all of them.  So we need to find out what it is by looking at your lshal:
```
lshal>RedPenguin_lshal.txt
```
You can post it with Manage Attachments (below) after compressing it by right clicking on it and using Create Archive.

---

### Post by Red Penguin on 2010-02-16
Please see attached

Thanks

RP

---

### Post by Favux on 2010-02-16
Ok, let's try this.  In the wacom.fdi (which one did you use?) go to the:
```
<!-- Wacom names "parser" -->
```
and remove
```
    <match key="info.udi" contains_not="subdev_1">
```
and it's matching (paired)
```
    </match>
```
below the "info.product" stuff.  It will have the same indent.  Then reboot.

Let's see if that changes your xinput and xsetwacom list.  Otherwise it may be the baud rate stuff.

---

### Post by Red Penguin on 2010-02-16
It worked, you're a wizard!

Thanks

RP

---

### Post by Favux on 2010-02-16
Great!  :D

---

