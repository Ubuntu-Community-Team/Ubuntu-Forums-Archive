---
title: "Suspend/hibernate not working"
date: 2009-03-07
forum: Hardware
---

### Post by Chibone on 2009-03-07
Hi all,

I've got a suspend/hibernate problem with my Compaq F767NR laptop, running 64-bit Intrepid Ibex (due to having 4gb memory), kernel 2.6.27-13-generic.

When I go to suspend my laptop, it looks like it suspends fine. However, when I attempt to resume, the screen remains black and pressing keys does nothing.  The only way I can get out is to reboot.  I've searched on the forums for any info on my laptop model and apparently power management works great but I haven't been able to get it to work personally.

Any help on this is much appreciated.

---

### Post by linux_tech on 2009-03-07
If you want to conserve power there are some useful tools here
[http://www.lesswatts.org/downloads/](http://www.lesswatts.org/downloads/)

---

### Post by bluegene on 2009-03-07
I've got exactly the same problem about suspend/hibernate issues. I think it may take some time for ubuntu developers hardware vendors alike to provide complete support for suspend/hibernate features. We'll just hope Jaunty Jackalope helps resolve the problem for most of us :).

---

### Post by Chibone on 2009-03-07
Thanks for the LessWatts link linux_tech ... very useful.

Does suspend work with a LiveCD?  I might check and see if it works in Jaunty if that's the case :)  April isn't too long to wait.

---

### Post by kidux on 2009-03-07
> **bluegene said:**
> I've got exactly the same problem about suspend/hibernate issues. I think it may take some time for ubuntu developers hardware vendors alike to provide complete support for suspend/hibernate features. We'll just hope Jaunty Jackalope helps resolve the problem for most of us :).
I have the same issue, but I think it's a problem with Intrepid. I never experienced the lockups with Hardy, so I think there's a coding error in the current release. I'm hoping they are able to figure it out in Jaunty.

---

### Post by khamil8686 on 2009-03-08
i had a problem where i would suspend my system, come back and hit the power button, it would start up and then when i would finish and enter my password the desktop wallpaper would show, soon go black or it would just start up with a bunch of weird lines on the screen, but it would just hang, sometimes the mouse would move, other times not, was weird. i did some googling and found a post which said to disable visual effects
i have ubuntu 8.10 and goto system>preferences>appearance, click the visual effects tab and then i clicked the radio button next to none, then had no problem with the black screen when resuming, another thing that many people said worked for their particular machine was edit /etc/default/acpi-support and change POST_VIDEO to false, anyways hope this helps out :) i started using ubuntu within a few weeks ago and i had a hard time with this prob so i decided to help out in whatever small way i could :) another thread reply i found was to use Conpiz Config, goto general options>display settings and disable Sync to VBlank

---

### Post by Chibone on 2009-03-11
Funnily enough, all my settings are actually set like you described.  I set them while in the process of getting my laptop to support sleep and hibernate.

Just for the record, still doesn't work after those changes. :)

---

### Post by HDTimeshifter on 2009-03-11
My PC wouldn't hibernate most of the time, but after rebooting a couple of days ago, goes into hibernation after inactivity, but won't wake up.  Keyboard keypress and mouse move don't wake it, and power-on button acts like it does - the blinking power light stops blinking and the HD light starts flashing, but the monitor won't wake, and the only thing that works is to reboot.

---

### Post by lalawawa on 2009-03-15
I've got the same problem.  When I was on 7.04 (Fiesty Fawn) it would suspend and resume properly, except it would only suspend one cycle -- after you suspended it, you had to reboot to be able to suspend again.  I upgraded to 8.04, and then it got worse instead of better.  If you suspended the machine would not wake up without being rebooted.  I upgraded to 8.10, but the problem remains.  Would appreciate help.

---

### Post by FiReSTaRT on 2009-03-15
That has to do with the NVidia driver. It worked flawlessly for me for a time, while running Hardy. Then it crapped out on me and an upgrade to Intrepid didn't help. I've tried every possible solution offered (other than sacrificing goats and/or virgins), without any success. Same story for streaming HDMI sound (with some ALSA/Pulse issues) So the way I see it is:
1) Either compile the new NVidia driver
or
2) Wait until Jaunty comes out and hope that the supplied driver will work as it should
I'll probably try booting from the live Alpha 5 CD just to see how it works.

---

### Post by HDTimeshifter on 2009-03-15
> **FiReSTaRT said:**
> That has to do with the NVidia driver. It worked flawlessly for me for a time, while running Hardy. Then it crapped out on me and an upgrade to Intrepid didn't help. I've tried every possible solution offered (other than sacrificing goats and/or virgins), without any success. Same story for streaming HDMI sound (with some ALSA/Pulse issues) So the way I see it is:
1) Either compile the new NVidia driver
or
2) Wait until Jaunty comes out and hope that the supplied driver will work as it should
I'll probably try booting from the live Alpha 5 CD just to see how it works.

I kind of figured it was the nVidia driver since it acted like it was waking up, but the monitor kept saying "no signal".  After several reboots, it came up in low resolution and I wasn't able to reset to high resolution through the System/Administration/nVidia X Server Settings menu.  I fixed it by copying a backup version of the config file over the current file:  [http://ubuntuforums.org/showthread.php?t=1094906]("http://ubuntuforums.org/showthread.php?t=1094906")

It now powers up when I press the power button.  :)
Btw, I'm running Ubuntu 8.10, nVidia GeForce 9500GT.  Another thing I noticed when it wasn't working was that my keyboard lights were off in hibernation (Fn & Num_lock lights on my MS 4000 ergo keyboard), and now they (at least the Fn) light stays on.  That didn't seem to validate my theory about it being video driver-only related, however...

---

### Post by inspired on 2009-03-19
I have an HP Compaq nx7010.
I was not able to suspend or hibernate.
I fixed the suspect issue by disabling wireless beforehand. Just a matter of clicking the button on the front of my machine that turns on/off wireless (I think all laptops with Wifi have such a button). Suspect works fine after that. Previously it was look like it was suspending but would either hang with the powerlight on and require a hard reboot, or it might shutdown but then reboot as per normal afterwards. Usually it would just hang.
Perhaps doing this same step solves your suspend issue.
I am still trying to resolve the hibernate issue. :popcorn:

All the best,
Jonathan

---

### Post by lalawawa on 2009-08-08
I've still got the suspend problem I described before, when I was on 8.10.  It suspends just fine, but won't wake up without rebooting.

I read something about suspend problems may be due to lack of a swap partition.  I've upgraded to 9.04 and when doing so, specified a 3G swap partition (I've got 1G of RAM).  However, I don't see the swap partition when I do 'df':
> df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2            150886048  10991000 132230440   8% /
tmpfs                   448132         0    448132   0% /lib/init/rw
varrun                  448132       124    448008   1% /var/run
varlock                 448132         0    448132   0% /var/lock
udev                    448132       156    447976   1% /dev
tmpfs                   448132      4232    443900   1% /dev/shm
lrm                     448132      2192    445940   1% /lib/modules/2.6.28-14-generic/volatile
>
What happened to it?  How do I get a swap partition?

---

### Post by HDTimeshifter on 2009-08-08
My suspend problems went away somewhere around Ubuntu 8.11 on my main PC (ASUS P5Q Pro Intel P45 ATX Intel MB, ASUS EN9500GT GeForce 9500 GT nVidia video card).  One thing is I may have been too impatient and thought it wasn't resuming from hibernation when I got the blank screen with flashing cursor on upper left after pressing the power button and hit the reboot too soon.  If I waited a few seconds, it would wake up.  The problems with the nVidia video driver not recognizing the CRT brand on reboot is because I was rebooting with the monitor power off (to save power especially when I was rebooting and leaving the PC for a while to come back later).  This would happen even on successive reboots with monitor power off.  If I leave the monitor power on during the boot cycle, it will recognize the monitor brand (Gateway).  I'm now on Ubuntu 9.04 64-bit desktop version.

A couple of weeks ago, I reformatted my basement file server from Windows to Ubuntu 9.04 32-bit desktop version.  It is an Athlon with 512 MB memory and always reports "System power saving failed" in a dialog, but usually does go into hibernation.  Occasionally it does not - usually because of System Update (which I've set to download, but not install automatically).  Hibernation is important for this server as it runs hot and is in a wooden entertainment center with the only ventilation being an 8"h x 18"w cable hole in the bottom rear.  I occasionally leave one of the doors on the A/V cabinet to keep it cool, but that is somewhat obtrusive.

---

