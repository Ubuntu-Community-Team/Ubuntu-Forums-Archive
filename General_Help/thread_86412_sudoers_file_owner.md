---
title: "sudoers file owner"
date: 2005-11-05
forum: General Help
---

### Post by pwaustin on 2005-11-05
I've somehow screwed up my sudoers file.  I was originally just getting the chmod error saying it needed to be 0440.  However, unlike other posts I've read, I am the owner of the file, so I can change the permissions.  The problem after is that after that I get the error 

sudo: /etc/sudoers is owned by uid 1000, should be 0

which i think is referring to the fact that root is not the owner.

Anyways, I can't use sudo and I've tried kdesu, but that returns

"Su returned with an error"

So, any ideas on how I can fix this?

---

### Post by heimo on 2005-11-05
Boot in recovery mode or using Live CD, chown root:root /etc/sudoers. I can confirm that on my system the permissions/ownership is 440 and root:root.

---

### Post by pwaustin on 2005-11-05
Thanks for the reply.

Ok, dumb question, how do i boot in recovery mode?

---

### Post by niko_ on 2005-11-05
for booting in recovery mode, when you are in grub choose the kernel that has recovery mode, or put a ubuntu cd1 and type there rescue.

---

### Post by pwaustin on 2005-11-05
Worked great!  Thanks a lot!

---

