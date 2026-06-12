---
title: "My sister is a retard."
date: 2008-08-31
forum: General Help
---

### Post by lakotajames on 2008-08-31
I don't know how she did it, but she has screwed up her account severely.  No sound works except for in totem movie player.  Sound juicer will not start, neither will vlc. Things close by themselves at random.  Her background changed itself to solid green. Firefox crashes often.  I have none of these problems on my account, and I don't see how she screwed everything up with out sudo privileges.  Is there a way to reset all of the settings that she could have changed to default?

---

### Post by simons-photography on 2008-08-31
maybe she is more of a geek than you have you asked her what she's been doing ? perhaps just delete her account and start again

---

### Post by sstusick on 2008-08-31
I'd backup her files and just create a new account for her, it be easier than trying to figure out what she did.

---

### Post by mb_webguy on 2008-08-31
First of all, can she sudo?  If not, back up all of the configuration files in her home directory, then delete the originals and see if things are any better.  If she has problems on her account and yet you don't have them on yours on the same computer, the fault can most likely be found in her local configuration files.

If she can sudo, then it's possible, however unlikely, that she's done something on a system level that only affects her account, such as changing permissions on certain files or directories.  In that case, it's probably best to back up her files, delete her account, and create a new one.

---

### Post by lakotajames on 2008-08-31
She can't sudo, I said that in my first post.  So, should I just delete all of the folders starting with a period in her home folder after backing them up?  Will she still be logged in?  I thought about just erasing the account and making a new one from scratch, but she doesn't want to loose her music, and I would like to avoid moving around a 5gb folder of music.

---

### Post by simons-photography on 2008-08-31
so how longs 5 Gb of music going to take to move ?

---

### Post by lakotajames on 2008-08-31
Actually, I don't know.  I assumed it would take awhile.  But if I can get away with deleting all the hidden folders, I'd rather do that.

---

### Post by sloggerkhan on 2008-08-31
What I would do is get rid of every dot file (.*) and (.*) directory in her folder that isn't associated with a critical program (like possibly her emails or something else that might have documents stored in its .folder or which has settings that it would be a pain to replace).

When she logs back in, new .files will replace the old ones that are the most likely cause of problems since she doesn't have sudo access.

---

### Post by jolx on 2008-08-31
5 gig wont take long at all

and it would probably(imo) be easier to back up all her files and make a new account, rather than try to fix whatever she screwed up

---

### Post by Sef on 2008-08-31
I don't think she did it since she didn't have sudo priviliges.  It sounds more like something caused a crash.

---

