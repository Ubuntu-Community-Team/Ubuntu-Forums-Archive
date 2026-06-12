---
title: "Tried setting up a HTPC with Ubuntu, this is my story"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by Jeinhor on 2009-07-05
Hello again!

This last week I've been trying to setup a HTPC using Ubuntu and XBMC.

I grabbed the alternate install CD, configured software RAID on my two 640 GB S-ATA-disks according to below:

/ 20 GB RAID1
/swap 4 GB RAID1
/safe 200 GB RAID1
/unsafe ~800 GB RAID0

I installed it using my 17" LCD monitor, and everything was fine. I then tried connecting it to my TV (via VGA, 1024x768 resolution). Just a black screen when trying to run gnome.

So I figured I had to install it at my TV directly for Ubuntu to properly detect it. Same result. I searched the web, tried various xorg.conf, different graphics drivers and so on. Found nothing that helped.

Then after hours of googling and a couple of reinstalls I tried connecting my TV when I was still running gnome on my 17" monitor. Using gnome-display-properties I was able to get a picture on my TV. However, after reboot it was gone again.

I found a startup script for gnome (/etc/gdm/Init/Default) and added a xrandr command to enable my VGA output and set its resolution to 1024x768. However, while my monitor was still connected gnome had a virtual resolution of 1280x1024 which was too big for 1024x768, so I added "Virtual 1024 768" to xorg.conf. This worked, but gave me problems with position of the desktop (slightly wrong and a green line of maybe 5px at the bottom), so I removed it and just disconnected the 17" monitor and rebooted. It worked!

So now I was all set to configure audio (through S/PDIF to my receiver). I enabled the ALSA S/PDIF playback device in "Sound", pressed "Test" and got the beeping test tone. Nice, worked out of the box! But (there it is again), still no sound in Ubuntu or flash in Firefox, but sound in Rhythmbox. After more searching on Internet (we're talking hours) I found a ~/.asoundrc configuration file which redirected all sound to the digital output. Now everything worked! I was all set!

I installed XBMC, scanned and tagged some media files and then clicked one to play it. The whole system hanged. I used Ctrl+Alt+F1/F2/F3(..) to switch to a terminal and tried to reboot. At the next reboot, automatic file check was started (fsck). It told me I had to run it manually though, so I did. Got some error, couldn't issue a single command, had to hard reboot. At next boot up I got the famous "Grub 17 error".

I then thought one of the hard drives were faulty, but I was glad I previously had setup mirroring on the root partition. So I removed one of the drives (physically) and tried booting on the other, still grub 17 error. Removed the other (and inserted the first back in) and tried booting, same error. So much for that RAID setup...

And that's where I am now. I can also mention that I've had the same setup running on Windows Server 2003 with the same hardware for months without any problems...

I can admit I am no Linux geek, but I do know my ways around Linux and I'm not stupid. I also hate to give up, and I don't do it very often. But I'm about to do an exception, I'm running out of reasons to spend any more time on this...

I really appreciate the work you guys have put into it, and I hope I might be able to use it someday (I like the open source concept), but it will be long before I touch a Linux dist again after this experience.

If anyone know what I did wrong and how to correct it, I'm listening, though I have no high hopes on this system right now.

Sorry for the ½rant, but I'm a bit frustrated right now. If you have any success stories with a similar setup, please share, might cheer me up =)

Cheers!

---

### Post by Jeinhor on 2009-07-09
New day, new possibilities!

I ran some diagnostic tests on the harddrives, turns one was faulty.

Booted with the healthy disk into Knoppix and mounted /dev/sda6. I could access the mirrored files! Even though I couldn't rescue the system, I could still copy the important files to a USB drive and re-install.

Let's see how it goes this time...

---

