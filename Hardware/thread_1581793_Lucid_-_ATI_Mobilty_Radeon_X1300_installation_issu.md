---
title: "Lucid - ATI Mobilty Radeon X1300 installation issue"
date: 2010-09-25
forum: Hardware
---

### Post by Wins2LinX on 2010-09-25
Hello

I am seeking your help to fix ATI Mobility Radeon X1300 display driver issue.

System - hp Compaq nc6400 laptop. Windows XP prof/ubuntu partitioned.
Display device - ATI Mobility Radeon X1300.

The laptop display is fine by it self and when docked, the Vizio monitor works excellent with Windows XP.

Requirement - Need the same display ability in Ubuntu Lucid 10.04.
The laptop is used as stand along and some time I want to dock and use with my new Visio HDTV monitor.

What I did - Decided to install the graphic drivers/software, (by mistake followed Nvidia installation procedure). Followed multiple websites on installation procedures and installed Nvidia drivers. Later realized on installing the wrong drivers, by 'Synaptic package manager' un-installed all Nvidia packages. and installed again the ATI packages. rebooted but still no good.

Issue - When I try to login to Ubuntu, I get a error message 'Ubuntu is running in low-graphics mode" and (EE) Failed to load module 'nvidia' (module does not exit '0').
bypassing the error and loging in isl no use. 
When I want to see the display configuration setting (see attached document for screenshot) I get initialization error. The Vizio HDTV monitor does not see signal from my docked laptop.

I have installed ATI packages in Synaptic Package manager I have updated " gksudo gedit [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]modprobe.d[COLOR=#000000]**/**[/COLOR]radeon-kms.conf " with " options radeon [COLOR=#007800]modeset[/COLOR]=[COLOR=#000000]0 " in the blank file.

Please let me know if you need more info.
[/COLOR]

---

### Post by darkstarbyte on 2010-09-25
ATI just opened up there drivers so the 2d drivers so the open source ones might not work as well. The reason they have not opened up the 3d drivers is because they don't own the code for some other company does. If you want the 3d drivers I think they have it on there page. Let me see if I can find it.

---

### Post by darkstarbyte on 2010-09-25
I got the website I hope this helps.

[http://www2.ati.com/drivers/linux/linux_8.24.8.html](http://www2.ati.com/drivers/linux/linux_8.24.8.html)

---

### Post by efflandt on 2010-09-25
You need to undo everything you did for nVidia drivers, since it is not nVidia, and some of the nVidia specific things can interfere with other video.  But if you manually installed nvidia instead of using Hardware Drivers or Synaptic I am not sure how you would do that.  At the very least you should delete xorg.conf (sudo rm /etc/X11/xorg.conf).  But if the nVidia proprietary glx is still there it might slow your ATI because it may interfere with mesa glx.

I don't think there are any proprietary ATI Linux drivers that work with legacy ATI chips (from before AMD bought them) anymore in current X servers.  So you should just use the default drivers except for one thing.

I have a Dell laptop with that mobile X1300.  By default Lucid uses kernel mode setting (kms) drivers and my X1300's (laptop or desktop) did not like that (the laptop would sometimes video glitch/hang during boot and desktop video was slow and could not suspend/hibernate).  Those issues were resolved using **nomodeset** (or more chip specific **radeon.modeset=0**) kernel boot parameter to use the older style user space video modules.

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

Worst case if you do not know how to undo what you did and have not done much else with the system would be to save whatever files you want to keep elsewhere and reinstall.  Manually select partition(s) it is currently installed on during install (automatically finds existing swap).

---

### Post by Wins2LinX on 2010-09-26
I thank you both for your response. 

[darkstarbyte]("http://ubuntuforums.org/member.php?u=1123095"), I tried your link and recommendation and it worked. I have installed "ati-driver-installer-10-9-x86.x86_64.run".

The issue are
1) the resolution is 1024x768. Worse than the laptop display which is 1440 x 900.
2) in terminal application, when I [FONT=monospace]'[/FONT]fglrxinfo', all I get is 'Segmentation fault' as response.

Now, I don't have a 'xorg.conf' file in /etc/X11 folder. I see only 'xorg.conf.backup' which has all nvidia info from the previous install.

Can you please guide me to resolve these issues.

thanks again for your guidance.

---

