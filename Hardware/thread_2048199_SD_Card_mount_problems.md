---
title: "SD Card mount problems"
date: 2012-08-26
forum: Hardware
---

### Post by Cammy on 2012-08-26
I used to connect my Canon Rebel directly to my PC, and the gthumb photo import tool would automatically open, and I could import pics.

Since installing 12.04, the camera is no longer detected, and I've not been able to get ubuntu to detect it.  So, I bought an internal SD card reader, but that has brought it's own problems.

When I insert an SD card, it mounts fine, but it's nearly impossible to copy files from it.  A 1 meg file takes over a full minute, so copying 100 pics that are 6+ megs each takes an inordinate amount of time.

I have tried various lines in fstab to no avail (maybe I'm using the wrong arguments?)

If I open the Disk administrator, I can select the card (16 GB Drive), click the little gear icon, and click "mount options".  I cam change the options here to get it to mount, but they revert upon next boot.

This is very annoying!  How can I get ubuntu to mount the card with full privilages?

---

### Post by sanderj on 2012-08-26
Some things worth trying to pinpoint the cause:

same card in a different machine
same card in a different Ubuntu version
other card in the same machine

That way you should be able to logically find out what the cause is

HTH

---

### Post by Cammy on 2012-08-26
Good ideas.  I've tried three different cards in this machine now, and they all do the exact same thing.  I don't have another ubuntu machine, but the cards read fine in my Win7 machine.

If I insert the card and go to a terminal, I can unmount it, then remount it using this:

mount -t vfat -o rw,umask=000 /dev/sdb1 /media/EOS_DIGITAL

Then it works perfectly fine.

(/media/EOS_DIGITAL is a folder I created and chmoded to 777)

But if I reboot then insert the card again, I'm back to the permissions problems.

---

### Post by Jedcurtis on 2012-08-26
I think you'll find the only way for it to work is to reboot with the SD card inserted.  When it boots up the next time with the SD card inserted it should mount automatically.  A pain I know, as this is the only way mine works as well.  As an avid photographer I'm hopeful they'll get this taken care of quickly.  Yours isn't the only post complaining about this issue...

Jed

---

### Post by Cammy on 2012-08-26
Thanks for that info Jed.  Now that I know it's a known bug, I can write a bash script as a workaround.  Plug in the card, run the script (that unmounts and remounts it) and I should be good to go.

---

### Post by Jedcurtis on 2012-08-27
Cammy, I wouldn't mind getting a copy of that bash script from you if you get it working.  I've been unable to get a script to work, though I'm the first to admit my skills are definitely limited!

Jed

---

### Post by Cammy on 2012-08-27
My luck hasn't improved much, Jed.

I installed something called 'pysdm' to see if I would have any luck with it getting the SD card to mount.  At first it seemed promising because I was able to get the card to work with proper permissions.

Then, suddenly, /dev/sdb1 vanished and hasn't been back.  Google has been no help with this at all, so I am going to try an OS reinstall before possibly rolling back to 10.10, which was the last version of ubuntu where I didn't have a plethora of problems.

I hope you have better luck than I've had!

---

