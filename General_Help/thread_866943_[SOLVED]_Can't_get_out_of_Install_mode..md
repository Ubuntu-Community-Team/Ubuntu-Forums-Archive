---
title: "[SOLVED] Can't get out of Install mode."
date: 2008-07-22
forum: General Help
---

### Post by jfare on 2008-07-22
Wubi helped me get Xubuntu installed on my Averatec 3200!  Unfortunately, the xorg.conf created during the install doesn't work for me and the install fails when it tries to start X.  I can manually FIX the xorg.conf and start X windows -- but the install still is not complete.  So the next time I boot, it goes through the install from the beginning again and I have lost all changes I have made to the hard disk.

What do I need to do to get the Xubuntu install to continue after I correct the xorg.conf?  I need it to update the boot instructions to NOT re-install.

Thanks for any help!
[J.F.]

---

### Post by ago on 2008-07-22
Reinstall, press esc at boot, and select safe graphic mode

---

### Post by jfare on 2008-07-22
I tried that.... It's not safe enough!  It ends up identical to the normal install.  Is there an option that is safer than "xforcevesa"?


installation-logs.zip attached.

Thanks again for any help you can give!
[J.F.]

---

### Post by jfare on 2008-07-24
Ok folks (if anybody REALLY reads this), Problem solved.  And THIS is how I fixed it...

- the NT bootloader let me choose XP or ubuntu.  I picked ubuntu
- in the GRUB4DOS bootloader I hit "e" to edit the install option
- in the second line (the long one) I REMOVED "quiet" and "splash"
- in the second line I ADDED "single" -- this let me into a recovery menu.
- The recovery menu had the option to drop to a root shell so I dropped to root.
- I edited the xorg.conf to replace the "Device", "Monitor", and "Screen" sections as follows:
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"via"
	Option		"DisableIRQ"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	ModelName	"LCD Panel 1024x768"
	HorizSync 31.5 - 60.5
	VertRefresh	50.0 - 70.0
	Option 		"dpms"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection	"Display"
	Viewport	0 0
	Depth		24
	Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```
- Then I typed exit to leave the root shell (back to the recovery menu)
- then I selected "resume install" and installation resumed!!!

I am now configuring my desktop!

Good Luck folks!
[J.F.]

---

### Post by paul_sc1 on 2008-07-30
> 
Ok folks (if anybody REALLY reads this), Problem solved. And THIS is how I fixed it...


Well, I was lucky enough to run across your post and read it..thank you!

Have been unable to get ubuntu working right on my laptop for ages.

thanks again.

---

### Post by mquest724 on 2008-08-19
I am also reading this and thanking you.  Though I have not tried it yet, I am going to as soon as I have my discs in front of me.  I have the exact same laptop and have been having one heck of a time trying to get Ubuntu to work.  If this was prison, I'd protect you in the shower...

---

### Post by mrlwalsh on 2008-11-29
jfare,

  Thanks for the xorg.conf edits for the Averatec 3200.  I had a good install of 8.04, but can not get 8.10 to install via wubi.

  I tried your edited xorg.conf, but get an error that the module via can not be found.  I continue the boot and the screen locks at the opening of the desktop.

  Any ideas on how to get the via module or the correct one on my installation?  I do appreciate your earlier post.

MRW

---

### Post by dm129 on 2008-12-14
> **mrlwalsh said:**
> jfare,

  Thanks for the xorg.conf edits for the Averatec 3200.  I had a good install of 8.04, but can not get 8.10 to install via wubi.

  I tried your edited xorg.conf, but get an error that the module via can not be found.  I continue the boot and the screen locks at the opening of the desktop.

  Any ideas on how to get the via module or the correct one on my installation?  I do appreciate your earlier post.

MRW

Try "openchrome" instead of "via". Worked for me.

---

