---
title: "Problem sharing with samba(failed to mount windows share)"
date: 2008-10-02
forum: General Help
---

### Post by linuxgr on 2008-10-02
Hi everybody!

I have this problem which suddenly occured(did not have it before).

I have 3 computers (1 PC & 2 Laptop) connected to a network, all ubuntu hardy. Each one has a share which I can access without need of authentication (guest) except of the PC which I cannot access at all, even through the same computer by going to Places->Network. The error message:

"Unable to mount location. Failed to mount Windows share"

Tried a lot of stuff like copying smb.conf from the laptops which experience no problem but no luck. I also added a share called "test" by right-clicking on a folder and selecting "Sharing Options"(the other folders are manually written in smb.conf). 

I noticed when I play with "security = share/user", the problem consists with all folders with =share, but when it is configured to =user same problem for all except for "test" share which requires authentication(even though I selected "guest access").

It's all weird, I know, any ideas?

(again, that suddenly happened, wasn't always like that and I don't recall messing with anything related to samba)

---

### Post by linuxgr on 2008-10-03
Anyone? Any ideas welcome, I've been trying for days......

---

### Post by linuxgr on 2008-10-04
Yesterday I also tried to completely remove all samba-related packages and then re-install them. The problem consists, I can access other computers but others can see but not access my PC. Is it possible for some other application to be responsible?

---

### Post by linuxgr on 2008-10-04
SOLVED!!!!! 

even though permissions to the files were correct, I had changed the access of others to my home folder from "access files" to "no access". I noticed that when I created a share on my second hard drive instead in my home folder, which worked.

I'm posting the solution in case someone has the same problem.

---

### Post by FokkerCharlie on 2008-10-26
Phew!

I had been struggling with this for a couple of days.  I was unable to access my shared folders from a PC with XP on it over wireless, but got around the problem by creating a shared folder in /home/ .

This, however, means that it's not possible to share a folder within a user's home folder without exposing all of the contents of my home, doesn't it?  Or am I missing something?

Charlie

---

### Post by Nepherte on 2008-10-26
Yes, that is possible. But it beats the whole purpose of having a personal home folder if you ask me. And just in case you missed something in the configuration, you better don't want people to be able to access your personal folder.

---

### Post by FokkerCharlie on 2008-10-26
Hmmm.  I see.

There's not a lot of documentation on this subject- so can you tell us, what is the classical thing to do with one's shared folder?  Make one in /home?  Or something else?

Charlie

---

### Post by Nepherte on 2008-10-27
There are some "logical" places to put a share. You can for example create a /home/shared or /home/public directory. If it's an entire disk you want to share and not the disk where / is put on, they are typically mounted in /media/somemountpoint. But there's no such thing as one fixed agreement on where to put a share.

That being said, you don't want to share system folders such as /bin, /usr, /opt, /var, /etc. Those are vital for your system. Considering the often private data in /home/username, I wouldn't share any of those either.

---

