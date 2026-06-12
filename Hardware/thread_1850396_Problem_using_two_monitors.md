---
title: "Problem using two monitors"
date: 2011-09-26
forum: Hardware
---

### Post by Aries01 on 2011-09-26
With the proprietary driver of my Radeon graphics card activated, I tried to set up a two-monitor display arrangement ("show same image in both monitors" unchecked), but the system gave the following error message:

   "Required virtual size (2560,1024) does not fit available size, min. 320,200 max. 1600,1600."

Curiously, this problem does not occur when the Radeon driver is left unactivated.

Is there a way to adjust those parameters that are causing a problem, so that I could set up a two-monitor desktop?

---

### Post by Toz on 2011-09-27
Hello and welcome to the forums.

Can you post the contents of your /etc/X11/xorg.conf file? There should be a section there about Virtual size. If not, we can try adding one.

Reference link: [https://wiki.ubuntu.com/X/Config/Resolution#Setting_resolution_changes_in_xorg.conf_--_resolution_lower_than_expected]("https://wiki.ubuntu.com/X/Config/Resolution#Setting_resolution_changes_in_xorg.conf_--_resolution_lower_than_expected")

---

### Post by Aries01 on 2011-10-08
Thank you for your advice. Here is the contents of xorg.conf:

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection


I tried replacing the contents of the file with the code offered at your reference link, but it rendered the computer incapable of booting. The graphics card is a Radeon HD 4670. I would be grateful for further advice.

---

### Post by Toz on 2011-10-08
Try this one:
```

Section "Screen"
   Identifier "Default Screen"
   DefaultDepth 24
   SubSection "Display"
      Virtual 2560 1024
   EndSubSection
EndSection

Section "Module"
   Load "glx"
EndSection
```

---

### Post by jonnyboysmithy on 2011-10-08
I had this problem till yesterday I figured out you have to use the proprietary drivers setting tools, for me it looks like the attached picture.
As you can see my normal screen config tools don't know the screens, the nvidia tool knows what to do.
**Use the proprietary driver screen settings software**.

---

### Post by Aries01 on 2011-10-10
The proprietary driver screen settings software did the trick. Thanks for the tip.

---

