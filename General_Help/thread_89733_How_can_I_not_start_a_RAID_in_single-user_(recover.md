---
title: "How can I *not* start a RAID in single-user (recovery) mode?"
date: 2005-11-13
forum: General Help
---

### Post by Vortacist on 2005-11-13
My question: How can I **not** start a RAID in single-user mode?
...or, *Who's Been Starting My RAID?*

I just installed 5.10 and was able to get it working successfully with a software RAID that I had created in another machine.  Ubuntu now starts the RAID up and shuts it down automatically, cleanly.

Great, except that I **don't** want the RAID to start up when I boot into single-user (recovery) mode...in case at some point I do need to troubleshoot the RAID.

I figured that the script responsible for starting up the raid was /etc/init.d/mdadm-raid.  By default, that script is symlinked from rcS.d (as S40mdadm-raid).  According to the README file in /etc/rcS.d, those scripts are run both for single-user and multi-user mode.  Since I only wanted the RAID to start in multi-user mode, I moved this symlink to /etc/rc2.d .

Unfortunately, the RAID still started up even when booting into single-user mode.  I then removed that S40mdadm-raid symlink from /etc entirely...and the RAID *still* starts in single-user mode (and in multi-user mode, for that matter.)

Note: I have not touched the S50mdadm-raid symlinks residing in rc0.d or rc6.d , since I am afraid of shutting the RAID down uncleanly on a halt or reboot. (Since it's being started whether I like it or not, I want to make sure it goes down cleanly, assuming mdadm-raid has anything to do with it at all.)

I am mystified.  Anybody have any idea what is really starting my RAID and how I can get it **not** to start the RAID in single-user mode?

Thanks for your help!

---

### Post by poptones on 2005-11-13
Just mdadm -S /dev/mdX and shut it down

Do man mdadm for instructions on doing more

---

### Post by Vortacist on 2005-11-13
[QUOTE=poptones]Just mdadm -S /dev/mdX and shut it down[/QUOTE]

Thanks, but the issue is: how do I boot the machine without ever starting the RAID at all? If I think something is wrong with the RAID, I would much rather not attempt to start it on boot.

---

### Post by Joe_lurker on 2005-11-13
There is a program called rcconf in the universe.  Install that program and run it as sudo.  This will allow you to remove programs from the startup.

-Joe

---

### Post by poptones on 2005-11-13
FWIW, If something unrecoverable is wrong with the raid it *ain't going to start*.

---

### Post by Vortacist on 2005-11-13
[QUOTE=poptones]FWIW, If something unrecoverable is wrong with the raid it *ain't going to start*.[/QUOTE]

That's a good point.  But consider what happened to the last computer I had this RAID in: just trying to start the RAID caused my system to completely lock up.  Being able to boot the machine without starting the RAID would have allowed me to continue to use the machine at least in some capacity and maybe do better troubleshooting.  The RAID itself was fine, as evidenced by the fact that it's now thriving in another machine - I believe that particular problem was a motherboard issue.  

However, I think this experience shows that are definitely times when it's useful not to have the system even try to start a RAID.

---

### Post by Vortacist on 2005-11-13
[QUOTE=Joe_lurker]There is a program called rcconf in the universe.  Install that program and run it as sudo.  This will allow you to remove programs from the startup.
[/QUOTE]

That's a neat little program. Unfortunately, it doesn't solve my problem: rcconf uses what's already in the rc.d directories to determine what it can turn on and off. I've already removed the mdadm-raid symlink, so mdadm-raid doesn't appear in the list of services that rcconf can control.  So my RAID is still being started on bootup whether I like it or not. :P 

Thanks for the tip, though!

---

### Post by slade_slater on 2005-11-15
Try this:

sudo update-rc.d -f mdadm-raid remove

---

### Post by Vortacist on 2005-11-16
[QUOTE=slade_slater]Try this:

sudo update-rc.d -f mdadm-raid remove[/QUOTE]

I just now tried this and rebooted my machine, and the RAID still started up. Thanks, though!

**The results of all of these experiments would lead me to conclude that mdadm-raid has absolutely nothing to do with starting RAIDs on bootup in Ubuntu.**  Anyone have any ideas about what does?

---

