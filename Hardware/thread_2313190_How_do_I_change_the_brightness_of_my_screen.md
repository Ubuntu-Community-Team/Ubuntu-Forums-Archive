---
title: "How do I change the brightness of my screen?"
date: 2016-02-10
forum: Hardware
---

### Post by MJae on 2016-02-10
Sorry if this is a really stupid question but I've been googling and searching out the forums and I just can't find a solution. I've tried a couple things but none of them worked. (Most the results are really old, too.)

I've tried [FONT=courier new]xbacklight[/FONT] but the monitor doesn't respond. There's[FONT=courier new] indicator-brightness[/FONT] and the brightness plugin from the [FONT=courier new]xfce4-power-manager-plugins [/FONT]package. They both report, "No backlights were found in your system". Which probably explains why [FONT=courier new]xbacklight[/FONT] won't do anything.

I know there is a brightness settings tool for Xubuntu somewhere. At least, my 12.04 installation does. However, that one is installed on my laptop which has its function keys for those settings so that's a double-up. I'm having a problem on my 14.04 installation here on the desktop. It's got none of those function keys and the monitor itself only has one button: the power button.

I've also found this command: [FONT=courier new]sudo setpci -s 00:02.0 F4.B=50[/FONT]. I get: [FONT=courier new]Warning: No devices selected for "F4.B=50"[/FONT].

Please, help. Thanks!

---

### Post by coldraven on 2016-02-10
> It's got none of those function keys and the monitor itself only has one button: the power button.

What make of monitor is that? Have you tried searching for the manufacturers instruction manual?

---

### Post by MJae on 2016-02-10
It says Samsung SMS19A100N.

And, no I didn't search for the instruction manual. Since, you mentioned it, I have. (As you might have guessed, it never crossed my mind to look for the instruction manual.)

I found it here: [http://downloadcenter.samsung.com/content/UM/201205/20120517112305649/SA10-04Eng.PDF](http://downloadcenter.samsung.com/content/UM/201205/20120517112305649/SA10-04Eng.PDF). Apparently, everything is controlled by that single power button.

Thanks a lot for your help!

---

