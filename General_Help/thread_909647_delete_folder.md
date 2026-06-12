---
title: "delete folder"
date: 2008-09-03
forum: General Help
---

### Post by warlock_handler on 2008-09-03
hi i created a new folder on my desktop with the name "user ~" it gave me an error and then it creates something which seems to be like a mix breed of a file and folder... and now when i try to delete this, it gives me a file not found error, i cant even rename it... can someone help me out?

i am on a ubuntu 7.10

---

### Post by tuxxy on 2008-09-03
Open a terminal and type

```
gksudo nautilus
```

Navigate to location of the folder/file and try remove it

---

### Post by EmanresuusernamE on 2008-09-03
Be VERY careful when removing files/folders this way.
Open up a terminal and type in:
```
cd ~
cd Desktop
```
Locate the file/folder that you want to delete, and then type in:
```
rm <%Name of file/folder>
```
If it gripes about it being a folder, put "-R" after that string.
[COLOR="Red"]Make sure you are in the proper folder, and avoid using sudo if at all possible![/COLOR]
That should remove the file/folder from your desktop.

---

### Post by warlock_handler on 2008-09-04
> **tuxxy said:**
> Open a terminal and type

```
gksudo nautilus
```

Navigate to location of the folder/file and try remove it

you cannot see that folder there cause it is named with "~" at the end of the name... anyother solution?

and in the terminal also if i hit ls... that folder is never shown

---

### Post by iaculallad on 2008-09-04
Delete it with:

```
rm -r ~/Desktop/user\ ~
```

---

### Post by warlock_handler on 2008-09-04
> **iaculallad said:**
> Delete it with:

```
rm -r ~/Desktop/user\ ~
```

rm: cannot remove `/home/lock/Desktop/user ~': No such file or directory

I keep getting this, when I can see it on the desktop, i tried Sudo as well still same error

is this a problem with ubuntu 7.10???

---

### Post by cariboo on 2008-09-04
Open a terminal and type:

```
ls -la ~/Desktop
```

This should give you a listing of all the files in /home/<user>/Desktop
you should then be able to delete the file by copying and pasting the file name:

```
rm ~/Desktop/<filename>
```

Jim

---

### Post by iaculallad on 2008-09-04
> **warlock_handler said:**
> rm: cannot remove `/home/lock/Desktop/user ~': No such file or directory

I keep getting this, when I can see it on the desktop, i tried Sudo as well still same error

is this a problem with ubuntu 7.10???

Are you sure you named it as "user ~"? Or is it "User ~"? I'm on Gutsy too so that wouldn't be an existing problem/bug.

Try listing your Desktop's content with:

```
ls -la ~/Desktop
```

---

### Post by warlock_handler on 2008-09-04
> **iaculallad said:**
> Are you sure you named it as "user ~"? Or is it "User ~"? I'm on Gutsy too so that wouldn't be an existing problem/bug.

Try listing your Desktop's content with:

```
ls -la ~/Desktop
```

yes i did what you saying... and when i list my desktop, it still wont show there...

if you are on gusty then why dont u try this... on you desktop try creating a new folder and name it "test ~" it will throw an error and then the folder is created.. and why dont you try deleting it?

---

### Post by iaculallad on 2008-09-04
> **warlock_handler said:**
> yes i did what you saying... and when i list my desktop, it still wont show there...

if you are on gusty then why dont u try this... on you desktop try creating a new folder and name it "test ~" it will throw an error and then the folder is created.. and why dont you try deleting it?

It's a success on my Gutsy:

I created the directory you mentioned:

> ian@gutsy-gibbon:~/Desktop$ mkdir test\ ~

I even tried listing it with ls -la ~/Desktop (For personal reason, I'll only be posting the test ~ folder):

```
drwxr-xr-x  2 ian ian   4096 2008-09-04 15:14 test ~
```

and deleted it:

> ian@gutsy-gibbon:~$ rm -r ~/Desktop/test\ ~

and again, listing the Desktop folder content:

---We'll for personal reason, I won't be posting it, but it's gone---

I'm on Gutsy as you can see:

> ian@gutsy-gibbon:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"
ian@gutsy-gibbon:~$ 




---

### Post by warlock_handler on 2008-09-04
> **iaculallad said:**
> It's a success on my Gutsy:

I created the directory you mentioned:



I even tried listing it with ls -la ~/Desktop (For personal reason, I'll only be posting the test ~ folder):

```
drwxr-xr-x  2 ian ian   4096 2008-09-04 15:14 test ~
```

and deleted it:



and again, listing the Desktop folder content:

---We'll for personal reason, I won't be posting it, but it's gone---

I'm on Gutsy as you can see:

ok how dumb of me... pls dont beat me up...

firstly i had created it through the GUI... 
and then after trying pretty much verything i got bugged and restarted X and when i came back to desktop that file wasnt there anymore... 

sorry for the trouble

thnx everyone for the help...

---

