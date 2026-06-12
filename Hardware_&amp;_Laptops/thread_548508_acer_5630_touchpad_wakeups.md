---
title: "acer 5630 touchpad wakeups"
date: 2007-09-11
forum: Hardware &amp; Laptops
---

### Post by karvec on 2007-09-11
Ok, I did search for this problem on google and didn't find anything other than an apple_touchpad driver problem.

  This relates to powertop and Gutsy Gibbon--  I just installed tribe 5 and did updates.  I also had this problem in Feisty, but did not know the source of the problem because I didn't have the latest kernel, but I figured it out by just using the touchpad.

The touchpad on my Acer 5630 causes up to several hundred wakeups per second when in use...  Is there any way to fix this problem, besides disabling the touchpad?  Say, another driver or patch that does not cause these wakeups?  I don't know how to install the apple_touchpad patch, as specified on the powertop website, and I don't think I want to because I'm not using an apple.  :P

So!!

I don't know whether this issue can be resolved, or if I will just have to not use my touchpad for navigation, but it would be really awesome if I could figure out how to use my touchpad without all the wakeups.

If anyone has the same problem, or has had the same problem and knows how to fix it, let me know!!  Thanks!!!!

```

  73.5% (345.5)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   6.7% ( 31.5)       <interrupt> : extra timer interrupt 
   4.1% ( 19.5)       <interrupt> : uhci_hcd:usb2, ipw3945 
   3.6% ( 17.0)              Xorg : do_setitimer (it_real_fn) 
   3.0% ( 14.0)              Xorg : schedule_timeout (process_timeout) 
 
```



~~karvec

---

### Post by karvec on 2007-09-13
Well, I've done some tinkering around, but really haven't figured out anything besides just disabling the touchpad.

*BUMP*

---

### Post by jeskuruvilla on 2007-09-18
I have the same config and the only problems I had were overcome with installation of the synaptic touch pad accessory. Dont know if this would help in any way! By the way , you can disable the touch pad by pressing Fn-F7. Restarting it may help?

Also add to the xorg.conf file, the following

 Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	**InputDevice	"Synaptics Touchpad"**
EndSection

Hope this helps.

---

### Post by dixon on 2008-01-17
Have you fixed the touchpad wakeups? I have the same problem on my HP 6720s...

---

### Post by mrThefter on 2008-01-25
To my understanding, this behavior is normal.
Most touchpads use PS/2, which is controlled through interrupts. 

The apple-touchpad uses USB, which is handled differently.

So really, this just prevents your processor from going into deep sleep. But there's really no reason for the processor to do so if you're actively using the computer. The processor should still at least get to the second lowest state, despite all the PS/2 interrupts.

But that's only what I think. Don't take my word for it.

---

