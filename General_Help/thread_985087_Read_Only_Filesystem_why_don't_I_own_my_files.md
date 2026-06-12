---
title: "Read Only Filesystem?? why don't I own my files?"
date: 2008-11-17
forum: General Help
---

### Post by gschoppe on 2008-11-17
I just installed intrepid on my previously gutsy box, and am having issues...

I had /home and /home/sharedData as two ext3 volumes on an LVM, since I couldn't figure out how to get ubuntu to install with LVM support, I installed intrepid with /home on the / partition.

afterwards, I installed LVM2, mounted my old /home partition to /tempHome, and set up fstab.  then I booted to live cd and copied /home to /tempHome.  I deleted the contents of /home, and edited fstab to make my LVM based partition mount to /home.

back in my normal ubuntu installation, I took ownership (via sudo nautilus and the properties -> permissions tab) of /home, and clicked the recursive option...


now to my issues... it appears that I sometimes have permissions in home, and sometimes don't... some settings won't persist, and Firefox will not allow me to accept certificates or even use the search bar unless i run "sudo firefox"...  my sharedData partition now says it has a "read only filesystem" and is owned by root... it wont allow me to change this, because its a "read only filesystem"...



what do I do?  This seems totally illogical.

---

### Post by gschoppe on 2008-11-17
I tried rebooting to a live cd, but it failed (busybox initramfs)


... what the heck?

---

### Post by scouser73 on 2008-11-17
Hi, to have full access to your files you need to log in as root. Firstly open a Terminal, then type **gksudo nautilus**, you'll then be prompted for your password, enter it, once you've done that, you'll be logged in as root, make your way to the partition/HDD/file or folder and then right click, select the **Properties** tab, then the **Permissions** tab, from here select the Owner drop-down menu, find your name in the list, select and click close. You will now have full access rights.

---

### Post by estyles on 2008-11-17
> **scouser73 said:**
> Hi, to have full access to your files you need to log in as root.

I think you just read his subject line and not the post...

Umm...  It sounds like you copied your old home directory from Gutsy into Intrepid.  It's likely an issue of who owns the files?  Can you find out your uid and the uid that owns those files?  I don't have access to my Ubuntu box right now, nor time to search for the syntax...  but if you do a search, you should be able to figure out to find out what user id owns the files.

If the owner is not the same as your uid, you'll need to chown the entire home directory.

---

