---
title: "Latitude D800 suspend issues"
date: 2006-11-12
forum: Hardware &amp; Laptops
---

### Post by Dark_Wolf77 on 2006-11-12
I'm running Ubuntu on a Latitude C800, and once I upgraded to Edgy, suspend no longer works properly. I have it set to suspend when the laptop lid is closed, and for whatever reason when I close the laptop lid, it doesn't suspend, it merely logs me out of my session and puts it into the login screen again. Oddly, suspend works fine otherwise: if I use the power icon to tell it to suspend, it's fine, and if I use the function keys it also works fine, down to waking up from suspend when I open the laptop lid. Any ideas?

---

### Post by ignavia on 2006-11-13
I'm having the same problem on my C500. I posted a message [here](http://ubuntuforums.org/showthread.php?t=299277), in case you want to follow it.

---

### Post by ignavia on 2006-11-14
Here's what worked for me:

From the thread [http://www.ubuntuforums.org/showthread.php?t=284872](http://www.ubuntuforums.org/showthread.php?t=284872) (modified)

Add the following to the bottom of your /etc/X11/gdm/gdm.conf-custom

```

# Definition of the standard X server.
[server-Standard]
name=Standard server
command=/usr/X11R6/bin/X -br -audit 0 -noacpi

```

The original thread states to edit the gdm.conf file, but the file explicitly states not to edit it, that the -custom file will overwrite any settings, so I added the lines there.

---

### Post by Dark_Wolf77 on 2006-11-15
That fixed it! thanks alot, Ubuntu support rocks.

---

