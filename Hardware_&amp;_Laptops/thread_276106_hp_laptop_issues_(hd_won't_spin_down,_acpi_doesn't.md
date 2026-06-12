---
title: "hp laptop issues (hd won't spin down, acpi doesn't get some events, etc)"
date: 2006-10-12
forum: Hardware &amp; Laptops
---

### Post by sedd on 2006-10-12
Hi,

I've just put Dapper 6.06 on an HP Compaq nw9440, and I've got a few issues. I've seen most of these issues in other threads for various other laptops, with a pretty low success rate for solving their problems, but I thought I'd give it a shot. What the hell, right?

acpid is not getting the ac power connect/disconnect events. I listen with "tail -f /var/log/acpid" and I see plenty of events from the lid and power buttons, but no ac power events. In gnome, this means that the lil green battery icon always says its charging, when I know its not. This could be a hardware issue, because the lil lightning bolt LED on the front of the computer doesn't come on like it should. But sometimes these lights are controlled via software (like numlock, capslock) so maybe it is a software issue. I haven't let the battery run down, but I'm pretty sure it would just run until it died, not shutting down gracefully, like in [this thread]("http://ubuntuforums.org/showthread.php?t=180764").

As a consequence of not getting the ac-disconnect events, the laptop doesn't go into laptop-mode. I'm not entirely sure what laptop-mode does, but I think it affects hard-disk spindown (makes it easier, and lets it sleep for longer?)  Something keeps accessing the disk every 2 seconds or so, for very short writes (I assume they are writes. reads would get buffered.)  I put noatime into /etc/fstab, but it still happens. Maybe if I could get laptop mode to come on, this would stop. I tried "/etc/init.d/laptop-mode start" but that doesn't work, because I think the script sees that the ac plug is in, even when its not. "/etc/init.d/laptop-mode status" always says that the plug is in.

Also, I can't get it to suspend, and I got it to hibernate and wake-up once, but I changed something and now it won't wake up. But I don't really care about these. Suspend would be nice, but getting a laptop to suspend with linux is like winning the lottery. And it takes as long to hibernate as it does to shutdown and bootup.

Any help on acpi/ac-power issue or the constant-hd-access issue would be very much appreciated.

And I must say that Ubuntu is pretty slick. I run Gentoo on my desktop and I can't imagine trying to get that to work on a laptop. Except for the above mentioned issues, everything just worked. Even the volume buttons and the help button (why does a laptop need a help button?) 

sedd

---

### Post by sedd on 2006-10-16
Ok after some investigating, it turns out that the AC/battery acpi events work fine on the Dapper liveCD.  I probably need to downgrade some package. How would I go about finding out what versions the liveCD packages are, and how do I install a specific version of a certain package?

---

