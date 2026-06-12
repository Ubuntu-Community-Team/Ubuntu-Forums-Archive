---
title: "Night of the Living Touchpad"
date: 2006-07-03
forum: Hardware &amp; Laptops
---

### Post by dregs on 2006-07-03
I have found plenty of good advice on the forums about getting my Alps touchpad working the way I like it on my Dell laptop. I have an xorg.conf file that works great.

HOWEVER, sometimes after I hibernate the touchpad starts behaving differently. Then I have to do sudo rm xorg.conf; cp xorg.conf.save xorg.conf; reboot to get things working again. It fixes the problem, but it's really annoying. 

Is there a known workaround? I just want my xorg.conf to stay put more reliably!

---

### Post by ericesque on 2006-07-03
um, don't let your lappy hibernate.  Hibernation is for bears.

roar.

---

### Post by dregs on 2006-07-03
My laptop is a bear.

Seriously, though, the whole point of having a laptop is mobility. Are you saying I should completely shut down every time I take a break from working? Now that Dapper has ACPI working (mostly) I've been enjoying both suspend and hibernate. In fact, on Breezy, hibernate didn't affect the touchpad at all. I don't remember having to mess with xorg.conf all the time the way I do with Dapper.

---

### Post by leadweight on 2006-07-03
I have more or less the same problem with a toshiba notebook.  reboot fixes it without the file manipulations.  I see lots of folks with touchpad problems and no answers.  Doesn't anyone who knows anything read these posts.

---

### Post by dregs on 2006-07-04
I found that my Alps migrated from /dev/input/event2 to /dev/input/event3 mysteriously. Changing the appropriate entry in /etc/X11/xorg.conf seems to have helped for now. But why did it migrate? Will it happen again? Why is this so difficult?

---

### Post by ericesque on 2006-07-05
most likely because your laptop is a bear.

---

