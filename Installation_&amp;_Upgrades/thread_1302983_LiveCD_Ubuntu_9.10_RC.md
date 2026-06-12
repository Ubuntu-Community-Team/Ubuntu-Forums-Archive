---
title: "LiveCD Ubuntu 9.10 RC"
date: 2009-10-27
forum: Installation &amp; Upgrades
---

### Post by iamjfarrell on 2009-10-27
I ran the 9.10 RC today from the LiveCD and the whole time I was running it, it kept making my speakers pop. It was very annoying and has me afraid to install it. Has anyone heard of this problem?

---

### Post by Pnuts on 2009-10-27
I am installing now, I got a few crackles several times through the install so far.

It also appears to be hung at 83% "Creating user..." although the HD seems to be working hard. There appears to be a new skip button that is tempting me to push it... o well, hopefully it finishes soon.

---

### Post by iamjfarrell on 2009-10-27
> **Pnuts said:**
> I am installing now, I got a few crackles several times through the install so far.

It also appears to be hung at 83% "Creating user..." although the HD seems to be working hard. There appears to be a new skip button that is tempting me to push it... o well, hopefully it finishes soon.

Yeah. It was really weird. I hope the final release doesn't do that. Otherwise I will be stuck on 9.04 and I love to be on the blazing edge haha.

---

### Post by jimcuk on 2009-10-28
yip still does it

---

### Post by mark.c.fernando on 2009-10-30
I found a solution for this one and it has worked like a charm for me. Apparently it has something to do with power saver settings. Just:

[LIST=1]
[*]Open the file **/etc/modprobe.d/alsa-base.conf**
[*]Change the **options snd-hda-intel power_save=10 power_save_****controller=****N** line to read **options snd-hda-intel power_save=0 power_save_****controller=****N **(so you're just changing the power_save setting from 10 to 0)
[*]Save the file.
[*]Reboot your computer.
[/LIST]
I got the solution from the comments of this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/442463").

---

### Post by raven01 on 2009-10-30
u do know the final release is out right? lol

---

### Post by mark.c.fernando on 2009-10-30
I know the final release is out. I am using the final release, and the bug is present in the final release.

---

### Post by RandomPSUStudent on 2009-10-30
> **mark.c.fernando said:**
> i found a solution for this one and it has worked like a charm for me. Apparently it has something to do with power saver settings. Just:

[list=1]
[*]open the file **/etc/modprobe.d/alsa-base.conf**
[*]change the **options snd-hda-intel power_save=10 power_save_****controller=****n** line to read **options snd-hda-intel power_save=0 power_save_****controller=****n **(so you're just changing the power_save setting from 10 to 0)
[*]save the file.
[*]reboot your computer.
[/list]
i got the solution from the comments of this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/442463").

solution

---

