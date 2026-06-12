---
title: "TouchPad Tapping problem"
date: 2007-08-10
forum: Hardware &amp; Laptops
---

### Post by matrixneo on 2007-08-10
My problem is when i tap on my touchpad, it doesn't work always.Sometimes when i tap nothing happens.i have to keep on tapping and it works say in its third round.I couldn't understand the problem.Sometimes i have to tap very hard.Everything is fine in windows. So i don't  think any problem with touchpad. Any help is highly appreciated.

---

### Post by porcorosso on 2007-08-10
Do you know whether your touchpad is a Synaptics or an Alps touchpad? If it's an Alps, I'm going to suggest disabling it in the BIOS (if possible) and using a mouse attached to your notebook. That's what I do with the Alps touchpad on my Dell Precision M70. It's damned near useless in Linux, but because the tap-to-click is ALWAYS too sensitive. And there's no way to turn it off.

If you have a Synaptics touchpad, you're in luck. Use Synaptic (no relation) package manager to find, download, and install the Synaptics Touchpad driver (qsynaptics?). You'll wind up with a Touchpad application in your System->Preferences menu. That may make it possible to control the behavior of your touchpad.

Good luck.

---

### Post by ugm6hr on 2007-08-10
Your touchpad is fully configurable - you just have to edit xorg.conf.

This will tell you about all the settings you need to add for the Touchpad:

```
man synaptics
```

If you need help finding out what settings are appropriate - you can use:
```
synclient -m 500
```

This will list the *x*, *y* and *z* (pressure) coordinates (along with other details) of any place you touch.  So if you run it, and then place your finger on the scroll area, it will tell you what pressure you are applying, so you can set that as the value in Option "FingerLow" "*z*" in xorg.conf.

Or you could use Option "TouchpadOff" "2" to turn off tapping.

For more links & examples - see the "xorg.conf" link in my signature.  And an ALPS Touchpad is equally configurable...

---

### Post by matrixneo on 2007-08-10
Thank you all.My problem was solved.

---

### Post by porcorosso on 2007-08-10
ugm6hr, are you saying that those instructions will work with an Alps touchpad? Heck! If so, I'm going to give it a shot. I tried using the Synaptics Touchpad drivers on this thing and they did nada. But they did work wonders on an old Inspiron that actually had a Synaptics Touchpad on it.

Thank you for the information.

---

### Post by ugm6hr on 2007-08-11
> **porcorosso said:**
> ugm6hr, are you saying that those instructions will work with an Alps touchpad? 

Yes. See this for some details - it does mention ALPS, and my previous laptop that had PuppyLinux on it had an ALPS Touchpad:
[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

Oh - and think about posting a copy of your **working** xorg.conf at my link in my signature for others to copy!

---

### Post by porcorosso on 2007-08-11
> **ugm6hr said:**
> Yes. See this for some details - it does mention ALPS, and my previous laptop that had PuppyLinux on it had an ALPS Touchpad:
[http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)

Oh - and think about posting a copy of your **working** xorg.conf at my link in my signature for others to copy!

Thank you very much. I will try to do the configuration this afternoon or evening and will post the working xorg.conf at the link in your signature.

Can't tell you how nice it will be to be able to use that monster notebook without an external mouse on those occasions when I need to use it in a cramped space. The ALPS Touchpad is absolutely useless as it comes up by default in Linux! Many thanks again.

Now -- if only the Open Source drivers for the blooming video subsystem could do multiple monitors and 3D acceleration... Maybe Gutsy Gibbon will get us closer.

Edit: Yup, it worked. I had read the man page before but was assuming that it applied only to Synaptics touchpads. Why do they call it synaptics instead of, oh I don't know, touchpad? Or at least put a note in there about it applying to other touchpads. I appreciate your help, ugm6hr, and I intend to look further into customizing the touchpad settings and fixing this dad-blamed video subsystem. Looks like links you've supplied may provide a bit more help in both directions.

---

### Post by ugm6hr on 2007-08-13
@porcorosso:
Glad to see I've helped fix one of your problems!

Even better that you've found the solution while trying to help someone else out :)  

Don't you love this forum?

---

### Post by porcorosso on 2007-08-13
> **ugm6hr said:**
> @porcorosso:
Glad to see I've helped fix one of your problems!

Even better that you've found the solution while trying to help someone else out :)  

Don't you love this forum?

This is just about the most generally useful online tech forum I've seen. And I've been around since arpanet and FidoNet. I never had occasion to become involved with Linux until the past couple of months and am amazed at how interesting this OS is, and how helpful the community is.

---

