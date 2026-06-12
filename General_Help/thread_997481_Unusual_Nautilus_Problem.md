---
title: "Unusual Nautilus Problem"
date: 2008-11-29
forum: General Help
---

### Post by kuxpac383 on 2008-11-29
First off I'm running Ubuntu 8.04 and Nautilus 2.22.5.1.

My problem is as follows, when I go into nautilus and go into the "pictures" folder followed by going into one of the sub-folders in the pictures folder nautilus freezes and I have to do a force quit in order for it to close.  All other folders and sub-folders work correctly except this one.  I've tried to delete the folder and its contents and create it again.  Every sub-folder I try to get into causes this problem.  This folder is in my Home folder also, if that helps.  I tried everything I know.  Any additional help would be greatly appreciated.  
Thanks,

---

### Post by drs305 on 2008-11-29
This could be related to a recent bug. Right click on any folder, select "Open with other application" and select "File browser". See if that fixes it.

---

### Post by kuxpac383 on 2008-11-29
That works, but I'm going to have to do that everytime? Odd.

---

### Post by kuxpac383 on 2008-11-29
When I mean "it works", I mean it opens up the folder in a separate window, but if I don't do this, it still freezes.

---

### Post by drs305 on 2008-11-29
No, what I described fixes the bug more or less permanently. It's actually "Open With", "Open with other application", "File Browser". If that was going to work it should work from that point forward. You may need to close out all instances of nautilus but that is about all it should take if this is going to solve it.

Added: there was a slight variation of this posted a few days ago but the solution above worked for the people who tried it. The variation got to the same point but via a slightly different method. If you do a search for posts with "Open with" "nautilus" "Open with other application" you can probably find the thread. 

Either one fixed a specific bug, but your problem may be unrelated.

---

### Post by kuxpac383 on 2008-11-29
Unfortunately, that did not fix it. When I click on "pictures", then the "wallpapers" sub-folder for example, that locks it up.  Doing your method does work, but only to open up a new window correctly.  It is very odd just by clicking on the folder, than the folder it locks up.  All other instances it works fine.  That is why I am stumped too.

---

### Post by Connyank on 2008-11-30
> **drs305 said:**
> No, what I described fixes the bug more or less permanently. It's actually "Open With", "Open with other application", "File Browser". If that was going to work it should work from that point forward. You may need to close out all instances of nautilus but that is about all it should take if this is going to solve it.

Added: there was a slight variation of this posted a few days ago but the solution above worked for the people who tried it. The variation got to the same point but via a slightly different method. If you do a search for posts with "Open with" "nautilus" "Open with other application" you can probably find the thread. 

Either one fixed a specific bug, but your problem may be unrelated.

I'm having a similar problem with Nautilus but it doesn't seem to be a specific folder - just any with more files than 100 or so.  The work around mentioned here has no effect.  It was suggested that I check my hd with fsck, which showed errors.  I did a force fsck upon reboot and it ran but didn't fix anything.  I am also having concurrent nvidia problems (surprise) but don't know if related.  This is my 1st post here (usually lurk over in the ubuntu newsgroup) since I can't get much response over there.
Using 8.10 w/ nvidia gforce mx 420, 5mg ram, P IV, u 8.04 on 2nd HD, just upgraded kernel, which had a nvidia upgrade inside it.

I'll continue on to rest of posts google pulled up as well as othere here.

should I start another thread on this?

Thanks,
jg

---

### Post by drs305 on 2008-11-30
Connyank,

First, welcome to the ubuntu forums. I think you will find it is an excellent resource. 

Most problems have been discussed somewhere on this forum but sometimes you just have to ask again. If you can't find any solutions via google on this site then yes I would post a new thread of your own and describe your problem and what you have tried.

---

### Post by mc4man on 2008-11-30
I think the bug in question was associated with 8.10 where right clicking on a dir. and using 'open with other application', 'use a custom command' and maybe the 'open with'  incorrectly set the app chosen as default for opening directories.

Small digression 

(( You can view the behavior of a r.click 'open with other....' or 'use a custom ...' on a dir. by watching the line "inode/directory=" in ~./local/share/applications/mimeapps.list.
Every time you use either of those a .desktop is either added or moved to the top of the line. 
That's one of the few lines in mimeapps where the first listed is not the default, the list just refects what's available off of the r.click 'open with'.

Initially in 8.10 the first listed was the default, no more

In 8.04 (and probably now in 8.10) you can't change the default double left on folders, if you've set your preference to 'always open in browser window' then that's locked in as the default - open in same window in nautilus or in a new browser window from the desktop. 
Even trying to change from right click properties will have no effect.))
............................


Out of curiosity what happens if you change your default behavior from 'icon view' to 'list view'
This can be set in file management -> views  (enable in edit menus -> preferences or go in nautilus -> edit -> preferences

Maybe nautilus is having trouble rendering all the icons... ?

Another 'interesting' thing to try would be to r. click on the folder ' open with' or continue to 'open with other.....' and pick Firefox or even better if you have it, Seamonkey.

---

### Post by Connyank on 2008-12-01
> **drs305 said:**
> Connyank,

First, welcome to the ubuntu forums. I think you will find it is an excellent resource. 


thanks for that thought...


Most problems have been discussed somewhere on this forum but sometimes you just have to ask again. If you can't find any solutions via google on this site then yes I would post a new thread of your own and describe your problem and what you have tried.

Thought so, though so far haven't gotten too far.  I know the answer is somewhere, though.  This format is a bit new to me so bear with my formatting.

---

### Post by Connyank on 2008-12-01
> **mc4man said:**
> 

<snip small digression - appears unrelated to my problems>

Out of curiosity what happens if you change your default behavior from 'icon view' to 'list view'
This can be set in file management -> views  (enable in edit menus -> preferences or go in nautilus -> edit -> preferences

Maybe nautilus is having trouble rendering all the icons... ?


nope - I use list as default

Another 'interesting' thing to try would be to r. click on the folder ' open with' or continue to 'open with other.....' and pick Firefox or even better if you have it, Seamonkey.

maybe interesting but don't think it would apply here - I'll post a new thread in the morning - then I'll try and figure out how to split these quotes up.
Thanks for your input.
jg

---

