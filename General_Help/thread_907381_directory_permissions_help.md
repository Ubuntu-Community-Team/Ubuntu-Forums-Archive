---
title: "directory permissions help"
date: 2008-09-01
forum: General Help
---

### Post by mattack on 2008-09-01
I have a directory that I want all the files to have the same permissions, 755. It would be awesome if all files added to this directory inherited these permissions as well, as some files are auto-created and I don't want to manually set the permissions when this happens.

For example, the directory in question contains music. I'm constantly adding files to it. I'd like all added files to inherit 755 permissions when I put them in the music directory without having to run chmod every time.

How do I do automatically set permissions to all files that get put in this directory?

Thanks.

---

### Post by aysiu on 2008-09-02
I'm not sure, but this thread may help:
[http://ubuntuforums.org/showthread.php?t=202582](http://ubuntuforums.org/showthread.php?t=202582)

---

### Post by Vivaldi Gloria on 2008-09-02
> **mattack said:**
> For example, the directory in question contains music. I'm constantly adding files to it. I'd like all added files to inherit 755 permissions when I put them in the music directory without having to run chmod every time.

Out of curiosity, why is 644 not enough for files?

---

### Post by monkeyking on 2008-09-02
I found the problem interessting but since,
no one has given a solution.
I guess there is non.

I would just write a script an use crontab to do it manually every hour or so.


good luck

---

### Post by bingoUV on 2008-09-02
Use this script: [http://bingouv.blogspot.com/2008/08/script-to-fix-directory-permission-and.html](http://bingouv.blogspot.com/2008/08/script-to-fix-directory-permission-and.html)

Use your username as the "group" for the script. It will set the permissions to 775. I am writing a generic version of this script, and if it gets completed you can get it. Otherwise you can edit it, or make do with permission 775. If all files are owned by you and the group owner of all files is always the group with the same name as your username, 775 is no different from 755.

It does not use any cron, and CPU utilization is negligible because it uses inotify. No guarantees.

---

### Post by mattack on 2008-09-08
> **Vivaldi Gloria said:**
> Out of curiosity, why is 644 not enough for files?
I'm running SqueezeCenter on my desktop, and it doesn't seem to like files that aren't executable by "other." I'm constantly adding files, MP3s as I rip my cd collection, and image files as I download cover images.
It would be nice if they inherited the correct permissions for the SqueezeCenter to use them.

---

### Post by mattack on 2008-09-08
> **monkeyking said:**
> 
I guess there is non.

I would just write a script an use crontab to do it manually every hour or so.


There's got to be a solution. And I don't add files that often to run an hourly cron job... While that would work, that's not what I'm looking for.

I think I'm just going to learn a little bit of Python to modify the CopyCover script in Amarok to create files with the permissions I need.

---

### Post by Vivaldi Gloria on 2008-09-08
> **mattack said:**
>  ... 

Thanks for answering. I think you should let the programmer know of the problem. It's not nice of the app to require 755 because it cannot be set with umask and it can also be a potential security problem.

Good luck with your script.

---

