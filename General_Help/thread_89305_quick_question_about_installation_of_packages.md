---
title: "quick question about installation of packages"
date: 2005-11-12
forum: General Help
---

### Post by spyke01 on 2005-11-12
is it possible to have the os on one partition, but to install the packages and config files to another partition?

---

### Post by DJ_Max on 2005-11-12
If I understand your question correctly, binaries and such are usually installed in /usr. Global config files are sometimes in /etc (sometimes user configs are in your /home).

So yes, you can. BTW, is there a reason you ned your setup like this?

---

### Post by spyke01 on 2005-11-12
there is a reason, but my boss wont let me say ^^

where is the actual os and temp inet files and stuf like that located for linux?

---

### Post by DJ_Max on 2005-11-12
Look for (different) config files in the /etc/init.d directory. The rc.inet files should be there. OS == Ubuntu software. So it's scattered.

---

### Post by spyke01 on 2005-11-12
hmm, is there anywhere that files get downloaded when surfing the internet in linux, like spyware, temp files and such?

---

### Post by DJ_Max on 2005-11-12
Not really(the same is true with OS X, because both Linux and OS X lack anything like ActiveX), even if they did, in order for them to do anything, they would need a user with proper permissions (i.e., root).

---

### Post by spyke01 on 2005-11-12
awesome, thanx alot m8

sorry i couldnt tell you guys u.u

---

### Post by SickTwist on 2005-11-12
[QUOTE=spyke01]there is a reason, but my boss wont let me say ^^

where is the actual os and temp inet files and stuf like that located for linux?[/QUOTE]

Some programs use the /tmp directory for temporary storage. However, I think the majority store their temp files, cache and such in the user's home directory (usually in a hidden file or hidden directory). For instance, Firefox stores web pages in the user's home directory. Nautilus stores thumbnails in each user's home directory as well.

I don't think regular users have permission to write files anywhere besides /tmp or ~ (user's home directory) after a default install.

Hope that helps.

---

