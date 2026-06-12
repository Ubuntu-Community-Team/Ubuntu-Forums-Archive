---
title: "Problem installing nvidia graphics card"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by mvander3 on 2009-09-10
I just installed Ubuntu 9.04 a couple of weeks ago (well, I'm actually dual booting with XP). Everything was going well until I tried to install a new PNY NVidia GeForce 8400 GS (PCI) graphics card. I have tried following a guide [here]("http://ubuntuforums.org/showthread.php?t=1125400&highlight=default+runlevel"), installing both new and older drivers, as well as using Envy.  However, whenever I try to boot Ubuntu using the new graphics card, I get an error in both normal and recovery mode.  

When booting normally, the progress bar gets about 10% and hangs for a few minutes, then has this:
"* Loading hardware drivers...
udevd-event[1448]: '/bin/mkdir/var/run/network' abnormal exit 

udevd-event[1566]: '/bin/mkdir/var/run/network' abnormal exit 

[blinking cursor]".
 
 , and after a few more minutes this: 

init: Unable to execute "/sbin/getty" for tty1: No such file or directory
init: tty1 main process  (1703) terminated with status 255
init: tty1 main process ended, respawning
init: tty1 respawning too fast, stopped

If I boot into recovery mode, I get this: 

"[   188.824084]: [<c0103f6b>] ? sysenter_do_call +0x12/0x2f
[   188.824084]: Code: [Random Hex lines] 
[   188.824084]: EIP: [<c021c6ec>] ext3_handle_error+0x1c/0xb0 SS:ESP 0068:f678bcc8
[   188.824084]: ---[ end trace 334f7c77748ab0fa ]---
init: rcS-sulogin main process (1714) killed by SEGV signal".

xfix didn't help.  I have looked around for solutions, but haven't found any that helped yet.  Thanks for any help you can give me.

---

### Post by bumanie on 2009-09-10
Whatever you have tried seems to have mucked a lot of things up. You may have to reinstall, which may be easier than trying to fix the problems that have been created (assuming it is a new installation, without heaps of saved files that you need).
If you reinstall, to get nvidia drivers going, go to System --> Administration --> Hardware drivers, click on hardware drivers, the system will search for drivers you need and when finished, click on "Activate" and the correct driver will automatically download.

---

### Post by Oiolosse on 2009-10-01
@mvander3:

I just received the same error messages, however

"init: tty1 main process  (1703) terminated with status 255"

is replaced with:

"init: tty1 main process  (**4289**) terminated with status 255"

It hung right about 10% also...BUT, I rebooted, nothing..I rebooted and voila! here I am.
I am afraid however to turn off my comp in fear of not being able to reboot. I will say that last night I could not get VLC/Mplayer to play DVDs. I installed Medibuntu and am now able to play DVDs when accessing Mplayer through the terminal. I did not mess around with my nvidia drivers though.

I will also say this, when first setting up Ubuntu the nvidia version (180) was/is recommended when I go into System-->Administartion-->Hardware Drivers. Well, this causes funky things to happen (forgot what, but for whatever reason it made my system inoperable). I reverted to version (177) and have had no problems since. Hope that helps.

However, if there are ubuntu/linux wizards reading this, what's up with those messages?

---

### Post by Oiolosse on 2009-10-19
It has been two weeks and no error message..it must have been a hiccup.

---

