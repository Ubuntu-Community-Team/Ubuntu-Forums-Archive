---
title: "Packard Bell Easynote HDMI output black screen"
date: 2011-09-13
forum: Hardware
---

### Post by batgranny on 2011-09-13
Hi folks, 
 
I'm a long time Ubuntu user who has recently purchased a Packard Bell  EasyNote (model PEW92).  As is usual whenever I get a new laptop the  first thing I did was to I attempt to install Ubuntu on it but I'm  having a little bit of an issue and I'm wondering if anyone here could  help me. 

When I boot the live CD it seems that the OS assumes my HDMI output is  my primary display and my laptop screen remains off. When Ubuntu has  booted and I go into the monitor properties I can see that there are two  displays, one marked OEM and one marked laptop.  The OEM display  controls my HDMI output but changes to the display marked 'laptop' don;t  have any effect on my laptop screen and I haven't been able to activate  it.

Has anyone come across this issue before? I've done a bit of Googling but nothing's come up. If anyone can help in any way at all I would be very grateful.

---

### Post by diasf on 2011-09-13
Did you try the Fn keys, on the laptop's keyboard, that change the current monitor?

---

### Post by batgranny on 2011-09-13
Yeah, they don't do anything, at least when I'm booted into the live CD.  Thanks though.

---

### Post by bgturk on 2011-12-31
I am experiencing a similar problem with Packard Bell. Have you been able to resolve it? If so, could you please post the solution.

---

### Post by batgranny on 2011-12-31
I'm afraid not.  I've had to go back to Windows until a solution turns up.  It's not so bad though, Win 7 is a pretty cool OS.

---

### Post by batgranny on 2012-04-28
Just giving this a little bump just in case there's been any movement on this issue.  If not, should I submit a bug report?  if so how do I do that?

---

### Post by batgranny on 2012-06-04
There is a [bug report on launchpad ]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/765438")for this issue.  Here's a workaround:

Add "acpi_osi=Linux" in your boot options. For example, modify /etc/default/grub like this:
GRUB_CMDLINE_LINUX_DEFAULT=“quiet splash acpi_osi=Linux”
then run update-grub and reboot.
 After boot you will be enable to change backlight power with notebook hardware keys.


In my case the laptop boots with a black screen but once it has booted to the login screen I can use my brightness keys to bring the screen to life.


Hope this helps someone until the issue is fixed.

---

