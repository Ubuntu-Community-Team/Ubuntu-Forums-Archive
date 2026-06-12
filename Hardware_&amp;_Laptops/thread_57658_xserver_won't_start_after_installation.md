---
title: "xserver won't start after installation"
date: 2005-08-17
forum: Hardware &amp; Laptops
---

### Post by UnitetError on 2005-08-17
hi, i just installed ubuntu on my pc, but when it's done, it sais it can't start xserver, and i should configure it. what do I have to do? I have an Saphire X800, a 640 P4, 1GB RAM, and an ASUS Mainboard.

Thanks

---

### Post by GavinX on 2005-08-17
Hi there,
 
 you should be able to run the following command in a shell
 
 sudo dpkg-reconfigure xserver-xorg
 
 and that should run you through setting up X again (make sure you have your monitor and video card detaisl to hand - you'll need to know (specially type and manufactrer of your card, and vertical and horizontal sync rates of your monitor)
 
 Other than that, it should be pretty simple. It's not that hard to reconfigure.

---

### Post by UnitetError on 2005-08-17
hm, ok I did exactly what you told me to, and after I got trough configuring my xserver, I rebooted but it still didn't work! I'm pretty sure I entered everything correctly! What can I do?

---

### Post by GavinX on 2005-08-17
[QUOTE=UnitetError]hm, ok I did exactly what you told me to, and after I got trough configuring my xserver, I rebooted but it still didn't work! I'm pretty sure I entered everything correctly! What can I do?[/QUOTE]Ok. Run the following command from the terminal window "sudo startx" (without the "") and see what happens. Report any errors.

---

### Post by UnitetError on 2005-08-17
ok, i configured the xserver again and started it but it still doesn't work! it sais: fatal error no screen found!

---

### Post by GavinX on 2005-08-17
[QUOTE=UnitetError]ok, i configured the xserver again and started it but it still doesn't work! it sais: fatal error no screen found![/QUOTE]Hmmmmm. This error points to one of two things: 1. The video card was not properly specified, hence the driver used is incorrect OR 2. The monitor was not set up correctly. Post a copy of your /etc/X11/xorg.conf file. Also, what kind of video card and monitor are you using? Please give exact details.

---

### Post by UnitetError on 2005-08-17
My Video Card is an ATI Radeon X800 265MB by Saphire. My Monitor is fujitsu-siemens scaleoview C19-4 (19" TFT). How am I able to read what is in that file, and how can I install a driver?

---

### Post by GavinX on 2005-08-17
[QUOTE=UnitetError]My Video Card is an ATI Radeon X800 265MB by Saphire. My Monitor is fujitsu-siemens scaleoview C19-4 (19" TFT). How am I able to read what is in that file, and how can I install a driver?[/QUOTE]Ok. When you reconfigure your xserver, which video driver do you choose? Also, do you know the vertical and horizontal sync range for the monitor?

---

### Post by UnitetError on 2005-08-17
It didn't give me an option to chose a video driver, and I don't know the sync ranges, how can I find out?

---

### Post by GavinX on 2005-08-17
The sync ranges would be obtained from the monitor's users' manual. It should be included in the specifications. Let me do a little research and get back to you asap.

---

### Post by UnitetError on 2005-08-17
My Manual sais:
horizontal sync range for 1280x1024@60Hz = 64,0 kHz
and
horizontal sync range for 1280x1024@75Hz = 79,9 kHz
But somehow he doesnt find the 75Hz one anyway and it doesnt't say anything about vertical sync range!

---

### Post by GavinX on 2005-08-17
In a terminal type...
 
  	Code:
 	[left]sudo nano /etc/X11/xorg.conf[/left]
 
 
 Scroll down to you get to a section something like this
  	Code:
 	[left]Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X700 Pro"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection[/left]
 
 
 And change the driver to radeon...
  	Code:
 	[left]Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X700 Pro"
	Driver		**"radeon"**
	BusID		"PCI:1:0:0"
EndSection[/left]
 
 
 then save(ctrl+o), exit(ctrl+x) and startx

---

### Post by Luftwaffle on 2005-09-03
I was having a similar problem to the person who posted this thread, and just got it worked out by following your advice GavinX (the last step of changing the driver to "radeon" is what did it, the other things didn't work even though I had correctly entered my monitor's refresh rates, etc.) Thanks! I'm glad there are helpful people on the forums here.  :)

---

