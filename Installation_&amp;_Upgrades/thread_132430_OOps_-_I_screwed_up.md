---
title: "OOps - I screwed up"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by cybersquirrel on 2006-02-18
I just installed ubuntu last night.  I was playing with it this morning and using bad judgement, deleted the adminstrator account name from my user list.

The account is still loginable, but I seem to have lost all admin rights.

Is there anyway I can get those rights back or do I have to do a full reinstall.  If I do a full reinstall, will it overright the same disc allocation?  XP covers 75% of the drive, 25% of the drive is Ubunto.

Please advise.

---

### Post by alamba on 2006-02-18
By administrator account name do you mean the first user you created?

Akshay

---

### Post by taurus on 2006-02-18
If you use GRUB to boot your Ubuntu, one way is to boot it into single user mode.  Then just add that user back on the adm list again in /etc/group...  And after you get back the root's privillage, write a big words in red on Post-It, "I'll be careful next time!!!", and post it on your monitor!  ;)

---

### Post by cybersquirrel on 2006-02-18
Yeah ... I did mean the first account I created ... yeah ... It was a stupid mistake ... I was really expecting the computer to say, "no you can't do that"

---

### Post by angkor on 2006-02-18
[QUOTE=cybersquirrel]I was really expecting the computer to say, "no you can't do that"[/QUOTE]

*lol* ;)

Well Linux usually doesn't work that way. Don't sweat it, most of us have been there and worse :)

It sometimes asks if you're sure about what you're doing but in general Linux assumes you know what you're doing

---

### Post by cybersquirrel on 2006-02-18
So will Taurus's suggestion work? If so, is GRUB one of the boot options?  Bare with me ... I'm a super Linux novice ... but really anxious to learn it.  Mr. Gates has enough of my money already!

---

### Post by cybersquirrel on 2006-02-20
I'm still trying to fix this problem.  Any more input?

---

