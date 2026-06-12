---
title: "update destroyed video... please help"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by swajime on 2008-12-20
Howdy,

I just installed the latest updates for my ubuntu system, and lost my video.  :-(

I video-taped the results, and placed here -> [http://tow.swajime.com/video/P1010790.MOV](http://tow.swajime.com/video/P1010790.MOV)
This file is very 80 Mb, and most browsers will time out when trying to load it.
Use wget to retrieve it.

I placed the output of hwinfo here -> [http://tow.swajime.com/video/hwinfo.txt](http://tow.swajime.com/video/hwinfo.txt)

Any help would be very appreciated.

john

---

### Post by swajime on 2008-12-20
X

---

### Post by swajime on 2008-12-20
X

---

### Post by swajime on 2008-12-20
I downloaded and installed the driver from Intel's site [http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html)

I changed the grub entry options to "ro screen=1280x1024 vsync=60 xmodule=i810 vga=ext"
 
I've run intel_reg_dumper and placed the output in [http://tow.swajime.com/video/intel_regs.txt](http://tow.swajime.com/video/intel_regs.txt)

I still have the same problem.  It 'looks' like the vsync is not set right, but I don't know what to set it to.

I do not know what to try next... :confused:

I haven't had any responses to this thread... Any help would be appreciated.

john

---

### Post by schimschone on 2008-12-20
Have you tried booting from the previous kernel on startup? The last update caused some entirely different issue for me.. so I just went back to the previous kernel until this one gets settled.

That may not help much, but it's the best I got.

schim

---

### Post by swajime on 2008-12-21
Schim,

Thank you for your suggestion.  I tried this, and it has no effect.  So far, everything that I have tried has appeared to have no effect at all. :-(

john

---

### Post by swajime on 2008-12-22
I put this on hold until somebody figures something out.  I've wasted too much time on it already.  For now, I switched to an older, smaller monitor with a lower resolution.

Another "feature" of the latest updates... : flashplayer lost audio
In case anybody else hits this one, the fix turned out to be installing 'libflashsupport', as mentioned here -> [http://ubuntuforums.org/showthread.php?t=613966](http://ubuntuforums.org/showthread.php?t=613966)

I am hoping that there are no more surprises of this nature.

john

---

### Post by swajime on 2008-12-23
Here's another side-effect of this last set of updates...

Evolution started underlining every word in every email with squigally underscores.
I had to go to the menu - Edit | Current Languages | English
The choices there were 6 flavors of English, and also Turkish !??

This was the wierdest set of updates I've ever had.
I've also never had so many updates at once.
Was this some sort of major release of Ubuntu?

I haven't been using ubuntu for that long, I thought that I had been using 8.10 for quite some time now.

---

### Post by schimschone on 2008-12-25
I'm curios as to whether your issues are directly related to the kernel update, or something else.. if you booted with prior kernel then all should have reverted.. likewise it wasn't all thatbig of an update from what I remember.

Could you have fiddled with anything else?

schim

---

### Post by swajime on 2008-12-25
It seems that it was a complete upgrade from Hardy to Intrepid.  For some reason, I thought that I had already done that.  It took a couple of hours to do all the downloads, on a 512kb connection.

I also had to reinstall my printer driver: [http://joeb454.ubuntuforums.org/showthread.php?p=6152521#post6152521](http://joeb454.ubuntuforums.org/showthread.php?p=6152521#post6152521)

I suppose I need to pay more attention in the future.

john

---

