---
title: "System Restore for Ubuntu?"
date: 2008-09-15
forum: General Help
---

### Post by Inane_Asylum on 2008-09-15
One of the things I really liked about Windows was the System Restore option.  It saved my butt quite a few times when making changes to my system that I wanted to undo...

Is there anything like that for Linux/Ubuntu?  The main reason I ask is that, after finally getting my sound working on my laptop, I uninstalled a few programs I wasn't using (VLC, Rosegarden, Superkaramba, and a couple others), and after the next reboot, my sound stopped working again.  Nothing I tried got the sound working again.  Would be nice if I could restore the system to a previous state and pretend it never happened...

---

### Post by phidia on 2008-09-15
Time vault is still in development, I believe, but you can try it. The Ubuntu wiki on it is [here]("https://wiki.ubuntu.com/TimeVault").

---

### Post by Inane_Asylum on 2008-09-15
Since it depends on Nautilus, would It work in Kubuntu?

What about these others that the wiki mentions?  Are they any good?

dirvish 
glastree 
pdumpfs 
rsnapshot 
rdiff-backup

EDIT: Whoops, just saw this...
> ToDo
KDE-port: I've done the GUI for KDE port, the code obviously needs a fair few changes but it's on the back boiler for a few weeks. -- KieranHogg

---

### Post by mrsteveman1 on 2008-09-15
There is always the ultra-insane option of using a filesystem that allows snapshots, but offhand i can't think of many that can do this. I do believe lvm2 can do it though.

Of course, if you do that you literally go back in time and lose any and all changes made to any file, not just the system.

blah :D

---

### Post by Antar Hydrus on 2008-10-01
I use rsnapshot and like it because it keeps the backups for all of my machines in one central location on my fileserver. AFAIK, it is command line only but pretty simple to figure out. The config file is well documented.

---

