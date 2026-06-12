---
title: "How I got suspend and hibernate working on a T43 with Gutsy"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by mperry on 2007-12-27
I spent a good deal of time on this and thought I would share a bit of what I've learned to date on my T43 Thinkpad.  First off, suspend and hibernate were not working out of the box so I went hunting solutions.  Here is what I did:

1) I installed uswsusp only to find that it did not have s2ram in the 
ubuntu package.  The s2both or whatever does not do the same for me so I removed the ubuntu package. I installed the one from Debian Lenny instead.  I then 
changed the hal suspend and hibernate scripts to only call s2ram and 
s2disk respectively.  These scripts are:

/usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux 
/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux

For the hibernate one, I simply backed up the original file and removed 
all the stuff and just put in s2disk. For the suspend, I put in s2ram.

2) I had a problem with screensavers either of gnome or the X variety. I 
removed both packages.  The gnome screensaver I think caused my T43 to 
blank out and not come back if I left it alone for some period of time.
For some reason with this activated my laptop would lock up solid when I left it alone and the screen blanked out.

3) I ensured that the /etc/uswsusp.conf called the swap 
partition by its /dev/ name and not the UUID.

4) I edited the /etc/initramfs-tools/conf.d/resume and ensured it had 
the correct swap UUID label.  Surprise!  Mine did not. 

5) I edited /etc/X11/xorg.conf and added in:

Section Device
...

Option          "VBERestore"    "true"

I also added in:

Section "ServerLayout"
...

Option          "BlankTime"     "15"
        Option          "StandbyTime"   "30"
#        Option          "SuspendTime"   "45"
#        Option          "OffTime"       "10"

I'm still playing around with the last two options a bit so I tend to 
comment them out and restart X and then try things.

Other steps I had to take which may be related or not...

1) I had to change how /etc/acpi/screenblank.sh operated. It makes a 
call to /usr/share/acpi-support/screenblank and I removed the lines 
which reset dpms and the rest of it.

2) I restarted acpid many times and every time I touched anything that even remotely looked like acpi stuff.

3) I edited menu.lst and included the following to defoptions:

# acpi_sleep=s3_bios resume=/dev/sda5

Then I ran update-grub as the root user.

4) I restarted acpid many more times

At this point, my T43 suspends and resumes about 95% of the time and the lockups when its left alone are gone completely.  My T43 is an experiment of one so your mileage may definitely vary when you do some of these things.

---

