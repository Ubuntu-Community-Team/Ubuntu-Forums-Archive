---
title: "How can I Disable Tapping for my Mousepad?"
date: 2006-07-26
forum: Hardware &amp; Laptops
---

### Post by jeff_ on 2006-07-26
I have a HP laptop and I would like to disable tapping for the mousepad. I don't see the option under preferences > mouse. What's the easiest way to do this? Thanks, Jeff

---

### Post by bensexson on 2006-07-26
Do you have a synaptics touchpad?

---

### Post by jeff_ on 2006-07-26
I believe it's an ALPS touchpad. I followed [http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad) to get it to work under gentoo.

---

### Post by spier on 2006-07-26
In a Terminal window,

synclient touchpadoff=1 

to turn touchpad off, and 

synclient touchpadoff=0 

to turn it on again!

Edited:

The following command will disable just the tapping events:
```
synclient touchpadoff=2
```

---

### Post by jeff_ on 2006-07-26
> **spier said:**
> In a Terminal window,

synclient touchpadoff=1 

to turn touchpad off, and 

synclient touchpadoff=0 

to turn it on again!

It says Can't access shared memory area. SHMConfig disabled?

Also I don't want to disable the entire touchpad, just the tapping feature where tapping on the pad itself is considered a click. Thanks.

---

### Post by spier on 2006-07-26
> **jeff_ said:**
> It says Can't access shared memory area. SHMConfig disabled?

Oh,forgot to mention that you will have to add 

```
Option "SHMConfig" "on"
```

to Synaptic section, in /etc/X11/xorg.conf, e.g.

```
Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
        
        ...

	Option		"SHMConfig"		"on"
EndSection
```

> Also I don't want to disable the entire touchpad, just the tapping feature where tapping on the pad itself is considered a click. Thanks.

Well, I tried with Tapbutton1 setting, and it seems to work!

```
synclient tapbutton1=0
``` 
disable tapping events while
```
synclient tapbutton1=1
``` 
enables.

---

### Post by jeff_ on 2006-07-26
Thanks, worked great. For future reference what's the best way to gracefully restart X?

---

### Post by spier on 2006-07-26
As I was intrigued about having 3 Tapbutton options Tabbutton1, tapbutton2 and tapbutton3, I google for tap events and from [this page]("http://www.unicom.com/chrome/a/000948.html"), seems setting MaxTapTime to 0 (milliseconds) disabes taps:

synclient maxtaptime=0 
synclient maxtime=180

---

### Post by spier on 2006-07-26
> **jeff_ said:**
> Thanks, worked great. For future reference what's the best way to gracefully restart X?

Ctrl + Alt + Backspace

---

### Post by hasimir44 on 2006-07-27
How about disabling tapping on just the scroll area of a synaptics touchpad?

---

### Post by sm0ke on 2006-07-27
I tried these steps with no luck. I edited the xorg.conf file but when i try and turn the touchpad off it still says that SHMConfig is disabled.

---

### Post by spier on 2006-07-27
> **hasimir44 said:**
> How about disabling tapping on just the scroll area of a synaptics touchpad?

Not sure, but you could try setting different values for MaxTapMove - option that sets the maximum movement for detecting a tap. I'd try a lowest useful value the way a minimum movement would be consider as a move instead a tap. I can't give it a try right now as I leave my laptop at home :(

i.e.
```
synclient maxtapmove=50
```

Edited:
Of course, after you got your preferred settings, you should set them in xorg.conf:
```
 
 Section "InputDevice"
   Driver  	"synaptics"
   Identifier  	"TouchPad"

   ...

   Option	"MaxTapTime"	"180"
   Option	"MaxTapMove"	"50"

   Option	"SHMConfig"	"on"
 EndSection

```


(No, I'm not a bad typist, I'm just a foreign)

---

### Post by spier on 2006-07-27
> **sm0ke said:**
> I tried these steps with no luck. I edited the xorg.conf file but when i try and turn the touchpad off it still says that SHMConfig is disabled.

Have you tried after restarting X?

---

### Post by gholen on 2006-07-27
Hi!
I choose to continune this thread, and post my problem.

I have a laptop too (suprise suprise) and I have the Synaptics driver for my touchpad. My problem is the same, turn of the "tapping".

It annoys me as hell when I type in dokuments, irssi, whatever, and the text goes elsewhere.

Så, tell me, how do I solve the problem?

Thanks in advace.
// Ambjörn AKA gholen

---

### Post by spier on 2006-07-27
> **gholen said:**
> Hi!
I choose to continune this thread, and post my problem.

I have a laptop too (suprise suprise) and I have the Synaptics driver for my touchpad. My problem is the same, turn of the "tapping".

It annoys me as hell when I type in dokuments, irssi, whatever, and the text goes elsewhere.

Så, tell me, how do I solve the problem?

Thanks in advace.
// Ambjörn AKA gholen

So, have you tried the tricks posted in this thread?

Say, executed 
```
synclient MaxTapTime=0
```

If this works, following this [touchpad howto]("https://wiki.ubuntu.com/SynapticsTouchpadHowTo"), one could create a shortcut to disable/enable tapping events!

---

### Post by gholen on 2006-07-28
That worked great!

You help'd me a lot!
sorry for not reading the post carefully, but having quite a lot stressmoments back then, and reading carefully was like having a Win ME cope that runs good on a Apple-computer :)

Anyway, the hack did it...
Thanks!

---

### Post by spier on 2006-07-28
I'm glad it worked, although my wrong English ;)

---

### Post by hayalci on 2006-07-30
> **spier said:**
> Ctrl + Alt + Backspace
Well that is not a very graceful way to restart X. It kills all open graphical applications instantly and they don't have time to save settings, do cleanups etc. [[ especially Gnome will be very upset of this :) ]]

As a graceful restart, Log off your user, and then log on. 

If it does not still work, use ctrl+alt+backspace in the login screen which appears after you have logged off.

If it **still** does not work, there is a problem with the configuration files or something, try looking into /var/log/Xorg.0.log file.

---

