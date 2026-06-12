---
title: "Laptop random freeze"
date: 2010-10-05
forum: Hardware
---

### Post by crazyelf on 2010-10-05
I have:
Laptop - Acer aspire 5610Z 
OS - Ubuntu 10.4.1
Kernel - 2.6.32-24-generic

I've had problems with this in the past but with the newest release I hadn't been having any problems.  But lately it started back up.  It randomly will freeze.  Sometimes 4-5 hours when idle or less had it happen with-in 10 minutes. Left and came back to it locked up.  Other times in the middle of watching a movie. ect.. 

I've looked through the Xorg log and the kern.log for errors.  

The only error I see between the two is:

> Fatal server error:
xf86OpenConsole: VT_WAITACTIVE failed: Interrupted system call

I'm not sure if this is the actual error or what.  Can someone point me in the right direction?

Thanks,

[update]
Now i'm getting this:

[ATTACH]171617[/ATTACH]

I recently got a similar message in a VM I had a server running on. Corrupt drive?

---

### Post by dirghrabadia on 2010-10-05
If you previously had this problem, I would suggest you to run memtest 86+ at boot, though I am not sure if that might be a problem. If not, I am sure someone might be able to help you out :)

---

### Post by crazyelf on 2010-10-05
I went back to windows 7 for a while.  Never had a problem.  Did the complete switch from windows to all linux.  Two or three months went by with out a problem.  Now its back. 

Thanks, I will give a memory check a shot.  I doubt its that simple though. 

I was thinking maybe graphics because of the error.. but that wouldn't cause the whole system to lock down.  No processing  happens of any kind.  Tried SSh'ing into the box nothing responds.  It fully freezes.

---

### Post by crazyelf on 2010-10-05
Nope memory is fine... Anyone else? I'm fresh out of ideas.  Is there a way to put the kernel in a heavy logging mode so I can see what's up?

---

### Post by crazyelf on 2010-10-08
Now i'm getting this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171617[/IMG]

I recently got a similar message in a VM I had a server running on. Corrupt drive?

Seems posts can't be deleted?  Was gonna delete the last post and put this one in.  

Updated the first post.

---

