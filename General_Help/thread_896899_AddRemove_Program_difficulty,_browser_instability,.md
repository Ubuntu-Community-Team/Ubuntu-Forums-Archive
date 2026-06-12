---
title: "Add/Remove Program difficulty, browser instability, inability to update"
date: 2008-08-21
forum: General Help
---

### Post by CityOflawrence on 2008-08-21
It started when I attempted to install the GStreamer ffmpeg codec pack, and the more I attempt to fix that, the more problems I run into. 

I am using Ubuntu Studio, Hardy Heron.
Computer is an average Gateway, with a Pentium 4. It's got two hard drives, a 40 gig and a 160 gig, and the operating system is installed on the 40 gig.

-Problem #1- Most software on the Add/Remove Programs list gives me an error of "cannot install, unsupported computer type i386". I attempted to fix that, but the solutions suggested in the thread did not work. So I thought an update would do the trick.

-Problem #2- Bringing up Update Manager and selecting "install all updates" brings a dialog that warns against non-authenticated software. When I attempt to view the list of non-authenticated software so I may simply not install it, the drop down list is blank. So there is no non-authenticated software. If I ignore this and go ahead, I get the following error:
> E: The package index files are corrupted. No Filename: field for package autopano-sift.
E: Unable to lock the download directory


-Problem #3- Not sure if this is related, but then I got on Firefow and get on these forums to get help, it wouldn't let me bookmark the site. clicking "bookmark this page" or hitting Ctrl-D does nothing. Bringing up the "manage bookmarks" page causes the browser to crash. 
UPDATE: Just noticed, I don't have a "back" button. It's there, but it's grayed out, no matter how many pages I go to. Not the most pressing issue, but weird.

Thanks for your time. Any advice as to what's going on would be appreciated. It seems odd though, as I've never encountered any of this on my Ubuntu box at home.

---

### Post by CityOflawrence on 2008-08-21
-Problem #2, Updated.
Okay, well I almost fixed #2, but then I ran into a whole new brick wall. I got past the nonsense by simply apt-get install updates, but afterward, the update manager still gave me a list of things that needed to be updated. So I update, and it gives me the following error: 
> The package index files are corrupted. No filename: field for package autopano-sift.
So I uncheck autopano-sift. Probably not important anyway. I try again, it gives me the same error, but for the next item in line. I now uncheck every item under autopano-sift, as they were all 0 kb files, and try once more. Now I get to the downloading package files dialog at last, and I see that it's failing to download every file. At the end, it spits out error messages that look like:
> W:Failed to fetch {address of the package} 403 response denied.
But with a message for each of the packages. I am again at a loss.

---

### Post by CityOflawrence on 2008-08-22
Okay, I fixed the update manager thing by simply apt-get update, but this did not make the 1386 issue go away. Searches for this topic reveal that it's been asked before, but a solution was never really provided.

---

