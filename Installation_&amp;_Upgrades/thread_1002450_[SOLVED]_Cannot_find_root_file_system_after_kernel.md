---
title: "[SOLVED] Cannot find root file system after kernel upgrade (?)"
date: 2008-12-05
forum: Installation &amp; Upgrades
---

### Post by callosum on 2008-12-05
Hi there,

I ran [FONT="Courier New"]sudo apt-get upgrade[/FONT] today and I *think* one of the things it did was install a new kernel ([FONT="Courier New"]8.04.1 kernel 2.6.24-19-generic[/FONT]).  After rebooting, the root file system couldn't be detected anymore.

If I try to use the newest kernel, it waits for a long time at [FONT="Courier New"]Waiting for root file system[/FONT] and then, it winds up with an [FONT="Courier New"]initramfs [/FONT]prompt.

I then tried logging in recovery mode for the newest kernel, and got this instead:
[FONT="Courier New"]
Waiting for root file system...
Clocksource tsc unstable ...
Time: hpet clocksource has been installed
Gave up waiting for root device
...
ALERT! /dev/disk/by-uuid/... does not exist!  Dropping to a shell!
[/FONT]
and then I get the [FONT="Courier New"]initramfs [/FONT]prompt.

I then thought I could get around this by going back to an older kernel (which has been working fine all the while).  I then got:
[FONT="Courier New"]
Failed to start X server
Fatal server error
...
AddScreen/ScreenInit failed for driver 0
[/FONT]
Eventually I managed to get a prompt using the recovery mode of an older kernel, but no X.

I googled for a few solutions including here at ubuntuforums, but none of them have changed anything so far.  I've tried:
[LIST]
[*]Adding [FONT="Courier New"]rootdelay=90[/FONT] to the kernel line.  Didn't help - in any case, most people for whom this worked seemed to be able to get in eventually after letting the boot process take its time, which didn't happen for me.
[*]Adding [FONT="Courier New"]all_generic_ide[/FONT] to the kernel line.  Again didn't help.
[*]Running [FONT="Courier New"]sudo update-initramfs[/FONT] when I managed to get a prompt.  I got the message: [FONT="Courier New"]cp: cannot stat '/lib/udeev/hotplug.function'[/FONT].  I think it did finish executing and this was just an error message.  Nevertheless, nothing changed.
[*]Cross-checking the UUID of / in the kernel line against what's in [FONT="Courier New"]/etc/fstab[/FONT].  It's the same.
[*]Upgrading to Intrepid Ibex.  When I tried selecting manual partition so I could keep the partitions the same, again it failed telling me it couldn't find a root file partition.  I stopped there as I didn't want to overwrite any existing partitions.
[/LIST]

If anyone has any more suggestions I'll be happy to hear them.  I'm running a Fujitsu Lifebook S Series if that's relevant.  I can also provide more diagnostic material if you tell me where to find it.  Thanks!!

---

### Post by utnubuuser on 2008-12-05
Have you tried re-installing the x-server?

> sudo apt-get install xserver-common
or  >  sudo apt-get install xserver-xorg-core
this is what synaptic says about the xorg core
> Xorg X server - core server
The Xorg X server is an X server for several architectures and operating
systems, which is derived from the XFree86 4.x series of X servers.

The Xorg server supports most modern graphics hardware from most vendors,
and supersedes all XFree86 X servers.

The Xorg server either needs fonts installed on the local host, or needs to
know of a remote hosts that provides font services (with xfs, for instance).
The former means that fonts packages are mandatory. The latter means that
font packages may be gratuitous. To err on the side of caution, install at
least the xfonts-base, xfonts-100dpi or xfonts-75dpi, and xfonts-scalable
packages.

More information about X.Org can be found at:
<URL:http://www.X.org>
<URL:http://xorg.freedesktop.org>
<URL:http://lists.freedesktop.org/mailman/listinfo/xorg>

This package is built from the X.org xserver module.


This is just a suggestion,  I've not tried this myself.

and if you end up going that route, you'll probably have to > sudo dpkg-reconfigure xserver-xorg afterwards

again, just a suggestion...  you might want to wait for someone more knowledgeable to respond

---

### Post by callosum on 2008-12-05
Hi utnubuuser,

Thanks for the suggestion.  I tried that using an earlier kernel.  Unfortunately it didn't seem to change things much - I still can't launch X on the old kernel.

In any case, it looks like the failure to locate the root file system seems to be the main issue.  I'm wondering if there's a way to get rid of the newest kernel and revert to the way things were, but I'm not finding anything about that right now.

Thanks a bunch!

---

### Post by callosum on 2008-12-05
Well, in the end I decided to just reformat the / partition and do a clean install of Intrepid Ibex, and it seems to work.  So I've bypassed the problem.  Thanks all.

---

### Post by utnubuuser on 2008-12-05
Callosum -- did you install with a seperate /home partition?
And if this is taken care of solved or otherwise, remember to mark the thread as solved.

---

### Post by littlebat on 2008-12-05
upgrade and dist-upgrade problems are bothering me too.
Here are my two questions, one is I get the "segment fault" after "dist-upgrade": "Segmentation fault" after "apt-get dist-upgrade" for Hardy [http://ubuntuforums.org/showthread.php?t=979639](http://ubuntuforums.org/showthread.php?t=979639)
One is I don't know the system how to keep the grub menu.lst options when the system installed initially: How does "dist-upgrade" find the intial grub menu.lst options? [http://ubuntuforums.org/showthread.php?t=1000663](http://ubuntuforums.org/showthread.php?t=1000663)

I am unwilling to bypass these questions now, so I have been stoped by the question about three weeks(the first question). Maybe, bypass these questions is a good idea for me. After some days, when I review these questions, the question will isn't a question.

---

### Post by callosum on 2008-12-06
utnubuuser - Yes, I did install with a separate /home partition, so all my data is thankfully intact.  I'll mark the thread [SOLVED], since littlebat's problem seems to be different from mine.  Thanks again.

---

