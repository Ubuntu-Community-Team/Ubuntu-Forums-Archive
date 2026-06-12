---
title: "Killing a Process that Doesn't Show Up?"
date: 2008-08-08
forum: General Help
---

### Post by A2JC4life on 2008-08-08
I am having a problem with Firefox.  I can't run it because it says it's already running.  When this happens in Windows, I can just go in and terminate the process.  (It does NOT show up as a program that's running, but does show up under the processes tab, and I can kill it there.)  In Ubuntu, though, I'm not seeing it anywhere.  It is not listed as a process, even if I tell it to show all processes and dependencies.  (Unless it's called something I would never recognize as Firefox.)  What can I do?  (I am a complete and utter newbie, having just installed Ubuntu last night, so I need a jargon-free answer please! :) )

---

### Post by blazercist on 2008-08-08
```
killall firefox-bin
```

---

### Post by PmDematagoda on 2008-08-08
Post the output of:-
```
pgrep firefox
```

---

### Post by A2JC4life on 2008-08-08
I can just type this in straight from a command line?  No necessary prerequisites?

---

### Post by PmDematagoda on 2008-08-08
> **A2JC4life said:**
> I can just type this in straight from a command line?  No necessary prerequisites?

Yes.

---

### Post by A2JC4life on 2008-08-08
No luck. :(  The pgrep command returns absolutely nothing.  The killall command returns a message that says no processes were killed.  (haha That sounds like a movie disclaimer: "No processes were killed in the making of this movie.")

---

### Post by blazercist on 2008-08-08
```
ps aux | grep firefox
```

if this returns nothing then the process is not running, period.  its possible, although I'm not sure that firefox creates some temp file somewhere to signal to itself that it is running, this file may not have been removed properly on the programs' last exit and thats why you get the error.  Again, I don't know if firefox actually works this way but it is a possibility.

---

### Post by A2JC4life on 2008-08-11
> **blazercist said:**
> ```
ps aux | grep firefox
```


Okay, I tried this, and it returned the following:

```
rachel 5899 0.0 0.1 3004 752 pts/0 R+ 21:40 0:00 grep firefox
```

When I try to run Firefox, the message I get states "Firefox is already running, but is not responding."  (Not an uncommon message on my Windows installation, either, but as I mentioned, I can usually just kill the process from the Task Manager in this case.)

---

### Post by PmDematagoda on 2008-08-13
Perhaps the issue is just a stale lock file, try looking in ~/.mozilla/firefox/97peui19.default and see if there is a lock file and then delete it.

---

### Post by Mgiacchetti on 2008-08-13
enable the viewing of hidden files and folders and search your ~/.mozilla/firefox folder for .parentlock

If it exists, delete it.

---

### Post by A2JC4life on 2008-08-17
Okay, now I'm very puzzled.

These sound like logical solutions, and would probably work.  Except I can't find my .mozilla folder now.  I have hidden files set to display.  (I've checked that several times.)  And I know it was there before; I copied a new profile into it (copied from my Windows installation).  I have come back to Windows and come online and double-checked the location and gone to look again, and I cannot find it anywhere.  A search does not turn it up.  Nor does a search turn up the xx...xx.default folder, except for the copy that's still on my thumb drive.  What in the world?!  :confused:

---

### Post by jmszr on 2008-08-17
A2JC4life,
          Perhaps you've already tried this,but if not :
Click system > administration > system monitor > processes > firefox > end process.

Hope this helps

---

### Post by A2JC4life on 2008-08-17
Yes, I tried that first.  That's where the process is not appearing.  Firefox says it's already running, but it is not in the list of processes in the system monitor.

---

### Post by todak on 2008-08-17
Try ```
killall firefox
``` from the terminal

---

### Post by A2JC4life on 2008-08-26
I don't see any lock files.  I have now completely uninstalled and reinstalled Firefox, and I am still getting the same error.  It still does not show up in the current processes list, and I have double-checked for a lock file since reinstalling.

---

### Post by tbunix on 2008-08-26
my .parentlock file is located in:

/home/xxx/.mozilla/firefox/axy04cpp.default/.parentlock

---

