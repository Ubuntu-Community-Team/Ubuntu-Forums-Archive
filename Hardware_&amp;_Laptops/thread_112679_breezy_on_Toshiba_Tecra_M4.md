---
title: "breezy on Toshiba Tecra M4"
date: 2006-01-04
forum: Hardware &amp; Laptops
---

### Post by intelliboy on 2006-01-04
I'm having problems installing breezy on my Tecra M4. When i start the installation, right in the third step when it detects the cd-rom, it says it couldn't  load a driver for the cd-rom. I suppose the one that usually gets loaded is the ide-cdrom or the generic-cdrom but in this case it only tries to load the linux-floppy and then fails. Is there any boot time parameter i need to supply ??
any help will be appreciated.

---

### Post by thelusiv on 2006-04-03
I'm not sure why the previous poster's cdrom was not detected. I have a Tecra M4 that I've loaded Linux on and it has a combodrive that will write CDs and DVDs as well as read them. I didn't have any problems when installing Breezy.

I did have problems trying to log in. I could get all the way to gdm, log in, and then gnome would start...but it would freeze after playing the login sound, but before bringing up the gnome loading box. So it just played the sound, then it sat there, not even loading anything, and the mouse would work but the keyboard wouldn't.

I fixed this by switching to VT1 and installing nvidia-glx and enabling it, then restarting X. I guess the mobile nvidia card in this thing doesn't like the nv drivers for some reason.

Now, I'm trying to set up the stylus...does anyone have an xorg.conf for a Tecra M4 already? it'd be much appreciated....thanks :)
...edit: just found this thread: [http://ubuntuforums.org/showthread.php?t=107552](http://ubuntuforums.org/showthread.php?t=107552)

intelliboy: what optical drive came with yours?

---

