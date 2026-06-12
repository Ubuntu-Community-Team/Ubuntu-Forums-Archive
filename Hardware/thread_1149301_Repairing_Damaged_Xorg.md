---
title: "Repairing Damaged Xorg"
date: 2009-05-05
forum: Hardware
---

### Post by Falcata on 2009-05-05
I've just spent the last 12 hours trying to help a friend of mine get her computer's xorg.conf fixed, and nothing's working.  Everything we've tried has failed.  My friend's not good with the command line, and so I've been helping her while she runs pidgin over her laptop.

We've tried running aticonfig which made things worse, and we've tried running defconf and debconf, but those commands either didn't do anything or we didn't understand how to do them.  We've tried running "sudo dpkg-reconfigure -phigh xserver-xorg", but that didn't help anything, and is in fact what caused the problems in the first place!

Reinstalling is not an option, because my friend has no way to back up her files, and can't afford to buy a large enough USB drive.  I know that the Ubuntu install CD must do something to automatically set up xorg.conf, but I don't know what it is and I'm not familiar enough with Ubuntu.  Is there a way to automatically recreate the xorg.conf with full 3D acceleration?  Or, failing that, is there a backup file I don't know about?

I know her video card is a Radeon 4000 series card, but I don't know the specific model.

---

### Post by DJonsson2008 on 2009-05-05
...been there and its not pretty.

you would think there would be some kind of meta script
to help with all this but the deal is giving your screen
the wrong settings can FRY the screen. so always start 
with conservative settings and only rachet up if you
now the monitors limitations with absolute certainty.

in my scenario i've had to decouple the video card/
drivers from the screen/resolution, rolling back to
VESA drivers, which are safe providing my screens
refresh rate, but i'm not sure about exceleration.

if your friend had something that worked before
then you may though be able to find it.

On your own machine first use nautilus to inspect your
/etc/X11 folder and see what you have there.

Then direct your friend to do the same, you may
find plenty of backup files.

Your friend can then use sudo nautilus to cruise the
same directory and try to find their last operable
xorg file by date. 

maybe they can send those files to you by email and you can
help them sort it out?

my /etc/X11 folder now has files with files 
which i've renamed like

xorg.VESA.1024.60rfresh.tested.ok.txt
xorg.Nvidia.1024.60rfresh.NOT.OK.txt
xorg.VESA.1024.76rfresh.tested.ok.txt

and so on.

At least xorg.VESA.1024.60rfresh.tested.ok.txt
gets me a workable screen, from there move forward...

hope that helps.

---

### Post by DJonsson2008 on 2009-05-05
note above i suggested using sudo nautilus, which is a delicate
place to go. perhaps first just use nautilus to see what is there
in etc/X11, but you will need to use sudo nautilus to rename the
files in order to attempt rollback to a known date when the
screen was o.k.

---

### Post by Falcata on 2009-05-05
Okay, we may need to reinstall it, but there's no way to back up the files.  I offered to upload the files to a server I have, but her connection speed is slow and it would take a few days to upload everything.

So, there's one thing I'm wondering: Is there a way to reinstall Ubuntu while leaving the /home directory intact?

---

### Post by wirporte on 2009-05-05
Recent updates to my Ubuntu 8.04 caused a problem with the ATI catalyst drivers and I had to reinstall them.  I pushed esc
when grub loaded and selected recovery mode, then selected restore X conf (don't remember all the options), and it worked well enough 
to allow me to download and intstall the drivers.  This may not work here, but thought I should through out the idea.

---

### Post by Falcata on 2009-05-05
Well, we're going to reinstall it now.  While my friend was away, me and her son were able to set up ssh on her laptop and desktop, and used sftp to download her /home directory onto her laptop.  It's just finished, so we should be able to get it up and running again.

---

### Post by Grey Box on 2009-05-06
There should be a way to do this without having to reinstall Ubuntu!

---

