---
title: "Linux can be weird sometimes!"
date: 2014-10-04
forum: Hardware
---

### Post by santosh83 on 2014-10-04
Hello all,

This weird little problem illustrates how a seemingly "minor" change can cause severe issues in a completely different place!

I've been a long-time user of Ubuntu Linux (since Dapper Drake days), and after enduring "no support" notices on 13.10 for a few months, I decided to do a clean install of 14.04.1 LTS (x64). For the first time I chose vanilla Ubuntu, just to acquaint myself with Unity and to see what was all the fuss about.

In any case install went flawlessly. My system is a pretty old one. It's an Intel Pentium Dual Core E2140 and MSI G41M-P33 combo based setup with AMD "Sapphire" HD 6670 graphics card, and an old 40Gb IDE drive. I dedicated the whole drive to Ubuntu, but nevertheless did manual partitioning, since the automatic method seems to create a small (~250Mb) /boot partition, which I dislike. The system seemed to work very well after install.

Here comes the problem. I've never been a fan of looking at boot time "splash" screens. I like seeing the actual boot messages instead. So one of the first things I do after every install is to comment out the line in grub configuration file which says "quiet splash". This never gave me any problems before. So I did the same again. Edited **/etc/default/grub** through sudo, *commented out* (not edited or deleted) the line saying:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

and invoked **update-grub**. And rebooted. As expected, the silly splash screen was gone and everything seemed to go normally until I hit the graphical login screen. The mouse froze. Nothing could make it move. Nevertheless for the life of me, I didn't initially make the connection between this problem and editing the grub configuration. Naturally I assumed it was a mouse driver issue (my mouse is an old Logitech optical mouse), or an X or graphics card based issue. Like everyone else in the Linux community, I was aware that proprietary AMD and Nvidia drivers can cause various strange problems. So that was the first thing I checked and found that the system was using X.org based open-source drivers. I searched long and hard online. Apparently 14.04 LTS seems to be causing a significant number of mouse/trackpad freezes for a lot of folk. I tried many of the online suggestions like fiddling with gsettings.org environment variables, using modprobe to reload the mouse driver, switching to the proprietary fglrx driver, and even physically removing my graphics card! Nothing made the problem go away. And there were no concrete solutions online. No bug reports and expected fixes.

Finally in desperation I thought the mouse itself must have died and tried the LiveCD to check, and lo and behold, mouse worked fine! A lot of vague online comments seemed to implicate Unity, and since I still couldn't get the mouse to move, and I still hadn't figured out the REAL culprit (disabling the splash screen through editing **/etc/default/grub**), I decided it was likely to be Unity and wiped everything and installed Xubuntu 14.04.1 LTS (x64).

Again everything seemed to work fine. Until I disabled the splash screen again, with the same effect. Mouse never moving. But this time the connection didn't escape me. So I checked and rechecked by commenting in and commenting out that line in **/etc/default/grub** several times. Without fail, every time the GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" line was commented out, mouse would freeze. Obviously the notorious plymouth is doing something naughty here. But I still wanted the splash screen gone, so I edited that line to remove quiet and splash, and give:

```
GRUB_CMDLINE_LINUX_DEFAULT=""
```

And now mouse works.

I've no idea (not being a software person) what actually is happening behind the scenes to cause this funny but hard to trace problem, but it happens in a repeatable manner, at least on this machine and software combination.

I just wanted to put out this post to help others who may face the same issue. If your mouse doesn't seem to work after a fresh install on 14.04 LTS try remembering if you edited the grub configuration file (as explained above) and if you did, either undo the edit and re-enable the splash screen or edit it the way I did above, and see. If mouse starts working again, that might save you additional hours of frustration!

By the way, can anyone suggest where exactly I should file a bug report on this problem? I think the site is Launchpad bug tracker, if I'm not wrong? But against which package should I file? Grub? Plymouth? Something else?

Thanks.

---

### Post by TheFu on 2014-10-04
So - excellent post - might be nice to add this to the top:

"**Not existing** and **being empty** are very different things when it comes to software.
GRUB_CMDLINE_LINUX_DEFAULT must exist or bad things happen."

That isn't surprising to me. Sure, it would be nice if grub handled this nicer. I doubt this is an Ubuntu-only issue.

Again - good post.

BTW - other OSes don't let you control this stuff with as many options, if at all. With great power, comes great responsibility. ;)

---

### Post by Bucky Ball on 2014-10-04
> **TheFu said:**
> 
GRUB_CMDLINE_LINUX_DEFAULT must exist or bad things happen.



^^^
This. Thanks for sharing. While it's a pain, it's not a bug, rather a hinderance, and I would avoid creating a bug report. Making your feelings known to the grub devs would be an idea, though, if you are so inclined. Good luck.

---

