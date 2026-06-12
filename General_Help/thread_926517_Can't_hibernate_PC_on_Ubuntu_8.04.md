---
title: "Can't hibernate PC on Ubuntu 8.04"
date: 2008-09-22
forum: General Help
---

### Post by lchong2 on 2008-09-22
Hi,
I can't hibernate my PC. Each time when I select Hibernate from the logout screen, the system will show me a login screen.

Hibernate used to be working on Ubuntu 7.10 and also works for other distributions such as Fedora, Suse, Mandriva.

I have also reserved swap file size of more than 2 times system memory.

How do I troubleshoot this problem?

Thanks.
Cheng

---

### Post by Taxman415a on 2008-09-22
One possible problem is that the UUID of your swap partition isn't correctly listed in /etc/initramfs-tools/conf.d/resume
run ```
sudo blkid -c /dev/null
```
and put the UUID of the swap device in /etc/initramfs-tools/conf.d/resume in the form 
RESUME=UUID=blah-blah-etc-foo-bar

See [https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

---

### Post by lchong2 on 2008-09-24
Confirmed the UUID of my swap partition in /etc/initramfs-tools/conf.d/resume is correct.

Problem remained even after i install the latest updates.

---

### Post by Liquidcool on 2008-09-24
I can't believe I'm gonna thank the "Taxman"

I moved my swapfile an even though I followed the guide(s) I found here and elsewhere my hibernate did not work because two files were overlooked . . . I followed your suggestion about the resume file and then checked /etc/fstab . . .  the UUID was wrong in both places. After a reboot everything was working . . . um well hibernating

Thanks again

---

