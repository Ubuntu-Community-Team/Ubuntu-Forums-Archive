---
title: "[SOLVED] Reformatted Deluge download drive.  Now Deluge won't open."
date: 2008-07-29
forum: General Help
---

### Post by ratdog on 2008-07-29
Hello,
I had a problem with my external USB drive where I'd had things downloading, and decided to reformat the drive.  The used to be called Media and I forgot to label it when I formatted it this time.  

Now when I try to open Deluge it displays this message a few times as it trys to download a few different torrents:

   There is not enough free disk space to complete your download.
   This torrents will be paused

It says there are 0kb of free space.

I have uninstalled and reinstalled Deluge in hopes that it would stop trying to download those torrents and still it does the same thing with the new installation.

How do I get it forget about the old settings and act like a fresh install?

---

### Post by DagMan on 2008-07-29
If you are still trying to download to the external drive, the name of the place where it mounts may have changed when the disk label changed.  So for example if it was mounting itself at /media/usb and now it's at /media/usbdisk then /media/usb wouldn't exist and that could be the reason for the error, in which case you would need to point deluge at the new location.

If the above is not the reason, and this is in general and most likely applicable to deluge though I have not specifically used deluge myself, then you would want to just delete the settings in your home directory.  There is likely a hidden folder called .deluge or a hidden file called .delugerc and usually when you wipe this clean it gets recreated with the default settings the next time you start it.

If you purge the configuration files using apt-get, you would do
apt-get remove --purge deluge
then reinstall it.
Using --purge when you remove something with apt doesn't always delete all configuration files I've found. It is supposed to but if the packagae maintainer decided something was best left for some reason, or just overlooked a thing or two, then it can leave things there but it's usually effective.

---

### Post by ratdog on 2008-07-29
Thanks for the reply.
Yes, that is what I was assuming the problem was as well.

I tried 
apt-get remove --purge deluge-torrent
and then reinstalled.

I still get the same error messages and Deluge aborting.

Any other ideas?

---

### Post by kpkeerthi on 2008-07-29
Delete the folder **deluge** under ~/.config and try again.

---

### Post by ratdog on 2008-07-29
That did it!
Thanks a bunch!

---

