---
title: "USB Drive Permisions"
date: 2008-09-05
forum: General Help
---

### Post by ceckard on 2008-09-05
I am having problems creating files/folders on my usb drive. Here's what I've tried with out any success:

sudo -r chmod 777 /media/disk
(this gives me an error message about the -r being an illegal option)

sudo chown chad:chad /media/disk

No matter what I can not change the permissions. I see that I am the owner and have write permissions, but the "root" group has "none" set as permissions for folder access.

Any suggestions that I can try to fix this?

Thanks.

---

### Post by lian1238 on 2008-09-05
Does your USB drive happen to have a built-in hardware write-lock? I couldn't write to a friend's drive which had one. Related problem?

---

### Post by b0n60 on 2008-09-05
i never saw this problem on ubuntu but you can simply try >  sudo nautilus <
that opens the file manager with root rights, the secon doption is to open a shell with root rights and mkdir xxxx but sorry i cant help you more the root user must normally have his rights ...:confused:

---

### Post by ceckard on 2008-09-05
No it doesn't. What's weird (i guess i should have mentioned this) but up until a few days ago I had write permissions.

It seems like Ubuntu would automatically grant write permissions to a drive like this. I mean if I inserted the drive I think it would be safe to say that I own it and can make changes to it.

I tried the "sudo nautilus" and I can't create files/folders with it either. Actually it is grey'd out and  I can't even click on it. I do not have the "Properties" option on the root of the drive. And If I look at the properties of a folder on the drive and try to change the permissions it tells me that access is denied.

Really weird

---

### Post by ceckard on 2008-09-05
I have also discovered that if I insert a different flash drive I do have write permissions on it. But what is even weirder is that when I look at the permissions on the flash drives I can write to they are exactly the same as the one I can't write to.

Now I'm really confused. I just re-inserted the drive I was having problems with and now I can write to it.

I havn't rebooted today or anything. It just started working.

Oh well I'm happy now. I didn't want to abandon Ubuntu for something so trivial.

---

