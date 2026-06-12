---
title: "Ubuntu AMD64 8.10 DVD - Partitioner shows blank screen only in LiveCD"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by k_aneda on 2008-12-29
Anyone noticed this?

Just did a quick search on forums while doing an installation on the laptop tonight and found that in the LiveCD, the partitioner shows blank for the partition setup.

Boot from the CD and select the Installation option, works fine.

CD used is the AMD64 8.10 DVD ISO (not CD)

---

### Post by plarq on 2008-12-29
The same, and I'm posting under a live cd session without the ability to install.

---

### Post by k_aneda on 2008-12-29
> **plarq said:**
> The same, and I'm posting under a live cd session without the ability to install.

So you notice that if you reboot, then choose the Install instead of LiveCD option that you can proceed and install?

---

### Post by konsultor on 2008-12-29
Sounds like what I'm experienceing with U 8.10 (from a fresh ISO download) on a generic notebook (from eRacks) which had been using Linspire 6.  Just installed a new HD (140 GB) so I'm starting from scratch.  Have so far failed to install openSUSE as that install process failed.  Now trying Ubuntu, as the successor to Linspire.

[ASIDE:  the boot from the ISO disk hangs often;  pressing a key such as SHIFT or CTL seems to move it along sometimes, but the process seems VERY slow.  For example, at the moment the boot is stalled for several minutes.  Hitting SHIFT started it again.]

On a previous boot to the Live Ubuntu, I used gparted started from a terminal window to set up 3 partitions:  sda1 = ROOT (tagged Boot), sda2 = SWAP, and sda3 = HOME.  Formatted for EXT3.

[ASSIDE Cont'd:  by the time I typed the previous paragraph, the boot stopped again.]

The curretn boot is going into "install" (not Live) to test the suggestion above.  However, it is going very slowly;  currently appears hung but in the past the process has restared after I went a way for a while--watched pot boiling?

It's been >5 minutes, but a key press seems to have got it moving again.  Ah ha!  After almost a quarter-hour, we are at the partitioner--and it shows the previously configured partitions.

Unfortunately, the proposed changes would create a new partition for U.  What happened to my mountings?
 Can I use O Manual to preserve my partition scheme and get U installed on sda1???
Standing by for your reply.

Thanks,

---

### Post by konsultor on 2008-12-29
Pressing ahead, I found that the steps after selecting "Manual" in the partitioner allowed me to use the previous layout. 

So I'm proceeding.  No reply necessary at this time.

---

### Post by konsultor on 2008-12-29
The install completed, but only after many key presses to complete the last 3% on the progress bar.  

Rebooted, as required.  Now hung on the logo page with the progress bar at abut 25% (for 10 minutes). :(](*,)

---

### Post by Nitehunter on 2008-12-30
I am having similar issues here. After my installation completed and the desktop went to boot on its own it is hung on a blank tan screen. Mouse still moves but nothing has happened yet. Been 15+ minutes.... :confused:

---

### Post by konsultor on 2008-12-30
Hang in there.  Press a key now and then, particularly SHIFT and the SPACE bar.

My install finally completed--after two reboots.  Now downloading the 198 updates.

---

### Post by Nitehunter on 2008-12-30
My install is still not completed. (Still Waiting!):popcorn:

---

### Post by plarq on 2008-12-30
What?! Is the kernel wrong or unstable? I notice that the kernel number is odd not even, meaning it is not a stable version...

---

### Post by k_aneda on 2008-12-30
> **plarq said:**
> What?! Is the kernel wrong or unstable? I notice that the kernel number is odd not even, meaning it is not a stable version...

Not really related to this, however odd/even versioning for linux kernel counts for the major version (i.e. 2.5.x .vs. 2.6.x), not for the minor version (i.e. 2.6.21 .vs. 2.6.22).

---

### Post by k_aneda on 2008-12-30
> **konsultor said:**
> Sounds like what I'm experienceing with U 8.10 (from a fresh ISO download) on a generic notebook (from eRacks) which had been using Linspire 6.  Just installed a new HD (140 GB) so I'm starting from scratch.  Have so far failed to install openSUSE as that install process failed.  Now trying Ubuntu, as the successor to Linspire.

[ASIDE:  the boot from the ISO disk hangs often;  pressing a key such as SHIFT or CTL seems to move it along sometimes, but the process seems VERY slow.  For example, at the moment the boot is stalled for several minutes.  Hitting SHIFT started it again.]

On a previous boot to the Live Ubuntu, I used gparted started from a terminal window to set up 3 partitions:  sda1 = ROOT (tagged Boot), sda2 = SWAP, and sda3 = HOME.  Formatted for EXT3.

[ASSIDE Cont'd:  by the time I typed the previous paragraph, the boot stopped again.]

The curretn boot is going into "install" (not Live) to test the suggestion above.  However, it is going very slowly;  currently appears hung but in the past the process has restared after I went a way for a while--watched pot boiling?

It's been >5 minutes, but a key press seems to have got it moving again.  Ah ha!  After almost a quarter-hour, we are at the partitioner--and it shows the previously configured partitions.

Unfortunately, the proposed changes would create a new partition for U.  What happened to my mountings?
 Can I use O Manual to preserve my partition scheme and get U installed on sda1???
Standing by for your reply.

Thanks,

1) Slow LiveCD load - didn't have that problem here, or in VMware.  I'd look first at your hardware or trying the disc on another system to confirm if it really is that slow

2) Your issue definetly isn't what I'm seeing.

What I'm seeing is that if I boot into the LiveCD -- not the installation option -- during the setup process at the partition screen I cannot see any partitions what so ever, not even the suggested layout.

The installation process works only if I reboot, then select "Install from CD" as opposed to booting the Live CD.

To be honest; I haven't seen much on this elsewhere on the forum so I guess the only way forward is to really log a bug for this which I'll do this weekend after new years celebrations.

EDIT: Really, it's an easy workaround - don't try to install from within the Live CD.  So it's not really life-threatning-cant-install-ubuntu, so I doubt even the bug testers will give this a high priority..

---

### Post by plarq on 2008-12-30
I did an alternative CD and tried to install with Text based program, still stopped at the partition section---cannot run away from this. It just give me nothing about my HDD partitions.

---

