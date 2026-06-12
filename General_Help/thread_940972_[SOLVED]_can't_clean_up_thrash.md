---
title: "[SOLVED] can't clean up thrash"
date: 2008-10-07
forum: General Help
---

### Post by suhaib1thariq on 2008-10-07
i some how got a folder on desktop named desktop and it contains nothing ...... i intend to delete it..i send it to trash...when i clean up my thrash...its not deleting..it shows directory not empty...when i opened it in trash itself ..it contains another folder named with same desktop..and it contains another desktop folder..and it goes on.........


what is this...how to delete it from system,. i

---

### Post by jerome1232 on 2008-10-07
Do you have a symlink pointing to it's parent folder? I can duplicate what your experiencing by making a symlink to Desktop then coping it to ~/Desktop, but when I goto my trash, I just select the file and delete it. Try that.

---

### Post by suhaib1thariq on 2008-10-08
i can't understand ..please tell complete procedure

---

### Post by jerome1232 on 2008-10-08
Just left click your icon once, left click your Desktop file in there once, then press the delete key on your keyboard.


If that fails can you post the output of, then I can tell you how to remove it.
```
ls -lah ~/.local/share/Trash/files
```

---

### Post by suhaib1thariq on 2008-10-08
it is not deletin it again shown can't delete...the output of that is
suhaib@suhaib-desktop:~$ ls -lah ~/.local/share/Trash/files
total 12K
drwx------ 3 suhaib suhaib 4.0K 2008-10-09 01:17 .
drwx------ 4 suhaib suhaib 4.0K 2008-10-05 01:22 ..
drwxr-xr-x 3 suhaib suhaib 4.0K 2008-10-05 18:30 Desktop



what can i do

---

### Post by jerome1232 on 2008-10-08
Try this then;

```
rm -rfvI ~/.local/share/Trash/*
```

It's owned by you according to what you posted but failing that try this next command. Be careful sudo and rm are trouble if you misstype (rm -rf removes files, directories and their contents as super user, if used wrong it can remove everything on your system) The -v just tells you what it's removing and -I gives you a chance to review the command you entered before you commit it.

```
sudo rm -rfvI ~/.local/share/Trash/*
```

---

### Post by suhaib1thariq on 2008-10-08
both doesn't clean up trash ...both executed succesfully but not deleting that desktop folder...what's that folder.....may it be spam

---

### Post by jerome1232 on 2008-10-08
You know I had an issue similar to this a long time ago, basicaly the system for some odd reason thought my Desktop was in my trash, so everytime I deleted it it got recreated. I don't remember how I solved it. Give me a moment to look around.

---

### Post by jerome1232 on 2008-10-08
Can you post one more thing for me

```
ls -ldh ~/Desktop
```

---

### Post by suhaib1thariq on 2008-10-08
pleasure...the output of that is:

suhaib@suhaib-desktop:~$ ls -ldh ~/Desktop
drwxr-xr-x 9 suhaib suhaib 4.0K 2008-10-09 01:04 /home/suhaib/Desktop

---

### Post by Therion on 2008-10-08
Install [QuickStart](http://www.howtoforge.com/quickstart-the-swiss-army-knife-for-ubuntu-8.04-desktop).

---

### Post by jerome1232 on 2008-10-08
*maybe* this will work, I'm trying as hard as I can to recreate your problem but I can't. But maybe this will fix it for you.

Press alt+f2, type gconf-editor and hit enter

Now expand apps, expand Nautilus, click on preferences.

In the right hand panel you should have alot of stuff. 

one option should say desktop_is_home_dir, if it's not checked check it. Log out then log back in. Empty your trash.

now to put the desktop back where it belongs.

alt+f2; gconf-editor; apps->nautilus->preferences; now uncheck desktop_is_home_dir; log out then log back in see if it's fixed.

---

### Post by suhaib1thariq on 2008-10-08
i configuration editor.....there is four items in the left side...which is root for many directories  and it contains apps,desktop,scemas and system under / ......there i sno option of checking it

---

### Post by jerome1232 on 2008-10-08
apps->Nautilus->Prefences; then the right hand pane will show stuff.

---

### Post by suhaib1thariq on 2008-10-08
i am not having nautilus in applications

---

### Post by jerome1232 on 2008-10-08
I think you missunderstood me;

press alt+f2; type gconf-editor.

In the Left hand pane you should have apps, click on the arrow to the left of it, now you should have a big list below apps, find nautilus, then once again click the arrow to the left of it, a new list will drop down you should see prefrences go ahead and left click it.

Now some options should appear in your right hand pane, check the one that says default_desktop_is_home.

Logout, log back in. Empty your trash.

Then go back into gconf-editor and uncheck that option and relog see if it fixes it.

---

### Post by suhaib1thariq on 2008-10-08
that too also not working...it again ...it cannot be deleted....
error:directory is not empty

---

### Post by jerome1232 on 2008-10-08
Is that even with the command line methods?

```
rm -rfvI ~/.local/share/Trash/*

or if needed

sudo rm -rfvI ~/.local/share/Trash/*
```

---

### Post by suhaib1thariq on 2008-10-09
problem solved ......thanks for the response u showed

---

### Post by ounas on 2008-12-11
Thanks

Ounas

---

