---
title: "device descriptor read 64 error -32"
date: 2008-11-24
forum: Hardware
---

### Post by kc4mts on 2008-11-24
I have some usb storage that recently quit working on me under Ubuntu Version 8.04.
 I am currenty typing from the 8.04 (hardy heron) version of Ubuntu and this is the version that broke on me, I believe, after I loaded a bunch of games into the machine at one time and I have updated a couple of times so it is difficult to find out which program did the dirty deed. USB was working fine on this machine for a long time so I know it has to be something that I did that caused the USB to stop working.
 I also have Ubuntu 8.10 installed on another drive (dual boot) and the USB works fine with it using the same hardware.
 I know that this error... device descriptor read\64 error -32 or (-32 ,-71,-110) seems to have been around for some time.....is there a fix out for it (aside from doing a clean install)?

 I am temporarily taking care of the issue by doing...
sudo rmmod ehci_hcd
from the terminal and both my Maxtor one touch drive and an 8 gig memory card read fine and seem to write also.

*UPDATE* Mar 26 2009 5.54 am EST

I just got an update of the following files and "magically" my USB 2.0 started working again which usually means that one of them caused the device descriptor issue.

libjasper1_1.900.1-3ubuntu0.8.04.1_i386.deb
wesnoth_1%3a1.4-1ubuntu0.1_i386.deb
wesnoth-all_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-aoi_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-data_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-did_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-editor_1%3a1.4-1ubuntu0.1_i386.deb
wesnoth-ei_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-httt_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-l_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-music_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-nr_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-server_1%3a1.4-1ubuntu0.1_i386.deb
wesnoth-sof_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-sotbe_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-thot_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-trow_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-tsg_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-ttb_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-utbs_1%3a1.4-1ubuntu0.1_all.deb


 I know that libjasper is part of the jpeg library and westnoth is a game. I am betting that one of the westnoth updates is what corrected the issue.

---

### Post by soylent_green_is_hamster on 2009-01-27
Hi,

did you get anywhere with this problem?

I'm having what appears to be the same problem. I'm not actually an Ubuntu user, I'm on Arch, but I'm not getting any joy over there (and I seem to end up these forums over and over again when troubleshooting!)

I too have unloaded ehci_hcd, but that's hardly a solution.

Can anyone offer any insight into this "device descriptor read\64 error -32 or (-32 ,-71,-110)" problem?

any help appreciated :)

---

### Post by kc4mts on 2009-02-02
In answer to your first question, I have not gotten anywhere with a fix yet for the device descriptor read 64 error -32.

I can tell you this much.... The error did not originally occur on this 8.04 version of Ubuntu....I believe one of the programs (games) that I loaded into the system may have over written the kernel code with some older code (maybe). I still have not done anything to fix the problem on 8.04 Ubuntu, but I had a busted linux version on a second drive so I did a drive format ( complete clean of the drive) and loaded 8.10 Ubuntu onto it and it works flawlessly. One of these days I will try to load the games one at a time (instead of 30 or 40 :p) and see which one crashes the usb in 8.10. When I do I will post the results here and contact the authors of the offending software of a bug so that it can be fixed.

Alan

*UPDATE* Mar 26 2009 5.54 am EST

I just got an update of the following files and "magically" my USB 2.0 started working again which usually means that one of them caused the device descriptor issue.

libjasper1_1.900.1-3ubuntu0.8.04.1_i386.deb
wesnoth_1%3a1.4-1ubuntu0.1_i386.deb
wesnoth-all_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-aoi_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-data_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-did_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-editor_1%3a1.4-1ubuntu0.1_i386.deb
wesnoth-ei_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-httt_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-l_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-music_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-nr_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-server_1%3a1.4-1ubuntu0.1_i386.deb
wesnoth-sof_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-sotbe_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-thot_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-trow_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-tsg_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-ttb_1%3a1.4-1ubuntu0.1_all.deb
wesnoth-utbs_1%3a1.4-1ubuntu0.1_all.deb


I know that libjasper is part of the jpeg library and westnoth is a game. I am betting that one of the westnoth updates is what corrected the issue.

---

