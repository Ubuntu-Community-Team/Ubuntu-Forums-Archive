---
title: "640x480 resolution doesn't fit on screen"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by Minilek on 2007-01-21
On my laptop I have an nVidia geforce2 go 5200.  I used to use the nvidia 1.0-7xxx driver but recently upgraded to the 1.0-9746 driver (from here: [http://www.nvidia.com/object/linux_display_ia32_1.0-9746.html)](http://www.nvidia.com/object/linux_display_ia32_1.0-9746.html)).  The 1024x768 and 800x600 resolutions work perfectly, but 640x480 is too big to fit on the screen (the monitor only displays the topleft corner of the screen).  I never had this problem before and have made no changes to my xorg.conf, so I'm not sure what the source of the problem is.  Anyone have any ideas?

Thanks,
Jelani

---

### Post by roderikk on 2007-01-21
Hi,

It would be helpful if you provide more information, such as the current content of the device section of your xorg.conf file. Hopefully we will be able to help you more in that case. Just out of interest though, when are you running your screen at a resolution of 640*480?

---

### Post by Minilek on 2007-01-21
Sorry about that. You can find my xorg.conf here: [http://web.mit.edu/minilek/Public/xorg.conf](http://web.mit.edu/minilek/Public/xorg.conf)

I changed this section:
[html]
SubSection "Display"
		Depth		16
		Modes		"1024x768" "640x480"
EndSubSection
[/html]
to this:
[html]
SubSection "Display"
		Depth		16
		Modes	       "640x480"
EndSubSection
[/html]
and restarted X then ran nvidia-bug-report.sh (a script that came with the driver).  It dumped a lot of info into a log file, and that's here: [http://web.mit.edu/minilek/Public/nvidia-bug-report.log](http://web.mit.edu/minilek/Public/nvidia-bug-report.log).

A game I play (Starcraft) requires the resolution to be 640x480.

EDIT: I should mention something weird.  Even if I change my video driver to something non-nvidia (say nv or vesa) in my xorg.conf, the problem persists.  I find this whole thing strange since I never updated my xorg.conf after installing the newer version of the nvidia driver.

---

### Post by Minilek on 2007-01-21
If anyone has this problem in the future, this is how I got it fixed: [http://www.nvnews.net/vbulletin/showthread.php?t=84740](http://www.nvnews.net/vbulletin/showthread.php?t=84740).

(in summary, I changed "640x480" in my xorg.conf to "640x480_60")

---

