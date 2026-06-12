---
title: "add hard disk - what format"
date: 2008-10-22
forum: General Help
---

### Post by mikepac69 on 2008-10-22
Hi all,

I am pretty new to Ubuntu.  I installed it correctly and now i need to patition my second drive.  What format and how should i do it? I have the gui GParted installed.

Thanks in advance...

Michael

---

### Post by No-Neck on 2008-10-22
If you need to access the files from Windows then it would be advisable to choose NTFS.

If not then you'll probably recommended to use either ext3 or reiserfs:

ext3 - default for most Linux installations, your Ubuntu should be using ext3 already.

reiserfs - I use this, I find it a fair bit faster but it's probably less tried and tested and the man it was named after has been put in prison for murdering his wife.

Your choice really.

EDIT: Oh yeah, and you're best off doing it with GParted, just right click on the empty drive and 'Create New' (or something similar).

---

### Post by jerome1232 on 2008-10-22
> **No-Neck said:**
> the man it was named after has been put in prison for murdering his wife.

Wow, interesting.

  I actually kind of like xfs because it has a few shiny tools thrown in that ext3 doesn't have. Like online defragging (should you ever need it) better support for resizing the filesystem while it's online, faster with large files (reiserfs is faster with small files). As far as I know it's developer isn't a madman ;) which is always a plus.

ext3 is a tried and true format though so you can't go wrong with it.

---

### Post by mikepac69 on 2008-10-22
ok, i formatted it with ext3.  Now how do I mount it or will it do it by itself?

---

### Post by bodhi.zazen on 2008-10-22
> **mikepac69 said:**
> ok, i formatted it with ext3.  Now how do I mount it or will it do it by itself?

You will need to add an entry in fstab

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

If you get stuck, feel free to ask, but we need to know your partition and desired mount point.

---

### Post by jespdj on 2008-10-22
> **No-Neck said:**
> reiserfs - I use this, I find it a fair bit faster but it's probably less tried and tested and the man it was named after has been put in prison for murdering his wife.
It was not only named after him, he invented it: [Hans Reiser](http://en.wikipedia.org/wiki/Hans_Reiser)

---

### Post by No-Neck on 2008-10-22
> **jespdj said:**
> It was not only named after him, he invented it: [Hans Reiser](http://en.wikipedia.org/wiki/Hans_Reiser)
Yes, which is why it's probably not such a good thing that he's gone to prison. Not like he's going to be having much input on the project from there. :D

---

### Post by mikepac69 on 2008-10-22
I mounted it but cant write anythng to it... I am stuck. The partition is /dev/sdb1 and wnt to mount it to /media/disk1

How can I get it to mount everytime the system boots up?

---

### Post by bodhi.zazen on 2008-10-22
> **mikepac69 said:**
> How can I get it to mount everytime the system boots up?

You need to unmount the partition and add an entry in fstab.

With the partition mounted, use chown and chmod to set permissions.

```
chown user.user /mount/point
sudo chmod 777 /mount/point # or 770 if you want to be more restrictive
```See the link I gave you for details.

---

### Post by Nxion on 2008-10-22
> **bodhi.zazen said:**
> You will need to add an entry in fstab

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

If you get stuck, feel free to ask, but we need to know your partition and desired mount point.


Follow the above from bodhi

---

### Post by mikepac69 on 2008-10-22
ok. big mistake.  I set in the FSTAB an extra line as my boot partition with some different options and now i cant boot anmore.  How can I remove it without loading Ubuntu? I cant even boot with the CD.

Help me!please

---

### Post by niteshifter on 2008-10-22
Hi .. and woah...

> reiserfs - I use this, I find it a fair bit faster but it's probably less tried and tested and the man it was named after has been put in prison for murdering his wife.

> As far as I know it's developer isn't a madman  which is always a plus.

So much for critical thinking :( What, pray tell does any of this have to do with the technical merits - or demerits - of ReiserFS?

Answer: Not a thing. ReiserFS and Reiser4 will continue to receive support, there are many other people involved. As to using either: my argument against Reiser file systems is the lack of robust fsck tools. Next, it's not really a good match for typical desktop usage, server yes, desktop not so much. Third: it's a hell of file system to turn loose on a newbie: when it breaks or needs tuning where will he turn to for support? The available literature is very sparse in comparison to more mainline file systems like ext2 / ext3.

"There is a thin line between genius and insanity. I have erased this line." -- Oscar Levant

---

### Post by bodhi.zazen on 2008-10-22
> **mikepac69 said:**
> ok. big mistake.  I set in the FSTAB an extra line as my boot partition with some different options and now i cant boot anmore.  How can I remove it without loading Ubuntu? I cant even boot with the CD.

Help me!please

Editing /etc/fstab should not affect your ability to boot from a CD drive. Booting from a CD drive is usually an option from your BIOS.

Boot the live CD, and we can edit (fix) fstab.

From the live CD :

```
sudo mount /dev/sdxy /mnt
```

Where "sdxy" is your Ubuntu partition (/dev/sda1 for example).

You can then edit fstab with:

```
gksu gedit /mnt/etc/fstab
```

If you need specific instructions, I suggest you post the output of :

```
sudo blkid
```

and the contents of the file /mnt/etc/fstab

---

### Post by bodhi.zazen on 2008-10-22
> **niteshifter said:**
> Hi .. and woah...





So much for critical thinking :( What, pray tell does any of this have to do with the technical merits - or demerits - of ReiserFS?

Answer: Not a thing. ReiserFS and Reiser4 will continue to receive support, there are many other people involved. As to using either: my argument against Reiser file systems is the lack of robust fsck tools. Next, it's not really a good match for typical desktop usage, server yes, desktop not so much. Third: it's a hell of file system to turn loose on a newbie: when it breaks or needs tuning where will he turn to for support? The available literature is very sparse in comparison to more mainline file systems like ext2 / ext3.

"There is a thin line between genius and insanity. I have erased this line." -- Oscar Levant

I think a better answer is ~

Answer: Don't feed the trolls ;)

---

