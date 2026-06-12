---
title: "Need to disable touchpad clicking with non-synaptics touchpad!"
date: 2008-05-20
forum: Hardware
---

### Post by bobbyshane on 2008-05-20
My touchpad clicking is way too sensitive even after setting it to the lowest setting in the mouse settings. I never use it anyway so I just want to disable it. I have tried what everyone says to do and found that I don't have a synaptics touchpad listed in my xorg.conf file instead I have this:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
        Option		"Emulate3Buttons"	"true"
	Option          "MaxTapTime"            "0"
EndSection

Notice where I put the maxtaptime setting in there and after restarting my touchpad clicking is still there and it's driving me mad! Any help would be great! Thanks.

***Edit***

I forgot to mention I'm using Ubuntu Studio Gutsy which I doubt makes a difference. Also according to the hardware information utility my touchpad is a synaptics touchpad.. go figure.. but there is no mention of it in xorg.conf and the mouse device listed is /dev/input/mice and according to hardware info it's /dev/input/event3, so I tried changing the device to that in xorg.conf and still can't turn off the clicking...

---

### Post by sdennie on 2008-05-20
I'm not sure if you want to disable the touchpad clicking or the touchpad itself.  Either way, can you not configure it with: System->Preferences->Mouse->Touchpad.

Edit:
I just checked and, on Gutsy, you can't directly configure the touchpad with mouse preferences so, this won't work.  Is there anything preventing you from upgrading to Hardy?  It's very simple to configure the touchpad in that version.

---

### Post by bobbyshane on 2008-05-20
> **vor said:**
> I'm not sure if you want to disable the touchpad clicking or the touchpad itself.  Either way, can you not configure it with: System->Preferences->Mouse->Touchpad.

Edit:
I just checked and, on Gutsy, you can't directly configure the touchpad with mouse preferences so, this won't work.  Is there anything preventing you from upgrading to Hardy?  It's very simple to configure the touchpad in that version.

I would love to but one of the main reasons I'm using Ubuntu Studio is for multitrack recording and my soundcard won't work with the Hardy's kernel for some reason and I would have to downgrade the kernel... So I ended up just installing a dual boot with Gutsy and Hardy so I could use Gutsy for recording and Hardy for everything else... and unfortunately it's an audio program I'm using in Gutsy that I mainly need the over sensitive clicking to stop in. Thanks though.

---

