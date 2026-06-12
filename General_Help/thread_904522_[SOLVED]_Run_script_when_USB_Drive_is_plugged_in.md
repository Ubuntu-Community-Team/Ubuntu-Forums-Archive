---
title: "[SOLVED] Run script when USB Drive is plugged in"
date: 2008-08-29
forum: General Help
---

### Post by pofigster on 2008-08-29
With school starting again pretty soon and with the volume of programming I'll have to do for classes, I'm a little paranoid about losing all of my work.  So, on my desktop at home I have a folder that every 30 minutes rsync with a flash drive that is always plugged into the back.

What I want to do is have the computer recognize when I plug my other flash drive into the computer and rysnc it with the desktop. I know I could place the script in a cron and have it run really often just rysnc with the folder where the flash drive mounts, but, I'd rather be more elegant about it.

Any ideas on how to have Gnome or Ubuntu run some script called, say, schbk.sh whenever I first plug it in?  Similar to the autorun of Windows.

---

### Post by fragos on 2008-08-29
I believe your solution will be in /etc/udev/rules.d. You can use rules to run scripts. In particular see 80-programs.rules.

---

### Post by mc4man on 2008-08-30
It would be very easy to do (100% automatic) if there is a way to 'override' the autorun prompt that hardy insists upon using.

for example
 
Put your script or a script calling your intended script into the root of the usb drive and name it autorun.sh. When you insert the drive you get a pop up asking if you want to run it, clicking 'run',  runs the script(s).
If there was a way to allow it to run without the prompt then that might fit the bill totally. 
Though clicking run on the pop up isn't too bad i guess.

see screen

I thought maybe if hardy saw the autorun.sh as being on a cdrom then it might allow autorun without a prompt. I created a small 'isofs' partition on the flash drive that only had an autorun.sh in it.  While it was seen as a cdrom drive (/dev/scd2) it could only be automounted by an entry in fstab, requiring the drive being inserted at boot. Plus unfortunately this way also ran into the same 'prompt' step.

Note; to get the popup I believe you have to go to file management -> behavior and enable 'run executable text....', otherwise it's shows up on r.click

I found it easiest to leave my script in home dir. and just use this for the autorun (rip being name of my script
> #! /bin/sh
cd ~
./rip

---

### Post by pofigster on 2008-08-30
I had no idea that .autorun would be recognized.  Thanks for the tip - it worked perfectly!

---

### Post by mc4man on 2008-08-31
glad it worked for you. 

small point

If you happened to set the 'executable text file' behavior in file management as noted above (to gain the pop up) there is a somewhat unintended consequence.
If you have text files that were **copied** from somewhere (ex. a flash drive), then d. clicking on them will attempt to 'run' them . In most cases nothing happens including opening them to view. (hard to describe but if it occurs you'll know what I mean.

The best way to approach is to r. click -> properties -> permissions and click **twice** on the execute box. First click will change from a line to a check mark, second click will clear the box (no execute)
After that they will open as normal text files.

Screen 1 before clicking, screen 2 after second click.

---

