---
title: "Share folder on 1 computer between 2 users"
date: 2008-07-20
forum: General Help
---

### Post by riseringseeker on 2008-07-20
I have searched these and other Linux forums and have googled to no avail.  What I am searching for is to be able to share a folder on one machine (running 8.04) between two users.  All my searches have revealed how to share between machines, not on a single machine.  (I use rsync, scp and ssh regularly and know how they are done.)  I also have no need or desire to share anything via samba, as we have no windows machines.

What I would like to do is to have "User A" and "User B" both be able to have unrestricted access to a folder - for example, a photo collection.  By unrestricted I mean that I want both users to be able to read, edit, add and/or delete files, and have all of them accessible to the other user as if that user had manipulated them in any way - added or edited them - in this case mostly with TheGimp.  (I would like to do the same with music files, but let's stick with photos for now)

I have tried to make a "/home/our" directory giving it 770 permissions, and having the owner be User A and the group be User B, or making the group be "photos" (both Users being a member of that group).  This will work until one or the other adds or edits one of the files, then that/those files are locked for the other user as they are added or saved using the ownership and group of the user adding/editing.

I can (and have) sudo'd the ownership to change the files back to being fully accessible by both, but it's a pain, and I would like to not have to go to a terminal each time a change is made to one of the files. 

I would be somewhat surprised if this cannot be done, but not in total shock if it can't.  

Anyone have any ideas?

---

### Post by RealPSL on 2008-07-20
You need to change 2 additional things. First you need to apply the setgid bit on the directory you are sharing. This will ensure that all future files (and directories) created in the directory will maintain the same group as the parent. You can do this with ```
sudo chmod g+s shared_directory_name
```

The second thing you need to do is change the umask for the users sharing the directory to 007. You can use 002 if you want to give others read but that is "not secure".

You can change the umask by adding the line ```
umask 007
``` to the .profile in your home directory with ```
gedit /home/some_user/.profile
```. This will take effect when the user logs out and back in.

---

