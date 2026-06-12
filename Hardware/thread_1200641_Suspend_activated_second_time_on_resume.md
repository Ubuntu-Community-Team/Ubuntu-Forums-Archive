---
title: "Suspend activated second time on resume"
date: 2009-06-30
forum: Hardware
---

### Post by slightly72 on 2009-06-30
I have a strange problem with suspend on a Thinkpad R61, running Jaunty (9.04), kernel 2.6.28-13-generic, Nvidia Quadro NVS 140M using the 180 version of the driver. When I close the lid, the system suspends without any problems. When I open the lid, the system resumes (I can see my windows) and then suspends immediately again. When I open the lid the second time, the notebook resumes without any problems.

I've had this problem when trying version 173 of the driver too. These problems started yesterday after upgrading to Jaunty from 8.10. I could not find a solution for this on the forums.

A bit of history: when using Ubuntu 8.10, versions 177 and 180 of the NVidia drivers were having problems, could not resume at all. Version 173 was almost perfect, it was resuming and not causing problems on logout, except that I had to have the screen locked on resume, otherwise the visual content of the windows was garbled. After upgrading to Jaunty, version 173 started to have this twice suspend problem too, and, sometimes, garbling the contents of the windows too; version 180 at least had only the twice suspend problem.

Any ideas on solving this are appreciated. If you need any logs, I can post them. Unfortunately, the /var/log/pm-suspend.log is overwritten on the second suspend/resume and I can't see what's happening between the two. Any way to save more than one log?

---

### Post by slightly72 on 2009-07-06
OK, I found the solution, but not entirely sure what why it works. I had to go to System->Preferences->Power Management (or run gnome-power-preferences) and in the "General" tag, set "When the suspend button is pressed:" to "Nothing". I have both in the "On AC Power" and "On Battery Power" set "When laptop lid is closed" to "Suspend". I think that gnome-power-manager was receiving two suspend events, both from "lid closed" and the suspend button pressed. I did not bother me that the suspend button is disabled, I've never used it.

If it bothers you, I found some stuff related to this problem on the web, but was not quite willing to go into a lot of script editing. I'm posting it here if other people are interested:

[http://bbs.archlinux.org/viewtopic.php?id=58129]("http://bbs.archlinux.org/viewtopic.php?id=58129")

[http://www.thinkwiki.org/wiki/Problems_with_ACPI_suspend-to-ram]("http://www.thinkwiki.org/wiki/Problems_with_ACPI_suspend-to-ram")  look for "Immediate suspend on resume"

---

