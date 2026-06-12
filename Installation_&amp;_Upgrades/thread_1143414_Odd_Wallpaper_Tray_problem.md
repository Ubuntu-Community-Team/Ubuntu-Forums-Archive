---
title: "Odd Wallpaper Tray problem"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by ShiftyEyes on 2009-04-29
I think this problem is different from all the others I've seen posted. After installing 9.04 and finding the new wallpaper tray panel app, everything is working well except that the panel app is looking in directories that I did not specify. It even tries to display old files that are no longer there, and so it shows a blank screen. This indicates that some cache of file paths survived through my upgrade and the app is now stuck looking for those files. I'm pretty sure the solution would be to find that file and delete it, but I'm fairly new to Ubuntu and I'm not sure how to do that. Any suggestions?

EDIT: It does seem to be accepting other configuration changes (like changing from centered to wallpaper mode). I did a search for wp_tray and looked through all the files it found on my system, but none of them appeared to have a path or file-list stored in them. Configuration editor shows the correct directory path (the one that it appears to be ignoring), so no luck there. I think I've run out of things to try at this point, so any help would be greatly appreciated.

EDIT 2: I created a testing account and checked how it worked there. There were no problems, so I am now completely sure it's a problem with a configuration file somewhere in my home directory (because that is the only directory that was on its own partition when I did the new install). The only problem is that there are a ton of configuration files and folders, and none of them are named wp_tray. So... it appears that Wallpaper Tray is getting that directory list from some file in there, and I'm not sure how to figure out which one.

---

### Post by Nessie7 on 2009-05-06
Hi,
i'm having the same problem and found a bugreport:
[https://bugs.launchpad.net/ubuntu/+source/wallpaper-tray/+bug/355081](https://bugs.launchpad.net/ubuntu/+source/wallpaper-tray/+bug/355081)

---

