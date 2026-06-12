---
title: "Asus Eee PC hotkeys and ACPI"
date: 2009-11-05
forum: Hardware
---

### Post by marmida on 2009-11-05
I'm running an Eee PC 1005HA, and just upgraded to 9.10.  I've noticed the following problems, and it seems like there's a lot of conflicting reports, claiming everything from "perfect out-of-the-box functionality" to "everything sucks."  I see two specific problems for my model:

[list=1]
[*] power management / overclocking not available
[*] hotkeys (both fn keys and silver hotkeys) don't work
[/list]

There might be other problems with the bootup time, but I'm not so concerned about that.

These are both caused by a problem with the ACPI packages; I can't install eeepc-acpi-scripts, because it conflicts with acpi-support, which is recommended by ubuntu-netbook-remix.  I tried removing it before installing eeepc-acpi-scripts, but then I hit a dependency issue trying to find a non-virtual candidate for acpi-support-base.

Has anybody else hit this problem?  I tried dragging in the Jaunty statux.org packages that just recently got abandoned in frustration by the developer, and those did not work (duh - special kernel mods no longer needed, but the hooks for acpi don't work with the tools in karmic).  Is this an all-or-nothing, to roll back to Jaunty?

---

### Post by babooka on 2009-11-11
Try installing eee-control.

I did a fresh install of 9.10 on 1005ha w/o any issues. And all of the hotkeys work, except for the fn-space to swicth the performance mode.

To change the mode there is eee-control-tray applet that allows you to do that.

---

### Post by tars_ac on 2009-11-13
I have the same issues, and as far as I can tell there is no eee-control for 9.10.  The 9.04 version kind of installs (but actually fails with some sort of error).  Once I get the eee-control-daemon up and running, it sort of works, sometimes, but still has some serious issues.  Have you found a different eee-control other than the one from greg @ geekmind?

---

### Post by tars_ac on 2009-11-14
I've found the solution to my issue.  I did a complete fresh install of 9.10, upon which everything worked except the wifi toggle and the volume mute status after suspend/resume.  The wifi toggle was fixed when I upgraded kernels to 2.6.31-16~pre2-Ubuntu and apparently there's some script in pm-utils that is re-enabling the sound on resume (/usr/lib/pm-utils/sleep.d/01PulseAudio).  Commenting that out makes it work.

I recommend a fresh re-install, and then tackling the issues one by one.  Worked for me at least.

---

### Post by marmida on 2009-12-16
> **babooka said:**
> Try installing eee-control.

I did a fresh install of 9.10 on 1005ha w/o any issues. And all of the hotkeys work, except for the fn-space to swicth the performance mode.

Just tried this again; nothing appears to have changed.  There is no eee-control package in the 9.10 distrib; are you adding something from a PPA?

Launchpad link:  eeepc_acpi_scripts acknowledged to be useless; should not be necessary under 9.10 with eeepc_laptop kernel mod (but still doesn't work): [https://bugs.launchpad.net/ubuntu/+source/eeepc-acpi-scripts/+bug/356335](https://bugs.launchpad.net/ubuntu/+source/eeepc-acpi-scripts/+bug/356335)

What we need is somebody to confirm that with only the eeepc_laptop kernel mod, they have all the hotkeys working, and/or whatever hoops they had to jump to get the hotkeys working.

edit: additional thought: [https://bugs.launchpad.net/ubuntu/+source/eeepc-acpi-scripts/+bug/356335/comments/6](https://bugs.launchpad.net/ubuntu/+source/eeepc-acpi-scripts/+bug/356335/comments/6) mentions running hotkey-setup; but there's also no version for 9.10 (see [https://launchpad.net/ubuntu/+source/hotkey-setup](https://launchpad.net/ubuntu/+source/hotkey-setup)).  I'm guessing even if the kernel support does exist for all the keys, the default install doesn't give gnome a way to use the hotkeys.

---

### Post by fewt on 2009-12-17
> **marmida said:**
> Just tried this again; nothing appears to have changed.  There is no eee-control package in the 9.10 distrib; are you adding something from a PPA?

Launchpad link:  eeepc_acpi_scripts acknowledged to be useless; should not be necessary under 9.10 with eeepc_laptop kernel mod (but still doesn't work): [https://bugs.launchpad.net/ubuntu/+source/eeepc-acpi-scripts/+bug/356335](https://bugs.launchpad.net/ubuntu/+source/eeepc-acpi-scripts/+bug/356335)

What we need is somebody to confirm that with only the eeepc_laptop kernel mod, they have all the hotkeys working, and/or whatever hoops they had to jump to get the hotkeys working.

edit: additional thought: [https://bugs.launchpad.net/ubuntu/+source/eeepc-acpi-scripts/+bug/356335/comments/6](https://bugs.launchpad.net/ubuntu/+source/eeepc-acpi-scripts/+bug/356335/comments/6) mentions running hotkey-setup; but there's also no version for 9.10 (see [https://launchpad.net/ubuntu/+source/hotkey-setup](https://launchpad.net/ubuntu/+source/hotkey-setup)).  I'm guessing even if the kernel support does exist for all the keys, the default install doesn't give gnome a way to use the hotkeys.

All of my hotkeys work.  Wait, I don't use Karmic.

Get a better distro. ;)

With only the eeepc_laptop kernel mod your silver keys will work, and trigger events will be sent to the OS.  If there is nothing there to intercept them, then it won't do anything.

In some cases the key is processed within the kernel module though, like the intercept for FN-F2.  Unfortunately, eeepc_laptop also exposes an rfkill hook which in some cases can conflict with the WIFI driver which also exposes an rfkill hook.

---

### Post by tars_ac on 2009-12-22
I can confirm in Karmic that all of the hotkeys work with just the standard module, with the latest kernel (original Karmic kernel had a wifi issue).

Fewt has had some issues with working with the ubuntu devs fixing the eee pc to work with ubuntu.  I appreciate his efforts and I'm not surprised he's bitter.  But current karmic does work.  There are some conflicts that happen from an upgrade though, so try a fresh install.

---

### Post by shihkster1015 on 2010-05-01
anyone here try out lucid lynx??
nothing works properly on it
LL is fast, but then eeepc's support's minimal

---

### Post by abyssign on 2010-05-01
Hi, same issue with an Asus 1005 HA-H with Lucid. Nothing works, unlike what's written on the eeepc ubuntu how-to page.

Going back to Karmic

---

### Post by marvelty on 2010-05-02
I just installed Lucid today (switched over from eeebuntu) on a 1000HE.

Some of my hotkeys work; I haven't tried suspend/F1 but wifi/F2, brightness/F5&F6, switch screen/F8 and volume/F10-12 all work, as does lock screen/silver button 1. The remainder of the keys (F3,4,7,9 and silver keys 2-4) seem to have no effect. 

I haven't been able to install eee-control; even downloading the old package, it requires the hotkey-setup package which is not available. I did install Jupiter; though it doesn't fix the keys, it does restore some of the functionality I missed from eeebuntu and seems to work fine (so far).

---

### Post by shihkster1015 on 2010-05-02
> **marvelty said:**
> I just installed Lucid today (switched over from eeebuntu) on a 1000HE.

Some of my hotkeys work; I haven't tried suspend/F1 but wifi/F2, brightness/F5&F6, switch screen/F8 and volume/F10-12 all work, as does lock screen/silver button 1. The remainder of the keys (F3,4,7,9 and silver keys 2-4) seem to have no effect. 

I haven't been able to install eee-control; even downloading the old package, it requires the hotkey-setup package which is not available. I did install Jupiter; though it doesn't fix the keys, it does restore some of the functionality I missed from eeebuntu and seems to work fine (so far).

I installed eee-control in 9.10 and now i'm trying to update to 10.04
i think this method might work!

---

### Post by shihkster1015 on 2010-05-02
WARNING DO NOT USE THE UPGRADE METHOD TO UPGRADE 9.10 to 10.04

it completely crashed my ubuntu

---

### Post by relva on 2010-05-02
On a 1008ha i've the same issue. 
All worked perfectly on UNR 9.10. 
I'm currently in a desperate mood to go back to 9.10 :x

---

### Post by MikaelHolber on 2010-05-02
Same here with a 1005HA. Only way to turn on and off wlan is via bios.

---

### Post by MikaelHolber on 2010-05-02
Check this out:

**[http://ubuntuforums.org/showthread.php?t=1466802&highlight=eeepc]("http://ubuntuforums.org/showthread.php?t=1466802&highlight=eeepc")**

Worked like a charm on my 1005HA.

---

### Post by shihkster1015 on 2010-05-03
@MikaelHolber 
Thanks for sharing the link, but it's too late D:

i switched back to 9.10

There is still a battery issue. I can get up to 9:55 hours in 9.10, but only 4:05 on 10.04
can't wait for 10.10 to come out :P
It seems to me that the October release's always a bit better.
You can really tell the difference between 8.04 and 8.10!!

---

