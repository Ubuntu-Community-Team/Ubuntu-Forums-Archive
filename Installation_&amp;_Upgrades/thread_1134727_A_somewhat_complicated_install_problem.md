---
title: "A somewhat complicated install problem"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by Random2 on 2009-04-23
First off, than you for talking the time to read this.  There's a little bit of a backstory to the probem, so please bear with the long introduction.

I've been running a dual-boot system (ubuntu and windows) for a little while now, and GRUB has been the boot interface that I've used to choose between them.  However, I noticed that there were errors with my NTFS Vista partition, and I need to fix that.  When I registered chkdsk for use and restarted the computer, it wouldn't run.  I assumed this was because of GRUB taking over the boot and simply skipping this step by directly going to the windows partition. 

So, when 9.04 was realeased, I figured I could uninstall my current ubuntu distro, use chkdsk to repair windows (and shrink it down more) and then install 9.04.  I found a thread reccomending the use of G-parted to delete the ubuntu partition, which I did.  
However, it seems that I should've read further, because GRUB still remains on my system.  But, I can't access the windows partition because GRUB informs me of an "Error 22" and cannot procede further.  
I did check to see if the windows partition was flagged as boot, and it is.  I can still access my computer via the live boot CD for 9.04, but I would like to be able to remove GRUB, repair and shrink vista, and then install 9.04 and GRUB correctly. 

Is there any way to do this without wiping my harddrive?

Than you for your time.
     Scott

---

### Post by Random2 on 2009-04-24
Also, I did try installing 9.04, but it did not resolve the problem.

---

