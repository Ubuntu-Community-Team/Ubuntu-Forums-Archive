---
title: "Places - Home Folder opens in VLC U8.10Beta"
date: 2008-10-17
forum: General Help
---

### Post by adder1972 on 2008-10-17
Hi,

I apologize for up front for posting this in what I am sure you will tell me is the wrong category.

I just upgraded to U8.10 on my IBM Thinkpad X60 (from U8.04.1). When clicking Places - Home Folder (or any other), VLC opens and starts to play the files! 

I had VLC installed in U8.04.1 and now it seems to be upgraded and amok. If I uninstall VLC, Nautilus works normally.  When I reinstall VLC, the problem returns. If I start Nautilus from the command-line, then it starts normally.

I guess this is a VLC problem, but their site is actively designed in order to prevent feedback it seems.

Has anyone else experienced this problem? And do you know how to give a quick feedback to VLC?

Thanks.

S

---

### Post by plucky on 2008-10-17
> Has anyone else experienced this problem? And do you know how to give a quick feedback to VLC?




This is a known [bug](https://bugs.launchpad.net/nautilus/+bug/260492) and is not a VLC problem.On my system it opened Rhythmbox. 

See bug report or from a terminal,start nautilus. Navigate Up one level so you see your Home Folder.Right click on the folder and go to **properties**.Select "open with" tag and either add "File browser" or select "Open Folder " instead of VLC.


This thread should be in the [Ibex subforum](http://ubuntuforums.org/forumdisplay.php?f=346)


Good Luck

---

### Post by adder1972 on 2008-10-17
Thanks plucky!

---

