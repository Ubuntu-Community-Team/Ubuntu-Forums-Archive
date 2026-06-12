---
title: "How to fix the sound on a Gateway MT3707"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by ctlongley on 2008-02-28
**Step 1:** Download the ALSA sound driver 1.0.15rc1, ALSA lib 1.0.15rc1, and the patch file.

[patch_sigmatel.c.patch-1.0.15rc1-simple]("https://bugtrack.alsa-project.org/alsa-bug/file_download.php?file_id=2229&type=bug")
[ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15rc1.tar.bz2]("ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15rc1.tar.bz2")
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc1.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc1.tar.bz2")

**Step 2:** Open package manager, and search for "build-essential" and install it.
**Step 3:** Open the terminal, cd into the appropriate directory, and copy/paste the following commands one line at a time until the process has been completed: (For the sake of simplicity, I downloaded all of my files into a directory called Sound on my Desktop)

[I]tar xfj alsa-driver-1.0.15rc1.tar.bz2
tar xfj alsa-lib-1.0.15rc1.tar.bz2   
sudo patch alsa-driver-1.0.15rc1/alsa-kernel/pci/hda/patch_sigmatel.c < patch_sigmatel.c.patch-1.0.15rc1-simple
cd alsa-lib-1.0.15rc1/
sudo ./configure 
sudo make 
sudo make install
cd ../alsa-driver-1.0.15rc1/
sudo ./configure 
sudo make 
sudo make install[/I]

**Step 4:** Restart your computer. You should hear the ubuntu log in sounds when you come back into the system.

That's it (at least, that was all I had to do to get it working). I have never used ubuntu before, but this method worked to get my sound working on Fedora 6. For everyone who complains that linux is too difficult or a pain in the *** to configure (which I would agree with), you can find EVERYTHING in message boards if you search enough - that's where I got the patch file.

**Let me know if this worked for you or if the above is confusing.**

---

### Post by Shoadow56 on 2008-02-29
You sir, are amazing. This worked on my Gateway MT3705 laptop with an updated version of Gutsy. I checked and the headphone jack also work properly! I absolutely love you!

---

### Post by eyeonthewinner on 2008-03-15
don't try on an m3701... 
Error "No volume control GStreamer devices and/or plugins found"
whoops, guess im reinstalling at some point, didn't work before not any different but would like another try...

---

### Post by indyj717 on 2008-03-16
What you want to do when that happens is go to software sources and enable unsupported updates (gutsy-backports)

Then go to synaptic package manager and download the package "Linux-backports-modules-2.6.22-14-generic"

restart and sound should work

---

### Post by jawmill on 2008-03-28
Your post was very helpful but i am still so new to ubuntu that I can't Get it to work. Step 3 is where i have my problems. 
Step 3: Open the terminal, cd into the appropriate directory, and copy/paste the following commands one line at a time until the process has been completed:

What terminal do i open? is it on the cd or something?

Where is the appropriate directory? I don't know where ubuntu stores everything. (I'm fresh out of windows)

These stupid questions may be my only problems.

thanks
Jawmill

---

### Post by jjacks on 2008-03-29
Terminal is an application that can be found under:

Applications - Accessories - Terminal

As for me, I followed the install "by the numbers" and did not have success.  At this point, I am not sure what to try.  Any thoughts?  By the way, I did not have any errors on the install, it looked like everything was going great, but after the reboot, no sound.

Great directions though!

---

