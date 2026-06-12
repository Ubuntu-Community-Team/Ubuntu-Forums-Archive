---
title: "Stuck at login screen!"
date: 2009-06-05
forum: Hardware
---

### Post by lariosa42 on 2009-06-05
Hello,

After copying some files to a backup drive (while working in root), I rebooted my computer.  The splash screen displayed with no problem, but my computer would not recognize any input from the mouse, keyboard, or touchpad, so I could not log in!

I rebooted in recovery mode, and I was able to use the keyboard.  I ran fsck, clean and a few other utilities, but to no avail.  Next, I tried booting off the live CD, but the computer doesn't recognize it, and goes straight to the usual log-in splash screen.  I don't think I deleted anything while in root, but I don't know what else would have caused this.  

Any help would be greatly appreciated!  =)  I'm up for doing a full system reinstall if that will fix it, but I can't do that without getting the live CD to run.  Thanks in advance!

EDIT: I was able to boot off the live CD using [FONT="Courier New"]startx[/FONT] from the recovery mode root, but it still will does not recognize keyboard or mouse input after booting up x.

---

### Post by lariosa42 on 2009-06-05
So I used [FONT="Courier New"]df[/FONT], and found out that both filesystems [FONT="Courier New"]procbususb[/FONT] (mounted on /proc/bus/usb) and [FONT="Courier New"]udev[/FONT] (mounted on /dev) are 100% full.  This seems bad, and may be why my built-in keyboard and USB mouse are not working.  Any tips on how to correct this, if it is indeed a problem?

---

### Post by lariosa42 on 2009-06-06
No replies yet?  I'm dying here...

OK, so I have been scouting around and found some huge log files in  [FONT="Courier New"]/dev/.bootchart/log[/FONT].  I deleted them hoping to free up some space on [FONT="Courier New"]/dev[/FONT], but it didn't fix the problem.

Upon reboot, it shows that now procbususb and udev are nearly empty, which means I'm out of ideas since things are still not working.  

Thanks in advance for any help! =)

---

### Post by lariosa42 on 2009-06-07
Well, it's been two days, and my computer is still completely stuck.  It would be nice if I didn't have my programming assignment on there that's due next week.

Anyway, I realized that it is not booting off the live CD at all.  [FONT="Courier New"]startx[/FONT] was just booting out of root, which is why it looked different, but behaved the same.  That leaves me still stuck: I can't use the keyboard or mouse with X, and I can't boot the live CD.  This leaves me with trying to find a solution in the terminal.  No luck on that front so far.

---

