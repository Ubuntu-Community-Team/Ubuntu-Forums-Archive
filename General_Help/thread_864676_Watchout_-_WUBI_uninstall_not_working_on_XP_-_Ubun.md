---
title: "Watchout - WUBI uninstall not working on XP - Ubuntu 8.0.4.1 Hardy Heron failure"
date: 2008-07-19
forum: General Help
---

### Post by VirtualSandBox on 2008-07-19
Folks,

I have been trying out various live CDs in the last few days so I can select the best flavor fit for my cyustom built PC(AMD Phenom Quad Core on ECS GeForce 7050M-M, 4GB Ram running Windows XP MCE SP2).

Had Ubuntu 8.0.4.1 installed in "Install Inside Windows" mode. Then had it updated for all the necessary updates that Ubuntu suggested.

It is then that I realized that I have ran out of space on the home directory (which resulted in few issues that have resulted in further issues that is choked further changes.) Anyways, all these issues made me think start over (if not move on... :( )

But when I tried uninstalling, the "Uninstall-Ubuntu.exe" just wont run. (clicking it will result in a sub-second hourglass cursor and nothing else).

Tried using windows uninstaller to uninstall Ubuntu from the control panel. Result is the same.

Now, I can have it nuked using force and cleared. But, I was not expecting to do that when I installed it when I got all the high praises the 8.0.4.1 Hardy Heron received on all media.

After some research found that this sort of issues have there for a long time, perhaps still getting addressed. :mad: :mad:

See for ex:
[http://ph.ubuntuforums.com/showthread.php?t=551841&highlight=xp+uninstall](http://ph.ubuntuforums.com/showthread.php?t=551841&highlight=xp+uninstall)

Just wanted to post it, so one would take know the one-way trip they are possibly taking beforehand. 

Also, just in case anybody had resolved this :KS :KS, I am all ears. :)

Thanks,

---

### Post by unicorn_2003_1 on 2008-07-20
Wubi uninstalled itself and the Ubuntu installation perfectly on my machine, no complaints whatsoever. 

It WORKS.

---

### Post by Pmax on 2008-07-20
I'm having the same problem. I can't run either wubi.exe again nor the uninstaller.
I'm also running winXP.

---

### Post by Pmax on 2008-07-20
check [http://ubuntuforums.org/showthread.php?t=861800&highlight=wubi+uninstall&page=2](http://ubuntuforums.org/showthread.php?t=861800&highlight=wubi+uninstall&page=2)

Sloved my problem

---

### Post by VirtualSandBox on 2008-07-20
Thanks PMax. :)

That sounds like the defect I am facing too. I have Wubi installed on G drive instead of the C drive. I will try the new patched Wubi after I tried some more of the items listed on that page you sent.

On to new ventures... :)

Thanks,

---

### Post by ago on 2008-07-21
Yes that was a bug or Wubi rev 505 fixed in Wubi rev 506, and, as explained in the sticky FAQ thread as well as in the WubiGuide you need to use a separate uninstaller (provided therein) if you installed with Wubi 505 on a drive different from C:

---

### Post by VirtualSandBox on 2008-07-25
Ok, so that was my problem. I completed the uninstall.

---

### Post by IeU on 2008-07-26
Just want to say ive the same problem with rev.506 . . .

the uninstall does not work under Vista . . .

I even tried that separated exe too . . .

Vista64 + Run with Adm rights . . .

---

### Post by Orlsend on 2008-07-26
Worked perfectly fine On my Windows Xp

---

### Post by ago on 2008-07-29
> **IeU said:**
> Just want to say ive the same problem with rev.506 . . .

the uninstall does not work under Vista . . .

I even tried that separated exe too . . .

Vista64 + Run with Adm rights . . .

If you originally installed rev505 and then run rev506, rev506 will still run the rev505 uninstaller. So you have to use the stand-alone 506 uninstaller in the link above.

---

### Post by IeU on 2008-08-02
ive installed the rev506

had to do the manually uninstall . . .

reinstalling it just to bug test . . .

---

