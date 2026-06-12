---
title: "Deleting empty folders"
date: 2008-08-24
forum: General Help
---

### Post by rabidg00se on 2008-08-24
Is there a command or utility that will scan a directory and delete all empty folders (or, say, all folders with a total filesize of less than 3MB, etc)? I'm planning on restructuring my music collection automatically, but that will probably leave me with a bunch of empty folders that I can see getting very annoying.

Edit: I just found a similar thread (looks like I had searched for 'delete' instead of 'deleting'--sorry!) involving scripts, which I unfortunately have no idea about. If that's the only solution, can anyone give me advice with that?

---

### Post by Elfy on 2008-08-24
Maybe help to put the link here to the thread you're talking about.

---

### Post by aloshbennett on 2008-08-24
You could call rmdir recursively on all files and folders.
It would leave files and non-empty directories alone.

---

### Post by lukjad on 2008-08-24
I don't think that you want to go randomly deleting files or folders. I would suggest that if they are empty and you did not create them, leave them where they are. I always get skittish when someone asks how to automatically delete files and folders. 

If you need get some extra space try these commands:

```
sudo apt-get clean
```
```
sudo apt-get autoclean
```

---

### Post by bodhi.zazen on 2008-08-24
rm -rf directory_to_delete

rmdir directory_to_delete

With the second command the directory must be empty, so the first is easier.

---

### Post by rabidg00se on 2008-08-24
Here's the thread I was talking about: [http://ubuntuforums.org/showthread.php?t=869955&highlight=deleting+empty+folders](http://ubuntuforums.org/showthread.php?t=869955&highlight=deleting+empty+folders)

lukjad, don't worry, I'm only trying to delete folders in ~/Music, all of which I imported. I don't know all that much about Ubuntu, but I know better than to mess around with deleting stuff all willy-nilly.

rmdir sounds promising. If I ran "rmdir ~/Music" would it only check the contents of ~/Music, or would it check every folder within it?

"rm -rf ~/Music" would just delete the folder and everything in it, wouldn't it?

---

### Post by lukjad on 2008-08-24
Phew! I just had to make sure. I hear these horror stories about people deleting all of their "useless" files. Did not want that to happen to you.

---

### Post by aloshbennett on 2008-08-24
> find ~/Music * -type d | xargs rmdir

It would delete all empty folders (but wouldnt work for parent folders containing only empty folders)

Btw, use at own risk :D

---

### Post by bodhi.zazen on 2008-08-24
> **aloshbennett said:**
> It would delete all empty folders (but wouldnt work for parent folders containing only empty folders)

Btw, use at own risk :D

That is what the -p flag is for :twisted:

rmdir -p a/b/c == rmdir a/b/c a/b a

---

### Post by rabidg00se on 2008-08-24
So to recap: ```
find ~/Music * -type d | xargs rmdir
``` would find every empty directory in ~/Music and delete it (as in, ~/Music/[Directory], right? What if I were to use ```
find -d ~/Music * -type d | xargs rmdir -p
```

Would that go down into subdirectories first, delete empty ones, and then go up in the hierarchy, eventually leaving me with no empty folders anywhere in the chain?

---

### Post by bodhi.zazen on 2008-08-24
```
find ~/Music/* -type d -exec rmdir '{}' \;
```

---

### Post by panayk on 2008-08-24
> **rabidg00se said:**
> So to recap: ```
find ~/Music * -type d | xargs rmdir
``` would find every empty directory in ~/Music and delete it (as in, ~/Music/[Directory], right? What if I were to use ```
find -d ~/Music * -type d | xargs rmdir -p
```

Would that go down into subdirectories first, delete empty ones, and then go up in the hierarchy, eventually leaving me with no empty folders anywhere in the chain?

That wouldn't have the effect you expect, and could be dangerous.

```
find -d ~/Music * -type d | xargs rmdir -p
```

Bash would expand * to the non-hidden files/directories in your current directory and pass them to find, that would interpret them as additional starting points for its search. So for example you could be deleting all empty folders under ~/Desktop too. But other than that, yes:

```
find ~/Music -depth -type d | xargs rmdir
```

---

### Post by rabidg00se on 2008-08-24
> **panayk said:**
> 
 But other than that, yes:

```
find ~/Music -depth -type d | xargs rmdir
```

Alright, thanks a lot. I'll try this as soon as Quod Libet finishes structuring it...should only be about 12 hours now.

---

