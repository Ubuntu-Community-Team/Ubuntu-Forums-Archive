---
title: "[SOLVED] I Did It! I Removed Freezing From My Xubuntu 8.04!!!"
date: 2008-06-25
forum: Hardware
---

### Post by Odrodzona-Sarmacja on 2008-06-25
Howto:
(freezing can be caused by issues like faulty swap, spinning gam_server out of control, bad memory chips or ..., but the freeze NONE can fix in Ubuntu 8.04 is actually network manager related! and I know how to fix it!)

in terminal

"sudo dpkg --purge --force-all network-manager"
"sudo dpkg --purge --force-all network-manager-gnome"
"gksudo mousepad /etc/networking/interfaces" (mousepad/kate/gedit)

in interfaces add these two lines:
"
auto eth0
iface eth0 inet dhcp
"

Don't ever fix broken dependencies occured from this patch, or you get these "mysterious" freezes everyone blame nvidia drives for and have no fixes for back again to your Ubuntu/Xubuntu/Kubuntu 8.04.

In event if internet connection drops, then do in terminal
"sudo ifup eth0"

Enjoy :)

---

### Post by Odrodzona-Sarmacja on 2008-06-26
Not only that I can use all 3d games, audio & video programs like vlc, browse internet with firefox without any freezes what so ever due rendering problem... I also made a hard drive image of this modified Xubuntu and guess what!

Before removing network-manager package hard drive image size : 5.2Gb
After removing network-manager package hard drive image size : 1.3Gb

WOW!!!
Network-Manager is a BIG IMAGE HARD DRIVE SPACE BLOATER! :D
3.9Gb space down on removing just network-manager package!
Incredible!

Is there a hidden "official ubuntu" rootkit in network-manager? It certainly could explain these issues with HUGE hard drive images I was getting few last months of fiesty, gutsy and hardy, as hard drive image when must copy errors on hard drive (like hidden rootkits file system error?) it can't efficiently compress its file structure in its image file. If it is not rootkit, then certainly network-manager seriously freezes direct rendering (RDI) programs, but also hogs unacceptably large amounts of hard drive space at least when making images of hard drive.

Are there any professional anti-rootkit programs on linux?

---

### Post by Odrodzona-Sarmacja on 2008-06-30
When I got it working without freezes for hours with internet connection all the time on, I forgot I had all cashing functions in BIOS still turned off after checking my memory chips. After I turned then back on I got freezes when networking is on back on my computer. So I looked at networking starting on my computer and disabled avahi-daemon networking service and hot-keys service. Then with synaptic manager I removed avahi-autopid from my computer. However I had still freezes after some time after I booted up my computer with networking. So I went checking for freezes + networking and I found this discusion:
[http://ubuntuforums.org/showthread.php?t=354961](http://ubuntuforums.org/showthread.php?t=354961)
Then with synaptic manager I removed ntpdate and edited and commented with "#" in /etc/bash-completition lines where there was a script for ntpdate.

Only then freezes stoped being random. They become regular. I noticed they were comming short time (about 5 mins) after hourly cron tab process. I went for /etc/crontab and commented line for hourly checks like that:
"#17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly"

Now I don't have any freezes when I boot my computer with networking on and cash in BIOS enabled.

I guess network-manager is only a part of some nasty Ubuntu troyan, as after removal of networking-manager it depends on avahi-daemon and then crontab hourly checks. It looks to me like DRM virus on windows OS computers (where DRM is part of OS and hard to be removed from), because it messes with rendering using applications (content check?) and then it goes using covertly socket for internet connectivity (informing on you).

---

### Post by Odrodzona-Sarmacja on 2008-06-30
Also small addition. I installed "libpam-gnome-keyring" package after I got rid off of freezes on my Xubuntu. All freezes returned immediately when I had computer booted up with internet and they got even worse. I got freeze even during loading up of my desktop. I removed it immediately of course.

I suspect that the second part of this DRM-like troyan is hiding somewhere with libpam packages on my Xubuntu. I recommend removing all possible for removal libpam-* packages (which dont break any dependencies) as possible.

---

### Post by Odrodzona-Sarmacja on 2008-07-04
Well, networking is a bitch. After small trick with editing crontab some stability was achieved for few days and then freezes returned. The bug program must have detected crontab is not servings its purposes any longer.

I got no freezes now only when being offline from internet. I strongly suspect the freezes are due some "popularity-contest" or DRM (Digital Rights Management) alike behaving software, which go wacky when there is internet connection detected on OS. Which package is the bandit I have still no clue.

I will be now installing Xubuntu 8.04.1 and checking it up. I would like to have Xubuntu networking without freezes too. At least now if i get image of Xubuntu 3-4Gb large I know I need just to purge network-manager from OS to get it down to 1-1.5 sizes. :D

---

### Post by Odrodzona-Sarmacja on 2008-07-09
Ok. Here is an update. I had installed on Xubuntu 8.04.1 only these applications:
vlc
firefox
openarena

I removed every other application and most of system packages (including with basing networking, avahi, powermanagement, xorg-video drives and exotic ttf fonts amongst others).

I had still freezes with networking on. So it is nothing to do with medibuntu repository and moblock repository. The freeze come from ubuntu repository and it is ubuntu core OS bound error.

Removing vbetool seemed to crash sometimes openarena to desktop instead of freezing computer and i could also watch vids for longer time, when connected to itnernet. Dunno why. When internet connected the freezes were still there though.

Vbetool is part of acpi-support package. I have acpi disabled in my bios by default. Also I read there is an effort to substitute acpi-support with pm-utils or something like that. Maybe it is causing some conflicts. I also found out that the acpi-support got some radeon controller installed although my computer is 100% nvidia one. Removing entire acpi-support didn't remove these freezes though.

I found out that there is an issue with Simple DirectMedia Layer (SDML) and libpng. It is SDML which is freezing computer. Upgrading libpng to version 1.2.27 removed one serious bug (0 size png pictures issue i think) also causing freezes on Ubuntu, but didn't remove the freezes from Ubuntu, when connected to internet.

I tried installing older version of SDML and libpng, but freezes got just more furious. Installing 8.10 version didn't fix freezes either. Although i think libpng 1.2.27 is serious upgrade for Xubuntu 8.04, which should be applied asap on it.

IMHO SDML is having here some crushing conflict issue with some core Ubuntu program, which removal would be fatal for firefox, openarena and vlc in the same manner as SDML removal. Using original not-upgraded fiesty (Xubuntu 7.04) Ubuntu core OS certainly fixes these freezings 100%.

---

### Post by Odrodzona-Sarmacja on 2008-07-09
1. Simple DirectMedia Layer (SDML) (1.2.13-1ubuntu1):

inflicts freezes in all games (not only 3d games but also 2d games too)

inflicts freezes in most audio/visual applications with vlc, amarok, audacious, movie player included

inflicts freezes in firefox and other diverse programs using python rendering engine

Disabled in freeze are keyboard, mouse, sound and video, which are used by SDML.

2. To install latest safest libpng used by SDML:
[http://packages.ubuntu.com/intrepid/libs/libpng12-0](http://packages.ubuntu.com/intrepid/libs/libpng12-0)
then in terminal in directory it downloaded:
"sudo dpkg --force-all --install <pakage name.deb>"

3. To remove vbetool:
"sudo dpkg --force-all --purge vbetool"
When doing software update you may wish temporarily install it again in synaptic manager. Then remove again with this command.

---

