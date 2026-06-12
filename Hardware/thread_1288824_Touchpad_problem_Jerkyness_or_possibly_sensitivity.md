---
title: "Touchpad problem: Jerkyness or possibly sensitivity resolution (any ideas?)"
date: 2009-10-11
forum: Hardware
---

### Post by Decepto on 2009-10-11
Hi everyone,

I just bought a new Asus G51 laptop with a synaptics touchpad. I've installed Karma and everything is working great except the touchpad.

It's a bit difficult to explain, but something seems to be wrong with the touchpad's input resolution. When I move the cursor, instead of a smooth linear move, I get a square step-motion move. 

I've included a graphic I made in GIMP to show what I'm talking about. As you can see, I'm trying to draw a diagonal straight line (which I normally can do fine). But instead I'm getting this square-step jumping behavior.

Does anyone know what causes this or how to fix it? Thank you.

**Edit**:

I think I found the problem. But I have no clue how to fix it.

Here's my output from xinput -list.

```

"SynPS/2 Synaptics TouchPad"	id=9	[XExtensionPointer]
	Type is TOUCHPAD
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

```

Shouldn't my min and max value be the same on both axis?

---

### Post by Decepto on 2009-10-12
Does anyone have any idea of why this might be happening?

---

### Post by dark_overload on 2010-12-22
Bump. I have this issue on my new HP G62 laptop as well. Vertical and horizontal movements are straight, but diagonal movements tend to wobble like shown above.

---

