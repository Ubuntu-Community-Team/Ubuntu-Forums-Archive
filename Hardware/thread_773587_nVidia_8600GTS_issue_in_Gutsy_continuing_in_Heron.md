---
title: "nVidia 8600GTS issue in Gutsy continuing in Heron"
date: 2008-04-29
forum: Hardware
---

### Post by netsurfau on 2008-04-29
This has been an "on & off" issue for a few months.

Note: There are no OS generated errors displayed at any point.

When I first boot my system each morning the following happens.

1. Once Ubuntu start loading, LCD monitor reports "No Signal".
2. Signal returns when Log-in screen appears.
3. After logging in, I can only see 1/16th (or less) of my desktop.
4. By moving the curser, I navigate to the top right corner of D/top and click on the "Log-off..." icon & select reboot.
5. Sys reboots showing the "No Signal" report and brings me back to the Log-in screen.
6. After logging in, the screen goes blank for 1-2 seconds then re-appears showing the whole D/top as it should.

* This morning I didn't have to reboot and hadn't changed any settings.

I have to go through this process in both Gutsy & now Heron.
At one point the nVidia Splash Screen was appearing and D/top would open without the need to reboot.
In Gutsy I was running a resolution of 1600x1200 but, since upgrading to Heron, I can only run a maximum resolution of 1280x1024 as I was getting an "Out of Range" error from monitor. The change in resolution has made no difference to my main issue.

System Specs:
AMD AM2 6000+
4GB RAM
500GB HDD
Gigabyte GA-M57SLI-S4 M/board with nVidia chipset
ASUS VW192s LCD Widesceen Monitor

---

### Post by chewearn on 2008-04-29
See this page for your boot-up display problem:
[http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html](http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html)

---

### Post by netsurfau on 2008-04-30
Thanks for the info AstalaVista,

With Gutsy, I was able to run 1600x1200 so, cannot understand why now (with the upgrade to Heron), I'm not able to use that resolution anymore.  The monitor has no trouble running it, in fact it's designed to run higher resolutions.  
Do you have any ideas where to look for the cause of the change?

---

### Post by chewearn on 2008-04-30
This is my guess, but I could be wrong :smile:

With Hardy, they upgrade to Xorg 7.3, which unfortunately is "less working" with nvidia driver (probably because it's new).  The whole problem with nvidia binary blob driver is no one can see the consequence of the changes, except nvidia.

So, we now have the automatic screen detections in hardy, but is some cases are messing up when dealing with nvidia.  Fortunately, the existing xorg.conf parameters have not been removed.  I mean, by default, everything is automatic, but you can still add the old manual parameters and they will be recognised.

Therefore, nvidia-settings should still work the same; you just have to manual install it.

At the moment, I'm advising everyone using nvidia restricted driver to change customize via nvidia-settings; ignore the ubuntu "Screen Resolution" utility.

---

### Post by netsurfau on 2008-05-04
After switching _off_ the proprietary nVidia driver and rebooting I'm now able to run 1600x1024.

So, then I tried updating the sys driver to "glx-new". I rebooted and ended up with the "Using Low Resolution" warning.  Tried to manually set up the screen & video card settings and couldn't get a resolution above 800x600. When I checked the error logs, there was a message saying that, the conflict was caused by, the kernel using driver version 100.14.19 and the installed driver (ie; glx-new) was version 169.12+2.6.24.12-16.34

I went back to using the default system driver which let me go back to 1600x1024.  All seemed good until I tried to run Google Earth.  It now wont run because it cannot detect what video card I'm using (Argh).  Haven't found any other applications having an issue (yet).

With Hardy being a "LTS" release, upgrading drivers etc. shouldn't cause these type of issues (IMO).  A friend who's a "devoted" Ubuntu user, has been having heaps of issues upgrading to Hardy - I thought it was supposed to be a "stable" release that shouldn't cause these kind of issues.

---

### Post by chewearn on 2008-05-04
Which system log are you referring to?  Is it /var/log/Xorg.0.log?  Can you post the exact error message?

Did you upgrade gutsy to hardy, or did you create a fresh install?  It could be the nvidia driver set-up has fubar during the upgrade.  If that's the case, I am out of my league.  But, a purge of all nvidia driver might be inorder.  Uninstall all nvidia driver and remove the configuration using synaptic package manager (select the purge settings option).

Side note:
The problem is with nvidia binary driver.  The Xorg developers don't have the source codes, they can't know the implications of their changes.  With Hardy using Xorg version 7.3, we have to wait for nvidia developers to get around fixing compatibility issues.  Judging by the fiasco they create with Vista driver, I would count on them to do this soon.

As a normal user, I understand the frustration when things don't work right.  A few hours ago, I myself upgraded to Hardy on my main desktop, it took an hour wrestling with the nvidia driver to get it to work right.  I'm not sure if my observations will help you, but you can find my chronicle here (shameless plug :lol:):
[http://ubuntuforums.org/showthread.php?t=780131](http://ubuntuforums.org/showthread.php?t=780131)

Definitely, there is a misunderstanding about the aim of LTS release.  This does not mean more stable than non-LTS.  It simply means longer support available.  As a consequence of that, the LTS version has to (sometime) make risky choices on the software version they put in.  A case to point (and a major contention here in the forum) is inclusion of Firefox 3 beta.  On one hand, putting beta in is a risk (potentially less stable).  On the other hand, due to the long support period, Firefox 2 would certainly has been obsolete.  This was a problem with Firefox 1.5 in Dapper, and there was complaint on why Firefox 2 was not rolled out.

---

### Post by netsurfau on 2008-05-04
*> **AstalaVista said:**
> Which system log are you referring to?  Is it /var/log/Xorg.0.log?  Can you post the exact error message?*

I just clicked on the link System/Administration/System Log.  From memory, it was in either "messages" or, "syslog".  Unfortunately, the error message isn't showing it the logs anymore but, I'm sure I got the main "thrust" of what it said, ie; differences in the kernel & installed driver versions.

*Did you upgrade gutsy to hardy, or did you create a fresh install?  It could be the nvidia driver set-up has fubar during the upgrade.  If that's the case, I am out of my league.  But, a purge of all nvidia driver might be inorder.  Uninstall all nvidia driver and remove the configuration using synaptic package manager (select the purge settings option).*

Performed an upgrade using the "Alternate" CD image. Biggest problem I had was: It wouldn't/couldn't recognise which version of Ubuntu I was running & I ended up having to install ubuntu-desktop the Synaptic to run the upgrade.

[I]Side note:
The problem is with nvidia binary driver.  The Xorg developers don't have the source codes, they can't know the implications of their changes.  With Hardy using Xorg version 7.3, we have to wait for nvidia developers to get around fixing compatibility issues.  Judging by the fiasco they create with Vista driver, I would count on them to do this soon.[/I]

I'm not. nVidia work to their own schedule which doesn't seem to match up with any user's needs - OS wise.

[I]As a normal user, I understand the frustration when things don't work right.  A few hours ago, I myself upgraded to Hardy on my main desktop, it took an hour wrestling with the nvidia driver to get it to work right.  I'm not sure if my observations will help you, but you can find my chronicle here (shameless plug :lol:):
[http://ubuntuforums.org/showthread.php?t=780131](http://ubuntuforums.org/showthread.php?t=780131)[/I]

Will check what you wrote later tonight.

*Definitely, there is a misunderstanding about the aim of LTS release.  This does not mean more stable than non-LTS.  It simply means longer support available.  As a consequence of that, the LTS version has to (sometime) make risky choices on the software version they put in.  A case to point (and a major contention here in the forum) is inclusion of Firefox 3 beta.  On one hand, putting beta in is a risk (potentially less stable).  On the other hand, due to the long support period, Firefox 2 would certainly has been obsolete.  This was a problem with Firefox 1.5 in Dapper, and there was complaint on why Firefox 2 was not rolled out.*

Add me to the many who missunderstand - D'oh (to quote Homer, who I'm matching for intelligence on this one HAH)

---

