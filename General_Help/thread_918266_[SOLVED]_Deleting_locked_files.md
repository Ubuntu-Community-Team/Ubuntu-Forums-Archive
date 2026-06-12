---
title: "[SOLVED] Deleting locked files"
date: 2008-09-12
forum: General Help
---

### Post by kelpie_canada on 2008-09-12
Hi everyone, I am back again with another question that probably has a very simple answer.

Normally I use discs that can be re-written to. I was given a read only disc and when I loaded it into my system I automatically transfered the file to my home folder. Now I have a file that has a lock on it and I don't know how to delete it from my system.

Any ideas and help would be greatly appreciated.

Katie

---

### Post by benerivo on 2008-09-12
```
sudo rm /home/ben/joker.gif
```

---

### Post by ordaide on 2008-09-12
And if that happens again and you just want to modify the file, 

Right click, select properties, then permissions, and mod away the restrictions in the menu.

---

### Post by kelpie_canada on 2008-09-12
> **benerivo said:**
> ```
sudo rm /home/ben/joker.gif
```

Am I to assume that this code is to be put in at the terminal?

If it is I have never used the terminal before. This is my first computer and I have only had it since June. I am not sure how to use the terminal.

Katie

---

### Post by kelpie_canada on 2008-09-12
> **ordaide said:**
> And if that happens again and you just want to modify the file, 

Right click, select properties, then permissions, and mod away the restrictions in the menu.

That was the first thing that I tried to do. It wouldn't let me change the permission even thought it is my file that is on the disc.

Katie

---

### Post by benerivo on 2008-09-12
> **kelpie_canada said:**
> Am I to assume that this code is to be put in at the terminal?
KatieOh yes, sorry. Please enter this in the terminal (replacing my file location with your own)

---

### Post by kelpie_canada on 2008-09-12
> **benerivo said:**
> Oh yes, sorry. Please enter this in the terminal (replacing my file location with your own)

I followed your directions and I keep getting 'no such file or directory'.

What am I doing wrong? I know that the folder exists because I can open it.

Katie

---

### Post by iaculallad on 2008-09-12
> **kelpie_canada said:**
> I followed your directions and I keep getting 'no such file or directory'.

What am I doing wrong? I know that the folder exists because I can open it.

Katie

On your terminal (Applications->Accessories->Terminal):

```
sudo rm ~/filename.ext
```

Replace **filename.ext** with the filename you see on your /home folder with a padlock on it.

Or if it's a folder, try doing:

```
sudo rm -r ~/Folder_Name
```

Replace **Folder_Name** with the folder's name you want to delete.

---

### Post by kelpie_canada on 2008-09-12
> **iaculallad said:**
> On your terminal (Applications->Accessories->Terminal):

```
sudo rm ~/filename.ext
```

Replace **filename.ext** with the filename you see on your /home folder with a padlock on it.

Or if it's a folder, try doing:

```
sudo rm -r ~/Folder_Name
```

Replace **Folder_Name** with the folder's name you want to delete.


I followed your directions for a folder and I got the same message: cannot remove...'no such file or directory'

What am I doing wrong?

Katie

---

### Post by iaculallad on 2008-09-12
If you could see the folder in your home directory (w/c we can't so we just suggested variable names), you could just use the command below. Just be careful of what you delete.

```
gksudo nautilus
```

Nautilus window will display, just browse your home directory and delete the folder with a padlock symbol.

---

### Post by ordaide on 2008-09-12
'alt + F2'

in the dialog box type

'gksudo nautilus' enter

 password - enter

after a few seconds a gui (window) will pop up;

*Caution - this is root gui -YOU CAN SCREW THINGS UP HERE SO BE CAREFULL!

ok, navigate to the file in question through the new window.

Highlight the file or folder in question and press the delete key.

click 'yes I want to delete'

close the window

Finished - I hope  :)

---

### Post by kelpie_canada on 2008-09-12
> **iaculallad said:**
> If you could see the folder in your home directory (w/c we can't so we just suggested variable names), you could just use the command below. Just be careful of what you delete.

```
gksudo nautilus
```

Nautilus window will display, just browse your home directory and delete the folder with a padlock symbol.

As  I have mentioned this is my first computer and I have only had it since June of this year. 

So am I to assume that I type this code into the terminal?

Katie

---

### Post by iaculallad on 2008-09-12
> **kelpie_canada said:**
> As  I have mentioned this is my first computer and I have only had it since June of this year. 

So am I to assume that I type this code into the terminal?

Katie

Yes, you could do it on the terminal.

---

### Post by kelpie_canada on 2008-09-12
I went to the terminal and entered what you suggested and got the following:

 (nautilus:31596): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS
--- Hash table keys for warning below:
--> file:///
(nautilus:31596): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:31596): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
seahorse nautilus module shutdown

I have no idea what this means. What have I done wrong?

Katie

---

### Post by mc4man on 2008-09-12
you didn't do anything wrong. 
It would be easier to go back and use this
> sudo rm -r ~/Folder_Name

Does your folder have 2 or more words? If so notice the _ between words or use ' ' on either side of the name.

Ex.
sudo rm -r ~/[COLOR="Red"]'[/COLOR]untitled folder[COLOR="Red"]'[/COLOR]  or
sudo rm -r ~/untitled[COLOR="Red"]_[/COLOR]folder

note - red is just to point out to you

Or just post the exact name as it appears in home folder and will give you a command you can copy and paste into a terminal

---

### Post by kelpie_canada on 2008-09-12
> **mc4man said:**
> you didn't do anything wrong. 
It would be easier to go back and use this


Does your folder have 2 or more words? If so notice the _ between words or use ' ' on either side of the name.

Ex.
sudo rm -r ~/[COLOR="Red"]'[/COLOR]untitled folder[COLOR="Red"]'[/COLOR]  or
sudo rm -r ~/untitled[COLOR="Red"]_[/COLOR]folder

note - red is just to point out to you

Or just post the exact name as it appears in home folder and will give you a command you can copy and paste into a terminal


I tried this command again and got the same message: cannot remove...

The folder is 'Patterns' and inside is another folder called 'patterns'.
Only the first folder has a lock on it, but if I try to delete the second folder I am told I do not have permission.It is located in 'Documents'

I am becoming very frustrated with the whole thing because I don't have any idea as to what I am doing.

Katie

---

### Post by mc4man on 2008-09-12
Run from the terminal (copy and paste these commands
```
cd Documents
```

followed by
```
sudo rm -r Patterns
```

this is what you'll see in terminal  (and the folder Patterns and everything inside will be gone

> doug@doug-desktop:~$ cd Documents
doug@doug-desktop:~/Documents$ sudo rm -r Patterns
[sudo] password for doug: 
doug@doug-desktop:~/Documents$ 

---

### Post by kelpie_canada on 2008-09-12
> **mc4man said:**
> Run from the terminal (copy and paste these commands
```
cd Documents
```

followed by
```
sudo rm -r Patterns
```

this is what you'll see in terminal  (and the folder Patterns and everything inside will be gone

Thank you so very much. The folder has now been deleted. How can I repay you for taking the time to explain how to do this to me?

Katie

---

### Post by mc4man on 2008-09-12
well i think it would be good if you understand what you did. (note - directory and folder mean the same thing

when you open up a terminal you are at the home dir. prompt

> doug@doug-desktop:[COLOR="Red"]~$[/COLOR] 
you were trying to run a command on a folder named Patterns, but it's not in the home directory, it's in the Documents directory.

cd means change directory, so by running that your prompt changed to this
> doug@doug-desktop[COLOR="Red"]:~/Documents$[/COLOR] . 
Now the command worked because a folder named Patterns **is** in that directory

The rm means remove
the -r is used on folders and also says to execute the  command on everything inside of that folder (recursive)

---

### Post by kelpie_canada on 2008-09-12
I learn something new every time I use this system.

This is the first time that I have had the courage to use the terminal. Now I know it is not a frightening as I thought it would be. I have several books on Ubuntu but they are for three upgrades back so they don't always give me accurate information.

I really am trying to understand the powerful system that I have. It just takes time to learn all of it.

Thank you again for the lesson.

Katie

---

