---
title: "[SOLVED] Need to change permisions so i can rip cd"
date: 2008-09-11
forum: General Help
---

### Post by jimmysheldon on 2008-09-11
Hi there

My problem is this. I'd like to rip CD's onto my computer with rythmbox/audio CD extractor but when I do I get an error saying "Sound Juicer could not extract this CD.
Reason: Failed to create output directory: Access denied"

So I'm guessing I just need to change the permissions of either the cdrom drive or the directory where I'm burning (preferably both just to save my self any future hassle.)  My problem is that i just don't know the command to do such a thing, I know it's something to do with chmod or chown, but that's all I know.

Thanks, jimmy

---

### Post by hwttdz on 2008-09-11
You're probably going to want to look in the preferences of sound juicer and see where it's trying to make a directory, or file.  If it's trying to make a directory, I'd recommend just making the directory for it.   If it's trying to make files in the directory, you may want to change the permissions on the directory.  This is accomplished by chmod (for change mode, don't ask me I don't know).  Call chmod --help to see what you might need to do.

---

### Post by jimmysheldon on 2008-09-12
Yeah i've made the directory, so its just the permission for the drive that the directory is on. I've had a look down chmod --help and couldn't really figure it out, I'll take another look though. If anyone does know that line i need to execute that'd be great!

also, thanks for the reply

---

### Post by hwttdz on 2008-09-12
It's not correct but 
chmod 777 dirname
will work.  
The first digit is permissions for you, the second permissions for your group, the third for everyone else.  The numbers are permissions for you, the group and others.  And they are made by summing 
4 - read
2 - write
1 - execute
So read+write+execute=7, and 777 is all permissions for everyone.  It's usually good form to make permissions as restrictive as you can.

---

### Post by jimmysheldon on 2008-09-12
Hi, just thought I'd keep you updated. I've found [http://webmasterworkshop.com/guides/chmod_guide.shtml](http://webmasterworkshop.com/guides/chmod_guide.shtml) which makes chmod alot easier to understand that chmod --help. and from what i can figure out what i need to do is run the command ```
sudo chmod a=rwx directory
```

---

### Post by jimmysheldon on 2008-09-12
okay, so that failed. still can't make files or directories with out getting an error message saying "access denied" i'm back to sqaure 1 and struggling, can anyone point me in the right direction?

---

### Post by jimmysheldon on 2008-09-12
> **hwttdz said:**
> It's not correct but 
chmod 777 dirname
will work.

Yeah i tried that after reading the guide on the link i posted but to no avail. the command executes successfully but when i go to make a file in the directory just to test i get that same "access denied" message that is driving me insane. I've tried restarting too, and still get the same error message.

I'm starting to wonder when i need to use chown to change the owner? or perhaps even theres an error in my /etc/fstab (because the directory i'm trying to get permission to is on a mounted hard drive)

I'm not gonna let this beat me, i'm determined to suss it out

---

### Post by jimmysheldon on 2008-09-12
ahh, just been reading about and found that chmod doesn't affect vfat file systems, which my drive is. so that settles it, i do need to change my /etc/fstab

---

### Post by jimmysheldon on 2008-09-12
YES MATE! Got it sorted, for now at least.

Yeah basically i think chmod and chown don't affect vfat or nfts filesystem, but the annoying thing is when you run the command, they don't tell you they haven't changed anything.

So it was a problem with my /etc/fstab file in the end. To solve what i did was add uid=1000,gid=1000 to line for my cd drive and my hard drive.

My /etc/stab file is looking very messy at the moment, after all the tweaking and messing around i've done to it, so i'm thinking about cleanly witting it from scratch some time in the future. But for now, it works so if ain't broken...

---

