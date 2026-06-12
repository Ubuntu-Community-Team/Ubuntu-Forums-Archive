---
title: "Help! Screen resolutions!!"
date: 2008-11-22
forum: General Help
---

### Post by basicxman on 2008-11-22
I've somehow set my screen resolution to 640x480 and the resolution preference only has an option for that same resolution. Problem is, my screens resolution is 1280x800.

---

### Post by basicxman on 2008-11-22
BTW this happened when ubuntu tried to go into low graphics mode and I pressed configure, the largest resolution there was 800x600 which is what I selected but I'm still stuck with 640x480....

---

### Post by eternalnewbee on 2008-11-22
Is your graphic card enabled?
To check, go to: **Main Menu > System > Administration > Hardware Drivers**.

---

### Post by Izek on 2008-11-22
> **eternalnewbee said:**
> Is your graphic card enabled?
To check, go to: **Main Menu > System > Administration > Hardware Drivers**.

It won't be enabled if catalyst/ati.com drivers are used, just so you know.

---

### Post by eternalnewbee on 2008-11-22
> It won't be enabled if catalyst/ati.com drivers are used, just so you know.
Thanks for the info, Izek. So how do you know that **atalyst/ati.com drivers** are being used?

---

### Post by Izek on 2008-11-22
> **eternalnewbee said:**
> Thanks for the info, Izek. So how do you know that **atalyst/ati.com drivers** are being used?

I don't, I just thought you may need a reminder just in case.

---

### Post by eternalnewbee on 2008-11-22
Am I missing something here?
There are so many drivers out there. Why you chose to remind me of these ones in particular is a mystery to me. If you're trying to point out that they're the only ones, then I understand. Otherwise your info wasn't of any value (unless you name all drivers which are currently unsupported). Of course we can agree that we disagree;)

---

### Post by basicxman on 2008-11-22
There is no graphics card needing to be enabled. Nothing shows up in the hardware drivers

---

### Post by gregphil on 2008-11-23
Under 8.10  (ubuntu or kubuntu)

That happened to me a couple of days ago, and I know I didn't do anything to select a lower video mode (I always run in 1920 x1200).

It turned out something (?) had added some lines to my /etc/X11/xorg.conf file and set a "mode line" to 640 x 480.  Orginally there were no mode lines, so (as root) I simply commented out the two new lines and rebooted.  That fixed it for me.

There should be backup xorg.conf files in your /etc/X11 directory, you could look at the backups and see what the most recent one looked like before your troubles started.

Good luck.

---

### Post by lalawawa on 2008-11-23
I, too am having trouble with screen resolutions so I decided to join this thread.

I used to be on fiesty fawn and I had a screen resolution of 1920 x 1280.  Then I installed (upgrade was not available) hardy (= 8.04) and now I can only get 1600 x 1200.

I enabled my hardware driver as someone suggested in this thread.

Here's the relevant stuff from my /etc/X11/xorg.conf:

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:0:13:0"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1920x1280"	"1600x1200"	"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Here are some traces from my /var/log/Xorg.0.log (note the line "No valid modes for "1920x1280"; removing." -- what does "no valid modes" mean?):

(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6150SE nForce 430 (C61) at PCI:0:13:0
(II) NVIDIA(0):     (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.61.32.25.02
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6150SE nForce 430 at
(--) NVIDIA(0):     PCI:0:13:0:
(--) NVIDIA(0):     Samsung SyncMaster (CRT-0)
(--) NVIDIA(0): Samsung SyncMaster (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1920x1280"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(--) NVIDIA(0): DPI set to (78, 95); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.

Anyone got any ideas?  Remember, the key thing is that higher resolution was WORKING on fiesty fawn, so it's not a hardware limitation.

---

### Post by lalawawa on 2008-11-23
Looking at other threads, I found my solution.  I add "Virtual 1900 1280" to the 'SubSection "Display"', rebooted, and got better results.

---

