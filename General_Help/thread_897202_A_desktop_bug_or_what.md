---
title: "A desktop bug or what?"
date: 2008-08-21
forum: General Help
---

### Post by colobix on 2008-08-21
Hey.

When I delete files from my desktop, they doesn't actually go away.
I went to my desktop folder once and found the deleted files hidden there. But these files are invisble on the desktop.
Is this a bug or what?
ANd I am not the only one with this "problem".

---

### Post by coolaj86 on 2008-08-22
What do you mean by 'hidden'?

When you delete a file it should be moved to 

```
/home/$USER/.local/share/Trash/files/
```

and then when you empty the trash the file should be permanently deleted.

---

### Post by colobix on 2008-08-22
I mean hidden as in hidden file. When I click delete on a file at the desktop then are being copied to the trash filden and hidden from desktop, so when I go to my user filder/desktop and clicks on view hidden files I can see all the files i have deleted are not deleted, just hidden.

---

### Post by malspa on 2008-08-22
Not having this problem, but when I delete files from the desktop, I normally bypass the Trash.  When I right-click on a desktop item, I have the choice to "Move to Trash" or "Delete."  That is set up by going into Nautilus, then Edit > Preferences > Behavior tab, down in the Trash section.  You can check the box next to "Include a Delete command that bypasses the Trash."

Anyway, I tried what you said and moved a desktop file to the Trash.  Then I went into Nautilus and looked at my desktop with "Show Hidden Files" enabled, but there's nothing there.  But the file I deleted from the desktop appears in the Trash, as expected.  Sorry, couldn't replicate your "bug" here.

Edit:  One thing on my system, well when I edit a file and save it there's a backup created of the original file, and in Nautilus it appears as the file named followed by a "~" -- for example, I had a .txt file named NoInternet and when I edited it and saved it (using gedit) that created another file called NoInternet~.  Later I deleted NoInternet from the desktop but the backup file NoInternet~ was still there when I looked at the desktop directory with "Show Hidden Files" enabled.  I don't know if your situation is similar.  Once I deleted the backup file NoInternet~, it was gone for good.

---

### Post by colobix on 2008-08-22
Yup I know. I have seen that too.
But another bug with my desktop is that when I download a file to my desktop, it won't show up until, so I Have to go to my home directory/desktop and there it is.
This is so strange, and Idon't know how to fix it or why it is like that, but I guess it has something to do with my other bug about the deleted files.
And another thing is that when I insert my ipod the ipod icon comes up but won't go away when I plug out the usb.
And again, everything works fine in my desktop directory.
So I asked my self if maybe this could be a graphic bug or something like that?
I don't know.

---

### Post by colobix on 2008-08-22
Bump.
Does anymnone know what this can be?

---

### Post by coolaj86 on 2008-08-22
Did you upgrade or clean install?

---

