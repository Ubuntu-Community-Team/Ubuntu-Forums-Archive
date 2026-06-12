---
title: "Really odd partition mounting problem"
date: 2008-06-27
forum: Hardware
---

### Post by Dasani on 2008-06-27
k...this seems to be one of those problems that occur without any explicit cause in Ubuntu.

I cannot mount my 2 windows (vista and xp) partitions even though I used them extensively until only yesterday. Then, all I did was move my CPU to a new room and attach a new monitor and suddenly I cannot access those partitions. If I try to through computer:///, I see 
"You are not privileged to mount the volume 'XP SP2'."

If I run a gksudo nautilus, then I see the error "fuse failed to access mount point /media/XP SP2: No such file or directory". And if you think it's the space in the location that's the problem, then that can't be because it has worked like that for a very long time, and the same problem is occurring for my other drive which does not have any spaces in it's name. Along with that I also get a new error message in a few seconds saying 

"DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

I don't know what that means but I believe that might be the source of the problem. 

BTW, I have the correct locations down in my fstab: I did mount -a command and received the same error. And I also tried mounting it manually by creating a new mount point, didn't work.

Thanks in advance~

---

### Post by Dasani on 2008-06-29
bump...

---

### Post by linfidel on 2008-06-29
Are you using Gnome?  And, did you upgrade to Hardy since the last time you were able to access the drives?  There are some bugs with the gnome virtual file system which is being used by the new Nautilus that might be causing problems for you.

A lot of people are having problems accessing Windows shares.  I'm not able to browse the network, but I can enter a share directly and it will be mounted, by typing in the Nautilus address (places) bar:
smb://ComputerName/ShareName, where ShareName is any share, including the administrative shares like c$.  When it prompts for a password, I need to enter my Windows password.  My user name is the same on both systems.

You may be able to do it by IP address:  "smb://you@ip.address.of.computer/sharename.
To get sharenames, you should be able to type " smbclient -L ComputerName", or IP address if ComputerName isn't known (I have mine in my /etc/hosts).

Hope this helps.

---

### Post by Odrodzona-Sarmacja on 2008-06-30
Try doing "sudo chmod 777 <mount point directory>" on the directory in Ubuntu you are mounting these hard drives on. If it is just privilege issue that is, then it should be solved this way.

---

### Post by Dasani on 2008-07-01
Odrodzona, I've tried that before and tried it just now again. It does not work, I get the error that the mountpoint cannot be found.

linfidel, I had actually upgraded a while back, like I mentioned, the only difference between the mounts working and not working was me moving the PC and attaching it to a new monitor. I could try samba, but I would have to activate those partitions on shares I believe. I'm not quite sure how to do that without accessing it first.

Thanks for the help so far!

---

### Post by linfidel on 2008-07-01
> **Dasani said:**
> Odrodzona, I've tried that before and tried it just now again. It does not work, I get the error that the mountpoint cannot be found.

linfidel, I had actually upgraded a while back, like I mentioned, the only difference between the mounts working and not working was me moving the PC and attaching it to a new monitor. I could try samba, but I would have to activate those partitions on shares I believe. I'm not quite sure how to do that without accessing it first.

Thanks for the help so far!
No, sorry, I was in the midst of Samba problems accessing Windows on the network, and my brain missed the fact that you were having mount problems, not share problems.

My only suggestion would be to try it manually until you get it working; you will need to use sudo or gksudo to mount it, but it's better to do it that way than fstab.  I had problems once with a couple of missing drives in my fstab, and it would not even mount my home directory because of it, so it's possible it could be something else in fstab.

---

