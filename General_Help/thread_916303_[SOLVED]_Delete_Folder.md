---
title: "[SOLVED] Delete Folder"
date: 2008-09-10
forum: General Help
---

### Post by elkade on 2008-09-10
I have a folder on my desktop that has a padlock in the upper right corner of the folder.  I am trying to delete the folder, unable to do so.

I get this when I try to move to trash:  Cannot move file to trash, do you want to delete immediately?
The file "User Names Passwords" cannot be moved to the trash.
My options are:
cancel skip all skip delete all delete
When I click on delete, I get this option

Error while deleting.
There was an error deleting usernamespasswords.xls
Show more detials
error removing file: Permission denied

Xcancel skip all skip

Sure could use some help

Thanks,

Larry

---

### Post by Predator106 on 2008-09-10
Not sure how it got there, but it was probably something from root, either way, to solve it in the terminal, do the following:

(I'm assuming you are using Ubuntu, of course).
'sudo nautilus /home/Your_User_Name/Desktop'

Remember, Linux is case-sensitive, so make sure you have it right, I'm not sure if it's Desktop or desktop, I think it's the former.

Anyways, this should bring you to the desktop, this is by the way, just to let you know, running Nautilus, the GNOME file manager (like Windows explorer) in root (high permission-mode), so you will be able to delete EVERYTHING in this Windows. Delete the folder them, make sure you do Shift+Delete, as sending to trash could cause some problems (I've had them happen before). Since root would be sending it to your trash(I think it sends it to your trash), you wouldn't be able to get it out without logging into root, and root can't access the trash easily, so basically... just remember to Shift+Delete it. You can also right click and goto the permissions and set read/write/create/delete access to everyone/'Others'.

Remember to close out of the window, and not do anything else, if you start moving things around i.e. system files, you can screw it up easily (obviously). Also don't move around too many of your files, because permissions _can_ get changed and will require a few keystrokes or so to get them back (or mouse gestures).

Hope this helps...

---

### Post by elkade on 2008-09-10
> **Predator106 said:**
> Not sure how it got there, but it was probably something from root, either way, to solve it in the terminal, do the following:

(I'm assuming you are using Ubuntu, of course).
'sudo nautilus /home/Your_User_Name/Desktop'

Remember, Linux is case-sensitive, so make sure you have it right, I'm not sure if it's Desktop or desktop, I think it's the former.

Anyways, this should bring you to the desktop, this is by the way, just to let you know, running Nautilus, the GNOME file manager (like Windows explorer) in root (high permission-mode), so you will be able to delete EVERYTHING in this Windows. Delete the folder them, make sure you do Shift+Delete, as sending to trash could cause some problems (I've had them happen before). Since root would be sending it to your trash(I think it sends it to your trash), you wouldn't be able to get it out without logging into root, and root can't access the trash easily, so basically... just remember to Shift+Delete it. You can also right click and goto the permissions and set read/write/create/delete access to everyone/'Others'.

Remember to close out of the window, and not do anything else, if you start moving things around i.e. system files, you can screw it up easily (obviously). Also don't move around too many of your files, because permissions _can_ get changed and will require a few keystrokes or so to get them back (or mouse gestures).

Hope this helps...

Thanks for the effort.  I went back to the file and did a little tinkering.  I found by altering permissions, the padlock on the folder was removed, and then I was able to send the folder to trash.

Thanks again for the quick reply.  I am a newbie and should have tinkered a little bit more before going into panic mode.
Larry

---

### Post by Predator106 on 2008-09-11
Good, glad I could help. Don't forget to hit the thank button on my post(it's a military-kind-of-medal).

---

