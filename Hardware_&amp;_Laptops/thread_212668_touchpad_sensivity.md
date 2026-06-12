---
title: "touchpad sensivity"
date: 2006-07-10
forum: Hardware &amp; Laptops
---

### Post by derakhshani on 2006-07-10
the sensivity of my touchpad is more than what is desired.
How can I adjust its sensivity to lower value?
(driver of touchpad under windows was apoint.)
From sensivity I mean clicking sensivity (undesirable clicks)

laptop model: Sony Vaio VGN-A230P

---

### Post by Athropos on 2006-07-10
If it's a synaptics touchpad, you may use the synclient command in a terminal to modify the behavior of your touchpad (use 'synclient -l' to get a list of variables). When you are happy with your settings, you have to write them in your xorg.conf to make them permanent. There may also exist a frontend for synclient...

---

### Post by derakhshani on 2006-07-10
> **Athropos said:**
> If it's a synaptics touchpad, you may use the synclient command in a terminal to modify the behavior of your touchpad (use 'synclient -l' to get a list of variables). When you are happy with your settings, you have to write them in your xorg.conf to make them permanent. There may also exist a frontend for synclient...

```

$ synclient -l
Can't access shared memory area. SHMConfig disabled?

```

Does this mean that it is not a synaptics touchpad or there is another problem?
any idea :idea: ?

---

### Post by Athropos on 2006-07-10
I got the same error on my own laptop. I had to activate SHMConfig by adding the corresponding option to xorg.conf:

```

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
        ...
        Option          "SHMConfig"             "on"
        ...
        Option          "LockedDrags"           "1"
EndSection

```

You then have to restart your X server. BTW, all your options about the touchpad go in this section (like "LockedDrags").

---

### Post by derakhshani on 2006-07-11
thank you for your guidelines.
Now I can edit via synclient.
I find gsynaptic a graphic frontend for synclient but it does not work correctly. It seems I should change them manually.
which variables are related to undesired clicking?
I guess FingerLow and FingerHigh are only related variables, am I right?

---

### Post by Athropos on 2006-07-12
> **derakhshani said:**
> 
I guess FingerLow and FingerHigh are only related variables, am I right?

I'm not currently using my laptop, but variables like MaxTapTime are also related. Correctly configuring the touchpad is difficult, you have to try & see :)

---

### Post by kaffekopp on 2006-09-05
Have you tried syndaemon? With it, you can set the touchpad to disable for a period of time after each time you press a button on the keyboard - pretty handy for eliminating those unwanted clicks while you're typing, while not having to mess around with the sensitivity of the touchpad.

Here's what I use:

syndaemon -i 1 -k -t -d

-i 1  (means that the touchpad will be suspended for 1 second after each time I press a button on the keyboard)
-k    (Ignore modifier keys - so that I can hold down ctrl and shift while using the touchpad)
-t    (disable only tapping and scrolling)
-d    (run in background)

Check out "man syndaemon" for more info.

---

