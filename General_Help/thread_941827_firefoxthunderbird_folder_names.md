---
title: "firefox/thunderbird folder names"
date: 2008-10-08
forum: General Help
---

### Post by reader4 on 2008-10-08
I currently sync most of the folders in /home/user/ on my laptop and desktop computers (hardy 32 and 64, respectively) with unison.  I would like to sync firefox/thunderbird info (bookmarks, addressbook, etc.) as well, but am faced with two different profile folder names on each system because of the random number code used by mozilla.  The easiest solution would seem to be changing the folder names (say, "user.default") and syncing that folder with unison, but initialization and preference files within the folder reference the xxxxxxxx.default names.  Anyone know how I can change the profile folder names without losing links to bookmarks, etc.?  I know that I can create a new profile using the proper folder name, but then I have to reset my preferences, bookmarks, etc. Maybe the solution is to do this and import/copy only the files needed, but I'm not sure which those are...

---

### Post by ajgreeny on 2008-10-08
Can't you simply copy the **.mozilla** and **.mozilla-thunderbird** folders from the most up to date of the two and copy it to the other machine.  That will then make sure the profile.ini file in both machines is the same and that all the bookmarks etc are the same, and that the same profile is loaded in both machines.  There shouldn't be a problem then syncing the two, unless, of course, the fact that one is 32bit and the other 64bit means that the profiles are not readable, one by the other.

---

### Post by reader4 on 2008-10-08
I think I can "sort of" do that, but I was hoping to merge some of the data which is currently inconsistent between systems.  I am probably just better-off to import one system's info into another, then copy and paste... was just hoping to hear there is some easy way to change the incidence of xxxxxxxx.default throughout each file in a directory or something similar...

---

### Post by charliea_w4 on 2008-12-19
I managed to set up a Firefox sync between two Ubuntu boxes using Unison and following the instructions below:

[http://www.micahcarrick.com/11-07-2007/unison-synchronize-ubuntu.html]("http://www.micahcarrick.com/11-07-2007/unison-synchronize-ubuntu.html")

Note the "Gotcha" at the end of the first section, he describes how to rename your folders to avoid the problem in syncing two random directory names

---

