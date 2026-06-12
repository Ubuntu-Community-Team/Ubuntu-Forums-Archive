---
title: "Cannot use HDMI"
date: 2013-01-11
forum: Hardware
---

### Post by Trevorius on 2013-01-11
I'm just wondering if anyone has any suggestions on this issue. I'm trying to use my Dell Vostro 3750 with a new TV via HMDI cord. It works perfectly in Win 7, so the hardware itself is fine. 

My initial reaction was to ensure that proprietary drivers for the Nvidia GeForce GT 525M 1GB Graphics were installed- they weren't - so I embared on a 2 day long battle trying to install them assuming this would solve all my problems. I tried using Jockey, but the window which should show drivers to activate was blank. So I use Muon package manager to purge and reinstall all jockey and invidia driver related stuff. 

After that, the drivers showed in Jockey, but it said no proprietary drivers are in use in this system, and when I clicked the bottom driver in the list, it said "The driver is active but not in use" and it only gave me the "remove" button as an option. When I click on one of the other drivers and click the "activate" button, it acts like it's all fine and says I need to reboot to allow the change to take effect, but after I reboot, nothing has changed. Jockey says no prorietary drivers are in use, the bottom driver is highlighed, and it says it's active but not in use, with only the remove button as an option after several tried. So I researched online and found [this]("http://dragly.org/2012/05/04/installing-the-nvidia-driver-in-kubuntu-12-04/") idea to install and update everything without Jockey and update (actually create) the "xorg.conf" file in /etc/x11/

Well all that did is put my system in 640x480 resolution, and the only way I could get it to go back to 1600x900 was to delete the xorg.conf file. it didn't install the Nvidia driver since I was not able to get past the error "Unknown driver: xorg:nvidia_current
 Use –list to see available drivers" which the page mentions. When I used "-list" it didn't offer any drivers. 

This all made me so annoyed I gave up and just reinstalled the OS, figuring an update from 12.04 to 12.10 would maybe give me some but fixes at the same time. Well I'm now able to use desktop effects which I never was on 12.04, and there is some basic interaction between the TV and computer, but it still isn't fully working, and I still can't install the Nvidia drivers due to the same issues as before. 

Currently when I first turn on the computer, the TV screen shows the KDE splash, and then it shows the wallpaper, but no icons, taskbar, or anything. Just the plain wallpaper stays on the TV, and the computer screen is still on and all is working normally there. The display and monitor settings don't acknowledge a second screen at all. 

Anyway, I'm sure I forgot a few things here and there considering all the stuff I've tried, but if anyone has any ideas or questions. I'll be happy to fill you in on any info you need to fill you in on any info.

At this point, I don't care how the issue is solved, whether it be by getting Nouveau to do HDMI properly, so by getting an Nvidia driver to work. As long as I can figure out something as reboot to Win7 evrey time would be torture.

---

### Post by Trevorius on 2013-01-22
Thank you to all the people who took the time to view my inquiry! Unfortunately at this time the issue has not been resolved, so if anyone has any suggestions I'd still be interested in hearing them.  ;)

---

### Post by Trevorius on 2013-03-13
Still interested in any information anyone would like to share!

---

### Post by Absolute Terror on 2013-03-14
[http://ubuntuforums.org/showthread.php?t=2123436](http://ubuntuforums.org/showthread.php?t=2123436) Come to my thread, maybe we can figure something out.

---

### Post by ManamiVixen on 2013-03-14
The problem lies in the fact your TV is being treated as a second X session linked to your current active account. The reason why it is blank is because KDE has no settings availibe for yet untill you configure it. In order to use the TV, you first need to kill the current X session on that monitor, then open the KDE video settings to include the monitor in the current X session of the default monitor and set it to an extended desktop mode.

---

