---
title: "[Hardy] Eject USB hard disk gives error and remounts"
date: 2008-07-28
forum: Hardware
---

### Post by sploeger on 2008-07-28
Hi,

I am using Xubuntu 8.04 (Hardy) on amd64 and experience the following problem. When right-clicking my USB external hard disk on the desktop and choosing "Eject Volume" I get an error message saying "Unable to eject [volume name]: An unknown error occurred". The disk is then remounted immediately.

I have searched the forums and a fix for this problem on Feisty systems has been given here: [http://ubuntuforums.org/showthread.php?t=540148]("http://ubuntuforums.org/showthread.php?t=540148").

I would love to apply this fix on my Hardy system, but it does not have a file /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi

Does anybody know how to fix this problem in Hardy?

Unmounting/ejecting USB flash drives works normally. The problem only pops up with my external USB hard disk.

Unmounting the disk from the command line works, but I want it to work via the GUI.

Thanks in advance!

---

### Post by jimmy the saint on 2008-07-28
The issue is that two tools are active to deal with automounting by default, and they don't always play nicely together.  There is a solution here [http://ubuntuforums.org/showthread.php?t=854557](http://ubuntuforums.org/showthread.php?t=854557)

You can either follow that, or remove the gnome mounting tool.  I forget what it is called.  I have disabled Thunars volume management and I haven't seen any problems so far.  The one exception is that seagate freeagent drives don't seem to unmount properly, but this is an issue with seagate.  The remounting thing is definitely the conflicting mounting tools though.

---

### Post by sploeger on 2008-07-29
Thanks jimmy, your solution solves one part of the problem: now when I choose "Eject Volume" the hard disk is unmounted and stays unmounted.

However, after unmounting I still get the error message I mentioned above: "unable to eject volume".

Does this mean that the system tries to eject the disk, as is possible with optical drives? Then it is obvious why the eject fails... :) My hard disk should only be unmounted, not ejected.

I would have expected an "Unmount volume" menu option instead of "Eject volume" here. I see that there have been discussions about this on various websites, that I do not want to initiate here again. I am just wondering whether the system under the hood really tries to "eject" the hard disk, like the menu option suggests.

Thanks again.

---

### Post by jimmy the saint on 2008-07-30
I have a similar problem with that seagate drive.  I know that there was a post somewhere on here that indicated that emptying the trash on the drive helps sometimes.  I don't remember what type of drive he had though.  It's worth a shot.  It might be a reportable bug.

---

### Post by sploeger on 2008-07-30
I cannot find a trash folder on the drive, so I guess this won't help much. Thanks for the tip, though. ;)

Does anybody know how I can find out what script Thunar executes when choosing "Eject Volume" from the menu? I am really wondering what it's doing under the hood.

Also, I am still interested in a fix for Hardy similar to the one for Feisty that I mentioned in my first post.

---

### Post by sploeger on 2008-07-30
I just went ahead and created a bug report for this, cause I think this is something that should be investigated more thoroughly.
[https://bugs.launchpad.net/bugs/253468]("https://bugs.launchpad.net/bugs/253468")

---

### Post by jimmy the saint on 2008-07-31
Just curious, did you disbale the Thunar volume management (either through the settings manager or through Thunar itself)?  If you did that instead of the gnome-mount, or whatever its called, it isn't Thunars volume management (Volman) that is the issue becasue it is no longer functional.  If that is the case, the bug should be submitted against the gnome app.

---

### Post by sploeger on 2008-07-31
Actually, I am at a loss about what component is the culprit here. Thunar has something to do with it, because disabling the thunar-volman solved part of the problem. However, like you say, it can't be just a Thunar-issue because part of the problem persisted afterwards. Then again, when I choose "Eject Volume" from the context menu, isn't Thunar handling that call in the first place?

I don't think it's a Gnome-issue, because I don't have the gnome-volume-manager installed. As I understand it, gnome-mount is a command-line tool and not a daemon or volume manager, right? And in Gnome, the gnome-volume-manager is calling gnome-mount under the hood. I'm not sure if gnome-mount gets called at all on my system, but if so, do you know what program could be calling it?

Currently, I believe the issue may involve both Thunar and HAL. As HAL is a very widely used layer (also on Gnome/KDE systems), I figure other Hardy-users would have found this issue already if it only had to do with HAL. So I decided to file the bug as a Thunar-bug for now. I am lacking expertise here to determine the real cause, so I'm hoping some Thunar developer can narrow it down...

---

