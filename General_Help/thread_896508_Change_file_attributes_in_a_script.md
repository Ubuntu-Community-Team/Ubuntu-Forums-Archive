---
title: "Change file attributes in a script"
date: 2008-08-21
forum: General Help
---

### Post by Silversleeves on 2008-08-21
Hi.

I was thinking about the pro's and con's of running Konqueror or Dolphin as file system navigators in superuser mode when it occurred to me that any copies of files or directories made in that mode would belong to root (elementary, my dear Watson, I hear you say). As a plain user in the same environment, these items would be uneditable and/or undelete-able, should either necessity arise. So, having already posted something regarding desktop links to applications and such, I wondered if it would be possible to create a bash or python script to change the attributes of a selected file, and make it accessible either from the desktop or from (as is possible in Gnome) the right-click menu. So the basic questions are, first,are any of the attribute-changing commands for files scriptable? And second, if so, how?

Optimistically, this may provide a workaround, if not a solution, to the problem I encountered (and I'm sure I'm not the only one) when running Dolphin as root -- that when I return to running Dolphin as a plain user, the bookmarks.xml file is reported as un-write-able, when it simply belongs to root, having changed in the previous user mode.

So here I go, waiting for a reply. 

Silversleeves

---

### Post by qstraza on 2008-08-21
I dont fully understand what do u want to do.
I get that if you use konqueror as root, every change will be made by root and not as user.

But what script do u want? You want a script which will change owner to user when you copy/edit a dir/file as root? Cant you use "sudo chown -r user_name file/dir" ?

Try to explain to me one more time, fancy english words confuses me:p

---

### Post by Silversleeves on 2008-08-24
Well, there's always another way, isn't there?

I found, while sating my curiosity for creating Service Menus to add to Dolphin, one that was already written and tested by the good folks at KDE-Apps.org. By name: Root Actions 2.3. It has an option to change permissions etc, as root on files and folders. This is pretty much what I had in mind. I had a strong feeling someone had puzzled it out and come up with a solution, and in this case I was right.

Silversleeves.

---

