---
title: "Trash is broken"
date: 2008-11-05
forum: General Help
---

### Post by illbashu on 2008-11-05
Everytime i add trash to the bar at the top it doesn't show the icon but when u click in the genral area it opens up trash and it says 

```
Sorry, couldn't display all the contents of "trash": Operation not supported
```

---

### Post by illbashu on 2008-11-07
Bump!

---

### Post by illbashu on 2008-11-11
bump

---

### Post by illbashu on 2008-11-18
BUMP! i need trash working! someone help!!!11!!

---

### Post by Awareness on 2008-11-18
What does "add trash to the bar" mean?

and what is that "general area"?

---

### Post by 420shaggy on 2008-11-18
I would try reinstalling Ubuntu and see if that works.  Or if you really don't want to do that, try this:

> 

Hello guys, i had to suffer under this ******* update as well. I spent hours n front of my computer, downgraded gvfs, reinstalled it, reinstalled nautilus over and over again-- nothing worked.

But now I got it working! nautilus will handle computer: , network: and trash: correctly. The only thing that got it for me was downgrading bth gvfs and gvfs-backends to version 0.2.3-0ubuntu3.
(0.2.3-0ubuntu4 is the version in the hardy repo, 0.2.5-0ubuntu2 the one in hardy-updates.)
I used the download page from launchpad, you can also search for the packages there (debs available):
gvfs-backends 0.2.3-0ubuntu3:
  [https://launchpad.net/ubuntu/hardy/amd64/gvfs-backends/0.2.3-0ubuntu3](https://launchpad.net/ubuntu/hardy/amd64/gvfs-backends/0.2.3-0ubuntu3)
gvfs 0.2.3-0ubuntu3:
 [https://launchpad.net/ubuntu/hardy/amd64/gvfs/0.2.3-0ubuntu3](https://launchpad.net/ubuntu/hardy/amd64/gvfs/0.2.3-0ubuntu3)
then download the debs. if you don't get your native package manager to install them because you have a newer version installed, type the following into a console:
sudo dpkg -i PATH\ OF\ DEB-FILE\

I hope it works for you. Remember not to update these files ever....
I'm so happy now!! Good luck to all of you as well with this problem..


---

### Post by illbashu on 2008-11-19
i have both already installed :/

---

### Post by illbashu on 2008-11-23
BUMP!
this is what it says when i click on the trash icon in file manager

"Sorry, could not display all the contents of "trash": Operation not supported"
----

bar= panel 
genaral area is where the trash icon should be but its not there, but you can still click in that area and it will try to open trash and say "Sorry, could not display all the contents of "trash": Operation not supported"

---

### Post by bigbrovar on 2008-11-23
if you are on hardy heron or ibex open terminal  and try this 
```
mkdir -p $HOME/.local/share/Trash/file
```
 then this 

```
mkdir -p $HOME/.local/share/Trash/info
```

---

### Post by illbashu on 2008-11-23
THX!~ the panel trash wont work still but that folder (/home/bash/.local/share/Trash/files) has all my trashed item in it so i will just make a shortcut to it on my desktop!
-----
edit, i have a prob now. i know where all my deleted files are going but it wont let me delete them from that folder, because they are just being sent back to that folder, like it thinks that its just a folder but its actully trash so it just keeps getting sent back there :/

---

### Post by earthpigg on 2008-11-23
> like it thinks that its just a folder but its actully trash so it just keeps getting sent back there :/

right click -> permanently delete?

---

### Post by drs305 on 2008-11-23
> **illbashu said:**
> 
edit, i have a prob now. I know where all my deleted files are going but it wont let me delete them from that folder, because they are just being sent back to that folder, like it thinks that its just a folder but its actully trash so it just keeps getting sent back there :/

**shift-delete** if you are doing it from a gui file browser.

---

### Post by illbashu on 2008-11-24
Thx!

---

### Post by illbashu on 2008-11-24
nm....

---

### Post by beanpop on 2009-06-22
I know that this thread is long dead, but I am having the same problem and have done everything listed in this post. Yeah, it's all fine and dandy that I know how to get to where my trash is mysteriously going but I really am not a fan of half assed fixes.

The fact that I have found almost 30 different posts on multiple websites and forums regarding this SAME EXACT issue and that no one knows seems to how to fix it really disturbs me.  There has to be at least ONE PERSON on these forums that knows how to ACTUALLY fix this problem.

If you need more information on my problem I posted a long explanation in two different subforums that I would be more than happy to link you to.

---

### Post by pirog on 2010-02-01
Dude you are right, IF MY WASTE BASKET CONTAINS ANYTHING then it WON'T open and then desktop space freezes. Unless I empty it by right-click it won't open!

there must be SOMEONE out there to help us!

---

### Post by drs305 on 2010-02-01
> **pirog said:**
> Dude you are right, IF MY WASTE BASKET CONTAINS ANYTHING then it WON'T open and then desktop space freezes. Unless I empty it by right-click it won't open!

there must be SOMEONE out there to help us!

Just curious - what are the results of this command, which shows ownership/permissions:
```
ls -la $HOME/.local/share/Trash/files
```

---

### Post by pirog on 2010-02-07
> **drs305 said:**
> Just curious - what are the results of this command, which shows ownership/permissions:
```
ls -la $HOME/.local/share/Trash/files
```

Hi drs305,

Sorry, I forgot to subscribe to the post :)
Well, I think you are suggesting whether I have any write/access restrictions. I am sure that i have some text files created by root, but I don't think this is an issue.
My friend doesn't really use sudo to open anything or create anything, it just stopped working after an update, but it does not seem to be a global issue.

Anyways, here is the output: [http://pastebin.com/m286840d](http://pastebin.com/m286840d)

---

### Post by drs305 on 2010-02-07
pirog,

There are files owned by root in the user's trash bin. It shouldn't be the cause of what is occurring, but I would try removing them to see if it changes the behavior of the Trash bin. The safest way is probably just to open Nautilus as root (disregard the terminal error messages it produces) and use SHIFT-DEL to permanently remove the files from the trash. (If you just use DEL, they will return to a trash bin).

```
gksu nautilus ~/.local/share/Trash/files
```

---

### Post by pirog on 2010-02-07
> **drs305 said:**
> pirog,

There are files owned by root in the user's trash bin. It shouldn't be the cause of what is occurring, but I would try removing them to see if it changes the behavior of the Trash bin. The safest way is probably just to open Nautilus as root (disregard the terminal error messages it produces) and use SHIFT-DEL to permanently remove the files from the trash. (If you just use DEL, they will return to a trash bin).

```
gksu nautilus ~/.local/share/Trash/files
```

that's the thing, i've done all of that to no avail. as i can recall, the whole thing went badly after i started opening Nautilus through gksudo. I'll report back after I have another go at it.

---

