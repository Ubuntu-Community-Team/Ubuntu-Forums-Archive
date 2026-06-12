---
title: "HP Envy 14 - Touchpad Disable feature"
date: 2010-07-22
forum: Hardware
---

### Post by Meson on 2010-07-22
I just got a new HP Envy 14, installed Ubuntu 10.04. The thouchpad has a little LED in the top left corner that if you tap is supposed to disable the touchpad (and the LED turns on).

What are my chances of getting this to work? I looked through the synaptics man page and didn't see anything specific to on the fly toggling of the touchpad...

The best workaround I've found so far is to "disable the touchpad when typing"

---

### Post by rethab on 2010-10-13
Has anybody found anything on this one? I'm currently facing the same problem. I installed Linux Mint though.. 

Cheers,
rethab

---

### Post by Simon Bridge on 2011-01-13
What about:
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

... it is a synaptics touchpad so these things will work. But afaict the corner is a software thing so we'll have to wait for it to be added to the driver as the feature becomes more common.

---

### Post by pi/roman on 2011-01-14
It's fairly simple to set up a software toggle for any input device. First look up your device in xinput.
```
xinput list
```If you're not sure which one it is then run xinput test on one and see if it responds.
```
xinput test [COLOR=Purple]#device[/COLOR]
```where "[COLOR=Purple]#device[/COLOR]" is the device name. Then create a file and place the following script in it.
```
# toggle synaptic touchpad on/off
SYNSTATE=$(xinput list-props "[COLOR=Purple]#device[/COLOR]" | grep Enabled | grep -Eo '.$')
if [ $SYNSTATE = 0 ]; then xinput set-prop "[COLOR=Purple]#device[/COLOR]" "Device Enabled" 1
else xinput set-prop "[COLOR=Purple]#device[/COLOR]" "Device Enabled" 0; fi
```replacing [COLOR=Purple]#device[/COLOR] with the actual name of your device.
Then save it as syntog or whatever name you like in /usr/bin/ and create a shortcut to it in "gnome-keybinding-properties" and add whatever key combination you like as a shortcut.

---

### Post by carpex on 2011-01-14
This works like a charm for me! Just note that the Device "name" is actually the device number (ID). 

Thank you for this!

---

### Post by pi/roman on 2011-01-14
The device number should work alright too, but if you add another device to your system then it may change.

---

### Post by Simon Bridge on 2011-01-17
> **pi/roman said:**
> It's fairly simple to set up a software toggle for any input device.Thanx for that ... note to others, the name of the device also works:

```
$ xinput test "SynPS/2 Synaptics TouchPad"
motion a[0]=3218 a[1]=3537 
button press   1 
button release 1 

```

The output comes from tapping the top left corner - which leads to the speculation that this could be set up as the "keypress" in question - though it still won't switch the led on? Probably I'm getting too enthusiastic...

---

### Post by Meson on 2011-01-17
Guys, if you are really interested, you can apply a patch to xf86-input-synaptics to get the double tap to work. You can also apply a kernel patch to get the LED to work (along with additional synaptics patches).

You can find them in Takashi Iwai's OpenSUSE Factory repo

---

### Post by Guilden_NL on 2011-06-11
> **Meson said:**
> Disclaimer: All of my advice is guaranteed without exception to work. If you find my advice unsatisfactory, you didn't do it right. 
Excuse me, but you should consider changing your signature.  I won't say what I am thinking, but will say this - I wouldn't read one of your posts from here on out if you leave that as your signature.

Signed, 
Chief Architect for one of the world's largest IT manufacturers and service providers.

I am always learning, many times from new users of technology. An arrogant attitude should place you firmly behind a McDonald's grill. Heaven forbid that you speak to customers.

Your post adds zip for value, but we'll let that slide.  At minimum, you could have added a URL for those searching for solutions.

---

### Post by belltown on 2011-06-11
There are patches in [launchpad.net]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809") that work well under Ubuntu 11.04 to fix a lot of the touchpad issues (e.g getting right-click to work, and getting the LED tap-to-disable to work). I'm not sure if they would work under 10.04. In particular see [Comment #144]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809/comments/144") (which fixes right-click, etc.) and [Comment #190]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/582809/comments/190") (which incorporates the Comment #144 patches and adds the LED patches).

---

### Post by yumgnomeandthensome on 2011-09-20
how does one install the download from the HP site that is at the bottom of the page of the launchpad link?
when I extract the file i get a '32' and '64' named file. I can not run either using "./ " command.

---

