---
title: "Wacom Digitizer Calibration? - Toughbook CF-19 mk1"
date: 2009-12-31
forum: Hardware
---

### Post by RobotFreak on 2009-12-31
Hello all,

I loaded Ubuntu 9.10 on my Toughbook CF-19. So far so good, all hardware seems to be recognized. The digitizer is working, but it isn't calibrated.

In the top-left corner the cursor is in the right place. Moving to the bottom-right it stays behind about 200px horizontal and a few vertical.

I found the wacomcpl utility, but nothing shows up in there.

Can anyone help me?

Thanks a lot,
RobotFreak

---

### Post by Favux on 2009-12-31
Hi RobotFreak,

Welcome to Ubuntu forums!

Please go the this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  Download the new-generic rc2 .fdi attached to the bottom.  Instructions on installing it are in Section 2 b).  Then go to Section 3 to setup wacomcpl.  You should be able to see your devices in wacomcpl with the new .fdi.

Hope this helps.

---

### Post by RobotFreak on 2010-01-03
Thanks, the digitizer is calibrated now.

I changed the calibration by hand; the pen was so far off that the calibration GUI did not read the presses on the arrows. An improvement point for Ubuntu!

---

### Post by Favux on 2010-01-03
Hi RobotFreak,

Good work!  You're welcome.  Thanks for posting the .xinitrc.

---

### Post by RobotFreak on 2010-01-03
Hello Favux,

I reinstalled Ubuntu because I wanted to remove Windows 7.
When I tried (twice and from usb boot) to manually select swap (2.5GB), root (20GB) and home (57 GB) the installation of the wacom digitizer did not work.

Then I tried it with the default installation settings and I could configure the digitizer right away...

A bit weird, don't you think?

Kind regards,
Robot Freak

---

### Post by Favux on 2010-01-03
Hi RobotFreak,

Yes, I don't understand that.  Partitioning shouldn't affect linuxwacom install.

---

