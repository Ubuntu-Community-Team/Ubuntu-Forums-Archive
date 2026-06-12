---
title: "New To The Game"
date: 2008-06-10
forum: Hardware
---

### Post by crayon7 on 2008-06-10
Hey guys, Im a new user of Ubuntu and found this site when I was on the hunt for info using an IDE to USB device on the new box. I do computer work and was wanting to use my Ubuntu box to run scans and clean up HDs but cant get this thing to work. Any ideas would be great. Vantec SATA/IDE to USB 2.0 Adapter. Let me know if its a lost cause and I wont waste time trying to figure it out. Ill just waste time learning Ubuntu. :popcorn:

---

### Post by EtniesBMX on 2008-06-10
I'm afraid I can't help answer your question, but a more descriptive title would probably help out with getting answers. Have fun  =)

---

### Post by ppc_guy on 2008-06-10
> **EtniesBMX said:**
> I'm afraid I can't help answer your question, but a more descriptive title would probably help out with getting answers. Have fun  =)
+2 Need a lot more info than just that. Does the device mount? Need a lot more background info here.

---

### Post by crayon7 on 2008-06-10
It says cannot mount volume... Unable to mount the volume.. The error message tells me that it failed to mount that windows was in hibernate and to shut it down properly or it tells me to type in this command. 

mount-t ntfs-3g /dev/sdb2/media/disk -o remove_hiberfile

---

### Post by wannadumpwindows on 2008-06-10
Sounds like the last time the computer that your hard disk was in was shutdown, it was in hibernate. And you need to remove the hibernation file before it will let you access the drive. I have a similar adapter, but a different brand. Mine has never given me issues like that. I can look at any hard disk no matter how it was shut down.

---

### Post by crayon7 on 2008-06-10
So if I run this command would it enable me to use the drive?

---

### Post by wannadumpwindows on 2008-06-10
> **crayon7 said:**
> So if I run this command would it enable me to use the drive?

I can't say for sure, but that's what it looks like. You might want to wait a bit for someone with a little more knowledge on the subject. But looking at the command, that's what it appears to want to do. If that's all it's going to do, I don't really see how it could hurt anything.

---

### Post by scott_g on 2008-06-11
I've had that message before on an internal drive...  I just restarted the computer into windows, and shut it down properly.  The next time it was in Ubuntu, it worked fine.  Same thing when windows crashes; you have to restart the computer (or remove the lock file), before you can mount the ntfs drive again.  

I can't add any more information to the removing of the file, but you may loose any programs/info you had open before you hibernated the computer...

Scott

---

