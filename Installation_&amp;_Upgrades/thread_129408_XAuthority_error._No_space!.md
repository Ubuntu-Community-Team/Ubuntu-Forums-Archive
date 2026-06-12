---
title: "XAuthority error. No space!??"
date: 2006-02-13
forum: Installation &amp; Upgrades
---

### Post by executex on 2006-02-13
Ok whenever i try to launch linux, it will say "XAuthority error: could not write to xaauthority file. This could be because no free space, or no write permissions to home folder."

I get this everytime i try to launch Linux. I can only use Linux recovery mode with ubuntu.

The ubuntu installer only allowed me to take out 2 GB of space, because i didn't know i was suppose to defrag my partition, since no one thought of telling me this. So once partitioned, i couldn't launch windows, so i guess i cant free up more space from my 110 GB NTFS WinXP drive. So my Win XP is dead.

And now i tried downloading flash player last night, and suddenly things started shutting down I thought maybe i should restart. Didn't know it would not let me back in after that. Now i only have access to bash or whatever.

I do df -h, and it says 1.9 GB drive of linux is full. 100%. However, i tried deleting a big folder with a bunch of programs in it. That must have freed atleast 50 mb... But it doesn't show of course. And so i am not sure what to do. Is there anyway i can access this Xauthority file, and modify it, or something? How can i fix this?

How can i see how many MBs are free... Not GB, cuz i can't see if there is any space on the MB level.

So anyway, i'm stuck, can't access windows or ubuntu, and i'm starting to regret ever trying. Any help??? or ideas on how to fix this Xauthority file error?

EDIT: The exact error:
[quote=GDM]GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact the system administrator.[/quote]
Doesn't it suck when you are the system administrator????

---

### Post by executex on 2006-02-13
UPDATE: 
Ok, this GDM won't start error is beggining to bug me.
I did some research. I checked incase my folders were wrong or something.
I checked the CHMOD and drwxrwxrwx lines for my /home/<username>/ folder, and i have permission, 644, otherwise it gives me error if i try to give more permission saying "recommended at 644", if i change to 777 or something, the GDM error still stays, but i get extra warnings when logging in. So it's not a permission issue. I even set the owner with chown, of /home/<username>/ as my <username>.
I tried creating a file, adding text to it with nano, and then saving it. And it worked out fine. It didn't say disk is full or anything.

So i just eliminated two of the biggest causes of this. And cornered myself ino an unsolvable bug case. Is this a bug then???

---

### Post by executex on 2006-02-13
UPDATE: Half-Way fixed.

I looked at permissions, and i fixed all those problems with no  result.

I had deleted many files before, but i guess they were really small, because df -h kept saying 100% full.

So finally i found a link: [http://www.ubuntuforums.org/showthread.php?t=90361](http://www.ubuntuforums.org/showthread.php?t=90361)
And got this command: apt-get clean
When i did this in recovery console
and then did 
df -h.

It said 89% full. So it cleared 200 mb!!!!!
Anyway since im talking to myself, perhaps someone will read later :O

I got another error. I mean the old error saying "GDM could not write to authorization file" went away. I was able to get into Failsafe Terminal. Which i couldn't before. 

Now it says this message when attempting to launch Gnome:
 Your session has lasted 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.

And then it has a check box to view .xsession-errors file. And in it it says it didnt have permission to make Gnome2 folder in my home/<username> folder. This may be due to my excessive playing around with chmod on my home/<username> directory. So i will see if i can solve that.
(The reason i typed all that stuff, is perhaps to help someone who may have searched a fragment of the error message in this forum :P, and i'm bored)

So i will play around with chmod some more..!! (i feel like Dave Mustaine in sweating bullets, very lonely forum :P)

UPDATE ::: I changed chmod of /home/<username>/ from 644 to 755, and it worked. Although it may be insecure now. But Gnome works WEEEEEEEEEEEEEEEEE case closed.

---

### Post by TIGRA on 2006-02-14
Hi Folks!

Had similar troubles with the lovely GDM. Got the same message after logging in. After several successless tries (Google, forums), 

I have managed to regain access via GDM. I dont know how and why it worked, but it has!

*Recovery mode -> (logged in as root) -> startx -> create new user -> restarted in normal mode*

I've been very surprised that I could log in with the new created user, and even more, as I even could log in as "old" user.

Greets,
TIGRA

---

### Post by executex on 2006-02-14
Yeah you can do that.... but not recommended... my problem was space. Some other problems may be permissions, you dont have to make a new user for that.

---

### Post by aysiu on 2006-02-14
I remember having a problem like this once when I actually did use up all the space.

Even after I deleted the offending files, I still got that error.

There may be another way to fix this, but I just did a clean reinstall (backing up important files first, of course).

---

