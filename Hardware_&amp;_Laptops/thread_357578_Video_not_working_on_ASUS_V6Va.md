---
title: "Video not working on ASUS V6Va"
date: 2007-02-09
forum: Hardware &amp; Laptops
---

### Post by CSMatt on 2007-02-09
I bought an ASUS V6F00VA to replace my awful Sony VAIO.  Ubuntu Dapper worked in almost completely out of the box on the Sony, but I can't get the video to work on the ASUS at all.  When I boot up the Desktop CD, all I get after the boot screens is a blank screen.  The sound works, so I know it didn't freeze.  Booting into safe graphics mode caused something along the lines of the kernel killing processes too fast or something, and it was forced to wait 5 minutes, upon which the same problem happens again.  The laptop has an ATI X700 video card.  This problem occurs with both Dapper and Edgy.  ASUS did provide a driver CD, stating that it contains drivers for most major operaing systems, but I'm not sure if Ubuntu is supported on that disc.

---

### Post by CSMatt on 2007-02-09
The GParted LiveCD doesn't work either.

This is really starting to anger me.  Not having 3D acceleration is one thing.  Not being able to use any graphical resolutions at all is quite another.

---

### Post by CSMatt on 2007-02-11
I've done some wiki searching and found [this](https://wiki.ubuntu.com/Bugs/AtiDriver).  While it's possible that the solutions provided would help if I installed Ubuntu with the text installer and then edited xorg.conf or whatever is recommended, this isn't really going to help in the case of LiveCDs.  I suppose I could download them in source form, change the required lines manually, and then compile the new binary, but based on testimonies it appears that only a few lines need to be changed to fix this, and it seems unreasonable that X.org hasn't provided a patch that incorporated a workaround for this.  It's apparently been documented for almost a year now.  Do the X.org developers just not know about this?

---

### Post by hardyn on 2007-02-12
I had a z71va, same notebook, and i get almost everthing working on it... i do not have the notebook anymore after a horrible experience with asus warranty but that is a story for another day.

edgy installed right out of the box, everthing worked.
i did have ALOT of problem with the x700...  basicly all the drivers are crap.
the "radeon" driver probably worked the best, and its really no work to add resoluions to xorg.conf (im sure you can find lots of documentation on this)

you MUST add the VertRefresh "60.0" as all the drivers like to default to 70hz which will overscan the display and dammage stuff. (again refert xorg.conf documentation.)

if you install the "fglrx" driver you will not have to worry about adding resolutions to xorg.conf, the driver handles that, but the flgrx driver isn't very reliable. again, must add VertRefresh "60.0".  you will also have to add vga=791 to the boot string in grub. (again refer to documentation)  the machine will hang on shutdown and suspend if you do not have this.

you may want to uncomment the "laptop mode" in your acpi config too... it will slow the video card down when running on batter and give you about 20 min more. (again refer to documentation)

hope his helps, lemme know if you need futher help.

---

### Post by CSMatt on 2007-02-13
What was the story about the warranty?  My battery was DOA and Newegg doesn't take returns or replacements for laptops so I have to send it back to ASUS.

---

### Post by hardyn on 2007-02-13
i would not worry about the battery, i never had any trouble with them over stuff like that.

if you would like to know the whole story, PM me and i give you all the gory details.

---

### Post by CSMatt on 2007-02-14
Using the latest GParted LiveCD ISO from SourceForge, I could not get X to display either automatically or by specifying the ati, radeon, or vesa drivers.  So I have a pretty good feeling the Ubuntu versions of those drivers won't work either.  Lower resolutions and/or bits didn't help either.

---

### Post by CSMatt on 2007-02-20
Is there any chance that the secondary display will work?  I suppose I could use GParted with that to set up the partitions.

---

### Post by CSMatt on 2007-03-04
Well, I enabled MonitorLayout in xorg.conf on the LiveCD and X booted sucessfully.  I didn't have to use the GParted CD this time as the Dapper GParted, although older, proved to be satisfactory for my needs at the time.  The LiveCD installer was either smart enough to add the MonitorLayout option from the LiveCD's xorg.conf into the installed xorg.conf or the hardware detection added it in.  However now I can't effectively switch to a resolution any higher than 1024x768.  Switching the driver to "radeon" doesn't help either.

---

### Post by CSMatt on 2007-03-06
Never mind.  I fixed it after finding [this](https://help.ubuntu.com/community/FixVideoResolutionHowto).

---

