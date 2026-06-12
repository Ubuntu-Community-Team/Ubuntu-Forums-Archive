---
title: "Programs stop launching after a while..."
date: 2008-09-20
forum: General Help
---

### Post by bjtuna on 2008-09-20
My machine has become very unstable. After I've been using it for a few hours, some condition gets triggered that causes applications to no longer launch, and existing applications to no longer respond. For example, I can click the "shutdown" button in the top-right, but nothing will happen. Or I'll switch to an open application, and I'll just see the window border, nothing inside it. I can, however, move the mouse around.  Restarting X with ctrl-alt-backspace does not solve the problem; the system has to be hard-rebooted. 

I wasn't sure what forum category to post this in, and I find I'm not even 100% sure how to describe the problem, but I'm going to post it anyway because I'm pretty much at my wits' end. I've been diagnosing computers for years and I can't seem to figure this out.  

It is a homebuilt machine running Ubuntu 8.04 (Hardy) i386 desktop edition.  The machine itself is pretty simple:
- MSI socket 939 motherboard with an Athlon 64 at 1994mhz
- a couple of hard drives, one SATA and on UDMA
- 2GB of RAM (from Crucial.com)
- onboard ATI Radeon XPress200 video

Here's what I've tried, to no avail
- Wiped the OS clean and re-installed Hardy.
- Removed the Virtualbox OSE kernel module
- Disabled Compiz
- Tried both 'ati' and 'fglrx' X modules
- Ran Memtest86 for almost 24 hours, no errors reported
- Switched out the old CDROM drive for a new one (it was broken)

Here are the programs I typically have running:
- Firefox3 (w/ Firebug, Web Developer, and Delicious Bookmarks addons)
- Pidgin
- Thunderbird2

My /var/log/messages logs at time of incident look pretty clean, although I do notice a bunch of errors related to Pulseaudio (I don't have them handy at the moment).

The last time it happened, I made a note in System Monitor that I had reached 1.1gb of memory usage (zero swap in use). I am going to keep tracking the RAM usage at incident times, to see if there's a correlation, but the clean Memtest86 results make me think that it's probably not the RAM.

As far as I remember, I did not have any problems on this machine running Gutsy.  That isn't to say that the hardware hasn't gone haywire somehow, but if the hardware IS still okay, it suggests that Hardy introduced the condition.

Any ideas or feedback would be greatly appreciated.  I don't expect anyone to simply have an answer to this, since you're not in front of the machine, although a quick fix would of course be amazing :)  But, troubleshooting ideas and such would probably help me out a lot.  

I'm quickly approaching the point where I'm going to have spent enough otherwise-billable hours trying to fix this thing, where I could have just purchased new hardware :)

Thanks in advance!

-Brian

---

### Post by stickmangumby on 2008-09-20
Hi Brian,

I'm not too sure what to suggest, but I've experienced something similar with the shutdown button. This was in Hardy as well I think. After you hit shutdown, go and make a cup of coffee and come back 5 minutes later. When I thought it was hanging and needed to be hard-reset, it was actually just taking a very long time and not responding to any user actions.

I never did figure out what was causing this, but it might provide you with some more information. Post back here after you give it a try.

---

### Post by bjtuna on 2008-09-22
Okay, I will try and wait it out the next time it happens and will report back here with the results. Thanks!

> **stickmangumby said:**
> Hi Brian,

I'm not too sure what to suggest, but I've experienced something similar with the shutdown button. This was in Hardy as well I think. After you hit shutdown, go and make a cup of coffee and come back 5 minutes later. When I thought it was hanging and needed to be hard-reset, it was actually just taking a very long time and not responding to any user actions.

I never did figure out what was causing this, but it might provide you with some more information. Post back here after you give it a try.

---

### Post by stickmangumby on 2008-09-22
I've done a bit of a search, and it seems like shutdown being unresponsive is a known bug.

[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/123078](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/123078)

Apparently you just re-enable the gnome-power-manager in Administration-Sessions.

However, it might be that your problem is something else. Give that a go and see if it helps at all.

---

### Post by bjtuna on 2008-09-22
Okay, I may have narrowed it down.  The condition triggered today while I was trying to watch a Youtube video and noticed I had no sound. This seems consistent with the pulseaudio errors I saw in the logs and with the numerous flash/pulseaudio problems out there in Ubuntu-land.  So I did some research and found: [http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472) and followed the guide.  I will post back here after I've confirmed whether this has, or hasn't, fixed the issue.

---

