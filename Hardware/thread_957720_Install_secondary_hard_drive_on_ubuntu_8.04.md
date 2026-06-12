---
title: "Install secondary hard drive on ubuntu 8.04"
date: 2008-10-24
forum: Hardware
---

### Post by ERnst W. on 2008-10-24
Hi everyone,

I got myself a new s-ata hard drive. The hard drive is supposed to run as secondary drive. So now I've plugged it in but don't know how to enter it. It shows up under Places-Computer so I guess I'm missing user permissions but I'm not totally sure. If there might be other reasons please tell me. This is what it shows me when I click on properties:

 Name:         SCSI Drive
 Type:         unknown type
 Size:         unknown
 Location:     computer:///
 Volume:       unknown
 Mine type:    application/octet-stream

 Modified:     unknown
 Accessed:     unknown


 Permissions:

 The permissions of "SCSI Drive" could not be determined.

I don't know if there's already a partition on the hard drive, but since it's used I guess there is an NTFS one on it. Hope you can help me.

---

### Post by dabl on 2008-10-24
You've got a couple of issues to sort there:

1. Partitioning - unless you want to leave it exactly as it is, you can run Gparted and partition or un-partition it, and format it ext3 for Linux use.  Do this while it is not mounted.

2. Mounting -- if you want it to be automatically mounted when you boot *buntu, you'll have to open /etc/fstab with a text editor, in root mode, and add a mount line for it.

That's general guidance -- a search on the forum for partitioning and mounting threads will provide lots of details.  :)

---

### Post by ERnst W. on 2008-10-25
ok I've got it all working now, thanks for your support.
Now the disk tells me that 18.8 Gigs are already in use without anything on it... is that normal or how can I get rid of these 18.8 gigs?

---

### Post by dabl on 2008-10-26
I'm not sure what you're seeing, or whether I'm understanding it.

An "empty" hdd partition will normally have a small percentage (1% - 2%) of its space used for the filesystem itself.  I happen to have an empty 150G hard drive, formatted ext3, mounted here and it shows 2.38G used in GParted.  So that's normal.  But not 18G.  Either something is on it, or you're not looking at what you think you're looking at, or ....   :confused:

---

### Post by ERnst W. on 2008-10-29
well that was what I was wondering about. I've got an 400G HDD so I guess about 7 or 8 might be normal...

Is there a way to find out if there is something hidden on the HDD (beside Ctrl H) and could it survive being formated?

---

### Post by djuke04 on 2009-10-28
Hello,
  I'm not trying to jack the thread, but I'm in the middle of the same process.  I've added a 1TB SATA drive and partitioned it into two halves.  I can find each of the drives, and mount them.  However, when I try to copy files into them, or create folders, I do not seem to have the permissions.

  I can't change the permissions because I'm not the owner.  How do I become the owner? I'm hoping that I can add it to the /etc/fstab and as it mounts during boot up that will fix it all, but I don't know what the text I'm supposed to add is, and where I should add it.

  In terminal: sudo gedit /etc/fstab

  Then a file opens but it isn't clear where I'm supposed to add which text.

thanks for your help!

---

### Post by djuke04 on 2009-10-28
SOLVED it,

the solution was to change the owner by 

$ sudo chown USERNAME:USERNAME dev/sdb1

then I figured out the text line to add in the /etc/fstab  It was just at the bottom.  I named them backwards at first, but corrected it after I had finished all the file transfers.

---

