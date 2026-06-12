---
title: "screen resolution"
date: 2005-04-24
forum: Hardware &amp; Laptops
---

### Post by eduncan01 on 2005-04-24
Hi Ubuntu Users!

I just installed Ubuntu 5.04, and it doesn't allow anything more than 640x480 for a screen resolution when I go to System/Preferences/Screen Resolution.  I know my video card and monitor can support more than that.  How can I fix this?

Thanks
Eric

---

### Post by gunnyman on 2005-04-24
this **REALLY** needs to be added to the ubuntu users guide at ubuntuguide.org:

sudo gedit /etc/X11/xorg.conf

look for the monitor section
make sure you have the specs for your monitor from the manufacturer.
Add refresh rate  values per your manufacturer's specs.

I have a Dell P780 and my file looks like this:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-85
	VertRefresh	48-120
```

---

### Post by Mat10 on 2005-04-25
The problem is a little more than missing the specs on install. It also drops the correct xconfig for no reason after a few restarts.  I'm also trying to get an option instead of a fixed res and refresh.   My xconfig file was empty and I copied and pasted the entire file that was also under the same name that did have the res and refresh rates, this did not change in the preferences after a reboot, nor was the screen res preferences box even showing on the system bar overhead.  Now it shows the preferences but locked.

Tom

---

### Post by Mat10 on 2005-04-25
](*,) OK folks, I have gone back and reinstalled Ubuntu Gnome one more time just to see what happens with reference to this screen resolution problem.  The only thing I have even touched since the install was to download the xmms package and install.  I let Ubuntu choose 1024x768 at install and made no change.  I missed the block that ask for resolutions that you want this machine to not use, because I was too stupid to use the right key to mark them.   Anyway it loads my 1024x768 that I want and the preference says that it is 1024x blah blah blah.

One thing to note here is the line that says "Use this resolution as default for this machine"   I ticked the box yes and previously had not done this.  So I have rebooted four times now and the res stays where it should.  If it fails again then I can only assume the xconfiguration file is getting erased or corrupted.

Am I going crazy or what ?

Tom     ](*,)     ](*,)     ](*,)

---

