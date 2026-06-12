---
title: "Resume problem HP DV 1325"
date: 2006-07-22
forum: Hardware &amp; Laptops
---

### Post by medisoft on 2006-07-22
Hi! i have a problem with my laptop. I can suspend to ram and it works perfectly, but when i suspend to disk it suspends, but sometimes it resumes OK and sometimes not.

When it does not resumes is only because the video, because all other elements of the systems works very well, but the video comes crazy, with lines and blinking, i still can change to textmode (in that mode i also see anything but lines blinking) and login and reboot.

I think it may be something with the post of the video, but i don't know how to check it.

Can you tell me how i can do changes to the method of the video resuming?

Thank you.

---

### Post by reacocard on 2006-07-22
look at your /etc/default/acpi-support file. there some options in there that might help. you could also look into suspend2 for hibernation (see my sig).

---

