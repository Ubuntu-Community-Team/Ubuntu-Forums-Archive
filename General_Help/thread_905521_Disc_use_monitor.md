---
title: "Disc use monitor"
date: 2008-08-30
forum: General Help
---

### Post by wobat on 2008-08-30
I have been looking for a program, preferably a GNOME panel applet, which is basically a software version of the LED showing HDD access, kind of like what you get in the status bar of VirtualBox or other VMs.

Does anyone know of something like this?

---

### Post by EmanresuusernamE on 2008-08-30
There should already be a program installed on your system to show disk usage.  I think it's also called Disk Usage and it should be under the Utilities menu.  I'm not sure, I'm at my parents house on their windows machine.

---

### Post by wobat on 2008-08-30
I think you are refering to the disk usage analyser, which shows how much disk space is used. What I would like is a real-time moniter for access to the disks.

I have 2 HDDs in my computer, and the hardware LED only shows use for the primary, so I want a software version which does both.

---

### Post by EmanresuusernamE on 2008-08-30
How about the process monitor under..... I think Preferences, or Administration in the System menu.  The last tab, if I recall right, has a monitor for filesystems.

---

### Post by wobat on 2008-08-30
Useful info in there :)
but still not what I'm looking for. It doesn't show real-time use.

---

### Post by EmanresuusernamE on 2008-08-30
](*,) Sorry, can't tell you till I get back onto a Ubuntu machine. :(
I think it does though...... My memory's kinda flaky, like a Pillsbury biscuit.

---

### Post by wobat on 2008-10-07
I've found what I was looking for :)
There is a Window Maker dockapp which does this called wmhdplop

---

### Post by Badly Overdrawn Boy on 2008-10-07
If you right-click on the top bar, you can add a system monitor. Right-click again, edit the preferences and you can display a disk activity monitor. That might be sort of what you're looking for.

---

### Post by tpost001 on 2009-02-03
I found that real time monitor.  Now anyone know what is being written or read?  My disk activity is consistently up at around 85-95% after I installed mythtv, but I am not using it.  I know the disk activity is coming from mythbackend, because if I kill it, the disk activity stops, but how can I tell what is being written or read during disk activity?

---

### Post by kay-man on 2009-05-08
is mythtv running something, like mythfilldatabase, flagging commercials or transcoding? That would be an explanation. But you'd expect that to be done after some time.

Have you installed mythweb? If so, is there anything in the backend status page?

Have you checked the mythbackend log files for anything peculiar?

---

