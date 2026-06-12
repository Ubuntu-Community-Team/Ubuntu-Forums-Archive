---
title: "Kubuntu hangs when loading hotplug subsystem"
date: 2005-11-28
forum: General Help
---

### Post by ErikTheRed on 2005-11-28
I recently reinstalled Kubuntu, and now it hangs on boot when it tries to load the hotplug subsystem. I'm running an ASUS Z71V Laptop. Kubuntu worked fine before, the only thing I've done since running it last was apply a BIOS update.

---

### Post by ErikTheRed on 2005-11-28
Doesn't anyone have any suggestions for me? This is happening right after a clean install, which strikes me as unusual.

---

### Post by Al_maverick on 2005-11-28
This happened to me also, just today. I shutdown my pc in the morning, and when I turned it on back from work, it hung when loading the hotplug subsystem. I resetted a couple of times and it went just fine. This happened at about 8pm GMT.
Anyway, it&#347; working fine now, I haven noticed anything unusual, other than having to restart twice in the first place (I use windows, so this is not at all unussual, but...)

---

### Post by tonysathre on 2005-11-28
when it hangs try hitting ctrl-c to kill it

---

### Post by carlos1 on 2005-11-28
Same thing happened to me today when I rebooted for the first time in a few days. 
I just restarted the boot process and it was fine.

---

### Post by ErikTheRed on 2005-11-29
I've rebooted a number of times with no success. I find it odd that this happens right after a fresh install too. Ctrl-C does nothing at this point. I'm stumped.

---

### Post by shanz on 2005-11-29
I have the same problem with a new Sony Vaio desktop with Windows XP and media center pre-installed. It stopped at "Starting hotplug subsystem ..."
any help??

---

### Post by tonysathre on 2005-11-29
have u tried disabling usb in the BIOS

---

### Post by leech on 2005-12-02
That's very interesting, I just had the exact same problem though I'm not running Kubuntu, BUT I did have the kubuntu-usplash theme, which I've tried to remove, actually, so it says Ubuntu again, but wasn't able to.  But just now, after being in windows for a while, I rebooted to Ubuntu and it indeed hung at loading the hotplug.  I fixed it by holding down the power (hence turning it off) then booting it back up and it worked.

Anyone now if Dapper is going to use the newer Udev so that hotplug is better integrated with it.  I know in debian sid, it is that way, in fact the new udev conflicts with Hotplug, and it boots up a LOT faster.  

Leech

---

### Post by thedstro on 2005-12-02
I had the same problem! In my case disabling the on-board sound through the BIOS setup fixed it and allowed me to boot. This is just a workaround of course! The solution could be replacing the sound driver (intel_snd_hda I think it was called in my case) or changing to udev instead of hotplug.

---

### Post by Cannedbread on 2005-12-11
aye, im installing it on an emt64 box, and disabling my integrated 8 channel audio fixed it :???:.

Oh, im not doing kubuntu though, just the regular kind. so this might not help you

---

### Post by tneto on 2005-12-20
I have  the same problem whith asus A6VA lap.

It is possible delete the file that starts this service...
someone tell me that that file is in /etc/init.d/
I will try to rename or delete this file and then post here the results

---

### Post by Heretic09 on 2005-12-21
I have the same issue, mine was due to the neomagic sound card that comes with my dell (Bug report: [https://bugzilla.ubuntu.com/show_bug.cgi?id=7939]("https://bugzilla.ubuntu.com/show_bug.cgi?id=7939") )

The kernel was patched for hoary that stops that driver from hanging hotplug but for some reason the developers neglected to patch the breezy kernel. I'm waiting for a kernel update with that patch or try to track down the patch they used so I can recompile the kernel myself.

EDIT: Seems that the newly released alsa 1.0.10 seems to have fixed it or at least has a better workaround:

> NM256 driver
    - Summary: nm256 - Fix PM and irq handling
      - Fixed the PCM resume - restoring the rate setting
      - Fixed the handling of buggy irqs
      - Dynamically acquire/release irq handler to make the driver more robust
        to unknown irq storms (as OSS driver does).
    - Summary: nm256: reset workaround for Latitude CSx
      The current snd-nm256 driver can cause Dell Latitude CSx laptops to
      lock-up during module (un)load.  I have isolated this to the writes to
      the control port register at offset 0x6cc which were not already
      protected by the existing reset_workaround.
      I tried grouping these writes with the existing reset_workaround
      clause, but that caused the driver to have (un)load problems on the
      Dell Latitude LS laptops.  So, I have implemented a reset_workaround_2
      clause (please feel free to suggest a better name!) to cover this
      situation and added a quirk entry for the CSx laptops.
      Signed-off-by: John W. Linville <linville@tuxdriver.com>

---

