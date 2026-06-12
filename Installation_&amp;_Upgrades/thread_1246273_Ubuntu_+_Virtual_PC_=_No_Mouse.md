---
title: "Ubuntu + Virtual PC = No Mouse"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by michaeljbergin on 2009-08-21
I'm trying install Ubuntu 9.0.4 in VirutalPC and everything reasonably well except for the mouse.  Its just totally unresponsible and I have to work through the UI with the keyboard.  I know there were bugs in the Linux PS/2 driver years back that caused this in VPC and VMWare but hard to believe that wouldn't have been fixed by now.  Is there any virtualization solution I can use on Windows that Linux will like?  Thanks

---

### Post by lemming465 on 2009-08-26
I've had reasonable results using both vmware and virtualbox.  I don't have any experience with Microsoft's variant.

---

### Post by Cybie257 on 2009-08-27
> **michaeljbergin said:**
> I'm trying install Ubuntu 9.0.4 in VirutalPC and everything reasonably well except for the mouse.  Its just totally unresponsible and I have to work through the UI with the keyboard.  I know there were bugs in the Linux PS/2 driver years back that caused this in VPC and VMWare but hard to believe that wouldn't have been fixed by now.  Is there any virtualization solution I can use on Windows that Linux will like?  Thanks

Use Virtual Box Binaries (Not Open Source Edition). Virtual PC is a Microsoft Product (last I ever looked at it) and I seriously doubt that MS would spend any time fixing a Linux related issue. Or, maybe this is just an anti-MS opinion, LoL.

[http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")

-Cybie

PS. VBox seems to be a bit tricky to get the addons to work correctly for releasing the mouse from the window, but easy enough to simply click the right CTRL button to do so.

---

### Post by BossBri on 2009-10-03
Michael,

I had this same problem when installing 9.04 in Virtual PC.  I managed to find a pretty simple fix.

In your grub startup file (/boot/grub/menu.lst) you need to add the "i8042.noloop" kernel option.  Just add that flag to the end of the line that starts with "kernel".  The line is towards the end of the file.

Also, if you're using a wheel mouse, I found that I needed to use the psmouse.proto=imps option to enable the wheel.

Hope this helps.

---

### Post by drifting on 2009-11-23
Drat I have the same problem with 9.10 . And this is on a company machine so I do not have the luxury of being able to choose the virtualisation technology.

9.10 does not have the menu.lst in /boot/grub ?

Paul.

---

### Post by presence1960 on 2009-11-23
> **drifting said:**
> Drat I have the same problem with 9.10 . And this is on a company machine so I do not have the luxury of being able to choose the virtualisation technology.

9.10 does not have the menu.lst in /boot/grub ?

Paul.

9.10 uses GRUB 2. it is totally different than legacy GRUB. See [here]("https://help.ubuntu.com/community/Grub2")

---

### Post by drifting on 2009-11-25
Thanks for the link, if I knew what I was doing I could be dangerous, not too sure on where I would add the line suggested in the new grub.cfg, so for now I am stick with windows 7 and no ubuntu mouse.

Paul

---

