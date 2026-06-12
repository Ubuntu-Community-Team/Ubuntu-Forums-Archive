---
title: "Total System Crashes!"
date: 2005-11-05
forum: General Help
---

### Post by skybum on 2005-11-05
Recently Ubuntu has become very unstable for me, with crashes that bring the entire system down.  I'm actually in the middle of one right now, and hopefully the system will stay up long enough for me to write this post and report the symptoms I'm seeing.  By the way, this just started happening; nothing discernable caused it.

1.) The gnome-panel doesn't work.  Any time I attempt to launch anything from the menu, I get a message saying "Cannot launch entry -- Details: not a launchable item"

2.) Fortunately, I had a terminal window open when this began.  So I thought to restart the Gnome-panel with a "killall gnome-panel".  It gave me the following response: "bash: /bin/ps: Input/output error".

3.) Thinking that perhaps my user login had gotten screwed up, I tried "sudo killall gnome-panel", but got the error: "sudo: Can't open /var/run/sudo/nathan/0: Read-only filesystem"

4.) Thinking that perhaps some weird process was mucking up the system, I tried "ps", but encountered the same results.  Only "cd" and "ls" seem to work.

5.) If this continues as it has, the icons off my desktop will soon vanish, my system will become unresponsive, and I'll have to do a hard reset.

So, with all of this, will someone tell me what the hell is going on???

Thanks in advance!

Edit: as an addendum, when I went to the "System / Log Out" menu item, it immediately dropped me into the full-screen shell mode, with an "Ubuntu Login" prompt that didn't seem to actually do anything.  When I hit ctrl-alt-delete, however, it gave me the message "cannot execute sbin/shutdown", so I had to hard-reset after all.

---

### Post by teaker1s on 2005-11-05
try reinstalling the base system If it goes screwy that cured mine also reistall users component.
Strange thing I've found I had default 386I kernel and it was unstable on an xp2200 cpu since I've installed K7 kernel image it's rock solid and way faster.

---

### Post by nightfly on 2005-11-06
Your filesystem is corrupted. There are errors in your filesytem inode structure.
This was due sudden power interruption or major I/O load at some point before.

> I tried "sudo killall gnome-panel", but got the error: "sudo: Can't open /var/run/sudo/nathan/0: Read-only filesystem"
When your filesystem is corrupted, the journalling daemon will eventually remount it read-only for you and thus nothing can be written on disk anymore. 

> Any time I attempt to launch anything from the menu, I get a message saying "Cannot launch entry -- Details: not a launchable item"
> So I thought to restart the Gnome-panel with a "killall gnome-panel". It gave me the following response: "bash: /bin/ps: Input/output error".
This is probably due to inability to write temporary files and/or creating lock files on the disk. Your milage may vary.

> the icons off my desktop will soon vanish
This is due to Nautilus not being able to update its cache files on your local disk and eventually stop working.
  
There are good news. You can fix your file system the way it was before without having to format anything. Use the e2fsck utility.

Grab the Ubuntu installer disc and boot it. Once you have selected the language click Tab to highlight the "Go back" button. Click it. You will presented  with a menu of the sections of the installer. Select the menu item that will open a command shell for you.

Once you are in a command line shell (you should be root), run the e2fsck utility against your filesystem.

Example. Substitute /dev/hda1 for your correct device
```
e2fsck -fp /dev/hda1
```

This will force fs correction and will not ask any questions. Be aware that this process may remove one or more of your files. For additional details on e2fsck see man e2fsck (not available from install shell).

---

