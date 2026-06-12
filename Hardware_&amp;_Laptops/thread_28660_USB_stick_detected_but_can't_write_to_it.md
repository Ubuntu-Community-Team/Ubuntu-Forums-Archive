---
title: "USB stick detected but can't write to it"
date: 2005-04-21
forum: Hardware &amp; Laptops
---

### Post by emmet on 2005-04-21
Hi All,

I'm a newbie to Ubuntu,  but I'm pretty happy with it so far.

I've just come across a little problem, which I'm sure is trivial to solve, but I can't work out what I'm doing wrong.

I insert my USB memory stick into a free USB port and the system recognised and mounts it without any problems. The desktop icon appears in Gnome and I can open Nautilus to see the contents. So far, so good!  :smile: 

I tried to delete the contents, but a message appeared saying 'not superuser'. Strange, but then there's probably something misconfigured in fstab, but I was in a hurry, so I sudo'd the command instead to delete everything. I then copied some new files over (also using sudo).

I then removed the stick and gave it to my wife.....

She just called me to say that there's nothing on the stick, even though when I did an ls, I saw the contents, and they were also there in Nautilus.

Any idea what I could be doing wrong here?

Thanks in advance,

Emmet

---

### Post by fdoving on 2005-04-21
[QUOTE=emmet]Hi All,

I'm a newbie to Ubuntu,  but I'm pretty happy with it so far.

I've just come across a little problem, which I'm sure is trivial to solve, but I can't work out what I'm doing wrong.

I insert my USB memory stick into a free USB port and the system recognised and mounts it without any problems. The desktop icon appears in Gnome and I can open Nautilus to see the contents. So far, so good!  :smile: 

I tried to delete the contents, but a message appeared saying 'not superuser'. Strange, but then there's probably something misconfigured in fstab, but I was in a hurry, so I sudo'd the command instead to delete everything. I then copied some new files over (also using sudo).

I then removed the stick and gave it to my wife.....

She just called me to say that there's nothing on the stick, even though when I did an ls, I saw the contents, and they were also there in Nautilus.

Any idea what I could be doing wrong here?

Thanks in advance,

Emmet[/QUOTE]
 If you use gnome-volume-manager to auto-mount with pmount (something you probably do, as the stick is automounted) fstab entries shouldn't be needed. If you have fstab entries, try to remove or disable them (add # at the start of the line).

As for the lost files, which you could see when you did an ls, you either need to run 'sync' in the terminal, umount the device properly (which does sync automatically before umounting), or you'll need to add a sync options to fstab. Take a look at 'man mount' for more details about fstab and mount options.


- Frode

---

### Post by emmet on 2005-04-21
[QUOTE=fdoving]If you use gnome-volume-manager to auto-mount with pmount (something you probably do, as the stick is automounted) fstab entries shouldn't be needed. If you have fstab entries, try to remove or disable them (add # at the start of the line).

As for the lost files, which you could see when you did an ls, you either need to run 'sync' in the terminal, umount the device properly (which does sync automatically before umounting), or you'll need to add a sync options to fstab. Take a look at 'man mount' for more details about fstab and mount options.


- Frode[/QUOTE]

Seriously sheepish grin time here....

I've spoken to the wife again....it was ***Windows*** that wasn't mounting the USB stick correctly, so it looked like it was empty. She tried it on another laptop, and the files were there.

Shame on me for thinking this was an Ubuntu error...

Thank you so much for the suggestions Frode, I didn't know about the 'sync' command, and that is really good to know about.

I'm going to revisit the superuser-only access problem when I have the USB stick in my possession again to see if this is a real problem.

Many thanks again,

Emmet

---

