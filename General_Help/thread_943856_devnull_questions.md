---
title: "/dev/null questions"
date: 2008-10-10
forum: General Help
---

### Post by brandon88tube on 2008-10-10
1.First of all I want to know if anything sent to /dev/null is kept anywhere or is readable after being sent there. I did some searches and it says that it doesn't do anything, but the information wasn't that clear.

2.I want to redirect two folders to go to /dev/null so that anything sent to that folder would be sent to /dev/null instead. How would I go about doing this? I've searched and cannot figure this one out.

---

### Post by Sam on 2008-10-10
> **brandon88tube said:**
> 1.First of all I want to know if anything sent to /dev/null is kept anywhere or is readable after being sent there. I did some searches and it says that it doesn't do anything, but the information wasn't that clear.
Anything sent to /dev/null "disappear". Imagine this as a black hole. Impossible to recover.

> **brandon88tube said:**
> 2.I want to redirect two folders to go to /dev/null so that anything sent to that folder would be sent to /dev/null instead. How would I go about doing this? I've searched and cannot figure this one out.
Hum I don't know if it's possible...

Why don't you do a regular deletion of your files instead of moving them in that directory ?

---

### Post by geirha on 2008-10-10
> **brandon88tube said:**
> 1.First of all I want to know if anything sent to /dev/null is kept anywhere or is readable after being sent there. I did some searches and it says that it doesn't do anything, but the information wasn't that clear.

It's gone, incinerated, fallen into the void, or whichever metaphor you prefer.

> **brandon88tube said:**
> 2.I want to redirect two folders to go to /dev/null so that anything sent to that folder would be sent to /dev/null instead. How would I go about doing this? I've searched and cannot figure this one out.

You can't really. What you'd do instead is have a cron script that checks the folder every now and again, and deletes files there, or have a process run in the background continuously polling the directory and deleting whenever new files appear.

---

### Post by brandon88tube on 2008-10-10
I found a post by someone, but I don't know how to do this. Can you explain?

****If you run Linux create the following and nothing will ever be stored or saved:

in /home/~/.macromedia/Flash_Player create #SharedObjects and point it to /dev/null
in /home/~/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys create #* and point it to /dev/null

This method also preserves your /home/~/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/settings.sol

The above locations may vary depending on distro.*****

---

### Post by Sam on 2008-10-10
You can create a file that point to /dev/null with a symlink:
```
ln -s /dev/null ~/vacuum
```
However you cannot drag'n'drop anything to this "file" in nautilus. It's commonly used if you don't want something to be written in a file.
Example: Making a symlink of ~/.bash_history to /dev/null will disable the history in bash because everything written in that file is sent to /dev/null.

Hope this helps.

---

### Post by brandon88tube on 2008-10-10
So would this command be correct then if I wanted to do as the example I gave? ln -s /dev/null /home/username/.macromedia/Flash_Player/#SharedObjects
& ln -s /dev/null /home/username/.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys

---

### Post by Sam on 2008-10-10
Absolutely.

---

### Post by brandon88tube on 2008-10-10
Thanks! :D  Going to try this out and see how it goes.

---

### Post by ilrudie on 2008-10-10
> **Sam said:**
> You can create a file that point to /dev/null with a symlink:
```
ln -s /dev/null ~/vacuum
```However you cannot drag'n'drop anything to this "file" in nautilus. It's commonly used if you don't want something to be written in a file.
Example: Making a symlink of ~/.bash_history to /dev/null will disable the history in bash because everything written in that file is sent to /dev/null.

Hope this helps.

Good call on the sym link.  You beat me to it.

---

### Post by brandon88tube on 2008-10-10
Well, it didn't come out as I was hoping. Instead it made a file called null located in that folder. What I ended up doing was taking that file and renaming it to #SharedObjects and then the other one I name #* This seems to have worked, but if I wanted to do this in the future is there a way of doing this without having to rename those files etc?

---

### Post by Sam on 2008-10-10
Because the destination existed as a folder. So the symlink was created in it with its original name.

```
ln -s /dev/null ~/test
```
If test is a directory, a symlink named "null" will be created in.
If test doesn't exists, the symlink will be called "test".


You must either delete or move elsewhere these directories, then make the symlinks.

---

### Post by brandon88tube on 2008-10-10
> **Sam said:**
> Because the destination existed as a folder. So the symlink was created in it with its original name.

```
ln -s /dev/null ~/test
```
If test is a directory, a symlink named "null" will be created in.
If test doesn't exists, the symlink will be called "test".


You must either delete or move elsewhere these directories, then make the symlinks.

Ahh, ok I think I understand now. Thanks again :D

---

### Post by sokopok on 2008-10-10
ln -s /dev/null '/home/username/.macromedia/Flash_Player/#SharedObjects'
note the single quotes (# and *) are reserved characters in the shell

---

### Post by brandon88tube on 2008-10-11
> **sokopok said:**
> ln -s /dev/null '/home/username/.macromedia/Flash_Player/#SharedObjects'
note the single quotes (# and *) are reserved characters in the shell

I didn't seem to need the single quotes as it worked without them.

;( I later found out that this somewhat works, but makes it so I can't watch any flash videos etc. If anyone knows a better method to have flash NOT store its cookies on my hard drive while still allowing me to view flash videos etc., please share. *Shakes fist at Adobe

---

