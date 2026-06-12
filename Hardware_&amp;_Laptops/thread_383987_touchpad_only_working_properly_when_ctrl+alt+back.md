---
title: "touchpad only working properly when ctrl+alt+back"
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by sit properly on 2007-03-13
Hello there. 

I've got a strange problem that really has me stumped. 

When I start up Ubuntu, my touchpad (Sony Vaio, C-series) works but won't scroll. I was told to add "qsynaptics -r" to Sessions > Startup and then do a ctrl alt backspace and it should work. And it did. 

However... when I reboot Ubuntu, the touchpad is back to its old, wicked ways. That is until i do a ctrl alt backspace. And then PRESTO! It's back!

That's neat and all, but is there any way that I could actually get qsynaptics -r to actually start up upon starting up?

Thanks!

---

### Post by matburton on 2007-03-14
Hmm I have a synaptics touchpad and I havn't had to use qsynaptics. I just added the following to xorg.conf.

```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
	Option		"HorizScrollDelta"	"0"		
	Option		"HScrollEmuOff"	"1"
	Option		"LeftRightScrolling"	"0"
	Option		"VScrollEmuOff"	"0"
	Option		"VertScrollDelta"	"90"
	Option		"RightEdge"		"5000"
        Option          "SHMConfig"             "on"
EndSection

```

And I don't have the described problem with that.
BTW if you try using this you'll probably need to change the RightEdge value (the scroll region) and possibly the VertScrollDelta for the scrolling speed.

Hope that helps!

---

### Post by sit properly on 2007-03-14
Well, I tried that and it definitely changed some things. It's a little slower than I had it set before, so I know that it worked. 

However, still no scrolling.

Now, it's not even scrolling when I refresh X (not because of what I just did - it stopped doing that prior to my changing xorg.conf. 

Any ideas?

---

### Post by matburton on 2007-03-14
It may be worth having a play with the right edge value.

5000 is the value I found for mine but it may be that this edge if off the right hand side of yours.

You could try something stupidly small like 1000 or even lower and see if it scrolls then (you may find it difficult to move the pointer though so use a mouse as well) and if it does its trial and error after that.

---

