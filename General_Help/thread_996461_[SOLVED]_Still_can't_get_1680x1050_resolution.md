---
title: "[SOLVED] Still can't get 1680x1050 resolution??"
date: 2008-11-28
forum: General Help
---

### Post by swoody on 2008-11-28
I've tried many different things, Googled, and looked through many posts on here, but still can't get my screen resolution to 1680x1050. I'm running the 177.80 nvidea driver on my 8600GT, and the monitor is a Samsung SyncMaster 2232BW. I had everything working in Vista, so I am pretty sure the card can handle this resolution. Any advice or tips would be extremely helpful at this point. Thank you all very much in advance!!

Woody

---

### Post by NT4usB on 2008-11-29
Which Ubuntu are you running?
Have you tried:```
sudo nvidia-settings
```Have you tried manually editing xorg.conf?

---

### Post by Seks on 2008-11-29
I had this problem for a while, but putting 

Option "ModeValidation" "NoMaxPClkCheck"

under Section "Screen" and

Option "ModeValidation" "NoDFPNativeResolutionCheck"

under Section "Device" fixed it, and gave me the 1680x1050 option

---

### Post by NT4usB on 2008-11-29
That makes sense. There are many posts about resolution problems. I'll bet a lot are a result of misdetected monitors. I get around it by specifying refresh and resolution in xorg.conf.

---

### Post by swoody on 2008-11-29
> **NT4usB said:**
> Which Ubuntu are you running?
Have you tried:```
sudo nvidia-settings
```Have you tried manually editing xorg.conf?

I'm running Ubuntu 8.10 I have nvidia-settings, and I've run it from System>Administration>nvidia but I have no idea what to change or what to do to make it work. Also, what would I put into the xorg.conf file to make it work manually?

> **Seks said:**
> I had this problem for a while, but putting 

Option "ModeValidation" "NoMaxPClkCheck"

under Section "Screen" and

Option "ModeValidation" "NoDFPNativeResolutionCheck"

under Section "Device" fixed it, and gave me the 1680x1050 option

Do I put this in the xorg.conf file? or where?

---

### Post by swoody on 2008-12-13
Still trying to get this to work :( Any other ideas?

---

### Post by NT4usB on 2008-12-13
First, look up what resolution and refresh your monitor supports. 
nvidia-settings>X server display configuration. 
Select the resolution and refresh you want.
When you run it from the GUI does it prompt for a password? If not, it won't be saving any changes. Run it from a terminal using sudo.

What you change in xorg depends on what's already in there. 8.10 uses x differently than earlier releases. There may be nothing more than a bunch of 'default' this and 'default' that in yours. 
If you change it and don't get it right, 8.10 tosses it and creates a new xorg.conf. Annoying when we're trying to sort it manually.
Basically, you're adding and/or editing the "Monitor" and/or "Screen" sections. Mine look like this. 
**Yours will have different values based on your monitor** so don't expect these to work. 
You're going to be setting HorizSync and VertRefresh in "Monitor" and Subsection "Display" Modes in "Screen" May as well add the options Seks suggested while you're in there.
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic Q20wb"
    HorizSync      31.0 - 82.0 
    VertRefresh    50.0 - 75.0 
        Option          "DPMS"

Section "Screen"
    Identifier     "lcd"
    Device         "7600GS"
    Monitor        "Q20wb"
    DefaultDepth    24
    Option         "VideoOverlay" "on"
    Option         "OpenGLOverlay" "on"
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050_60" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050_60" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

---

### Post by swoody on 2008-12-23
> **Seks said:**
> Option "ModeValidation" "NoMaxPClkCheck"

under Section "Screen" and

Option "ModeValidation" "NoDFPNativeResolutionCheck"

under Section "Device"

I tried this, and rebooted, but still have no option anywhere for my screen resolution.

> **NT4usB said:**
> First, look up what resolution and refresh your monitor supports. 
nvidia-settings>X server display configuration. 
Select the resolution and refresh you want.
When you run it from the GUI does it prompt for a password? If not, it won't be saving any changes. Run it from a terminal using sudo.

I tried going into nvidia-settings, but it still doesn't show me anything with my resolution in it.

> What you change in xorg depends on what's already in there. 8.10 uses x differently than earlier releases. There may be nothing more than a bunch of 'default' this and 'default' that in yours. 
If you change it and don't get it right, 8.10 tosses it and creates a new xorg.conf. Annoying when we're trying to sort it manually.
Basically, you're adding and/or editing the "Monitor" and/or "Screen" sections. Mine look like this. 
**Yours will have different values based on your monitor** so don't expect these to work. 
You're going to be setting HorizSync and VertRefresh in "Monitor" and Subsection "Display" Modes in "Screen"

How can I find out what I have to enter for my monitor?

---

### Post by Coder543 on 2008-12-23
Just wondering... have you restarted X any time recently? Ctrl + Alt + Backspace! (it might decide to be nice, idk)

---

### Post by swoody on 2008-12-24
haha, Nope, I'm not that lucky! Tried it out, same old thing, and no new options :( 

I've been rebooting my comp several times to apply some of the settings, so it's been getting restarted on it's own, too.

---

### Post by NT4usB on 2008-12-25
> **woody86 said:**
> ...How can I find out what I have to enter for my monitor?

Grab the manual off the Samsung site and look it up, like this.

HorizSync 30.0 - 81.0
VertRefresh   56.0 - 75.0

---

### Post by swoody on 2008-12-26
Thank you guys SO much! I finally got it working!! :D I'm so happy, and this looks a million times better now! Here's my xorg.conf file if anyone else has any more input for me, or wants to use it:

```
Section "Monitor"
	Identifier     "Unknown"
	VendorName     "Samsung"
	ModelName      "SyncMaster 2232BW"
	HorizSync      30.0 - 81.0 
	VertRefresh    56.0 - 75.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Unknown"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	"ModeValidation"	"NoMaxPClkCheck"
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050_60" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050_60" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       32
        Modes      "1680x1050_60" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	Option	"ModeValidation"	"NoDFPNativeResolutionCheck"
EndSection
```

---

### Post by swoody on 2008-12-26
oops, double post :)

Thanks again guys!

---

